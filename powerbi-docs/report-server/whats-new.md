---
title: A Power BI jelentéskészítő kiszolgáló újdonságai
description: A Power BI jelentéskészítő kiszolgáló újdonságainak bemutatása. A cikk a főbb funkciókat ismerteti és az új elemek kibocsátásakor frissül.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: 526a971817c50599bf77ae085f3d5ff07294b25b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858740"
---
# <a name="whats-new-in-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgáló újdonságai

A Power BI jelentéskészítő kiszolgáló és a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop újdonságainak bemutatása. A cikk a főbb funkciókat ismerteti, és minden új kibocsátásakor frissül.

Az újdonságokra vonatkozó Power BI-információk:

* [A Power BI szolgáltatás újdonságai](../service-whats-new.md)
* [A Power BI Desktop újdonságai](../desktop-latest-update.md)
* [A Power BI-mobilalkalmazások újdonságai](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="september-2019"></a>2019. szeptember

Az összes új funkció részleteit megtalálhatja a [Power BI jelentéskészítő kiszolgáló 2019. szeptemberi](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) blogbejegyzésében.

A Power BI jelentéskészítő kiszolgáló 2019. szeptemberi frissítése számos Power BI-jelentésfunkciót tartalmaz. Kiemelünk néhányat a legfontosabbak közül:

- **Vizualizációszintű szűrők szeletelőkhöz** Vizualizációszintű szűrők vehetők fel szeletelőkhöz. Ugyanúgy működik, mint a többi vizualizációszintű szűrő: csak magát a szeletelőt szűri, más vizualizációkat nem. Ez a szűrő jól használható az üres mezők kiszűrésére, vagy ha mértékszűrőket kell használnia.
- **Ikonkészletek táblázatokhoz és mátrixokhoz** A fő teljesítménymutatók (KPI) ikonjaival különböző ikonokat jeleníthet meg táblázatokban és mátrixokban, az Excel ikonkészleteihez hasonlóan.
- **Vizualizációk csoportba foglalása** A vizualizációk, alakzatok, szövegdobozok, képek és gombok mostantól ugyanúgy csoportba foglalhatók egy jelentésoldalon, mint a PowerPointban. A csoportba foglalt objektumok együtt méretezhetők át és mozgathatók. A csoportba foglalás megkönnyíti az olyan jelentésekkel végzett munkát, amelynek egy-egy oldalán sok objektum van egymásra rétegezve.
- **Új alapértelmezett témák** Az új JSON-témabeállításokkal összhangban frissítettük a jelentésekhez elérhető témákat, és megváltoztattuk az új jelentések alapértelmezett témáját. Az új alapértelmezett téma jobban illeszkedik a Microsoft tervezési nyelvéhez és a vizualizációkhoz ajánlott eljárásokat követi. 
- **A panelek frissített megjelenése** Sok frissítést végeztünk a felhasználói felületen. Világosabb színűre módosítottuk az összes panelt, a láblécet és a nézetváltót, frissítettük a térközöket és új ikonokat vezettünk be. Az új megjelenés a teljes felhasználói felület frissítésének első állomása.

A funkciók teljes listája a következő. 

### <a name="reporting"></a>Jelentéskészítés

- A panelek frissített megjelenése
- Vizualizációszintű szűrők szeletelőkhöz
- A teljesítményelemző panel rendezése
- Vizualizáció-fejléc elemleírásai
- Táblázat- és mátrix-címkék teljes testreszabása
- A hierarchiaszeletelő szeletelőszinkronizálási támogatása
- Egységes betűméretek a vizualizációkban
- Ikonkészletek táblázatokhoz és mátrixokhoz
- Százalék támogatása a feltételes formázási szabályokhoz
- Általánosan elérhető az új szűrőpanel
- Adatszínek támogatása lejátszási tengely pontdiagramon való használatakor
- Jobb teljesítmény relatív dátum és legördülő szeletelők használatakor
- Vizualizációk csoportba foglalása
- Szín- és szövegosztályok témákban
- Új alapértelmezett témák

### <a name="analytics"></a>Elemzés

- Egyéni formátumsztringek
- A formázási beállítások feltételes formázási frissítései

    - Háttér- és címszínek vizualizációkhoz
    - Kártyaszínek
    - Kijelző kitöltése és színei
    - Helyettesítő szöveg
    - Szegély színe

- Feltételes formázási figyelmeztetések
- Keresztrészletezési felderíthetőség fejlesztése
- Új DAX-kifejezések: REMOVEFILTERS és CONVERT
- Új DAX összehasonlító operátor: ==

### <a name="data-preparation"></a>Adatok előkészítése

- Az M IntelliSense fejlesztései
- Új átalakítás: Oszlop felosztása pozíció alapján
- Másolás a vágólapra adatprofil-készítésből


## <a name="may-2019-power-bi-desktop-for-power-bi-report-server"></a>2019. május: A Power BI jelentéskészítő kiszolgálóhoz készült Power BI Desktop

Az összes új funkció részleteit megtalálhatja a [Power BI jelentéskészítő kiszolgáló 2019. májusi](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) blogbejegyzésében.

Kiemelünk néhányat a kiadás legfontosabb részletei közül:

### <a name="performance-analyzer"></a>Teljesítményelemző 

Ha a jelentés a vártnál lassabban fut, kipróbálhatja a Power BI Desktop Teljesítményelemzőjét. Ez az elindításakor naplófájl hoz létre a jelentéssel végzett összes művelettel kapcsolatos információkkal. További információk a [Teljesítményelemzőről](../desktop-performance-analyzer.md).

### <a name="new-modeling-view"></a>Új modellezési nézet

A Power BI Desktop új Modellezés nézetében sok táblát tartalmazó, összetett adathalmazokat tekinthet meg és kezelhet. Ennek lényeges eleme például a többszörös diagramelrendezés, valamint az oszlopok, mértékek és táblázatok csoportos szerkesztése. További tudnivalók a [Modellezés nézetről](../desktop-modeling-view.md).

### <a name="accessible-visual-interaction"></a>Vizualizációk akadálymentes használata

Mostantól a beépített vizualizációk többségében a billentyűzettel navigálva is elérhetők az adatpontok. További tudnivalók a [Power BI-jelentések akadálymentességéről](../desktop-accessibility.md).

### <a name="conditional-formatting-titles-and-web-url-actions"></a>Címek feltételes formázása és webes URL-műveletek

A Power BI-jelentések interaktívak. Kézenfekvő, hogy a jelentések címe is dinamikus legyen, és tükrözze a jelentés aktuális állapotát. Ugyanazzal a kifejezésalapú formázással teheti dinamikussá a gombok, alakzatok és képek URL-címeit. További információ a [kifejezésalapú címekről](../desktop-conditional-format-visual-titles.md).

### <a name="cross-highlight-by-axis-labels"></a>Keresztkiemelés tengelyfeliratok alapján

Egy vizualizáció kategóriatengely-feliratainak kijelölésével keresztkiemelést végezhet az oldal más elemein, mintha az adatpontokat jelölte volna ki a vizualizáción. További tudnivalók a [keresztkiemelésről](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

### <a name="all-the-new-features"></a>Az összes új funkció

Az alábbi lista az összes új funkciót felsorolja:

### <a name="reporting"></a>Jelentéskészítés

- Keresztkijelölés a vonaldiagramok egyetlen pontján 
- Címek több sorba tördelése 
- A vizualizáció alapműveletének módosítása keresztszűrésre
- Lekerekített sarkú vizualizációszegélyek 
- Egyetlen elem kijelölése szeletelő  
- Intenzitástérkép támogatása a Bing Térképekhez  
- Keresztkiemelés tengelyfeliratok alapján  
- Elemleírások alapértelmezett formázása  
- Statikus webes URL-címek támogatása gombokhoz, alakzatokhoz és képekhez  
- Oldaligazítási beállítások   
- A Kijelölés panel fejlesztései  
- Vizualizációk akadálymentes használata  
- Vizualizációk címeinek feltételes formázása  
- A gombok, alakzatok és képek webes URL-műveleteinek feltételes formázása
- Teljesítményelemző panel
- Navigálás billentyűzettel táblákban és mátrixokban
- Vonal-adatfelirat helyzetének szabályozása
- KPI vizuális kijelző szövegméretének szabályozása

### <a name="analytics"></a>Elemzés

- A dátumok hierarchikus megjelenítése már általánosan elérhető  

### <a name="modeling"></a>Modellezés

- Mostantól általánosan elérhető az új modellezési nézet
- Új DAX-függvények
- Az ALLSELECTED DAX-függvény frissítése
- Dátumtáblák automatikus létrehozásának letiltása új jelentések esetén

## <a name="may-2019-power-bi-report-server"></a>2019. május: Power BI jelentéskészítő kiszolgáló

### <a name="support-for-trusted-visuals"></a>Megbízható vizualizációk támogatása

A Power BI jelentéskészítő kiszolgálót a megbízható vizualizációk támogatásával egészítettük ki. Jelenleg a Mapbox és PowerOn vizualizációkat támogatjuk. Az ESRI, a Visio és a PowerApps ebben a kiadásban nem támogatott.

### <a name="improved-security-features"></a>Továbbfejlesztett biztonsági funkciók

A **RestrictedResourceMimeTypeForUpload** használatával a rendszergazdák vesszővel tagolt listában adhatják meg a letiltott MIME-típusokat (például text/html).

## <a name="january-2019"></a>2019. január

Az alábbi funkciók támogatása a Power BI-jelentésekben:

[**Sorszintű biztonság**](row-level-security-report-server.md) A Power BI jelentéskészítő kiszolgálóban a sorszintű biztonság (RLS) használatával korlátozható adott felhasználók adatokhoz való hozzáférése. A szűrők a sorok szintjén korlátozzák az adatok elérését, és szerepkörökön belül határozhat meg szűrőket.

[**Kibontás és összecsukás mátrix sorazonosítókban**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Most már lehetőség van az egyes sorazonosítók kibontására és összecsukására, amely az egyik leggyakrabban kért funkció volt a vizualizációknál.

[**Másolás és beillesztés .pbix-fájlok között**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) A vizualizációk másolhatók .pbix-fájlok között akár a vizualizáció helyi menüjét használva, akár a szokásos Ctrl+C billentyűparanccsal, majd utána a Ctrl+V használatával másik jelentésbe illeszthető be.

[**Útmutatók intelligens igazításhoz**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Ha objektumokat mozgat a jelentésoldalon, intelligens igazítási útmutatók jelennek majd meg hasonlóan ahhoz, ahogyan az a PowerPointban történik, így egyszerűbben tudja az oldalon az objektumokat igazítani. Az intelligens útmutatók minden esetben megjelennek, amikor húzással áthelyez vagy átméretez valamit az oldalon. Ha egy objektumot egy másik közelébe helyez, akkor az a másik objektumhoz igazítva a megfelelő pozícióba illeszkedik.

**Kisegítő lehetőségek** Olyan sok kisegítő lehetőség van, hogy a listázás nehéz. Elérhetőek például a [mezőlistázási panel kisegítő lehetőségei](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). A mezőlistázási panel teljes mértékben akadálymentes. A panelen navigálni lehet kizárólag billentyűzetet és a képernyőolvasót használva is, a helyi menüvel pedig mezőket lehet hozzáadni a jelentésoldalhoz.

#### <a name="custom-visuals"></a>Egyéni vizualizációk

- A kiadás a 2.3 API-verziót tartalmazza.

### <a name="administrator-settings"></a>Rendszergazdai beállítások

A rendszergazdák a következő tulajdonságokat állíthatják be az SSMS-ben a kiszolgálófarm speciális tulajdonságai között:

**AllowedResourceExtensionsForUpload** Lehetőség a jelentéskészítő kiszolgálóra feltölthető erőforrások bővítményeinek beállítására. A beépített fájltípusok bővítményeit (például &ast;.rdl vagy &ast;.pbix) nem szükséges belefoglalni. Az alapértelmezés „&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx”. 

**SupportedHyperlinkSchemes** Azoknak az URI-sémáknak a vesszővel tagolt listáját állítja be, amelyeket definiálni lehet a megjeleníthető hiperhivatkozásos műveleteknél, vagy „&ast;” az összes hiperhivatkozásos séma engedélyezéséhez. A „http,https” beállítással például engedélyezni lehet a „https://www. contoso.com” helyre mutató hivatkozásokat, de eltávolítja a „mailto:bill@contoso.com” vagy “javascript:window.open(‘www.contoso.com’, ‘_blank’)” hivatkozásokat. Az alapértelmezés „&ast;”.

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

### <a name="analytics"></a>Elemzés

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

- [Keresztkiemelés könyvjelzőkhöz](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): A könyvjelzők fenntartják és megjelenítik a jelentésoldalak keresztkiemelt állapotát a könyvjelző létrehozásakor aktuális állapot szerint.
- [További lehetőségek könyvjelzőkkel](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): A könyvjelzők tükrözik a jelentésben beállított tulajdonságokat, és csak a választott vizualizációkra vannak hatással.

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

### <a name="analytics"></a>Elemzés

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

* EnableCustomVisuals: Igaz/Hamis
* EnablePowerBIReportEmbeddedModels: Igaz/Hamis
* EnablePowerBIReportExportData: Igaz/Hamis
* MaxFileSizeMb: Az alapértelmezett érték jelenleg 1000
* ModelCleanupCycleMinutes: Milyen gyakran ellenőrzi a memóriából kizárandó modelleket
* ModelExpirationMinutes Mennyi idő után jár le és záródik ki a modell az utolsó használat időpontja után
* ScheduleRefreshTimeoutMinutes: Mennyi ideig tarthat egy modell adatfrissítése. Az alapértelmezett korlát két óra.  Nincs merev felső korlát.

**Az rsreportserver.config konfigurációs fájl**

```xml
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

Ezekből a forrásokból folyamatosan értesülhet a Power BI jelentéskészítő kiszolgáló új funkcióiról.

* [Microsoft Power BI-blog](https://powerbi.microsoft.com/blog/)
* [Az SQL Server Reporting Services csapat blogja](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* A [Guy in a Cube YouTube-csatorna](https://aka.ms/guyinacube)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
