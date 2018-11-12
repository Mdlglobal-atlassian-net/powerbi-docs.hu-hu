---
title: Jelentések exportálása Power BI-ból PowerPointba
description: Ismerje meg, hogyan exportálhat jelentést a Power BI-ból a PowerPointba.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 661d615ed33b12ae0557fd8feaa0bc47b3a6638f
ms.sourcegitcommit: ac63e6a082ca8397909217837e8d98c9389b23ac
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50736941"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>Jelentések exportálása Power BI-ból PowerPointba
A Power BI segítségével mostantól közzéteheti jelentését a **Microsoft PowerPointban**, és könnyedén létrehozhat bemutatót a Power BI-jelentés alapján. A **PowerPointba történő exportáláskor** a következő történik:

* A PowerPointban a Power BI-jelentés minden lapjából külön dia lesz
* A rendszer a Power BI-jelentés minden oldalát egyetlen, magas felbontású képként exportálja a PowerPointba
* A Power BI-jelentés szövegdobozai a PowerPointban szerkeszthető szövegdobozok lesznek
* A PowerPointban létrejön egy hivatkozás, amely a Power BI-jelentésre mutat

A **Power BI-jelentést** egyszerűen exportálhatja a **PowerPointba**. Csak kövesse az alábbi szakaszban leírt lépéseket.

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>Hogyan exportálhatja a Power BI-jelentést a PowerPointba
A Power BI szolgáltatás bal oldali navigációs ablaktábláján a **Jelentések** elemre kattintva bontsa ki a szakaszt, majd válassza ki a vásznon megjeleníteni kívánt jelentést. Ha a jelentés megtalálható a **Saját munkaterület** vagy a **Kedvencek** szakaszban, akkor ezeken a helyeken is kijelölheti.

![](media/end-user-powerpoint/powerbi_to_powerpoint_0.png)

Amikor a PowerPointba exportálandó jelentés megjelenik a vásznon, kattintson a **Fájl > Exportálás a PowerPointba (előzetes verzió)** elemre a Power BI szolgáltatás menüsávján, az alábbi kép szerint.

![](media/end-user-powerpoint/powerbi_to_powerpoint_1.png)

Ekkor a Power BI szolgáltatás böngészőablakának jobb felső sarkában megjelenik egy értesítés, hogy folyamatban van a jelentés exportálása a PowerPointba. Ez igénybe vehet néhány percet, de a jelentés exportálása közben Ön tovább dolgozhat a Power BI-ban.

![](media/end-user-powerpoint/powerbi_to_powerpoint_2.png)

A folyamat végén az értesítési fejlécen üzenet jelenik meg, hogy a Power BI szolgáltatás befejezte az exportálási folyamatot.

![](media/end-user-powerpoint/powerbi_to_powerpoint_3.png)

A fájl mostantól elérhető azon a helyen, ahol a böngésző megjeleníti a letöltött fájlokat. Az alábbi képen ez egy letöltési szalag formájában látható a böngészőablak alján.

![](media/end-user-powerpoint/powerbi_to_powerpoint_4.png)

És már kész is van. A fájlt letöltheti, megnyithatja a PowerPointban, módosíthatja és kibővítheti, mint minden más PowerPoint-bemutatót.

## <a name="checking-out-your-exported-powerpoint-file"></a>Az exportált PowerPoint-fájl megtekintése
Amikor megnyitja a Power BI-ból exportált PowerPoint-fájlt, számos remek és praktikus elemet talál. Tekintse meg az alábbi képet, és nézze végig a számozott elemek által szemléltetett nagyszerű funkciókat.

![](media/end-user-powerpoint/powerbi_to_powerpoint_5.png)

1. A bemutató első oldalán a jelentés neve és egy hivatkozás látható, amelynek segítségével a bemutató alapjául szolgáló jelentést **megtekintheti a Power BI-ban**.
2. Továbbá olyan hasznos információkat kap a jelentésről, mint például az exportált jelentés alapjául szolgáló *legutóbbi adatfrissítés* és a *letöltés ideje*, amely a Power BI-jelentés PowerPoint-fájlba történt exportálásának dátumát adja meg.
3. A jelentés minden oldala külön dián jelenik meg, ahogy a bal oldali navigációs ablaktábla mutatja.
4. A közzétett jelentést a Power BI a saját nyelvi beállításainak megfelelően, vagy a böngésző nyelve szerint rendereli. A nyelvi beállításokat megtekintheti vagy módosíthatja a fogaskerék ikon, majd a ![](./media/end-user-powerpoint/power-bi-settings-icon.png) **> Beállítások > Általános > Nyelv** lehetőség választásával. Nyelvi információk: [A Power BI által támogatott nyelvek és országok/régiók](../supported-languages-countries-regions.md).
5. A PowerPoint-bemutató tartalmaz egy címoldalt, amelyen megjelenik az exportált idő a megfelelő időzónában.

Bármelyik önálló diára kattintva megfigyelheti, hogy minden egyes jelentésoldal külön kép.

>[!NOTE]
> Az, hogy minden egyes jelentésoldalhoz egy vizualizáció tartozik, új funkció. Ez előző viselkedés, amelynél minden vizualizációhoz egy-egy különálló kép tatozott, már nem funkcionál. 
 

![](media/end-user-powerpoint/powerbi_to_powerpoint_6.png)

Most már csak Önön múlik, hogy miképpen használja fel a PowerPoint-bemutatót vagy a magas felbontású képeket.

## <a name="limitations"></a>Korlátozások
Az **Exportálás a PowerPointba** funkció használatakor figyelembe kell vennie néhány megfontolást és korlátozást.

* Az **R vizualizációk** jelenleg nem támogatottak. Az ilyen vizualizációkat a rendszer üres képként exportálja a PowerPointba, és hibaüzenetet küld, hogy a vizualizáció nem támogatott.
* A **hitelesített** **egyéni vizualizációk** támogatottak. A hitelesített egyéni vizualizációkról, beleértve az egyéni vizualizáció hitelesítési folyamatát, az [Egyéni vizualizáció hitelesítése](../power-bi-custom-visuals-certified.md) oldalon talál további információt. A nem hitelesített egyéni vizualizációkat a rendszer üres képként exportálja a PowerPointba, és hibaüzenetet küld, hogy a vizualizáció nem támogatott.
* A **hitelesített egyéni vizualizációk** támogatottak. A hitelesített egyéni vizualizáció használatát jóváhagyták a Power BI-ban, kódja megfelel bizonyos követelményeknek, és szigorú biztonsági ellenőrzésen ment át. [Ismerje meg részletesebben **a hitelesített egyéni vizualizációkat**](../power-bi-custom-visuals-certified.md).
* A 30-nál több jelentésoldalt tartalmazó jelentések jelenleg nem exportálhatók.
* A jelentés PowerPointba történő exportálása néhány percet igénybe vehet, ezért türelmét kérjük. Az exportálás időtartamát többek között a jelentés szerkezete és a Power BI szolgáltatás aktuális terhelése befolyásolhatja.
* Ha az **Exportálás a PowerPointba** menüpont nem érhető el a Power BI szolgáltatásban, valószínűleg a bérlői rendszergazda letiltotta a funkciót. Lépjen kapcsolatba a bérlői rendszergazdával.
* A háttérképek szélét a program a diagram határoló területével együtt levágja. Erősen ajánljuk, hogy a PowerPointba való exportálás előtt távolítsa el a háttérképeket.
* A **munkamenet közbeni interaktivitás** egyes formái, mint például a kiemelés, a szűrés és a részletezés, jelenleg még nem támogatottak a PowerPointba történő exportálás során. Az exportált PowerPoint az eredeti vizualizációkat a jelentésben mentett módon mutatja be.
* A PowerPoint lapjai, függetlenül a Power BI-jelentés eredeti oldalméreteitől és dimenzióitól, mindig a szabványos 9:16 méretben jönnek létre.
* A Power BI bérlői tartományán kívüli felhasználók jelentéseit (például olyan felhasználókét, akik nem a cég munkatársai, de megosztották Önnel a jelentést), nem lehet közzétenni a PowerPointban.
* Ha egy irányítópultot cégen kívüli felhasználóval oszt meg (tehát olyasvalakivel, aki nincs jelen a Power BI-bérlőn), akkor az a felhasználó nem tudja a PowerPointba exportálni a megosztott irányítópulthoz kapcsolódó jelentéseket. Például ha Ön aaron@contoso.com, megoszthatja a munkáját a következővel: david@cohowinery.com. De david@cohowinery.com nem exportálhatja a kapcsolódó jelentéseket a PowerPointba.
* Ahogy korábban említettük, a rendszer minden jelentésoldalt külön képként exportál a PowerPoint-fájlba.
* A Power BI szolgáltatás a PowerPoint-exportálásnál a Power BI nyelvi beállításait alkalmazza. A nyelvi beállításokat megtekintheti vagy módosíthatja a fogaskerék ikon, majd a ![](./media/end-user-powerpoint/power-bi-settings-icon.png) **> Beállítások > Általános > Nyelv** lehetőség választásával.
* Az exportált PowerPoint-fájl címoldalán található **Letöltés ideje** a számítógép időzónáját követi a letöltés idején.

## <a name="next-steps"></a>Következő lépések
[Elemzés az Excelben](../service-analyze-in-excel.md)

[Excel-adatok a Power BI-ban](../service-excel-workbook-files.md)

[Egyéni vizuális elem hitelesítése](../power-bi-custom-visuals-certified.md)

