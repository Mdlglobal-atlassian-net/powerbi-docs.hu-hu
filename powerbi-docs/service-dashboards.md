---
title: Irányítópultok a Power BI szolgáltatásban
description: Az irányítópult a Power BI szolgáltatás egyik legfontosabb funkciója.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: b7f94d47452fb9d1ea24c950dba2988c6c80c053
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/20/2018
ms.locfileid: "49473728"
---
# <a name="dashboards-in-the-power-bi-service"></a>Irányítópultok a Power BI szolgáltatásban

A Power BI-***irányítópult*** egy gyakran vászonnak is nevezett oldal, amely vizualizációk segítségével mesél el egy történetet. Mivel az irányítópult egyetlen lapon jelenik meg, ezért a jól megtervezett irányítópult csak a történet legfontosabb elemeit tartalmazza.

![irányítópult](media/service-dashboards/power-bi-dashboard2.png)

Az irányítópult a Power BI szolgáltatás egyik funkciója, ezért a Power BI Desktopban nem érhető el. Mobileszközökön csak [megtekinteni és megosztani](mobile-apps-view-dashboard.md) lehet az irányítópultokat, létrehozni nem.

## <a name="dashboard-creators-and-dashboard-consumers"></a>Az irányítópultok létrehozói és felhasználói
Szerepkörétől függően létrehozhat irányítópultokat saját maga vagy akár kollégái számára. Információt az **Irányítópult létrehozóknak** című tájékoztatóban találhat. Ha más felhasználóktól kapja az irányítópultokat. Szeretné megtanulni, hogyan kell értelmeznie és használnia azokat. Akkor ez a cikk Önnek szól!


### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Ha irányítópultokat fogad és használ

Az irányítópulton látható vizualizációkat *csempéknek* nevezik, és az irányítópult *létrehozói* a jelentésekből az irányítópultokra *rögzíthetik* őket. Ha csak most kezdte el használni a Power BI-t, a [Power BI alapfogalmait](service-basic-concepts.md) elolvasva egyszerűen elsajátíthatja az alapokat.

> [!IMPORTANT]
> A megosztott irányítópultok megtekintéséhez [Power BI Pro](service-free-vs-pro.md) szükséges.

Az irányítópulton megjelenő vizualizációk a jelentéseken, az egyes jelentések pedig egy-egy adatkészleten alapulnak. Az irányítópultok tulajdonképpen az alapjául szolgáló jelentésekhez és adatkészletekhez való hozzáférési útnak is tekinthetők. Egy vizualizáció kiválasztásával hozzáférhet a létrehozásához használt jelentéshez (és adatkészlethez).

![az irányítópultok, jelentések és adatkészletek közötti kapcsolatot megjelenítő diagram](media/service-dashboards/power-bi-diagram.png)



## <a name="advantages-of-dashboards"></a>Az irányítópultok előnyei
Az irányítópultok segítségével nagyszerűen nyomon követheti üzletmenetét, választ találhat kérdéseire, és egyetlen pillantással megtekintheti a legfontosabb mérőszámokat. Az irányítópulton található vizualizációk egy vagy több adatkészletből vagy jelentésből is származhatnak. Az irányítópult a helyi és a felhőben keletkezett adatokat ötvözi, és egyesített nézetet biztosít függetlenül attól, hogy az adatok hol találhatók.

Az irányítópult nem csak egy tetszetős kép, hanem egy interaktív funkció, amelyben az egyes csempék az alapul szolgáló adatok változásának megfelelően frissülnek.

## <a name="dashboards-versus-reports"></a>Irányítópultok és jelentések
A [Jelentések](service-reports.md) összekeverhetők az irányítópultokkal, mivel mind a kettő egy vizualizációkkal teli vászon. Azonban van köztük néhány alapvető különbség a Power BI felhasználói számára.

| **Képesség** | **Irányítópultok** | **Jelentések** |
| --- | --- | --- |
| Oldalak |Egy oldal |Egy vagy több oldal |
| Adatforrások |Egy vagy több jelentés és egy vagy több adatkészlet irányítópultonként |Egyetlen adatkészlet jelentésenként |
| Elérhető a Power BI Desktopban |Nem |Igen, a ***létrehozók*** létrehozhatnak és megtekinthetnek jelentéseket a Desktopban |
| Előfizetés |Feliratkozhat irányítópultra |Előfizethet jelentésoldalakra |
| Szűrés |Nem lehet szűrni és szeletelni |Számos szűrési, kiemelési és szeletelési móddal rendelkezik |
| Kiemelt |Kiválaszthat és beállíthat egy „kiemelt” irányítópultot |Nem hozhat létre kiemelt jelentést |
| Kedvenc | Irányítópultokat *kedvencként* jelölhet meg | Jelentéseket *kedvencként* jelölhet meg
| Riasztások beállítása |Bizonyos helyzetekben elérhető irányítópultok csempéihez |Nem érhető el a jelentésekből |
| Természetes nyelven történő lekérdezések |Elérhető az irányítópultból |Nem érhető el a jelentésekből |
| Láthatja az alapul szolgáló adatkészlet-táblázatokat és -mezőket |Nem. Exportálhatja az adatokat, de magán az irányítópulton nem fogja látni a táblázatokat és a mezőket. |Igen. Láthatja az adatkészlet-táblázatokat, -mezőket és -értékeket. |
| Testreszabás |Nem |Az olvasási nézetben közzétehet, beágyazhat, szűrhet és exportálhat adatokat, letöltheti őket .pbix-ként, megtekintheti a vonatkozó tartalmakat, QR-kódokat generálhat, exceles elemzést hajthat végre stb.  |

## <a name="next-steps"></a>Következő lépések
* [Minta-irányítópultjaink](sample-tutorial-connect-to-the-samples.md) egyikének megtekintése révén megismerkedhet az irányítópultok használatával.
* Ismerkedjen meg az [irányítópult-csempékkel](service-dashboard-tiles.md), és fedezze fel mi történik, ha kiválaszt egy csempét.
* Szeretne nyomon követni egy adott irányítópult-csempét, és e-mailes értesítést kapni, ha elér egy bizonyos küszöbértéket? [Riasztások létrehozása a csempéken](service-set-data-alerts.md).
* Tegye fel bátran az irányítópultokkal kapcsolatos kérdéseit. Fedezze fel, hogyan teheti fel az adatokkal kapcsolatos kérdéseit és szerezheti meg a válaszokat vizualizáció formájában a [Power BI Q&A](power-bi-tutorial-q-and-a.md) segítségével.
