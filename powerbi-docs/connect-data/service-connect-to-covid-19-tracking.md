---
title: Csatlakozás a COVID-19 USA-beli nyomon követésére szolgáló jelentéshez
description: A COVID-19 US Cases sablonalkalmazás telepítése és csatlakozás az adatokhoz.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/05/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 97e0a4f6e522997e6f132d1c3dbc493188ba66ba
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275478"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>Csatlakozás a COVID-19 USA-beli nyomon követésére szolgáló jelentéshez
Ez a cikk a COVID-19 nyomon követésére szolgáló jelentés sablonalkalmazásának telepítését és az adatforrásokhoz való csatlakozást ismerteti.

![A COVID-19 USA-beli nyomon követésére szolgáló jelentés](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

Magáról a jelentésről a felelősséget kizáró nyilatkozatokat és az adatokkal kapcsolatos információkat is tartalmazó a [COVID-19-nyomonkövetési minta az USA tagállami és helyi szintű közigazgatási szervei részére](../create-reports/sample-covid-19-us.md) című cikk nyújt részletes tájékoztatást.

Miután telepítette a sablonalkalmazást, és csatlakoztatta az adatforrásokat, igényei szerint testre szabhatja a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

## <a name="install-the-app"></a>Az alkalmazás telepítse

1. Az alkalmazás beszerzéséhez kattintson a következő hivatkozásra: [A COVID-19 USA-beli nyomon követésére szolgáló jelentés sablonalkalmazása](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms)

1. Az alkalmazás AppSource-oldalán kattintson az [**LETÖLTÉS MOST**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms) elemre.

    [![A Covid-19 USA-beli nyomon követésére szolgáló jelentés az AppSource-on](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms)

1. Amikor a rendszer kéri, kattintson a **Telepítés** gombra. A telepítést követően megtekintheti az alkalmazást az Alkalmazások oldalon.

   ![A COVID-19 USA-beli nyomon követésére szolgáló jelentés az Alkalmazások oldalon](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Kapcsolódás adatforrásokhoz

1. Az alkalmazás megnyitásához válassza az Alkalmazás oldalon lévő ikont.

1. A megjelenő üdvözlőképernyőn válassza a **Csatlakozás** lehetőséget.

   ![Sablonalkalmazás üdvözlőképernyője](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-splash-screen.png)

1. Két bejelentkezési párbeszédpanel nyílik meg egymás után. Az adatvédelmi szintet mindkettőn állítsa Nyilvánosra.

   ![A Covid-19 USA-beli nyomon követésére szolgáló jelentés bejelentkezési párbeszédpanelje](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)

   A jelentés csatlakozik az adatforrásokhoz, és naprakész adatokkal lesz feltöltve. Eközben forogni fog a tevékenységfigyelő.

   ![A COVID-19 USA-beli nyomon követésére szolgáló jelentés frissítése folyamatban van](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Jelentés frissítésének ütemezése

Amikor az adatfrissítés befejeződött, az alkalmazáshoz tartozó munkaterületre kerül. [Állítson be frissítési ütemezést](../connect-data/refresh-scheduled-refresh.md) a jelentés adatainak naprakészen tartásához.

## <a name="customize-and-share"></a>Testreszabás és megosztás

További információkért lásd: [Az alkalmazás testreszabása és megosztása](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app). Az alkalmazás közzététele és terjesztése előtt mindenképpen tekintse át a [jelentésekre vonatkozó jogi nyilatkozatokat](../create-reports/sample-covid-19-us.md#disclaimers).

## <a name="next-steps"></a>Következő lépések
* [COVID-19-nyomonkövetési minta az USA tagállami és helyi szintű közigazgatási szervei részére](../create-reports/sample-covid-19-us.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
* [Mik azok a Power BI-sablonalkalmazások?](../connect-data/service-template-apps-overview.md)
* [Sablonalkalmazások telepítése és terjesztése a vállalatnál](../connect-data/service-template-apps-install-distribute.md)
