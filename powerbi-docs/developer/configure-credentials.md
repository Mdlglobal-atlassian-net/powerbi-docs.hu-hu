---
title: Hitelesítő adatok programozott konfigurálása a Power BI-hoz
description: Hitelesítő adatok automatizálási célú, programozott konfigurálása a Power BI-hoz
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: 2b4e2f5a4e95b412459dd8fe8d497966e541b389
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892839"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Hitelesítő adatok programozott konfigurálása a Power BI-hoz

Az alábbi lépések végrehajtásával programozott módon konfigurálhat hitelesítő adatokat a Power BI-hoz.

## <a name="configure-a-credential-flow-for-data-sources"></a>Hitelesítőadat-folyam konfigurálása adatforrásokhoz

1. A [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) hívásával állapítsa meg az adathalmaz adatforrásait. A válasz törzsében minden adatforrásnál szerepel annak típusa, kapcsolati adatai, az átjáró és az adatforrás-azonosító.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Az [adatforrás frissítésére bemutatott példák](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) alapján készítse el a hitelesítő adatok típusának megfelelő hitelesítőadat-sztringet.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Állítsa össze a hitelesítő adatok részleteit.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. A hitelesítő adatok beállításához hívja meg az [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) API-t az 1. lépésben kapott átjáróval és adatforrás-azonosítóval, valamint a hitelesítő adatok 3. lépésben megkapott részleteivel.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Helyszíni adatforrás lejárt hitelesítőadat-folyama

1. [Hajtsa végre az előző példa 1. és 2. lépését](#configure-credential-flow-for-data-sources).

2. A [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) API hívásával kérje le az átjáró nyilvános kulcsát.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Titkosítsa a hitelesítőadat-sztringet az átjáró nyilvános kulcsával, az RSA titkosítási algoritmussal.

    A titkosításhoz használja az alábbi segédosztályt:

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

4. Állítsa össze a hitelesítő adatok részleteit a titkosított hitelesítő adatokkal.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. A hitelesítő adatok beállításához hívja meg az [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) API-t.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Új adatforrás konfigurálása adatátjáróhoz

1. Telepítse számítógépére a [helyszíni adatátjárót](https://powerbi.microsoft.com/gateway/).

2. A [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) hívásával kérje le az átjáró azonosítóját és nyilvános kulcsát.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Az előző példához hasonlóan állítsa össze a hitelesítő adatok részleteit az átjárónak a [Helyszíni adatforrás lejárt hitelesítőadat-folyama](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway) lépésben megkapott nyilvános kulcsát használva.

4. a kérés törzsének összeállítása

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
    dataSourceType: "SQL",
    connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
    credentialDetails: credentialDetails,
    dataSourceName: "my sql datasource");
    ```

5. Hívja meg a [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) API-t.

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Nem található átjáró és adatforrás-azonosító a Get Datasources hívásakor

Ez a hiba azt jelenti, hogy az adathalmaz nincs átjáróhoz kötve. Új adathalmaz létrehozásakor minden felhőbeli kapcsolathoz automatikusan létrejön egy, hitelesítő adatok nélküli adatforrás a felhasználó felhőátjáróján. Ez az átjáró a felhőbeli kapcsolatok hitelesítő adatainak tárolására lesz használva.

Az adathalmaz létrehozása után automatikusan kötés jön létre az adathalmaz és egy megfelelő átjáró között, amely az összes kapcsolat megfelelő adatforrását tartalmazza. Ha nincs egy vagy több ilyen megfelelő átjáró, akkor az automatikus kötés sikertelen lesz.

Hozza létre az esetleg hiányzó helyszíni adatforrásokat, az adathalmazt pedig kösse manuálisan egy átjáróhoz a [Bind to Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) használatával.

A kötéshez alkalmas átjárók felderítésére használja a [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) API-t.
