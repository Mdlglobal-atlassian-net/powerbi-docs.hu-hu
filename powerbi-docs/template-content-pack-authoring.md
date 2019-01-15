---
title: Sablonalapú tartalomcsomagok készítése a Power BI-ban
description: Sablonalapú tartalomcsomagok készítése
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: ab80739b64a3fc72fec0af000b7678bfad585c6c
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285070"
---
# <a name="author-template-content-packs-in-power-bi"></a>Sablonalapú tartalomcsomagok készítése a Power BI-ban
Sablonalapú tartalomcsomagok a Power BI Desktop és a PowerBI.com használatával készíthetők. A tartalomcsomagnak négy összetevője van:

* A lekérdezésekkel [csatlakoztathatja](desktop-connect-to-data.md) és [átalakíthatja](desktop-query-overview.md) az adatokat, valamint [paramétereket](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) határozhat meg  
* Az adatmodellek a [kapcsolatokat](desktop-create-and-manage-relationships.md) és [mértékeket](desktop-measures.md) létrehozását, valamint a Kérdések és válaszok fejlesztését teszik lehetővé  
* A [jelentésoldalak](desktop-report-view.md) vizualizációkat és szűrőket tartalmaznak, amelyek betekintést nyújtanak az adatokba  
* Az [irányítópult](consumer/end-user-dashboards.md) és a [csempék](service-dashboard-create.md) a belefoglalt elemzések áttekintésére adnak lehetőséget  

Az egyes összetevőket meglévő Power BI-funkciókként ismerheti. Tartalomcsomag összeállításakor további szempontokat is figyelembe kell venni az egyes elemek kapcsán. Részleteket az alábbi szakaszokban talál.

<a name="queries"></a>

## <a name="queries"></a>Lekérdezések
A sablonalapú tartalomcsomagok esetében a Power BI Desktopban fejlesztett lekérdezésekkel lehet az adatforráshoz csatlakozni és adatokat importálni. Ezekre a lekérdezésekre szükség van a konzisztens sémák visszaadásához, valamint az ütemezett adatfrissítés esetében is támogatottak (a közvetlen lekérdezés nem támogatott).

A sablonalapú tartalomcsomagok tartalomcsomagonként csak egy adatforrást támogatnak, ezért körültekintően határozza meg a lekérdezéseket. Egyetlen adatforrás van meghatározva az ugyanazon hitelesítést igénylő forrásként. Több API-hívást intézhet a különböző lekérdezésekben, ha minden hívás ugyanarra az API-végpontra irányul és ugyanazt a hitelesítést használja. A Power BI-tartalomcsomagok nem támogatják a különböző hitelesítéseket igénylő többszörös forrásokat.

### <a name="connect-to-your-api"></a>Csatlakozás az API-hoz
Első lépésként csatlakoznia kell az API-hoz a Power BI Desktopból, hogy megkezdhesse a lekérdezések felépítését.

A Power BI Desktopban részét képező azonnal használható Adatösszekötőkkel csatlakozhat az API-hoz. A webes adatösszekötővel (Adatok lekérése -> Web) csatlakozhat a Rest API-hoz, az OData összekötővel (Adatok lekérése -> OData-csatorna) pedig az OData-csatornához. Vegye figyelembe, hogy ezek az összekötők csak akkor állnak használatra készen, ha az API támogatja az Egyszerű hitelesítést.

> [!NOTE]
> Ha az API más hitelesítéstípusokat használ, például az OAuth 2.0-t vagy webes API-kulcsot, akkor saját adatösszekötőt kell fejlesztenie, hogy a Power BI Desktop sikeresen csatlakozhasson az API-hoz és hitelesítse azt. A tartalomcsomaghoz való saját adatösszekötő fejlesztésével kapcsolatos részleteket az Adatösszekötők [innen](https://aka.ms/DataConnectors) elérhető dokumentációjában találja. 
>
>

### <a name="consider-the-source"></a>Tartsa szem előtt a forrást
A lekérdezések határozzák meg az adatmodellben szereplő adatokat. A rendszer méretétől függően ezeknek a lekérdezéseknek szűrőket is tartalmazniuk kell, hogy az ügyfelek kezelhető mérettel legyen dolguk a vállalati forgatókönyvnek megfelelően.

A Power BI–tartalomcsomagok egyszerre több lekérdezést tudnak futtatni több felhasználó számára.  Tervezze meg előre a szabályozási és párhuzamossági stratégiáját, majd kérjen tőlünk tanácsot a tartalomcsomag hibatűrővé tételét illetően.

### <a name="schema-enforcement"></a>Séma kényszerítése
Biztosítsa, hogy a lekérdezések ellenálljanak a rendszerben beállt változásoknak. A sémák változásai a frissítéskor tönkretehetik a modellt. Ha a forrás null/hiányzó sémaeredményt adhat vissza néhány lekérdezésben, érdemes lehet üres táblát vagy egy egyéni hibaüzenetet visszaadni, amelyet a felhasználó könnyen megért.

### <a name="parameters"></a>Paraméterek
A Power BI Desktop [paraméterei](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) lehetővé teszik, hogy a felhasználók olyan bemeneti értékeket adjanak meg, amelyek testreszabják a felhasználó által lekért adatokat. Gondoljon előre a paraméterekre, hogy elkerülje a felesleges munkát, miután időt fektetett a részletes lekérdezések vagy jelentések felépítésébe.

> [!NOTE]
> A sablonalapú tartalomcsomagok jelenleg csak szöveges paramétereket támogatnak. A fejlesztés során használhat más paramétertípusokat, de a [tesztelés](template-content-pack-testing.md#templates) alatt a felhasználók által megadott összes értéknek szövegkonstansnak kell lennie.
>
>

### <a name="additional-query-tips"></a>További lekérdezési tippek

* Győződjön meg arról, hogy minden oszlop helyesen van begépelve
* Az oszlopok leíró nevekkel rendelkeznek (lásd: Kérdések és válaszok)  
* Megosztott logika esetében érdemes lehet függvényeket vagy lekérdezéseket használni  
* Az adatvédelmi szintek jelenleg nem támogatottak a szolgáltatásban – ha a rendszer kérdést tesz fel az adatvédelmi szintekkel kapcsolatban, lehet, hogy újra kell írnia a lekérdezést, hogy az relatív útvonalakat használjon  

## <a name="data-model"></a>Adatmodell

A jól meghatározott adatmodellek biztosítják, hogy az ügyfelek könnyedén és intuitív módon kezelhessék a tartalomcsomagot. Hozza létre az adatmodellt a Power BI Desktopban.

> [!NOTE]
> Az alapszintű modellezés nagy részét (a gépelést, az oszlopneveket) a [lekérdezésekben](#queries) kell elvégezni.
>
>

### <a name="qa"></a>Kérdések és válaszok
A modellezés arra is hatással van, hogy a Kérdések és válaszok milyen hatékonyan tud eredményekkel szolgálni az ügyfeleknek. Mindenképpen vegyen fel szinonimákat a gyakran használt oszlopokhoz, valamint ellenőrizze, hogy az oszlopok megfelelően vannak-e elnevezve a [lekérdezésekben](#queries).

### <a name="additional-data-model-tips"></a>Adatmodellekkel kapcsolatos további tippek
* Az összes értékoszlopra formázás van alkalmazva.
    >[!NOTE]
    >A lekérdezésben típusokat kell alkalmazni.  
* Az összes mértékre formázás van alkalmazva.  
* Be van állítva az alapértelmezett összegzés. Különösen a „Nincs összegzés”, amikor alkalmazható (például egyedi értékekhez).  
* Be van állítva az adatkategória, amikor alkalmazható.  
* Be vannak állítva kapcsolatok, ha szükséges.  

## <a name="reports"></a>Jelentések
A jelentésoldalak további betekintést nyújtanak a tartalomcsomagban szereplő adatokba. A jelentések oldalai segítségével megválaszolhatja azokat a fő üzleti kérdéseket, amelyekkel a tartalomcsomag foglalkozik. Hozza létre a jelentést a Power BI Desktoppal.

> [!NOTE]
> Egy tartalomcsomagban csak egy jelentés szerepelhet. Kihasználhatja a különböző oldalakat a forgatókönyv egyes szakaszainak feliratozásához.
>
>

### <a name="additional-report-tips"></a>Jelentésekkel kapcsolatos további tippek
* Oldalanként több vizualizációt használhat a keresztszűréshez.  
* Körültekintően igazítsa a vizualizációkat (ne legyen átfedés).  
* Az elrendezéshez az oldal legyen „4:3” vagy „16:9” módban.  
* Győződjön meg arról, hogy az összes bemutatott összesítés numerikus értékei megfelelőek (átlagok, egyedi értékek).  
* Ellenőrizze, hogy a szeletelés eredményei észszerűek-e.  
* Ellenőrizze, hogy az embléma legalább a legfelső jelentésen szerepeljen.  
* Győződjön meg arról, hogy elemek az ügyfél színsémáját használják a lehetséges mértékig.  

<a name="dashboard"></a>

## <a name="dashboard"></a>Irányítópult
Az irányítópult az ügyfelek számára a tartalomcsomag kezelésének elsődleges helye. Meg kell jelenítenie a tartalom áttekintését, különös tekintettel az üzleti forgatókönyv fontosabb mérőszámaira.

Ha létre szeretne hozni egy irányítópultot a sablonalapú tartalomcsomaghoz, egyszerűen töltse fel a PBIX-fájlt a Lekérdezés > Fájl paranccsal, vagy tegye közzé közvetlenül a Power BI Desktopról.

> [!NOTE]
> A sablonalapú tartalomcsomagokhoz jelenleg tartalomcsomagonként egy jelentés és adatkészlet használható. Ne rögzítsen több jelentésből/adatkészletből származó tartalmakat a tartalomcsomagban használt irányítópultra.
>
>

### <a name="additional-dashboard-tips"></a>Irányítópultokkal kapcsolatos további tippek
* Őrizze meg ugyanazt a témát a rögzítéskor, hogy az irányítópulton lévő csempék konzisztensek legyenek.  
* Rögzítsen egy emblémát a témához, hogy az ügyfelek tudják, honnan származik a csomag.  
* A legtöbb képernyőfelbontással működő, ajánlott elrendezés 5-6 kisméretű csempe szélességű.  
* Az irányítópult összes csempéjének megfelelő címmel/alcímmel kell rendelkeznie.  
* Érdemes megfontolni különböző csoportosítások használatát a különféle forgatókönyvekhez az irányítópulton, függőlegesen vagy vízszintesen.  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>A korlátozások összefoglalása
A fentiekben említettek szerint a sablonalapú tartalomcsomagok jelenleg korlátozásokkal rendelkeznek:  

| Támogatott | *Nem támogatott* |
| --- | --- |
| A PBI Desktop beépített adatkészletei |*Más tartalomcsomagokból vagy bemenetekből, például Excel-fájlokból származó adatkészletek* |
| A felhőbeli ütemezett adatfrissítéshez támogatott adatforrás |*A közvetlen lekérdezés és a helyszíni kapcsolat nem támogatott* |
| Konzisztens sémát vagy hibákat visszaadó lekérdezések, ahol lehetséges |*Dinamikus vagy egyéni sémák* |
| Adatkészletenként egy adatforrás |*Több adatforrás, például adategyesítések vagy URL-címek, amelyek több adatforrásként vannak észlelve* |
| Szöveg típusú paraméterek |*Egyéb paramétertípusok (például dátum) vagy „az engedélyezett értékek listája”* |
| Egy irányítópult, jelentés és adatkészlet |*Több irányítópult, jelentés vagy adatkészlet* |

## <a name="next-step"></a>Következő lépés
[Tartalomcsomag tesztelése és elküldése](template-content-pack-testing.md)