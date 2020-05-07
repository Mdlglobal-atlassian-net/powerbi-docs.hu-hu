---
title: A Kerberos egyszeri bejelentkezésének használata az SAP BW-hez a CommonCryptoLibbel (sapcrypto.dll)
description: Az SAP BW-kiszolgáló konfigurálása a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez a CommonCryptoLib (sapcrypto.dll) használatával
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 02c8ac991fbf84051ae795ef4a80f2b3dc07a1ce
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "75000181"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>A Kerberos egyszeri bejelentkezésének használata az SAP BW-hez a CommonCryptoLibbel (sapcrypto.dll)

Ez a cikk azt ismerteti, hogy hogyan konfigurálhatja az SAP BW-adatforrást a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez a CommonCryptoLib (sapcrypto.dll) használatával.

> [!NOTE]
> Mielőtt megpróbál frissíteni egy Kerberos SSO-t használó, SAP BW-alapú jelentést, végezze el a jelen cikkben szereplő mindkét lépést, valamint [A Kerberos SSO konfigurálása](service-gateway-sso-kerberos.md) című cikkben szereplő lépéseket. Ha a CommonCryptoLib az SNC-könyvtára, SSO-kapcsolatokat az SAP BW-alkalmazáskiszolgálóihoz és SAP BW-üzenetkezelési kiszolgálókhoz is használhat.

## <a name="configure-sap-bw-to-enable-sso-using-commoncryptolib"></a>Az SAP BW konfigurálása egyszeri bejelentkezéshez a CommonCryptoLib használatával

> [!NOTE]
> A helyszíni adatátjáró egy 64 bites szoftver, ezért a BW SSO végrehajtásához a CommonCryptoLib (sapcrypto. dll) 64 bites verziójára van szükség. Ha az SSO-kapcsolat átjárón keresztüli létrehozása előtt tesztelni szeretné az SAP BW-kiszolgáló SSO-kapcsolatát az SAP GUI-ban (ez az ajánlott eljárás), a CommonCryptoLib 32 bites verziójára is szüksége lesz, mivel az SAP GUI egy 32 bites szoftver.

1. Ellenőrizze, hogy a BW-kiszolgáló megfelelően van-e konfigurálva a Kerberos CommonCryptoLibbel történő egyszeri bejelentkezéséhez. Ha igen, az SSO-val elérheti a BW-kiszolgálót (közvetlenül vagy egy SAP BW-üzenetkezelési kiszolgálón keresztül) egy CommonCryptoLib használatára konfigurált SAP-eszközzel, például az SAP GUI-val. 

   A telepítés lépéseivel kapcsolatos további információkért lásd: [SAP egyszeri bejelentkezés: Hitelesítés Kerberos/SPNEGO használatával](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). A BW-kiszolgálónak a CommonCryptoLib-et kell használnia a SNC-kódtárként, és egy *CN =* résszel (például: *CN = BW1*) kezdődő SNC-névvel kell rendelkeznie. Az SNC-nevekre vonatkozó követelményekkel (különösképp az SNC/Identity/as paraméter) kapcsolatos további információk: [SNC-paraméterek Kerberos-konfigurációhoz](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/360534094511490d91b9589d20abb49a.html).

1. Ha még nem tette meg, telepítse az [SAP .NET-összekötő](https://support.sap.com/en/product/connectors/msnet.html) x64-es verzióját azon a számítógépen, amelyen az átjáró telepítve van. 
   
   Azt, hogy az összetevő telepítve van-e, úgy ellenőrizheti, ha megkísérel kapcsolódni az átjárót tartalmazó számítógépről a BW-kiszolgálóhoz a Power BI Desktopban. Ha nem tud kapcsolatot létesíteni a 2.0-s implementációval, az azt jelzi, hogy a .NET-összekötő nincs telepítve, vagy nem lett telepítve a globális szerelvény-gyorsítótárba.

1. Ügyeljen rá, hogy az SAP biztonságos bejelentkezési ügyfél (SLC) ne fusson azon a számítógépen, amelyen az átjáró telepítve van. 

   Az SLC olyan módon gyorsítótárazza a Kerberos-jegyeket, amely zavarhatja az átjárók számára a Kerberos használatát az egyszeri bejelentkezéshez. 

1. Ha az SLC telepítve van, távolítsa el azt, vagy lépjen ki az SAP biztonságos bejelentkezési ügyfélből. Kattintson a jobb gombbal a tálcaikonra, és válassza a **Kijelentkezés** és **Kilépés** lehetőséget, mielőtt SSO-kapcsolódást kísérel meg az átjáró használatával. 

   Az SLC nem támogatott a Windows Server rendszerű gépeken. További információt az [SAP 2780475 megjegyzés](https://launchpad.support.sap.com/#/notes/2780475) című cikkben talál (s-felhasználó szükséges hozzá).

   ![SAP biztonságos bejelentkezési ügyfél](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

1. Ha eltávolítja az SLC-t, vagy ha a **Kijelentkezés** és **Kilépés** lehetőséget választotta, nyisson meg egy parancsablakot, és a `klist purge` paranccsal törölje a gyorsítótárazott Kerberos-jegyeket, mielőtt az átjárón keresztül egyszeri bejelentkezést használna.

1. Töltse le a 64 bites CommonCryptoLib (sapcrypto.dll) *8.5.25 vagy újabb* verzióját az SAP Launchpadből, és másolja azt az átjárót tartalmazó számítógép egyik mappájába. Ugyanabban a könyvtárban, ahová a sapcrypto.dll fájlt másolta, hozzon létre egy sapcrypto.ini nevű fájlt a következő tartalommal:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    Az .ini fájl tartalmazza a CommonCryptoLib által az SSO engedélyezéséhez szükséges konfigurációs adatokat az átjárót használó forgatókönyvekben.

    > [!NOTE]
    > Ezeket a fájlokat ugyanazon a helyen kell tárolni; más szóval a _/Path/to/sapcrypto/_ könyvtárnak tartalmaznia kell a sapcrypto.ini és a sapcrypto.dll fájlt is.

    Mind az átjáró-szolgáltatás felhasználójának, mind pedig a Szolgáltatás felhasználó által megszemélyesített Active Directory- (AD-) felhasználónak rendelkeznie kell olvasási és végrehajtási engedélyekkel mindkét fájlhoz. Javasoljuk, hogy az .ini és a .dll kiterjesztésű fájlokra vonatkozó engedélyeket adja meg a Hitelesített felhasználók csoport számára. Tesztelési célból ezeket az engedélyeket explicit módon megadhatja az átjárószolgáltatás felhasználója és a tesztelési Active Directory-felhasználó számára is. Az alábbi képernyőképen a Hitelesített felhasználók csoport számára az **olvasási &amp; végrehajtási** engedélyt adtuk meg a sapcrypto.dll fájlhoz:

    ![Hitelesített felhasználók](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Ha még nincs társítva SAP BW-adatforrás az SSO-csatlakozáshoz használni kívánt átjáróhoz, vegyen fel egyet a Power BI szolgáltatás **Átjárók kezelése** lapján. Ha már van ilyen adatforrása, módosítsa azt: 
    - **Adatforrás típusaként** válassza az **SAP Business Warehouse** lehetőséget, ha létre szeretne hozni egy SSO-kapcsolatot egy BW-alkalmazáskiszolgálóhoz. 
    - Ha létre szeretne hozni egy SSO-kapcsolatot egy BW-üzenetkezelési kiszolgálóhoz, válassza az **SAP Business Warehouse-üzenetkezelési kiszolgáló** lehetőséget.

1. Az **SNC-kódtár** esetében válassza vagy az **SNC\_LIB** vagy az **SNC\_LIB\_64** környezeti változót vagy az **Egyéni** lehetőséget. 

   - Ha az **SNC\_LIB** beállítást választja, akkor az átjárógépen az **SNC\_LIB\_64** környezeti változó értékét a 64 bites sapcrypto.dll fájlnak az átjárógépen található példányára mutató abszolút elérési útra kell beállítania. Például: *C:\Users\Test\Desktop\sapcrypto.dll*.

   - Ha az **Egyéni** lehetőséget választja, illessze be a *sapcrypto.dll* fájl abszolút elérési útját az Egyéni SNC-kódtár elérési útja mezőbe, amely az **Átjárók kezelése** lapon jelenik meg. 

1. Az **SNC-partner neve** beállításnál adja meg a BW-kiszolgáló SNC-nevét. A **Speciális beállítások** területen jelölje be az **Egyszeri bejelentkezés használata Kerberosszal DirectQuery-lekérdezéseknél** jelölőnégyzetet. A többi mezőt úgy töltse ki, mintha egy Windows-hitelesítéses kapcsolatot hozna létre a PBI Desktopból.

1. Hozzon létre egy **CCL\_PROFILE** rendszerkörnyezeti változót, és állítsa be ennek értékeként a sapcrypto.ini fájl elérési útját.

    ![A CCL\_PROFILE rendszerkörnyezeti változó](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    A sapcrypto .dll és .ini kiterjesztésű fájloknak ugyanazon a helyen kell lenniük. A fenti példában a sapcrypto.ini és a sapcrypto.dll is az asztalon van elhelyezve.

1. Indítsa újra az átjárószolgáltatást.

    ![Az átjárószolgáltatás újraindítása](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Power BI-jelentés futtatása](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Hibaelhárítás

Ha nem tudja frissíteni a jelentést a Power BI szolgáltatásban, a probléma diagnosztizálásához használhatja az átjáró nyomkövetését, a CPIC-nyomkövetést és a CommonCryptoLib-nyomkövetést is. Mivel a CPIC-nyomkövetés és a CommonCryptoLib is SAP-termék, a Microsoft nem tud támogatást biztosítani hozzájuk.

### <a name="gateway-logs"></a>Átjárónaplók

1. Reprodukálja a problémát.

2. Nyissa meg az [átjáróalkalmazást](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), és a **Diagnosztika** lapon válassza a **Naplók exportálása** lehetőséget.

      ![Átjárónaplók exportálása](media/service-gateway-sso-kerberos/export-gateway-logs.png)

### <a name="cpic-tracing"></a>CPIC-nyomkövetés

1. A CPIC-nyomkövetés engedélyezéséhez állítsa be a következő két környezeti változót: **CPIC\_TRACE** és **CPIC\_TRACE\_DIR**. 

   Az első változó beállítja a profilelemzési szintet, a második változó pedig beállítja a profilelemzési fájl könyvtárát. A címtárnak olyan helyen kell lennie, amelyet a Hitelesített felhasználók csoport tagjai írhatnak. 
 
2. A **CPIC\_TRACE** értékét állítsa *3*-ra, a **CPIC\_TRACE\_DIR** értékét pedig arra a könyvtárra, amelybe a nyomkövetési fájlokat szeretné írni. Például:

   ![CPIC-nyomkövetés](media/service-gateway-sso-kerberos/cpic-tracing.png)

3. Reprodukálja a problémát, és ellenőrizze, hogy a **CPIC\_TRACE\_DIR** tartalmaz-e profilelemzési fájlokat.
 
    A CPIC-nyomkövetés képes a magasabb szintű problémák, például a sapcrypto.dll kódtár betöltésének sikertelenségének diagnosztizálására. Íme például egy CPIC-nyomkövetési fájlból származó kódrészlet, amelyben egy .dll-betöltési hiba történt:

    ```
    [Thr 7228] *** ERROR => DlLoadLib()==DLENOACCESS - LoadLibrary("C:\Users\test\Desktop\sapcrypto.dll")
    Error 5 = "Access is denied." [dlnt.c       255]
    ```

    Ha ilyen hibát tapasztal, de az olvasási és végrehajtási engedélyeket a sapcrypto.dll és a sapcrypto.ini fájlra vonatkozóan a [fenti szakaszban](#configure-sap-bw-to-enable-sso-using-commoncryptolib) leírtak szerint állította be, akkor próbálja meg ugyanazokat az olvasási és végrehajtási engedélyeket beállítani a fájlokat tartalmazó mappához is.

    Ha továbbra sem tudja betölteni a .dll-fájlt, próbálja meg bekapcsolni [naplózást a fájlra](/windows/security/threat-protection/auditing/apply-a-basic-audit-policy-on-a-file-or-folder). A Windows Eseménynaplóban az eredményül kapott naplók vizsgálata segíthet megállapítani, hogy a fájl miért nem töltődik be. Keresse meg a megszemélyesített Active Directory-felhasználó által kezdeményezett hibabejegyzést. A `MYDOMAIN\mytestuser` megszemélyesített felhasználó esetén például a következőhöz hasonló hibát fog látni a naplóban:

    ```
    A handle to an object was requested.

    Subject:
        Security ID:        MYDOMAIN\mytestuser
        Account Name:       mytestuser
        Account Domain:     MYDOMAIN
        Logon ID:       0xCF23A8

    Object:
        Object Server:      Security
        Object Type:        File
        Object Name:        <path information>\sapcrypto.dll
        Handle ID:      0x0
        Resource Attributes:    -

    Process Information:
        Process ID:     0x2b4c
        Process Name:       C:\Program Files\On-premises data gateway\Microsoft.Mashup.Container.NetFX45.exe

    Access Request Information:
        Transaction ID:     {00000000-0000-0000-0000-000000000000}
        Accesses:       ReadAttributes
                
    Access Reasons:     ReadAttributes: Not granted
                
    Access Mask:        0x80
    Privileges Used for Access Check:   -
    Restricted SID Count:   0
    ```

### <a name="commoncryptolib-tracing"></a>CommonCryptoLib-nyomkövetés 

1. Kapcsolja be a CommonCryptoLib-nyomkövetést úgy, hogy ezeket a sorokat beszúrja a korábban létrehozott sapcrypto.ini fájlba:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

2. A `ccl/trace/directory` beállítást módosítsa arra egy olyan helyre, ahová a Hitelesített felhasználók csoport tagjai írhatnak. 

3. Másik lehetőségként létrehozhat egy új .ini fájlt a viselkedés módosításához. Az sapcrypto.ini és az sapcrypto.dll fájlok könyvtárában hozzon létre egy sectrace.ini nevű fájlt az alábbi tartalommal. Cserélje le a `DIRECTORY` beállítást a számítógép egy olyan helyére, amelybe a Hitelesített felhasználók csoport tagjai írni tudnak:

    ```
    LEVEL = 5
    DIRECTORY = <drive>:\logs\sectrace
    ```

4. Reprodukálja a problémát, és ellenőrizze, hogy a **DIRECTORY** beállításban megadott hely tartalmaz-e nyomkövetési fájlokat. 

5. Ha elkészült, kapcsolja ki a CPIC- és a CCL-nyomkövetést.

    A CommonCryptoLib-nyomkövetésről az [SAP 2491573 megjegyzésben](https://launchpad.support.sap.com/#/notes/2491573) talál további információt (SAP s-felhasználó szükséges).

## <a name="next-steps"></a>Következő lépések

A helyszíni adatátjáróval és a DirectQueryvel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a helyszíni adatátjáró?](/data-integration/gateway/service-gateway-onprem)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
