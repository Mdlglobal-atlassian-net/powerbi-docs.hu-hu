---
title: Kapcsolódás a Microsoft Dynamics szolgáltatáshoz a Power BI segítségével
description: Planview Enterprise a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ad93a57e08f858c78e71d66792315d1836c2a075
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/21/2018
ms.locfileid: "46547660"
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Kapcsolódás a Microsoft Dynamics szolgáltatáshoz a Power BI segítségével
A Planview Enterprise tartalomcsomaggal teljesen új módokon jelenítheti meg az erőforrás- és munkakezelési adatokat közvetlenül a Power BI-ban. A Planview Enterprise bejelentkezési hitelesítő adatainak használatával interaktívan tekintheti meg a portfólióbefektetési kiadásokat, megtekintheti, hogy mely tételek lépték túl a költségvetést, és melyek vannak azon belül, továbbá megismerheti, hogy hogyan illeszkednek a projektek a vállalat stratégai prioritásaihoz. Az alapértelmezett irányítópultot és jelentéseket emellett kibővítheti az Ön számára legfontosabb elemzésekkel.

Csatlakozás a [Planview Enterprise tartalomcsomaghoz a Power BI-ban](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>A Planview Enterprise adatok Power BI-ba importálásához Planview Enterprise-felhasználónak kell lennie, akinek a szerepkörén engedélyezve van a Reporting Portal Viewer szolgáltatás. A további követelményeket alább találja.

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
    ![](media/service-connect-to-planview/get.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
    ![](media/service-connect-to-planview/services.png)
3. A Power BI oldalán válassza a **Planview Enterprise**, majd a **Beolvasás** lehetőséget:  
    ![](media/service-connect-to-planview/planview.png)
4. A Planview Enterprise URL-cím szövegmezőjében adja meg a használni kívánt Planview Enterprise-kiszolgáló URL-címét. A Planview Enterprise-adatbázis szövegmezőjében adja meg a Planview Enterprise-adatbázis nevét, majd kattintson a Tovább lehetőségre.  
    ![](media/service-connect-to-planview/params.png)
5. A Hitelesítési módszer listáról válassza az **Alapszintű** lehetőséget, ha még nincs bejelölve. Adja meg a fiókjához tartozó **Felhasználónevet** és **Jelszót**, és válassza a **Bejelentkezés** lehetőséget.  
   ![](media/service-connect-to-planview/creds.png)
6. A bal oldali panelen válassza a Planview Enterprise-t az irányítópultok listájáról.  
     A Power BI importálja a Planview Enterprise adatokat az irányítópultra. Vegye figyelembe, hogy az adatok betöltése eltarthat egy darabig.  
    ![](media/service-connect-to-planview/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
A Planview Enterprise adatok Power BI-ba importálásához Planview Enterprise-felhasználónak kell lennie, akinek a szerepkörén engedélyezve van a Reporting Portal Viewer szolgáltatás. A további követelményeket alább találja.

Ez az eljárás feltételezi, hogy már bejelentkezett a Microsoft Power BI kezdőlapjára egy Power BI-fiókkal. Ha még nincs Power BI-fiókja, látogasson el a [powerbi.com](https://powerbi.microsoft.com/get-started/) webhelyre, és a **Power BI - Felhőbeli együttműködés és megosztás** területen válassza az **Ingyenes próba** lehetőséget. Ez után kattintson az **Adatok letöltése** lehetőségre.

## <a name="next-steps"></a>Következő lépések:

[Mi az a Power BI?](power-bi-overview.md)

[Power BI – Adatok lekérése](service-get-data.md)