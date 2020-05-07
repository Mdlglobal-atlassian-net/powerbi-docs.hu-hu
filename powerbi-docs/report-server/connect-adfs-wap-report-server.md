---
title: A Webalkalmazás-proxy és az Active Directory összevonási szolgáltatások használata – Power BI jelentéskészítő kiszolgáló
description: Megtudhatja, hogyan használhatja a Webalkalmazás-proxyt (a WAP-ot) és az Active Directory összevonási szolgáltatásokat (az AD FS-t) a Power BI jelentéskészítő kiszolgálóhoz, valamint az SQL Server Reporting Services (SSRS) 2016-os vagy újabb verzióihoz való csatlakozáshoz.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76042440"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>A Webalkalmazás-proxy és az Active Directory összevonási szolgáltatások használata – Power BI jelentéskészítő kiszolgáló

Ez a cikk azt ismerteti, hogyan használhatja a Webalkalmazás-proxyt (a WAP-ot) és az Active Directory összevonási szolgáltatásokat (az AD FS-t) a Power BI jelentéskészítő kiszolgálóhoz, valamint az SQL Server Reporting Services (SSRS) 2016-os vagy újabb verzióihoz való csatlakozáshoz. Ezzel az integrációval a vállalati hálózaton kívül tartózkodó felhasználók hozzáférhetnek a Power BI jelentéskészítő kiszolgáló és a Reporting Services jelentéseihez az ügyfélböngészőikben, és AD FS-előhitelesítéssel védhetők. Power BI-mobilalkalmazások esetében [az OAuth-t is konfigurálnia kell a Power BI jelentéskészítő kiszolgálóhoz és az SSRS-hez való kapcsolódáshoz](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Előfeltételek

### <a name="domain-name-services-dns-configuration"></a>A tartománynév-szolgáltatások (DNS) konfigurációja

- Határozza meg azt a nyilvános URL-címet, amelyhez a felhasználó csatlakozni fog. A következő példához hasonló lehet: `https://reports.contosolab.com`.
- Konfigurálja az állomásnévhez tartozó DNS-rekordot (példa: `reports.contosolab.com`) úgy, hogy a Webalkalmazás-proxy (WAP) kiszolgálójának nyilvános IP-címére mutasson.
- Konfiguráljon egy nyilvános DNS-rekordot az AD FS-kiszolgálóhoz. Elképzelhető például, hogy az alábbi URL-címmel konfigurálta az AD FS-kiszolgálót: `https://adfs.contosolab.com`.
- Konfigurálja a DNS-rekordot úgy, hogy a Webalkalmazás-proxy (WAP) kiszolgálójának nyilvános IP-címére mutasson. Példa: `adfs.contosolab.com`. Ez a WAP-alkalmazás részeként van közzétéve.

### <a name="certificates"></a>Tanúsítványok

A WAP-alkalmazáshoz és az AD FS-kiszolgálóhoz is konfigurálnia kell tanúsítványt. Mindkét tanúsítványnak egy érvényes, a gépek által felismert, érvényes hitelesítésszolgáltatóhoz kell tartoznia.

## <a name="1-configure-the-report-server"></a>1. A jelentéskészítő kiszolgáló konfigurálása

Meg kell győződnünk arról, hogy az egyszerű szolgáltatásnév (SPN) érvényes. Az érvényes egyszerű szolgáltatásnév lehetővé teszi, hogy megfelelő Kerberos-hitelesítés történjen, és hogy a jelentéskészítő kiszolgáló egyeztetni tudja a hitelesítést.

### <a name="service-principal-name-spn"></a>Egyszerű szolgáltatásnév (SPN)

Az SPN egy egyedi azonosító egy Kerberos-hitelesítést használó szolgáltatáshoz. Mindenképpen szüksége van egy megfelelő HTTP SPN-re a jelentéskészítő kiszolgálón.

Információk a megfelelő egyszerű szolgáltatásnév (SPN) konfigurálásáról a jelentéskészítő kiszolgálón: [Egyszerű szolgáltatásnév (SPN) regisztrálása egy jelentéskészítő kiszolgálóhoz](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Egyeztetéses hitelesítés engedélyezése

Ha engedélyezni szeretné a Kerberos-hitelesítés használatát, konfigurálnia kell a hitelesítés típusát a jelentéskészítő kiszolgálón RSWindowsNegotiate értékre. Ezt az rsreportserver.config fájlban konfigurálhatja.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

További információk: [Reporting Services konfigurációs fájl módosítása](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) és [Windows-hitelesítés konfigurálása egy jelentéskészítő kiszolgálón](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Az Active Directory összevonási szolgáltatások (AD FS) konfigurálása

Konfigurálnia kell az AD FS-t egy, a környezetben lévő Windows 2016-kiszolgálón. Ez konfigurálás a Kiszolgálókezelőben végezhető el a Kezelés területen a Szerepkörök és szolgáltatások hozzáadása lehetőség kiválasztásával. További információk: [Active Directory összevonási szolgáltatások](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

Hajtsa végre a következő lépéseket a AD FS-kiszolgálón az AD FS-kezelő alkalmazással.

1. Kattintson a jobb gombbal a **Megbízható függő entitások** > **Megbízható függő entitás hozzáadása** lehetőségre.

    ![Megbízható függő entitások hozzáadása](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Kövesse a **Megbízható függő entitás hozzáadása** varázsló lépéseit.

    Válassza a **Nem jogcímbarát** lehetőséget a Windows beépített biztonsági szolgáltatásainak hitelesítési mechanizmusként való használatához.

    ![Üdvözöljük a Megbízható függő entitások hozzáadása varázslóban](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Adja meg a preferált nevet a **Megjelenített név meghatározása** mezőben, majd válassza a **Tovább** lehetőséget.
    Adja meg a megbízható függő entitás azonosítóját: `<ADFS\_URL>/adfs/services/trust`

    Példa: `https://adfs.contosolab.com/adfs/services/trust`

    ![Jelentéskészítő kiszolgáló](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Válassza a vállalat igényeinek megfelelő **Hozzáférés-vezérlési házirendet**, majd válassza a **Tovább** lehetőséget.

    ![Hozzáférés-vezérlés kiválasztása](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Válassza a **Tovább**, majd a **Befejezés** lehetőséget a **Megbízható függő entitás hozzáadása** varázsló befejezéséhez.

    Ha elkészült, a Megbízható függő entitások tulajdonságainak a következőkhöz hasonlóknak kell lenniük.

    ![Megbízható függő entitások](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Webalkalmazás-proxy (WAP) konfigurálása

Érdemes engedélyeznie a Webalkalmazás-proxy (szerepkör) Windows-szerepkört a környezete egy kiszolgálóján. Ennek egy Windows Server 2016-on kell lennie. További információ: [Webalkalmazás-proxy a Windows Server 2016-ban](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) és [Alkalmazások közzététele AD FS előhitelesítéssel](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Korlátozott delegálás konfigurálása

Az Űrlapos hitelesítésről Windows-hitelesítésre váltáshoz korlátozott delegálást kell használnia protokollváltással. Ez a lépés a Kerberos-konfiguráció részét képezi. A jelentéskészítő kiszolgáló SPN-jét már definiáltuk a jelentéskészítő kiszolgáló konfigurációjában.

A korlátozott delegálást konfigurálnunk kell a WAP-kiszolgáló gép Active Directory-fiókjában. Ha nem rendelkezik Active Directory-jogosultságokkal, szüksége lehet egy tartományi rendszergazda segítségére.

A korlátozott delegálás konfigurálásához kövesse az alábbi lépéseket.

1. Indítsa el az **Active Directory – felhasználók és számítógépek** elemet egy olyan számítógépen, ahol telepítve vannak az Active Directory-eszközök.
2. Keresse meg a WAP-kiszolgálóhoz tartozó számítógépfiókot. Alapértelmezés szerint ez a **Számítógépek** tárolóban van.
3. Kattintson a jobb gombbal a WAP-kiszolgálóra, és lépjen a **Tulajdonságok** elemhez.
4. A **Delegáció** lapon válassza **A számítógépen csak a megadott szolgáltatások delegálhatók**, majd a **Bármely hitelesítési protokoll használatával** elemet.

    ![A számítógép megbízható](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Ez a lehetőség állítja be a korlátozott delegálást ehhez a WAP-kiszolgálói számítógépfiókhoz. Ezután meg kell adnunk a szolgáltatásokat, amelyekre ez a számítógép delegálhat.
2. Válassza a **Hozzáadás** lehetőséget a szolgáltatások panelen.

    ![AD FS megbízhatósági kapcsolatának hozzáadása](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Válassza a **Felhasználók vagy számítógépek** elemet.
2. Adja meg a jelentéskészítő kiszolgálóhoz használt szolgáltatásfiókot. Ez a fiók ugyanaz, mint amelyet a HTTP SPN hozzáadásához használt a [jelentéskészítő kiszolgáló konfigurálására](#1-configure-the-report-server) vonatkozó korábbi szakaszban. 

3. Válassza ki a jelentéskészítő kiszolgáló HTTP SPN-jét, majd válassza az **OK** lehetőséget.

    > [!NOTE]
    > Elképzelhető, hogy csak a NetBIOS SPN-t látja. Igazából a NetBIOS és a teljes tartományneves SPN-t is ki fogja választani a rendszer, ha mindkettő létezik.

1. Ha bejelölte a **Kibontott** jelölőnégyzetet, az eredménynek a következő példához hasonlóan kell kinéznie.

    ![WAP-tulajdonságok](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>WAP-alkalmazás hozzáadása

1. A webalkalmazásproxy-kiszolgálón nyissa meg a **Távelérés-kezelés** konzolját, majd válassza a **Webalkalmazás-proxy** lehetőséget a navigációs panelen. 

2. A **Feladatok** panelen válassza a **Közzététel** lehetőséget.

2. A Kezdőlapon válassza a **Tovább** lehetőséget.

    ![A Közzététel kezdőoldala](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. Az **Előhitelesítés** lapon válassza az **Active Directory összevonási szolgáltatások (AD FS)** , majd a **Következő** lehetőséget.

    ![Előhitelesítés](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Válassza a **Web és MSOFBA** előhitelesítési lehetőséget, mivel csak a böngészőalapú hozzáférést fogjuk beállítani a jelentéskészítő kiszolgálóhoz, a mobilalkalmazás-hozzáférést nem.

    ![Támogatott kliensek](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Adja hozzá az AD FS-kiszolgálón létrehozott **Függő entitást** az alább látható módon, majd válassza a **Tovább** lehetőséget.

    ![Függő entitás közzététele](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. A **Külső URL-cím** szakaszban adja meg a WAP-kiszolgálón konfigurált nyilvánosan elérhető URL-címet. Adja hozzá a jelentéskészítő kiszolgálón (a Jelentéskészítő kiszolgáló – konfigurációkezelőben) konfigurált URL-címet a **Háttérkiszolgáló URL-címe** szakaszban az alább látható módon. Adja hozzá a jelentéskészítő kiszolgáló egyszerű szolgáltatásnevét a **Háttérkiszolgáló egyszerű szolgáltatásneve** szakaszban.

    ![Közzétételi beállítások](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Válassza a **Tovább**, majd a **Közzététel** lehetőséget.
8. Futtassa a következő PowerShell-parancsot a WAP-konfiguráció ellenőrzéséhez.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![PowerShell-parancs](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Kapcsolódás a jelentéskészítő kiszolgálóhoz a böngészőben

Ezután hozzáférhet a nyilvános WAP URL-címhez a böngészőben, például a `https://reports.contosolab.com/ReportServer` címen a webszolgáltatás, és a `https://reports.contosolab.com/Reports` címen a webportál esetében. A sikeres hitelesítés után megtekintheti a jelentéseket.

![AD FS-bejelentkezés](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Következő lépések

* [Az OAuth konfigurálása a Power BI jelentéskészítő kiszolgálóhoz és az SSRS-hez való kapcsolódáshoz](../consumer/mobile/mobile-oauth-ssrs.md)
*[Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

