---
title: Egyéni adatösszekötők használata a helyszíni adatátjáróval
description: A helyszíni adatátjáróval egyéni adatösszekötőket használhat.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 51d03582ec91b926526a075a356323eb4f95a84b
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609892"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Egyéni adatösszekötők használata a helyszíni adatátjáróval

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

A Power BI-hoz készült adatösszekötőkkel alkalmazásokból, szolgáltatásokból vagy adatforrásokból származó adatokhoz csatlakozhat és férhet hozzá. Egyéni adatösszekötőket készíthet, és használhatja azokat a Power BI Desktopban.

Egyéni adatösszekötők Power BI-hoz való fejlesztéséről a [Data Connector SDK GitHub-oldalán](https://aka.ms/dataconnectors) olvashat. Ez a webhely az első lépésekre vonatkozó információkat, valamint a Power BI-hoz és a Power Queryhez készült mintákat tartalmazza.

Ha egyéni adatösszekötőket használó jelentéseket készít a Power BI Desktopban, akkor azokat a helyszíni adatátjáró használatával frissítheti a Power BI szolgáltatásból.

## <a name="enable-and-use-this-capability"></a>A képesség engedélyezése és használata

A helyszíni adatátjáró 2018. júliusi vagy újabb verziójának telepítése során egy **Összekötők** lapot talál a helyszíni adatátjáró alkalmazásban. Az **Egyéni adatösszekötők betöltése mappából** mezőben megadhat egy mappát, amelyből az egyéni összekötők be lesznek töltve. Az alapértelmezett felhasználó *NT SERVICE\PBIEgwService*. Az átjáró automatikusan betölti az ebben a mappában található egyéni összekötőfájlokat. Ezek az adatösszekötők listájában jelennek meg.

![Egyéni adatösszekötők](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Ha a (privát) helyszíni adatátjárót használja, akkor fel tudja tölteni Power BI-jelentését a Power BI szolgáltatásba, és frissítheti azt az átjáró használatával.

A helyszíni adatátjáró esetén az egyéni összekötőhöz létre kell hozni egy adatforrást. A Power BI szolgáltatás Átjáróbeállítások oldalán az átjárófürt kijelölésekor meg kell jelennie egy lehetőségnek, amellyel engedélyezheti egyéni összekötők használatát a fürthöz. Ez a beállítás csak akkor lesz elérhető, ha a fürthöz tartozó összes átjáró rendelkezik a 2018. júliusi vagy annál újabb frissítéssel. A lehetőség bejelölésével engedélyezi az egyéni összekötők használatát a fürthöz.

![Az Átjárófürt beállításai oldal](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Ha ezt a beállítást engedélyezte, akkor egyéni összekötői megjelennek az átjárófürt alatt létrehozható adatforrásként. Miután létrehoz egy adatforrást az új egyéni összekötővel, már használhatja ezt az egyéni összekötőt a Power BI szolgáltatásban a Power BI-jelentések frissítésére.

![Az Adatforrás beállításai oldal](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Gondoskodjon arról, hogy háttérbeli átjárószolgáltatás hozzáférjen a létrehozott mappához. A felhasználók Windows-mappáin belüli mappák és a rendszermappák általában nem lesznek hozzáférhetők. A helyszíni adatátjáró alkalmazás üzenetet jelenít meg, ha a mappa nem érhető el. Ez az utasítás a (privát) helyszíni adatátjáróra nem vonatkozik.
* Ahhoz, hogy egy egyéni összekötő működjön a helyszíni adatátjáróval, a kódjában lennie kell egy „TestConnection” szakasznak. Ez a szakasz nem szükséges akkor, ha az egyéni összekötőt a Power BI Desktoppal használja. Éppen ezért létezhet olyan összekötő, amely a Power BI Desktoppal működik, az átjáróval viszont nem. A TestConnection szakasz megírásáról [ebből a dokumentációból](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) tájékozódhat.
* Az átjárókon keresztül üzemeltetett egyéni összekötőkhöz egyelőre csak az átjárók rendszergazdái használhatják az OAuth protokollt, más adatforrás-felhasználók nem.

## <a name="next-steps"></a>Következő lépések

* [Az adatforrás kezelése – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Az adatforrás kezelése – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Adatforrások kezelése – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Adatforrások kezelése – Oracle](service-gateway-onprem-manage-oracle.md)  
* [Adatforrások kezelése – Importálás/ütemezett frissítés](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Helyszíni adatátjáró proxybeállításainak konfigurálása](/data-integration/gateway/service-gateway-proxy)
* [A Kerberos használata a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezéshez (SSO)](service-gateway-sso-kerberos.md)  

További kérdései vannak? Forduljon a [Power BI közösségéhez](https://community.powerbi.com/).
