---
title: Bevezetés a Q&A-eszközök használatába a Power BI Q&A tanításához (előzetes verzió)
description: Bevezetés a Power BI Q&A-eszközök használatába
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
ms.openlocfilehash: 6178c9f157578110a09abf3fcbebccba54339f13
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866069"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Bevezetés a Q&A-eszközök használatába a Power BI Q&A tanításához (előzetes verzió)

A Power BI Q&A-*eszközökkel* javíthatja a felhasználók természetes nyelvi élményét. Tervezőként vagy rendszergazdaként három területen találkozhat a természetes nyelvi motorral, és fejlesztheti azt tovább: 

- A felhasználók által feltett kérdések áttekintése.
- A Q&A tanítása a kérdések megértése érdekében.
- A Q&A-nek megtanított kifejezések kezelése.

A dedikált eszközök ezen képességei mellett a Power BI Desktop **Modellezés** lapján további lehetőségek érhetők el:  

- Szinonimák
- Sorfeliratok
- Elrejtés a Q&A-ben
- Nyelvi séma konfigurálása (speciális)

## <a name="get-started-with-qa-tooling"></a>A Q&A-eszközök használatának első lépései

A Q&A-eszközök csak a Power BI Desktopban érhetők el, és jelenleg csak az importálási módot támogatják.

1. Nyissa meg Power BI Desktopot, és hozzon létre egy vizualizációt a Q&A-vel. 
2. Válassza a fogaskerék ikont a vizualizáció sarkában. 

    ![Q&A-vizualizáció fogaskerék ikonja](media/q-and-a-tooling-intro/qna-visual-gear.png)

    Ekkor megnyílik az Első lépések lap.  

    ![A Q&A használatának első lépései](media/q-and-a-tooling-intro/qna-tooling-dialog.png)

### <a name="review-questions"></a>Kérdések áttekintése

Válassza a **Kérdések áttekintése** lehetőséget a bérlő a Power BI szolgáltatásban használt adathalmazai listájának megtekintéséhez. A **Kérdések áttekintése** lapon az adathalmaz tulajdonosa, a munkaterület és a legutóbbi frissítés dátuma is megjelenik. Itt kiválaszthat egy adathalmazt, és megtekintheti, hogy a felhasználók milyen kérdéseket tettek fel. Az adatok között azok a szavak is megjelennek, amelyeket nem ismert fel a rendszer. Az összes itt megjelenő adat az elmúlt 28 napra vonatkozik.

![Kérdések áttekintése a Q&A-ben](media/q-and-a-tooling-intro/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>A Q&A tanítása

**A Q&A tanítása** szakaszban betaníthatja a Q&A-t szavak felismerésére. A kezdéshez adjon meg egy olyan szót vagy szavakat tartalmazó kérdést, amelyet vagy amelyeket a Q&A nem ismer fel. A Q&A bekéri a kifejezés definícióját. Adjon meg egy olyan szűrőt vagy mezőnevet, amely megfelel annak, amit az adott szó jelöl. A Q&A ezután újból értelmezi az eredeti kérdést. Ha elégedett az eredménnyel, mentheti a bemenetet. További információért lásd: [A Q&A tanítása](q-and-a-tooling-teach-q-and-a.md)

![Szinonima tanításának előnézete a Q&A-ben](media/q-and-a-tooling-intro/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Kifejezések kezelése

Itt minden megjelenik, amit A Q&A tanítása szakaszból mentett, így áttekintheti vagy törölheti a definiált kifejezéseket. A meglévő definíciókat jelenleg nem lehet szerkeszteni, ezért a kifejezés újbóli definiálásához törölnie kell az adott kifejezést, majd újból létre kell hoznia azt.

![Kifejezések kezelése a Q&A-ben](media/q-and-a-tooling-intro/qna-manage-terms.png)

### <a name="suggest-questions"></a>Javasolt kérdések

Beállítás nélkül a Q&A vizualizáció több kezdő kérdést is javasol. Ezek automatikusan jönnek létre az adatmodell alapján. A **Javasolt kérdések** területen felülírhatja saját kérdésekkel az automatikusan létrehozott kérdéseket. 

A kezdéshez írja be a hozzáadni kívánt kérdést a szövegmezőbe. Az előnézet szakaszban láthatja, hogy az eredmény hogyan fog kinézni a Q&A vizualizációban. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-suggest-questions.png" alt-text="Q&A-kérdésjavaslatok":::
 
A **Hozzáadás** gombbal adhatja hozzá a kérdést a **Saját javasolt kérdésekhez**. Minden további kérdés a lista végére kerül. A kérdések a Q&A vizualizációban ugyanabban a sorrendben jelennek meg, mint ezen a listán. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-save-suggest-questions.png" alt-text="Javasolt kérdések mentése":::
 
A **Mentés** lehetőséggel jelenítse meg a javasolt kérdéseket a Q&A vizualizációban. 


## <a name="other-qa-settings"></a>A Q&A egyéb beállításai

### <a name="bulk-synonyms"></a>Tömeges szinonimák

A Power BI Desktop **Modellezés** lapján további lehetőségek érhetők el a Q&A felhasználói élményének javítására. 

1. Válassza a Modellező nézetet a Power BI Desktopban.

2. Ha kiválaszt egy mezőt vagy egy táblát, megjelenik a **Tulajdonságok** panel.  Ez a panel a vászon jobb oldalán jelenik meg, és számos Q&A-művelet van felsorolva benne. Az egyik lehetőség a **Szinonimák**. A **Szinonimák** mezőben gyorsan definiálhat alternatívákat a kiválasztott táblához vagy mezőhöz. Emellett az Eszközök párbeszédpanel **A Q&A tanítása** szakaszában is definiálhat szinonimákat, de gyakran gyorsabb, ha egy tábla számos mezőjéhez definiál szinonimákat itt.

    ![Szinonimák a Q&A Modellezés paneljén](media/q-and-a-tooling-intro/qna-modelling-pane-synonyms.png)

3. Ha több szinonimát szeretne definiálni egyetlen mezőhöz, a következő szinonimát vesszőkkel jelölje.

### <a name="hide-from-qa"></a>Elrejtés a Q&A-ben

A mezőket és a táblákat el is rejtheti, hogy azok ne jelenjenek meg a Q&A eredményei között. 

1. Válassza a Modellező nézetet a Power BI Desktopban.

2. Válasszon ki egy mezőt vagy egy táblát, hogy megjelenjen a **Tulajdonságok** panel, majd a **Rejtett** beállítást kapcsolja **Be**.

    A Q&A figyelembe veszi ezt a beállítást, és biztosítja, hogy a Q&A ne ismerje fel ezt a mezőt. Előfordulhat például, hogy el szeretné rejteni az azonosítómezőket és a külső kulcsokat, hogy elkerülje a felesleges, azonos nevű ismétlődő mezők használatát. Még ha el is rejti a mezőt, a Power BI Desktopban, a Q&A-n kívüli vizualizációkban továbbra is használhatja azt.

### <a name="set-a-row-label"></a>Sorfelirat beállítása

A sorfeliratokkal meghatározhatja, hogy melyik oszlop (vagy *mező*) azonosítja a legjobban egy tábla adott sorát. Egy Customer (Ügyfél) nevű tábla esetében például a sorfelirat általában a Display Name (Megjelenített név). Ha kiegészítő metaadatokat ad meg, a Q&A hasznosabb vizualizációt tud megjeleníteni, amikor a felhasználók a Show me sales by customer (Értékesítések megjelenítése ügyfél szerint) kifejezést írják be. Ahelyett, hogy a customer (ügyfél) kifejezést táblaként kezelné, használhatja a Display Name (Megjelenített név) mezőt, és az egyes ügyfelek értékesítéseit ábrázoló sávdiagramot jeleníthet meg. A sorfeliratot csak a Modellezés nézetben lehet beállítani. 

1. Válassza a Modellező nézetet a Power BI Desktopban.

2. Ha kiválaszt egy táblát, megjelenik a **Tulajdonságok** panel.

3. A **Sorfelirat** mezőben adjon meg egy mezőt.

## <a name="configure-the-linguistic-schema-advanced"></a>A nyelvi séma konfigurálása (speciális)

A Power BI-ban teljes egészében betaníthatja és javíthatja a Q&A-beli természetes nyelvi motort, beleértve a mögöttes természetes nyelvi eredmények pontozásának és súlyozásának módosítását is. További információért lásd: [A Q&A nyelvi sémájának szerkesztése, és kifejezések hozzáadása](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Következő lépések

A természetes nyelvi motor fejlesztéséhez számos ajánlott eljárás áll rendelkezésre. További információ: [Q&A – Ajánlott eljárások](q-and-a-best-practices.md).
