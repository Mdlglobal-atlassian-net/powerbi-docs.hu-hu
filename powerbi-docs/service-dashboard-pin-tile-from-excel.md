---
title: Csempe rögzítése Power BI-irányítópultra Excelből
description: Csempe rögzítése Power BI-irányítópultra a OneDrive Vállalati verziós Excelből. Tartományok, diagramok és táblázatok rögzítése
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: l8JoB7w0zJA
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: d0f258af383327fb25c8f0e896677bbd19eca6c4
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877430"
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-excel"></a>Csempe rögzítése Power BI-irányítópultra Excelből
Mielőtt egy Excel-munkafüzet csempéjét rögzítené, csatlakoztatnia kell a munkafüzetet a Power BI szolgáltatáshoz (app.powerbi.com). A munkafüzet csatlakoztatásával lényegében a munkafüzet egy csak olvasható példányát nyitja meg a Power BI szolgáltatásban, így tartományokat rögzíthet az irányítópultokon. Akár egy teljes munkalapot is rögzíthet az irányítópulton.  
Ha megosztottak Önnel egy munkafüzetet, megtekintheti a tulajdonos által rögzített csempéket, saját csempéket azonban nem hozhat létre az irányítópulton. 

Részletes információ az Excel és a Power BI együttműködéséről: [Adatok lekérdezése Excel-munkafüzetből](https://go.microsoft.com/fwlink/?LinkID=521962).

Will bemutatja az Excel-munkafüzetekből való adatimportálás és a munkafüzetekhez való csatlakozás módjait.

<iframe width="560" height="315" src="https://www.youtube.com/embed/l8JoB7w0zJA" frameborder="0" allowfullscreen></iframe>

## <a name="connect-your-excel-workbook-from-onedrive-for-business-to-power-bi"></a>Excel-munkafüzet csatlakoztatása a Power BI-hoz a OneDrive Vállalati verzióból
A **Csatlakozás** lehetőséget választva a munkafüzet megjelenik a Power BI felületén, ahogyan az megjelenne az Excel Online-ban. Az Excel Online-nal ellentétben azonban ebben az esetben néhány kiváló funkció segítségével rögzítheti a munkalapok egyes elemeit közvetlenül az irányítópulton.

A Power BI-ban nincs lehetőség a munkafüzet szerkesztésére. Azonban ha néhány módosítást szeretne elvégezni, válassza a ceruza ikont a munkaterület **Munkafüzetek** lapján, majd szerkessze a munkafüzetet az Excel Online-ban, vagy nyissa meg a számtógépén az Excelben. A módosításai a OneDrive-on található munkafüzetbe lesznek mentve.

1. Töltse fel a munkafüzetet a OneDrive Vállalati verzióba.

2. [Kapcsolódjon ehhez a munkafüzethez](service-excel-workbook-files.md) a Power BI-ban az **Adatok lekérése > Fájlok > OneDrive – Vállalati** lehetőség választásával és a mentett Excel-fájl megkeresésével. Válassza ki a fájlt, majd válassza a **Kapcsolódás > Kapcsolódás** lehetőséget.

    ![OneDrive Vállalati verzió párbeszédpanel](media/service-dashboard-pin-tile-from-excel/power-bi-connect.png)

3. A Power BI felületén a munkafüzet a munkaterület **Munkafüzetek** lapján jelenik meg.  Az ![munkafüzet ikon](media/service-dashboard-pin-tile-from-excel/pbi_workbookicon.png) ikon azt jelzi, hogy ez egy Excel-munkafüzet, a sárga csillag pedig arra utal, hogy új.
    
    ![munkafüzetek lap](media/service-dashboard-pin-tile-from-excel/power-bi-workbooks.png)
4. Nyissa meg a munkafüzetet a Power BI-ban. Ehhez kattintson a munkafüzet nevére.

    A munkafüzeten a Power BI-ban végzett módosításokat nem menti a rendszer, és nem jelennek meg OneDrive Vállalati verziós eredeti munkafüzetben. Ha rendszerezi, szűri vagy módosítja az adatokat a Power BI felületén, a módosításokat nem mentheti és nem rögzítheti. Ha mentendő változtatásokat szeretne végezni, válassza a jobb felső sarokban található **Szerkesztés** elemet, majd nyissa meg és szerkessze az Excel Online-ban vagy az Excelben. Az így végzett módosítások néhány percen belül megjelennek az irányítópult csempéin.
   
    ![Az Excel Online a Power BI-ban](media/service-dashboard-pin-tile-from-excel/power-bi-opened.png)

## <a name="pin-a-range-of-cells-to-a-dashboard"></a>Cellatartomány rögzítése egy irányítópulton
Ha egy új [irányítópult-csempét](consumer/end-user-tiles.md) szeretne hozzáadni, egyik módszerként ezt megteheti egy Power BI-ban megnyitott Excel-munkafüzetből. Tartományokat olyan Excel-munkafüzetekből rögzíthet, amelyeket a OneDrive Vállalati verzióban vagy más, csoportmegosztású dokumentumtárban mentett. A tartományok tartalmazhatnak adatokat, diagramokat, táblázatokat, kimutatásokat, kimutatásdiagramokat és egyéb Excel-elemeket.

1. Jelölje ki a rögzíteni kívánt cellákat.
   
    ![cellák kijelölése az Excel-munkafüzetben](media/service-dashboard-pin-tile-from-excel/pbi_selectrange.png)
2. Válassza a gombostű ![gombostű ikon](media/service-dashboard-pin-tile-from-excel/pbi_pintile_small.png) ikonra. 
3. Tűzze ki a csempét egy meglévő vagy egy új irányítópultra. 
   
   * Meglévő irányítópult: válassza ki az irányítópult nevét a legördülő listából.
   * Új irányítópult: írja be az új irányítópult nevét.
   
     ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-pin-tile-from-excel/pbi_dashdialog1.png)
4. Kattintson a **Rögzítés** elemre. Miután sikeresen hozzáadta a tartományt csempeként az irányítópulthoz, a jobb felső sarokban megjelenik egy üzenet, amely tudatja Önt erről. 
   
    ![Rögzítve az irányítópulton párbeszédablak](media/service-dashboard-pin-tile-from-excel/power-bi-go-to-dashboard.png)
5. Válassza az **Ugrás az irányítópultra** lehetőséget. Itt [átnevezheti, átméretezheti, csatlakoztathatja és áthelyezheti](service-dashboard-edit-tile.md) a rögzített vizualizációt. Alapértelmezés szerint a rögzített csempe a Power BI-ban nyitja meg a munkafüzetet.

## <a name="pin-an-entire-table-or-pivottable-to-a-dashboard"></a>Teljes táblázat vagy Kimutatás rögzítése egy irányítópulton
Kövesse a fenti lépéseket, azonban a cellatartomány helyett jelölje ki a teljes táblázatot vagy Kimutatást.

Egy táblázat rögzítéséhez jelölje ki annak teljes tartományát, és ügyeljen rá, hogy a fejlécek sem maradjanak ki.  Kimutatás rögzítésénél annak minden látható elemét jelölje ki, beleértve az esetleges szűrőket is.

 ![cellák kiválasztása](media/service-dashboard-pin-tile-from-excel/pbi_selecttable.png)

A táblázatokból vagy Kimutatásokból létrehozott csempék a teljes táblázatot megjelenítik.  Ha az eredeti munkafüzetben hozzáad, eltávolít vagy szűr egyes sorokat vagy oszlopokat, azokat a csempéhez is hozzáadja, illetve onnan is eltávolítja vagy szűri.

## <a name="view-the-workbook-linked-to-the-tile"></a>A csempéhez csatolt munkafüzet megtekintése
Ha egy munkafüzet csempéjére kattint, a csatolt munkafüzet a Power BI-ban nyílik meg. Mivel a munkafüzet a tulajdonos OneDrive Vállalati verziójában található, annak megtekintéséhez olvasási engedéllyel kell rendelkeznie. Ha nincs engedélye, hibaüzenet jelenik meg.  

 ![videó](media/service-dashboard-pin-tile-from-excel/pin-from-excel.gif)

## <a name="considerations-and-troubleshooting"></a>Szempontok és hibaelhárítás
Nem támogatott funkciók: a Power BI az Excel Services szolgáltatással kéri le a munkafüzet csempéit. Ennek következtében, mivel az Excel néhány funkciója nem támogatott az Excel Services REST API-ban, ezek a funkciók nem jelennek meg a Power BI-csempéken. Ilyen funkciók például az értékgörbék, az ikonkészletek feltételes formázása és az időszeletelők. A nem támogatott funkciók teljes listája: [Az Excel Services REST API nem támogatott funkciói](https://msdn.microsoft.com/library/office/ff394477.aspx)

## <a name="next-steps"></a>További lépések
[Egy Excel-munkafüzethez csatolt irányítópult megosztása](service-share-dashboard-that-links-to-excel-onedrive.md)

[Adatok lekérdezése Excel-munkafüzetekből](service-excel-workbook-files.md)

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

