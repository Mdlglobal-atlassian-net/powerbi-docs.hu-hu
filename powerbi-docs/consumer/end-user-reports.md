---
title: Jelentés megtekintése a Power BI-ban
description: Jelentések a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 9a844ff813435328df63240aa46aff3430117f6e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532182"
---
# <a name="reports-in-power-bi"></a>Jelentések a Power BI-ban

A Power BI-jelentések az adathalmazok többszempontú nézetei, amelyek az adathalmazból származó különféle eredményeket és megállapításokat bemutató vizualizációkat tartalmaznak.  A jelentések egyetlen vagy akár több oldalnyi vizualizációt is tartalmazhatnak. Munkahelyi szerepkörétől függően lehet, hogy Ön jelentéseket *tervez*. Előfordulhat az is, hogy jelentéseket *használ*.

![Képernyőkép egy jelentésoldalról.](./media/end-user-reports/power-bi-report.png)

Ez a jelentés négy oldallal (vagy lappal) rendelkezik, és jelenleg a **Hangulat** oldalt látja. Ezen az oldalon öt különböző vizualizáció és egy oldalcím található.

Ha csak most kezdte el használni a Power BI-t, a [Power BI szolgáltatás felhasználói számára az alapfogalmakat](end-user-basic-concepts.md) ismertető cikket elolvasva egyszerűen elsajátíthatja az alapokat. A jelentések megtekinthetők és megoszthatók mobileszközön, illetve jegyzetek fűzhetők hozzájuk. További információ: [Jelentések vizsgálata a Power BI-mobilalkalmazásokban](mobile/mobile-reports-in-the-mobile-apps.md).

## <a name="advantages-of-reports"></a>A jelentések előnyei

A Power BI egyetlen adathalmazra alapozza a jelentéseket. A jelentések egy-egy információmorzsát ábrázoló vizualizációit a *tervezők* hozzák létre. A vizualizációk nem statikusak.  Az alapul szolgáló adatok változásának megfelelően frissülnek. A vizualizációkat és szűrőket használva részletesen áttekintheti az adatokat megállapítások kinyerése és válaszok keresése céljából. Az irányítópultokhoz hasonlóan a jelentések is nagy mértékben interaktívak és személyre szabhatók.

### <a name="safely-interact-with-content"></a>A tartalom biztonságos kezelése

A tartalmak kezelése és használata (szűrés, szeletelés, feliratkozás és exportálás) során nem tudja tönkretenni a jelentéseket. A munkája nincs hatással az alapul szolgáló adathalmazra vagy az eredeti megosztott tartalomra. Ez egyaránt vonatkozik az irányítópultokra, jelentésekre és alkalmazásokra.

> [!NOTE]
> Ne feledje, nem tud kárt tenni az adatokban. A Power BI nagyszerű eszközt jelent a felfedezéshez és kísérletezéshez, és közben nem kell amiatt aggódnia, hogy elront valamit.

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>Módosítások mentése vagy visszaállítás az alapértelmezett beállításokra

Ez nem azt jelenti, hogy a módosításait nem mentheti. Megteheti, a módosítások azonban egyedül azt befolyásolják, ahogyan Ön látja a tartalmakat. A jelentés eredeti alapértelmezett nézetének visszaállításához válassza a **Visszaállítás alapértelmezettre** elemet.

## <a name="dashboards-versus-reports"></a>Irányítópultok és jelentések

Az [irányítópultokat](end-user-dashboards.md) gyakran összekeverik a jelentésekkel, mivel mindegyik egy vizualizációkkal teli vászon. Azonban van köztük néhány alapvető különbség.  

| **Képesség** | **Irányítópultok** | **Jelentések** |
| --- | --- | --- |
| Oldalak |Egy oldal |Egy vagy több oldal |
| Adatforrások |Egy vagy több jelentés és egy vagy több adatkészlet irányítópultonként |Egyetlen adatkészlet jelentésenként |
| Szűrés |Nem lehet szűrni és szeletelni |Számos szűrési, kiemelési és szeletelési móddal rendelkezik |
| Riasztások beállítása |Létrehozhat olyan riasztásokat, amelyek e-mailen keresztül értesítik, ha az irányítópult teljesít bizonyos feltételeket |Nem |
| Funkció |Kiválaszthat és beállíthat egy kiemelt irányítópultot |Nem hozhat létre kiemelt jelentést |
| Láthatja az alapul szolgáló adatkészlet-táblázatokat és -mezőket |Nem. Exportálhatja az adatokat, de magán az irányítópulton nem fogja látni az adathalmaz táblázatait és mezőit |Igen. Láthatja az adathalmaz-táblázatokat, -mezőket és -értékeket, amelyek megtekintésére engedélye van |
| Testreszabás |Nem  |Szűrhet, exportálhat, megtekinthet kapcsolódó tartalmakat, könyvjelzőket adhat hozzá, QR-kódokat hozhat létre, exceles elemzést hajthat végre stb. |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-designers-and-report-consumers"></a>Jelentéstervezők és jelentésfelhasználók

A szerepkörétől függően Ön lehet *tervező*, aki jelentéseket hoz létre saját használatra vagy a munkatársakkal való megosztáshoz. Ez esetben a jelentések létrehozásáról és megosztásáról kell ismereteket szereznie.

Lehet *felhasználó* is, aki másoktól kap jelentéseket. Ez esetben azt kell tudnia, hogyan értelmezheti és használhatja a jelentéseket. Ha Ön *jelentésfelhasználó*, ezeket a hivatkozásokat ajánljuk:

* Kezdje a [Power BI szolgáltatás áttekintésével](end-user-basic-concepts.md), amelyből megtudhatja, hol találhatja meg a jelentéseket és a jelentéseszközöket.
* Ismerje meg, hogyan tud [megnyitni egy jelentést](end-user-report-open.md), és fedezze fel az [Olvasó nézetben](end-user-reading-view.md) elérhető műveleteket.
* Gyakorolja a jelentések használatát az egyik [mintánk](../sample-tutorial-connect-to-the-samples.md) segítségével.  
* Annak megtekintéséhez, hogy a jelentés melyik adathalmazt használja, és mely irányítópultok rendelkeznek a jelentésből rögzített csempékkel, olvassa el a [kapcsolódó tartalom Power BI szolgáltatásban való megtekintését](end-user-related.md) ismertető témakört.

> [!TIP]
> Ha nem találta meg itt, amit keres, a bal oldali tartalomjegyzékben böngészhet a *jelentésekhez* kapcsolódó cikkek között.

## <a name="next-steps"></a>Következő lépések

[Mi az a Power BI?](../power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai felhasználók számára](end-user-basic-concepts.md)