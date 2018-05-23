---
title: Az SAP HANA használata a Power BI Desktopban
description: Az SAP HANA használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 03/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 44dff39d043bb7a71c01b5103cfdf65e7d5e33cb
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2018
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Az SAP HANA használata a Power BI Desktopban
A Power BI Desktoppal mostantól hozzáférhet az **SAP HANA**-adatbázisokhoz. Az **SAP HANA**-adatbázisok használatához telepíteni kell az SAP HANA ODBC-illesztőprogramot a helyi ügyfélszámítógépen, hogy a Power BI Desktop **SAP HANA**-adatkapcsolat megfelelően működjön. Az SAP HANA ODBC-illesztőprogramot az [SAP Software Download Center központból](https://support.sap.com/swdc) töltheti le. Itt keresse meg a Windows rendszerű számítógépekhez készült SAP HANA-ügyfelet. Mivel az **SAP Software Download Center** szerkezete gyakran változik, a helyet nem tudjuk pontosabban meghatározni.

Ha **SAP HANA**-adatbázishoz szeretne csatlakozni, válassza az **Adatok lekérése > Adatbázis > SAP HANA-adatbázis** lehetőséget az alábbi ábrának megfelelően:

![](media/desktop-sap-hana/sap-hana-1.png)

Amikor SAP HANA-adatbázishoz csatlakozik, adja meg a kiszolgáló nevét és a portot *kiszolgáló:port* formátumban – a következő képen látható példában a kiszolgáló neve *ServerXYZ*, a port pedig a *30015-ös* port.

![](media/desktop-sap-hana/sap-hana-2.png)

Ebben a kiadásban az **SAP HANA** [DirectQuery](desktop-directquery-sap-hana.md) módban támogatott a Power BI Desktopban és a Power BI szolgáltatásban, és a **SAP HANA**-adatbázist DirectQuery módban használó jelentéseket tehet közzé és tölthet fel a Power BI szolgáltatásban. A Power BI szolgáltatásban akkor is közzétehet és feltölthet jelentéseket, ha nem **SAP HANA**-adatbázist használ DirectQuery módban.

### <a name="supported-features-for-sap-hana"></a>Az SAP HANA támogatott funkciói
Ebben a kiadásban számos képesség érhető el az **SAP HANA**-hoz, például a következők:

* Az **SAP HANA**-hoz készült Power BI-összekötő az SAP ODBC-illesztőprogramját használja a legjobb felhasználói élményt érdekében
* Az **SAP HANA** a DirectQuery és az importálási lehetőségeket is támogatja
* A Power BI támogatja a HANA-információmodelleket (például az elemzési és számítási nézeteket), és optimalizált navigációval rendelkezik
* Az **SAP HANA** használatával a közvetlen SQL funkciót is használhatja a sor- és oszloptáblázatokhoz való csatlakozáshoz
* Optimalizált navigáció érhető el a HANA-modellekhez
* A Power BI támogatja az **SAP HANA** változóit és bemeneti paramétereit

### <a name="installing-the-sap-hana-odbc-driver"></a>Az SAP HANA ODBC-illesztőprogramjának telepítése
### <a name="limitations-of-sap-hana"></a>Az SAP HANA korlátozásai
Az **SAP HANA** használatára a következő néhány korlátozás vonatkozik:

* Az NVARCHAR karakterláncokat a rendszer legfeljebb 4000 Unicode karakter hosszúságúra csonkolja
* A SMALLDECIMAL nem támogatott
* A VARBINARY nem támogatott
* Az érvényes dátumok 1899/12/30 és 9999/12/31 közöttiek


## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a DirectQueryről, tekintse át a következő forrásanyagokat:

* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)

