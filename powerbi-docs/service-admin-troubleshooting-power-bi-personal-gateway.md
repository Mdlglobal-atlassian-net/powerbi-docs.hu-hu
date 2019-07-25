---
title: A Power BI személyes átjáró hibáinak elhárítása
description: A Power BI személyes átjáró hibáinak elhárítása
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 7827ce359022eccfb75798b08da164b7504c84df
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271827"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>A Power BI személyes átjáró hibáinak elhárítása

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

A következő szakaszokban áttekintjük a Power BI privát átjáró használata kapcsán gyakorta felmerülő kérdéseket.

## <a name="update-to-the-latest-version"></a>Frissítés a legújabb verzióra

Az átjáró aktuális, személyes használatú verziója a **Helyszíni adatátjáró (személyes)** . A telepített példányt frissítve térjen át erre a verzióra.

Elavult verziójú átjáró használatakor számos probléma merülhet fel.  Általában véve célszerű mindig a legújabb verziót használni. Ha az átjárót már legalább egy hónapja nem frissítette, ajánlott telepíteni az átjáró legújabb verzióját. Ez után nézze meg, hogy jelentkezik-e ugyanaz a probléma.

## <a name="installation"></a>Telepítés
**A privát átjáró 64 bites** – Ha a gép 32 bites, nem telepítheti a privát átjárót. Az operációs rendszernek 64 bitesnek kell lennie. Telepítse a Windows 64 bites verzióját, vagy telepítse 64 bites számítógépre a privát átjárót.

**Bár Ön rendszergazda a számítógépen, a privát átjárót nem tudja szolgáltatásként telepíteni** ‒ A telepítés meghiúsulhat, ha a felhasználó tagja a helyi Rendszergazda csoportnak, de a csoport házirendje nem engedélyezi, hogy az adott felhasználónév szolgáltatásként jelentkezzen be. Egyelőre ellenőrizze, hogy a csoportházirend lehetővé teszi-e, hogy a felhasználó szolgáltatásként jelentkezzen be. Ennek a problémának a javításán még dolgozunk. [További információ](https://technet.microsoft.com/library/cc739424.aspx)

**A művelet túllépte az időkorlátot** ‒ Ez az üzenet gyakran megjelenik, ha a számítógép (fizikai gép vagy VM), amelyre telepíti a privát átjárót, egymagos processzorral rendelkezik. Zárja be az alkalmazásokat, állítsa le azokat a folyamatokat, melyek nem nélkülözhetetlenek, és próbálja meg újra telepíteni az átjárót.

**Az Adatkezelési átjáró vagy az Analysis Services Connector nem telepíthető a privát átjáróval egy gépre** – Ha a gépén már telepítve van az Analysis Services Connector vagy az Adatkezelési átjáró, akkor először el kell távolítania a Connectort vagy az átjárót. Ez után próbálja meg telepíteni a privát átjárót.

> [!NOTE]
> Ha a telepítés során problémát észlel, a telepítési napló valószínűleg tartalmaz olyan információt, amely segít megoldani a kérdést. Ezzel kapcsolatban a [telepítési naplókról](#SetupLogs) szóló részben talál további információkat.
> 
> 

 **Proxybeállítások** Ha olyan környezetet használ, amelyben szükség van proxy használatára, problémák jelentkezhetnek a privát átjáró telepítésekor. Ha további információkra van szüksége a proxyadatok konfigurálásával kapcsolatban, tekintse át a [helyszíni adatátjáró proxybeállításainak konfigurálásáról](/data-integration/gateway/service-gateway-proxy) szóló cikket.

## <a name="schedule-refresh"></a>Frissítés ütemezése
**Hiba: The credential stored in the cloud is missing. (A felhőben tárolt hitelesítő adat hiányzik.)**

Ilyen hiba az \<adathalmazok\> beállításainál jelentkezhet, ha az adathalmazhoz korábban megadott ütemezett frissítést, majd eltávolította és újratelepítette a privát átjárót. A privát átjáró eltávolításakor a rendszer eltávolítja az adathalmazok frissítéshez szükséges adatforrás-hitelesítési adatokat a Power BI szolgáltatásból.

**Megoldás:** A Power BI-ban lépjen az adatkészletre vonatkozó beállítások frissítéséhez. Az adatforrások kezelésére szolgáló felületen mindegyik hibás adatforrásnál válassza a **Hitelesítő adatok szerkesztése** lehetőséget, majd jelentkezzen be ismét az adatforrásra.

**Hiba: The credentials provided for the dataset are invalid. (Az adatkészlethez megadott hitelesítő adatok érvénytelenek.) A folytatáshoz először frissítse a hitelesítő adatokat a lap frissítésével vagy az Adatforrás beállításai párbeszédpanelen.**

**Megoldás**: Ha a hitelesítő adatokkal kapcsolatos üzenet jelenik meg, az a következőket jelentheti:

* Ellenőrizze, hogy naprakészek-e az adatforrásokra történő bejelentkezéshez használt felhasználói nevek és jelszavak. A Power BI-ban lépjen az adatkészlet beállításainak frissítéséhez. Az adatforrások kezelési felületén válassza az adatforrás melletti **Hitelesítő adatok szerkesztése** lehetőséget, majd frissítse az adatforráshoz tartozó hitelesítő adatokat.
* Egy felhőbeli forrás és egy helyi forrás egyesített lekérdezése a privát átjárón keresztül nem frissíthető, ha bármelyik forrás OAuth eljárást használ a hitelesítéshez. Ilyen problémával jár például a CRM Online és egy helyi SQL-szerver egyesítése is. Ebben az esetben az egyesítés azért nem fog sikerülni, mert a CRM Online OAuth-hitelesítést igényel.
  
  Ez a hiba ismert probléma, már foglalkozunk vele. A probléma úgy kerülhető meg, hogy külön lekérdezést használ a felhőbeli forráshoz és a helyszíni adatforráshoz. Ezt követően összefésüléssel vagy összefűzéssel egyesíti az eredményeket.

**Hiba: Unsupported data source. (Nem támogatott adatforrás.)**

**Megoldás:** Ha nem támogatott adatforrásról tájékoztató üzenetet kap a frissítések ütemezése közben, az a következőket jelentheti: 

* Jelenleg Power BI-ban nem támogatott az adatforrás frissítése. 
* Az Excel-munkafüzet nem tartalmaz adatmodellt, csak munkafüzet adatokat. A Power BI jelenleg csak akkor támogatja a frissítést, ha a feltöltött Excel-munkafüzet tartalmaz adatmodellt. Ha az Excelbe a Power Query-t használva importál adatokat, válassza az Adatok betöltése adatmodellbe lehetőséget. Ez a lehetőség biztosítja, hogy az adatokat egy adatmodellbe importálja a rendszer. 

**Hiba: [Az adatok nem kombinálhatók] a &lt;lekérdezés rész&gt;/&lt;... &gt;/&lt;... &gt; olyan adatforrásokhoz próbál hozzáférni, melyek különböző adatvédelmi szintjei együtt nem használhatók. Kérjük, építse újra az adategyesítést.**

**Megoldás**: Ezt a hibát az adatvédelmi szintekre vonatkozó korlátozások és az Ön által használt adatforrástípusok okozzák.

**Hiba: Adatforráshiba: We cannot convert the value "\[Table\]" to type Table. (Adatforrás-hiba: A [Tábla] érték nem konvertálható a következő típusra: Tábla.)**

**Megoldás**: Ezt a hibát az adatvédelmi szintekre vonatkozó korlátozások és az Ön által használt adatforrástípusok okozzák.

**Hiba: Nincs elegendő szabad terület ehhez a sorhoz.**

Ez a hiba akkor fordul elő, ha egyetlen sor mérete nagyobb 4 MB-nál. Keresse meg az adatforrás érintett sorát, és kísérlje meg kiszűrni vagy csökkenteni a méretét.

## <a name="data-sources"></a>Adatforrások
**Hiányzó adatszolgáltató** – A privát átjáró csak 64 bites verzióban érhető el. Működéséhez arra van szükség, hogy a számítógépre, amelyen a személyes átjáró üzemel, telepítve legyen az adatszolgáltató 64 bites verziója. Például, ha az adatkészletben szereplő adatforrás Microsoft Access típusú, telepítenie kell a 64 bites ACE-szolgáltatót arra a számítógépre, amelyen a személyes átjáró is fut.  

>[!NOTE]
>Ha 32 bites Excellel rendelkezik, nem fog tudni 64 bites ACE-szolgáltatót telepíteni a gépre.

**Access-adatbázis használata esetén a Windows-hitelesítés nem támogatott** – Access-adatbázis esetén a Power BI jelenleg csak a névtelen hitelesítést támogatja. Dolgozunk azon, hogy Windows-hitelesítést lehessen használni az Access-adatbázisokhoz is.

**Bejelentkezési hiba az adatforrás eléréséhez használandó hitelesítő adatok beírásakor** – Ha a Windows hitelesítési adatok beírásakor ehhez hasonló hibaüzenetet kap, amikor megpróbál kapcsolódni egy adatforráshoz, elképzelhető, hogy a privát átjáró egy régebbi verzióját használja. [Telepítse a Power BI személyes átjáró legfrissebb verzióját](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Hiba: Bejelentkezési hiba Windows-hitelesítés kijelölésekor, ACE OLEDB-t használó adatforrás esetén** – Ha ACE OLEDB szolgáltatót használó adatforrás esetén a hitelesítési adatok beírásakor az alábbi üzenet jelenik meg:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

A Power BI jelenleg nem támogatja a Windows-hitelesítést ACE OLEDB szolgáltatót használó adatforrások esetén.

**Megoldás:** A hiba elkerülése érdekében válassza a **Névtelen hitelesítést**. A hagyományos ACE OLEDB szolgáltatók esetén a Névtelen hitelesítő adatok megegyeznek a Windows-hitelesítő adatokkal.

## <a name="tile-refresh"></a>Csempefrissítés
Ha az irányítópult csempéinek frissítésével kapcsolatban kap hibaüzenetet, tekintse át a következő cikket.

[Csempékkel kapcsolatos hibák elhárítása](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Hibaelhárítási eszközök
### <a name="refresh-history"></a>Frissítési előzmények
A **Frissítési előzmények** segítenek áttekinteni az előfordult hibákat, és hasznos adatokat biztosítanak arra az esetre, ha a támogatást nyújtó ügyfélszolgálathoz kellene fordulnia. Itt az ütemezett és az igény szerinti frissítéseket is láthatja. A **Frissítési előzmények** oldalra az alábbiak szerint juthat el.

1. A Power BI navigációs ablaktáblájának **Adatkészletek** területén jelöljön ki egy adatkészletet, majd válassza a &gt;Menü megnyitása&gt; **Frissítés ütemezése** lehetőséget.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. A **Beállítások:...** területem válassza a **Frissítési előzmények** lehetőséget.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Eseménynaplók
Több eseménynapló is nyújthat információkat. Az első kettőt, a **Data Management Gateway** (Adatkezelési átjáró) és a **PowerBIGateway** (PowerBI átjáró) naplókat akkor láthatja, ha Ön rendszergazda a számítógépen.  Ha ön nem rendszergazda, és a privát átjárót használja, a naplóbejegyzéseket az **Alkalmazásnaplóban** tudja megtekinteni.

A **Data Management Gateway** (Adatkezelési átjáró) és **PowerBIGateway** naplók az **Alkalmazás- és szolgáltatásnaplók** között találhatók.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Nyomon követés a Fiddlerrel
A [Fiddler](http://www.telerik.com/fiddler) a Telerik ingyenes eszköze, amely a HTTP-adatforgalom figyelésére használható. Nyomon követheti a Power BI szolgáltatás és az ügyfélszámítógép közötti kommunikációt. A kommunikációban hibaüzenetek és egyéb, kapcsolódó információk is megjelenhetnek.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Telepítési naplók
Ha a **privát átjárót** nem tudja telepíteni, megjelenik egy hivatkozás, melynek segítségével megjelenítheti a telepítési naplót. A telepítési naplóban további információkat talál a hibával kapcsolatban. Ezek naplók windowsos telepítési naplók, más néven MSI-naplók. Ezek a bejegyzések meglehetősen összetettek és nehezen olvashatók. A hiba rendszerint alul olvasható, ugyanakkor a hiba okát nem egyszerű megállapítani. Lehet, hogy egy másik naplóban feljegyzett hibák eredményeképpen alakult ki, de az is előfordulhat, hogy egy korábbi bejegyzésben szereplő hiba miatt.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Másik lehetőségként megnyithatja a **Temp mappát** (%temp%), és megkeresheti a **Power\_BI\_** sztringgel kezdődő fájlokat.

> [!NOTE]
> Elképzelhető, hogy a %temp% használatával a Temp mappa egyik almappájába kerül. A **Power\_BI\_** fájlok a temp könyvtár gyökerében találhatók.  Ehhez lehet, hogy egy vagy két szinttel feljebb kell lépnie.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Következő lépések
[Helyszíni adatátjáró proxybeállításainak konfigurálása](/data-integration/gateway/service-gateway-proxy)  
[Adatfrissítés](refresh-data.md)  
[A Power BI személyes átjáró](service-gateway-personal-mode.md)  
[Csempékkel kapcsolatos hibák elhárítása](refresh-troubleshooting-tile-errors.md)  
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

