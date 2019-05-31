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
ms.date: 5/10/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 02652bd027d7dab8a40d77fb92c5aae8f09d8820
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607893"
---
# <a name="reports-in-power-bi"></a>Jelentések a Power BI-ban
## <a name="what-is-a-power-bi-report"></a>Mi a Power BI-jelentés?
A Power BI ***jelentés*** adatkészletbe, az adott adathalmazból származó eredményeket és meglátásokat különböző bemutató képviselő Vizualizációk nézőpontból nézet.  Egy jelentés egyetlen vizualizáción vagy a Vizualizációk teljes oldalak rendelkezhetnek. Függően, hogy lehet olyan személy akik *tervek* jelentéseket, illetve előfordulhat, hogy lehet olyan személy, aki *használ fel* vagy jelentéseket használ.

![jelentés oldala](./media/end-user-reports/power-bi-report.png)

Ez a jelentés hat oldalak (vagy lapok) rendelkezik, és jelenleg nézi, hogy a róluk szóló véleményeket lap. Ezen az oldalon a következők 6 különböző vizualizációt és egy lapcímet.  

Ha először használja a Power BI-t, sok mindent megtudhat, ha elolvassa a [Power BI alapvető fogalmai](end-user-basic-concepts.md) című témakört.

Jelentések megtekintését, megosztását és a mobileszközök jegyzetkészítés érhetők el. További információkért lásd: [mobil Power BI-jelentések](mobile/mobile-reports-in-the-mobile-apps.md).

## <a name="advantages-of-reports"></a>A jelentések előnyei
A jelentések egyetlen adatkészleten alapulnak. A jelentés hozzák létre a jelentésekben a vizualizációkban *tervezők* , és olyan információk nuget képviseli. A Vizualizációk nem statikusak; és használhatja a vizualizációkat és szűrőket szintjére lehatolva elemzésekhez és a válaszok kereséséhez az adatok. Például egy irányítópultot azonban más –, egy jelentés így interaktív és nagymértékben testre szabható, és a Vizualizációk frissítése az alapul szolgáló adatok változásának megfelelően.

### <a name="safely-interact-with-content"></a>A tartalom biztonságos kezelése
Fedezze fel és kezelheti a tartalmat, szűrés, tovább szeletelve, feliratkozik, és exportálása, biztosítják nyugalmát; a munkahelyi nem befolyásolja az alapjául szolgáló adatkészletet vagy az eredeti megosztott tartalmak (irányítópultok, jelentések és alkalmazások).
 
> [!NOTE]
> Ne feledje, hogy nem csökkentheti a adatait. A Power BI a nagyszerű hely ismerje meg, és nem kell, hogy "elront" bármit kísérletezhet.

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>Mentse a módosításokat, vagy az alapértelmezett beállítások visszaállítása
Ez nem jelenti azt, nem tudja menteni a módosításokat; Igen, de ezek a módosítások csak a tartalom a megjelenített hatással. Visszaállítás az eredeti alapértelmezett nézet a visszaállítás az alapértelmezett gomb kiválasztásával beállítható.

## <a name="dashboards-versus-reports"></a>Irányítópultok és jelentések
[Az irányítópultok](end-user-dashboards.md) általában a jelentésekkel, mert ezek is összetévesztik a vizualizációkat. Azonban van köztük néhány alapvető különbség.  

| **Képesség** | **Irányítópultok** | **Jelentések** |
| --- | --- | --- |
| Oldalak |Egy oldal |Egy vagy több oldal |
| Adatforrások |Egy vagy több jelentés és egy vagy több adatkészlet irányítópultonként |Egyetlen adatkészlet jelentésenként |
| Szűrés |Nem lehet szűrni és szeletelni |Számos szűrési, kiemelési és szeletelési móddal rendelkezik |
| Riasztások beállítása |Létrehozhat olyan riasztásokat, amelyek e-mailen keresztül értesítik, ha a feltételek teljesülnek |Nem |
| Kiemelés |Kiválaszthat és beállíthat egy „kiemelt” irányítópultot |Nem hozhat létre kiemelt jelentést |
| Láthatja az alapul szolgáló adatkészlet-táblázatokat és -mezőket |Nem. Is exportálhat adatokat, de nem láthatják az adatkészlet-táblázatokat és a mezők magán az irányítópulton. |Igen. Adatkészlet-táblázatokat és mezők és értékek megtekintéséhez engedélyekkel rendelkező látható. |
| Testreszabás |Nem  |Is szűrheti, exportálása, kapcsolódó tartalom megtekintése, a Könyvjelzők hozzáadása, QR-kódokat generálhat, elemzés az Excelben és más.   |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-creators-and-report-consumers"></a>Jelentések ***létrehozói*** és ***felhasználói***
A szerepkör függően előfordulhat, hogy lehet egy *designer*, személy, aki jelentéseket a saját használatra, illetve a munkatársakkal való megosztásáról hoz létre. Ez esetben a jelentések létrehozásáról és megosztásáról kell ismereteket szereznie. Vagy lehet olyan személy is, aki jelentéseket kap másoktól. Ez esetben azt kell tudnia, hogy hogyan értelmezheti és használhatja a jelentéseket. Ha egy jelentés **fogyasztói**, ezek a hivatkozások akkor az Ön számára. 

* Kezdje a [Power BI szolgáltatás áttekintésével](end-user-basic-concepts.md), melyből megtudhatja, hol találhatja meg a jelentéseket és a jelentéseszközöket.
* Ismerje meg, hogyan tud [megnyitni egy jelentést](end-user-report-open.md), és fedezze fel az [Olvasó nézetben](end-user-reading-view.md) elérhető műveleteket.
* Gyakorolja a jelentések használatát az egyik [mintánk](../sample-tutorial-connect-to-the-samples.md) segítségével.  
<!--* Don't need the report any more? You can [remove it](../service-delete.md).-->
* Ha szeretné megtudni, milyen adatkészletet használ egy jelentés, és mely irányítópultok tartalmaznak rögzített csempéket a jelentésből, [tekintse meg a kapcsolódó tartalmat](end-user-related.md).

> [!TIP]
> Ha nem találta meg itt, amit keres, a bal oldali tartalomjegyzékben elérheti a *jelentések* témaköreinek teljes listáját.
> 
> 

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](../power-bi-overview.md) 

[Power BI – Alapfogalmak](end-user-basic-concepts.md)

