---
title: Mik azok a Power BI-sablonalkalmazások? (előzetes verzió)
description: Ez a cikk a Power BI sablonalkalmazási programjáról nyújt áttekintést. Ismerje meg, hogyan hozhat létre Power BI-alkalmazásokat kevés kódolással vagy anélkül, és hogyan helyezheti üzembe azokat bármely Power BI-ügyfél részére.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: maggies
ms.openlocfilehash: 445f5f087bd9589b18f798e8db40a63b0ddceafe
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249994"
---
# <a name="what-are-power-bi-template-apps-preview"></a>Mik azok a Power BI-sablonalkalmazások? (előzetes verzió)

A Power BI új *sablonalkalmazásai* lehetővé teszik a Power BI-partnerek részére, hogy kevés kódolással vagy anélkül hozzanak létre Power BI-alkalmazásokat, és helyezzék azokat üzembe a Power BI bármely ügyfele számára.  Ez a cikk a Power BI sablonalkalmazási programjáról nyújt áttekintést.

A sablonalkalmazások a jelenlegi szolgáltatás-tartalomcsomagokat helyettesítik. Power BI-partnerként létrehozhat használatra kész tartalmakat az ügyfeleinek, és közzéteheti azokat saját maga.  

Létrehozhat sablonalkalmazásokat, amelyeket az ügyfelei a fiókjukhoz kapcsolhatnak és példányosíthatnak. Tartományszakértőkként könnyen fogyaszthatóvá tehetik az adatokat az üzleti felhasználók számára.  

Beküldheti a partner által készített sablonalkalmazásokat a Cloud Partner Portalra. Az alkalmazások ekkor nyilvánosan elérhetővé válnak a Power BI alkalmazáskatalógusában (app.powerbi.com/getdata/services) és a Microsoft AppSource-ban (appsource.microsoft.com). Íme egy példa a nyilvános sablonalkalmazás felhasználói felületére.  

## <a name="overview"></a>Áttekintés
A sablonalkalmazások fejlesztésének és elküldésének általános eljárása több szakaszból áll, melyek közül néhány egyszerre több tevékenység végzésével jár.


| Szakasz | Power BI Desktop |  |Power BI szolgáltatásban  |  |Cloud Partner Portal  |
|---|--------|--|---------|---------|---------|
| **Egy** | Hozzon létre egy adatmodellt és egy jelentést egy .pbix-fájlban |  | Hozzon létre egy munkaterületet. Importálja a .pbix-fájlt. Hozzon létre egy kiegészítő irányítópultot  |  | Regisztráljon partnerként |
| **Kettő** |  |  | Hozzon létre vizsgálati csomagot, és futtasson belső érvényesítést        |  | |
| **Három** | |  | Léptesse elő a vizsgálati csomagot az üzem előtti fázisba a Power BI-bérlőn kívüli ellenőrzéshez, és küldje el az AppSource-nak  |  | Az üzem előtti csomaggal hozzon létre egy sablonalkalmazás-ajánlatot a Power BI-ban, és indítsa el az ellenőrzési folyamatot |
| **Négy** | |  | Az üzem előtti csomag előléptetése üzemi csomaggá |  | Go Live |

## <a name="requirements"></a>Követelmények

A sablonalkalmazás létrehozásához engedély szükséges. Részletekért tekintse meg a Power BI felügyeleti portálján a sablonalkalmazás beállításait. 

Egy sablonalkalmazás Power BI szolgáltatásban és AppSource-ban történő közzétételéhez meg kell felelnie a [felhőbeli piactér kiadójává váláshoz](https://docs.microsoft.com/azure/marketplace/become-publisher) szükséges feltételeknek.
 
## <a name="high-level-steps"></a>Magas szintű lépések

Az alábbiakban a magas szintű lépésekről olvashat. 

1. [Tekintse át a követelményeket](#requirements), és győződjön meg róla, hogy teljesülnek. 

1. Hozzon létre egy jelentést a Power BI Desktopban. Használjon paramétereket, hogy menthesse olyan fájlként, amelyet mások használhatnak. 

1. Hozzon létre egy munkaterületet a sablonalkalmazáshoz a bérlőben a Power BI szolgáltatásban (app.powerbi.com). 

1. Importálja a .pbix-fájlt, és vegyen fel az alkalmazásába tartalmat, például irányítópultot. 

1. Hozzon létre egy vizsgálati csomagot, hogy tesztelhesse saját maga a sablonalkalmazást a szervezetben. 

1. Léptesse elő a tesztalkalmazást üzem előttivé, hogy elküldhesse az alkalmazást ellenőrzésre az AppSource-ban, és hogy tesztelhesse a saját bérlőjén kívül. 

1. Küldje el a tartalmat a Cloud Partner Platformra a közzétételhez. 

1. Tegye élővé az ajánlatot az AppSource-ban, és helyezze üzemi környezetbe az alkalmazást a Power BI-ban.
2. Most elkezdheti fejleszteni a következő verziót ugyanazon a munkaterületen az üzem előtti környezetben. 

## <a name="requirements"></a>Követelmények

A sablonalkalmazás létrehozásához engedély szükséges. Részletekért tekintse meg a Power BI [felügyeleti portálján a sablonalkalmazás beállításait](service-admin-portal.md#template-apps-settings-preview). 

Egy sablonalkalmazás Power BI szolgáltatásban és AppSource-ban történő közzétételéhez meg kell felelnie a [felhőbeli piactér kiadójává váláshoz](https://docs.microsoft.com/azure/marketplace/become-publisher) szükséges feltételeknek.

## <a name="tips"></a>Tippek 

- Foglalja bele az alkalmazásba a mintaadatokat, hogy mindenki egyetlen kattintással kezdhessen. 
- Gondosan vizsgálja meg az alkalmazást úgy, hogy telepíti a bérlőjében és egy másodlagos bérlőben. Ellenőrizze, hogy az ügyfelek csak azt láthatják-e, amit szeretne, hogy lássanak. 
- Használja az AppSource-t online áruházként az alkalmazás tárolásához. Így mindenki megtalálja az alkalmazást, aki a Power BI-t használja. 
- Fontolja meg több sablonalkalmazás felajánlását különféle egyéni forgatókönyvekhez. 
- Engedélyezze az adatok testreszabását, támogassa például az egyéni kapcsolatokat és a paraméterek konfigurálását a telepítőprogramban.

További javaslatokért lásd: [Tippek sablonalkalmazások készítéséhez a Power BI-ban (előzetes verzió)](service-template-apps-tips.md).

## <a name="support"></a>Támogatás
Ha a fejlesztési fázisban van szüksége támogatásra, használja a következő webhelyet: [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Ezt a webhelyet a Microsoft aktívan figyeli és felügyeli. Az ügyfélincidensek gyorsan eljutnak a megfelelő csapathoz.

## <a name="next-steps"></a>Következő lépések

[Sablonalkalmazás létrehozása](service-template-apps-create.md)