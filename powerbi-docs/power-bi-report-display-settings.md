---
title: Oldal megjelenítési beállításai Power BI-jelentésben
description: Jelentések oldalmegjelenítési és oldalnézet-beállításai
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 6aefe879e6d5871c8f88ac15407038aa600bf980
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762508"
---
# <a name="apply-page-display-settings-in-a-power-bi-report"></a>Oldalmegjelenítési beállítások alkalmazása egy Power BI-jelentésben
Tudjuk, milyen fontos, hogy jelentéseinek elrendezése az utolsó képpontig tökéletes legyen. Ez azonban olykor kihívást jelenthet, ugyanis Ön és a munkatársai a jelentéseket esetleg különböző méretű és méretarányú képernyőkön tekintik meg. 

Az alapértelmezett megjelenítési nézet a **Laphoz igazítás**, az alapértelmezett méretarány pedig a **16:9**-es. Ha a jelentést egy másik méretarányban szeretné zárolni, vagy máshogyan szeretné igazítani, akkor ehhez két eszköz áll rendelkezésére: Az ***Oldal nézet*** beállításai és az ***Oldalméret***-beállítások.


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>Az oldalnézet-beállítások helye a Power BI szolgáltatásban és a Power BI Desktopban
Az oldalnézet-beállítások a Power BI szolgáltatásban és a Power BI Desktopban is elérhetők, de a felület kismértékben eltér. Az alábbi szakaszok azt ismertetik, hogy hol találhatja meg a Nézet beállításait az egyes Power BI-eszközökben.

### <a name="in-power-bi-desktop"></a>A Power BI Desktopban
A Jelentés nézetben a **Nézet** lapot választva nyithatja meg az oldalnézet-beállításokat, illetve a telefonos elrendezés beállításait.

  ![Oldalnézet beállításai a Desktopban](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>A Power BI szolgáltatásban (app.powerbi.com)
A Power BI szolgáltatásban nyisson meg egy jelentést, majd válassza a **Nézet** lehetőséget a bal felső menüsorban.

![Oldalnézet beállításai a szolgáltatásban](media/power-bi-report-display-settings/power-bi-change-page-view.png)

Az oldal nézetének beállításai az [Olvasó nézetből és a Szerkesztő nézetből](consumer/end-user-reading-view.md) is elérhetők. A jelentés tulajdonosa a Szerkesztési nézetben az egyes jelentésoldalakhoz különböző oldalnézetek-beállításokat rendelhet, melyeket a jelentéssel együtt ment a rendszer. Ha a munkatársak Olvasó nézetben nyitnak meg egy jelentést, akkor a jelentésoldalakat a tulajdonos beállításainak megfelelően fogják látni. Olvasási nézetben a munkatársak *néhányat* módosíthatnak az **Oldalnézet** beállításai közül, de a rendszer nem menti a módosításokat, amikor kilépnek a jelentésből.

## <a name="page-view-settings"></a>Oldalnézet beállításai
Az Oldalnézet beállításainak első készlete a jelentésoldal megjelenítését a böngésző ablakához viszonyítva szabályozza. Az alábbiak közül választhat:

* **Laphoz igazítás** (alapértelmezés): A tartalmak úgy vannak méretezve, hogy a legjobban igazodjanak a laphoz
* **Szélességhez igazítás**: A tartalmak úgy vannak méretezve, hogy a lap szélességéhez igazodjanak
* **Tényleges méret**: A tartalmak teljes méretükben jelennek meg

Az Oldalnézet beállításainak második része az objektumok a jelentésvásznon való elhelyezését szabályozza. Az alábbiak közül választhat:

* **Rácsvonalak megjelenítése**: Rácsvonalak bekapcsolása az objektumok a jelentésvásznon való elhelyezésének segítése érdekében.
* **Rácshoz illesztés**: A **Rácsvonalak megjelenítése** beállítással együtt használva pontosan helyezheti el és igazíthatja az objektumokat a jelentésvásznon. 
* **Objektumok zárolása**: Minden objektum zárolása a vásznon, hogy azokat ne lehessen áthelyezni vagy átméretezni.
* **Kijelölés panel**: A **Kijelölés** panel a vásznon lévő összes objektumot kilistázza. Ön döntheti el, hogy melyek jelenjenek meg, és melyek legyenek elrejtve.

    ![Kiválasztás panel](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Oldalméret-beállítások
![oldalméret-beállítások módosítása](media/power-bi-report-display-settings/power-bi-page-size.png)

Az **Oldalméret** beállításai csak a jelentések tulajdonosai számára érhetők el. A Power BI szolgáltatásban (az app.powerbi.com webhelyen) ehhez meg kell tudni nyitni a jelentést a [Szerkesztési nézetben](consumer/end-user-reading-view.md). A **Vizualizációk** panelen található **Oldalméret** beállítások a jelentésvászon méretarányát és a (képpontokban megadott) tényleges méretét határozzák meg:   

* 4:3-as arány
* 16:9-es arány (alapértelmezett)
* Letter
* Egyéni (magasság és szélesség pixelben)

## <a name="next-steps"></a>Következő lépések
[Jelentés nézet a Power BI Desktopban](desktop-report-view.md)

[Az Oldalnézet-beállítások és az Oldalméret-beállítások módosítása saját Power BI-jelentésekben](consumer/end-user-report-view.md)

A [Power BI jelentéseiről itt talál](consumer/end-user-reports.md) további információkat

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

