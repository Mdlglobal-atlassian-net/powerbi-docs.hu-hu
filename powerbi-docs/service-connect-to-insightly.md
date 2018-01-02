---
title: "Csatlakozás az Insightly-hoz a Power BI használatával"
description: Insightly a Power BI-hoz
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 822d38dc84ca4473bae64339b8dafc1414bc856b
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-insightly-with-power-bi"></a>Csatlakozás az Insightly-hoz a Power BI használatával
Megjelenítheti és megoszthatja Insightly CRM-adatait a Power BI-ban az Insightly tartalomcsomag használatával. Csatlakozzon a Power BI-hoz az Insightly API-kulccsal jelentések és irányítópultok megtekintéséhez és felépítéséhez a CRM-adatokból. A Power BI használatával új módokon elemezheti az adatokat, hatékony gráfokat és diagramokat hozhat létre, valamint térképen jeleníthet meg a kapcsolattartókat, érdeklődőket és cégeket.

Kapcsolódjon a Power BI-hoz készült [Insightly tartalomcsomaghoz](https://app.powerbi.com/getdata/services/insightly).

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-insightly/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-insightly/services.png)
3. Válassza az **Insightly** \>  **Lekérés** lehetőséget.
   
   ![](media/service-connect-to-insightly/insightly.png)
4. Válassza a **Kulcs** lehetőséget mint hitelesítési típust, adja meg az Insight API-kulcsot, majd válassza a **Bejelentkezés** lehetőséget. [Ennek megkeresésének](#FindingParams) részleteit alább találja.
   
   ![](media/service-connect-to-insightly/creds.png)
5. A jóváhagyás után automatikusan megkezdődik az importálási folyamat. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
     ![](media/service-connect-to-insightly/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](service-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](service-dashboard-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A tartalomcsomag a következő táblákat tartalmazza a megfelelő rekordokból származó mezőkkel:

| Táblák |  |  |  |
| --- | --- | --- | --- |
| Kapcsolattartók |Lehetőségek |Folyamat szakaszai |Feladat befejezésének dátuma |
| Egyéni mezők |Lehetőség záró dátuma |Projekt befejezésének dátuma |Feladatok |
| Események |Lehetőség előrejelzett dátuma |Projektek |Csapatok/tagok |
| Érdeklődők |Cégek |Címkék |Felhasználók |

Sok tábla és jelentés egyedi számított mezőket is tartalmaz, például a következőket:  

* „Csoportosított” lehetőség előrejelzett záró dátumai, lehetőség tényleges záró dátumai, projekt befejezési dátumai és feladat befejezési dátumai mezőkkel rendelkező táblák hónap, negyedév vagy év alapján végzett elemzéshez.  
* A lehetőségek súlyozott értékmezője (lehetőség értéke * az elnyerés valószínűsége).  
* Átlagos és teljes időtartam mezők a feladatokhoz, a kezdés és a befejezés dátumai alapján.  
* A lehetőség nyerési aránya (az elnyert lehetőségek száma/az összes lehetőség száma) és a nyerési arány értéke (az elnyert lehetőségek értéke/az összes lehetőség értéke) számított mezőivel rendelkező jelentések.  

## <a name="system-requirements"></a>Rendszerkövetelmények
Szükség van egy olyan Insightly-fiókra, amely hozzáféréssel rendelkezik az Insightly API-hoz. A láthatósági engedélyek a Power BI-jal való kapcsolat létesítésére használt API-kulcson alapulnak. Az Ön által látható összes Insightly-rekord a másokkal megosztott Power BI-jelentésekben és -irányítópultokon is látható.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
**API-kulcs**

Ha másolni szeretné az API-kulcsot az Insightly-ból, válassza az Insightly profilmenüjének Felhasználói beállítások elemét, és görgessen lefelé. Ezzel a karakterlánccal csatlakoztathatja az adatokat a Power BI-hoz.

![](media/service-connect-to-insightly/findapi.png)

## <a name="troubleshooting"></a>Hibaelhárítás
Az adatokat az Insightly API-n keresztül importálja, amelyre az Insightly előfizetési csomag szintjétől függő napi korlát vonatkozik. A korlátok az API-dokumentáció Sebességkorlátozás/Kérelmek szabályozása szakaszában szerepelnek: https://api.insight.ly/v2.2/Help#!/Overview/Introduction#ratelimit

A megadott jelentések az Insightly alapértelmezett mezőit használják, így előfordulhat, hogy nem tartalmazzák a testreszabásait. Szerkessze a jelentést az összes elérhető mező megtekintéséhez.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

