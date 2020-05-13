---
title: Engedélyezési listára helyezendő Power BI URI-címek
description: Ez a cikk a Power BI esetében a biztonságos kapcsolatok listájára felvehető URL-végpontokat és portokat sorolja fel.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.custom: seodec18
ms.openlocfilehash: 1426cb2926641ca93bcbff3e55ea151f829f290a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83129678"
---
# <a name="power-bi-urls-for-whitelisting"></a>Engedélyezési listára helyezendő Power BI URI-címek
[//]: # "suparnap és miwehnia a lista fenntartásáért felelős kapcsolattartók"

A Power BI SaaS (szolgáltatott szoftver) alkalmazás néven is ismert **online Power BI szolgáltatáshoz** internetkapcsolatra van szükség. Az online Power BI szolgáltatást használó ügyfeleknek el kell érniük az alábbi végpontokat.

A Power BI online szolgáltatás használatához tudnia kell csatlakozni az alábbi táblázatokban **kötelezőként** megjelölt végpontokhoz, és a hivatkozott webhelyeken **kötelezőként** megjelölt végpontokhoz is. Ha egy külső webhelyre mutató hivatkozás egy adott bekezdésre mutat, akkor csak az abban a bekezdésben lévő végpontokat kell megvizsgálnia.

Bizonyos funkciók működése érdekében a **választhatóként** megjelölt végpontok is **szerepelhetnek az engedélyezési listán**.

Az online Power BI szolgáltatás csak a 443-as TCP-port megnyitását igényli a felsorolt végpontokhoz.

A helyettesítő karakterek (*) a gyökértartomány alatti összes szintet jelentik. Ha nincs elérhető információ, azt az N/A jelölés mutatja. A **Cél(ok)** oszlop teljes tartománynevek/tartományok listája, és olyan külső webhelyekre hivatkozik, amelyek további információkat tartalmaznak a végpontokról.

>[!Important]
>Az alábbi táblázatok információi nem vonatkoznak az **Egyesült államok kormányzati felhőszolgáltatására**, **a németországi felhőre** és a **kínai felhőre**.

## <a name="authentication"></a>Hitelesítés

A Power BI működése függ az Office 365 hitelesítés és identitás szakaszban feltüntetett végpontoktól. A Power BI használatához tudnia kell csatlakozni az alább hivatkozott webhelyen található végpontokhoz.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Kötelező:** Hitelesítés és identitás | Tekintse meg az [Office Online szolgáltatást és a közös URL-címeket](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) bemutató Office 365-dokumentációt  | N.A. |

## <a name="general-site-usage"></a>Általános webhelyhasználat

A Power BI használatához tudnia kell csatlakozni az alábbi táblázatban és a hivatkozott webhelyeken megadott végpontokhoz.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Kötelező:** Háttérbeli API-k | *.analysis.windows.net | TCP 443 |
| 2 | **Kötelező:** Háttérbeli API-k | *.pbidedicated.windows.net | TCP 443 |
| 3 | **Kötelező:** Office 365-integráció | Tekintse meg az [Office Online szolgáltatást és a közös URL-címeket](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) bemutató Office 365-dokumentációt | N.A. |
| 4 | **Kötelező:** Portál | app.powerbi.com | TCP 443 |
| 5 | **Kötelező:** Szolgáltatási telemetria | dc.services.visualstudio.com | TCP 443 |
| 6 | **Nem kötelező:** Tájékoztató üzenetek | dynmsg.modpim.com | TCP 443 |
| 7 | **Nem kötelező:** NPS-felmérések | nps.onyx.azure.net | TCP 443 |
| 8 | **Nem kötelező:** Content Delivery Network (CDN) | content.powerapps.com | TCP 443 |
| | | |

## <a name="administration"></a>Felügyelet

Ahhoz, hogy rendszergazdai funkciókat láthasson el a Power BI-ban, tudnia kell csatlakozni az alább hivatkozott webhelyeken megadott végpontokhoz.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Kötelező:** A felhasználók kezeléséhez és auditnaplók megtekintéséhez | Tekintse meg az [Office Online szolgáltatást és a közös URL-címeket](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) bemutató Office 365-dokumentációt | N.A. |
| | | |

## <a name="getting-data"></a>Adatok beolvasása

Ahhoz, hogy adatokat kérhessen le bizonyos adatforrásokból, például a OneDrive-ból, tudnia kell csatlakozni az alábbi táblázatban megadott végpontokhoz. Előfordulhat, hogy további internetes tartományok és URL-címek elérése szükséges a vállalatnál használt egyes adatforrásokhoz.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Kötelező:** AppSource (belső vagy külső alkalmazások a Power BI-ban) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Nem kötelező:** Bejelentkezés és adatok lekérése tartalomcsomagokhoz | A használt tartalomcsomagoktól függ | A használt tartalomcsomagoktól függ |
| 3 | **Nem kötelező:** Fájlok importálása személyes OneDrive-ból | Lásd: [A OneDrive webhelyhez megkövetelt URL-címek és portok](https://docs.microsoft.com/onedrive/required-urls-and-ports) | N.A. |
| 4 | **Nem kötelező:** A Power BI 60 másodpercben – bemutató videó | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Nem kötelező:** PubNub streamelési adatforrások | Lásd: [PubNub dokumentáció](https://support.pubnub.com/support/solutions/articles/14000043522) | N.A. |
| | | |

## <a name="dashboard-and-report-integration"></a>Irányítópultok és jelentések integrálása

A Power BI-nak szüksége van bizonyos végpontokra az irányítópultok és jelentések támogatásához. Tudnia kell csatlakozni az alábbi táblázatban és a hivatkozott webhelyeken megadott végpontokhoz.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Kötelező:** Excel-integráció | Tekintse meg az [Office Online szolgáltatást és a közös URL-címeket](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) bemutató Office 365-dokumentációt | N.A. |
| | | |

## <a name="power-bi-visuals"></a>Power BI-vizualizációk

A Power BI-nak szüksége van bizonyos végpontokra a Power BI-vizualizációk eléréséhez és megjelenítéséhez. Tudnia kell csatlakozni az alábbi táblázatban és a hivatkozott webhelyeken megadott végpontokhoz.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Kötelező:** Egyéni vizualizáció importálása a Marketplace felületéről vagy egy fájlból | *. azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Nem kötelező:** Bing Térképek | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Nem kötelező:** PowerApps | Lásd a [Szükséges szolgáltatások szakaszt](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) a PowerApps rendszerkövetelményeinek webhelyén | N.A. |
| 4 | **Nem kötelező:** Visio | Tekintse meg az [Office Online szolgáltatást és a közös URL-címeket](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), valamint a [SharePoint Online szolgáltatást és a OneDrive Vállalati verziót](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) bemutató Office 365-dokumentációt | N.A. |
| | | |

## <a name="related-external-sites"></a>Kapcsolódó külső webhelyek

A Power BI más webhelyekre is hivatkozik. Ezek közé tartoznak a dokumentációkat tartalmazó, a támogatást nyújtó, az új funkciókéréseket kezelő stb. webhelyek. Az ezekhez a webhelyekhez való hozzáférés nem befolyásolja a Power BI funkcióit, így az engedélyezési listára való felvételük nem kötelező.

| Sor | Szerep | Cél(ok) | Port(ok) |
| --- | --- | --- | --- |
| 1 | **Nem kötelező:** Közösségi webhely | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Nem kötelező:** Dokumentációs webhely | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Nem kötelező:** Letöltési webhely (Power BI Desktophoz stb.) | download.microsoft.com | TCP 443 |
| 4 | **Nem kötelező:** Külső átirányítások | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Nem kötelező:** Ötletek visszajelzési webhelye| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Nem kötelező:** A Power BI webhelye – kezdőlap, további információs hivatkozások, támogatási webhely, letöltési hivatkozások, partnerek bemutatása stb. | powerbi.microsoft.com | TCP 443 |
| 7 | **Nem kötelező:** Power BI Fejlesztői központ | dev.powerbi.com | TCP 443 |
| 8 | **Nem kötelező:** Támogatási webhely | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
