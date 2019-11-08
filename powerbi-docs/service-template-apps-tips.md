---
title: Tippek sablonalkalmazások készítéséhez a Power BI-ban
description: Tippek lekérdezések, adatmodellek, jelentések és irányítópultok létrehozásához, hogy jó sablonalkalmazásokat készíthessen
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: tebercov
ms.openlocfilehash: 57d8da8bafb62f1f24598f5f0ef4cb5e3facd59b
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432122"
---
# <a name="tips-for-authoring-template-apps-in-power-bi"></a>Tippek sablonalkalmazások készítéséhez a Power BI-ban

Ha [sablonalkalmazást készít](service-template-apps-create.md) a Power BI-ban, annak részét képezi a munkaterület létrehozásához, annak teszteléséhez és üzemi környezetbe helyezéséhez szükséges logisztika. De a másik fontos rész nyilvánvalóan a jelentés és az irányítópult elkészítése. Az elkészítési folyamatot négy fő összetevőre bonthatjuk. Az ezeken az összetevőkön végzett munka lehetővé teszi a lehető legjobb sablonalkalmazás létrehozását:

* A **lekérdezésekkel** [csatlakoztathatja](desktop-connect-to-data.md) és [átalakíthatja](desktop-query-overview.md) az adatokat, valamint [paramétereket](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) határozhat meg. 
* Az **adatmodell** a [kapcsolatok](desktop-create-and-manage-relationships.md) és [mértékek](desktop-measures.md) létrehozását, valamint a Kérdések és válaszok fejlesztését teszi lehetővé.  
* A **[jelentésoldalak](desktop-report-view.md)** vizualizációkat és szűrőket tartalmaznak, amelyek betekintést nyújtanak az adatokba.  
* Az **[irányítópultok](consumer/end-user-dashboards.md)** és a [csempék](service-dashboard-create.md) a belefoglalt elemzések áttekintésére adnak lehetőséget.
* A mintaadatokkal az alkalmazás a telepítést követően azonnal felfedezhető lesz.

Az egyes összetevőket meglévő Power BI-funkciókként ismerheti. Sablonalkalmazás készítésekor további szempontokat is figyelembe kell venni minden egyes összetevőnél. További részleteket az alábbi szakaszokban talál.

<a name="queries"></a>

## <a name="queries"></a>Lekérdezések
A sablonalkalmazások esetében a Power BI Desktopban fejlesztett lekérdezésekkel lehet az adatforráshoz csatlakozni és adatokat importálni. Ezekre a lekérdezésekre szükség van a konzisztens sémák visszaadásához, valamint az ütemezett adatfrissítés esetében is támogatottak (a DirectQuery nem támogatott).

### <a name="connect-to-your-api"></a>Csatlakozás az API-hoz
Első lépésként csatlakoznia kell az API-hoz a Power BI Desktopból, hogy megkezdhesse a lekérdezések felépítését.

A Power BI Desktopban részét képező Adatösszekötőkkel csatlakozhat az API-hoz. A webes adatösszekötővel (Adatok lekérése -> Web) csatlakozhat a Rest API-hoz, az OData összekötővel (Adatok lekérése -> OData-csatorna) pedig az OData-csatornához.

> [!NOTE]
> A sablonalkalmazások jelenleg nem támogatják az egyéni összekötőket. Egyes kapcsolati helyzetek esetén ajánlatos lehet használni az Odatafeed Auth 2.0-át migráláshoz, vagy elküldheti az összekötőt hitelesítésre. Az [Adatösszekötők dokumentációjában](https://aka.ms/DataConnectors) részletes információt talál összekötők fejlesztéséről és tanúsításáról.

### <a name="consider-the-source"></a>Tartsa szem előtt a forrást
A lekérdezések határozzák meg az adatmodellben szereplő adatokat. A rendszer méretétől függően ezeknek a lekérdezéseknek szűrőket is tartalmazniuk kell, hogy az ügyfelek kezelhető mérettel legyen dolguk a vállalati forgatókönyvnek megfelelően.

A Power BI sablonalkalmazásai egyszerre több lekérdezést tudnak futtatni több felhasználó számára.  Tervezze meg előre a szabályozási és párhuzamossági stratégiáját, majd kérjen tőlünk tanácsot a sablonalkalmazás hibatűrővé tételét illetően.

### <a name="schema-enforcement"></a>Séma kényszerítése
Biztosítsa, hogy a lekérdezések ellenálljanak a rendszerben beállt változásoknak. A sémák változásai a frissítéskor tönkretehetik a modellt. Ha a forrás null/hiányzó sémaeredményt adhat vissza néhány lekérdezésben, érdemes lehet üres táblát vagy egy egyéni hibaüzenetet visszaadni, amelyet a felhasználó könnyen megért.

### <a name="parameters"></a>Paraméterek
A Power BI Desktop [paraméterei](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) lehetővé teszik, hogy a felhasználók olyan bemeneti értékeket adjanak meg, amelyek testreszabják a felhasználó által lekért adatokat. Gondoljon előre a paraméterekre, hogy elkerülje a felesleges munkát, miután időt fektetett a részletes lekérdezések vagy jelentések felépítésébe.

> [!NOTE]
> A sablonalkalmazások az „Any” és a „Binary” paraméterek kivételével minden paramétert támogatnak.
>

### <a name="additional-query-tips"></a>További lekérdezési tippek

* Győződjön meg róla, hogy minden oszlop típusa helyesen van megadva.
* Az oszlopok leíró nevekkel rendelkeznek (lásd: [Q&A](#qa)).  
* Megosztott logika esetében érdemes lehet függvényeket vagy lekérdezéseket használni.  
* Az adatvédelmi szintek jelenleg nem támogatottak a szolgáltatásban. Ha az adatvédelmi szintekkel kapcsolatos kérdést kap, szükség lehet a lekérdezés újraírására, hogy relatív elérési utakat használjon.  

## <a name="data-models"></a>Adatmodellek

A jól meghatározott adatmodellek biztosítják, hogy az ügyfelek könnyedén és intuitív módon kezelhessék a sablonalkalmazást. Hozza létre az adatmodellt a Power BI Desktopban.

> [!NOTE]
> Az alapszintű modellezés nagy részét (a típusmeghatározást, az oszlopneveket) a [lekérdezésekben](#queries) kell elvégezni.

### <a name="qa"></a>Q&A
A modellezés arra is hatással van, hogy a Q&A milyen hatékonyan tud eredményekkel szolgálni az ügyfeleknek. Mindenképpen vegyen fel szinonimákat a gyakran használt oszlopokhoz, valamint ellenőrizze, hogy az oszlopok megfelelően vannak-e elnevezve a [lekérdezésekben](#queries).

### <a name="additional-data-model-tips"></a>Adatmodellekkel kapcsolatos további tippek

Győződjön meg az alábbiakról:

* Az összes értékoszlopra formázást alkalmazott. Típusokat alkalmaz a lekérdezésekben.  
* Formázást alkalmazott az összes mértékre.
* Megadta az alapértelmezett összegzést. Különösen a „Ne legyen összegzés”-t, ha alkalmazandó (például egyedi értékeknél).  
* Adatkategóriát állított be, ahol szükséges.  
* Kapcsolatokat állított be, ha szükséges.  

## <a name="reports"></a>Jelentések
A jelentésoldalak további betekintést nyújtanak a sablonalkalmazásban szereplő adatokba. A jelentések oldalai segítségével megválaszolhatja azokat a fő üzleti kérdéseket, amelyek megoldására a sablonalkalmazást használja. Hozza létre a jelentést a Power BI Desktoppal.


### <a name="additional-report-tips"></a>Jelentésekkel kapcsolatos további tippek

* Használjon oldalanként több vizualizációt a keresztszűréshez.  
* Körültekintően igazítsa a vizualizációkat (ne legyen átfedés).  
* Az elrendezéshez az oldal legyen „4:3” vagy „16:9” módban.  
* Győződjön meg arról, hogy az összes bemutatott aggregáció numerikus értékei megfelelőek (átlagok, egyedi értékek).  
* Ellenőrizze, hogy a szeletelés eredményei észszerűek-e.  
* Ellenőrizze, hogy az embléma legalább a legfelső jelentésen szerepeljen.  
* Győződjön meg arról, hogy az elemek az ügyfél színsémáját használják a lehetséges mértékig.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Irányítópultok
Az irányítópult az ügyfelek számára a sablonalkalmazás kezelésének elsődleges helye. Meg kell jelenítenie a tartalom áttekintését, különös tekintettel az üzleti forgatókönyv fontosabb mérőszámaira.

Ha létre szeretne hozni egy irányítópultot a sablonalkalmazáshoz, egyszerűen töltse fel a PBIX-fájlt a Lekérdezés > Fájlok paranccsal, vagy tegye közzé közvetlenül a Power BI Desktopról.


### <a name="additional-dashboard-tips"></a>Irányítópultokkal kapcsolatos további tippek

* Őrizze meg ugyanazt a témát a kitűzéskor, hogy az irányítópulton lévő csempék konzisztensek legyenek.  
* Tűzzön ki egy emblémát a témához, hogy az ügyfelek tudják, honnan származik a csomag.  
* A legtöbb képernyőfelbontással működő, ajánlott elrendezés 5-6 kisméretű csempe szélességű.  
* Az irányítópult összes csempéjének megfelelő címmel/alcímmel kell rendelkeznie.  
* Érdemes megfontolni különböző csoportosítások használatát a különféle forgatókönyvekhez az irányítópulton, függőlegesen vagy vízszintesen.  

## <a name="sample-data"></a>Mintaadatok
A sablonalkalmazások az alkalmazáskészítés részeként az alkalmazásba foglalva becsomagolják a munkaterület gyorsítótárazott adatait:

* Lehetővé teszi, hogy a telepítő átlássa az alkalmazás célját és funkcióit, mielőtt adatokat csatlakoztatna.
* Olyan felhasználói élményt nyújt, amely arra ösztönzi a telepítőt, hogy részletesebben is megismerje az alkalmazás képességeit, ami az alkalmazás adatkészletének csatlakoztatásához vezet.

Azt javasoljuk, hogy minőségi mintaadatokat használjon, mielőtt létrehozná az alkalmazást. gondoskodjon arról, hogy az alkalmazás jelentése és irányítópultjai fel legyenek töltve adatokkal.

## <a name="publishing-on-appsource"></a>Közzététel az AppSource-on
A sablonalkalmazásokat közzé lehet tenni az AppSource-on. Mielőtt közzétenné az alkalmazást az AppSource-on, kövesse az alábbi útmutatót:

* A sablonalkalmazásokat érdekes mintaadatokkal töltse fel, amelyek segítenek majd a telepítőnek megérteni az alkalmazás képességeit (üres jelentés és irányítópult nem engedélyezett).
A sablonalkalmazások csak mintaadatokkal szerepelhetnek, ügyeljen rá, hogy be kell jelölnie a statikus alkalmazás jelölőnégyzetet. [További információ](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Rendelkezzen útmutatóval az érvényesítési csapat számára, amely tartalmazza az adatokhoz való csatlakozáshoz szükséges hitelesítő adatokat és paramétereket is.
* Az alkalmazásnak tartalmaznia kell egy alkalmazásikont a Power BI-ban és a CPP-ajánlatban is. [További információ](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Konfigurált kezdőlap. [További információ](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Kövesse a [Power BI-alkalmazások ajánlat](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) dokumentációját.
* Ha az alkalmazáshoz irányítópult is tartozik, ügyeljen rá, hogy az ne legyen üres.
* A beküldés előtt az alkalmazást az alkalmazáshivatkozás használatával telepítse, ellenőrizze, hogy lehet-e csatlakozni az adatkészlethez, és hogy az alkalmazás a tervek szerint használható-e.
* Mielőtt feltöltené a bpix-et a sablon munkaterületére, távolítson el minden felesleges kapcsolatot.
* Kövesse a Power BI [Ajánlott tervezési eljárások jelentésekhez és vizualizációkhoz](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-best-practices) című dokumentumában foglaltakat, hogy maximalizálhassa a felhasználókra gyakorolt hatást, és hogy jóváhagyást szerezhessen a terjesztéshez.
<!--- * In general, only application with valuable functionality can be approved for general use on AppSource. Application with sample data content only must have either a guidance or statistical value.) -->

## <a name="known-limitations"></a>Ismert korlátozások

| Funkció | Ismert korlátozás |
|---------|---------|
|Tartalom:  Adathalmazok   | Pontosan egy adatkészletnek kell jelen lennie. Csak a Power BI Desktopban (.pbix-fájlok) készült adatkészletek használata engedélyezett. <br>Nem támogatott: Más sablonalkalmazásokból származó adatkészletek, munkaterületeken átnyúló adatkészletek, lapszámozott jelentések (.rdl-fájlok), Excel-munkafüzetek |
|Tartalom: Irányítópultok | A valós idejű csempék nem engedélyezettek (más szóval nem támogatott a leküldéses vagy a folyamatos átvitelű adatkészlet) |
|Tartalom: Adatfolyamok | Nem támogatott: Adatfolyamok |
|Fájlok tartalmai | Csak a PBIX-fájlok engedélyezettek. <br>Nem támogatott: .rdl-fájlok (lapszámozott jelentések), Excel-munkafüzetek   |
| Adatforrások | A felhőbeli ütemezett adatfrissítéshez támogatott adatforrások engedélyezettek. <br>Nem támogatott: <li> DirectQuery</li><li>Élő kapcsolatok (nem Azure AS)</li> <li>Helyszíni adatforrások (a személyes és a vállalati átjárók nem támogatottak)</li> <li>Valós idejű (a leküldéses adatkészlet nem támogatott)</li> <li>Összetett modellek</li></ul> |
| Adatkészlet: munkaterületeken átnyúló | Munkaterületeken átnyúló adatkészletek használata nem engedélyezett  |
| Lekérdezési paraméterek | Nem támogatott: „Any” típusú paraméterek vagy „Binary” típusú blokkfrissítési művelet az adatkészlethez |
| Egyéni vizualizációk | Csak a nyilvánosan elérhető egyéni vizualizációk támogatottak. A [céges egyéni vizualizációk](power-bi-custom-visuals-organization.md) nem támogatottak |

## <a name="next-steps"></a>Következő lépések

[Mik azok a Power BI-sablonalkalmazások?](service-template-apps-overview.md)
