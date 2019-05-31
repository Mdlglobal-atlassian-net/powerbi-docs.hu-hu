---
title: Kapcsolódás a Power BI-ból a VMobhoz
description: VMob a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 2cf6b351c00d89ad6e87b6bc95661dab57078bac
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61151883"
---
# <a name="connect-to-vmob-with-power-bi"></a>Kapcsolódás a Power BI-ból a VMobhoz
A Power BI-hoz készült VMob-tartalomcsomaggal könnyedén nyomon követheti és feltárhatja VMob-adatait. A Power BI az alábbi adatokat kéri le: Felhasználói statisztika a teljes időszakban és az elmúlt 30 napban, kiskereskedelmi KPI az elmúlt 30 napban és kampányteljesítmény az elmúlt 30 napban.

Kapcsolódjon a Power BI-hoz készült [VMob-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/vmob).

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
    ![](media/service-connect-to-vmob/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-vmob/services.png)
3. Válassza a **VMob** \> **Beolvasás** lehetőséget.
   
   ![](media/service-connect-to-vmob/vmob.png)
4. Amikor a rendszer kéri, adja meg VMob URL-címét, majd kattintson a Tovább gombra. Ezt az URL-címet a VMob külön adja meg.
   
    ![](media/service-connect-to-vmob/params.png)
5. A Hitelesítési módszer legördülő menüjében válassza az **Alapszintű** lehetőséget, adja meg a VMob-fiókja felhasználónevét és jelszavát, majd kattintson a **Bejelentkezés** gombra.
   
    ![](media/service-connect-to-vmob/creds.png)
6. Az importálási folyamat ekkor automatikusan elindul, és a Power BI beolvassa a VMob-adatait, hogy létrehozzon Önnek egy használatra kész irányítópultot és jelentést.
   
   ![](media/service-connect-to-vmob/dashboard2.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

