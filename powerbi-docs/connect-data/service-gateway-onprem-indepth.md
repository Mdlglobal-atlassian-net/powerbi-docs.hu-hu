---
title: Helyszíni adatátjáró – részletesen
description: Ez a cikk a helyszíni adatátjárót ismerteti részletesen. Kitér a szolgáltatás és az Azure Active Directory, valamint a helyszíni Active Directory közötti együttműködésre az Analysis Services használata során.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 129a76876538ba69572a119263d7f90fd64224bb
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83308739"
---
# <a name="on-premises-data-gateway-in-depth"></a>Helyszíni adatátjáró – részletesen

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Ebből a cikkből áthelyeztük az információkat a Power BI több másik cikkébe és általános dokumentációkba. A megfelelő tartalmat az egyes fejlécek alatti hivatkozásokat használva találja meg.

## <a name="how-the-gateway-works"></a>Az átjáró működése

Lásd: [Helyszíni adatátjáró architektúrája](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Elérhető adatforrástípusok listája

Lás: [Adatforrások kezelése](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Hitelesítés helyszíni adatforrásoknál

Lásd: [Hitelesítés helyszíni adatforrásoknál](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Hitelesítés élő Analysis Services-adatforrásnál

Lásd: [Hitelesítés élő Analysis Services-adatforrásnál](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Szerepköralapú biztonság

Lásd: [Szerepköralapú biztonság](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Sorszintű biztonság

Lásd: [Sorszintű biztonság](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>Mi az Azure Active Directory szerepe?

Lásd: [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Honnan tudhatom meg, mi az UPN-em?

Lásd: [Honnan tudhatom meg, mi az UPN-em?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is)

## <a name="map-user-names-for-analysis-services-data-sources"></a>Felhasználónevek és Analysis Services-adatforrások egymáshoz rendelése

[Felhasználónevek és Analysis Services-adatforrások egymáshoz rendelése](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Helyszíni Active Directory szinkronizálása az Azure Active Directoryval

Lásd: [Helyszíni Active Directory szinkronizálása az Azure Active Directoryval](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Hogyan tovább?

Lásd az adatforrásokról szóló cikkeket:

[Adatforrások kezelése](service-gateway-data-sources.md)
[Az adatforrás kezelése – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Az adatforrás kezelése – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Adatforrások kezelése – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Adatforrások kezelése – Oracle](service-gateway-onprem-manage-oracle.md)  
[Adatforrások kezelése – Importálás és ütemezett frissítés](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Hibalehetőségek

Lásd: [A helyszíni adatátjáróval kapcsolatos hibák elhárítása](/data-integration/gateway/service-gateway-tshoot) és [Az átjárókkal kapcsolatos hibák elhárítása – Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Bejelentkezési fiók

Lásd: [Bejelentkezési fiók](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Windows-szolgáltatásfiók

Lásd: [Helyszíni adatátjáró szolgáltatásfiókjának módosítása](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Portok

Lásd: [Portok](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>A HTTPS-kommunikáció kényszerítése az Azure Service Busszal

Lásd: [A HTTPS-kommunikáció kényszerítése az Azure Service Busszal](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>A TLS 1.2 támogatása

Lásd: [TLS 1.2 átjáró adatforgalmához](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Az átjáró újraindítása

Lásd: [Átjáró újraindítása](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Következő lépések

[Mi az a helyszíni adatátjáró?](service-gateway-onprem.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)