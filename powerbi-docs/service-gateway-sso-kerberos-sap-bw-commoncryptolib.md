---
title: A Kerberos egyszeri bejelentkezésének használata az SAP BW-hez a CommonCryptoLibbel (sapcrypto.dll)
description: Az SAP BW-kiszolgáló konfigurálása a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez a CommonCryptoLib (sapcrypto.dll) használatával
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c4f2b0d8856d5e68e02b9b33cf393ca85ecb580
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106285"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>A Kerberos egyszeri bejelentkezésének használata az SAP BW-hez a CommonCryptoLibbel (sapcrypto.dll)

Ez a cikk azt ismerteti, hogy hogyan konfigurálhatja az SAP BW-kiszolgálót a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez a CommonCryptoLib (sapcrypto.dll) használatával.

> [!NOTE]
> Egy Kerberos SSO-t használó, SAP BW-alapú jelentés frissítése előtt végezze el ezen, valamint a [Kerberos SSO konfigurálását ismertető](service-gateway-sso-kerberos.md) cikk lépéseit. Ha a CommonCryptoLib az SNC-könyvtára, SSO-kapcsolatokat az SAP BW-alkalmazáskiszolgálóihoz és SAP BW-üzenetkezelési kiszolgálókhoz is használhat.

## <a name="configure-sap-bw-server-to-enable-sso-using-commoncryptolib"></a>Az SAP BW-kiszolgáló konfigurálása egyszeri bejelentkezéshez a CommonCryptoLib használatával

> [!NOTE]
> A helyszíni adatátjáró egy 64 bites szoftver, ezért a CommonCryptoLib (sapcrypto. dll) 64 bites verzióját igényli. Ha az SSO-kapcsolat átjárón keresztüli létrehozása előtt tesztelni szeretné az SAP BW-kiszolgáló SSO-kapcsolatát az SAP GUI-ban (ez az ajánlott eljárás), a CommonCryptoLib 32 bites verziójára is szüksége lesz, mivel az SAP GUI 32 bites szoftver.

1. Ellenőrizze, hogy a BW-kiszolgáló megfelelően van-e konfigurálva a Kerberos CommonCryptoLibbel történő egyszeri bejelentkezéséhez. Ha igen, az SSO-val elérheti a BW-kiszolgálót (közvetlenül vagy egy SAP BW-üzenetkezelési kiszolgálón keresztül) egy CommonCryptoLib használatára konfigurált SAP-eszközzel, például az SAP GUI-val. A telepítés lépéseivel kapcsolatos további információkért lásd: [SAP egyszeri bejelentkezés: Hitelesítés Kerberos/SPNEGO használatával](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). A BW-kiszolgálónak a CommonCryptoLib-et kell használnia a SNC-kódtárként, és rendelkeznie kell egy „CN =” résszel (például: „CN = BW1”) kezdődő SNC-névvel. Az SNC-nevekre vonatkozó követelményekkel kapcsolatos további információkért lásd: [SNC-paraméterek Kerberos-konfigurációhoz](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (különösképp az SNC/Identity/as paraméter).

1. Ha még nem tette meg, telepítse az [SAP .NET-összekötő](https://support.sap.com/en/product/connectors/msnet.html) x64-es verzióját azon a számítógépen, amelyen az átjáró telepítve van. Azt, hogy az összetevő telepítve van-e, úgy ellenőrizheti, ha a BW-kiszolgálóhoz megpróbál kapcsolódni a Power BI Desktopban. Ha nem tud kapcsolatot létesíteni a 2.0-ás implementációval, a .NET-összekötő nincs telepítve.

1. Ügyeljen rá, hogy az SAP biztonságos bejelentkezési ügyfél (SLC) ne fusson azon a számítógépen, amelyen az átjáró telepítve van. Az SLC olyan módon gyorsítótárazza a Kerberos-jegyeket, amely zavarhatja az átjárók számára a Kerberos használatát az egyszeri bejelentkezéshez. Ha az SLC telepítve van, távolítsa el, vagy lépjen ki az SAP biztonságos bejelentkezési ügyfélből: kattintson a jobb gombbal a tálcán található ikonra, és válassza a Kijelentkezés és Kilépés lehetőséget, mielőtt az átjáróval egyszeri bejelentkezést használna. Az SLC nem támogatott a Windows Server rendszerű gépeken. További információt az [SAP 2780475 megjegyzés](https://launchpad.support.sap.com/#/notes/2780475) című cikkben talál (s-felhasználó szükséges hozzá).

    ![SAP biztonságos bejelentkezési ügyfél](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Ha eltávolítja az SLC-t, vagy ha a **Kijelentkezés** és **Kilépés** lehetőséget választotta, nyisson meg egy parancsablakot, és a `klist purge` paranccsal törölje a gyorsítótárazott Kerberos-jegyeket, mielőtt az átjárón keresztül egyszeri bejelentkezést használna.

1. Töltse le a 64 bites CommonCryptoLib (sapcrypto.dll) **8.5.25 vagy újabb** verzióját az SAP Launchpadből, és másolja azt az átjárót tartalmazó számítógép egyik mappájába. Ugyanabban a könyvtárban, ahová a sapcrypto.dll fájlt másolta, hozzon létre egy sapcrypto.ini nevű fájlt a következő tartalommal:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    Az .ini fájl tartalmazza a CommonCryptoLib által az SSO engedélyezéséhez szükséges konfigurációs adatokat az átjárót használó forgatókönyvekben.

    > [!NOTE]
    > Ezeket a fájlokat ugyanazon a helyen kell tárolni; más szóval a _/Path/to/sapcrypto/_ könyvtárnak tartalmaznia kell a sapcrypto.ini és a sapcrypto.dll fájlt is.

    Mind az átjáró-szolgáltatás felhasználójának, mind pedig a Szolgáltatás felhasználó által megszemélyesített Active Directory- (AD-) felhasználónak rendelkeznie kell olvasási és végrehajtási engedélyekkel mindkét fájlhoz. Javasoljuk, hogy az .ini és a .dll kiterjesztésű fájlokra vonatkozó engedélyeket adja meg a Hitelesített felhasználók csoport számára. Tesztelési célból ezeket az engedélyeket explicit módon megadhatja az átjáró Szolgáltatás felhasználója és a tesztelési Active Directory-felhasználó számára is. Az alábbi képernyőképen a Hitelesített felhasználók csoport számára **olvasási &amp; végrehajtási** engedélyeket adtuk meg a sapcrypto.dll fájlhoz:

    ![Hitelesített felhasználók](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Ha nem rendelkezik SAP BW-kiszolgálói adatforrással, a Power BI szolgáltatás **Átjárók kezelése** lapján adjon hozzá egy adatforrást. Ha már rendelkezik olyan BW-adatforrással, amely ahhoz az átjáróhoz van társítva, amelyen az SSO-csatlakozást szeretné használni, készítse elő szerkesztésre. **Adatforrás típusaként** válassza az **SAP Business Warehouse** lehetőséget, ha létre szeretne hozni egy SSO-kapcsolatot egy BW-alkalmazáskiszolgálóhoz. Ha létre szeretne hozni egy SSO-kapcsolatot egy BW-üzenetkezelési kiszolgálóhoz, válassza az **SAP Business Warehouse-üzenetkezelési kiszolgáló** lehetőséget.

    Az **SNC-kódtár** esetében válassza vagy az **SNC\_LIB vagy az SNC\_LIB\_64 környezeti változót** vagy az **Egyéni** lehetőséget. Ha az **SNC\_LIB** beállítást választja, akkor az átjárógépen az **SNC\_LIB\_64** környezeti változó értékét a 64 bites sapcrypto.dll fájlnak az átjárógépen található példányára mutató abszolút elérési útra kell beállítania, ami lehet például: C:\Users\Test\Desktop\sapcrypto.dll. Ha az **Egyéni** lehetőséget választja, illessze be a sapcrypto.dll fájl abszolút elérési útját az egyéni SNC-kódtár elérési útja mezőbe, amely az **Átjárók kezelése** oldalon jelenik meg. Az **SNC-partner neve** beállításnál adja meg a BW-kiszolgáló SNC-nevét. A **Speciális beállítások** területen jelölje be az **Egyszeri bejelentkezés használata Kerberosszal DirectQuery-lekérdezéseknél** jelölőnégyzetet. A többi mezőt úgy kell kitöltenie, mintha egy Windows-hitelesítéses kapcsolatot hozna létre a PBI Desktopból.

1. Hozzon létre egy CCL\_PROFILE rendszerkörnyezeti változót, amely a sapcrypto.ini fájlra mutat:

    ![A CCL\_PROFILE rendszerkörnyezeti változó](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Ne feledje, hogy a sapcrypto .dll és .ini kiterjesztésű fájloknak ugyanazon a helyen kell lenniük. A fenti példában az sapcrypto.ini az asztalon található, ezért a sapcrypto.dll fájlt is az asztalon kell elhelyezni.

1. Indítsa újra az átjárószolgáltatást:

    ![Az átjárószolgáltatás újraindítása](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Power BI-jelentés futtatása](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Hibaelhárítás

Ha nem tudja frissíteni a jelentést a Power BI szolgáltatásban, a probléma diagnosztizálásához használhatja az átjáró nyomkövetését, a CPIC-nyomkövetést és a CommonCryptoLib-nyomkövetést is. A CPIC-nyomkövetés és a CommonCryptoLib SAP-termékek, így a Microsoft nem tud közvetlen támogatást biztosítani hozzájuk. Azon Active Directory felhasználók számára, akik SSO-hozzáférést kapnak a BW-hez, egyes Active Directory konfigurációknál előfordulhat, hogy a felhasználóknak a rendszergazdák csoport tagjainak kell lenniük azon a gépen, amelyen az átjáró telepítve van.

1. **Átjárónaplók:** Reprodukálja a problémát, nyissa meg az [átjáró alkalmazást](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), lépjen a **Diagnosztika** lapra, és válassza a **Naplók exportálása** lehetőséget:

    ![Átjárónaplók exportálása](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **CPIC-nyomkövetés:** A CPIC-nyomkövetés engedélyezéséhez állítsa be a következő két környezeti változót: CPIC\_TRACE és CPIC\_TRACE\_DIR. Az első változó beállítja a nyomkövetési szintet, a második változó pedig beállítja a nyomkövetési fájl könyvtárát. A címtárnak olyan helyen kell lennie, amelyet a Hitelesített felhasználók csoport tagjai írhatnak. A CPIC\_TRACE értékét állítsa 3-ra, a CPIC\_TRACE\_DIR értékét pedig arra a könyvtárra, amelybe a nyomkövetési fájlokat szeretné írni.

    ![CPIC-nyomkövetés](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Reprodukálja a problémát, és ellenőrizze, hogy a CPIC\_TRACE\_DIR tartalmaz-e nyomkövetési fájlokat.

1. **CommonCryptoLib-nyomkövetés:** Kapcsolja be a CommonCryptoLib-nyomkövetést úgy, hogy két sort ad hozzá a korábban létrehozott sapcrypto.ini fájlhoz:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    Fontos, hogy a _ccl/trace/directory_ beállítást olyan hely megadásával módosítsa, amelyre a Hitelesített felhasználók csoport tagjai írni tudnak. Másik lehetőségként létrehozhat egy új .ini fájlt a viselkedés módosításához. Az sapcrypto.ini és az sapcrypto.dll fájlok könyvtárában hozzon létre egy sectrace.ini nevű fájlt az alábbi tartalommal. Cserélje le a DIRECTORY beállítást a számítógépének egy olyan helyére, amelyet a Hitelesített felhasználó írni tud:

    ```
    LEVEL = 5

    DIRECTORY = <drive>:\logs\sectrace
    ```

    Most reprodukálja a problémát, és ellenőrizze, hogy a DIRECTORY beállításban megadott hely tartalmaz-e nyomkövetési fájlokat. Ha elkészült, kapcsolja ki a CPIC- és a CCL-nyomkövetést.

    A CommonCryptoLib-nyomkövetésről az [SAP 2491573 megjegyzésben](https://launchpad.support.sap.com/#/notes/2491573) talál további információt (s-felhasználó szükséges).

## <a name="next-steps"></a>Következő lépések

A **helyszíni adatátjáróval** és a **DirectQueryvel** kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a helyszíni adatátjáró?](/data-integration/gateway/service-gateway-getting-started)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
