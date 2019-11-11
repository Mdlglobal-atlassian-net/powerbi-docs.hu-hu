---
title: Power BI-adatok feltárása Apple Watchra készült mobilalkalmazásban
description: Apple Watchra készült Power BI alkalmazás
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: mshenhav
ms.openlocfilehash: 31db6725c027ed09e900dac7036778004e9e3ff3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870733"
---
# <a name="explore-your-data-in-the-power-bi-mobile-app-on-your-apple-watch"></a>Adatok feltárása az Apple Watchra készült Power BI mobilalkalmazásban
Az Apple Watchra készült Power BI alkalmazással közvetlenül az órájáról tekintheti meg az irányítópultján található KPI-ket és kártyacsempéket. A KPI-k és a kártyacsempék a legalkalmasabbak arra, hogy egy kisméretű kijelzőn szívverés típusú mértékeket jelenítsenek meg. Az irányítópult frissíthető az iPhone-járól vagy akár magáról az óráról is.

## <a name="install-the-apple-watch-app"></a>Az Apple Watchra készült alkalmazás telepítése
Az Apple Watchra készült Power BI mobilalkalmazás az iOS-re készült Power BI alkalmazás részét képezi, így amikor az Apple Store-ból [letölti az iPhone-jára a Power BI alkalmazást](https://go.microsoft.com/fwlink/?LinkId=522062 "Az iPhone-alkalmazás letöltése"), automatikusan a Watchra készült Power BI alkalmazást is letölti. Az Apple útmutatójából megtudhatja, hogyan történik az [Apple Watch-alkalmazások telepítése](https://support.apple.com/HT204784).

## <a name="use-the-power-bi-app-on-the-apple-watch"></a>Az Apple Watchra készült Power BI alkalmazás használata
Nyissa meg az Apple Watchra készült Power BI alkalmazást vagy az óra springboardjáról, vagy közvetlenül az óraszámlapon a Power BI-widgetre kattintva (ha konfigurálta).

![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_complicatn240arrow.png)

Az Apple Watchra készült Power BI alkalmazás két részből áll.

* Az **index képernyő** a szinkronizált irányítópulton található összes KPI és kártyacsempe áttekintését teszi lehetővé.
  
  ![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_indexscreen240.png)
* A **fókuszban lévő csempe**: Kattintson az index képernyőn egy csempére a részletes nézetének megtekintéséhez.
  
  ![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_kpi.png)

## <a name="refresh-a-dashboard-from-your-apple-watch"></a>Irányítópult frissítése Apple Watchról
A szinkronizált irányítópultját közvetlenül az órájáról is frissítheti.

* Az órán az irányítópult nézetben nyomjon hosszan a képernyőre, majd válassza a **refresh** (frissítés) lehetőséget.

Az órára készült alkalmazás ekkor szinkronizálja az irányítópultot a Power BI szolgáltatásban lévő adatokkal.

> [!NOTE]
> Az órára készült alkalmazás az iPhone-on található Power BI mobilalkalmazáson keresztül kommunikál a Power BI-jal. Ezért ahhoz, hogy az órára készült alkalmazáson lévő irányítópult frissülhessen, az iPhone-ján lévő Power BI alkalmazásnak (legalább a háttérben) futnia kell.
> 
> 

## <a name="refresh-a-dashboard-on-your-apple-watch-from-your-iphone"></a>Apple Watchon lévő irányítópult frissítése iPhone-ról
Az Apple Watchon lévő irányítópultot az iPhone-járól is frissítheti.

1. Az iPhone-ján található Power BI-ban nyissa meg az Apple Watchon szinkronizálni kívánt irányítópultot. 
2. Válassza **További beállítások** (...) > **Szinkronizálás a Watchcsal** lehetőséget.

A Power BI ekkor jelzi, hogy folyamatban van az irányítópult szinkronizálása az órával.

Egyszerre csak egy irányítópultot szinkronizálhat az órával.

> [!TIP]
> Ahhoz, hogy az óráján egyszerre több irányítópult csempéjét is megtekinthesse, hozzon létre egy új irányítópultot a Power BI szolgáltatásban, majd rögzítse rá az összes releváns csempét.
> 
> 

## <a name="set-a-custom-power-bi-widget"></a>Egyéni Power BI-widget beállítása
Közvetlenül az Apple Watch óraszámlapján is megjeleníthet egy adott Power BI-csempét, hogy az mindig látható és elérhető legyen.

Az Apple Watchra készült Power BI-widget megközelítőleg olyan gyakran frissül, amilyen gyakran az adatok is, így mindig naprakész információval szolgál.

### <a name="add-a-power-bi-widget-to-your-watch-face"></a>Power BI-widget felvétele az óraszámlapon
Tekintse meg az Apple útmutatói között [Az óraszámlap módosítása az Apple Watchon](https://support.apple.com/HT205536) témakört.

### <a name="change-the-text-on-the-widget"></a>Szöveg módosítása a widgeten
Tekintve, hogy az Apple Watch óraszámlapján csak kevés hely áll rendelkezésünkre, az Apple Watchra készült Power BI alkalmazásban módosítható a widget címe, hogy ezen a kis helyen is elférjen.

* Az iPhone-ján nyissa meg az óra vezérléséhez használt Apple Watch alkalmazást, válassza ki a Power BI-t, navigáljon a widget név mezőjéhez, majd írjon be egy új nevet.
  
  ![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_oniphone.png)

> [!NOTE]
> Ha nem változtatja meg a nevet, akkor a Power BI-widget annyi karakter hosszúságúra rövidíti a nevet, ahány karakter az óraszámlapon elfér. 
> 
> 

## <a name="next-steps"></a>Következő lépések
Visszajelzésével segíthet nekünk eldönteni, hogy a jövőben mely funkciókat implementáljuk, ezért kérjük, szavazzon, hogy milyen funkciókat szeretne viszontlátni a Power BI mobilalkalmazásokban. 

* Az [iPhone-ra készült Power BI mobilalkalmazás](https://go.microsoft.com/fwlink/?LinkId=522062) letöltése
* Kövessen minket a [@MSPowerBITwitteren](https://twitter.com/MSPowerBI)
* Vegyen részt [a Power BI-közösség](https://community.powerbi.com/) beszélgetéseiben

