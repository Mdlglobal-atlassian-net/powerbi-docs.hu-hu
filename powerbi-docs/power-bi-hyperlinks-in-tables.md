---
title: Hivatkozások táblázathoz adása
description: A Power BI Desktop használatával hivatkozásokat hozhat létre. Ezeket a hivatkozásokat aztán a Power BI Desktop vagy a Power BI szolgáltatás segítségével adhatja hozzá a jelentések táblázataihoz és a mátrixokhoz.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 92224e00da95714125a8e15c27432e8d305ae0f7
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180553"
---
# <a name="add-hyperlinks-to-a-table"></a>Hivatkozások táblázathoz adása
Ez a témakör azt mutatja be, hogyan hozhatók létre hivatkozások a Power BI Desktopban. Ezeket a hivatkozásokat aztán a Power BI Desktop vagy a Power BI szolgáltatás segítségével adhatja hozzá a jelentések táblázataihoz és a mátrixokhoz. 

![Hivatkozásokat tartalmazó táblázat](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> Az [irányítópultok csempéin](service-dashboard-edit-tile.md) és az [irányítópultok szövegdobozain](service-dashboard-add-widget.md) lévő hivatkozásokat a Power BI szolgáltatással hozhatja létre menet közben. A [jelentések szövegdobozaiban](service-add-hyperlink-to-text-box.md) lévő hivatkozásokat a Power BI szolgáltatással és a Power BI Desktoppal is létrehozhatja menet közben.
> 
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Hivatkozás létrehozása táblázatban vagy mátrixban a Power BI Desktop segítségével
A táblázatokban és mátrixokban lévő hivatkozásokat csak a Power BI Desktoppal hozhatja létre, a Power BI szolgáltatással nem. A hivatkozásokat az Excel Power Pivotban is létrehozhatja, mielőtt a munkafüzeteket a Power BI-ba importálná. Az alábbiakban mindkét módszer leírása megtalálható.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Hivatkozás létrehozása táblázatban vagy mátrixban a Power BI Desktop használatával
A hivatkozás felvételének menete attól függ, hogy importálta az adatokat, vagy a DirectQuery segítségével csatlakozott hozzájuk. Az alábbiakban mindkét eset leírása megtalálható.

### <a name="for-data-imported-into-power-bi"></a>Power BI-ba importált adatok
1. Ha a hivatkozás még nem létezik mezőként az adatkészletben, vegye fel a Desktoppal [egyéni oszlopként](desktop-common-query-tasks.md).
2. Az Adatok nézetben válassza ki az oszlopot, és a **Modellezés** lapon válassza az **Adatkategória** legördülő menüt.
   
    ![Adatkategóriák legördülő listája](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Kattintson a **Webes URL-cím** lehetőségre.
4. Váltson Jelentés nézetre, majd hozzon létre egy táblázatot vagy mátrixot a Webes URL-cím kategóriába sorolt mező használatával. A hivatkozások kék színnel, aláhúzva jelennek meg.

    ![Kék, aláhúzott hivatkozások](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > Az URL-címeknek a **http://, a https://** vagy a **www** előtaggal kell kezdődniük.
    >
   
1. Ha nem szeretne hosszú URL-címet megjeleníteni a táblázatban, egy hivatkozásikont is megjeleníthet  ![Hivatkozásikon](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) helyette. Figyelem: a mátrixokban nem jeleníthet meg ikonokat.
   
   * A diagram aktiválásához kattintson a diagramra.
   * Válassza a festőhenger ikont ![Festőhenger ikon](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) a Formázás lap megnyitásához.
   * Bontsa ki az **Értékek** elemet, keresse meg az **URL-ikont**, és kapcsolja **Be**.
6. (Nem kötelező.) [A Desktopról származó jelentést közzéteheti a Power BI szolgáltatásban](guided-learning/publishingandsharing.yml?tutorial-step=2), és megnyithatja a Power BI szolgáltatáson belül. A hivatkozások itt is működni fognak.

### <a name="for-data-connected-with-directquery"></a>DirectQuery segítségével csatlakoztatott adatok
DirectQuery módban nem hozhat létre új oszlopot,  de az adatokban már meglévő URL-címeket átalakíthatja hivatkozásokká.

1. Jelentés nézetben hozzon létre egy táblázatot egy URL-címeket tartalmazó mezővel.
2. Jelölje ki az oszlopot, majd a **Modellezés** lapon válassza az **Adatkategória** legördülő menüt.
3. Kattintson a **Webes URL-cím** lehetőségre. A hivatkozások kék színnel, aláhúzva jelennek meg.
4. (Nem kötelező.) [A Desktopról származó jelentést közzéteheti a Power BI szolgáltatásban](guided-learning/publishingandsharing.yml?tutorial-step=2), és megnyithatja a Power BI szolgáltatáson belül. A hivatkozások itt is működni fognak.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Hivatkozás létrehozása táblázatban vagy mátrixban az Excel Power Pivot használatával
A Power BI táblázataihoz és mátrixaihoz úgy is hozzáadhatja a hivatkozásokat, hogy még azelőtt létrehozza őket az adatkészletben, hogy az adatkészletet importálná vagy csatlakoztatná a Power BI-ban. Ez a példa egy Excel-munkafüzetet használ.

1. Nyissa meg a munkafüzetet az Excelben.
2. Kattintson a **PowerPivot** lapra, majd a **Kezelés** elemre.
   
   ![A PowerPivot megnyitása az Excelben](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Amikor megnyílik a PowerPivot, kattintson a **Speciális** fülre.
   
   ![A PowerPivot Speciális lapja](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Vigye a kurzort arra az oszlopra, amely azokat az URL-címeket tartalmazza, amelyeket hivatkozásokká szeretne alakítani a Power BI tábláiban.
   
   > [!NOTE]
   > Az URL-címeknek a **http://, a https://** vagy a **www** előtaggal kell kezdődniük.
   > 
5. A **Jelentéskészítési tulajdonságok** csoportban válassza az **Adatkategória** legördülő menüt, és kattintson a **Webes URL-cím** elemre. 
   
   ![Adatkategóriák legördülő listája az Excelben](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Csatlakozzon a munkafüzethez a Power BI szolgáltatásból vagy a Power BI Desktopról, vagy importálja a munkafüzetet.
7. Hozzon létre egy táblázatvizualizációt, amely tartalmazza az URL-mezőt.
   
   ![Táblázat létrehozása a Power BI-ban az URL-cím mezővel](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
KÉRDÉS: Használhatok hivatkozásként egyéni URL-t a táblázatokban és a mátrixokban?    
VÁLASZ: Nem. Csak hivatkozás ikont lehet használni. Ha a hivatkozáshoz egyéni szöveget szeretne használni, és túl kevés URL van a listán, érdemes lehet szövegmezőt használni inkább.


## <a name="next-steps"></a>Következő lépések
[Vizualizációk a Power BI jelentéseiben](visuals/power-bi-report-visualizations.md)

[Power BI – Alapfogalmak](consumer/end-user-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

