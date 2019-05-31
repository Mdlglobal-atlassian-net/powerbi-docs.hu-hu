---
title: A Power BI-tartalomcsomag (Azure AD B2B) külső vendég felhasználók megtekintése
description: Külső szervezet Önnel megosztott tartalmak megtekintéséhez Power BI-mobilalkalmazásokat használja.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: mshenhav
ms.openlocfilehash: a15da4349ce97e34c8321909abc862e424b2839c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61338699"
---
# <a name="view-power-bi-content-shared-with-you-from-an-external-organization"></a>A külső szervezet Önnel megosztott tartalom megtekintése a Power BI

A Power BI integrálható az Azure Active Directory-vállalatok (Azure AD B2B), hogy a Power BI-tartalmakat cégen kívüli biztonságos terjesztését. És külső vendégfelhasználóknak használhatja a Power BI mobilalkalmazásban a velük megosztott Power BI-tartalmak eléréséhez. 


A következőkre vonatkozik:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android rendszerű telefon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android rendszerű táblagép](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone-ok |iPadek |Android rendszerű telefonok |Android rendszerű táblagépek |

## <a name="accessing-shared-content"></a>A megosztott tartalom elérése

**Először meg kell adnia a külső szervezet megosztani egy elemet.** Ha valaki [elem megoszt Önnel](../../service-share-dashboards.md), ugyanazon a szervezeten belül vagy külső szervezet, kap egy e-mailt, amely a megosztott elem hivatkozását. A következő hivatkozás a mobileszközén megnyitása a Power BI mobilalkalmazásban. Ha az alkalmazás felismeri, hogy a cikk a külső szervezet megosztották, az alkalmazás újracsatlakozik a személyazonosság az adott szervezet. Az alkalmazás betölt, amely a szervezetben lévő Önnel megosztott összes elemet.

![Power bi-ban nyissa meg a megosztott elem, e-mailből ](./media/mobile-apps-b2b/mobile-b2b-open-item-email.png)

> [!NOTE]
> Ha ez az első elem, az Önnel megosztott, külső Vendég felhasználóként, meg kell jogcím egy böngészőben a meghívót. Nem igényelhet a meghívó a Power BI alkalmazásban.

Mindaddig, amíg egy külső szervezet csatlakozik, az alkalmazás egy fekete fejléc jelenik meg. Ez a fejléc jelzi, hogy nem csatlakozik a szervezet. Vissza a saját szervezethez csatlakozó, a Vendég módból való kilépés.

![A Power BI Vendég felhasználó fejléc](./media/mobile-apps-b2b/mobile-b2b-exit-home.png)

Annak ellenére, hogy a Power bi-ban való csatlakozáshoz külső szervezet, miután az alkalmazás vált összetevő hivatkozás van szüksége, az Önnel megosztott (nem csak az elem, nyithatók meg az e-mailben) összes elemet is elérheti. A külső szervezet elérheti az összes elem megtekintéséhez nyissa meg az alkalmazás menüjében, és válassza **velem megosztott**. A **alkalmazások** is használható alkalmazásokat kereshet.

![A Power BI alkalmazás menüjében Vendég külső felhasználóként](./media/mobile-apps-b2b/mobile-b2b-menu.png)

## <a name="limitations"></a>Korlátozások

- Feltételes hozzáférés és egyéb Intune-szabályzatok nem támogatottak az Azure AD B2B és a Power BI mobilalkalmazásban. Ez azt jelenti, hogy az alkalmazás kikényszeríti csak a saját szervezet szabályzatainak, ha vannak ilyenek.
- Leküldéses értesítések fogadott csak a szervezet helyről (még ha a felhasználó csatlakozik a külső szervezet vendégként). Nyissa meg az értesítést az alkalmazásnak, hogy a felhasználó otthoni szervezet webhelyén újra kapcsolódik a szolgáltatáshoz.
- Ha a felhasználó leállítja az alkalmazást, amikor újra megnyitni az alkalmazás automatikusan csatlakozik a felhasználó otthoni szervezete.
- Ha csatlakozik a külső szervezet, bizonyos műveletek le vannak-e tiltva: kedvenc elemmel, Adatriasztások megjegyzéseket és megosztása érdekében.
- Offline adatok nem érhető el, miközben külső szervezet csatlakozik.
- Ha a vállalati portál alkalmazás telepítve van az eszközén, majd az eszköz regisztrálva kell lenniük.
