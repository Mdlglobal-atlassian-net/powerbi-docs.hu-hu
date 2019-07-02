---
title: Power BI-sablonalkalmazás frissítése, törlése és kivonása
description: Sablonalkalmazás frissítése, törlése és kinyerése.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125878"
---
# <a name="update-delete-and-extract-template-app"></a>Sablonalkalmazás frissítése, törlése és kinyerése

Most, hogy az alkalmazása üzemi környezetbe került, újrakezdheti a tesztelési fázist anélkül, hogy az üzemi környezetben lévő alkalmazás működését megzavarná.
## <a name="update-your-app"></a>Alkalmazás frissítése


1. A **Kiadáskezelés** panelen válassza az **Alkalmazás létrehozása** lehetőséget.
2. Menjen végig ismét az alkalmazás-létrehozási folyamaton.
3. Miután megadta a **Védjegyezés**, a **Tartalom**, a **Vezérlő** és a **Hozzáférés** beállításait, válassza ismét az **Alkalmazás létrehozása** lehetőséget.
4. Válassza a **Bezárás** lehetőséget, és térjen vissza **Kiadáskezelés** panelre.

   Láthatja, hogy most már két verzióval rendelkezik: Egy verzióval üzemi környezetben, valamint egy új tesztelési verzióval.

    ![A sablonalkalmazás két verziója](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. Ha készen áll az alkalmazás előléptetésére az üzem előtti állapotba a bérlőn kívüli további teszteléshez, térjen vissza a Kiadáskezelés panelre, és válassza a **Tesztelés** mellett az **Alkalmazás előléptetése** lehetőséget.
6. A hivatkozás immáron használható. Küldje be újra a Cloud Partner Portalra (CPP-re) a [Power BI-alkalmazásajánlat frissítéséről](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer) szóló cikk lépéseit követve.
7. A CPP-ben **közzé kell tennie** újra az ajánlatot, valamint ismét érvényesíteni kell.

>[!NOTE]
>Az alkalmazást csak akkor léptetheti elő a gyártási fázisra, ha jóvá lett hagyva a Cloud Partner Portalon, valamint már közzétette.

## <a name="extract-workspace"></a>Munkaterület kinyerése
Egy sablonalkalmazás korábbi verziójára váltás mostantól minden eddiginél könnyebb a kinyerési funkciónak köszönhetően. Az alábbi lépésekkel egy adott alkalmazásverziót nyerhet ki a különböző kiadási fázisokból egy új munkaterületre:

1. A Kiadáskezelés panelen kattintson a Továbbiak **(...)** , majd a **Kinyerés** lehetőségre.

    ![sablonalkalmazás verziójának kinyerése](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![sablonalkalmazás verziójának kinyerése](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. A párbeszédpanelen adja meg a kinyert munkaterület nevét. Ekkor megjelenik egy új munkaterületet.

Az új munkaterületi verziókezelési beállítások alaphelyzetbe kerülnek, Ön pedig az újonnan kinyert munkaterületen fejlesztheti és terjesztheti a sablonalkalmazást.

## <a name="delete-template-app-version"></a>Sablonalkalmazás verziójának törlése
A sablonalkalmazás munkaterülete az aktív elosztott sablonalkalmazás forrása. A sablonalkalmazás felhasználóinak védelme érdekében nem törölhetők munkaterületek úgy, hogy előtte nem távolította el annak összes létrehozott alkalmazásverzióját.
Egy alkalmazásverzió törlése az alkalmazás URL-címét is törli, amely ezután nem használható.

1. A Kiadáskezelés panelen kattintson a három pontra **(...)** , majd a **Törlés** lehetőségre.
 ![sablonalkalmazás verziójának törlése](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
  ![sablonalkalmazás verziójának törlése](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Ügyeljen arra, hogy ne törölje azt az alkalmazásverziót, amelyet ügyfelek vagy az **AppSource** használ, ezzel ugyanis használhatatlanná teszi azt.

## <a name="next-steps"></a>Következő lépések

Arról, hogyan használják a sablonalkalmazást az ügyfelek a [Sablonalkalmazások telepítése, testreszabása és terjesztése a szervezetnél](service-template-apps-install-distribute.md) szakaszban olvashat.

Az alkalmazás terjesztését részletesen [A Power BI-alkalmazásra vonatkozó ajánlat](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) weblapon ismerheti meg.
