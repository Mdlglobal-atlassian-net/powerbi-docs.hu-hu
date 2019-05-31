---
title: Ismerje meg, és vizualizációkat hozhat létre a Power BI Q & A használatával
description: Hogyan lehet új vizualizációkat létrehozni irányítópultokon és jelentésekben a Power BI Q & A használatával.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c6fd8967a49515af4d0614653b3d7550c335052f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625461"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>A Power BI Q & A segítségével feltárhatja az adatait, és vizualizációkat hozhat létre

Ha válaszokat keres az adatokban, néha az a leggyorsabb megoldás, ha természetes nyelven kérdez. A Power bi-ban a Q & A szolgáltatás lehetővé teszi az adatokat a saját szavaival.  Ez a cikk első részében bemutatja, hogyan használhatja a Q & A az irányítópultok a Power BI szolgáltatásban. A második rész bemutatja, hogy mit tehet a Q & A a Power BI szolgáltatásban vagy a Power BI Desktopban a jelentések létrehozásakor. A további háttér-információkért lásd: a [Q & a fogyasztók](consumer/end-user-q-and-a.md) cikk. 

[Q & A a Power BI-mobilalkalmazásokban](consumer/mobile/mobile-apps-ios-qna.md) és [Q & A használata a Power BI Embedded](developer/qanda.md) külön cikkekben szerepelnek. 

A Q & A használata a interaktív, még szórakoztató is. Gyakran egy kérdésre vezet, mások számára érdekes elérési utak szerezni a újabbakhoz. Figyelje meg, hogyan hoz létre Amanda vizualizációkat a Q&A-val, hogyan tárja fel ezeket a vizualizációkat, és rögzíti őket irányítópultokon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>1. rész: A Q & A használata irányítópulton a Power BI szolgáltatásban

A Power BI szolgáltatásban (app.powerbi.com) egy irányítópult csempéi, egy vagy több adatkészletet, rögzített, így található bármely adatkészlet bármely adatával kapcsolatban feltehető kérdés. Az irányítópult létrehozásához mely jelentéseket és adatkészleteket használták megtekintéséhez válasszon **kapcsolódó megtekintése** a menüsoron.

![Kapcsolódó jelentés és adatkészlet megtekintése](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

A Q & A kérdésmező az irányítópulton, ahová beírhatja a természetes nyelvet használva tehet fel a bal felső sarkában található. A Q & A mezőben nem jelenik meg? Lásd: [megfontolandó szempontok és hibaelhárítás](consumer/end-user-q-and-a.md#considerations-and-troubleshooting) a a **Q & a fogyasztók** cikk.  Q & A felismeri a beírt szavakat, és kitalálja, hogy hol (melyik adatkészletben) található meg a válasz. A Q&A a kérdés megfogalmazásában is segít automatikus kiegészítéssel, átfogalmazással és más szöveges és vizuális támogatással.

![A Q & A kérdésmező](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

A kérdésére adott válasz használható vizualizációként jelenik meg, és a kérdés módosításakor frissül.

1. Nyisson meg egy irányítópultot, és vigye a kurzort a kérdésmező fölé. A jobb felső sarokban válassza **új Q & A élmény**.

    ![A Power BI új Q & A élmény](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Még mielőtt gépelni kezdene, a Q&A egy új képernyőt nyit meg, amelyen javaslatokkal segít a kérdés megfogalmazásában. Mondatok és a kész kérdéseket, amely tartalmazza az alapul szolgáló adatkészlet tábláinak nevei, és előfordulhat, hogy látni, ha az adatkészlet tulajdonosa létrehozott kész kérdéseket [kiemelt kérdéseket](service-q-and-a-create-featured-questions.md),

   ![Q & A javasolt kérdések](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Válasszon egyet az alábbi kérdésekre kiindulási pontként, és továbbra is egy adott válasz keresése a kérdést. Vagy használhat egy Táblanév egy másik kérdést is megfogalmazhat.

2. Válassza ki a listából azon kérdése van, vagy kezdje begépelni saját kérdését, és válassza ki a legördülő javaslatokból.

   ![Válasszon ki egy kérdést a listából](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. Kérdés beírása közben a Q & A kiválasztja a legjobb vizualizációt a válasz megjelenítéséhez.

   ![A Q & A hány tárolja a state szerint](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. A Vizualizáció dinamikusan változik, a kérdés módosítása.

   ![A Q & A hány tárolja a sávdiagramot oszlopdiagramra cseréli, state szerint](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. A kérdés begépelésekor a Power BI minden olyan adatkészletben keresi a választ, amelyhez csempe tartozik az irányítópulton.  Ha az összes csempe forrása az *A adatkészlet*, akkor a válaszok az *A adatkészletből* származnak.  Ha nincsenek származó csempék *adatkészletből* és *adatkészletből*, majd a Q & A megkeresi a legjobb választ az adatkészletekből 2.

   > [!TIP]
   > Ügyeljen rá, hogy ha az *A adatkészletnek* csak egy csempéje van, és eltávolítja azt az irányítópultról, akkor a Q&A többé nem fog hozzáférni az *A adatkészlethez*.
   >

5. Ha elégedett az eredménnyel, a PIN-kód ikon kiválasztásával a jobb felső sarokban az irányítópulthoz a Vizualizáció rögzítése. Ha az irányítópultot más osztotta meg Önnel, vagy egy alkalmazás része, akkor a rögzítésre nincs lehetősége.

   ![A Q & A a vizualizációt rögzíti.](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>2. rész: A Q&A használata jelentésben a Power BI szolgáltatásban és a Power BI Desktopban

A Q&A használatával megismerheti az adatkészletet, és vizualizációkat adhat hozzá jelentésekhez és irányítópultokhoz. Egy jelentés egyetlen adatkészletet használ, és lehet teljesen üres is, vagy tartalmazhat számos vizualizációval rendelkező oldalakat is. Ha azonban üres egy jelentés, az még nem jelenti azt, hogy nincsenek rendelkezésre álló és feltárható adatok benne: az adatkészlet csatolva van a jelentéshez, és az adatai vizualizációk létrehozásával fel is tárhatóak.  Ha meg szeretné nézni, hogy a jelentés mely adatkészlet használatával készült, nyissa meg a jelentést a Power BI szolgáltatásban Olvasó nézetben, és válassza a **Kapcsolódó megtekintése** lehetőséget.

![Kapcsolódó adatkészlet megtekintése](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

A Q & a használata a jelentésekben, szerkesztési engedéllyel a jelentés és az alapjául szolgáló adatkészlethez kell rendelkeznie. Az a [Q & a fogyasztók](consumer/end-user-q-and-a.md) ezt nevezzük a cikkben egy *létrehozó* forgatókönyv. Ha ehelyett Ön *felhasználása* a jelentést megosztották Önnel, a Q & A nem érhető el.

1. Nyisson meg egy jelentést szerkesztési nézetben (Power BI szolgáltatás) vagy a jelentés nézetben (Power BI Desktop), és válassza ki **kérdés feltevése** a menüsoron.

    **A Power BI Desktopban**    
    ![Kattintson a kérdés feltevése a Power BI Desktopban](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Service**    
    ![Válassza ki a kérdés feltevése a Power BI szolgáltatásban](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. A jelentésvásznon megjelenik a Q&A kérdésmező. Az alábbi példában a kérdésmező egy másik vizualizáció fölött jelenik meg. Ez nem okoz problémát, de tanácsosabb új üres oldalt hozzáadni a jelentéshez a kérdés feltevése előtt.

    ![A Q & A kérdésmező](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Vigye a kurzort a kérdésmező fölé. A kérdés begépelése közben a Q&A javaslatokat jelenít meg a kérdés megfogalmazásához.

   ![Írja be a Q & A kérdésmező](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. A kérdés beírása közben a Q&A kiválasztja a legjobb [vizualizációt](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) a válasz megjelenítéséhez; a kérdés módosítása közben a vizualizáció dinamikusan változik.

   ![A Q & A létrehoz egy vizualizációt](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Ha megjelent a kívánt vizualizáció, nyomja meg az ENTER billentyűt. Ha a vizualizációt menteni szeretné a jelentéssel, válassza a **Fájl > Mentés** lehetőséget.

6. Az új vizualizációt használatba is veheti. Függetlenül attól, hogy a vizualizációt hogyan hozta létre, elérhetőek lesznek ugyanazok a lehetőségek az interakcióra, a formázásra és egyéb funkciókra.

   ![A vizualizációt](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Ha a vizualizációt a Power BI szolgáltatás használatával hozta létre, akkor [rögzítheti is azt egy irányítópulton](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>A Q&A által használt vizualizáció megadása
A Q&A-tól nem csak annyit kérhet, hogy az adatok beszéljenek magukért, azt is megadhatja, hogy a Power BI hogyan jelenítse meg a válaszokat. Elég a kérdés végét a "as a <visualization type>" ("mint ...") szöveggel kiegészíteni.  Erre példa a "show inventory volume by plant as a map" ("mutasd a raktárkészletet üzemenként mint térkép") és a "show total inventory as a card" ("mutasd a teljes leltárt mint kártya").  Próbálja ki.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
- Ha az adatkészlethez élő kapcsolattal vagy átjáró használatával csatlakozott, a Q&A-t [engedélyezni kell az adott adatkészlethez](service-q-and-a-direct-query.md).

- Megnyitott egy jelentést, de nem jelenik meg a Q&A lehetőség. Ha a Power BI szolgáltatást használja, mindenképpen a Szerkesztési nézetében nyissa meg a jelentést. Ha azt jelenti, hogy nincs meg a jelentést szerkesztési engedélyekkel, és használható a Q & A az adott jelentés szerkesztési nézetében nem nyitható meg.

## <a name="next-steps"></a>Következő lépések

- [A Q & A a fogyasztók számára](consumer/end-user-q-and-a.md)   
- [Tippek kérdések feltevéséhez a Q&A-ben](consumer/end-user-q-and-a-tips.md)   
- [Munkafüzet előkészítése a Q&A használatához](service-prepare-data-for-q-and-a.md)  
- [Helyszíni adatkészlet előkészítése Q & a](service-q-and-a-direct-query.md)   
- [Csempe rögzítése az irányítópulton a Q&A-ból](service-dashboard-pin-tile-from-q-and-a.md)
