---
title: Adatfolyamok meghirdetése és minősítése (előzetes verzió)
description: További információ az adatfolyamok meghirdetéséről és minősítéséről.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/17/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 7634711e8d26c4f265752427c5086e0901b210d5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81268880"
---
# <a name="promote-or-certify-dataflows-preview"></a>Adatfolyamok meghirdetése és minősítése (előzetes verzió)

A Power BI-ban kétféleképpen, a **meghirdetés** és a **minősítés** módszerével hívhatja fel a figyelmet az értékes és kiváló minőségű adatfolyamokra.

* **Meghirdetés**: A meghirdetéssel a felhasználó kiemelheti az értékes és mások számára hasznosnak ítélt adatfolyamokat. Ezzel elősegítheti az adatfolyamok együttműködő terjesztését a cégen belül. Az adatfolyam-tulajdonosok és az adatfolyamot tartalmazó munkaterület írási jogosultsággal rendelkező tagjai egyszerűen hirdethetik meg a megosztásra érdemesnek ítélt adatfolyamokat.

* **Minősítés**: A minősítés azt jelenti, hogy az adatfolyam átesett egy hitelesített felülvizsgáló ellenőrzésén, tehát a teljes cégen belül használható, megbízható, mérvadó adatforrás. A Power BI bérlői rendszergazdája által kijelölt felülvizsgáló csoport dönt arról, hogy mely adatfolyamokat kell minősíteni. Ha egy felhasználó úgy véli, hogy egy adatfolyamot minősíteni kell, de ő maga nem jogosult a művelet elvégzésére, a bérlői rendszergazdához kell fordulnia.

  Az adatfolyam csak [a Power BI bérlői rendszergazdájának engedélyével](../admin/service-admin-setup-certification.md) minősíthető.

A adatfolyam meghirdetése vagy minősítése az úgynevezett *ajánlás*. A Power BI-jelentéskészítők gyakran számos adatfolyam közül választhatnak, így az ajánlások segíthetnek nekik megtalálni ezek között a megbízható és mérvadó adatfolyamokat.

Az ajánlott adatfolyamok egyértelmű címkével vannak ellátva a Power BI számos helyén, így a megbízható adatokat kereső jelentéskészítők könnyen megtalálhatják őket, a rendszergazdák és a jelentéskészítők pedig nyomon követhetik használatukat a cégen belül.

Az alábbi képen láthatók a könnyen azonosítható meghirdetett és minősített adatfolyamok a Power Queryben.

![Ajánlott adatfolyamok kiemelése a Power Queryben](media/service-dataflows-promote-certify/powerbi-dataflow-endorsement-power-query.png)

Ez a cikk a következőket ismerteti:
* Adatfolyam meghirdetése (adatfolyam-tulajdonos, vagy bármely felhasználó, akinek tagengedélye van az adatfolyamot tartalmazó munkaterületen)
* Adatfolyam minősítése (bérlői rendszergazda által kijelölt, jogosult adatfolyam-minősítő)

Az adatfolyam-minősítés (bérlői rendszergazda által végzett) beállításához lásd: [Adatkészlet és adatfolyam minősítésének beállítása](../admin/service-admin-setup-certification.md)


## <a name="promote-a-dataflow"></a>Adatfolyam meghirdetése

Egy adatfolyam meghirdetéséhez írási engedélyekkel kell rendelkeznie arra a munkaterületre vonatkozóan, ahol a meghirdetni kívánt adatfolyam található.

1. Nyissa meg az adatfolyamok listáját a munkaterületen.
 
1. A meghirdetni kívánt adatfolyamnál válassza a **További beállítások** (...) lehetőséget, majd válassza a **Beállítások**lehetőséget.

    ![Az adatfolyam melletti három pont kiválasztása](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Bontsa ki az ajánlás szakaszt, és válassza a **Meghirdetve** lehetőséget.

    ![A Meghirdetve beállítás és az Alkalmaz lehetőség kiválasztása](media/service-dataflows-promote-certify/power-bi-dataflow-promoted-endorsement.png)

1. Kattintson az **Alkalmaz** elemre.

## <a name="certify-a-dataflow"></a>Adatfolyam minősítése

Ez a szakasz azon felhasználóknak szól, akik jogosultságot kaptak a bérlői rendszergazdától az adatfolyamok minősítésére. A adatfolyamok minősítése nagy felelősséggel jár. Ez a szakasz a minősítési folyamat lépéseit ismerteti.

1. Szerezzen be írási engedélyt azon a munkaterületen, ahol a minősíteni kívánt adatfolyam található. Ezt az engedélyt megadhatja az adatfolyam tulajdonosa, vagy a munkaterületen rendszergazdai jogosultságokkal rendelkező bármely felhasználó. 

1. Vizsgálja meg körültekintően az adatfolyamot, és döntse el, hogy érdemes-e a minősítésre.

1. Ha a minősítés mellett dönt, lépjen az adatfolyamot tartalmazó munkaterületre.
 
1. Keresse meg a kiválasztott adatfolyamot, kattintson a **További beállítások** (...) elemre, majd válassza a **Beállítások** lehetőséget.

    ![Az adathalmaz vagy adatfolyam melletti három pont kiválasztása](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Bontsa ki az ajánlás szakaszt, és válassza a **Minősítve** lehetőséget. 

    ![Kattintson a További információ hivatkozásra.](media/service-dataflows-promote-certify/service-certify-datasets-dataflows.png)

2. Kattintson az **Alkalmaz** gombra.

## <a name="next-steps"></a>Következő lépések

* [Adatkészlet és adatfolyam minősítésének beállítása](../admin/service-admin-setup-certification.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)