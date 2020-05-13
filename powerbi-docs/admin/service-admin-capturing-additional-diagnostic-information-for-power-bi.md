---
title: További diagnosztikai adatok gyűjtése
description: A következő útmutatók két lehetséges módszert kínálnak további diagnosztikai adatok manuális begyűjtésére a Power BI-webügyféltől.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 670373afb5cb890c87a24a129cd43fde7bd5d892
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83128953"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>További diagnosztikai adatok gyűjtése a Power BI számára

Ez a cikk két lehetséges módszert kínál további diagnosztikai adatok manuális begyűjtésére a Power BI-webügyféltől.

1. Nyissa meg a [Power BI](https://app.powerbi.com)-t a Microsoft Edge-ben vagy az Internet Explorerben.

1. Nyomja le az **F12** billentyűt a Microsoft Edge fejlesztői eszközeinek megnyitásához.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközeinek Elemek lapjáról.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Válassza a **Hálózat** lapot. Itt látható az eddig rögzített forgalom.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközeinek Hálózat lapjáról.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    A következőket teheti:

    * Az ablakban böngészve minden felmerülő probléma reprodukálható.

    * A fejlesztői eszközök ablaka a munkamenet során bármikor megjeleníthető és elrejthető az F12 billentyű lenyomásával.

1. A munkamenet profilkészítésének leállításához válassza a piros négyzetet a fejlesztői eszközök terület **Hálózat** fülén.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközeinek Hálózat lapjáról kiemelt Leállítás gombbal.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Az adatok HTTP-archív (HAR-) fájlként való exportálásához válassza a lemez ikont.

   ![Képernyőkép a Microsoft Edge fejlesztői eszközeinek Hálózat lapjáról kiemelt lemez ikonnal.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Adjon nevet a HAR-fájlnak és mentse.

    A HAR-fájl minden információt tartalmaz a böngészőablak és a Power BI közötti hálózati kérelmekről, többek között a következőket:

    * Az egyes kérések tevékenységazonosítói.

    * Az egyes kérések pontos időbélyegzője.

    * Az ügyfélnek visszaadott hibaüzenetek.

    Tartalmazza a képernyőn megjelenő vizualizációk feltöltéséhez használt adatokat is.

1. A HAR-fájlt átadhatja vizsgálatra a támogatási szolgálatnak.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
