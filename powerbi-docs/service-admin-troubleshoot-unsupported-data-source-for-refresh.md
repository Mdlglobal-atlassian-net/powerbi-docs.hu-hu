---
title: Hibaelhárítás – frissítéshez nem támogatott adatforrás
description: Hibaelhárítás – frissítéshez nem támogatott adatforrás
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 08931086d05ca3fe7edba2cd195a4f6f61cfccc7
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025907"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Hibaelhárítás – frissítéshez nem támogatott adatforrás
Előfordulhat, hogy hibaüzenetet tapasztal, amikor egy adatkészletet ütemezett frissítését próbálja konfigurálni.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Ez akkor fordul elő, ha a Power BI Desktopban használt adatkészlet nem támogatja a frissítést. Meg kell keresnie, hogy milyen adatforrást használ, és összevetnie az [Adatok frissítése a Power BI-ban](refresh-data.md) című cikkben található támogatott adatforrások listájával. 

## <a name="find-the-data-source"></a>Adatforrás megkeresése
Ha nem biztos abban, hogy milyen adatforrást használt, akkor a következő lépéseket végrehajtva megkeresheti az adatforrást a Power BI Desktopban.  

1. Győződjön meg arról, hogy a Power BI Desktopban a **Report** (Jelentés) ablaktábla van megnyitva.  
   ![Desktop jelentéspanel](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. A menüszalagon válassza az **Edit Queries** (Lekérdezések szerkesztése) lehetőséget.  
   ![Lekérdezések szerkesztése](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Válassza az **Advanded Editor** (Speciális szerkesztő) lehetőséget.  
   ![Speciális szerkesztő](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Jegyezze fel a forrásnál látható szolgáltatót.  Ebben a példában az ActiveDirectory a szolgáltató.  
   ![Adatforrás-szolgáltató](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Vesse össze a szolgáltatót az [Adatok frissítése a Power BI-ban](refresh-data.md) című cikkben található támogatott adatforrások listájával.  Láthatja, hogy az Active Directory-adatforrás nem támogatja a frissítést.  

## <a name="next-steps"></a>Következő lépések
[Adatfrissítés](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[Helyszíni adatátjáró](service-gateway-onprem.md)  
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
[A személyes Power BI Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

