---
title: A Kerberos konfigurálása Power BI-jelentések használatára
description: Megtudhatja, hogyan konfigurálhatja a jelentéskészítő kiszolgálót Kerberos-hitelesítéssel a Power BI-jelentésekhez használt adatforrásokhoz egy elosztott környezetben.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maggies
ms.openlocfilehash: 6e341f80e3631228c28590ccf0a7711e0b624f2c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874224"
---
# <a name="configure-kerberos-to-use-power-bi-reports"></a>A Kerberos konfigurálása Power BI-jelentések használatára
<iframe width="640" height="360" src="https://www.youtube.com/embed/vCH8Fa3OpQ0?showinfo=0" frameborder="0" allowfullscreen></iframe>

Megtudhatja, hogyan konfigurálhatja a jelentéskészítő kiszolgálót Kerberos-hitelesítéssel a Power BI-jelentésekhez használt adatforrásokhoz egy elosztott környezetben.

A Power BI jelentéskészítő kiszolgálóval Power BI-jelentéseket üzemeltethet. A jelentéskészítő kiszolgáló számos adatforrást támogat. Ez a cikk kifejezetten az SQL Server Analysis Services szolgáltatással foglalkozik, az itt említett fogalmakat azonban egyéb adatforrásokra is alkalmazhatja, például az SQL Serverre.

A Power BI jelentéskészítő kiszolgálót, az SQL Servert és az Analysis Services szolgáltatást egyetlen gépen telepítheti, és további konfiguráció nélkül használhatja. Ez nagyszerű megoldás tesztkörnyezetekhez. Ha ezeket a szolgáltatásokat több, különálló gépre telepíti – egy elosztott környezetben –, hibákba ütközhet. Az ilyen környezetekben Kerberos-hitelesítést kell használnia, amelyhez bizonyos konfigurációkra van szükség. 

Név szerint a korlátozott delegálást kell konfigurálnia. Előfordulhat, hogy a környezetében már konfigurálta a Kerberost, azonban nem a korlátozott delegáláshoz.

## <a name="error-running-report"></a>Hiba a jelentés futtatásakor
Ha a jelentéskészítő kiszolgáló nem megfelelően van konfigurálva, a következő hibaüzenet jelenhet meg.

    Something went wrong.

    We couldn’t run the report because we couldn’t connect to its data source. The report or data source might not be configured correctly. 

A technikai részletek alatt az alábbi üzenet látható.

    We couldn’t connect to the Analysis Services server. The server forcibly closed the connection. To connect as the user viewing the report, your organization must have configured Kerberos constrained delegation.

![](media/configure-kerberos-powerbi-reports/powerbi-report-config-error.png)

## <a name="configuring-kerberos-constrained-delegation"></a>A korlátozott Kerberos-delegálás konfigurálása
A korlátozott Kerberos-delegálás megfelelő működéséhez több elemet is konfigurálni kell. Ilyen az egyszerű szolgáltatásnév és a szolgáltatásfiókok delegálási beállításai.

> [!NOTE]
> Az egyszerű szolgáltatásnevek és a delegálási beállítások konfigurálásához tartományi rendszergazdának kell lennie.
> 
> 

Az alábbi elemeket kell konfigurálni vagy érvényesíteni:

1. A jelentéskészítő kiszolgáló konfigurációjának hitelesítési típusa.
2. A jelentéskészítő kiszolgáló szolgáltatásfiókjának egyszerű szolgáltatásnevei.
3. Az Analysis Services szolgáltatás egyszerű szolgáltatásnevei.
4. Az Analysis Services-gép SQL Browser szolgáltatásának egyszerű szolgáltatásnevei. Ez csak a megnevezett példányok esetén szükséges.
5. A jelentéskészítő kiszolgáló szolgáltatásfiókjának delegálási beállításai.

## <a name="authentication-type-within-report-server-configuration"></a>A jelentéskészítő kiszolgáló konfigurációjának hitelesítési típusa
A korlátozott Kerberos-hitelesítés engedélyezéséhez konfigurálni kell a jelentéskészítő kiszolgáló hitelesítési típusát. Ezt a **rsreportserver.config** fájlban teheti meg. A fájl alapértelmezett helye: `C:\Program Files\Microsoft Power BI Report Server\PBIRS\ReportServer`.

A rsreportserver.config fájlban keresse meg az **Authentication/AuthenticationTypes** szakaszt.

Fontos, hogy az RSWindowsNegotiate kifejezésnek az első helyen kell szerepelnie a fájlban a hitelesítési típusok között. A képernyőnek az alábbihoz hasonlóan kell kinéznie.

```xml
<AuthenticationTypes>
    <RSWindowsNegotiate/>
    <RSWindowsNTLM/>
</AuthenticationTypes>
```

Ha módosítania kellett a konfigurációs fájlt, álljon meg és indítsa el a jelentéskészítő kiszolgálót, így meggyőződhet arról, hogy a módosítások életbe lépnek.

Erről a [Windows-hitelesítés konfigurálása a jelentéskészítő kiszolgálón](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server) című cikk nyújt részletesebb tájékoztatást.

## <a name="spns-for-the-report-server-service-account"></a>A jelentéskészítő kiszolgáló szolgáltatásfiókjának egyszerű szolgáltatásnevei
Következő lépésként győződjön meg róla, hogy a jelentéskészítő kiszolgáló számára elérhető egyszerű szolgáltatásnevek érvényesek. Ezt a jelentéskészítő kiszolgálóhoz konfigurált szolgáltatásfiók alapján teheti meg.

### <a name="virtual-service-account-or-network-service"></a>Virtuális szolgáltatásfiók vagy hálózati szolgáltatás
Ha a jelentéskészítő kiszolgáló a virtuális szolgáltatásfiókhoz vagy a hálózati szolgáltatáshoz van konfigurálva, nincs további teendője. Ezek a számítógépfiók környezetében találhatók. Alapértelmezés szerint a számítógépfiók HOST egyszerű szolgáltatásnevekkel rendelkezik. Ezek biztosítják a HTTP-szolgáltatást, és ezeket használja a jelentéskészítő kiszolgáló is.

Ha virtuális kiszolgálónevet használ, amely nem egyezik meg a számítógépfiók nevével, a HOST-bejegyzések nem vonatkoznak Önre, és manuálisan kell hozzáadnia a virtuális kiszolgálónév egyszerű szolgáltatásneveit.

### <a name="domain-user-account"></a>Tartományi felhasználó fiókja
Ha a jelentéskészítő kiszolgáló egy tartományi felhasználói fiók használatához van konfigurálva, Önnek manuálisan kell létrehoznia a fiókban HTTP egyszerű szolgáltatásneveit. Ezt megteheti a Windows Setspn eszközével.

> [!NOTE]
> Az egyszerű szolgáltatásnév létrehozásához rendszergazdai jogosultságra van szüksége a tartományban.
> 
> 

Javasoljuk, hogy két egyszerű szolgáltatásnevet hozzon létre: Egyet NetBIOS néven és egyet a teljes tartománynévvel. Az egyszerű szolgáltatásnév az alábbi formátummal rendelkezik:

    <Service>/<Host>:<port>

A Power BI jelentéskészítő kiszolgálója egy HTTP-szolgáltatást fog használni. A HTTP egyszerű szolgáltatásneveihez nem kell portot megadnia. Mi jelenleg csak a HTTP-szolgáltatással foglalkozunk. Az egyszerű szolgáltatásnév üzemeltetője egy Ön által választott, URL-ben megadott név lesz. Ez általában a számítógép neve. Ha terheléselosztót használ, előfordulhat, hogy ez egy virtuális név.

> [!NOTE]
> Az URL-t ellenőrizheti a böngésző címsorában, vagy a webportál URL lapján a Jelentéskészítő kiszolgáló – konfigurációkezelőben.
> 
> 

Ha a számítógépe neve ContosoRS, az egyszerű szolgáltatásnevek az alábbiak lesznek:

| Egyszerű szolgáltatásnév típusa | Egyszerű szolgáltatásnév |
| --- | --- |
| Teljes tartománynév |HTTP/ContosoRS.contoso.com |
| NetBIOS |HTTP/ContosoRS |

### <a name="location-of-spn"></a>Egyszerű szolgáltatásnév helye
Hová helyezheti az egyszerű szolgáltatásnevet? Az egyszerű szolgáltatásnevet a szolgáltatásfiókhoz használt szolgáltatásban fogja elhelyezni. Ha virtuális szolgáltatásfiókot vagy hálózati szolgáltatást használ, ez a számítógépfiók lesz. Bár korábban említettük, hogy erre csak a virtuális URL-ek esetében van szükség. Ha egy tartományi felhasználót használ a jelentéskészítő kiszolgáló szolgáltatásfiókjához, az egyszerű szolgáltatásnevet a tartományi felhasználó fiókjában fogja elhelyezni.

Ha például hálózati szolgáltatásfiókot használ, a számítógép neve pedig ContosoRS, az egyszerű szolgáltatásnév a ContosoRS-re kerül.

Ha az RSService egy tartományi felhasználói fiókját használja, az egyszerű szolgáltatásnév az RSService-re kerül.

### <a name="using-setspn-to-add-the-spn"></a>Az egyszerű szolgáltatásnév hozzáadása a SetSPN eszközzel
Az egyszerű szolgáltatásnevet hozzáadhatja a SetSPN eszközzel. Itt is a fenti, számítógépfiókra és a tartományi felhasználói fiókra vonatkozó példát követjük.

Ha a contoso-jelentések virtuális URL-jeit használja, az egyszerű szolgáltatásnevek elhelyezése a számítógépfiókon mind a teljes tartománynév, mind a NetBIOS egyszerű szolgáltatásneve esetén ehhez hasonlóan néz ki:

      Setspn -a HTTP/contosoreports.contoso.com ContosoRS
      Setspn -a HTTP/contosoreports ContosoRS

Ha az egyszerű szolgáltatásnév üzemeltetőjeként a számítógépnevet használja, az egyszerű szolgáltatásnevek elhelyezése a tartományi felhasználói fiókon mind a teljes tartománynév, mind a NetBIOS egyszerű szolgáltatásneve esetén ehhez hasonlóan néz ki:

      Setspn -a HTTP/ContosoRS.contoso.com RSService
      Setspn -a HTTP/ContosoRS RSService

## <a name="spns-for-the-analysis-services-service"></a>Az Analysis Services szolgáltatás egyszerű szolgáltatásnevei
Az Analysis Services egyszerű szolgáltatásnevei hasonlítanak a Power BI jelentéskészítő kiszolgálójához használtakhoz. Az egyszerű szolgáltatásnév formátuma kissé eltérő, ha egy megnevezett példánnyal rendelkezik.

Az Analysis Services esetén egy MSOLAPSvc.3 szolgáltatást használunk. A port helyének példánynevét az egyszerű szolgáltatásnévben adjuk meg. Az egyszerű szolgáltatásnév üzemeltető része vagy a számítógép neve, vagy a fürt virtuális neve.

Egy Analysis Serviceshez tartozó egyszerű szolgáltatásnév ehhez hasonlóan néz ki:

| Típus | Formátum |
| --- | --- |
| Alapértelmezett példány |MSOLAPSvc.3/ContosoAS.contoso.com<br>MSOLAPSvc.3/ContosoAS |
| Megnevezett példány |MSOLAPSvc.3/ContosoAS.contoso.com:INSTANCENAME<br>MSOLAPSvc.3/ContosoAS:INSTANCENAME |

Az egyszerű szolgáltatásnév elhelyezése is hasonlít a Power BI jelentéskészítő kiszolgálójához használthoz. Ez a szolgáltatásfiókon alapul.  Ha helyi rendszert vagy hálózati szolgáltatást használ, a számítógépfiók környezetében dolgozik. Ha egy tartományi felhasználót használ az Analysis Services-példányhoz, az egyszerű szolgáltatásnevet a tartományi felhasználó fiókjában fogja elhelyezni.

### <a name="using-setspn-to-add-the-spn"></a>Az egyszerű szolgáltatásnév hozzáadása a SetSPN eszközzel
Az egyszerű szolgáltatásnevet hozzáadhatja a SetSPN eszközzel. Ebben a példában a számítógép neve ContosoAS.

Az egyszerű szolgáltatásnevek elhelyezése a számítógépfiókon mind a teljes tartománynév, mind a NetBIOS egyszerű szolgáltatásneve esetén ehhez hasonlóan néz ki:

    Setspn -a MSOLAPSvc.3/ContosoAS.contoso.com ContosoAS
    Setspn -a MSOLAPSvc.3/ContosoAS ContosoAS

Az egyszerű szolgáltatásnevek elhelyezése a tartományi felhasználói fiókon mind a teljes tartománynév, mind a NetBIOS egyszerű szolgáltatásneve esetén ehhez hasonlóan néz ki:

    Setspn -a MSOLAPSvc.3/ContosoAS.contoso.com OLAPService
    Setspn -a MSOLAPSvc.3/ContosoAS OLAPService

## <a name="spns-for-the-sql-browser-service"></a>Az SQL Browser szolgáltatás egyszerű szolgáltatásnevei
Ha egy Analysis Services szolgáltatásbeli megnevezett példánnyal rendelkezik, arról is gondoskodnia kell, hogy a böngészőszolgáltatás rendelkezzen egyszerű szolgáltatásnévvel. Ez csak az Analysis Services esetében igaz.

Az SQL Browser egyszerű szolgáltatásnevei hasonlítanak a Power BI jelentéskészítő kiszolgálójához használtakhoz.

Az SQL Browserhez egy MSOLAPDisco.3 szolgáltatást használunk. A port helyének példánynevét az egyszerű szolgáltatásnévben adjuk meg. Az egyszerű szolgáltatásnév üzemeltető része vagy a számítógép neve, vagy a fürt virtuális neve.
A példány nevének vagy portjának nem kell megadnia semmit.

Egy Analysis Serviceshez tartozó egyszerű szolgáltatásnév ehhez hasonlóan néz ki:

    MSOLAPDisco.3/ContosoAS.contoso.com
    MSOLAPDisco.3/ContosoAS

Az egyszerű szolgáltatásnév elhelyezése is hasonlít a Power BI jelentéskészítő kiszolgálójához használthoz. A különbség az, hogy az SQL Browser mindig a helyi rendszer fiókja alatt fut. Ez azt jelenti, hogy az egyszerű szolgáltatásnevek mindig a számítógépfiókra kerülnek. 

### <a name="using-setspn-to-add-the-spn"></a>Az egyszerű szolgáltatásnév hozzáadása a SetSPN eszközzel
Az egyszerű szolgáltatásnevet hozzáadhatja a SetSPN eszközzel. Ebben a példában a számítógép neve ContosoAS.

Az egyszerű szolgáltatásnevek elhelyezése a számítógépfiókon mind a teljes tartománynév, mind a NetBIOS egyszerű szolgáltatásneve esetén ehhez hasonlóan néz ki:

    Setspn -a MSOLAPDisco.3/ContosoAS.contoso.com ContosoAS
    Setspn -a MSOLAPDisco.3/ContosoAS ContosoAS

További információ: [Az SQL Server Browser szolgáltatáshoz egy egyszerű szolgáltatásnévre van szükség](https://support.microsoft.com/kb/950599).

## <a name="delegation-settings-on-the-report-server-service-account"></a>A jelentéskészítő kiszolgáló szolgáltatásfiókjának delegálási beállításai
Az utolsó szakaszban konfiguráljuk a jelentéskészítő kiszolgáló szolgáltatásfiókjának delegálási beállításait. Ezeket a lépéseket több eszközzel is elvégezheti. Ebben a dokumentumban az Active Directory – felhasználók és számítógépek modult használjuk.

Első lépésként nyissa meg a jelentéskészítő kiszolgáló szolgáltatásfiókjának tulajdonságait az Active Directory – felhasználók és számítógépek modulban. Ha virtuális szolgáltatásfiókot vagy hálózati szolgáltatást használt, ez a számítógépfiók, ellenkező esetben pedig egy tartományi felhasználói fiók.

A korlátozott delegálást protokollátvitellel konfiguráljuk. A korlátozott delegáláshoz explicit módon kell megadnia azokat a szolgáltatásokat, amelyekhez delegálni szeretne. Adjuk hozzá az Analysis Services szolgáltatás és az SQL Browser egyszerű szolgáltatásneveit is ahhoz a listához, amely számára a Power BI jelentéskésíztő kiszolgálója delegálhat.

1. Kattintson jobb gombbal a jelentéskészítő kiszolgáló szolgáltatásfiókjára, majd válassza a **Tulajdonságok** lehetőséget.
2. Válassza a **Delegálás** lapot.
3. Válassza **A számítógépen csak a megadott szolgáltatások delegálhatók** lehetőséget.
4. Válassza a **Bármely hitelesítési protokoll** lehetőséget.
5. **A fiók az alábbi szolgáltatásokhoz használhat delegált hitelesítő adatokat:** : területen kattintson a **Hozzáadás** lehetőségre.
6. Az új párbeszédpanelben válassza a **Felhasználók vagy számítógépek** elemet.
7. Adja meg az Analysis Service szolgáltatásfiókját, majd kattintson az **OK** gombra.
8. Válassza ki a létrehozott egyszerű szolgáltatásnevet. Ez az alábbi kifejezéssel kezdődik: `MSOLAPSvc.3`. Ha a teljes tartománynév és a NetBIOS egyszerű szolgáltatásnevét is hozzáadta, mindkettő ki lesz jelölve. Lehet, hogy csak az egyiket látja.
9. Kattintson az **OK** gombra.  Ekkor az SPN-nek meg kell jelennie a listában.
10. Másik lehetőségként válassza a **Kibontva** lehetőséget a teljes tartománynév és a NetBIOS egyszerű szolgáltatásnevének megjelenítéséhez.
11. Kattintson ismét a **Hozzáadás** gombra. Most hozzáadjuk az SQL Browser egyszerű szolgáltatásnevét.
12. Az új párbeszédpanelben válassza a **Felhasználók vagy számítógépek** elemet.
13. Adja meg annak a számítógépnek a nevét, amelyen az SQL Browser szolgáltatás található, majd kattintson az **OK** gombra.
14. Válassza ki a létrehozott egyszerű szolgáltatásnevet. Ez az alábbi kifejezéssel kezdődik: `MSOLAPDisco.3`. Ha a teljes tartománynév és a NetBIOS egyszerű szolgáltatásnevét is hozzáadta, mindkettő ki lesz jelölve. Lehet, hogy csak az egyiket látja.
15. Kattintson az **OK** gombra. A párbeszédpanelnek az alábbi képhez kell hasonlítania, ha bejelölte a **Kibontva** négyzetet.
    
    ![](media/configure-kerberos-powerbi-reports/powerbi-report-config-delegation.png)
16. Kattintson az **OK** gombra.
17. Indítsa újra a Power BI jelentéskészítő kiszolgálót.

## <a name="running-a-power-bi-report"></a>Power BI-jelentés futtatása
A fenti konfigurációk elvégzése után a jelentésnek megfelelően meg kell jelennie. 

![](media/configure-kerberos-powerbi-reports/powerbi-report.png)

Ez a konfiguráció a legtöbb esetben működik, a Kerberosszal azonban a környezettől függően szükség lehet további konfigurációkra. Ha a jelentés továbbra sem töltődik be, vegye fel a kapcsolatot a tartományi rendszergazdával vagy az ügyfélszolgálattal.

## <a name="next-steps"></a>További lépések
[Rendszergazdai áttekintés](admin-handbook-overview.md)  
[A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md)  

Több kérdése van? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)

