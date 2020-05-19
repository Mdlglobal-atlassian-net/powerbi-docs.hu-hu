---
title: Csatlakozás a QuickBooks Online-hoz a Power BI használatával
description: QuickBooks Online a Power BI-hoz
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 4c21c36694f36e4d6f95b8edc920648313dc8a7a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348505"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Csatlakozás a QuickBooks Online-hoz a Power BI használatával
Amikor Power BI-ból csatlakozik a QuickBooks Online-adatokhoz, azonnal megjelenik egy Power BI-irányítópult és néhány Power BI-jelentés, amelyek alapján pénzforgalmával, jövedelmezőségével, ügyfeleivel és sok más területtel kapcsolatban összefüggéseket tárhat fel. Az irányítópultot és a jelentéseket a megjelenített formában is használhatja, illetve igényei szerint át is alakíthatja azokat, hogy azokat az információkat emeljék ki, melyek az Ön számára a legfontosabbak. Az adatokat naponta egyszer automatikusan frissíti a rendszer.

Kapcsolódjon a Power BI-hoz készült [QuickBooks Online-sablonalkalmazáshoz](https://dxt.powerbi.com/getdata/services/quickbooks-online).

>[!NOTE]
>A QuickBooks Online adatok Power BI-ba történő importálásához, QuickBooks Online-fiókjában rendszergazdának kell lennie, és rendszergazdai hitelesítő adataival kell bejelentkeznie. A QuickBooks Desktop szoftverrel ez az összekötő nem használható. 

## <a name="how-to-connect"></a>Csatlakozás

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Válassza ki **QuickBooks Online**, majd kattintson a **Letöltés most** lehetőségre.
   
   ![A QuickBooks letöltése](media/service-connect-to-quickbooks-online/qbo.png)

4. A **Telepíti ezt a Power BI-alkalmazást?** területen válassza a **Telepítés** lehetőséget.

    ![A QuickBooks telepítése](media/service-connect-to-quickbooks-online/power-bi-install-quickbooks.png)

4. Az **Alkalmazások** panelen válassza a **QuickBooks** csempét.

   ![A QuickBooks csempe kiválasztása](media/service-connect-to-quickbooks-online/power-bi-quickbooks-tile.png)

6. **Az új alkalmazás használatának első lépései** résznél válassza az **Csatlakozás** lehetőséget.

    ![Első lépések az új alkalmazással](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Hitelesítési módszerként válassza az **oAuth2** eljárást, majd kattintson a **Bejelentkezés** lehetőségre. 
5. Amikor a rendszer kéri, adja meg QuickBooks Online hitelesítő adatait, majd haladjon végig a hitelesítési folyamaton. Ha böngészőjében már bejelentkezett a QuickBooks Online-ba, a rendszer nem feltétlenül fogja kérni hitelesítő adatait.
   >[!NOTE]
   >A QuickBooks Online-fiókjába rendszergazdai hitelesítő adatokkal kell bejelentkeznie.
6. A következő képernyőn válassza ki azt a céget, amelyet csatlakoztatni szeretne a Power BI-hoz.
   
   ![Majdnem készen áll a QuickBooks használatára](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)

7. Az importálási folyamat elindításához a következő képernyőn kattintson az **Authorize** (Engedélyezés) elemre. A folyamat a vállalati adatok méretétől függően néhány percet is igénybe vehet. 
   
   ![A QuickBooks engedélyezése](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
8. Miután a Power BI importálta az adatokat, megjelenik a QuickBooks-alkalmazás tartalomlistája: egy új irányítópult, jelentés és adathalmaz.
9. A feltárási folyamat elindításához válassza ki a QuickBooks irányítópultját. A Power BI automatikusan létrehozza ezt az irányítópultot az importált adatok megjelenítéséhez.

    ![QuickBooks-irányítópult](media/service-connect-to-quickbooks-online/power-bi-connect-quickbooks-sample.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](../consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](../create-reports/service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](../consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="troubleshooting"></a>Hibaelhárítás
**„Hoppá! Hiba történt.”**

Ha az **Authorize** (Engedélyezés) választása után ezt az üzenetet kapja:

„Hoppá! Hiba történt.” Zárja be ezt az ablakot, és próbálkozzon újra.

Az alkalmazásra már feliratkozott a cég egy másik felhasználója. Az előfizetés módosításához írjon a(z) [rendszergazda e-mail-címe] címre.”

![Hoppá! Hiba történt](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

…Ez a hiba azt jelzi, hogy a vállalat egy másik rendszergazdája már csatlakozott a vállalati adatokhoz a Power BI-jal. Kérje meg azt a rendszergazdát, hogy ossza meg Önnel az irányítópultot. Jelenleg csak egy rendszergazdai jogú felhasználó csatlakoztathat egy adott QuickBooks Online céges adatkészletet a Power BI-hoz. Miután a Power BI létrehozta az irányítópultot, a rendszergazda megoszthatja az ugyanazon a Power BI-bérlőn található munkatársakkal.

**„Az alkalmazásban nincs beállítva az Ön országából induló kapcsolatok engedélyezése"**

A Power BI jelenleg csak a QuickBooks Online egyesült államokbeli kiadásait támogatja. 

![Az alkalmazásban nincs beállítva az Ön országából induló kapcsolatok engedélyezése](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](../fundamentals/power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](../fundamentals/service-basic-concepts.md)
