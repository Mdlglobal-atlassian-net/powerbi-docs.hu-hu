---
title: Az SAML használata a helyszíni adatforrásokba történő egyszeri bejelentkezéshez (SSO)
description: Az átjáró konfigurálása a Security Assertion Markup Language (SAML) használatával a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezés (SSO) engedélyezéséhez.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 8762e575574b717965ac55d4cf32a5c925c298ab
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507784"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>A Security Assertion Markup Language (SAML) használata a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezéshez (SSO)

Használhatja a [Security Assertion Markup Language- (SAML-)](https://www.onelogin.com/pages/saml) protokollt a közvetlen SSO-kapcsolat engedélyezéséhez. Az SSO engedélyezése egyszerűvé teszi a Power BI-jelentések és -irányítópultok számára az adatok helyszíni forrásokból történő frissítését.

## <a name="supported-data-sources"></a>Támogatott adatforrások

Jelenleg az SAP HANA használata támogatott a SAML-protokoll esetén. További információt az egyszeri bejelentkezés a SAML használatával az SAP HANA rendszerhez történő beállításáról és konfigurálásáról a [SAML-alapú a BI Platformhoz történő egyszeri bejelentkezést a HANA használatakor](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) ismertető témakörben talál az SAP HANA dokumentációjában.

További adatforrásokat a [Kerberos](service-gateway-sso-kerberos.md) használata esetén támogatunk.

## <a name="configuring-the-gateway-and-data-source"></a>Az átjáró és az adatforrás konfigurálása

A SAML használatához először hozzon létre egy tanúsítványt a SAML-identitásszolgáltató számára, majd társítson egy Power BI-felhasználót az identitáshoz.

1. Állítson elő egy tanúsítványt. Győződjön meg arról, hogy az SAP HANA-kiszolgáló teljes tartománynevét (FQDN) használja a *köznapi név* kitöltése során. A tanúsítvány 365 nap után jár le.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. Az SAP HANA Studio felületén kattintson a jobb gombbal az SAP HANA-kiszolgáló mezőjére, majd nyissa meg a **Security** > **Open Security Console** > **SAML Identity Provider** > **OpenSSL Cryptographic Library** (Biztonság>Biztonsági konzol megnyitása>SAML-identitásszolgáltató>OpenSSL titkosítási kódtár) elemet.

1. Válassza ki az **Import** (Importálás) lehetőséget, keresse meg a samltest.crt nevű elemet, és importálja.

    ![Identitásszolgáltatók](media/service-gateway-sso-saml/identity-providers.png)

1. Az SAP HANA Studio felületén nyissa meg a **Security** (Biztonság) mappát.

    ![Security mappa](media/service-gateway-sso-saml/security-folder.png)

1. Nyissa meg a **Users** (Felhasználók) menüt, majd válassza ki azt a felhasználót, akihez társítani szeretné a Power BI-felhasználóját.

1. Válassza ki a **SAML** majd a **Configure** (Konfigurálás) elemet.

    ![A SAML konfigurálása](media/service-gateway-sso-saml/configure-saml.png)

1. Válassza ki a 2. lépésben létrehozott identitásszolgáltatót. Az **External Identity** (Külső identitás) esetén adja meg a Power BI-felhasználó egyszerű felhasználónevét, majd kattintson az **Add** (Hozzáadás) parancsra.

    ![Identitásszolgáltató kiválasztása](media/service-gateway-sso-saml/select-identity-provider.png)

Ezután ellenőrizze a beállítást egy *SAML assertion* (SAML-helyességifeltétel) és az [xmlsec1](http://sgros.blogspot.com/2013/01/signing-xml-document-using-xmlsec1.html) eszköz használatával.

1. Mentse az alábbi helyességi feltételt assertion-template.xml néven. Cserélje le a \<MyUserId\> nevet a Power BI-felhasználó egyszerű felhasználónevére, amelyet a 7. pontban adott meg.

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <saml2:Assertion ID="Assertion12345789" IssueInstant="2015-07-16T04:47:49.858Z" Version="2.0" xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
      <saml2:Issuer></saml2:Issuer> 
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
          <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
          <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
          <Reference URI="">
            <Transforms>
              <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
              <Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            </Transforms>
            <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue />
          </Reference>
        </SignedInfo>
        <SignatureValue />
        <KeyInfo>
          <X509Data />
        </KeyInfo>
      </Signature>
      <saml2:Subject>
        <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified"><MyUserId></saml2:NameID>
      </saml2:Subject>
      <saml2:Conditions NotBefore="2010-01-01T00:00:00Z" NotOnOrAfter="2050-01-01T00:00:00Z"/>
    </saml2:Assertion>
    ```

1. Futtassa a következő parancsot. A saltest.key és a samltest.crt az 1. lépésben létrehozott kulcs és tanúsítvány.

    ```
    xmlsec1 --sign --privkey-pem samltest.key, samltest.crt --output signed.xml assertion-template.xml
    ```

1. Az SAP HANA Studio felületén nyissa meg a SQL-konzolablakot, és futtassa a következő parancsot. Cserélje le a \<SAMLAssertion\> értékét az előző lépés XML-jének tartalmára.

    ```SQL
    CONNECT WITH SAML ASSERTION '<SAMLAssertion>'
    ```

Ha a lekérdezés sikeres, az azt jelenti, hogy az SAP HANA SAML SSO-beállítása sikeres.

Most, hogy rendelkezik a sikeresen beállított tanúsítvánnyal és identitással, alakítsa át a tanúsítványt pfx-formátumúra, és konfigurálja az átjárót tartalmazó számítógépet a tanúsítvány használatára.

1. Alakítsa át a tanúsítványt pfx-formátumúra a következő parancs futtatásával.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. Másolja a pfx-fájlt az átjárót tartalmazó számítógépre:

    1. Kattintson duplán a samltest.pfx fájlra, majd válassza a **Helyi gép** > **Tovább** elemet.

    1. Írja be a jelszót, majd válassza a **Tovább** elemet.

    1. Válassza a **Minden tanúsítvány tárolása ebben a tárolóban** lehetőséget, majd kattintson a **Tallózás** > **Személyes** > **OK** elemre.

    1. Kattintson a **Tovább**, majd a **Befejezés** gombra.

    ![Tanúsítvány importálása](media/service-gateway-sso-saml/import-certificate.png)

1. Biztosítsa az átjárószolgáltatás-fiók hozzáférését a tanúsítvány titkos kulcsához:

    1. Az átjárót tartalmazó számítógépen futtassa a Microsoft Management Console-t (MMC).

        ![Az MMC futtatása](media/service-gateway-sso-saml/run-mmc.png)

    1. A **Fájl** menüben válassza ki a **Beépülő modul hozzáadása/eltávolítása** elemet.

        ![Beépülő modul hozzáadása](media/service-gateway-sso-saml/add-snap-in.png)

    1. Válassza ki a **Tanúsítványok** > **Hozzáadás** elemet, majd kattintson a **Számítógép-fiók** > **Tovább** elemre.

    1. Kattintson a **Helyi számítógép** > **Befejezés** > **OK** elemre.

    1. Bontsa a **Tanúsítványok** > **Személyes** > **Tanúsítványok** tartalmát, és keresse meg a tanúsítványt.

    1. Kattintson a jobb gombbal a tanúsítványra, és válassza a **Minden feladat** > **Titkos kulcsok kezelése** elemet.

        ![Titkos kulcsok kezelése](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Adja hozzá az átjárószolgáltatás-fiókot a listához. Alapértelmezés szerint a fiók az **NT SERVICE\PBIEgwService**. Úgy tudhatja meg, hogy melyik fiók futtatja az átjárószolgáltatást, hogy elindítja a **services.msc** parancsot, és megkeresi a **Helyszíni adatátjáró szolgáltatás** bejegyzést.

        ![Átjárószolgáltatás](media/service-gateway-sso-saml/gateway-service.png)

Végül kövesse ezeket a lépéseket a tanúsítvány-ujjlenyomat az átjáró konfigurációjához történő hozzáadásához.

1. Az alábbi PowerShell-parancs futtatásával megjelenítheti a számítógépén található tanúsítványokat.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Másolja ki az Ön által létrehozott tanúsítvány ujjlenyomatát.

1. Keresse meg az átjáró könyvtárát, amelynek alapértelmezett helye: C:\Program Files\On-premises data gateway.

1. Nyissa meg a PowerBI.DataMovement.Pipeline.GatewayCore.dll.config fájlt, és keresse meg a \*SapHanaSAMLCertThumbprint\* szakaszt. Illessze be a vágólapra másolt ujjlenyomatot.

1. Indítsa újra az átjárószolgáltatást.

## <a name="running-a-power-bi-report"></a>Power BI-jelentés futtatása

Most már használhatja az **Átjáró kezelése** lapot a Power BI-ban az adatforrás konfigurálásához, a **Speciális beállítások** alatt pedig engedélyezze az SSO-t. Ezután közzétehet az adatforráshoz kötődő jelentéseket és adatkészleteket.

![Speciális beállítások](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="next-steps"></a>Következő lépések

A **helyszíni adatátjáróval** és a **DirectQueryvel** kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Helyszíni adatátjáró](service-gateway-onprem.md)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)