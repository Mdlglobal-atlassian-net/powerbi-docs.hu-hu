---
title: Jelentés beágyazása egy biztonságos portálon vagy webhelyen
description: A Power BI jelentések biztonságos beágyazását lehetővé tevő funkciójával engedélyezheti a felhasználóknak, hogy könnyen és biztonságosan beágyazzanak jelentéseket belső webportálokon.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 81f6d77543ec53ac790f5c5183da32bde80fd6b9
ms.sourcegitcommit: b3af4f7ef486c95cea173caea5a31d0472816ddd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54136767"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Jelentés beágyazása egy biztonságos portálon vagy webhelyen

A Power BI jelentéseinek új, biztonságos **beágyazás** funkciójával engedélyezheti a felhasználóknak, hogy könnyen és biztonságosan beágyazzanak jelentéseket belső, **felhőalapú** vagy **helyszínen üzemeltetett** webportálokon, például a SharePoint 2019-ben. Az így beágyazott jelentések minden elemengedélyt tiszteletben tartanak, az adatbiztonsággal együtt egészen a sorszintű biztonságig (RLS). A funkció célja, hogy lehetővé tegye a kód nélküli beágyazást bármilyen portálon, amely elfogad beágyazható URL-eket vagy iFrame-eket.

A **beágyazás** lehetőséget az [URL-szűrőket](service-url-filters.md) és az URL-beállításokat is támogatja. A **beágyazás** lehetőséggel kevés kódot használó, alapszintű HTML- és JavaScript-szakértelmet kívánó megközelítéssel integrálhat portálokkal.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Power BI-jelentések **beágyazása** portálokba

1. Az új **beágyazás** lehetőség a Power BI szolgáltatás jelentéseinek **Fájl** menüjében érhető el.

    ![Biztonságos beágyazás lehetőség – legördülő elem](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Válassza a Beágyazás lehetőséget, amellyel megnyit egy párbeszédpanelt, ahol egy, a jelentés biztonságos beágyazásához szükséges hivatkozás és egy iFrame található.

    ![Beágyazás lehetőség – párbeszédpanel](media/service-embed-secure/secure-embed-code-dialog.png)

3. Az URL a webportálon való beágyazása után vagy az URL közvetlen megnyitása után a felhasználót hitelesíteni kell, mielőtt hozzáférhetne a jelentéshez. A lenti példában a felhasználó nem jelentkezett be a Power BI szolgáltatásba a böngésző munkamenetében. Amikor a **Bejelentkezés** gombra kattintanak, új böngészőablakot vagy -lapot kell megnyitni. Ha nem lát bejelentkezési kérelmet, ellenőrizze, hogy nincsenek-e letiltva a felugró ablakok.

    ![Jelentkezzen be a jelentés megtekintéséhez](media/service-embed-secure/secure-embed-sign-in.png)

4. Miután a felhasználó bejelentkezett, a jelentés megnyílik, és megjelennek az adatok. A felhasználók ekkor szabadon navigálhatnak az oldalak között, és megadhatnak szűrőket. A jelentést csak azon felhasználók láthatják, akiknek erre engedélyük van a Power BI-ban. Minden sorszintű biztonsági (RLS) szabály érvényben van. Végül a felhasználónak rendelkeznie kell a megfelelő licenccel. Vagy Power BI Pro-licencre van szüksége, vagy a jelentésnek kell Power BI Premium-kapacitáson lévő munkaterületen lennie. A felhasználónak minden alkalommal be kell jelentkeznie, amikor megnyit egy új böngészőablakot, azonban egyszeri bejelentkezés után minden jelentés automatikusan betöltődik.

    ![Jelentés beágyazása](media/service-embed-secure/secure-embed-report.png)

5. Az iFrame lehetőség használatakor célszerű szerkesztenie a megadott HTML-t, így megszabhatja a kívánt magasságot és szélességet, a portál weboldalához igazítva.

    ![Magasság és szélesség megadása](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-access-to-reports"></a>Hozzáférés biztosítása a jelentésekhez

A Beágyazás lehetőség nem engedélyezi automatikusan felhasználóknak a jelentés megtekintését. A megtekintési engedélyeket a Power BI szolgáltatásban kell beállítani.

Ha hozzáférést szeretne nyújtani a jelentéshez a Power BI szolgáltatásban, megoszthatja azt azokkal a felhasználókkal, akiknek a beágyazott jelentéshez való hozzáférésre van szükségük. Ha egy Office 365-csoportot használ, akkor a felhasználót hozzáadhatja az alkalmazás-munkaterülethez a Power BI szolgáltatásban. További információkért lásd: [Alkalmazás-munkaterület kezelése](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licencelés

A beágyazott jelentést megtekintő felhasználónak vagy Power BI Pro-licencre van szüksége, vagy a tartalomnak kell [Power BI Premium-kapacitáson (EM vagy P termékváltozat)](service-admin-premium-purchase.md) lévő munkaterületen lennie.

## <a name="customize-your-embed-experience-using-url-settings"></a>A beágyazás testreszabása URL-beállításokkal

A beágyazási URL-cím számos bemeneti beállítást támogat, amelyekkel testreszabhatja a beágyazást. Ha a megadott iFrame-et használja, ügyeljen rá, hogy frissítse az URL-t az iFrame src-beállításaiban.

| Tulajdonság  | Leírás  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | A **pageName** lekérdezési karakterlánc paraméterével beállíthatja, hogy a jelentés mely oldala nyíljon meg. A **pageName** érték a jelentés URL-címének végének felel meg, ha a jelentést a Power BI szolgáltatásban tekinti meg, a lenti ábrához hasonlóan. |  |  |  |
| URL-szűrők  | A beágyazás tartalmának szűréséhez használhatja a Power BI felhasználói felületén kapott beágyazási URL-cím [URL-szűrőit](service-url-filters.md). Így alacsony kódigényű integrációkat fejleszthet, csupán alapszintű HTML- és JavaScript-tapasztalattal.  |  |  |  |

## <a name="set-which-page-opens-when-the-report-is-embedded"></a>A jelentés megnyitásakor megjelenő oldal beállítása

A *pageName* beállításban megadott érték a jelentés URL-címének végének felel meg, ha a jelentést a Power BI szolgáltatásban tekinti meg.

1. Nyissa meg a jelentést a Power BI szolgáltatásból a böngészőben, és másolja a vágólapra az URL-címet a címsorból.

    ![Jelentésszakasz](media/service-embed-secure/secure-embed-report-section.png)

2. Fűzze a *pageName* beállítást az URL-címhez.

    ![pageName hozzáfűzése](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Jelentés tartalmának szűrése URL-szűrőkkel

Az [URL-szűrőkkel](service-url-filters.md) bizonyos speciális funkciókat is elérhet, amelyekkel további megoldásokat készíthet a jelentést használva. Az alábbi URL például úgy szűri a jelentést, hogy az az energiaipar adatait jelenítse meg.

A **pageName** és az [URL-szűrők](service-url-filters.md) együttes használata rendkívül hatékony lehet. Megoldásokat alapszintű HTML- és JavaScript-szakértelemmel is fejleszthet.

Például a következőképp adhat hozzá egy gombot egy HTML-laphoz:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

A gomb lenyomáskor meghív egy függvényt, amely frissíti az iFrame-et egy új URL-címmel, amely tartalmazza az energiaiparra vonatkozó szűrőt.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Szűrő](media/service-embed-secure/secure-embed-filter.png)

Tetszőleges számú gombot hozzáadhat, így alacsony kódigényű megoldást készíthet. 

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Nem támogatja az Azure vállalatközi megoldásait használó külső vendégfelhasználókat.

* A biztonságos beágyazás a Power BI szolgáltatásban közzétett jelentésekkel működik.

* A felhasználónak be kell jelentkeznie a jelentés megtekintéséhez minden alkalommal, amikor megnyit egy új böngészőablakot.

* Egyes böngészőkben előfordulhat, hogy frissíteni kell a lapot a bejelentkezést követően, kifejezetten InPrivate vagy inkognitó módban való használatkor.

* Egyszeri bejelentkezéses használathoz használja a Beágyazás SharePoint Online-ban lehetőséget, vagy fejlesszen egyéni integrációt a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) módszerrel. További információ a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) megközelítésről.

* A **beágyazás** lehetőség automatikus hitelesítés funkciója nem működik a Power BI JavaScript API-jával. A Power BI JavaScript API-hoz a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) módszert kell használnia. További információ a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) megközelítésről.

## <a name="next-steps"></a>Következő lépések

* [A munka megosztásának módjai](service-how-to-collaborate-distribute-dashboards-reports.md)

* [URL-szűrők](service-url-filters.md)

* [SharePoint Online jelentéskijelző](service-embed-report-spo.md)

* [Webes közzététel](service-publish-to-web.md)