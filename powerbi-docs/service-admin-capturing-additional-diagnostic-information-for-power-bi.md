---
title: További diagnosztikai adatok rögzítése
description: A következő útmutatók két lehetséges módszert kínálnak további diagnosztikai adatok manuális begyűjtésére a Power BI-webügyféltől.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100260"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>A Power bi további diagnosztikai adatok rögzítése

Ez a cikk útmutatást manuálisan további diagnosztikai adatok gyűjtését a Power BI webes ügyféllel.

1. Keresse meg a [Power bi-ban](https://app.powerbi.com) a Microsoft Edge vagy az Internet Explorerben.

1. Nyomja meg **F12** , nyissa meg a Microsoft Edge fejlesztői eszközeit.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközök elemek lap.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Válassza a **Hálózat** lapot. Itt látható az eddig rögzített forgalom.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközök hálózati lap.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    A következőket teheti:

    * Keresse meg az időtartamon belül, és bármely olyan probléma reprodukálásához.

    * Elrejtése és megjelenítése a fejlesztői eszközök ablaka a munkamenet során bármikor F12 billentyű lenyomásával.

1. Profilkészítés a munkamenet leállításához is kijelölheti a piros négyzetet a **hálózati** lapján a fejlesztői eszközök terület.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközök hálózati lap kívül a leállítási gomb-hívással.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. A lemez ikonra exportálhatja az adatokat egy HTTP-archívum (HAR) fájlba.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközök hálózati lap egy képfelirattal, a lemez ikonra.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Adjon nevet a HAR-fájlnak és mentse.

    A HAR-fájl a böngészőablakot, és többek között a Power BI közötti hálózati kérelmekről minden információt tartalmaz:

    * A tevékenység azonosítók az egyes kérések.

    * Az egyes kérések pontos időbélyegét.

    * Hiba információt küld vissza az ügyfélnek.

    Tartalmazza a képernyőn megjelenő vizualizációk feltöltéséhez használt adatokat is.

1. A HAR-fájlt átadhatja vizsgálatra a támogatási szolgálatnak.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
