---
title: Csatlakozás a SparkPosthoz a Power BI használatával
description: SparkPost a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 48cdff67e613093c3ac473b0a505a6f0d57f4f2d
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008097"
---
# <a name="connect-to-sparkpost-with-power-bi"></a>Csatlakozás a SparkPosthoz a Power BI használatával
A Power BI SparkPosthoz készült tartalomcsomagja lehetővé teszi a SparkPost-fiók értékes adatkészleteinek kinyerését egyetlen informatív irányítópultra. A SparkPost-tartalomcsomag segítségével megjelenítheti a teljes levelezés statisztikai adatait, beleértve a tartományokat, a kampányokat és az internetszolgáltató által generált érdeklődést is.

Csatlakozás a [Power BI-hoz készült SparkPost-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/spark-post).

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-sparkpost/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-sparkpost/services.png)
3. Válassza ki a **SparkPost**-tartalomcsomagot, és kattintson a **Beolvasás** elemre. 
   
   ![](media/service-connect-to-sparkpost/sparkpost.png)
4. Amikor a rendszer kéri, adja meg a SparkPost API-kulcsot, és kattintson a Bejelentkezés elemre. A [paraméter megkereséséről](#FindingParams) alább olvashat részletesebben.
   
   ![](media/service-connect-to-sparkpost/creds.png)
5. Megkezdődik az adatok betöltése, ami a fiók méretétől függően eltarthat egy ideig. Miután a Power BI importálta az adatokat, a bal oldali navigációs ablaktáblán megjelenik az alapértelmezett irányítópult, a jelentés és az adatkészlet, amely az elmúlt 90 nap levelezési statisztikáit tartalmazza. Az új elemeket sárga csillag jelöli \*.
   
   ![](media/service-connect-to-sparkpost/dashboard.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A Power BI-hoz készült SparkPost-tartalomcsomag többek között ezeket az információkat tartalmazza: egyedi kattintások, elfogadások aránya, visszapattanások aránya, késleltetések aránya, visszautasítások aránya.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek keresése
A tartalomcsomag egy API-kulcsot használ a SparkPost-fiók és a Power BI csatlakoztatásához. Az API-kulcsot a fiókjában találja meg a Fiók \> API & SMTP helyen (további részletek [itt](https://support.sparkpost.com/customer/portal/articles/1933377-create-api-keys)). Javasoljuk, hogy olyan API-kulcsot használjon, amely a következő engedélyekkel rendelkezik: `Message Events: Read-only ` és `Metrics: Read-only`

![](media/service-connect-to-sparkpost/sparkpost1.png)

