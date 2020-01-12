---
title: A Power Query háttérbeli frissítésének letiltása
description: Arra vonatkozó útmutató, hogy mikor kell letiltani a Power Query háttérbeli frissítését.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: ef9ab7c0d84b926094c33e8aa2765cd43b844314
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623061"
---
# <a name="disable-power-query-background-refresh"></a>A Power Query háttérbeli frissítésének letiltása

Ez a cikk a Power BI Desktopot használó importálásiadat-modellezőknek szól.

Alapértelmezés szerint amikor a Power Query adatokat importál, eközben minden lekérdezés esetében legfeljebb 1000 sornyi előnézeti adatot gyorsítótáraz. Az előnézeti adatoknak köszönhetően megtekintheti a forrásadatok, valamint a lekérdezések egyes lépései transzformációs eredményeinek gyors előnézetét. Ezek különállóan vannak tárolva a lemezen, nem pedig a Power BI Desktop-fájlban.

Ha azonban a Power BI Desktop-fájl nagy mennyiségű lekérdezést tartalmaz, az előnézeti adatok lekérése és tárolása meghosszabbíthatja a frissítés befejezéséhez szükséges időt.

## <a name="recommendation"></a>Javaslat

Felgyorsíthatja a frissítést, ha úgy állítja be a Power BI Desktop-fájlt, hogy _a háttérben_ frissítse az előnézeti gyorsítótárat. Ezt úgy engedélyezheti a Power BI Desktopban, hogy a _Fájl > Lehetőségek és beállítások > Beállítások_ lehetőséget, majd az _Adatok betöltése_ lapot választja. Ezután bekapcsolhatja a **Adatelőnézet háttérbeli letöltésének engedélyezése** lehetőséget. Fontos megjegyezni, hogy ezt a beállítást csak az aktuális fájlra vonatkozóan lehet beállítani.

![A Power BI Desktop háttérbeli adatátvitelre vonatkozó beállításai](media/power-query-background-refresh/power-query-options-background-data.png)

A háttérben történő frissítés engedélyezésének hatására előfordulhat, hogy az előnézeti adatok elavulttá válnak. Ha ez történik, a Power Query-szerkesztő a következő figyelmeztetéssel értesíti:

![A Power Query-szerkesztő régi előnézeti adatokra vonatkozó figyelmeztetése](media/power-query-background-refresh/power-query-preview-data-old.png)

Az előnézeti gyorsítótár bármikor frissíthető. Az **Előnézet frissítése** paranccsal frissítheti egy adott lekérdezésre vagy az összes lekérdezésre vonatkozóan. Ezt a Power Query-szerkesztő ablakának **Kezdőlap** menüszalagján találhatja meg.

![A Power Query-szerkesztő az előnézeti adatok frissítésére szolgáló parancsai](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Power Query-dokumentáció](/power-query/)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
