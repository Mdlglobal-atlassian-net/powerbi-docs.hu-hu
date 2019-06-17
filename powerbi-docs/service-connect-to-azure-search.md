---
title: Kapcsolódás az Azure Search szolgáltatáshoz a Power BI-jal
description: Azure Search-tartalomcsomag a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4756bcef5d50783940a9b9565d0af6b9978e52b7
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721287"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Kapcsolódás az Azure Search szolgáltatáshoz a Power BI-jal
Az Azure Search Forgalomelemzés funkciójával monitorozható és értelmezhető az Azure Search szolgáltatáshoz beérkező forgalom. A Power BI-hoz készült Azure Search-tartalomcsomag segítségével részletes információk szerezhetők a keresési adatok alapján az elmúlt 30 napra visszamenőleg (a keresésről, az indexelésről, a szolgáltatás statisztikáiról és a késésről). Az [Azure blog bejegyzésében](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/) további részletek olvashatók.

Kapcsolódjon a Power BI-hoz készült [Azure Search-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/azure-search).

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. A **Szolgáltatások** keretben kattintson a **Beolvasás** elemre.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Válassza az **Azure Search** \> **Beolvasás** elemet.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Adja meg annak a Table Storage-fióknak a nevét, amely az Azure Search-elemzést tárolja.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Hitelesítési mechanizmusként válassza a **Kulcs** lehetőséget, majd adja meg a Storage-fiók kulcsát. Kattintson a **Bejelentkezés** gombra. Ennek hatására elkezdődik a betöltés.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Amikor befejeződik a betöltés, a navigációs panelen megjelenik egy új irányítópult, egy új jelentés és egy új modell. Az importált adatok megtekintéséhez válassza az irányítópultot.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
Az Azure Search-tartalomcsomag csak akkor használható, ha az Azure Search Forgalomelemzés engedélyezve van a fiókban.

## <a name="troubleshooting"></a>Hibaelhárítás
Ellenőrizze, hogy helyesen adta-e meg a Storage-fiók nevét, illetve a teljes hozzáférési kulcsot. A Storage-fiók nevének meg kell egyeznie annak a fióknak a nevével, amelyben az Azure Search Forgalomelemzés konfigurálva van.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

