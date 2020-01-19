---
title: Kapcsolódás Azure Cost Management-adatokhoz a Power BI Desktopban
description: Könnyedén kapcsolódhat az Azure-hoz és elemzésekhez juthat hozzá az Azure költségeiről és használatáról a Power BI Desktop segítségével
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bf83df157738621116eb9e5461876eee8faf0863
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761680"
---
# <a name="create-visuals-and-reports-with-the-azure-cost-management-connector-in-power-bi-desktop"></a>Vizualizációk és jelentések létrehozása az Azure Cost Management-összekötővel a Power BI Desktopban

A Power BI Desktop Azure Cost Management összekötőjével hatékony, testreszabott vizualizációkat és jelentéseket készíthet, amelyek segítségével jobban megismerheti az Azure-t. Az Azure Cost Management-összekötő jelenleg a [Microsoft Ügyfélszerződéssel](https://azure.microsoft.com/pricing/purchase-options/microsoft-customer-agreement/) vagy a [Nagyvállalati Szerződéssel (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/) rendelkező ügyfeleket támogatja.  

Az Azure Cost Management-összekötő OAuth 2.0 hitelesítést használ az Azure-hoz, és azonosítja az összekötőt használó felhasználókat. Az ebben a folyamatban generált jogkivonatok meghatározott időtartamra érvényesek. A Power BI megőrzi a jogkivonatot a következő bejelentkezéshez. Az OAuth 2.0 annak a folyamatnak a szabványa, amely a háttérben gondoskodik ezeknek az engedélyeknek a biztonságos kezeléséről. A kapcsolódáshoz egy [Nagyvállalati rendszergazdai](https://docs.microsoft.com/azure/billing/billing-understand-ea-roles) fiókot kell használnia a Nagyvállalati Szerződéshez, vagy egy [Számlázási fióktulajdonosi](https://docs.microsoft.com/azure/billing/billing-understand-mca-roles) fiókot a Microsoft Ügyfélszerződéshez. 

> [!NOTE]
> Ez az összekötő felváltja a korábban elérhető [Azure Consumption Insights és Azure Cost Management (bétaverzió)](desktop-connect-azure-consumption-insights.md) összekötőjét. Az előző összekötővel létrehozott jelentéseket újra létre kell hozni ennek az összekötőnek a használatával.

## <a name="connect-using-azure-cost-management"></a>Kapcsolódás az Azure Cost Management segítségével

Ha az **Azure Cost Management-összekötő** szeretné használni a Power BI Desktopban, az alábbi lépéseket kell elvégeznie:

1.  A **Kezdőlap** menüszalagon válassza az **Adatok lekérése** lehetőséget.
2.  Az adatkategóriák listájában válassza az **Azure-t**.
3.  Válassza az **Azure Cost Management** lehetőséget.

    ![Adatok lekérése](media/desktop-connect-azure-cost-management/azure-cost-management-00b.png)

4. A megjelenő párbeszédpanelen adja meg vagy a **Microsoft Ügyfélszerződéshez** tartozó **Számlázási profil azonosítóját**, vagy a **Nagyvállalati Szerződéshez (EA)** tartozó **Regisztrációs számot**. 


## <a name="connect-to-a-microsoft-customer-agreement-account"></a>Kapcsolódás a Microsoft Ügyfélszerződés-fiókhoz 

Ha kapcsolódni szeretne a **Microsoft Ügyfélszerződési** fiókjához, a **Számlázási profil azonosítóját** az Azure Portalon szerezheti be:

1.  Az [Azure Portalon](https://portal.azure.com/) lépjen a **Költségkezelés + Számlázás** területre.
2.  Jelölje ki a számlázási profilját. 
3.  A **Beállítások** menüterületen az oldalsávon válassza a **Tulajdonságok** lehetőséget.
4.  A **Számlázási profil** területen másolja az **Azonosítót**. 
5.  A **Hatókör kiválasztása** területen válassza a **Számlázási profil azonosítója** lehetőséget, és illessze be az előző lépésben másolt számlázásiprofil-azonosítót. 
6.  Adja meg a hónapok számát, és válassza az **OK** lehetőséget.

    ![A számlázási azonosító beszerzése](media/desktop-connect-azure-cost-management/azure-cost-management-01a.png)

7.  Ha a rendszer kéri, jelentkezzen be az Azure-beli felhasználói fiókjával és jelszavával. 


## <a name="connect-to-an-enterprise-agreement-account"></a>Kapcsolódás Nagyvállalati Szerződéses fiókhoz

Ha Nagyvállalati Szerződéses (EA-) fiókkal szeretne csatlakozni, a regisztrációs azonosítót a Azure Portalon kérheti le:

1.  Az [Azure Portalon](https://portal.azure.com/) lépjen a **Költségkezelés + Számlázás** területre.
2.  Válassza ki számlafiókját.
3.  Az **Áttekintés** oldalon másolja ki a **Számlázási fiók azonosítóját**.
4.  A **Hatókör kiválasztása** területen válassza a **Regisztráció száma** lehetőséget, és illessze be az előző lépésben másolt számlázásiprofil-azonosítót. 
5.  Adja meg a hónapok számát, és válassza az **OK** lehetőséget.

    ![A számlázási azonosító beszerzése](media/desktop-connect-azure-cost-management/azure-cost-management-01b.png)

6.  Ha a rendszer kéri, jelentkezzen be az Azure-beli felhasználói fiókjával és jelszavával. 

## <a name="data-available-through-the-connector"></a>Az összekötőn keresztül elérhető adatok

Miután sikeresen elvégezte a hitelesítést, megjelenik egy **Navigátor** ablak a következő elérhető adattáblákkal:



| **Tábla** | **Leírás** |
| --- | --- |
| **Egyenleg összegzése** | A Nagyvállalati Szerződések (EA) egyenlegének összefoglalása. |
| **Billing events** | Új számlák, kreditvásárlások és egyebek eseménynaplói. Csak Microsoft Ügyfélszerződésre vonatkozik. |
| **Budgets** | Költségvetési részletek a tényleges költségek megtekintéséhez vagy a használat és a költségkeret összehasonlításához. |
| **Charges** | Az Azure-használat, a Marketplace-díjak és a külön számlázott díjak havi szintű összefoglalása. Csak Microsoft Ügyfélszerződésre vonatkozik. |
| **Credit lots** | Az Azure-kreditek vásárlási részletei az adott számlázási profilhoz. Csak Microsoft Ügyfélszerződésre vonatkozik. |
| **Pricesheets** | Az adott számlázási profil vagy az EA-regisztráció alkalmazható mérődíjait tartalmazza. |
| **RI charges** | A fenntartott példányaival kapcsolatos utolsó 24 havi díjak. |
| **RI recommendations (shared)** | Fenntartott példányok vásárlására vonatkozó javaslatok az összes előfizetésen belül 7, 30 vagy 60 napon át tapasztalt használati trendek alapján. |
| **RI recommendations (single)** | Fenntartott példányok vásárlására vonatkozó javaslatok az egy előfizetésen belül 7, 30 vagy 60 napon át tapasztalt használati trendek alapján. |
| **Fenntartott példányok felhasználási adatai** | Az utolsó hónapra vonatkozó fogyasztási részletek a meglévő fenntartott példányairól. |
| **Fenntartott példányok felhasználási összefoglalása** | Napi Azure-foglalás százalékos kihasználtsága. |
| **Usage details** | A Nagyvállalati Szerződéses regisztrációhoz tartozó adott számlázási profilazonosító fogyasztott mennyiségeinek és a becsült díjainak részletezése. |
| **Felhasználási adatok visszatérítésről** | A Nagyvállalati Szerződéses regisztrációhoz tartozó adott számlázási profilazonosító fogyasztott mennyiségeinek és a becsült visszatérített díjainak részletezése. |

Előnézetet jeleníthet meg egy tábla párbeszédpaneljének kiválasztásával. Több táblát is kiválaszthat a nevek melletti jelölőnégyzetekkel, majd kattintson a **Betöltés** gombra.

![A számlázási azonosító beszerzése](media/desktop-connect-azure-cost-management/azure-cost-management-01c.png)

Ha a **Betöltés** gombra kattint, a rendszer betölti az adatokat a Power BI Desktopba. 

A kiválasztott adatok betöltése után az adattáblák és mezők láthatók lesznek a **Mezők** panelen.


## <a name="next-steps"></a>Következő lépések

A Power BI Desktop használatával számos különböző adatforráshoz csatlakozhat. További információért tekintse át a következő cikkeket:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   
