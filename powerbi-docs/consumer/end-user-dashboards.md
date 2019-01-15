---
title: Mi az az irányítópult és hogyan lehet megnyitni?
description: Az irányítópult a Power BI szolgáltatás egyik legfontosabb funkciója.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: f0dad05569bdebcd83a57a396d0edead5a741353
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279872"
---
# <a name="dashboards-for-power-bi-service-consumers"></a>Irányítópultok a Power BI szolgáltatás felhasználói számára

A Power BI-***irányítópult*** egy gyakran vászonnak is nevezett oldal, amely vizualizációk segítségével mesél el egy történetet. Mivel az irányítópult egyetlen lapon jelenik meg, ezért a jól megtervezett irányítópult csak a történet legfontosabb elemeit tartalmazza.

![irányítópult](media/end-user-dashboards/power-bi-dashboard2.png)

Az irányítópulton látható vizualizációkat *csempéknek* nevezik, és a jelentésekből *rögzíthetők* az irányítópultra. Ha csak most kezdte el használni a Power BI-t, a [Power BI alapfogalmait](end-user-basic-concepts.md) elolvasva egyszerűen elsajátíthatja az alapokat.

> [!NOTE]
> Az irányítópult a Power BI szolgáltatás egyik funkciója, ezért a Power BI Desktopban nem érhető el. Mobileszközökön csak [megtekinteni és megosztani](mobile/mobile-apps-view-dashboard.md) lehet az irányítópultokat, létrehozni nem.
> 
> 

Az irányítópulton megjelenő vizualizációk a jelentéseken, az egyes jelentések pedig egy-egy adatkészleten alapulnak. Az irányítópultok tulajdonképpen az alapjául szolgáló jelentésekhez és adatkészletekhez való hozzáférési útnak is tekinthetők. Egy vizualizáció kiválasztásával hozzáférhet a létrehozásához használt jelentéshez (és adatkészlethez).

![az irányítópultok, jelentések és adatkészletek közötti kapcsolatot megjelenítő diagram](media/end-user-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Az irányítópultok előnyei
Az irányítópultok segítségével nagyszerűen nyomon követheti üzletmenetét, választ találhat kérdéseire, és egyetlen pillantással megtekintheti a legfontosabb mérőszámokat. Az irányítópulton található vizualizációk egy vagy több adatkészletből vagy jelentésből is származhatnak. Az irányítópult a helyi és a felhőben keletkezett adatokat ötvözi, és egyesített nézetet biztosít függetlenül attól, hogy az adatok hol találhatók.

Az irányítópult nem csak egy tetszetős kép, hanem egy interaktív, egyénre szabható funkció, amelyben az egyes csempék az alapul szolgáló adatok változásának megfelelően frissülnek.

## <a name="dashboards-versus-reports"></a>Irányítópultok és jelentések
A jelentéseket könnyű összekeverni az irányítópultokkal, mivel mind a kettő egy vizualizációkkal teli vászon. Azonban van köztük néhány alapvető különbség.

| **Képesség** | **Irányítópultok** | **Jelentések** |
| --- | --- | --- |
| Oldalak |Egy oldal |Egy vagy több oldal |
| Adatforrások |Egy vagy több jelentés és egy vagy több adatkészlet irányítópultonként |Egyetlen adatkészlet jelentésenként |
| Elérhető a Power BI Desktopban |Nem |Igen, a jelentések létrehozhatók és megtekinthetők a Desktopban |
| Rögzítés |Csak az aktuális irányítópultról képes a létező vizualizációkat (csempéket) más irányítópultokra rögzíteni |Bármelyik irányítópultra képes rögzíteni a vizualizációkat (csempékként). Teljes oldalakat rögzíthet a jelentésből bármely irányítópultra. |
| Előfizetés |Nem fizethet elő irányítópultra |Előfizethet jelentésoldalakra |
| Szűrés |Nem lehet szűrni és szeletelni |Számos szűrési, kiemelési és szeletelési móddal rendelkezik |
| Riasztások beállítása |Létrehozhat olyan riasztásokat, amelyek e-mailen keresztül értesítik, ha a feltételek teljesülnek |Nem |
| Kiemelés |Kiválaszthat és beállíthat egy „kiemelt” irányítópultot |Nem hozhat létre kiemelt jelentést |
| Természetes nyelven történő lekérdezések |Elérhető az irányítópultból |Nem érhető el a jelentésekből |
| Megváltoztathatja a vizualizáció típusát |Nem. Ha egy jelentéstulajdonos megváltoztatja a vizualizáció típusát a jelentésen belül, az irányítópulton rögzített vizualizáció nem fog frissülni |Igen |
| Láthatja az alapul szolgáló adatkészlet-táblázatokat és -mezőket |Nem. Exportálhatja az adatokat, de magán az irányítópulton nem fogja látni a táblázatokat és a mezőket. |Igen. Láthatja az adatkészlet-táblázatokat, -mezőket és -értékeket. |
| Létrehozhat vizualizációkat |Csak a widgetek irányítópulthoz történő hozzáadása lehetséges a „Csempe hozzáadása” lehetőség használatával |A Szerkesztési engedéllyel létrehozhat számos különböző vizualizációtípust, egyéni vizualizációkat adhat hozzá és szerkeszthet stb. |
| Testreszabás |Mozgathatja és rendezheti a vizualizációkat (csempéket), újraméretezheti őket és hivatkozásokat adhat hozzájuk, valamint átnevezheti, törölheti vagy teljes képernyőn jelenítheti meg őket. Maguk az adatok és a vizualizációk azonban csak olvashatók. |Az olvasási nézetben közzétehet, beágyazhat, szűrhet és exportálhat adatokat, letölthet .pbix-ként, megtekintheti a vonatkozó tartalmakat, QR-kódokat generálhat, exceles elemzést hajthat végre stb.  Szerkesztési nézetben a fent említettek mellett számos más dolgot is végrehajthat. |

## <a name="dashboard-creators-and-dashboard-consumers"></a>Az irányítópultok létrehozói és felhasználói
Szerepkörétől függően létrehozhat irányítópultokat saját maga vagy akár kollégái számára. Szeretné megtanulni, hogyan hozhat létre és oszthat meg irányítópultokat. Vagy más felhasználóktól is kapja az irányítópultokat. Szeretné megtanulni, hogyan kell értelmeznie és használnia azokat.

Összegyűjtöttünk önnek néhány témát szerepkör szerint, hogy segítsünk megtenni az első lépéseket.

A Power BI Pro az irányítópultok megosztásához és a megosztott irányítópultok megtekintéséhez is szükséges.

### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Ha irányítópultokat fogad és használ
* [Minta-irányítópultjaink](../sample-tutorial-connect-to-the-samples.md) egyikének megtekintése révén megismerkedhet az irányítópultok használatával.
* Ismerkedjen meg az [irányítópult-csempékkel](end-user-tiles.md), és fedezze fel mi történik, ha kiválaszt egy csempét.
* Szeretne nyomon követni egy adott irányítópult-csempét, és e-mailes értesítést kapni, ha elér egy bizonyos küszöbértéket? [Riasztások létrehozása a csempéken](end-user-alerts.md).
* Tegye fel bátran az irányítópultokkal kapcsolatos kérdéseit. Fedezze fel, hogyan teheti fel az adatokkal kapcsolatos kérdéseit és szerezheti meg a válaszokat vizualizáció formájában a [Power BI Q&A](end-user-q-and-a.md) segítségével.

> [!TIP]
> Ha nem találta meg, amit keres, használja a bal oldalon található tartalomjegyzéket.
> 

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](../power-bi-overview.md)  
[Power BI – Alapfogalmak](end-user-basic-concepts.md)  