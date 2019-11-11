---
title: Q&A a Power BI-ügyfelek számára
description: 'Q&A szolgáltatás: Természetes nyelvi kérdések a Power BI-ban – Dokumentáció'
author: mihart
manager: kvivek
ms.reviewer: mohammad ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/22/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 8c39d64619018d01c436ddb1478881f15480bab6
ms.sourcegitcommit: 8e28280d9d4d6034d28e2f635af2b765edc282ba
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72793969"
---
# <a name="qa-for-power-bi-consumers"></a>Q&A a Power BI-**ügyfelek** számára

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-qa"></a>Mi a Q&A?
Ha válaszokat keres az adatokban, néha az a leggyorsabb megoldás, ha természetes nyelven kérdez. Például: „what were total sales last year (mennyi volt az összes értékesítés tavaly).”

A Q&A szolgáltatás könnyen használható, természetes nyelvi funkciókat kínál az adatok elemzéséhez, és kérdéseire grafikonok vagy diagramok formájában ad választ. A Q&A nem keresőmotor – csak a Power BI-ban lévő adatokról szolgáltat eredményeket.

## <a name="which-visualization-does-qa-use"></a>Mely vizualizációkat használja a Q&A?
A Q&A az éppen megjelenített adatok alapján választja ki a legalkalmasabb vizualizációt. Az alapul szolgáló adathalmaz adatai egy bizonyos típusba vagy kategóriába vannak besorolva, ami segít a Q&A-nak eldönteni, hogy hogyan jelenítse meg azokat. Ha az adat például dátum típusúként van megadva, akkor nagyobb valószínűséggel jelenik meg vonaldiagramként. Városként kategorizált adatok nagyobb valószínűséggel lesznek térképen megjelenítve.

Utasíthatja is a Q&A-t, hogy melyik vizualizációt használja, ha hozzáfűzi azt a kérdéséhez. Azt azonban mindig vegye figyelembe, hogy a Q&A nem mindig tudja a kért vizualizációtípusban megjeleníteni az adatokat. A Q&A felajánlja a használható vizualizációtípusok listáját.

## <a name="where-can-i-use-qa"></a>Hol találom a Q&A-t?
A Q&A a Power BI szolgáltatás irányítópultjain és a Power BI mobilalkalmazás irányítópultjának alján érhető el. Ha a tervező nem adott Önnek szerkesztési jogosultságot, a Q&A-vel feltárhatja az adatokat, azonban nem mentheti a Q&A használatával létrehozott vizualizációkat.

![kérdésmező](media/end-user-q-and-a/powerbi-qna.png)

A Q&A-t jelentésekben is megtalálhatja, ha a jelentés *készítője* felvett abba egy [Q&A vizualizációt](../visuals/power-bi-visualization-q-and-a.md).   

![Q&A – vizualizáció](media/end-user-q-and-a/power-bi-q-and-a-default.png)

## <a name="qa-on-dashboards"></a>Q&A az irányítópultokon

A **Power BI Q&A** Pro- vagy Premium-licenccel érhető el.  A [Q&A a Power BI-mobilalkalmazásokban](mobile/mobile-apps-ios-qna.md) és a [Q&A a Power BI Embedded használatával](../developer/qanda.md) külön cikkekben szerepelnek. A **Power BI Q&A** jelenleg csak angol nyelven feltett természetes nyelvű kérdéseket támogat, de előzetes verzióban elérhető a spanyol is, amelyet a Power BI-rendszergazda engedélyezhet.


![q&a által létrehozott fatérkép](media/end-user-q-and-a/power-bi-treemap.png)

A kérdés megfogalmazása csak az első lépés.  Pontosíthatja vagy kibővítheti a kérdést, megbízható új információkat fedezhet fel, összpontosíthat a részletekre, vagy feltárhatja a szélesebb összefüggéseket, így az adatok feltérképezése valódi élménnyé válik. Örömét lelheti az új eredményekben és felfedezésekben.

Valóban interaktív élmény... és gyors! A memóriabeli tárolás segítségével szinte egy pillanat alatt megkapja a választ.


## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>A Q&A használata irányítópulton a Power BI szolgáltatásban
A Power BI szolgáltatásban (app.powerbi.com) az irányítópultokon egy vagy több adatkészletből származó csempék vannak rögzítve, így bármely adatkészlet bármely adatával kapcsolatban feltehető kérdés. Ha meg szeretné nézni, hogy mely jelentéseket és adathalmazokat használták fel az irányítópult létrehozásához, válassza a **További műveletek** legördülő menü **Kapcsolódó megtekintése** elemét.

![kapcsolódó megtekintése a menüsávról](media/end-user-q-and-a/power-bi-q-and-a-view-related.png)

## <a name="how-do-i-start"></a>Hogyan kezdjem meg a használatát?
Először ismerkedjen meg a tartalommal. Tekintse meg az irányítópulton és a jelentésben található vizualizációkat. Mérje fel az elérhető adatok típusát és terjedelmét. 

Például:

* Ha a vizualizáció tengelyfeliratai és értékei között szerepelnek a „sales”, „account”, „month” és „opportunity” szavak, akkor feltehet olyan angol nyelvű kérdéseket, mint: "Which *account* has the highest *opportunity*", vagy "show *sales* by month as a bar chart".

* Ha rendelkezik egy webhely Google Analytics-beli teljesítményadataival, akkor kérdezheti a Q&A-t a weboldalakon töltött időről, az egyedi oldallátogatások számáról és a felhasználói érdeklődés mérőszámairól. Demográfiai adatok lekérdezésekor például az életkor és a háztartások bevétele földrajzi hely szerinti eloszlásáról tehet fel kérdéseket.

Ha már megismerte az adatokat, lépjen vissza az irányítópultra, és helyezze a kurzort a kérdésmezőbe. Ekkor megnyílik a Q&A képernyő.

![Q&A képernyő](media/end-user-q-and-a/power-bi-screen.png) 

Még mielőtt gépelni kezdene, a Q&A egy új képernyőt nyit meg, amelyen javaslatokkal segít a kérdés megfogalmazásában. Olyan kifejezéseket és kérdéseket fog látni, amelyekben szerepelnek a mögöttes adathalmazok tábláinak nevei, sőt *kiemelt* kérdések is megjelenhetnek, amelyeket az adathalmaz tulajdonosa hozott létre.

Ezek bármelyikét kiválaszthatja és hozzáadhatja a kérdés mezőhöz, és módosíthatja őket meghatározott kérdésekhez. 

A Q&A emellett kérdésekkel, automatikus kiegészítéssel és vizuális jelekkel is segíti a kérdések feltételét. 

<!-- ![video](../visuals/media/end-user-q-and-a/qna4.gif) -->


## <a name="the-qa-visual"></a>A Q&A-vizualizáció

A Q&A-vizualizáció lehetővé teszi, hogy természetes nyelven feltett kérdéseire vizualizáció formájában kapja meg a választ. A Q&A-vizualizáció a többi vizualizációhoz hasonlóan viselkedik, biztosítja a keresztszűrés és a keresztkijelölés lehetőségét, és a könyvjelzőket és megjegyzéseket is támogatja. 

A Q&A-vizualizációk a felső kérdésmezőről ismerhetők fel. Ide írhatja be a természetes nyelven megfogalmazott kérdéseket. A Q&A-vizualizációt többször is felhasználhatja arra, hogy az adatokkal kapcsolatos kérdéseket tegyen fel. A jelentés elhagyásakor a Q&A-vizualizáció visszaállítja az alapértelmezéseit. 

![Alapértelmezett Q&A-vizualizáció képernyőképe](media/end-user-q-and-a/power-bi-q-and-a-default.png)


## <a name="use-the-qa-visual"></a>A Q&A-vizualizáció használata
A Q&A-vizualizáció használatához választhat a javasolt kérdések közül, vagy begépelheti saját természetes nyelvű kérdését. 

### <a name="create-a-qa-visual-by-using-a-suggested-question"></a>Q&A-vizualizáció létrehozása javasolt kérdés használatával

Ebben a példában a **top geo states by total units** lehetőséget választottuk. A Power BI megkísérli a lehető legjobb vizualizációtípus kiválasztani. Ebben az esetben ez egy térkép.

![Q&A-vizualizáció térkép](media/end-user-q-and-a/power-bi-q-and-a-suggested.png)

De a természetes nyelven megadott lekérdezésekhez hozzáadhatja annak meghatározását is, hogy a Power BI milyen típusú vizualizációt használjon. Vegye figyelembe, hogy nem minden vizualizációtípus fog működni vagy értelmezhető eredményt mutatni az adatokkal. Ezek az adatok például nem ábrázolhatók értelmezhetően egy pontdiagramon. A kartogram azonban jól használható.

![Q&A-vizualizáció, mint kartogram](media/end-user-q-and-a/power-bi-filled-map.png)

### <a name="create-a-qa-visual-by-typing-a-natural-language-query"></a>Q&A-vizualizáció létrehozása természetes nyelvi lekérdezés begépelésével


Ha nem biztos a kérdéstípusban vagy a szóhasználatban, bontsa ki az **Összes javaslat megjelenítése** elemet, vagy tekintse át a jelentésben lévő többi vizualizációt. Így megismerheti az adathalmaz szóhasználatát és tartalmát.

1. Gépelje be természetes nyelven megfogalmazott kérdését a Q&A mezőbe. A kérdés beírását a Power BI automatikus kiegészítéssel, javaslatokkal és visszajelzéssel segíti.

    - Piros aláhúzás jelöli a Power BI által nem felismert szavakat. A Power BI lehetőség szerint segítséget nyújt az ilyen szavak körülírásához. Ha meglátja a helyes definíciót, válassza ki azt a legördülő listából.  

        ![Pirossal aláhúzott kifejezés a Q&A kérdésmezőben](media/end-user-q-and-a/power-bi-q-and-a-red.png)

    - Ha a definíciók egyike sem helyes, próbálkozzon más kifejezéssel, vagy jelölje ki az aláhúzott szót, és kérje meg a jelentés készítőjét, hogy ezt a szót is vegye fel.

        ![Kérdés beírása a Q&A kérdésmezőbe](media/end-user-q-and-a/power-bi-q-and-a-owner.png)

    - Ahogy előrehalad a kérdés beírásával, a Power BI értesíti, ha nem érti a kérdést, és megpróbál segíteni. Az alábbi példában a Power BI felteszi a „Did you mean...” (Arra gondolt hogy...) kérdést, és javaslatot tesz egy másik szó használatára az adathalmazból. 

        ![Módosítási javaslatokat felkínáló Q&A-vizualizáció](media/end-user-q-and-a/power-bi-q-and-a-did-you-mean.png)

2. A Power BI által javasolt módosítás kiválasztása után az eredmények vonaldiagramon jelennek meg. 

    ![Q&A-vizualizáció eredményei vonaldiagramként](media/end-user-q-and-a/power-bi-q-and-a-line.png)


3. A vonaldiagramot azonban más típusú vizualizációvá is alakíthatja.  

    ![Q&A-vizualizáció a kérdéshez hozzátett „as a column chart” (oszlopdiagramként) kifejezéssel](media/end-user-q-and-a/power-bi-q-and-a-specify-type.png)



## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

**Kérdés**: Nem látom a Q&A-t ezen az irányítópulton.    
**1. válasz**: Ha nem látja a kérdésmezőt, először ellenőrizze a beállításokat. Ehhez kattintson a Power BI-eszköztár jobb felső sarkában lévő fogaskerék ikonra.   
![fogaskerék ikon](media/end-user-q-and-a/power-bi-settings.png)

Ezután válassza a **Beállítások** > **Irányítópultok** elemet. Ellenőrizze, hogy látható-e pipa a **Q&A-keresőmező megjelenítése ezen az irányítópulton** beállítás mellett.    
![Irányítópult Q&A-beállításai](media/end-user-q-and-a/power-bi-turn-on.png)  


**2. válasz**: Bizonyos helyzetekben nem fog hozzáférni a beállításokhoz. Ha az irányítópult *készítője* vagy a rendszergazda kikapcsolta a Q&A-t, akkor tőlük kell megkérdeznie, hogy visszakapcsolhatja-e.   

**Kérdés**: Nem a várt eredményeket látom, amikor beírok egy kérdést.    
**Válasz**: Válassza ki a jelentés vagy irányítópult tulajdonosával való kapcsolatfelvétel lehetőségét. Ezt megteheti közvetlenül a Q&A irányítópult oldaláról vagy a Q&A-vizualizációból. A tulajdonos kilétét a Power BI fejlécéből is kiolvashatja.  A tervező sok mindent tehet a Q&A-eredmények javítása érdekében. A tervező például átnevezheti az adatkészlet oszlopait, hogy azok könnyebben érhető kifejezéseket használjanak (`CustomerFirstName` `CustFN` helyett). Mivel a tervező ismeri igazán jól az adathalmazt, hasznos kérdéseket is megfogalmazhat, és felveheti azokat a Q&A által javasolt kérdések közé.

![Kapcsolattartási adatok megjelenítése](media/end-user-q-and-a/power-bi-q-and-a-contact.png)

## <a name="next-steps"></a>Következő lépések
Azt, hogy a *készítőik* hogyan hozzák létre és kezelik a Q&A-vizualizációkat, a [Q&A-vizualizációtípus](../visuals/power-bi-visualization-q-and-a.md) című cikkből tudhatja meg.
