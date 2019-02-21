---
title: Tippek sablonalkalmazások készítéséhez a Power BI-ban (előzetes verzió)
description: Tippek lekérdezések, adatmodellek, jelentések és irányítópultok létrehozásához, hogy jó sablonalkalmazásokat készíthessen
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/05/2019
ms.author: maggies
ms.openlocfilehash: 282638c7c1c8a60ee93292602766d63fd0fe436e
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249856"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>Tippek sablonalkalmazások készítéséhez a Power BI-ban (előzetes verzió)

Ha [sablonalkalmazást készít](service-template-apps-create.md) a Power BI-ban, annak részét képezi a munkaterület létrehozásához, annak teszteléséhez és üzemi környezetbe helyezéséhez szükséges logisztika. De a másik fontos rész nyilvánvalóan a jelentés és az irányítópult elkészítése. Az elkészítési folyamatot négy fő összetevőre bonthatjuk. Az ezeken az összetevőkön végzett munka lehetővé teszi a lehető legjobb sablonalkalmazás létrehozását:

* A **lekérdezésekkel** [csatlakoztathatja](desktop-connect-to-data.md) és [átalakíthatja](desktop-query-overview.md) az adatokat, valamint [paramétereket](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) határozhat meg. 
* Az **adatmodell** a [kapcsolatok](desktop-create-and-manage-relationships.md) és [mértékek](desktop-measures.md) létrehozását, valamint a Kérdések és válaszok fejlesztését teszi lehetővé.  
* A **[jelentésoldalak](desktop-report-view.md)** vizualizációkat és szűrőket tartalmaznak, amelyek betekintést nyújtanak az adatokba.  
* Az **[irányítópultok](consumer/end-user-dashboards.md)** és a [csempék](service-dashboard-create.md) a belefoglalt elemzések áttekintésére adnak lehetőséget.  

Az egyes összetevőket meglévő Power BI-funkciókként ismerheti. Sablonalkalmazás készítésekor további szempontokat is figyelembe kell venni minden egyes összetevőnél. További részleteket az alábbi szakaszokban talál.

<a name="queries"></a>

## <a name="queries"></a>Lekérdezések
A sablonalkalmazások esetében a Power BI Desktopban fejlesztett lekérdezésekkel lehet az adatforráshoz csatlakozni és adatokat importálni. Ezekre a lekérdezésekre szükség van a konzisztens sémák visszaadásához, valamint az ütemezett adatfrissítés esetében is támogatottak (a DirectQuery nem támogatott).

### <a name="connect-to-your-api"></a>Csatlakozás az API-hoz
Első lépésként csatlakoznia kell az API-hoz a Power BI Desktopból, hogy megkezdhesse a lekérdezések felépítését.

A Power BI Desktopban részét képező azonnal használható Adatösszekötőkkel csatlakozhat az API-hoz. A webes adatösszekötővel (Adatok lekérése -> Web) csatlakozhat a Rest API-hoz, az OData összekötővel (Adatok lekérése -> OData-csatorna) pedig az OData-csatornához. Ezek az összekötők csak akkor állnak használatra készen, ha az API támogatja az Alapszintű hitelesítést.

> [!NOTE]
> Ha az API más hitelesítéstípusokat használ, például az OAuth 2.0-t vagy webes API-kulcsot, akkor saját adatösszekötőt kell fejlesztenie, hogy a Power BI Desktop sikeresen csatlakozhasson az API-hoz, és végrehajthassa a hitelesítést. A sablonalkalmazáshoz a saját adatösszekötő fejlesztésével kapcsolatos részleteket az [Adatösszekötők dokumentációjában](https://aka.ms/DataConnectors) talál. 
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
>


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

> [!NOTE]
> Egy sablonalkalmazásban csak egy jelentés szerepelhet, tehát használja ki a különböző oldalakat a forgatókönyv egyes szakaszainak feliratozásához.
>
>

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

> [!NOTE]
> A sablonalkalmazásokkal jelenleg sablonalkalmazásonként egy jelentés és adatkészlet használható. Ne rögzítsen több jelentésből/adatkészletből származó tartalmat a sablonalkalmazásban használt irányítópultra.
>
>

### <a name="additional-dashboard-tips"></a>Irányítópultokkal kapcsolatos további tippek

* Őrizze meg ugyanazt a témát a kitűzéskor, hogy az irányítópulton lévő csempék konzisztensek legyenek.  
* Tűzzön ki egy emblémát a témához, hogy az ügyfelek tudják, honnan származik a csomag.  
* A legtöbb képernyőfelbontással működő, ajánlott elrendezés 5-6 kisméretű csempe szélességű.  
* Az irányítópult összes csempéjének megfelelő címmel/alcímmel kell rendelkeznie.  
* Érdemes megfontolni különböző csoportosítások használatát a különféle forgatókönyvekhez az irányítópulton, függőlegesen vagy vízszintesen.  

## <a name="known-limitations"></a>Ismert korlátozások

| Funkció | Ismert korlátozás |
|---------|---------|
|Tartalom:  Adathalmazok   | Pontosan egy adatkészletnek kell jelen lennie. Csak a Power BI Desktopban (.pbix-fájlok) készült adatkészletek használata engedélyezett. <br>Nem támogatott: Más sablonalkalmazásokból származó adatkészletek, munkaterületeken átnyúló adatkészletek, lapszámozott jelentések (.rdl-fájlok), Excel-munkafüzetek |
|Tartalom: Jelentések     | Legfeljebb egy jelentés    |
| Tartalom: Irányítópultok | Legfeljebb egy, nem üres irányítópult <br>Nem támogatott: Valós idejű csempék (más szóval nem támogatott a PushDataset vagy a pubnub) |
| Tartalom: Adatfolyamok | Nem támogatott: Adatfolyamok |
| Fájlok tartalmai | Csak a PBIX-fájlok engedélyezettek. <br>Nem támogatott: .rdl-fájlok (lapszámozott jelentések), Excel-munkafüzetek   |
| Adatforrások | A felhőbeli ütemezett adatfrissítéshez támogatott adatforrások engedélyezettek. <br>Nem támogatott: <br>DirectQuery <br>Élő kapcsolatok (nem Azure AS) <br>Helyszíni adatforrások (a személyes és a vállalati átjárók nem támogatottak) <br>Valós idejű (a pushdataset nem támogatott) <br>Összetett modellek |
| Adatkészlet: munkaterületeken átnyúló | Munkaterületeken átnyúló adatkészletek használata nem engedélyezett  |
| Tartalom: Irányítópultok | A valós idejű csempék nem engedélyezettek (más szóval nem támogatott a PushDataset vagy a pubnub) |
| Lekérdezési paraméterek | Nem támogatott: „Any” típusú paraméterek vagy „Binary” típusú blokkfrissítési művelet az adatkészlethez |
| Egyéni vizualizációk | Csak a nyilvánosan elérhető egyéni vizualizációk támogatottak. A [céges egyéni vizualizációk](power-bi-custom-visuals-organization.md) nem támogatottak |

## <a name="next-steps"></a>Következő lépések

[Mik azok a Power BI-sablonalkalmazások? (előzetes verzió)](service-template-apps-overview.md)
