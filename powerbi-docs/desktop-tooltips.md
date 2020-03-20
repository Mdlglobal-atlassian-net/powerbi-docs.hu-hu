---
title: Elemleírás-oldalak használata Power BI-jelentésekben
description: A Power BI Desktop elemleírás-oldalaival tartalomban gazdag elemleírások hozhatók létre a jelentésekben használt vizualizációkhoz
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/26/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 2492996c8bbc6ea7a8d359b4b1015de67bb17430
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378708"
---
# <a name="create-tooltips-based-on-report-pages-in-power-bi-desktop"></a>Elemleírások létrehozása jelentésoldalak alapján a Power BI Desktopban
A **Power BI Desktopban** létrehozott jelentésoldalak alapján sokatmondóan látványos **jelentés-elemleírásokat** készíthet, amelyek akkor jelennek meg, ha az egérmutató a vizualizáció felett van. Elemleírásként szolgáló jelentésoldal létrehozásakor az egyéni elemleírásokban vizualizációk, képek és a jelentésoldalon létrejött bármely más elemek gyűjteményei is szerepelhetnek. 

![Elemleírások Power BI Desktop-jelentésekhez](media/desktop-tooltips/desktop-tooltips_00a.png)

Tetszőleges számú elemleírás-oldalt létrehozhat. Minden elemleírás-oldal a jelentés egy vagy több mezőjéhez társítható, így ha az egérmutatót a kiválasztott mezőt tartalmazó vizualizáció fölé viszi, az elemleírás-oldalon létrehozott, az egérmutató alatti adatpont szerint szűrt elemleírás jelenik meg. 

A jelentések elemleírásainak számos felhasználási módja van. Tekintsük át az elemleírások létrehozását és a konfigurálásukhoz szükséges teendőket.

## <a name="create-a-report-tooltip-page"></a>Elemleírás-oldal létrehozása jelentéshez
Kiindulásként hozzon létre egy új jelentésoldalt a **Power BI Desktop**-vászon alján, a lapfülek sávjában található **+** gombra kattintva. A gomb a jelentés utolsó oldala mellett van. 

![Új jelentésoldal létrehozása elemleíráshoz](media/desktop-tooltips/desktop-tooltips_02.png)

Az elemleírás bármekkora lehet, de figyelembe kell venni, hogy a jelentésvászon előtt fog megjelenni, tehát érdemes ésszerűen kicsire méretezni. Az **Oldalméret** kártya **Formátum** paneljén megjelenik egy új, *Elemleírás* nevű méretsablon. Ez az elemleíráshoz alkalmas jelentésvászon-méretet biztosít.

![Az Elemleírás oldalméret kiválasztása előre elkészített elemleíráshoz](media/desktop-tooltips/desktop-tooltips_03.png)

A **Power BI Desktop** alapértelmezés szerint az oldalon rendelkezésre álló helyhez igazítja a jelentésvásznat. Ez többnyire megfelelő, elemleírások esetén viszont nem az. Jobban látható, hogy milyen lesz a kész elemleírás, ha az **Oldal nézet** a tényleges méretre van állítva. 

Ehhez válassza a menüszalag **Nézet** elemét. Ott a következő ábrán látható módon válassza az **Oldal nézet > Tényleges méret** elemet.

![Jelentésoldal megjelenítése tényleges méretben elemleírás egyszerű létrehozásához](media/desktop-tooltips/desktop-tooltips_04.png)

A jelentésoldalnak a rendeltetését egyértelműen leíró nevet is adhat. Válassza az **Oldal információi** kártyát a **Formátum** panelen, majd adja meg a nevet az ott található **Név** mezőben. A következő ábrán az elemleírásként szolgáló jelentés neve *Tooltip 1*, de bármilyen ötletes nevet megadhat.

![Elemleírásként szolgáló jelentésoldal elnevezése](media/desktop-tooltips/desktop-tooltips_05.png)

Innen kiindulva az elemleírásban megjeleníteni kívánt bármilyen vizualizációt létrehozhat. A következő ábrán két kártya és egy fürtözött sávdiagram látható az elemleírás-oldalon. Az oldal és az egyes vizualizációk háttérszíne is a kívánt megjelenésnek megfelelően van beállítva.

![Elemleírások Power BI Desktop-jelentésekhez](media/desktop-tooltips/desktop-tooltips_06.png)

Ahhoz, hogy az elemleírásnak szánt jelentésoldal elemleírásként használható legyen, szükség van még néhány további lépésre. Az elemleírás-oldalt több módon is konfigurálni kell a következő szakaszban leírtak alapján. 

## <a name="configure-your-tooltip-report-page"></a>Elemleírásként szolgáló jelentésoldal konfigurálása

Az elemleírásként szolgáló jelentésoldal létrehozása után az oldalt konfigurálni kell, hogy a **Power BI Desktop** elemleírásként ismerje fel, és hogy a megfelelő vizualizációk felett jelenjen meg.

Elsőként az **Elemleírás** kapcsolót kell **Be** állásba húzni az **Oldal információi** kártyán, hogy az oldal elemleírás legyen. 

![Oldal megjelölése elemleírásként az Elemleírás kapcsolóval](media/desktop-tooltips/desktop-tooltips_07.png)

A kapcsoló beállítása után megadhatja azokat a mezőket, amelyeknél az elemleírást meg kívánja jeleníteni. Az elemleírás azoknál a vizualizációknál fog megjelenni, amelyek tartalmazzák a megadott mezőt. A kívánt egy vagy több mezőt úgy adhatja meg, hogy a **Vizualizációk** panel **Mezők** oszlopában lévő **Elemleírás-mezők** gyűjtőbe húzza őket. A következő ábrán a *SalesAmount* mező van az **Elemleírás-mezők** gyűjtőbe húzva.

![Elemleírás megjelenési helyének meghatározása mezők megadásával](media/desktop-tooltips/desktop-tooltips_08.png)
 
Az **Elemleírás-mezők** gyűjtőben kategorikus és numerikus mezők, akár mértékek is elhelyezhetők.

Ha ez kész, akkor a létrehozott elemleírás-oldal az alapértelmezett Power BI-elemleírást helyettesítő elemleírásként lesz használva a jelentésnek az **Elemleírás-mezők** gyűjtőben megadott mezőket használó vizualizációihoz.

## <a name="manually-setting-a-report-tooltip"></a>Elemleírás manuális beállítása jelentéshez

A megadott mezőt tartalmazó vizualizáció fölé vitt egérmutatónál automatikusan megjelenő elemleírásokon kívül manuálisan is állíthat be elemleírásokat. 

A jelentés-elemleírásokat támogató vizualizációk **Formázás** paneljén már található egy **Elemleírás** kártya. 

Elemleírás manuális beállításához jelölje ki azt a vizualizációt, amelyhez manuális elemleírást kíván megadni, majd válassza a **Vizualizációk** panel **Formátum** szakaszát, és bontsa ki az **Elemleírás** kártyát.

![Elemleírás-kártya egyéni vizualizációhoz](media/desktop-tooltips/desktop-tooltips_09.png)

A **Lap** legördülő listából válassza ki az adott vizualizációhoz használni kívánt elemleírást. Fontos, hogy a párbeszédpanelen csak az **Elemleírás** tulajdonsággal megadott jelentésoldalak jelennek meg.

![Elemleírás-oldal kiválasztása manuális elemleírásként](media/desktop-tooltips/desktop-tooltips_10.png)

A manuálisan beállított elemleírások számos célra felhasználhatók. Beállíthat elemleírásként egy üres lapot, hogy felülírja az alapértelmezett Power BI-elemleírást. A manuáli elemleírások akkor is hasznosak, ha nem szeretné, hogy a Power BI által automatikusan kiválasztott elemleírás jelenjen meg. Ha egy vizualizáció például két mezőt tartalmaz, és mindkettőhöz tartozik elemleírás, akkor a Power BI csak az egyiket jeleníti meg. Lehetséges, hogy Ön nem ezt szeretné. Ilyenkor manuálisan kiválaszthatja a megjelenítendő elemleírást.

## <a name="reverting-to-default-tooltips"></a>Alapértelmezett elemleírások visszaállítása

Ha manuálisan hoz létre elemleírást egy vizualizációhoz, de mégis az alapértelmezett elemleírás használata mellett dönt, akkor bármikor visszatérhet a Power BI által biztosított alapértelmezett elemleíráshoz. Az alapértelmezés visszaállításához elég a kijelölt vizualizáció kibontott **Elemleírás** kártyájának **Lap** legördülő menüjéből az *Auto* lehetőséget megadni.

![Vizualizáció alapértelmezett elemleírásának visszaállítása](media/desktop-tooltips/desktop-tooltips_11.png)

## <a name="custom-report-tooltips-and-line-charts"></a>Egyéni jelentés-elemleírások vonaldiagramokhoz

Ha a jelentéshez készült elemleírás vonaldiagram típusú vagy keresztkiemelést használó vizualizációkhoz van kötve, akkor figyelembe kell venni néhány szempontot.

### <a name="report-tooltips-and-line-charts"></a>Jelentés-elemleírások vonaldiagramokhoz

Ha a jelentés elemleírása vonaldiagramhoz tartozik, akkor a diagram minden vonalához csak egy elemleírás jelenik meg. Ez a vonaldiagramok alapértelmezett elemleírásainak viselkedéséhez hasonló, ahol szintén csak egy elemleírás jelenik meg. 

Ennek az az oka, hogy jelmagyarázat mezője nem szűrőként van átadva az elemleírásnak. A következő ábrán látható elemleírás az adott napon a jelentésben ábrázolt három kategóriában (a példában Deluxe, Economy és Regular) értékesített egységeket mutatja be. 

![Vonaldiagramok elemleírásaiban csak összesített adatok jelennek meg](media/desktop-tooltips/desktop-tooltips_12.png)

### <a name="report-tooltips-and-cross-highlighting"></a>Jelentés-elemleírások keresztkiemeléssel

Ha egy jelentés vizualizációja keresztkiemeléssel készült, akkor a jelentés elemleírása mindig a keresztkiemelt adatokat mutatja még akkor is, ha az egérmutató az adatpont elhalványított része felett van. A következő ábrán az egér az oszlopdiagram elhalványított (nem kiemelt) részére mutat, az jelentés elemleírásában mégis az adatpont kiemelt részéhez tartozó adat jelenik meg.

![Keresztkiemelés esetén a jelentés elemleírása a kiemelt adatot mutatja](media/desktop-tooltips/desktop-tooltips_13.png)



## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
Az **elemleírásokra** vonatkozik néhány korlátozás és egyéb szempont.

* A **Power BI Desktop** 2018. decemberi kiadásától kezdve a gomb vizualizációk az elemleírásokat is támogatják.
* A jelentés-elemleírások Power BI-vizualizációkhoz nem támogatottak. 
* A fürtök mezőként történő megjelenítése a jelentésekhez készült elemleírásokban jelenleg nem támogatott. 
* Ha az elemleírásban megjeleníteni kívánt mező egy kategóriát helyettesít, akkor a mezőt tartalmazó vizualizációknál csak akkor jelenik meg az adott elemleírás, ha a kiválasztott mezők összegzése megegyezik. 



## <a name="next-steps"></a>Következő lépések
Az elemleírásokhoz hasonló vagy azokkal együtt használható funkciókkal kapcsolatos részletesebb információkat az alábbi cikkekben talál:

* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)
* [Irányítópult-csempe vagy jelentésvizualizáció megjelenítése Fókusz módban](consumer/end-user-focus.md)

