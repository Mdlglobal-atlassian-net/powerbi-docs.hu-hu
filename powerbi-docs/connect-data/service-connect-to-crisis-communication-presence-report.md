---
title: Csatlakozás a válsághelyzettel kapcsolatos kommunikációról szóló jelentéshez
description: A Jelentés a COVID-19 válsághelyzettel kapcsolatos kommunikációról sablonalkalmazás beszerzése, telepítése és az adataihoz való csatlakozás
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: f637bb10ed7ec27dcb3da07fc04cae39328ffebe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "80752257"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Csatlakozás a válsághelyzettel kapcsolatos kommunikációról szóló jelentéshez

Ez a Power BI-alkalmazás a Microsoft Power Platform válsághelyzettel kapcsolatos megoldásának jelentés/irányítópult-összetevője. Nyomon követi a válságkommunikációs alkalmazást használó munkatársak mozgását. A megoldás kombinálja a Power Apps, a Power Automate, a Teams, a SharePoint és a Power BI képességeit. Weben, mobileszközön és a Teams szolgáltatásban is igénybe vehető.

![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazásjelentés](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

Az irányítópult az egészségügyi rendszer összesített adatainak megjelenítésével segít jó időben jó döntéseket hozni a válságmenedzsereknek.

Ez a cikk az alkalmazás telepítését és adatforrásokhoz csatlakoztatását ismerteti. A Kríziskommunikáció alkalmazással kapcsolatos további információkért lásd: [Kríziskommunikáció-mintasablon beállítása és megismerése a Power Appsben](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)

Miután telepítette a sablonalkalmazást és csatlakoztatta az adatforrásokat, igény szerint testre szabhatja a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

## <a name="prerequisites"></a>Előfeltételek

A sablonalkalmazás telepítése előtt telepítenie kell a [Kríziskommunikáció-mintát](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app). Ennek a megoldásnak a telepítésével létrehozza azokat az adatforrás-hivatkozásokat, amelyek ahhoz szükségesek, hogy az alkalmazást adatokkal lehessen feltölteni.

A Kríziskommunikáció-minta telepítésekor figyelje a [SharePoint-lista „CI_Employee Status” mappaelérési útját és a listaazonosítót](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>Az alkalmazás telepítse

1. Az alkalmazás beszerzéséhez kattintson a következő hivatkozásra: [Jelentés a válsághelyzettel kapcsolatos kommunikációról sablonalkalmazás](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Az alkalmazás AppSource-beli oldalán válassza az [**AZONNALI BESZERZÉS**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms) lehetőséget.

    [![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás az AppSource-on](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. A **Még valami** részben olvassa el a tudnivalókat, és válassza a **Folytatás** lehetőséget.

    ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás, Még valami](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Válassza a **Telepítés** gombot. 

    ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás telepítése](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    A telepítést követően megtekintheti az alkalmazást az Alkalmazások oldalon.

   ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás az Alkalmazások oldalon](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Kapcsolódás adatforrásokhoz

1. Az alkalmazás megnyitásához kattintson az Alkalmazás oldalon lévő ikonra.

1. A kezdőképernyőn válassza a **Böngészés** lehetőséget.

   ![Sablonalkalmazás üdvözlőképernyője](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   Ekkor az alkalmazás megnyílik és mintaadatokat jelenít meg.

1. Kattintson az **Adatok csatlakoztatása** hivatkozásra az oldal tetején látható szalagcímen.

   ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás, csatlakozás saját adatokhoz hivatkozás](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. A párbeszédpanelen:
   1. A SharePoint_Folder mezőben adja meg a [saját „CI_Employee Status” elérési útját a SharePoint-listán](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).
   1. A List_ID mezőben adja meg a listabeállításokból kapott listaazonosítót. Ha befejezte, kattintson a **Tovább** elemre.

   ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás URL-cím párbeszédpanel](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. Az ekkor megjelenő párbeszédpanelen állítsa be az **OAuth2** hitelesítési módszert. Az adatvédelmi szint beállításával nem kell foglalkoznia.

   Válassza a **Bejelentkezés** lehetőséget.

   ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás hitelesítési párbeszédpanel](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. A Microsoft bejelentkezési képernyőjén jelentkezzen be Power BI-ba.

   ![Microsoft bejelentkezési képernyő](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Miután bejelentkezett, a jelentés csatlakozik az adatforrásokhoz, és naprakész adatokkal töltődik fel. Ekkor bekapcsol a tevékenységfigyelő.

   ![Jelentés a válsághelyzettel kapcsolatos kommunikációról alkalmazás frissítési folyamata](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Jelentés frissítésének ütemezése

Miután lezajlott az adatfrissítés, [állítson be frissítési ütemezést](../refresh-scheduled-refresh.md) a jelentés adatainak naprakészen tartásához.

1. A felül látható fejlécen kattintson a **Power BI** elemre.

   ![Power BI-útkövetés](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. A bal oldali navigációs panelen, a **Munkaterületek** rész alatt, keresse meg a Kórházi vészhelyzetekre vonatkozó döntési támogatás munkaterületet, és kövesse az [Ütemezett frissítés konfigurálása](../refresh-scheduled-refresh.md) című cikkben ismertetett utasításokat.

## <a name="customize-and-share"></a>Testreszabás és megosztás

További információkért lásd: [Az alkalmazás testreszabása és megosztása](../service-template-apps-install-distribute.md#customize-and-share-the-app). Az alkalmazás közzététele és terjesztése előtt mindenképpen tekintse át a [jelentésekre vonatkozó jogi nyilatkozatokat](../create-reports/sample-covid-19-us.md#disclaimers).

## <a name="next-steps"></a>Következő lépések
* [Kríziskommunikáció-mintasablon beállítása és megismerése a Power Apps-ben](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
* [Mik azok a Power BI-sablonalkalmazások?](../service-template-apps-overview.md)
* [Sablonalkalmazások telepítése és terjesztése a vállalatnál](../service-template-apps-install-distribute.md)
