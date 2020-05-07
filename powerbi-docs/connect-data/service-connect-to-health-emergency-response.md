---
title: Csatlakozás a Kórházi sürgősségi döntéstámogatási irányítópulthoz
description: Az egészségügyi vészhelyzetekben használható COVID-19 Döntéstámogatási irányítópult beszerzése, telepítése és csatlakozás az adatokhoz
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: b951e96a5d81603dc91e4fc47a2b412d4140f85d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "80752050"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>Csatlakozás a Kórházi sürgősségi döntéstámogatási irányítópulthoz
A Kórházi sürgősségi döntéstámogatási irányítópult sablonalkalmazása a [Microsoft Power Platform egészségügyi vészhelyzetek kezelésére szolgáló megoldásának](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/) jelentéskészítési összetevője. Az irányítópult az egészségügyi rendszer összesített adatainak bemutatásával segít jó időben jó döntéseket hozni a válságmenedzsereknek.

![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazásjelentés](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

Ez a cikk az alkalmazás telepítését és adatforrásokhoz csatlakoztatását ismerteti. Az ezzel az alkalmazással megjeleníthető jelentés használatáról a [Kórházi sürgősségi döntéstámogatási irányítópult dokumentációjából](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard) tájékozódhat.

Miután telepítette a sablonalkalmazást, és csatlakoztatta az adatforrásokat, igényei szerint testre szabhatja a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

## <a name="prerequisites"></a>Előfeltételek

A sablonalkalmazás telepítése előtt először a [Kórházi vészhelyzet-kezelési Power Platform-megoldást](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure) kell telepítenie és beállítania. Ez a megoldás hozza létre az alkalmazás adatokkal feltöltéséhez szükséges adatforrás-hivatkozásokat.

A Kórházi vészhelyzet-kezelési Power Platform-megoldás telepítése közben jegyezze fel a [Common Data Service-beli környezetpéldány URL-címét](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Erre szüksége lesz a sablonalkalmazás adatokhoz csatlakoztatásához.

## <a name="install-the-app"></a>Az alkalmazás telepítse

1. Az alkalmazás beszerzéséhez kattintson a következő hivatkozásra: [Kórházi sürgősségi döntéstámogatási irányítópult sablonalkalmazása](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare)

1. Az alkalmazás AppSource-oldalán válassza az [**AZONNALI BESZERZÉS**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare) lehetőséget.

    [![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás az AppSource-on](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare)

1. Olvassa el a **Még valami** rész tudnivalóit, és válassza a **Folytatás** lehetőséget.

    ![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás, Még valami](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. Válassza a **Telepítés** gombot. 

    ![A Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás telepítése](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    A telepítést követően megtekintheti az alkalmazást az Alkalmazások oldalon.

   ![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás az Alkalmazások oldalon](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Kapcsolódás adatforrásokhoz

1. Az alkalmazás megnyitásához kattintson az Alkalmazás oldalon lévő ikonra.

1. A kezdőképernyőn válassza a **Böngészés** lehetőséget.

   ![Sablonalkalmazás üdvözlőképernyője](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   Ekkor az alkalmazás megnyílik és mintaadatokat jelenít meg.

1. Kattintson a **Csatlakozás saját adatokhoz** hivatkozásra az oldal tetején látható szalagcímen.

   ![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás Csatlakozás saját adatokhoz hivatkozása](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. A párbeszédpanelen:
   1. A Szervezet neve mezőben adja meg a szervezet nevét, például: „Contoso Health Systems”. A mező kitöltése nem kötelező. Ez a név fog megjelenni az irányítópult bal felső részén.
   1. A CDS_base_solution mezőbe írja be a [Common Data Service-beli környezetpéldány URL-címét](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Például: https://[sajatkornyezet].crm.dynamics.com. Ha befejezte, kattintson a **Tovább** elemre.

   ![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás URL-cím párbeszédpanelje](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. A következő párbeszédpanelen állítsa a hitelesítési módszert az **OAuth2** lehetőségre. Az adatvédelmi szint beállításával nem kell foglalkoznia.

   Válassza a **Bejelentkezés** lehetőséget.

   ![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás hitelesítési párbeszédpanelje](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. A Microsoft bejelentkezési képernyőjén jelentkezzen be Power BI-ba.

   ![Microsoft bejelentkezési képernyő](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   Miután bejelentkezett, a jelentés csatlakozik az adatforrásokhoz, és naprakész adatokkal töltődik fel. Eközben forog a tevékenységfigyelő.

   ![Kórházi sürgősségi döntéstámogatási irányítópult alkalmazás frissítése folyamatban](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Jelentés frissítésének ütemezése

Miután lezajlott az adatfrissítés, [állítson be frissítési ütemezést](../refresh-scheduled-refresh.md) a jelentés adatainak naprakészen tartásához.

1. A felül látható fejlécen kattintson a **Power BI** elemre.

   ![Power BI-útkövetés](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. A bal oldali navigációs panelen, a **Munkaterületek** rész alatt, keresse meg a Kórházi sürgősségi döntéstámogatás munkaterületet, és kövesse az [Ütemezett frissítés konfigurálása](../refresh-scheduled-refresh.md) című cikkben ismertetett utasításokat.

## <a name="customize-and-share"></a>Testreszabás és megosztás

További információkért lásd: [Az alkalmazás testreszabása és megosztása](../service-template-apps-install-distribute.md#customize-and-share-the-app). Az alkalmazás közzététele és terjesztése előtt mindenképpen tekintse át a [jelentésekre vonatkozó jogi nyilatkozatokat](../create-reports/sample-covid-19-us.md#disclaimers).

## <a name="next-steps"></a>Következő lépések
* [A Kórházi vészhelyzet-kezelési jelentés ismertetése](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [Kríziskommunikáció-mintasablon beállítása és megismerése a Power Apps-ben](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
* [Mik azok a Power BI-sablonalkalmazások?](../service-template-apps-overview.md)
* [Sablonalkalmazások telepítése és terjesztése a vállalatnál](../service-template-apps-install-distribute.md)
