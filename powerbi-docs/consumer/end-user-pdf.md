---
title: Jelentések exportálása PDF-fájlba
description: Megtudhatja, hogyan exportálhat jelentést a Power BI-ból egy PDF-fájlba.
author: mihart
manager: kvivek
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: c18257f1f4e4e3f325c8d4d895e3b6abf88e900c
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794994"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Jelentések exportálása a Power BI-ból PDF-be
A Power BI segítségével közzéteheti jelentését PDF formátumban, és könnyedén létrehozhat egy dokumentumot a Power BI-jelentés alapján. **PDF-fájlba történő exportáláskor** a Power BI-jelentés minden egyes oldalából a PDF dokumentum egy-egy oldala lesz.

## <a name="how-to-export-your-power-bi-report-to-pdf"></a>A Power BI-jelentés exportálása PDF-fájlba
A Power BI szolgáltatásban jelöljön ki egy jelentést a vásznon való megjelenítéshez. Jelentést saját Kezdőlapján, az Alkalmazások között, vagy a bal oldali navigációs panel bármely más szakaszában kijelölhet.

1. Válassza a **Fájl** > **Exportálás PDF-fájlba** lehetőséget a menüsávon.

    ![Válassza a Fájl lehetőséget a menüsávon, majd az Exportálás PDF-be elemre mutató nyilat](media/end-user-pdf/power-bi-export-pdf.png)

    Megjelenik egy előrehaladást jelző sáv a jobb felső sarokban. Az exportálás igénybe vehet néhány percet, de a jelentés exportálása közben Ön tovább dolgozhat a Power BI-ban.

    ![Exportálás előrehaladása üzenet](media/end-user-pdf/power-bi-export-message.png)

    A folyamat végén az értesítési fejlécen üzenet jelenik meg, hogy a Power BI szolgáltatás befejezte az exportálási folyamatot.

2. A fájl mostantól elérhető azon a helyen, ahol a böngésző megjeleníti a letöltött fájlokat. Az alábbi képen ez egy letöltési szalag formájában látható a böngészőablak alján.

    ![A letöltött fájl helye](media/end-user-pdf/power-bi-save-file.png)

Ennyi az egész! Letöltheti a fájlt, és megnyithatja bármely PDF-megtekintő alkalmazással, mint például a Microsoft Edge-ben rendelkezésre állóval.


## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
Az **Exportálás PDF-be** funkció használatakor figyelembe kell vennie néhány megfontolást és korlátozást.

- A munkamenet közbeni interaktivitás egyes formái, mint például a kiemelés, a szűrés és a részletezés, jelenleg még nem támogatottak a PDF-fájlba történő exportálás során. Az exportált PDF-fájl az eredeti vizualizációkat a jelentésben mentett módon mutatja be. Ha szűrőket és szeletelőket alkalmazott, és az exportban is meg szeretné őrizni őket, mentse a jelentést, és az után exportáljon.

* Az **R vizualizációk** jelenleg nem támogatottak. A PDF-fájlban ezek a vizualizációk lehetnek üresek, és megjeleníthetnek egy hibaüzenetet.  

* A **hitelesített** **egyéni vizualizációk** támogatottak. A hitelesített egyéni vizualizációkról, beleértve az egyéni vizualizáció hitelesítési folyamatát, az [Egyéni vizualizáció hitelesítése](../power-bi-custom-visuals-certified.md) oldalon talál további információt. A nem hitelesített egyéni vizualizációk nem támogatottak. A PDF-fájlban hibaüzenettel jelennek meg.   

* A 30-nál több jelentésoldalt tartalmazó jelentések jelenleg nem exportálhatók.

* A jelentés PDF-fájlba történő exportálása néhány percet igénybe vehet, ezért legyen türelemmel. Az exportálás időtartamát többek között a jelentés szerkezete és a Power BI szolgáltatás aktuális terhelése befolyásolhatja.

* Ha az **Exportálás PDF-be** menüpont nem érhető el a Power BI szolgáltatásban, valószínűleg a bérlői rendszergazda letiltotta a funkciót. Részletekért lépjen kapcsolatba a bérlői rendszergazdával.

* A háttérképek szélét a program a diagram határoló területével együtt levágja. Erősen ajánlott, hogy a PDF-fájlba való exportálás előtt távolítsa el a háttérképeket.

* A Power BI bérlői tartományán kívüli felhasználók jelentéseit (például olyan felhasználókét, akik nem a cég munkatársai, de megosztották Önnel a jelentést), nem lehet közzétenni PDF-fájlban.

* Ha egy irányítópultot cégen kívüli felhasználóval oszt meg (tehát olyasvalakivel, aki nincs jelen a Power BI-bérlőben), akkor az a felhasználó nem tudja PDF-fájlba exportálni a megosztott irányítópulthoz kapcsolódó jelentéseket. Például ha Ön aaron@contoso.com, megoszthatja a munkáját a következővel: cassie@cohowinery.com. De cassie@cohowinery.com nem exportálhatja a kapcsolódó jelentéseket PDF-fájlba.

* A Power BI szolgáltatás a PDF-exportálásnál a Power BI nyelvi beállításait alkalmazza. A nyelvi beállításokat megtekintheti vagy módosíthatja a fogaskerék ikon, majd a **Beállítások** > **Általános** > **Nyelv** lehetőség választásával.

## <a name="next-steps"></a>Következő lépések
[Jelentés nyomtatása](end-user-print.md)