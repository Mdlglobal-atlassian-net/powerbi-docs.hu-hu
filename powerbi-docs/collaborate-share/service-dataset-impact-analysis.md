---
title: Adatkészletek hatáselemzése
description: Megjelenítheti és elemezheti az adathalmazok módosításának alsóbb rétegbeli következményeit.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/13/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: d6d62583d6ef6bd1fcc1630b46bdb5d97c221f16
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525330"
---
# <a name="dataset-impact-analysis"></a>Adatkészletek hatáselemzése

Amikor módosít egy adathalmazt, vagy változtatásokat fontolgat, fontos, hogy fel tudja mérni, milyen hatásai lesznek ezeknek a változtatásoknak az erre az adathalmazra támaszkodó alsóbb rétegbeli jelentésekben és irányítópultokban. Az **Adathalmazok hatáselemzése** olyan információkat biztosít, amelyek segítenek felmérni ezeket a hatásokat.
* A funkció megmutatja, hány munkaterületet, jelentést és irányítópultot érint az adott változtatás, és lehetővé teszi, hogy a behatóbb vizsgálat érdekében könnyedén odanavigálhasson azokhoz a munkaterületekhez, amelyek az érintett jelentéseket és irányítópultokat tartalmazzák.
* Azt is megjeleníti, hány egyedi megtekintőt és hány megtekintést rögzített a rendszer a potenciálisan érintett elemeknél. Ez segít meghatározni a változtatások alsóbb rétegbeli elemeket érintő általános hatását. Például valószínűleg sokkal fontosabb, hogy megvizsgáljuk egy olyan jelentés megváltoztatásának a hatásait, amelynek 20 000 egyedi megtekintője van, mint egy olyannak, amelynek mindössze három.
* A szolgáltatás azt is lehetővé teszi, hogy könnyedén értesíthesse az érintett felhasználókat a végrehajtott vagy tervezett változtatásokról.

Az Adathalmazok hatáselemzése könnyedén elindítható az [adatéletút nézetből](service-data-lineage.md).

## <a name="identifying-shared-datasets"></a>Megosztott adathalmazok azonosítása

Az adathalmazok hatáselemzését megosztott és nem megosztott adathalmazokon egyaránt elvégezheti. Azonban a funkció különösen az egyszerre több munkaterületeken is megosztott adathalmazok esetében hasznos, hiszen ezeknél sokkal nehezebb tisztán látni az alsóbb rétegbeli függőségeket, mint az olyan nem megosztott adathalmazoknál, amelyeknek függőségei ugyanazon a munkaterületen találhatók, mint az maga adathalmaz.

Az adatéletút nézetben a megosztott és nem megosztott adathalmazokat az adathalmaz kártyájának bal felső sarkában látható ikon alapján különböztetheti meg.

![A megosztott és nem megosztott adathalmazok ikonjai](media/service-dataset-impact-analysis/shared-unshared-icon.png)

## <a name="perform-dataset-impact-analysis"></a>Az adathalmazok hatáselemzésének folyamata

A munkaterület bármely adathalmazán végezhet hatáselemzést, függetlenül attól, hogy az meg van-e osztva mással. Viszont nem végezhető hatáselemzés azokon az adathalmazokon, amelyek bár láthatóak az adatéletút nézetben, de más munkaterülethez tartoznak. Ahhoz, hogy külső adathalmazokon végezzen hatáselemzést, előbb a forrás-munkaterületre kell navigálnia.

Az adathalmaz hatáselemzésének indításához kattintson a Hatáselemzés gombra az adathalmazhoz tartozó kártyán.

![Adathalmaz hatáselemzése gomb](media/service-dataset-impact-analysis/open-analysis-pane-button.png)

Megnyílik a Hatáselemzés oldalsó panelje.

![Adathalmaz hatáselemzésének oldalsó panelje](media/service-dataset-impact-analysis/service-impact-analysis-pane.png)

* A **hatás összegzésében** megtekintheti a potenciálisan érintett munkaterületek, jelentések és irányítópultok számát, valamint az adathalmazhoz kapcsolódó alsóbb rétegbeli jelentésekre és irányítópultokra vonatkozó összes megtekintésének számát.
* A **Partnerek értesítése** hivatkozás egy párbeszédpanelt nyit meg, ahol létrehozhatja és elküldheti az érintett munkaterületek partnerlistáján található személyeknek az adathalmaz változtatásait összefoglaló üzenetét. 
* A **tételes használati adatok** között megtekintheti, hogy az egyes munkaterületek esetében a munkaterülethez tartozó potenciálisan érintett jelentéseknek és irányítópultoknak összesen hány megtekintése van, és hogy az egyes jelentéseknek és irányítópultoknak hány megtekintője és megtekintése van, ahol:
   * A megtekintők: A jelentést vagy irányítópultot megtekintő különböző felhasználók számát jelöli.
   * A megtekintések: Azt jelöli, összesen hányszor tekintették meg a jelentést vagy irányítópultot

A használati metrikák az elmúlt 30 napra vonatkoznak, és az aktuális nap adatait nem tartalmazzák. Az adat tartalmazza a kapcsolódó alkalmazásokon keresztüli használat adatait is. A metrikák segítségével megismerheti az adathalmazok használatát az egész bérlőben, és felmérheti az adathalmaz módosításának lehetséges hatásait.

## <a name="notify-contacts"></a>Felhasználók értesítése

Ha módosított egy adathalmazt, vagy változtatáson gondolkodik, érdemes lehet kapcsolatba lépni az érintett felhasználókkal, hogy a változtatásról őket is tájékoztassa. A felhasználók értesítésekor a rendszer e-mailt küld minden olyan felhasználónak, aki szerepel az érintett munkaterületek [partnerlistáján](../service-create-the-new-workspaces.md#workspace-contact-list). Az e-mail az Ön nevét is tartalmazza, így a felhasználók könnyedén megtalálhatják, és válaszolhatnak egy új e-mail-beszélgetésben. 

1. Kattintson a **Felhasználók értesítése** hivatkozásra a Hatáselemzés oldalsó paneljében. Ekkor megjelenik a Felhasználók értesítése párbeszédpanel.

   ![Felhasználók értesítése párbeszédpanel](media/service-dataset-impact-analysis/notify-contacts-dialog.png)

1. A szövegmezőbe írja be a módosítással kapcsolatos részleteket.
1. Ha elkészült az üzenettel, kattintson a **Küldés**gombra.

> [!NOTE]
> A felhasználók értesítésének funkciója nem érhető el, ha az érintett adathalmaz egy klasszikus munkaterülethez tartozik.

## <a name="privacy"></a>Adatvédelem

Az adathalmazok hatáselemzésének elvégzéséhez írási jogosultsággal kell rendelkeznie az adott adathalmazra vonatkozóan. A hatáselemzési panelen csak azok a munkaterületek, jelentések és irányítópultok valós nevei jelennek meg, amelyekhez rendelkezik hozzáféréssel. Azok az elemek, amelyekhez nincs hozzáférése, **Korlátozott hozzáférés** címkével jelennek meg. Ennek az az oka, hogy egyes elemek nevei személyes adatokat is tartalmazhatnak.

Még ha nincs hozzáférése bizonyos munkaterületekhez, akkor is megtekintheti a munkaterületek összesített használati metrikáit, és értesítési üzenetei ezen munkaterületek partnerlistáját is el fogják érni.

## <a name="impact-analysis-from-power-bi-desktop"></a>Hatáselemzés a Power BI Desktop használatával

Amikor módosít egy adathalmazt a Power BI Desktopban, majd azt újból közzéteszi a Power BI-szolgáltatásban, egy üzenet jelenik meg, amely megmutatja, hogy hány munkaterületet, jelentést és irányítópultot érint a változás, és arra fogja kérni, hogy erősítse meg, hogy a jelenleg közzétett adathalmazt a módosítottra kívánja cserélni. Az üzenet egy hivatkozást is tartalmaz, amellyel megnyithatja a Power BI szolgáltatás teljeskörű adathalmaz-hatáselemzési szolgáltatását, ahol további információkat tekinthet meg, és csökkentheti a változtatással kapcsolatos kockázatokat.

![Az adathalmaz-hatáselemzési üzenet a Power BI Desktopban](media/service-dataset-impact-analysis/service-dataset-impact-analysis-desktop-warning.png)

> [!NOTE]
> Az üzenetben megjelenő információk csak a lehetséges hatásokat jelzik – ez nem feltétlenül jelenti azt, hogy valóban hiba történt. Gyakran az adathalmazok változása nincs semmilyen káros hatással az alsóbb rétegbeli jelentésekre és irányítópultokra, az üzenet azonban ilyenkor is megjelenik, hogy Ön mindig tisztában lehessen a lehetséges hatásokkal.
>
>Az üzenetben a munkaterületek száma csak akkor jelenik meg, ha egynél több munkaterület jelentéseit és irányítópultjait is érintik a változtatások.

## <a name="limitations"></a>Korlátozások

* A használati metrikák a klasszikus és a személyes munkaterületek esetében jelenleg nem támogatottak.

## <a name="next-steps"></a>Következő lépések

* [Adathalmazok használata több munkaterületen (előzetes verzió)](../service-datasets-across-workspaces.md)
* [Adatéletút](service-data-lineage.md)
