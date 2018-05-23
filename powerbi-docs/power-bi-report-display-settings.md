---
title: Jelentések oldalmegjelenítési és oldalnézet-beállításai
description: Jelentések oldalmegjelenítési és oldalnézet-beállításai
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/24/2017
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: af90ba6bcf85c07d2d046ed21f733ca7c16e3856
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2018
---
# <a name="page-display-settings-in-a-power-bi-report"></a>Oldal megjelenítési beállításai Power BI-jelentésben
Tudjuk, milyen fontos, hogy a jelentéseinek elrendezése az utolsó pixelig tökéletes legyen. Néha azonban ez kihívást jelenthet, ugyanis Ön és a munkatársai a jelentéseket különböző méretű és méretarányú képernyőkön nézik. 

Az alapértelmezett megjelenítési nézet a **Laphoz igazítás**, az alapértelmezett méretarány pedig a **16:9**-es. Ha a jelentést egy másik méretarányban szeretné zárolni, vagy máshogyan szeretné igazítani, akkor ehhez két eszköz áll rendelkezésére: az ***Oldal nézet*** beállításai és az ***Oldalméret***-beállítások.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-power-bi-service-and-power-bi-desktop"></a>Az oldalnézet-beállítások helye a Power BI szolgáltatásban és a Power BI Desktopban
Az oldalnézet-beállítások a Power BI szolgáltatásban és a Power BI Desktopban is elérhetők, de a felület kismértékben eltér. Az alábbi két szakasz azt ismerteti, hogy hol találhatja meg a Nézet beállításait az egyes Power BI-eszközökben.

### <a name="in-power-bi-desktop"></a>A Power BI Desktopban
A Jelentés nézetben a **Nézet** lapot választva nyithatja meg az oldalnézet-beállításokat, illetve a telefonos elrendezés beállításait.

  ![Kiválasztás panel](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-power-bi-service-apppowerbicom"></a>A Power BI szolgáltatásban (az app.powerbi.com webhelyen)
A Power BI szolgáltatásban nyisson meg egy jelentést, majd válassza a **Nézet** lehetőséget a bal felső menüsorban.

![](media/power-bi-report-display-settings/power-bi-change-page-view.png)

Az oldal nézetének beállításai az [Olvasó nézetből és a Szerkesztő nézetből](service-reading-view-and-editing-view.md) is elérhetők. A jelentés tulajdonosa a Szerkesztési nézetben az egyes jelentésoldalakhoz különböző oldalnézetek-beállításokat rendelhet, melyeket a jelentéssel együtt ment a rendszer. Ha a munkatársak Olvasó nézetben nyitnak meg egy jelentést, akkor a jelentésoldalakat a tulajdonos beállításainak megfelelően fogják látni.  Olvasási nézetben a munkatársak *néhányat* módosíthatnak az oldalnézet beállításai közül, de a rendszer nem menti a módosításokat, amikor kilépnek a jelentésből.

##    <a name="page-view-settings"></a>Oldalnézet beállításai
Az *Oldalnézet* beállításainak első készlete a jelentésoldal megjelenítését a böngésző ablakához viszonyítva szabályozza.  Az alábbiak közül választhat:

* **Laphoz igazítás** (alapértelmezett): a tartalmak úgy vannak méretezve, hogy a legjobban igazodjanak a laphoz.
* **Szélességhez igazítás**: a tartalmak úgy vannak méretezve, hogy a lap szélességéhez igazodjanak.
* **Tényleges méret**: a tartalmak teljes méretükben jelennek meg.

Az *Oldalnézet* beállításainak második készlete az objektumok a jelentésvásznon való elhelyezését szabályozza

* **Rácsvonalak megjelenítése**: rácsvonalak bekapcsolása az objektumok a jelentésvásznon való elhelyezésének segítése érdekében
* **Rácshoz illesztés**: a **Rácsvonalak megjelenítése** beállítással együtt használva pontosan helyezheti el és igazíthatja az objektumokat a jelentésvásznon 
* **Objektumok zárolása**: minden objektum zárolása a vásznon, hogy azokat ne lehessen áthelyezni vagy átméretezni
* **Kiválasztás panel**: a Kiválasztás panelen a vásznon levő összes objektum fel van sorolva, és meghatározhatja, hogy melyik jelenjen meg és melyik legyen elrejtve

    ![Kiválasztás panel](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Oldalméret-beállítások
![](media/power-bi-report-display-settings/power-bi--page-size.png)

Az *Oldalméret* beállításai csak a jelentések tulajdonosai számára érhetők el. A Power BI szolgáltatásban (az app.powerbi.com webhelyen) ehhez meg kell tudni nyitni a jelentést a [Szerkesztési nézetben](service-reading-view-and-editing-view.md). Ezek a beállítások a jelentésvászon méretarányát és a (pixelben megadott) tényleges méretét határozzák meg.   

* 4:3-as arány
* 16:9-es arány (alapértelmezett)
* Cortana
* Letter
* Egyéni (magasság és szélesség pixelben)

## <a name="next-steps"></a>Következő lépések
[Tudnivalók az Oldalnézet-beállítások és az Oldalméret-beállítások saját Power BI-jelentésekben való használatáról](power-bi-change-report-display-settings.md).

További tudnivaló a [Power BI-jelentésekről](service-reports.md)

[Power BI – Alapfogalmak](service-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

