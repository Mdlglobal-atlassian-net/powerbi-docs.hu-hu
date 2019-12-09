---
title: A Security Assertion Markup Language (SAML) használata a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezéshez
description: Az átjáró konfigurálása a Security Assertion Markup Language (SAML) használatával a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezés engedélyezéséhez.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: bbb0584843f79445c4e5cca073f9c4b953d346aa
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699360"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>A Security Assertion Markup Language (SAML) használata a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezéshez

Az SSO engedélyezése egyszerűvé teszi a Power BI-jelentések és -irányítópultok számára az adatok helyszíni forrásokból történő frissítését, miközben tiszteletben tartják azokat a felhasználói engedélyeket is, amelyeket azokon a forrásokon konfiguráltak. Használhatja a [Security Assertion Markup Language- (SAML-)](https://www.onelogin.com/pages/saml) protokollt a közvetlen SSO-kapcsolat engedélyezéséhez. 

## <a name="supported-data-sources"></a>Támogatott adatforrások

Jelenleg az SAP HANA használata támogatott a SAML-protokoll esetén. További információt az egyszeri bejelentkezésnek a SAML használatával az SAP HANA rendszerhez történő beállításáról és konfigurálásáról: [SAML-alapú SSO-bejelentkezés a HANA-ba a BI Platformhoz](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA).

További adatforrásokat támogatunk a [Kerberosszal](service-gateway-sso-kerberos.md) (többek között az SAP HANA-t).

SAP HANA esetében ajánlott engedélyezni a titkosítást az SAML SSO-kapcsolat létrehozása előtt. A titkosítás engedélyezéséhez konfigurálja a HANA-kiszolgálót úgy, hogy fogadja a titkosított kapcsolatokat, és konfigurálja az átjárót úgy, hogy titkosítást használjon a HANA-kiszolgálóval való kommunikációhoz. Mivel a HANA ODBC-illesztőprogram alapértelmezés szerint nem titkosítja az SAML helyességi feltételeit, az aláírt SAML típusú helyességi feltételt a rendszer az átjáróról a HANA-kiszolgálóra *korlátozás nélkül* küldi, így azt harmadik felek elfoghatják és újra felhasználhatják. Ha engedélyezni szeretné a HANA-titkosítást az OpenSSL-könyvtárral, tekintse meg [Az SAP HANA titkosításának engedélyezése](/power-bi/desktop-sap-hana-encryption) című cikket.

## <a name="configuring-the-gateway-and-data-source"></a>Az átjáró és az adatforrás konfigurálása

Az SAML használatához megbízhatósági kapcsolatot kell létrehoznia a HANA-kiszolgáló, amelyhez engedélyezni szeretné az SSO-t és az átjáró között. Ebben az esetben az átjáró szolgál az SAML identitásszolgáltatójaként. Ezt a kapcsolatot többféleképpen is létre lehet hozni, például az átjáró identitásszolgáltatója X509 szabvány szerinti tanúsítványának a HANA-kiszolgálók megbízhatósági tárolójába való importálásával vagy az átjáró X509-tanúsítványának a HANA-kiszolgálók számára megbízhatónak minősülő legfelső szintű hitelesítésszolgáltató (CA) általi aláírásával. Ebben az útmutatóban az utóbbi megközelítést ismertetjük, de használhat más megközelítést is, ha az kényelmesebb.

Ebben az útmutatóban OpenSSL-t használunk a HANA-kiszolgáló titkosítási szolgáltatójaként, de OpenSSL helyett az SAP az SAP titkosítási kódtár (másként CommonCryptoLib vagy sapcrypto) használatát javasolja a beállítási lépések végrehajtásához a bizalmi kapcsolat létrehozásakor. További információt az SAP hivatalos dokumentációjában talál.

A következő lépések azt ismertetik, hogyan hozhat létre megbízhatósági kapcsolatot a HANA-kiszolgáló és az átjáró identitásszolgáltatója között az átjáró identitásszolgáltatója X509-tanúsítványának a HANA-kiszolgáló által megbízhatónak tekintett legfelső szintű hitelesítésszolgáltató általi aláírásával. Ezt a legfelső szintű hitelesítésszolgáltatót fogja létrehozni:

1. Hozza létre a legfelső szintű hitelesítésszolgáltató X509-tanúsítványát és titkos kulcsát. A legfelső szintű hitelesítésszolgáltató X509-tanúsítványának és a titkos kulcsának .pem formátumban történő létrehozásához például adja meg ezt a parancsot:

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    Győződjön meg róla, hogy a legfelső szintű hitelesítésszolgáltató titkos kulcsa megfelelően védett. Ha egy harmadik fél megszerzi, felhasználható a HANA-kiszolgálóhoz való jogosulatlan hozzáférésre. 

 1. Adja hozzá a tanúsítványt (például CA_Cert.pem) a HANA-kiszolgáló megbízhatósági tárolójához, hogy a HANA-kiszolgáló megbízzon a létrehozott legfelső szintű hitelesítésszolgáltató által aláírt minden tanúsítványban. 

    A HANA-kiszolgáló megbízhatósági tárolójának helye az **ssltruststore** konfigurációs beállítás vizsgálatával található meg. Ha követte az SAP dokumentációját azzal kapcsolatban, hogyan konfigurálja az OpenSSL-t, akkor a HANA-kiszolgáló már megbízhat egy legfelső szintű hitelesítésszolgáltatóban, amelyet újból felhasználhat. További részletek: [Az OpenSSL konfigurálása az SAP HANA Studio és az SAP HANA-kiszolgálók közötti kommunikációhoz](https://archive.sap.com/documents/docs/DOC-39571). Ha több HANA-kiszolgálóval is rendelkezik, amelyekhez engedélyezi szeretné az SAML SSO-t, győződjön meg róla, hogy mindegyik kiszolgáló megbízik ebben a legfelső szintű hitelesítésszolgáltatóban.

1. Hozza létre az átjáró identitásszolgáltatója X509-tanúsítványát. 

   Egy évig érvényes tanúsítvány-aláírási kérelemnek (IdP_Req.pem) és egy titkos kulcsnak (IdP_Key.pem) a létrehozásához például futtassa a következő parancsot:

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

 1. Írja alá a tanúsítvány-aláírási kérelmet annak a legfelső szintű hitelesítésszolgáltatónak a használatával, amelyet megbízhatóként konfigurált a HANA-kiszolgálókon. 

    Ha például az IdP_Req.pem kérelmet a CA_Cert.pem és CA_Key.pem (a tanúsítvány és a legfelső szintű hitelesítésszolgáltató kulcsa) használatával szeretné aláírni, hajtsa végre a következő parancsot:

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```

     Az eredményül kapott identitásszolgáltatói tanúsítvány egy évig érvényes (lásd a -days kapcsolót). 

Importálja az identitásszolgáltatói tanúsítványát a HANA Studióban egy új SAML-identitásszolgáltató létrehozásához:

1. Az SAP HANA Studio felületén kattintson a jobb gombbal az SAP HANA-kiszolgáló nevére, majd nyissa meg a **Security** &gt; **Open Security Console** &gt; **SAML Identity Provider** &gt; **OpenSSL Cryptographic Library** (Biztonság>Biztonsági konzol megnyitása>SAML-identitásszolgáltató>OpenSSL titkosítási kódtár) elemet.

    ![Identitásszolgáltatók](media/service-gateway-sso-saml/identity-providers.png)

1. Válassza az **Importálás** lehetőséget, keresse meg az IdP_Cert.pem nevű elemet, és importálja azt.

1. Az SAP HANA Studio felületén nyissa meg a **Security** (Biztonság) mappát.

    ![Security mappa](media/service-gateway-sso-saml/security-folder.png)

1. Nyissa meg a **Users** (Felhasználók) menüt, majd válassza ki azt a felhasználót, akihez társítani szeretné a Power BI-felhasználóját.

1. Válassza az **SAML**, majd a **Konfigurálás** lehetőséget.

    ![A SAML konfigurálása](media/service-gateway-sso-saml/configure-saml.png)

1. Válassza ki a 2. lépésben létrehozott identitásszolgáltatót. **Külső identitás** esetén adja meg a Power BI-felhasználó UPN-jét (ez általában az az e-mail-cím, amellyel a felhasználó bejelentkezik a Power BI-ba), majd válassza a **Hozzáadás** lehetőséget. Ha az átjárót az *ADUserNameReplacementProperty* beállítással konfigurálta, akkor meg kell adnia a Power BI-felhasználó eredeti UPN-jét helyettesítő értéket. 

   Ha az *ADUserNameReplacementProperty* alatt például a **SAMAccountName** értéket adja meg, akkor a felhasználóhoz tartozó **SAMAccountName** értéket kell megadnia.

    ![Identitásszolgáltató kiválasztása](media/service-gateway-sso-saml/select-identity-provider.png)

Most, hogy rendelkezik az átjáró beállított tanúsítványával és identitásával, alakítsa át a tanúsítványt pfx-formátumúra, és konfigurálja az átjárót a tanúsítvány használatára:

1. Alakítsa át a tanúsítványt pfx-formátumúra a következő parancs futtatásával. Ez a parancs az eredményül kapott .pfx-fájnak a samlcert.pfx nevet adja, és a *root* jelszót állítja be:

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. Másolja a pfx-fájlt az átjárót tartalmazó számítógépre:

    1. Kattintson duplán a samltest.pfx fájlra, majd válassza a **Helyi gép** &gt; **Tovább** elemet.

    1. Írja be a jelszót, majd válassza a **Tovább** elemet.

    1. Válassza a **Minden tanúsítvány tárolása ebben a tárolóban** lehetőséget, majd kattintson a **Tallózás** &gt; **Személyes** &gt; **OK** elemre.

    1. Válassza a **Tovább**, majd a **Befejezés** gombot.

       ![Tanúsítvány importálása](media/service-gateway-sso-saml/import-certificate.png)

1. Biztosítsa az átjárószolgáltatás-fiók hozzáférését a tanúsítvány titkos kulcsához:

    1. Az átjárót tartalmazó számítógépen futtassa a Microsoft Management Console-t (MMC).

        ![Az MMC futtatása](media/service-gateway-sso-saml/run-mmc.png)

    1. A **Fájl** menüben válassza ki a **Beépülő modul hozzáadása/eltávolítása** elemet.

        ![Beépülő modul hozzáadása](media/service-gateway-sso-saml/add-snap-in.png)

    1. Válassza ki a **Tanúsítványok** &gt; **Hozzáadás** elemet, majd kattintson a **Számítógépfiók** &gt; **Tovább** elemre.

    1. Válassza a **Helyi számítógép** &gt; **Befejezés** &gt; **OK** lehetőséget.

    1. Bontsa a **Tanúsítványok** &gt; **Személyes** &gt; **Tanúsítványok** tartalmát, és keresse meg a tanúsítványt.

    1. Kattintson a jobb gombbal a tanúsítványra, és válassza a **Minden feladat** &gt; **Titkos kulcsok kezelése** elemet.

        ![Titkos kulcsok kezelése](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Adja hozzá az átjárószolgáltatás-fiókot a listához. Alapértelmezés szerint a fiók az **NT SERVICE\PBIEgwService**. Úgy tudhatja meg, hogy melyik fiók futtatja az átjárószolgáltatást, hogy elindítja a **services.msc** parancsot, és megkeresi a **Helyszíni adatátjáró szolgáltatás** bejegyzést.

        ![Átjárószolgáltatás](media/service-gateway-sso-saml/gateway-service.png)

Végül kövesse ezeket a lépéseket a tanúsítvány-ujjlenyomatnak az átjáró konfigurációjához történő hozzáadásához:

1. Az alábbi PowerShell-parancs futtatásával megjelenítheti a számítógépén található tanúsítványokat:

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. Másolja ki az Ön által létrehozott tanúsítvány ujjlenyomatát.

1. Keresse meg az átjáró könyvtárát, amelynek alapértelmezett helye: C:\Program Files\On-premises data gateway.

1. Nyissa meg a PowerBI.DataMovement.Pipeline.GatewayCore.dll.config fájlt, és keresse meg a *SapHanaSAMLCertThumbprint* szakaszt. Illessze be a vágólapra másolt ujjlenyomatot.

1. Indítsa újra az átjárószolgáltatást.

## <a name="running-a-power-bi-report"></a>Power BI-jelentés futtatása

Most már használhatja az **Átjáró kezelése** lapot a Power BI-ban az SAP HANA-adatforrás konfigurálásához. A **Speciális beállítások** szakaszban engedélyezze az egyszeri bejelentkezést az SAML-n keresztül. Ezután közzétehet az adatforráshoz kötődő jelentéseket és adatkészleteket.

   ![Speciális beállítások](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Hibaelhárítás

Az SSO konfigurálása után a következő hibaüzenet jelenhet meg a Power BI-portálon: *A megadott hitelesítő adatok nem használhatók az SapHana forráshoz.* Ez a hiba azt jelenti, hogy az SAP HANA elutasította az SAML-hitelesítő adatokat.

A kiszolgálóoldali hitelesítés követése részletes információt nyújt az SAP HANA hitelesítési hibáinak elhárításához. SAP HANA-kiszolgálójához az alábbi lépések végrehajtásával konfigurálhat követést:

1. Az SAP HANA-kiszolgálón az alábbi lekérdezés futtatásával kapcsolhatja be a hitelesítés követését:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reprodukálja a problémát.

1. A HANA Studióban nyissa meg a felügyeleti konzolt, majd válassza a **Diagnosztikai fájlok** lapot.

1. Nyissa meg a legújabb indexkiszolgálói nyomkövetést, és keresse meg az *SAMLAuthenticator.cpp* fájlt.

    Itt részletes hibaüzenetet kell találnia, amely megadja a hiba elsődleges okát, például:

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. A hibaelhárítás befejezése után kapcsolja ki a hitelesítés követését az alábbi lekérdezés futtatásával:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Következő lépések

A helyszíni adatátjáróval és a DirectQueryvel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a helyszíni adatátjáró?](/data-integration/gateway/service-gateway-onprem)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
