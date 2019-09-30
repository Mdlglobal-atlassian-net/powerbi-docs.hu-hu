---
title: Kerberos használata az SAP HANA-n belüli egyszeri bejelentkezéshez (SSO)
description: Az SAP HANA-kiszolgáló konfigurálása a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4e94781b3a424e894e0f0e2209ec48efb25c5db5
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106308"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Kerberos használata az SAP HANA-n belüli egyszeri bejelentkezéshez (SSO)

Ez a cikk azt ismerteti, hogy hogyan konfigurálhatja az SAP HANA-kiszolgálót a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez.

> [!NOTE]
> Egy Kerberos SSO-t használó, SAP HANA-alapú jelentés frissítése előtt végezze el ezen, valamint a [Kerberos SSO konfigurálását ismertető](service-gateway-sso-kerberos.md) cikk lépéseit.

## <a name="enable-sso-for-sap-hana"></a>Az SSO engedélyezése az SAP HANA esetében

Az egyszeri bejelentkezés SAP HANA rendszerrel való engedélyezéséhez kövesse az alábbi lépéseket:

* Ellenőrizze, hogy az SAP HANA-kiszolgáló a minimálisan megkövetelt verzióval fut-e, ami az SAP HANA-kiszolgáló platformjának szintéjtől függ:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Az átjárót tartalmazó számítógépen telepítse az SAP legfrissebb HANA ODBC-illesztőjét.  A minimális verzió a HANA ODBC 2017. augusztusi, 2.00.020.00-s verziója.

Győződjön meg arról, hogy az SAP HANA-kiszolgáló konfigurálva van a Kerberos-alapú egyszeri bejelentkezéshez. További információt az SAP HANA egyszeri bejelentkezésének a Kerberosszal történő beállításáról az SAP HANA biztonsági útmutatójának [Egyszeri bejelentkezés a Kerberosszal](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) című szakaszában találhat. Emellett a lap hivatkozásait is megtekintheti, amelyek közül az SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory különösen hasznos lehet.

Emellett javasoljuk, hogy kövesse az alábbi lépéseket, amelyek egy kis teljesítménynövekedést eredményezhetnek.

1. Az átjáró telepítési könyvtárában keresse meg, majd nyissa meg ezt a konfigurációs fájlt: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Keresse meg a *FullDomainResolutionEnabled* tulajdonságot, és módosítsa *True* értékre.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Futtasson egy [Power BI-jelentést](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Következő lépések

A **helyszíni adatátjáróval** és a **DirectQueryvel** kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a helyszíni adatátjáró?](/data-integration/gateway/service-gateway-getting-started)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
