---
title: Mik azok a Power BI-sablonalkalmazások?
description: Ez a cikk a Power BI sablonalkalmazási programjáról nyújt áttekintést. Ismerje meg, hogyan hozhat létre Power BI-alkalmazásokat kevés kódolással vagy anélkül, és hogyan helyezheti üzembe azokat bármely Power BI-ügyfél részére.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
ms.openlocfilehash: 3c508578b6438b0edfc3b4c9dfb7b724418894dd
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83307980"
---
# <a name="what-are-power-bi-template-apps"></a>Mik azok a Power BI-sablonalkalmazások?

A Power BI új *sablonalkalmazásai* lehetővé teszik a Power BI-partnerek részére, hogy kevés kódolással vagy anélkül hozzanak létre Power BI-alkalmazásokat, és helyezzék azokat üzembe a Power BI bármely ügyfele számára.  Ez a cikk a Power BI sablonalkalmazási programjáról nyújt áttekintést.

Power BI-partnerként létrehozhat használatra kész tartalmakat az ügyfeleinek, és közzéteheti azokat saját maga.  

Létrehozhat sablonalkalmazásokat, amelyeket az ügyfelei a fiókjukhoz kapcsolhatnak és példányosíthatnak. Tartományszakértőkként könnyen fogyaszthatóvá tehetik az adatokat az üzleti felhasználók számára.  

Beküldheti a sablonalkalmazásokat a Partnerközpontba. Az alkalmazások ezután nyilvánosan elérhetővé válnak a [Power BI-alkalmazások piacterén](https://app.powerbi.com/getdata/services) és a [Microsoft AppSource-on](https://appsource.microsoft.com/?product=power-bi). Íme egy magas szintű áttekintés a nyilvános sablonalkalmazás létrehozási folyamatáról.

## <a name="power-bi-apps-marketplace"></a>Power BI-alkalmazások piactere

A Power BI-sablonalkalmazások lehetővé teszik, hogy a Power BI Pro vagy a Power BI Premium felhasználói azonnal betekintést nyerjenek előre elkészített irányítópultokkal és jelentésekkel, amelyek élő adatforrásokhoz csatlakoztathatók. Számos Power BI-alkalmazás már elérhető a [Power BI-alkalmazások piacterén](https://app.powerbi.com/getdata/services).

|  |
|     :---:      |
| [![Microsoft Project-webalkalmazás](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp) [![Microsoft 365 Usage Analytics-webalkalmazás](./media/service-template-apps-overview/microsoft365-usage-analytics.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics) [![Dynamic 365 Business Central – értékesítési webalkalmazás](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales) [![Microsoft Forms Pro – ügyfél-elégedettségi webalkalmazás](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction) |
|  |

## <a name="process"></a>Folyamat
A sablonalkalmazások létrehozásának és beküldésének általános folyamata több lépésből áll. Egyes szakaszokhoz egyszerre több műveletet is el kell végezni.


| Szakasz | Power BI Desktop |  |Power BI szolgáltatásban  |  |Partnerközpont  |
|---|--------|--|---------|---------|---------|
| **Egy** | Hozzon létre egy adatmodellt és egy jelentést egy .pbix-fájlban |  | Hozzon létre egy munkaterületet. Importálja a .pbix-fájlt. Hozzon létre egy kiegészítő irányítópultot  |  | Regisztráljon partnerként |
| **Kettő** |  |  | Hozzon létre vizsgálati csomagot, és futtasson belső érvényesítést        |  | |
| **Három** | |  | Léptesse elő a vizsgálati csomagot az üzem előtti fázisba a Power BI-bérlőn kívüli ellenőrzéshez, és küldje el az AppSource-nak  |  | Az üzem előtti csomaggal hozzon létre egy sablonalkalmazás-ajánlatot a Power BI-ban, és indítsa el az ellenőrzési folyamatot |
| **Négy** | |  | Az üzem előtti csomag előléptetése üzemi csomaggá |  | Go Live |

## <a name="before-you-begin"></a>Előkészületek

A sablonalkalmazás létrehozásához engedély szükséges. Részletekért tekintse meg a Power BI felügyeleti portálján a sablonalkalmazás beállításait. 

Egy sablonalkalmazás Power BI szolgáltatásban és AppSource-ban történő közzétételéhez meg kell felelnie a [Partnerközpont kiadójává váláshoz](https://docs.microsoft.com/azure/marketplace/become-publisher) szükséges feltételeknek.
 
## <a name="high-level-steps"></a>Magas szintű lépések

Az alábbiakban a magas szintű lépésekről olvashat. 

1. [Tekintse át a követelményeket](#requirements), és győződjön meg róla, hogy teljesülnek. 

2. Hozzon létre egy jelentést a Power BI Desktopban. Használjon paramétereket, hogy menthesse olyan fájlként, amelyet mások használhatnak. 

3. Hozzon létre egy munkaterületet a sablonalkalmazáshoz a bérlőben a Power BI szolgáltatásban (app.powerbi.com). 

4. Importálja a .pbix-fájlt, és vegyen fel az alkalmazásába tartalmat, például irányítópultot. 

5. Hozzon létre egy vizsgálati csomagot, hogy tesztelhesse saját maga a sablonalkalmazást a szervezetben. 

6. Léptesse elő a tesztalkalmazást üzem előttivé, hogy elküldhesse az alkalmazást ellenőrzésre az AppSource-ban, és hogy tesztelhesse a saját bérlőjén kívül. 

7. Küldje be a tartalmat a [Partnerközpontba](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer) közzétételre. 

8. Tegye élővé az ajánlatot az AppSource-ban, és helyezze üzemi környezetbe az alkalmazást a Power BI-ban.

9. Most elkezdheti fejleszteni a következő verziót ugyanazon a munkaterületen az üzem előtti környezetben. 

## <a name="requirements"></a>Követelmények

A sablonalkalmazás létrehozásához engedély szükséges. Részletekért tekintse meg a Power BI [felügyeleti portálján a sablonalkalmazás beállításait](../admin/service-admin-portal.md#template-apps-settings).

Egy sablonalkalmazás Power BI szolgáltatásban és AppSource-ban történő közzétételéhez meg kell felelnie a [Partnerközpont kiadójává váláshoz](https://docs.microsoft.com/azure/marketplace/become-publisher) szükséges feltételeknek.
 > [!NOTE] 
 > Sablonalkalmazások beküldését a [Partnerközpontban](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer) lehet kezelni. A bejelentkezéshez használja ugyanazt a Microsoft Fejlesztői Központhoz tartozó fiókot. Az AppSource-ajánlatokhoz csak egy Microsoft-fiókkal kell rendelkeznie. A fiókok ne legyenek egyes szolgáltatásokhoz vagy ajánlatokhoz kötve.

## <a name="tips"></a>Tippek 

- Foglalja bele az alkalmazásba a mintaadatokat, hogy mindenki egyetlen kattintással kezdhessen. 
- Gondosan vizsgálja meg az alkalmazást úgy, hogy telepíti a bérlőjében és egy másodlagos bérlőben. Ellenőrizze, hogy az ügyfelek csak azt láthatják-e, amit szeretne, hogy lássanak. 
- Használja az AppSource-t online áruházként az alkalmazás tárolásához. Így mindenki megtalálja az alkalmazást, aki a Power BI-t használja. 
- Fontolja meg több sablonalkalmazás felajánlását különféle egyéni forgatókönyvekhez. 
- Engedélyezze az adatok testreszabását, támogassa például az egyéni kapcsolatokat és a paraméterek konfigurálását a telepítőprogramban.

További javaslatokért lásd: [Tippek sablonalkalmazások készítéséhez a Power BI-ban](service-template-apps-tips.md).

## <a name="known-limitations"></a>Ismert korlátozások

| Funkció | Ismert korlátozás |
|---------|---------|
|Tartalom:  Adathalmazok   | Pontosan egy adatkészletnek kell jelen lennie. Csak a Power BI Desktopban (.pbix-fájlok) készült adatkészletek használata engedélyezett. <br>Nem támogatott: Más sablonalkalmazásokból származó adatkészletek, munkaterületeken átnyúló adatkészletek, lapszámozott jelentések (.rdl-fájlok), Excel-munkafüzetek |
|Tartalom: Irányítópultok | A valós idejű csempék nem engedélyezettek (más szóval nem támogatott a leküldéses vagy a folyamatos átvitelű adatkészlet) |
|Tartalom: Adatfolyamok | Nem támogatott: Adatfolyamok |
|Fájlok tartalmai | Csak a PBIX-fájlok engedélyezettek. <br>Nem támogatott: .rdl-fájlok (lapszámozott jelentések), Excel-munkafüzetek   |
| Adatforrások | A felhőbeli ütemezett adatfrissítéshez támogatott adatforrások engedélyezettek. <br>Nem támogatott: <li> DirectQuery</li><li>Élő kapcsolatok (nem Azure AS)</li> <li>Helyszíni adatforrások (a személyes és a vállalati átjárók nem támogatottak)</li> <li>Valós idejű (a leküldéses adatkészlet nem támogatott)</li> <li>Összetett modellek</li></ul> |
| Adatkészlet: munkaterületeken átnyúló | Munkaterületeken átnyúló adatkészletek használata nem engedélyezett  |
| Lekérdezési paraméterek | Nem támogatott: „Any” típusú paraméterek vagy „Binary” típusú blokkfrissítési művelet az adatkészlethez |
| Power BI-vizualizációk | Csak a nyilvánosan elérhető Power BI-vizualizációk támogatottak. A [céges Power BI-vizualizációk](../developer/visuals/power-bi-custom-visuals-organization.md) nem támogatottak |
| Független felhők | A sablonalkalmazások nem elérhetők független felhőkben |

## <a name="support"></a>Támogatás
Ha a fejlesztési fázisban van szüksége támogatásra, használja a következő webhelyet: [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Ezt a webhelyet a Microsoft aktívan figyeli és felügyeli. Az ügyfélincidensek gyorsan eljutnak a megfelelő csapathoz.

## <a name="next-steps"></a>Következő lépések

[Sablonalkalmazás létrehozása](service-template-apps-create.md)
