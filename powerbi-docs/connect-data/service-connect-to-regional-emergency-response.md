---
title: Csatlakozás a Regionális vészhelyzet-kezelési irányítópulthoz
description: A regionális vészhelyzetekben használható COVID-19 Döntéstámogatási irányítópult beszerzése, telepítése és csatlakozás az adatokhoz
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149670"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Csatlakozás a Regionális vészhelyzet-kezelési irányítópulthoz
A Regionális vészhelyzet-kezelési irányítópult a [Microsoft Power Platform Regionális vészhelyzet-kezelési megoldásának](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview) jelentéskészítési összetevője. A regionális szervezetek rendszergazdái megtekinthetik az irányítópultot a Power BI-bérlőben ezáltal gyorsan áttekinthetik a hatékony döntéshozatalt elősegítő lényeges adatokat és metrikákat.

![Regionális vészhelyzet-kezelési irányítópult-alkalmazás jelentése](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

Ez a cikk a Regionális Vészhelyzet-kezelési alkalmazásnak a Regionális vészhelyzet-kezelési irányítópult sablonalkalmazásával történő telepítését, és az adatforrásokhoz való csatlakozást ismerteti.

Az irányítópult által megjelenített adatokról az [Eredmények lekérése](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights) című szakasz nyújt részletes információkat.

Miután telepítette a sablonalkalmazást és csatlakoztatta az adatforrásokat, igény szerint testre szabhatja a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

## <a name="prerequisites"></a>Előfeltételek

A sablonalkalmazás telepítése előtt először a [Regionális vészhelyzet-kezelési megoldást](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy) kell telepítenie és beállítania. Ennek a megoldásnak a telepítésével létrehozza azokat az adatforrás-hivatkozásokat, amelyek ahhoz szükségesek, hogy az alkalmazást adatokkal lehessen feltölteni.

A Regionális vészhelyzet-kezelési megoldás telepítése közben jegyezze fel a [Common Data Service-beli környezetpéldány URL-címét](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). Erre szüksége lesz a sablonalkalmazás adatokhoz csatlakoztatásához.

## <a name="install-the-app"></a>Az alkalmazás telepítse

1. Az alkalmazás beszerzéséhez kattintson a következő hivatkozásra: [Regionális vészhelyzet-kezelési irányítópult sablonalkalmazása](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Az alkalmazás AppSource-oldalán válassza az [**AZONNALI BESZERZÉS**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response) lehetőséget.

    [![Regionális vészhelyzet-kezelési irányítópult sablonalkalmazása az AppSource-on](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Válassza a **Telepítés** gombot. 

    ![A Regionális vészhelyzet-kezelési irányítópult telepítése](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    A telepítést követően megtekintheti az alkalmazást az Alkalmazások oldalon.

   ![Regionális vészhelyzet-kezelési irányítópult-alkalmazás az Alkalmazások oldalon](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Kapcsolódás adatforrásokhoz

1. Az alkalmazás megnyitásához kattintson az Alkalmazás oldalon lévő ikonra.

1. A kezdőképernyőn válassza a **Böngészés** lehetőséget.

   ![Sablonalkalmazás üdvözlőképernyője](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   Ekkor az alkalmazás megnyílik és mintaadatokat jelenít meg.

1. Kattintson az **Adatok csatlakoztatása** hivatkozásra az oldal tetején látható szalagcímen.

   ![Regionális vészhelyzet-kezelési irányítópult-alkalmazás adatkapcsolat-hivatkozása](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. A megjelenő párbeszédablakban írja be a [Common Data Service-beli környezetpéldány URL-címét](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Például: https://[sajatkornyezet].crm.dynamics.com. Ha befejezte, kattintson a **Tovább** elemre.

   ![Regionális vészhelyzet-kezelési irányítópult-alkalmazás URL-címre vonatkozó párbeszédpanelje](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. Az ekkor megjelenő párbeszédpanelen állítsa be az **OAuth2** hitelesítési módszert. Az adatvédelmi szint beállításával nem kell foglalkoznia.

   Válassza a **Bejelentkezés** lehetőséget.

   ![Regionális vészhelyzet-kezelési irányítópult-alkalmazás hitelesítési párbeszédpanelje](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. A Microsoft bejelentkezési képernyőjén jelentkezzen be Power BI-ba.

   ![Microsoft bejelentkezési képernyő](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Miután bejelentkezett, a jelentés csatlakozik az adatforrásokhoz, és naprakész adatokkal töltődik fel. Eközben forog a tevékenységfigyelő.

   ![A Regionális vészhelyzet-kezelési irányítópult-alkalmazás frissítése folyamatban](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Jelentés frissítésének ütemezése

Miután lezajlott az adatfrissítés, [állítson be frissítési ütemezést](../refresh-scheduled-refresh.md) a jelentés adatainak naprakészen tartásához.

1. A felül látható fejlécen kattintson a **Power BI** elemre.

   ![Power BI-útkövetés](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. A bal oldali navigációs panelen, a **Munkaterületek** rész alatt, keresse meg a Regionális vészhelyzet-kezelési irányítópult munkaterületét, és kövesse az [Ütemezett frissítés konfigurálása](../refresh-scheduled-refresh.md) című cikkben ismertetett utasításokat.

## <a name="customize-and-share"></a>Testreszabás és megosztás

További információkért lásd: [Az alkalmazás testreszabása és megosztása](../service-template-apps-install-distribute.md#customize-and-share-the-app). Az alkalmazás közzététele és terjesztése előtt mindenképpen tekintse át a [jelentésekre vonatkozó jogi nyilatkozatokat](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer).

## <a name="next-steps"></a>Következő lépések
* [A Regionális vészhelyzet-kezelési irányítópult ismertetése](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Kríziskommunikáció-mintasablon beállítása és megismerése a Power Apps-ben](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
* [Mik azok a Power BI-sablonalkalmazások?](../service-template-apps-overview.md)
* [Sablonalkalmazások telepítése és terjesztése a vállalatnál](../service-template-apps-install-distribute.md)
