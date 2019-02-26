---
title: A Q&A használata a Power BI szolgáltatásban – áttekintés
description: 'Q&A szolgáltatás: Természetes nyelvi kérdések a Power BI-ban – Dokumentáció'
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: e6f95eedbd84ad5f512bbc1a1255cee7130a60d7
ms.sourcegitcommit: a054782370dec56d49bb205ee10b7e2018f22693
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56661975"
---
# <a name="qa-for-power-bi-consumers"></a>Q&A a Power BI-**ügyfelek** számára
## <a name="what-is-qa"></a>Mi a Q&A?
Ha válaszokat keres az adatokban, néha az a leggyorsabb megoldás, ha természetes nyelven kérdez. Például: „what were total sales last year (mennyi volt az összes értékesítés tavaly).”  
A Q&A szolgáltatás könnyen használható, természetes nyelvi funkciókat kínál az adatok elemzéséhez, és kérdéseire grafikonok vagy diagramok formájában ad választ. A Q&A nem keresőmotor – csak a Power BI-ban lévő adatokról szolgáltat eredményeket.

A **Power BI Q&A** csak angol nyelven támogatja a természetes nyelven írt lekérdezések megválaszolását. Elérhető egy előzetes verzió spanyol nyelven, amelyet a Power BI-rendszergazda engedélyezhet.

A **Power BI Q&A** Pro- vagy Premium-licenccel érhető el. 
>

![q&a által létrehozott fatérkép](media/end-user-q-and-a/power-bi-qna.png)

A kérdés megfogalmazása csak az első lépés.  Pontosíthatja vagy kibővítheti a kérdést, megbízható új információkat fedezhet fel, összpontosíthat a részletekre, vagy feltárhatja a szélesebb összefüggéseket, így az adatok feltérképezése valódi élménnyé válik. Örömét lelheti az új eredményekben és felfedezésekben.

Valóban interaktív élmény... és gyors! A memóriabeli tárolás segítségével szinte egy pillanat alatt megkapja a választ.

## <a name="where-can-i-use-qa"></a>Hol találom a Q&A-t?
A Q&A a Power BI szolgáltatás irányítópultjain, a Power BI mobilalkalmazás irányítópultjának alján és a Power BI Embeddedben látható vizualizáció felett érhető el. Ha a tervező nem adott Önnek szerkesztési jogosultságot, a Q&A-vel feltárhatja az adatokat, azonban nem mentheti a Q&A használatával létrehozott vizualizációkat.

![kérdésmező](media/end-user-q-and-a/powerbi-qna.png)

## <a name="how-does-qa-know-how-to-answer-questions"></a>Honnan tudja a Q&A, hogy hogyan válaszoljon meg egy kérdést?
A Q&A az irányítópulthoz társított adatkészletek mindegyikében keresi a válaszokat. Ha egy adatkészlet rendelkezik csempével az irányítópulton, a Q&A abban az adatkészletben fogja keresni a válaszokat. 

## <a name="how-do-i-start"></a>Hogyan kezdjem meg a használatát?
Először ismerkedjen meg a tartalommal. Tekintse meg az irányítópulton és a jelentésben található vizualizációkat. Mérje fel az elérhető adatok típusát és terjedelmét. Ezután lépje vissza az irányítópultra, és helyezze a kurzort a kérdésmezőbe. Ekkor megnyílik a Q&A képernyő.

![Q&A képernyő](media/end-user-q-and-a/power-bi-qna-screen.png) 

* Ha a vizualizáció tengelyfeliratai és értékei között szerepelnek a "sales", "account", "month" és "opportunity" szavak, akkor feltehet olyan angol nyelvű kérdéseket, mint "Which *account* has the highest *opportunity*", vagy "show *sales* by month as a bar chart".

* Ha rendelkezik egy webhely Google Analytics-beli teljesítményadataival, akkor kérdezheti a Q&A-t a weboldalakon töltött időről, az egyedi oldallátogatások számáról és a felhasználói érdeklődés mérőszámairól. Demográfiai adatok lekérdezésekor például az életkor és a háztartások bevétele földrajzi hely szerinti eloszlásáról tehet fel kérdéseket.

A képernyő alján egyéb hasznos dolgokat láthat. A Q&A minden adatkészlethez kapcsolódóan megjelenít kulcsszavakat, néha pedig még minta- vagy javasolt kérdéseket is. Ezek bármelyikét kijelölheti, és hozzáadhatja a kérdésmezőhöz. 

A Q&A emellett kérdésekkel, automatikus kiegészítéssel és vizuális jelekkel is segíti a kérdések feltételét. 

![videó](media/end-user-q-and-a/qa.gif) 


### <a name="which-visualization-does-qa-use"></a>Mely vizualizációkat használja a Q&A?
A Q&A az éppen megjelenített adatok alapján választja ki a legalkalmasabb vizualizációt. Az alapul szolgáló adatkészlet(ek) adatai egy bizonyos típusba vagy kategóriába vannak besorolva, ami segít a Q&A-nak eldönteni, hogy hogyan jelenítse meg. Ha az adat például dátum típusúként van megadva, akkor nagyobb valószínűséggel jelenik meg vonaldiagramként. Városként kategorizált adatok nagyobb valószínűséggel lesznek térképen megjelenítve.

Utasíthatja is a Q&A-t, hogy melyik vizualizációt használja, ha hozzáfűzi azt a kérdéséhez. Azt azonban mindig vegye figyelembe, hogy a Q&A nem mindig tudja a kért vizualizációtípusban megjeleníteni az adatokat. A Q&A felajánlja a használható vizualizációtípusok listáját.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
**Kérdés**: Nem látom a Q&A-t ezen az irányítópulton.    
**1. válasz**: Ha nem látja a kérdésmezőt, először ellenőrizze a beállításokat. Ehhez kattintson a Power BI-eszköztár jobb felső sarkában lévő fogaskerék ikonra.   
![fogaskerék ikon](media/end-user-q-and-a/power-bi-settings.png)

Ezután válassza a **Beállítások** > **Irányítópultok** elemet. Ellenőrizze, hogy látható-e pipa a **Q&A-keresőmező megjelenítése ezen az irányítópulton** beállítás mellett.
![Irányítópult Q&A-beállításai](media/end-user-q-and-a/power-bi-turn-on.png)  


**2. válasz**: Néha az irányítópult *tervezője* vagy a rendszergazda kikapcsolja a Q&A-t. Kérdezze meg őket, hogy engedélyezni lehetne-e a használatát.   

**Kérdés**: Nem a várt eredményeket látom, amikor beírok egy kérdést.    
**Válasz**: Beszéljen az irányítópult *tervezőjével*. A tervező sok mindent tehet a Q&A-eredmények javítása érdekében. A tervező például átnevezheti az adatkészlet oszlopait, hogy azok könnyebben érhető kifejezéseket használjanak (`CustomerFirstName` `CustFN` helyett). Mivel a tervező ismeri igazán jól az adatkészletet, hasznos kérdéseket is javasolhat, és hozzáadhatja azokat a Q&A-vászonhoz.

![kiemelt kérdés bekeretezve](media/end-user-q-and-a/power-bi-featured-q.png)

## <a name="next-steps"></a>Következő lépések

