---
title: Irányítópultok a Power BI szolgáltatás tervezői számára – bevezetés
description: Az irányítópult a Power BI szolgáltatás egyik legfontosabb funkciója. Ez egy gyakran vászonnak is nevezett oldal, amely vizualizációk segítségével mutat be információkat.
author: maggieMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 41381a2f0ccc2c5db904d9ac94c7dad19edfa4e5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872744"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Irányítópultok a Power BI szolgáltatás tervezői számára – bevezetés

A *Power BI-irányítópult* egy gyakran vászonnak is nevezett oldal, amely vizualizációk segítségével mutat be információkat. Mivel egyetlen lapon jelenik meg, ezért a jól megtervezett irányítópult csak a történet legfontosabb elemeit tartalmazza. Az olvasók a kapcsolódó jelentésekben tekinthetik meg a részleteket.

![Irányítópult](media/service-dashboards/power-bi-dashboard2.png)

Az irányítópult funkció csak a Power BI szolgáltatásban érhető el. A Power BI Desktopban nem érhetők el. Mobileszközön nem hozhat létre irányítópultokat, azonban [megtekintheti és megoszthatja](mobile-apps-view-dashboard.md) őket.

## <a name="dashboard-basics"></a>Irányítópult – alapok 

Az irányítópulton látható vizualizációkat *csempéknek* nevezik. Ezek jelentésekből *rögzíthetők* az irányítópultra. Ha csak most kezdte el használni a Power BI-t, a [Power BI szolgáltatás tervezői számára az alapfogalmakat](service-basic-concepts.md) ismertető cikket elolvasva egyszerűen elsajátíthatja az alapokat.

Az irányítópulton megjelenő vizualizációk a jelentéseken, az egyes jelentések pedig egy-egy adatkészleten alapulnak. Az irányítópultok az alapjául szolgáló jelentésekhez és adatkészletekhez való hozzáférési útnak is tekinthetők. Egy vizualizáció kiválasztásával hozzáférhet az alapjául szolgáló jelentéshez (és adatkészlethez).

![Az irányítópultok, jelentések és adatkészletek közötti kapcsolatot megjelenítő diagram](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Az irányítópultok előnyei
Az irányítópultok segítségével nagyszerűen nyomon követheti üzletmenetét, és egyetlen pillantással megtekintheti a legfontosabb mérőszámokat. Az irányítópulton található vizualizációk egy vagy több adatkészletből vagy jelentésből is származhatnak. Az irányítópult a helyi és a felhőben keletkezett adatokat ötvözi, és egyesített nézetet biztosít függetlenül attól, hogy az adatok hol találhatók.

Az irányítópult nem csak egy tetszetős kép. Egy interaktív funkció, amelyben az egyes csempék az alapul szolgáló adatok változásának megfelelően frissülnek.

## <a name="who-can-create-a-dashboard"></a>Ki hozhat lére irányítópultot?
Az irányítópult létrehozása *létrehozói* művelet, ezért csak akkor végezheti el, ha jogosultsága van a jelentést szerkeszteni. Szerkesztési jogosultsággal a jelentés létrehozója rendelkezik, valamint azok, akikek a létrehozó engedélyezte ezt. Ha például Dávid létrehoz egy jelentést az ABC munkaterületen, Önt pedig felveszi tagként erre a munkaterületre, akkor Ön is és Dávid is rendelkezik szerkesztési jogosultsággal. Ha azonban a jelentés meg van osztva Önnel, akár közvetlenül, akár egy [Power BI-alkalmazás](service-create-distribute-apps.md) részeként, Ön a jelentés *felhasználója*. Ilyen esetben nem feltétlenül rögzíthet csempéket az irányítópultra. 

> [!IMPORTANT]
> Irányítópult létrehozásához [Power BI Pro-licencre](service-free-vs-pro.md) van szüksége a munkaterületen. A Saját munkaterületen Power BI Pro-licenc nélkül is hozhat létre irányítópultokat.


## <a name="dashboards-versus-reports"></a>Irányítópultok és jelentések
A [jelentések](service-reports.md) hasonlítanak az irányítópultokra, mivel mind a kettő egy vizualizációkkal teli vászon. Azonban jelentősen el is térnek bizonyos dolgokban, ahogyan a következő táblázatban látható.

| **Képesség** | **Irányítópultok** | **Jelentések** |
| --- | --- | --- |
| Oldalak |Egy oldal |Egy vagy több oldal |
| Adatforrások |Egy vagy több jelentés és egy vagy több adatkészlet irányítópultonként |Egyetlen adatkészlet jelentésenként |
| Elérhető a Power BI Desktopban |Nem | Igen. Létrehozhatnak és megtekinthetnek jelentéseket a Power BI Desktopban |
| Feliratkozás |Igen. Feliratkozhat irányítópultra |Igen. Feliratkozhat jelentésoldalra |
| Szűrés |Nem. Nem lehet szűrni és szeletelni |Igen. Számos szűrési, kiemelési és szeletelési móddal rendelkezik |
| Kiemelt |Igen. Kiválaszthat és beállíthat egy *kiemelt* irányítópultot |Nem |
| Kedvenc | Igen. Több irányítópultot *kedvencként* jelölhet meg | Igen. Több jelentést *kedvencként* jelölhet meg
| Riasztások beállítása |Igen. Bizonyos helyzetekben elérhető irányítópultok csempéihez |Nem |
| Természetes nyelven történő lekérdezések (Q&A) |Igen | Igen, ha szerkesztési jogosultsága van a jelentéshez és az alapul szolgáló adathalmazhoz |
| Láthatja az alapul szolgáló adatkészlet-táblázatokat és -mezőket |Nem. Exportálhatja az adatokat, de magán az irányítópulton nem fogja látni a táblázatokat és a mezőket |Igen |


## <a name="next-steps"></a>Következő lépések
* [Minta-irányítópultjaink](sample-tutorial-connect-to-the-samples.md) egyikének megtekintése révén megismerkedhet az irányítópultok használatával.
* Információ az [irányítópult csempéiről](service-dashboard-tiles.md).
* Szeretne nyomon követni egy adott irányítópult-csempét, és e-mailes értesítést kapni, ha elér egy bizonyos küszöbértéket? [Hozzon létre egy riasztást egy csempén](service-set-data-alerts.md).
* Fedezze fel, hogyan teheti fel az adatokkal kapcsolatos kérdéseit és szerezheti meg a válaszokat vizualizáció formájában a [Power BI Q&A](power-bi-tutorial-q-and-a.md) segítségével.
