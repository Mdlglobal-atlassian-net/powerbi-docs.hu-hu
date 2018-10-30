---
title: Egyéni adatösszekötők használata a helyszíni adatátjáróval
description: Helyszíni adatátjáróval egyéni adatösszekötők is használhatók.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 08/08/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 75e760c1ad808d05986de46cf2bc427bb078e3ce
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50101278"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Egyéni adatösszekötők használata a helyszíni adatátjáróval

A Power BI-beli adatösszekötők lehetővé teszik az alkalmazásból, szolgáltatásból vagy adatforrásból származó adatokhoz való csatlakozást és hozzáférést. Egyéni adatösszekötőket készíthet, és használhatja azokat a Power BI Desktopban.

Egyéni adatösszekötők Power BI-hoz való fejlesztéséről az [itt](http://aka.ms/dataconnectors) található dokumentációban olvashat.

Ha egyéni adatösszekötőket használó jelentéseket készít a Power BI Desktopban, akkor azokat a helyszíni adatátjáró használatával frissítheti a Power BI szolgáltatásból.

## <a name="here-is-a-guide-on-how-to-enable-and-use-this-capability"></a>Útmutató ennek a funkciónak az engedélyezéséhez és használatához

A helyszíni adatátjáró 2018. júliusi vagy újabb verziójának telepítése során egy „Összekötők” lapot talál a konfiguráló programban. Itt megadhat egy mappát, amelyből az egyéni összekötők be lesznek töltve. Mindenképpen olyan mappát kell választania, amelyhez az átjárószolgáltatást futtató felhasználó (alapértelmezés szerint „NT SERVICE\PBIEgwService”) hozzáférhet. Az átjáró automatikusan betölti az ebben a mappában lévő összekötőfájlokat, és azoknak meg kell jelenniük az adatösszekötők listájában.

![Egyéni összekötő, 1. ábra](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Ha a helyszíni adatátjáró személyes verzióját használja, akkor fel tudja tölteni Power BI-jelentését a Power BI szolgáltatásba, és frissítheti azt az átjáró használatával.

Az átjáró nagyvállalati verziója esetén az egyéni összekötőhöz még létre kell hozni egy adatforrást. A Power BI szolgáltatás Átjáróbeállítások oldalán az átjárófürt kijelölésekor meg kell jelennie egy új lehetőségnek, amellyel engedélyezheti egyéni összekötők használatát a fürthöz. Ez a beállítás csak akkor lesz elérhető, ha a fürthöz tartozó összes átjáró rendelkezik a 2018. júliusi vagy annál újabb frissítéssel. A lehetőség bejelölésével engedélyezi az egyéni összekötők használatát a fürthöz.

![Egyéni összekötő, 2. ábra](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Ha ezt a beállítást engedélyezte, akkor egyéni összekötői megjelennek az átjárófürt alatt létrehozható adatforrásként. Miután létrehoz egy adatforrást az új egyéni összekötővel, már használhatja ezt az egyéni összekötőt a Power BI szolgáltatásban a Power BI-jelentések frissítésére.

![Egyéni összekötő, 3. ábra](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Gondoskodjon arról, hogy háttérbeli átjárószolgáltatás hozzáférjen a létrehozott mappához. A felhasználók Windows-mappáin belüli mappák és a rendszermappák általában nem lesznek hozzáférhetők. Az átjárókonfiguráló program üzenetet jelenít meg, ha a mappa nem érhető el (az átjáró személyes verziójára ez nem vonatkozik)
* Ahhoz, hogy egy egyéni összekötő működjön a helyszíni adatátjáróval, a kódjában lennie kell egy „TestConnection” szakasznak. Ez nem szükséges akkor, ha az egyéni összekötő a Power BI Desktoppal van használva. Éppen ezért létezhet olyan, amely a Desktoppal működik, az átjáróval viszont nem. A TestConnection szakasz megírásáról [ebből a dokumentációból](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) tájékozódhat.

## <a name="next-steps"></a>Következő lépések

* [Adatforrások kezelése – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Az adatforrás kezelése – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Adatforrások kezelése – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Adatforrások kezelése – Oracle](service-gateway-onprem-manage-oracle.md)  
* [Adatforrások kezelése – Importálás és ütemezett frissítés](service-gateway-enterprise-manage-scheduled-refresh.md)  
* [Helyszíni adatátjáró – részletes](service-gateway-onprem-indepth.md)  
* [Helyszíni adatátjáró (személyes mód)](service-gateway-personal-mode.md)
* [Helyszíni adatátjáró proxybeállításainak konfigurálása](service-gateway-proxy.md)  
* [Kerberos használata egyszeri bejelentkezésre (SSO) a Power BI-ból a helyszíni adatforrásokba](service-gateway-sso-kerberos.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
