---
title: Jelentés beágyazása egy biztonságos portálon vagy webhelyen
description: A Power BI egyszerűen beágyazza a funkció lehetővé teszi, hogy felhasználók számára, és biztonságos belső webes portálok a jelentéseket beágyazhatja.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222232"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Jelentés beágyazása egy biztonságos portálon vagy webhelyen

Az új **beágyazási** lehetőséget a Power bi-jelentések, egyszerűen és biztonságosan beágyazhat jelentéseket a belső webes portálok. Ezeken a portálokon jelenleg lehet **felhőalapú** vagy **a helyileg üzemeltetett**, például a SharePoint 2019. Beágyazott jelentések veszik figyelembe az összes elem engedélyek és az adatok biztonsági keresztül [sorszintű biztonság (RLS)](service-admin-rls.md). Bármilyen portál, amely egy URL-cím vagy egy IFRAME-keret beágyazási kódot nem biztosítanak. 

A **beágyazási** beállítást támogatja [URL-szűrőkhöz](service-url-filters.md) és URL-beállítások. Csekély programozást igénylő csak alapszintű HTML és JavaScript Tudásbázis módszerével portálok integrálását lehetővé teszi.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Power BI-jelentések **beágyazása** portálokba

1. Az új **beágyazás** lehetőség a Power BI szolgáltatás jelentéseinek **Fájl** menüjében érhető el.

    ![Biztonságos beágyazás lehetőség – legördülő elem](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Válassza ki a **beágyazási** beállítás, amely tartalmaz egy hivatkozást, és használhatja a jelentés biztonságos beágyazása az iFrame párbeszédpanel megnyitásához.

    ![Beágyazás lehetőség – párbeszédpanel](media/service-embed-secure/secure-embed-code-dialog.png)

3. E egy felhasználó megnyitja a jelentés URL-címet közvetlenül, vagy egy olyan webes portál ágyazva, jelentés-hozzáférés hitelesítést igényel. A következő képernyő jelenik meg, ha a felhasználó még nincs bejelentkezve a Power bi-bA a böngésző-munkamenetet a. Ha kiválaszt **bejelentkezési**, megnyithat egy új böngészőablakban vagy lapon. Kell őket előugró blockers keresése, ha nem kérni, jelentkezzen be.

    ![Jelentkezzen be a jelentés megtekintéséhez](media/service-embed-secure/secure-embed-sign-in.png)

4. Miután a felhasználó jelentkezett be, megnyílik a jelentés, adatait jeleníti meg, és lehetővé teszi a lapok közötti navigálásról és -szűrő beállítása. Csak olyan felhasználók, akik rendelkeznek engedély megtekintése a jelentést a Power bi-ban látható. Az összes [sorszintű biztonság (RLS)](service-admin-rls.md) szabályok is vonatkoznak. Végül a felhasználónak rendelkeznie kell a megfelelő licenccel. Vagy Power BI Pro-licencre van szüksége, vagy a jelentésnek kell Power BI Premium-kapacitáson lévő munkaterületen lennie. A felhasználónak kell minden alkalommal, amikor megnyitják egy új böngészőablakban jelentkezzen be. Azonban ha már bejelentkezett, más jelentések automatikusan betöltődik.

    ![Jelentés beágyazása](media/service-embed-secure/secure-embed-report.png)

5. Egy IFRAME elembe használatakor szükség lehet szerkeszteni a **magasság** és **szélesség** , hogy illeszkedjen a portálon a weblapon.

    ![Magasság és szélesség megadása](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>A jelentés-hozzáférés biztosítása

A **beágyazási** beállítás automatikusan nem engedélyezheti a felhasználóknak a jelentés megtekintéséhez. Engedélyek megtekintése a Power BI szolgáltatásban vannak beállítva.

A Power BI szolgáltatásban megoszthatja beágyazott jelentések hozzáférést igénylő felhasználók. Ha Office 365-csoportot használ, mint egy alkalmazás-munkaterületen tag listázhatja a felhasználó. További információkért lásd: hogyan [kezelheti az alkalmazás-munkaterülethez a Power BI és az Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licencelés

A beágyazott jelentés megtekintéséhez, felhasználók vagy a Power BI Pro licencre van szüksége, vagy a tartalomnak kell lennie, amely a munkaterület egy [Power BI Premium-kapacitás (EM vagy P Termékváltozat)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>A beágyazás testreszabása URL-beállításokkal

Testre szabhatja a felhasználói élmény a beágyazási URL-cím beviteli beállítások használatával. A megadott IFrame-keretben, az URL-címet is frissítheti **src** beállításait.

| Tulajdonság  | Leírás  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Használhatja a **pageName** lekérdezési karakterlánc paraméterének be, hogy melyik jelentés lap megnyitásához. Annak ezt az értéket a jelentés URL-cím végén egy jelentést a Power BI szolgáltatásban megtekintésekor alább látható módon. |  |  |  |
| URL-szűrők  | Használhat [URL-szűrőkhöz](service-url-filters.md) a beágyazási URL-ben kapott a Power BI felhasználói felületén a beágyazott tartalom szűrése. Így alacsony kódigényű integrációkat fejleszthet, csupán alapszintű HTML- és JavaScript-tapasztalattal.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Mely lap, melyen a beágyazott jelentések beállítása 

Annak a **pageName** a Power BI szolgáltatás bármely jelentésének megtekintésekor a jelentés URL-cím végén értékét.

1. Nyissa meg a jelentést a Power BI szolgáltatásból a webböngészőben, és ezután másolja az URL-címe sáv.

    ![Jelentésszakasz](media/service-embed-secure/secure-embed-report-section.png)

2. Fűzze a **pageName** beállítást az URL-címhez.

    ![pageName hozzáfűzése](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Jelentés tartalmának szűrése URL-szűrőkkel 

Használhat [URL-szűrőkhöz](service-url-filters.md) nézetek különböző jelentést biztosít. Az alábbi URL például úgy szűri a jelentést, hogy az az energiaipar adatait jelenítse meg.

A **pageName** és az [URL-szűrők](service-url-filters.md) együttes használata rendkívül hatékony lehet. Megoldásokat alapszintű HTML- és JavaScript-szakértelemmel is fejleszthet.

Ha például a következő egy HTML-oldalt is hozzáadhat egy gombot:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Kiválasztásakor a a gomb meghív egy függvényt, frissítheti az IFRAME-keret egy frissített URL-CÍMÉT, amely tartalmazza az energia iparági szűrő.

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

* A felhasználónak kell bejelentkezni, amikor egy új böngészőablakban megnyitja a jelentés megtekintéséhez.

* Egyes böngészők szükséges, hogy a bejelentkezés után frissítse az oldalt, különösen akkor, ha InPrivate vagy Inkognitó módban.

* Egy egyszeri bejelentkezéses működést érhet el, a beágyazási használata a SharePoint online-hoz lehetőséget vagy egy egyéni integrációs használatával a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) metódus beágyazásához. 

* A **Beágyazás** lehetőség automatikus hitelesítés funkciója nem működik a Power BI JavaScript API-jával. A Power BI JavaScript API használata a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) metódus beágyazásához. 

## <a name="next-steps"></a>Következő lépések

* [Megoszthatja a munkáját a Power bi-ban módjai](service-how-to-collaborate-distribute-dashboards-reports.md)

* [A jelentések szűrhetők az URL-cím lekérdezési karakterlánc paraméterei az](service-url-filters.md)

* [Beágyazás jelentéskijelzővel a SharePoint online-hoz](service-embed-report-spo.md)

* [A Power BI webes közzététel](service-publish-to-web.md)