---
title: A Power BI jelentéskészítő kiszolgáló újdonságai
description: A Power BI jelentéskészítő kiszolgáló újdonságainak bemutatása. A cikk a főbb funkciókat ismerteti és az új elemek kibocsátásakor frissül.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 08/16/2018
ms.openlocfilehash: 648938006cd15e2bb92b305aa9a2af24d028cead
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/12/2018
ms.locfileid: "44726938"
---
# <a name="whats-new-in-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgáló újdonságai

A Power BI jelentéskészítő kiszolgáló újdonságainak bemutatása. A cikk a főbb funkciókat ismerteti, és az új elemek kibocsátásakor frissül.

A Power BI jelentéskészítő kiszolgáló, illetve a Power BI jelentéskészítő kiszolgálóra optimalizált Power BI Desktop letöltéséhez nyissa meg az [On-premises reporting with Power BI Report Server](https://powerbi.microsoft.com/report-server/) (Helyi jelentéskészítés Power BI jelentéskészítő kiszolgálóval) webhelyet.

Ezekből a forrásokból folyamatosan értesülhet a Power BI jelentéskészítő kiszolgáló új funkcióiról.

* [Microsoft Power BI-blog](https://powerbi.microsoft.com/blog/)
* [Az SQL Server Reporting Services csapat blogja](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* A [Guy in a Cube YouTube-csatorna](https://aka.ms/guyinacube)

Az újdonságokra vonatkozó Power BI-információk:

* [A Power BI szolgáltatás újdonságai](../service-whats-new.md)
* [A Power BI Desktop újdonságai](../desktop-latest-update.md)
* [A Power BI-mobilalkalmazások újdonságai](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="august-2018"></a>2018. augusztus

A Power BI Desktop alkalmazás Power BI jelentéskészítő kiszolgálóhoz optimalizált verziója nagyszámú új szolgáltatással bővült a 2018. augusztusi kiadásban. Az új szolgáltatások, területekre osztva:

- [Jelentéskészítés](#reporting)
- [Elemzés](#analytics)
- [Modellezés](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>A 2018. augusztusi kiadás kiemelt funkciói

Az új szolgáltatások hosszú listájából az alábbiak különösen érdekesek. További információkat a [blogbejegyzésben](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/) talál.

#### <a name="report-theming"></a>Jelentési téma

A Power BI jelentéskészítő kiszolgáló 2018. augusztusi kiadásához jelentési témát adtunk hozzá, amellyel gyorsan kiszínezheti a teljes jelentést a témának vagy vállalati védjegyezésnek megfelelően. A téma frissítésekor minden diagram automatikusan frissül a téma színeinek használatához, és elérheti a téma színeit a színpalettáról. A témafájlt a **Témaváltás** gomb alatti **Téma importálása** lehetőség használatával töltheti fel.

A témafájl egy JSON-fájlt, amely tartalmazza a jelentésben használni kívánt összes színt és azokat az alapértelmezett formázásokat, amelyeket alkalmazni szeretne a vizualizációkra.
Íme egy egyszerű JSON-mintatéma, amely frissíti a jelentés alapértelmezett színeit:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Feltételes formázás másik mező alapján

A feltételes formázás jelentős fejlesztéseinek egyike az a lehetőség, hogy az oszlopot egy másik mező alapján formázhatja a modellben.

#### <a name="conditional-formatting-by-values"></a>Feltételes formázás értékek alapján

Egy másik új feltételes formázási típus a **Formázás mezőérték szerint**. A Formázás mezőérték szerint lehetővé teszi egy színt hexadecimális kóddal vagy névvel meghatározó mérték vagy oszlop használatát, és alkalmazza ezt a színt a háttér vagy előtér színekén.

#### <a name="report-page-tooltips"></a>Jelentésoldal elemleírásai

A jelentésoldal elemleírásai szolgáltatás a Power BI jelentéskészítő kiszolgáló 2018. augusztusi frissítésének része. Ez a funkció lehetővé teszi egy jelentésoldal tervezését, amelyet felhasználhat a jelentés más vizualizációinak egyéni elemleírásaként.

#### <a name="log-axis-improvements"></a>Logaritmikus tengely fejlesztései

Nagymértékben továbbfejlesztettük a logaritmikus tengelyt a Descartes-féle diagramokban. Már választhat logaritmikus méretezést bármely Descartes-féle diagram, többek között a kombinált diagram számtengelyéhez, ha teljes egészében pozitív vagy teljes egészében negatív adatokkal rendelkezik.

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO Direct Query

Már elérhető a Power BI-jelentésekhez a SAP HANA SSO Direct Query Kerberosszal támogatása.

>[!Note]
>Ez a forgatókönyv csak akkor támogatott, ha a SAP HANA platformot relációs adatforrásként kezeli a Power BI Desktop alkalmazásban létrehozott jelentésekben.  Ennek engedélyezéséhez a Power BI Desktop DirectQuery menüjének Beállítások területén jelölje be „A SAP HANA kezelése relációs forrásként” jelölőnégyzetet, majd kattintson az OK gombra.

#### <a name="custom-visuals"></a>Egyéni vizualizációk

- A kiadás az 1.13.0 API-verziót tartalmazza.

- Az egyéni vizualizációk most visszaváltanak a kiszolgálói API jelenlegi verziójával kompatibilis előző verzióra (ha rendelkezésre áll).

### <a name="reporting"></a>Jelentéskészítés 

- [Jelentési téma](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Műveletek indítása gombokkal](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Vonalstílusok kombinált diagramokhoz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Továbbfejlesztett alapértelmezett rendezés vizualizációkhoz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Numerikus szeletelő](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Fejlettebb szeletelő-szinkronizálás](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Logaritmikus tengely fejlesztései](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Adatcímke-lehetőségek tölcsérdiagramhoz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Vonalvastagság nullára állítása](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Kontrasztos megjelenítés a jelentésekhez](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Gyűrűdiagram sugarának vezérlője](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Torta- és gyűrűdiagram adatcímke-elhelyezésének vezérlője](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Adatfeliratok formázása elkülönülten minden mértéknél kombinált diagramban](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Új, rugalmasabb és több módon formázható vizualizáció-fejléc](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Háttérkép formázása](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Elemleírások a táblához és mátrixhoz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Vizualizációk elemleírásainak kikapcsolása](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Szeletelő akadálymentessége](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [A Formázás panel fejlesztései](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Lépcsőzetes vonal támogatása vonal- és kombinált diagramokhoz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [A rendezési felület fejlesztései](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Jelentések nyomtatása az Exportálás PDF-be funkcióval (a Power BI Desktopban)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Könyvjelzőcsoportok létrehozása](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Szűrő átértékelése](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Jelentésoldal elemleírásai](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Elemzések

- [Új DAX-függvény: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Mérték részletezése](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Feltételes formázás másik mező alapján](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Feltételes formázás értékek alapján](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modellezés

- [Szűrés és rendezés adatnézetben](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Továbbfejlesztett területi formázás](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Adatkategóriák mértékekhez](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Statisztikai DAX-függvények](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>2018. máj.

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Az iOS-es Power BI-mobilalkalmazások jelentéskészítő kiszolgálóhoz való távoli konfigurálása

Rendszergazdaként mostantól a cég MDM eszközével távolról konfigurálhatja a Power BI iOS-es mobilalkalmazásának egy jelentéskészítő kiszolgálóhoz való hozzáférését. További részleteket [Az iOS-es Power BI-mobilalkalmazás jelentéskészítő kiszolgálóhoz való távoli hozzáférésének konfigurálása](configure-powerbi-mobile-apps-remote.md) című témakörben talál.

## <a name="march-2018"></a>2018. március

A Power BI Desktop alkalmazás Power BI jelentéskészítő kiszolgálóhoz optimalizált verziója nagyszámú új szolgáltatással bővült a 2018. márciusi kiadásban. Az új szolgáltatások, területekre osztva:

- [Vizualizációk](#visuals-updates)
- [Jelentéskészítés](#reporting)
- [Elemzés](#analytics)
- [Teljesítmény](#performance)
- [Jelentéskészítő kiszolgáló](#report-server)
- [Továbbiak](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>A 2018. márciusi kiadás kiemelt funkciói

Az új szolgáltatások hosszú listájából az alábbiak különösen érdekesek.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Szabályalapú feltételes formázás táblához és mátrixhoz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Táblán vagy mátrixon alapuló egyéni üzleti logika segítségével szabályokat hozhat létre, melyekkel feltételesen formázhatja az oszlopok háttérszínét és betűszínét.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Oldalak megjelenítése és elrejtése](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Előfordulhat, hogy a jelentését mások számára is elérhetővé szeretné tenni, de egyes oldalak még nem készültek el teljesen. Mostantól elrejtheti őket, amíg el nem készülnek. Vagy másik lehetőségként elrejtheti az oldalakat a normál navigációból, hogy az olvasók továbbra is elérhessék őket könyvjelzők vagy részletezés segítségével.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Könyvjelzőkezelés](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Könyvjelzők létrehozásával mostantól egyéni információkat állíthat össze a jelentésében lévő adatokból.

- [Keresztkiemelés könyvjelzőkhöz:](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting) A könyvjelzők fenntartják és megjelenítik a jelentésoldalak keresztkiemelt állapotát a könyvjelző létrehozásakor aktuális állapot szerint.
- [További lehetőségek könyvjelzőkkel:](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility) A könyvjelzők tükrözik a jelentésben beállított tulajdonságokat, és csak a választott vizualizációkra vannak hatással.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Többszörös kiválasztású adatpontok több diagramra](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Több adatpontot is kiválaszthat több diagramon, és a teljes oldalra alkalmazhat keresztszűrést.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Szeletelők szinkronizálása több jelentésoldalon](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

A szeletelők alkalmazhatók egy, kettő vagy több oldalra is a jelentésben.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Gyorsmérők](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Létrehozhat mértékeket meglévő mértékek és táblabeli numerikus oszlopok alapján.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Más vizualizációk szűrése részletezéskor](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Amikor részletezi egy vizualizáció egy kategóriáját, mostantól az adott oldal összes vizualizációját szűrheti ugyanazon kategória alapján.

### <a name="visuals-updates"></a>Vizualizációk frissítései

- [Cellaigazítás táblához és mátrixhoz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Megjelenítési egységek és precíziós vezérlők a tábla- és mátrixoszlopokhoz](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Adatcímkék túlcsordulása sáv- és oszlopdiagramot tartalmazó vizualizációknál](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [A Descartes-féle és térképes vizualizációk adatcímkéi háttérszínének vezérlése](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Sáv- és oszlopdiagram kitöltésének vezérlése](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Diagramokon belüli tengelycímkék területének növelése](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Pontvizualizáció az X és az Y tengely szerinti csoportosítással](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Nagy sűrűségű mintavétel szélességen és hosszúságon alapuló térképekhez](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Rugalmas szeletelők](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Relatív dátumszeletelő rögzített kezdőidejének hozzáadása](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Jelentéskészítés

- [Vizualizációs fejléc kikapcsolása jelentések olvasási nézetében](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Jelentési lehetőségek lassú adatforrásokhoz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Vizualizációk alapértelmezett elhelyezésének javítása](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [A vizualizációk rendezésének vezérlése a kijelöléspanelen keresztül](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Objektumok zárolása a jelentésben](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Keresés a Formázás és Elemzés panelen](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Mezőtulajdonságok panelje és mezőleírások](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Elemzések

- [UTCNOW() és UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Egyéni dátumtábla megjelölése](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Más vizualizációk szűrése részletezéskor](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Cellaszintű formázás többsoros kártyákhoz készült többdimenziós AS-modellekhez](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Teljesítmény

- [Javított szűrési teljesítmény](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Javított DirectQuery-teljesítmény](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Javított megnyitási és mentési teljesítmény](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Továbbfejlesztett „Adatot nem tartalmazó elemek megjelenítése” funkció](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Jelentéskészítő kiszolgáló

#### <a name="export-to-accessible-pdf"></a>Exportálás akadálymentes PDF-fájlba

Mostantól a többoldalas (RDL) jelentéseket akadálymentes/címkézett PDF-fájlba is exportálhatja. Ezeknek a fájloknak a mérete nagyobb, de a képernyőolvasók és más kisegítő technológiák könnyebben tudják olvasni a tartalmukat, illetve könnyebben tudnak navigálni a fájlban. Az akadálymentes PDF-eket az **AccessiblePDF** eszközinformációs beállítás **Igaz** értékre állításával engedélyezheti. Lásd: [PDF-fájlok eszközinformációs beállításai](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) és [Eszközinformációs beállítások módosítása](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Egyéb fejlesztések

- [Továbbfejlesztett „Oszlop felvétele példákból” funkció](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Tanácsadási szolgáltatások gyorshivatkozása](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Továbbfejlesztett hibajelentés](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Korábban észlelt hibák megtekintése](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>2017. október

### <a name="power-bi-report-data-sources"></a>Adatforrások a Power BI-jelentésekhez

Power BI jelentéskészítő kiszolgáló Power BI-jelentései többféle adatforráshoz kapcsolódhatnak. Importálhatja az adatokat és ütemezheti a frissítésüket, vagy lekérdezheti őket közvetlenül a DirectQuery vagy az SQL Server Analysis Services élő kapcsolata használatával. Az ütemezett frissítést és a DirectQuery-t támogató adatforrások listáját a "Adatforrások Power BI-jelentésekhez a Power BI jelentéskészítő kiszolgálóban" című cikk tartalmazza.

### <a name="scheduled-data-refresh-for-imported-data"></a>Importált adatok ütemezett frissítése

A Power BI jelentéskészítő kiszolgálóval ütemezett adatfrissítést állíthat be, hogy élő kapcsolat vagy a DirectQuery helyett beágyazott modellel tartsa naprakészen a Power BI-jelentések adatait. A beágyazott modellben az adatokat importálja, így azok elkülönülnek az eredeti adatforrástól. Az adatok naprakészen tartásához frissíteni kell, erről pedig az ütemezett frissítés gondoskodik. További információ: "Power BI jelentéskészítő kiszolgáló Power BI-jelentéseinek ütemezett frissítése".

### <a name="editing-power-bi-reports-from-the-server"></a>Power BI-jelentések szerkesztése a kiszolgálóról

A Power BI-jelentésfájlokat (.pbix) a kiszolgálóról is megnyithatja és szerkesztheti, de az eredetileg feltöltött fájlt kapja vissza.  Emiatt **ha a kiszolgáló frissítette az adatokat, akkor azok nem frissülnek a fájl első megnyitásakor**. Helyileg, manuálisan kell frissítenie őket, hogy lássa a változást.

### <a name="large-file-uploaddownload"></a>Nagy méretű fájlok feltöltése/letöltése

Legfeljebb 2 GB méretű fájlok tölthetők fel, bár ez a korlát alapértelmezés szerint 1 GB-ra van beállítva a jelentéskészítő kiszolgáló SQL Server Management Studio-beli (SSMS) beállításaiban.  Ezek a fájlok az adatbázisban vannak tárolva, ahogyan a SharePoint esetében, és nem igényelnek különleges konfigurációt az SQL Server-katalógusban.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Megosztott adatkészletek elérése OData-csatornákként

A megosztott adatkészletek a Power BI Desktopból OData-csatorna használatával érhetők el. További információ: [Megosztott adatkészletek elérése OData-csatornákként a Power BI jelentéskészítő kiszolgálóban](access-dataset-odata.md).

### <a name="scale-out"></a>Bővítés

Ez a kiadás támogatja a bővítést. A legjobb eredmény érdekében használjon terheléselosztót, és állítsa be a kiszolgálóaffinitást. Ne feledje, hogy a rendszer ekkor még nincs bővítésre optimalizálva, így esetleg több csomópont között replikált modelleket fog látni. Ez az összeállítás a hálózati terheléselosztó és rögzített munkamenetek nélkül is működik. Az N példányban betöltődő modell azonban nem csupán túlzott memóriahasználatot eredményez, de a kapcsolatok közötti átvitel is lassul a kérelmek között új csomópontot elérő modell átvitele miatt.  

### <a name="administrator-settings"></a>Rendszergazdai beállítások

A rendszergazdák a következő tulajdonságokat állíthatják be az SSMS-ben a kiszolgálófarm speciális tulajdonságai között:

* EnableCustomVisuals (Egyéni megjelenítések engedélyezése): True/False (Igaz/Hamis)
* EnablePowerBIReportEmbeddedModels (Power BI-jelentés beágyazott modellek engedélyezése): True/False (Igaz/Hamis)
* EnablePowerBIReportExportData (Power BI-jelentés adatexportálás engedélyezése): True/False (Igaz/Hamis)
* MaxFileSizeMb (Maximális fájlméret MB-ban): Alapértelmezett értéke jelenleg 1000
* ModelCleanupCycleMinutes (Modellek törlési ciklusa percekben): Milyen gyakran ellenőrzi a memóriából kizárandó modelleket
* ModelExpirationMinutes (Modellek lejárati ideje percekben): Mennyi idő után jár le és záródik ki a modell az utolsó használat időpontja után
* ScheduleRefreshTimeoutMinutes (Ütemezett frissítés időtúllépése percekben): Mennyi ideig tarthat egy modell adatfrissítése. Az alapértelmezett korlát két óra.  Nincs merev felső korlát.

**Az rsreportserver.config konfigurációs fájl**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>Fejlesztői API

Az SSRS 2017-hez bevezetett fejlesztői API (REST API) kibővült az Excel- és .pbix-fájloknak a Power BI jelentéskészítő kiszolgálóval való használatával. Egy lehetséges felhasználási mód fájlok program alapján történő letöltése a kiszolgálóról, frissítése majd újbóli közzététele. PowerPivot modelleket tartalmazó Excel-munkafüzetek például csak ezen a módon frissíthetők.

Érdemes tudni, hogy létezik egy új, külön API a nagyméretű fájlokhoz, amelyek a Swaggernek a Power BI jelentéskészítő kiszolgálóhoz készült verziójával frissülnek. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>Az SQL Server Analysis Services (SSAS) és a Power BI jelentéskészítő kiszolgáló memóriaigénye

A Power BI jelentéskészítő kiszolgáló már belsőleg üzemelteti az SQL Server Analysis Services szolgáltatást. Ez nem csak az ütemezett frissítésre vonatkozik. Az SSAS fenntartása nagy mértékben megnöveli a jelentéskészítő kiszolgáló memóriaigényét. Az AS.ini konfigurációs fájl megtalálható a kiszolgáló-csomópontokon, így ha jártas az SSAS használatában, módosíthatja a beállításokat, köztük a maximális memóriahasználatot és a lemezek gyorsítótárazását. További részletek: [Kiszolgálótulajdonságok az Analysis Services szolgáltatásban](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services).

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Excel-munkafüzetek megtekintése és kezelése

Az Excel és a Power BI az iparágban egyedülálló eszköz-portfóliót tartalmaz. Együttesen egyszerűbbé teszik az üzleti elemzők számára az adatok gyűjtését, formálását, elemezését és vizuális felfedezését. A Power BI-jelentéseknek a webes portálon való megtekintésén kívül az üzleti felhasználók ugyanezt már Excel-munkafüzetekkel is megtehetik a Power BI jelentéskészítő kiszolgálón, így egy helyen tehetik közzé és tekinthetik meg önkiszolgáló Microsoft BI-tartalmaikat.

A Microsoft közzétett egy [útmutató Office Online Server (OOS) Power BI jelentéskészítő kiszolgáló előzetes környezetéhez való hozzáadásához](excel-oos.md) című cikket. A mennyiségi licenc fiókkal rendelkező ügyfelek költség nélkül tölthetik le az OOS-t a Volume License Servicing Centerből, és csak megtekintési funkciókhoz férnek hozzá. Konfigurálás után a felhasználók a következő követelményeknek megfelelő Excel-munkafüzeteket tekinthetnek meg és kezelhetnek:

* Nem függenek külső adatforrástól
* Élő kapcsolatuk van egy külső SQL Server Analysis Services-adatforrással
* PowerPivot-adatmodellel rendelkeznek

### <a name="support-for-new-table-and-matrix-visuals"></a>Támogatják az új táblázat és mátrix vizualizációkat

A Power BI jelentéskészítő kiszolgáló már támogatja a Power BI új táblázat és mátrix vizualizációit. Az ezeket a vizualizációkat tartalmazó jelentések készítéséhez a 2017. októberi kiadásra frissített Power BI Desktop szükséges. Az új verzió nem telepíthető a Power BI Desktop (2017. június) kiadása mellé. A Power BI Desktop legújabb verziója a [Power BI jelentéskészítő kiszolgáló letöltési oldal](https://powerbi.microsoft.com/report-server/) **Speciális letöltési beállítások** eleme alatt található.

## <a name="june-2017"></a>2017. június

* Általánosan elérhető (GA) a Power BI jelentéskészítő kiszolgáló.

## <a name="may-2017"></a>2017. május

* Elérhető a Power BI jelentéskészítő kiszolgáló előzetes verziója
* Power BI-jelentések helyszíni közzétételének lehetősége
  * egyéni vizualizációk támogatása
  * **Élő Analysis Services-kapcsolatok** támogatása, de további adatforrások később várhatók.
  * A Power BI mobilalkalmazás frissítése a Power BI jelentéskészítő kiszolgálón tárolt Power BI-jelentések megjelenítéséhez
* Továbbfejlesztett együttműködés megjegyzéseket tartalmazó jelentésekben

## <a name="next-steps"></a>Következő lépések

[Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md) 
[Rendszergazdai kézikönyv](admin-handbook-overview.md)  
[A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md)  
[A Jelentéskészítő telepítése](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Az SQL Server Data Tools (SSDT) letöltése](http://go.microsoft.com/fwlink/?LinkID=616714)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)