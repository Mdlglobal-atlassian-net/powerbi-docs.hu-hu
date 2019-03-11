---
title: Az SAML használata a helyszíni adatforrásokba történő egyszeri bejelentkezéshez (SSO)
description: Az átjáró konfigurálása a Security Assertion Markup Language (SAML) használatával a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezés (SSO) engedélyezéséhez.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 03/05/2019
LocalizationGroup: Gateways
ms.openlocfilehash: c1ca797efa2e40bf74384a1e9f2362acd26c6f8f
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555661"
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

    Ezek a beállítási lépések OpenSSL helyett az SAP titkosítási kódtárral (Cryptographic Library, más néven CommonCryptoLib vagy sapcrypto) is végrehajthatók. További információkat a hivatalos SAP-dokumentációban találhat.

1. Válassza ki az **Import** (Importálás) lehetőséget, keresse meg a samltest.crt nevű elemet, és importálja.

    ![Identitásszolgáltatók](media/service-gateway-sso-saml/identity-providers.png)

1. Az SAP HANA Studio felületén nyissa meg a **Security** (Biztonság) mappát.

    ![Security mappa](media/service-gateway-sso-saml/security-folder.png)

1. Nyissa meg a **Users** (Felhasználók) menüt, majd válassza ki azt a felhasználót, akihez társítani szeretné a Power BI-felhasználóját.

1. Válassza ki a **SAML** majd a **Configure** (Konfigurálás) elemet.

    ![A SAML konfigurálása](media/service-gateway-sso-saml/configure-saml.png)

1. Válassza ki a 2. lépésben létrehozott identitásszolgáltatót. Az **External Identity** (Külső identitás) esetén adja meg a Power BI-felhasználó egyszerű felhasználónevét, majd kattintson az **Add** (Hozzáadás) parancsra.

    ![Identitásszolgáltató kiválasztása](media/service-gateway-sso-saml/select-identity-provider.png)

Most, hogy rendelkezik a beállított tanúsítvánnyal és identitással, alakítsa át a tanúsítványt pfx-formátumúra, és konfigurálja az átjárót tartalmazó számítógépet a tanúsítvány használatára.

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

## <a name="troubleshooting"></a>Hibaelhárítás

Az SSO konfigurálása után a következő hibaüzenet jelenhet meg a Power BI-portálon: „A megadott hitelesítő adatok nem használhatók az SapHana forráshoz.” Ez a hiba azt jelenti, hogy az SAP HANA elutasította az SAML-hitelesítő adatokat.

A hitelesítés követése részletes információt nyújt az SAP HANA hitelesítési hibáinak elhárításához. SAP HANA-kiszolgálójához az alábbi lépések végrehajtásával konfigurálhat követést.

1. Az SAP HANA-kiszolgálón az alábbi lekérdezés futtatásával kapcsolhatja be a hitelesítés követését.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reprodukálja a felmerült hibát.

1. A HANA Studióban nyissa meg a felügyeleti konzolt, majd lépjen a **Diagnosztikai fájlok** lapra.

1. Nyissa meg a legújabb indexkiszolgálói nyomkövetést, és keresse meg a SAMLAuthenticator.cpp fájlt.

    Itt részletes hibaüzenetet kell találnia, amely az alábbi példához hasonlóan megadja a hiba elsődleges okát.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. A hibaelhárítás befejezése után kapcsolja ki a hitelesítés követését az alábbi lekérdezés futtatásával.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Következő lépések

A **helyszíni adatátjáróval** és a **DirectQueryvel** kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Helyszíni adatátjáró](service-gateway-onprem.md)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
