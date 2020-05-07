---
title: Power BI-adatok védelme az eszközök natív azonosításával
description: Megtudhatja, hogyan konfigurálhatja úgy az iOS- vagy Android-alkalmazást, hogy az további azonosítást követeljen meg a Power BI-adatok eléréséhez
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: painbar
ms.openlocfilehash: ce7b3c3bc667023ef36650d8c551caaceab04c02
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "80802801"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-passcode-or-biometric-data"></a>A Power BI alkalmazás védelme a Face ID, a Touch ID, hitelesítő kód vagy biometriai adatok használatával 

A Power BI-ban kezelt adatok sok esetben bizalmasak, így védelemre van szükségük, hogy csak engedéllyel rendelkező felhasználók férhessenek hozzá. 

Az iOS és az Android rendszerhez készült Power BI alkalmazásban további azonosítási beállítások konfigurálásával védheti meg az adatait. Így az alkalmazás minden alkalommal megköveteli az azonosítást, amikor elindul vagy előtérbe kerül. iOS rendszeren ez Face ID, Touch ID vagy hitelesítő kód megadását jelenti. Android rendszeren ez biometriai adatok (ujjlenyomat-azonosító) megadását jelenti.

Hatóköre:

| ![iPhone](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![iPadek](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![Android rendszerű telefon](././media/mobile-native-secure-access/android-logo-40-px.png) | ![Android rendszerű táblagép](././media/mobile-native-secure-access/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone-ok |iPadek |Android rendszerű telefonok |Android-táblagépek |

## <a name="turn-on-face-id-touch-id-or-passcode-on-ios"></a>A Face ID, a Touch ID vagy a hitelesítő kód bekapcsolása iOS rendszeren

Az iOS rendszerhez készült Power BI mobilalkalmazás további azonosítási beállításainak használatához lépjen az **Adatvédelem és biztonság** terület alkalmazásbeállításaira. Itt láthatók a Face ID, a Touch ID és a hitelesítő kód bekapcsolására vonatkozó beállítások. A megjelenő lehetőségek az eszköz adottságaitól függnek.

![Az iOS Power BI alkalmazásbeállításainak lapja](./media/mobile-native-secure-access/mobile-ios-native-secured-setting.png)

A beállítás bekapcsolása esetén az alkalmazás minden elindításakor vagy előtérbe hívásakor meg kell adnia a megfelelő azonosító adatokat.

Az azonosító típusa, amelynek a rendszer a megadását kéri, az eszköz képességeitől függ. Ha az eszköz támogatja a Face ID-t, azt kell használnia. Ha az eszköz támogatja a Touch ID-t, azt kell használnia. Ha egyiket sem támogatja, hitelesítő kódot kell alkalmaznia. Az alábbi ábra a Face ID hitelesítési képernyőt mutatja be.

![iOS Power BI Face ID](./media/mobile-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="turn-on-biometric-data-fingerprint-id-on-android"></a>Biometriai adatok (ujjlenyomat-azonosító) bekapcsolása Android rendszeren

Az Android rendszerhez készült Power BI mobilalkalmazás további azonosítási beállításainak használatához lépjen az **Adatvédelem és biztonság** terület alkalmazásbeállításaira. Itt található a biometriai adatok bekapcsolásának lehetősége.

![Az androidos Power BI alkalmazásbeállításainak lapja](./media/mobile-native-secure-access/mobile-android-native-secured-setting.png)

A beállítás bekapcsolása esetén az alkalmazás minden elindításakor vagy előtérbe hívásakor meg kell adnia a biometriai adatokat (ujjlenyomat-azonosító).

Az alábbi ábra az ujjlenyomat-hitelesítési képernyőt mutatja be.

![iOS Power BI Face ID](./media/mobile-native-secure-access/mobile-android-native-secured-fingerprint-id.png)

>[!NOTE]
>A mobilalkalmazás Biometrikus hitelesítés megkövetelése beállításának használatához először be kell állítania a biometriát az Android-eszközön. Ha az eszköz nem támogatja a biometriát, nem tudja ezzel a mobilalkalmazás-beállítással védeni a Power BI-adatokhoz való hozzáférést.
>
>Ha a rendszergazda [távolról bekapcsolta a biztonságos hozzáférést](#mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app) a mobilalkalmazásban, az alkalmazás eléréséhez be kell kapcsolnia az eszközön a biometriát, ha még nem tette meg. Ha az eszköz nem támogatja a biometriát, a távoli beállítás Önt nem érinti. A mobilalkalmazáshoz való hozzáférés továbbra sem lesz biztonságos.

## <a name="mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app"></a>A Power BI mobilalkalmazás biztonságos elérésének MDM általi megkövetelése

Egyes szervezetek olyan biztonsági szabályzatokkal és megfelelőségi követelményekkel rendelkeznek, amelyek további azonosítást tesznek kötelezővé a bizalmas üzleti adatok eléréséhez.

Ennek támogatására az Power BI mobilalkalmazással a rendszergazdák leküldhetik az alkalmazáskonfigurációs beállításokat a Microsoft Intune-ból és egyéb mobileszköz-kezelési (MDM-) megoldásból, így vezérelhetik a mobilalkalmazás biztonságos elérését. A rendszergazdák az alkalmazásvédelmi szabályzattal kapcsolhatják be ezt a beállítást az összes felhasználónak vagy csak egyes csoportoknak. Erről a [Power BI mobilalkalmazás távoli konfigurálása MDM használatával](mobile-app-configuration.md#data-protection-settings-ios-and-android) című cikk ír részletesebben.

## <a name="next-steps"></a>További lépések
* [Power BI mobilalkalmazás távoli konfigurálása MDM használatával](mobile-app-configuration.md)
