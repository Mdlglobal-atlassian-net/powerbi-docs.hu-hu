---
title: Csatlakozás Power BI Premium-kapacitásmetrikákhoz
description: Hogyan telepíthető a Power BI Prémium kapacitásmetrikáinak sablonalkalmazása, és hogyan lehet csatlakozni az adatokhoz
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/18/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: fe54cedf7f8432d4a5e621256b9b77029f6b38a5
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692888"
---
# <a name="connect-to-power-bi-premium-capacity-metrics"></a>Csatlakozás Power BI Premium-kapacitásmetrikákhoz
A kapacitások figyelése elengedhetetlen a megalapozott döntések meghozatalához, hogy a prémium szintű kapacitás erőforrásait a legjobban használhassa ki. A kapacitások teljesítményéről a Power BI Premium kapacitásmetrikák alkalmazás nyújtja a legrészletesebb információkat.

![A Power BI Premium-kapacitásmetrikák alkalmazás jelentés](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-report.png)

Ez a cikk az alkalmazás telepítését és adatforrásokhoz csatlakoztatását ismerteti. A jelentés tartalmáról és használatáról további információt a [Prémium szintű kapacitások figyelése az alkalmazással](../service-admin-premium-monitor-capacity.md) című témakörben és a [Premium kapacitás metrikaalkalmazása blogbejegyzésében](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/) talál.

Miután telepítette az alkalmazást és csatlakoztatta az adatforrásokat, igény szerint testre szabhatja a jelentést. Ezután terjesztheti a szervezeti munkatársai között.

> [!NOTE]
> A sablonalkalmazások telepítéséhez [engedélyekre](./service-template-apps-install-distribute.md#prerequisites) van szükség. Ha nem rendelkezik megfelelő engedélyekkel, lépjen kapcsolatba a bérlő rendszergazdájával.

## <a name="install-the-app"></a>Az alkalmazás telepítse

1. Az alkalmazás beszerzéséhez kattintson a következő hivatkozásra: [A Power BI Premium-kapacitásmetrikák sablonalkalmazás](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Az alkalmazás AppSource-oldalán válassza az [**AZONNALI BESZERZÉS**](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt) lehetőséget.

    [![A Power BI Premium-kapacitásmetrikák alkalmazás az AppSource-on](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Válassza a **Telepítés** gombot. 

    ![A Power BI Premium-kapacitásmetrikák alkalmazás telepítése](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metric-select-install.png)

    > [!NOTE]
    > Ha korábban már telepítette az alkalmazást, a rendszer megkérdezi, hogy szeretné-e [felülírni a telepítést](./service-template-apps-install-distribute.md#update-a-template-app), vagy új munkaterületre szeretné azt telepíteni.

    A telepítést követően megtekintheti az alkalmazást az Alkalmazások oldalon.

   ![A Power BI Premium-kapacitásmetrikák alkalmazás az Alkalmazás oldalon](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Kapcsolódás adatforrásokhoz

1. Az alkalmazás megnyitásához kattintson az Alkalmazás oldalon lévő ikonra.

1. A kezdőképernyőn válassza a **Böngészés** lehetőséget.

   ![Sablonalkalmazás üdvözlőképernyője](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-splash-screen.png)

   Ekkor az alkalmazás megnyílik és mintaadatokat jelenít meg.

1. Kattintson az **Adatok csatlakoztatása** hivatkozásra az oldal tetején látható szalagcímen.

   ![A Power BI Premium-kapacitásmetrikák alkalmazás adatkapcsolat csatlakoztatása](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-connect-data.png)

1. A megjelenő párbeszédpanelen adja meg az UTC-eltérést, azaz az egyezményes világidő és a tartózkodási hely ideje közötti különbséget. Ezután kattintson a **Tovább** gombra.
  
   ![A Power BI Premium-kapacitásmetrikák alkalmazás, UTC-párbeszédablak beállítása](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-setutc-dialog.png)

1. A következő megjelenő párbeszédablakban semmit nem kell tennie. Mindössze válassza a **Bejelentkezés** lehetőséget.

   ![A Power BI Premium-kapacitásmetrikák alkalmazás, hitelesítési párbeszédablak](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-authentication-dialog.png)

1. A Microsoft bejelentkezési képernyőjén jelentkezzen be Power BI-ba.

   ![Microsoft bejelentkezési képernyő](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-microsoft-login.png)

   Miután bejelentkezett, a jelentés csatlakozik az adatforrásokhoz, és naprakész adatokkal töltődik fel. Eközben forog a tevékenységfigyelő.

   ![Power BI Premium-kapacitásmetrikák alkalmazás, frissítés folyamatban](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-refresh-monitor.png)

   A jelentés adatai naponta egyszer automatikusan frissülnek, kivéve, ha letiltotta ezt a bejelentkezési folyamat során. Lehetőség van [a frissítési ütemezés beállítására](./refresh-scheduled-refresh.md) is, hogy szükség szerint frissen tartsa a jelentésadatokat.

## <a name="customize-and-share"></a>Testreszabás és megosztás

Az alkalmazás testre szabásának megkezdéséhez kattintson a jobb felső sarokban található ceruza ikonra.

 ![Microsoft bejelentkezési képernyő](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-customize.png)

További információkért lásd: [Az alkalmazás testreszabása és megosztása](./service-template-apps-install-distribute.md#customize-and-share-the-app).

## <a name="next-steps"></a>Következő lépések
* [Prémium szintű kapacitások monitorozása az alkalmazással](../admin/service-admin-premium-monitor-capacity.md)
* [Premium-kapacitásmetrikák alkalmazás, blogbejegyzés](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/)
* [Mik azok a Power BI-sablonalkalmazások?](./service-template-apps-overview.md)
* [Sablonalkalmazások telepítése és terjesztése a vállalatnál](./service-template-apps-install-distribute.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)