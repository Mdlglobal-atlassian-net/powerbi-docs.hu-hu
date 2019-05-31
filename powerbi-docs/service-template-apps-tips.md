---
title: Tippek sablonalkalmazások készítéséhez a Power BI-ban (előzetes verzió)
description: Tippek lekérdezések, adatmodellek, jelentések és irányítópultok létrehozásához, hogy jó sablonalkalmazásokat készíthessen
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/19/2019
ms.author: maggies
ms.openlocfilehash: 83049a16ecd42b41375da57a5a99a374596a9846
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514863"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>Tippek sablonalkalmazások készítéséhez a Power BI-ban (előzetes verzió)

Ha [sablonalkalmazást készít](service-template-apps-create.md) a Power BI-ban, annak részét képezi a munkaterület létrehozásához, annak teszteléséhez és üzemi környezetbe helyezéséhez szükséges logisztika. De a másik fontos rész nyilvánvalóan a jelentés és az irányítópult elkészítése. Az elkészítési folyamatot négy fő összetevőre bonthatjuk. Az ezeken az összetevőkön végzett munka lehetővé teszi a lehető legjobb sablonalkalmazás létrehozását:

* A **lekérdezésekkel** [csatlakoztathatja](desktop-connect-to-data.md) és [átalakíthatja](desktop-query-overview.md) az adatokat, valamint [paramétereket](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) határozhat meg. 
* Az **adatmodell** a [kapcsolatok](desktop-create-and-manage-relationships.md) és [mértékek](desktop-measures.md) létrehozását, valamint a Kérdések és válaszok fejlesztését teszi lehetővé.  
* A **[jelentésoldalak](desktop-report-view.md)** vizualizációkat és szűrőket tartalmaznak, amelyek betekintést nyújtanak az adatokba.  
* Az **[irányítópultok](consumer/end-user-dashboards.md)** és a [csempék](service-dashboard-create.md) a belefoglalt elemzések áttekintésére adnak lehetőséget.
* Mintaadatok lehetővé teszi az alkalmazás észlelhető azonnal a telepítés után.

Az egyes összetevőket meglévő Power BI-funkciókként ismerheti. Sablonalkalmazás készítésekor további szempontokat is figyelembe kell venni minden egyes összetevőnél. További részleteket az alábbi szakaszokban talál.

<a name="queries"></a>

## <a name="queries"></a>Lekérdezések
A sablonalkalmazások esetében a Power BI Desktopban fejlesztett lekérdezésekkel lehet az adatforráshoz csatlakozni és adatokat importálni. Ezekre a lekérdezésekre szükség van a konzisztens sémák visszaadásához, valamint az ütemezett adatfrissítés esetében is támogatottak (a DirectQuery nem támogatott).

### <a name="connect-to-your-api"></a>Csatlakozás az API-hoz
Első lépésként csatlakoznia kell az API-hoz a Power BI Desktopból, hogy megkezdhesse a lekérdezések felépítését.

A Power BI Desktopban részét képező azonnal használható Adatösszekötőkkel csatlakozhat az API-hoz. A webes adatösszekötővel (Adatok lekérése -> Web) csatlakozhat a Rest API-hoz, az OData összekötővel (Adatok lekérése -> OData-csatorna) pedig az OData-csatornához. Ezek az összekötők csak akkor állnak használatra készen, ha az API támogatja az Alapszintű hitelesítést.

> [!NOTE]
> Ha az API más hitelesítéstípusokat használ, például az OAuth 2.0-t vagy webes API-kulcsot, akkor saját adatösszekötőt kell fejlesztenie, hogy a Power BI Desktop sikeresen csatlakozhasson az API-hoz, és végrehajthassa a hitelesítést. Az egyéni összekötő hozzá kell adni ahhoz, hogy a sablon telepítő elérni PBI-szolgáltatáshoz. <br> A sablonalkalmazáshoz a saját adatösszekötő fejlesztésével kapcsolatos részleteket az [Adatösszekötők dokumentációjában](https://aka.ms/DataConnectors) talál. 
>
>

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
Sablon alkalmazások, az alkalmazás létrehozása fázis részeként becsomagolja a gyorsítótárazott adatok a munkaterületen, az alkalmazás részeként:

* Lehetővé teszi, hogy a telepítő a funkciók és az alkalmazás célját megértéséhez adatok összekapcsolása előtt.
* Létrehoz egy szolgáltatás, amely a telepítő részletesebb megismerése alkalmazásképességeket, ami az alkalmazás adatkészlet csatlakoztatása.

Azt javasoljuk, hogy minőségi mintaadatok kellene az alkalmazás létrehozása előtt. Győződjön meg arról, a jelentéskészítő alkalmazás és az irányítópultok adatokkal van feltöltve.

## <a name="publishing-on-appsource"></a>Közzététel az appsource-on
Sablon alkalmazások tehetők közzé az appsource-on, mielőtt beküldi az alkalmazást az appsource-ban az alábbiakra:

* Ellenőrizze, hogy a mintaadatokat, amelyek segítségével megismerheti, mit teheti meg az alkalmazás a telepítő vonzó sablonalapú alkalmazásként hoz létre (üres jelentés és irányítópulton nem jóváhagyott lesz).
Sablon alkalmazásokat támogatja a mintaalkalmazások adatok egyetlen, mindenképpen jelölje be a statikus alkalmazás jelölőnégyzetet. [További információ](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Az érvényesítés csapat kövesse, amely tartalmazza a hitelesítő adatok és az adatokhoz való csatlakozáshoz szükséges paramétereket utasítás rendelkezik.
* Alkalmazás tartalmaznia kell az alkalmazás ikonjára a Power bi-ban és a CPP ajánlatát. [További információ](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* A kezdőlap konfigurálva. [További információ](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Ügyeljen arra, hogy kövesse a dokumentáció a [Power BI alkalmazás ajánlat](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
* Abban az esetben, ha egy irányítópult az alkalmazás része, ellenőrizze, hogy nem üres.
* Telepítse az alkalmazást, mielőtt elküldené azokat az alkalmazásra mutató hivatkozás segítségével, győződjön meg arról, hogy az adatkészlet csatlakozhat, és az alkalmazás felhasználói felülete, a tervek szerint.
* Mielőtt feltöltené bpix a sablon alkalmazás-munkaterületre, ügyeljen arra, hogy távolítsa el a felesleges kapcsolatokat.
* Hajtsa végre a Power BI [ajánlott eljárások jelentések és Vizualizációk megalkotásához](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-best-practices) a felhasználók és az első terjesztési engedélyezett maximális gyakorolt eléréséhez.

## <a name="known-limitations"></a>Ismert korlátozások

| Funkció | Ismert korlátozás |
|---------|---------|
|Tartalom:  Adathalmazok   | Pontosan egy adatkészletnek kell jelen lennie. Csak a Power BI Desktopban (.pbix-fájlok) készült adatkészletek használata engedélyezett. <br>Nem támogatott: Más sablonalkalmazásokból származó adatkészletek, munkaterületeken átnyúló adatkészletek, lapszámozott jelentések (.rdl-fájlok), Excel-munkafüzetek |
|Tartalom: Irányítópultok | Valós idejű csempék nem engedélyezett (más szóval nem támogatott leküldéses vagy streamelési adatkészletekhez) |
|Tartalom: Adatfolyamok | Nem támogatott: Adatfolyamok |
|Fájlok tartalmai | Csak a PBIX-fájlok engedélyezettek. <br>Nem támogatott: .rdl-fájlok (lapszámozott jelentések), Excel-munkafüzetek   |
| Adatforrások | A felhőbeli ütemezett adatfrissítéshez támogatott adatforrások engedélyezettek. <br>Nem támogatott: <li> DirectQuery</li><li>Élő kapcsolatok (nem Azure AS)</li> <li>A helyszíni adatforrások (a személyes és a vállalati átjárókat nem támogatottak)</li> <li>Valós idejű (nem támogatja a leküldéses adatkészletek)</li> <li>Összetett modellek</li></ul> |
| Adatkészlet: munkaterületeken átnyúló | Munkaterületeken átnyúló adatkészletek használata nem engedélyezett  |
| Lekérdezési paraméterek | Nem támogatott: „Any” típusú paraméterek vagy „Binary” típusú blokkfrissítési művelet az adatkészlethez |
| Egyéni vizualizációk | Csak a nyilvánosan elérhető egyéni vizualizációk támogatottak. A [céges egyéni vizualizációk](power-bi-custom-visuals-organization.md) nem támogatottak |

## <a name="next-steps"></a>Következő lépések

[Mik azok a Power BI-sablonalkalmazások? (előzetes verzió)](service-template-apps-overview.md)
