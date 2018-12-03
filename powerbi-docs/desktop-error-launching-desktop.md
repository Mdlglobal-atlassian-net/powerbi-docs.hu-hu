---
title: A Power BI Desktop indítási hibáinak elhárítása
description: A Power BI Desktop indítási hibáinak elhárítása
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 78cfcd51a951095353ce5d0f25c4511cc720c632
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578221"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>A Power BI Desktop meghiúsult indulásával kapcsolatos hibák elhárítása
A **Power BI Desktop** esetében azok a felhasználók, akik a **Power BI helyszíni adatátjáró** korábbi verzióit telepítették és futtatják, esetenként nem tudják elindítani a Power BI Desktopot a rendszergazdai szabályzatok korlátozásai miatt, amelyeket a Power BI helyszíni adatátjáró alkalmazott a helyi gép nevesített csöveire. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>A helyszíni adatátjáróval és a Power BI Desktoppal kapcsolatos hibák elhárítása
A helyszíni adatátjáróval kapcsolatos hibák elhárítására és a Power BI Desktop indításának engedélyezésére három lehetőség létezik:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>1. megoldás: A Power BI helyszíni adatátjáró legújabb verziójának telepítése
A Power BI helyszíni adatátjáró legújabb verziója nem helyez korlátozásokat a helyi gép nevesített csöveire, és engedi a Power BI Desktop megfelelő indítását. Ha továbbra is szeretné használni a Power BI helyszíni adatátjárót, ezt a megoldást ajánlott alkalmazni. A Power BI helyszíni adatátjáró legújabb verzióját [innen](https://go.microsoft.com/fwlink/?LinkId=698863) töltheti le. Megjegyzés: a hivatkozás egy, a futtatható telepítőre mutató közvetlen letöltési hivatkozás.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>2. megoldás: A Power BI helyszíni adatátjáró Windows-szolgáltatás eltávolítása vagy leállítása
Ha már nincs szüksége a Power BI helyszíni adatátjáróra, eltávolíthatja vagy leállíthatja ezt a Windows-szolgáltatást, így a szabályzat korlátozási is megszűnnek, és a Power BI Desktop indíthatóvá válik.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>3.megoldás: Futtassa a Power BI Desktopot rendszergazdai jogosultsággal
Harmadik lehetőségként rendszergazdai jogosultsággal is futtathatja a Power BI Desktopot, ami biztosítja annak sikeres indítását. Ekkor is javasolt azonban telepíteni a Power BI helyszíni adatátjáró legújabb verzióját, a cikkben korábban leírtaknak megfelelően.

Fontos észben tartani, hogy a Power BI Desktop egy többfolyamatos architektúrával rendelkezik, amelynek számos folyamata Windows nevesített csövekkel kommunikál. Más folyamatok befolyásolhatják ezeket a nevesített csöveket. Az ilyen interferenciák leggyakoribb oka a biztonság, például azok a helyzetek, amelyekben a vírusirtó szoftver vagy a tűzfal letiltja a csöveket, vagy egy adott portra irányítja a forgalmat. Ha rendszergazdai jogosultsággal indítja el a Power BI Desktopot, az megoldhatja a problémát. Ha ez nem lehetséges, forduljon a rendszergazdához, és kérdezze meg, mely biztonsági szabályok gátolják meg a nevesített csövek megfelelő kommunikációját, valamint kérje meg, hogy helyezze engedélyezőlistára a Power BI Desktopot és annak részfolyamatait.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Az SQL Serverhez történő kapcsolódással összefüggő problémák megoldása
Ha a következőhöz hasonló hibaüzenettel találkozik, amikor SQL Server-adatbázishoz csatlakozik, a problémát legtöbbször megoldja, ha a **Power BI Desktopot** rendszergazda-módban indítja el, és csak ezután hozza létre az SQL Server-kapcsolatot:

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

A rendszergazda módban való indítás és a kapcsolat létrehozása után a szükséges DLL-fájlok már megfelelően regisztrálva lesznek. Ezt követően már nem lesz rá szükség, hogy a Power BI Desktopot rendszergazda módban indítsa el.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>A Power BI Desktop egyéb indítási hibáival kapcsolatos támogatás
Igyekszünk a **Power BI Desktop** lehető legtöbb hibájára kitérni. Rendszeresen vizsgáljuk az olyan hibákat, amelyek több felhasználót is érintenek, és ezeket a cikkeinkben tárgyaljuk.

Ha a **Power BI Desktop** indításával kapcsolatos hiba nem kapcsolódik a helyszíni adatátjáróhoz, vagy ha a fenti megoldások nem működnek, küldhet egy hibajegyet a [Power BI támogatási csapatának](https://support.powerbi.com) (https://support.powerbi.com)) a probléma azonosítása és megoldása érdekében.

A **Power BI Desktoppal** kapcsolatos egyéb esetleges jövőbeli hibák esetén (reményeink szerint ilyenek nem, vagy csak elvétve akadnak majd), hasznosnak bizonyulhat a nyomkövető és gyűjtő naplófájlok bekapcsolása a problémák hatékonyabb elkülönítése és azonosítása érdekében. A nyomkövetés bekapcsolásához válassza a **Fájl > Lehetőségek és beállítások > Beállítások**, majd a **Diagnosztika** lehetőséget, és jelölje be a **Nyomkövetés engedélyezése** beállítást a *Diagnosztikai beállítások* területen. Tisztában vagyunk vele, hogy ennek a beállításnak a megadásához a **Power BI Desktopnak** futnia kell, ezért inkább a **Power BI Desktop** indításával kapcsolatos jövőbeli problémák esetében lehet hasznos.

