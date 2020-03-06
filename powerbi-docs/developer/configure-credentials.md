---
title: Hitelesítő adatok programozott konfigurálása a Power BI-hoz
description: Hitelesítő adatok programozott konfigurálása a Power BI automatizálásakor
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/23/2020
ms.openlocfilehash: 1c8741736f0639cba7f8df3f9891a6fe20397d8e
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260784"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Hitelesítő adatok programozott konfigurálása a Power BI-hoz

Az alábbi lépések végrehajtásával programozott módon konfigurálhat hitelesítő adatokat a Power BI-hoz.

## <a name="update-credentials-flow-for-data-sources"></a>Hitelesítőadat-folyam frissítése adatforrásokhoz

1. A [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) hívásával állapítsa meg az adathalmaz adatforrásait. A válasz törzsében minden adatforrásnál szerepel annak típusa, kapcsolati adatai, az átjáró és az adatforrás-azonosító.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Az [adatforrás frissítésére bemutatott példák](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) alapján készítse el a hitelesítő adatok típusának megfelelő hitelesítőadat-sztringet.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. A [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) API hívásával kérje le az átjáró nyilvános kulcsát.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Titkosítsa a hitelesítő adatokat.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    Titkosítsa a hitelesítőadat-sztringet a 2. lépésben használt átjáró nyilvános kulcsával. A különböző átjáróverziók különböző nyilvánoskulcs-mérettel rendelkezhetnek. Tekintse át az alábbi példákat az SDK-kódban, amely a [PowerBI-CSharp GitHub-adattárbanérhető el](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Állítsa össze a hitelesítő adatok részleteit a titkosított hitelesítő adatokkal.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    Használja az AssymetricKeyEncriptor osztályt a **3. lépésben** lekért nyilvános kulccsal.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. A hitelesítő adatok beállításához hívja meg az [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) API-t.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Új adatforrás konfigurálása adatátjáróhoz

1. Telepítse számítógépére a [helyszíni adatátjárót](https://powerbi.microsoft.com/gateway/).

2. A [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) hívásával kérje le az átjáró azonosítóját és nyilvános kulcsát.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. A [Hitelesítőadat-folyam frissítése adatforrásokhoz](#update-credentials-flow-for-data-sources) című szakasz szerint állítsa össze a hitelesítő adatok részleteit az átjárónak a **2. lépésben** lekért nyilvános kulcsát használva.

4. Állítsa össze a kérés törzsét.

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

## <a name="credential-types"></a>Hitelesítő adatok típusai

Ha egy **vállalati helyszíni átjárón[ a [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) használatával az ](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource)Adatforrás létrehozása[ vagy az ](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)Adatforrás frissítése** utasítást hívja, a hitelesítő adatokat az átjáró nyilvános kulcsával kell titkosítani.

>[!NOTE]
>A .NET SDK v3 az alább felsorolt .NET SDK v2-példákat is futtathatja.

### <a name="windows-and-basic-credentials"></a>Windowsos és alapszintű hitelesítő adatok

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Kulcshitelesítő adatok

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2 hitelesítő adatok**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Névtelen hitelesítő adatok**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Nem található átjáró és adatforrás-azonosító a Get Datasources hívásakor

Ez a hiba azt jelenti, hogy az adathalmaz nincs átjáróhoz kötve. Új adathalmaz létrehozásakor minden felhőbeli kapcsolathoz automatikusan létrejön egy, hitelesítő adatok nélküli adatforrás a felhasználó felhőátjáróján. Ez az átjáró a felhőbeli kapcsolatok hitelesítő adatainak tárolására lesz használva.

Az adathalmaz létrehozása után automatikusan kötés jön létre az adathalmaz és egy megfelelő átjáró között, amely az összes kapcsolat megfelelő adatforrását tartalmazza. Ha nincs egy vagy több ilyen megfelelő átjáró, akkor az automatikus kötés sikertelen lesz.

Ha helyszíni adatkészleteket használ, hozza létre a hiányzó helyszíni adatforrásokat, az adathalmazt pedig kösse manuálisan egy átjáróhoz a [Bind to Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) használatával.

A kötéshez alkalmas átjárók felderítésére használja a [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) API-t.