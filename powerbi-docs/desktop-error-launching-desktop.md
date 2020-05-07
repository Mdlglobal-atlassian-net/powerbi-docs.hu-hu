---
title: A Power BI Desktop indításával kapcsolatos hibák elhárítása
description: A Power BI Desktop indításával kapcsolatos hibák elhárítása
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 67c83f2cc0eb81e90f447961ed178a04e97e050e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160903"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Power BI Desktop megnyitásának hibaelhárítása

A Power BI Desktop esetében azok a felhasználók, akik a *Power BI helyszíni adatátjáró* korábbi verzióit telepítették és futtatják, esetenként nem tudják megnyitni a Power BI Desktopot a rendszergazdai szabályzatok korlátozásai miatt, amelyeket a Power BI helyszíni adatátjáró alkalmazott a helyi gép nevesített csöveire.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>A helyszíni adatátjáróval és a Power BI Desktoppal kapcsolatos hibák elhárítása

A helyszíni adatátjáróval kapcsolatos hibák elhárítására és a Power BI Desktop megnyitásának engedélyezésére három lehetőség létezik:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>1\. megoldás: A Power BI helyszíni adatátjáró legújabb verziójának telepítése

A Power BI helyszíni adatátjáró legújabb verziója nem helyez korlátozásokat a helyi gép nevesített csöveire, és engedi a Power BI Desktop megfelelő megnyitását. Ha továbbra is szeretné használni a Power BI helyszíni adatátjárót, javasoljuk, hogy frissítse. Töltse le a [Power BI helyszíni adatátjáró legújabb verzióját](https://go.microsoft.com/fwlink/?LinkId=698863). A hivatkozás egy, a futtatható telepítőre mutató közvetlen letöltési hivatkozás.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>2\. megoldás: A Power BI helyszíni adatátjáró Microsoft-szolgáltatás eltávolítása vagy leállítása

Ha már nincs szüksége rá, eltávolíthatja a Power BI helyszíni adatátjárót. Másik megoldásként leállíthatja a Power BI helyszíni adatátjáró Microsoft-szolgáltatást, ami eltávolítja a szabályzatkorlátozást, és engedélyezi a Power BI Desktop megnyitását.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>3\.megoldás: Futtassa a Power BI Desktopot rendszergazdai jogosultsággal

Harmadik lehetőségként rendszergazdai jogosultsággal is futtathatja a Power BI Desktopot, ami biztosítja annak sikeres megnyitását. Ekkor is javasolt azonban telepíteni a Power BI helyszíni adatátjáró legújabb verzióját, a korábban leírtaknak megfelelően.

A Power BI Desktop egy többfolyamatos architektúrával rendelkezik, amelynek számos folyamata Windows nevesített csövekkel kommunikál. Más folyamatok befolyásolhatják ezeket a nevesített csöveket. Az ilyen interferenciák leggyakoribb oka a biztonság, például azok a helyzetek, amelyekben a vírusirtó szoftver vagy a tűzfal letiltja a csöveket, vagy egy adott portra irányítja a forgalmat. Ha rendszergazdai jogosultsággal nyitja meg a Power BI Desktopot, az megoldhatja a problémát. Ha nem tudja megnyitni rendszergazdai jogosultsággal, kérje meg a rendszergazdát, hogy állapítsa meg, mely biztonsági szabályok gátolják meg a nevesített csövek kommunikációját. Ezután engedélyezőlistára teheti a Power BI Desktopot és annak alfolyamatait.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Az SQL Serverhez történő kapcsolódással összefüggő problémák megoldása

Ha egy SQL Server-adatbázishoz próbál csatlakozni, az alábbi szöveghez hasonló hibaüzenet jelenhet meg:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Erre gyakran megoldás lehet, ha a Power BI Desktopot rendszergazdaként nyitja meg az SQL Server-kapcsolat létrehozása előtt.

A Power BI Desktop rendszergazdai jogosultsággal való megnyitása és a kapcsolat létrehozása után a szükséges DLL-fájlok már megfelelően regisztrálva lesznek. Ezt követően már nem lesz rá szükség, hogy a Power BI Desktopot rendszergazda módban nyissa meg.

## <a name="get-help-with-other-launch-issues"></a>Segítség kérése más indítási problémákhoz

Igyekszünk a Power BI Desktop lehető legtöbb hibájára kitérni. Rendszeresen vizsgáljuk az olyan hibákat, amelyek több felhasználót is érintenek, és ezeket a cikkeinkben tárgyaljuk.

Ha a Power BI Desktop megnyitásával kapcsolatos hiba nem kapcsolódik a helyszíni adatátjáróhoz, vagy ha a fenti megoldások nem működnek, küldhet egy hibajegyet a *Power BI támogatási csapatának* (<https://support.powerbi.com>) a probléma azonosítása és megoldása érdekében.

Ha a jövőben más problémákba ütközik a Power BI Desktoppal kapcsolatban, hasznos lehet, ha bekapcsolja a nyomkövetést, és összegyűjti a naplófájlokat. A naplófájlok segíthetnek elkülöníteni és azonosítani a problémát. A nyomkövetés bekapcsolásához válassza a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** lehetőséget, válassza a **Diagnosztika** elemet, majd pedig a **Nyomkövetés engedélyezése** lehetőséget. Ennek a beállításnak a megadásához a Power BI Desktopnak futnia kell, ezért inkább a Power BI Desktop megnyitásával kapcsolatos jövőbeli problémák esetében lehet hasznos.
