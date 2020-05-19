---
title: A Microsoft Sustainability Calculator csatlakoztatása
description: Microsoft Sustainability Calculator a Power BI-hoz
author: joshthor3222
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/06/2020
ms.author: v-tikid
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ab3dbb500faf072b87ba398b16b820c164cdefa
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83337604"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>A Microsoft Sustainability Calculator csatlakoztatása
Betekintést nyerhet az informatikai infrastruktúrája szén-dioxid-kibocsátásába, és fenntarthatóbb informatikai döntéseket hozhat.

A Microsoft Sustainability Calculator új megállapításokat nyújt az Azure-szolgáltatásokhoz kapcsolódó szén-dioxid-kibocsátási adatokról. A szervezet fenntarthatóságáért és a fenntarthatósági jelentések készítéséért felelős munkatársak mostantól számszerűsíthetik az egyes Azure-előfizetésekhez kapcsolódó szén-dioxid-kibocsátást, továbbá azt, hogy az adott számítási feladatok mennyivel kevesebb szén-dioxid-kibocsátás mellett futtathatók az Azure-ban a helyszíni adatközpontokhoz képest. Ezek az adatok felhasználhatók az üvegházhatású gázok 3. hatókörű kibocsátásának jelentéséhez. A Microsoft Sustainability Calculator eléréséhez szükség van a bérlőazonosítóra és a hozzáférési kulcsra, amely általában a szervezet Azure-rendszergazdájánál érhető el.

Az alkalmazás használatához az Azure Enterprise Portalról származó információkra van szükség. A vállalati rendszergazdák segíthetnek ezen információk beszerzésében. Az alkalmazás telepítése előtt tekintse át ezeket az utasításokat, és szerezze be a szükséges információkat. 

Az összekötő ezen verziója csak a [https://ea.azure.com](https://ea.azure.com/) címről történő vállalati regisztrációkat támogatja. A Kínából történő belépések jelenleg nem támogatottak.

## <a name="how-to-connect"></a>Csatlakozás
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. Válassza a **Microsoft Sustainability Calculator** \> **Letöltés most** lehetőséget.
1. A **Telepíti ezt a Power BI-alkalmazást?** területen válassza a **Telepítés** lehetőséget.
1. Az **Alkalmazások** panelen válassza a **Microsoft Sustainability Calculator** csempét.
1. **Az új alkalmazás használatának első lépései** résznél válassza az **Csatlakozás** lehetőséget.

    ![Első lépések az új alkalmazással](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. Adja meg a **vállalat nevét, a felhasználói regisztráció számát** és a **hónapok számát \> Bejelentkezés**. A [paraméterek fellelhetőségével](#finding-parameters) kapcsolatos információt lásd alább.

    ![Vállalati regisztráció](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. A **Hitelesítési módszer** értékeként válassza a **Kulcs** lehetőséget, az **Adatvédelem szintje** pedig legyen **Szervezeti**.
1. A **Kulcs** beállításhoz adja meg a **hozzáférési kulcsot \> Bejelentkezés**.

    ![Hozzáférési kulcs megadása](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. Az importálás automatikusan megkezdődik. Ha befejeződött, a **navigációs ablaktáblán** megjelenik egy új irányítópult, jelentés és modell. Az importált adatok megtekintéséhez válassza ki a jelentést.

## <a name="finding-parameters"></a>Paraméterek helye

A vállalati **regisztrációs azonosító** és a **hozzáférési kulcs** megkereséséhez a szükséges információk beszerzéséhez működjön együtt az Azure-rendszergazdával. A rendszergazda

1. bejelentkezik az [Azure Enterprise Portalra](https://ea.azure.com), a bal oldali menüszalag **Kezelés** elemére kattint, és beszerzi a **regisztrációs számot** az alábbiakban látható módon.
2. Az [Azure Enterprise Portalon](https://ea.azure.com) a **Jelentések**, majd az API-hozzáférési kulcs lehetőségre kattint az alábbiakban látható módon az elsődleges regisztrációs fiókkulcs beszerzéséhez.

## <a name="using-the-app"></a>Az alkalmazás használata

Ha bármikor frissíteni szeretné a paramétereket, navigáljon az **Adathalmaz** beállításaihoz, nyissa meg az alkalmazás-munkaterülethez társított adatokat, és frissítse a bérlőazonosítót, a vállalat nevét vagy az adatok hónapját. A paraméterek alkalmazása után kattintson a **Frissítés** lehetőségre. Ezzel újratöltheti az adatokat az új paraméterekkel.