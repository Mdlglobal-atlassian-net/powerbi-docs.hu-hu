---
title: Csatlakozás Power Platform-adatfolyamok által létrehozott adatokhoz a Power BI Desktopban
description: Egyszerű csatlakozás adatfolyamokhoz, és azok használata a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: abbe6192819daa6b5d0197d9471a8eab84596262
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349655"
---
# <a name="connect-to-data-created-by-power-platform-dataflows-in-power-bi-desktop"></a>Csatlakozás Power Platform-adatfolyamok által létrehozott adatokhoz a Power BI Desktopban
A **Power BI Desktopban** ugyanúgy csatlakozhat a **Power Platform-adatfolyamok** által létrehozott adatokhoz, mint bármely más adatforráshoz.

![Csatlakozás adatfolyamokhoz](media/desktop-connect-dataflows/connect-dataflows_01.png)

A **Power Platform-adatfolyamok** összekötője lehetővé teszi az adatfolyamok által létrehozott entitásokhoz való csatlakozást a Power BI szolgáltatásban. 

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

A **Power Platform-adatfolyamok összekötőjének** használatához a **Power BI Desktop** valamelyik friss verzióját kell futtatnia. Bármikor [letöltheti a Power BI Desktopot](../fundamentals/desktop-get-the-desktop.md), és telepítheti a számítógépére, hogy mindig a legújabb verzióval rendelkezzen.  

> [!NOTE]
> A Power Platform-adatfolyamok összekötőjének előző verziójához le kellett tölteni egy .MEZ fájlt és elhelyezni egy mappában. A **Power BI Desktop** aktuális verziói tartalmazzák a Power Platform-adatfolyamok összekötőjét, így ez a fájl már nem szükséges, és az összekötő mellékelt verziójával ütközést okozhat. Ha manuálisan a mappába helyezte ezt a . MEZ-fájlt, akkor törölnie *kell* a letöltött .MEZ-fájlt a **Dokumentumok > Power BI Desktop > Egyéni összekötők** mappából az ütközések elkerülése érdekében. 

## <a name="desktop-performance"></a>Asztali teljesítmény
A **Power BI Desktop** helyben fut azon a számítógépen, amelyen telepítve van. Az adatfolyamok adatbetöltési teljesítményét számos tényező befolyásolja. Ezen tényezők közé tartozik az adatok mérete, a számítógép CPU-ja és RAM-ja, a hálózati sávszélesség, az adatközponttól való távolság és más tényezők.

Javíthatja az adatfolyamok adatbetöltési teljesítményét. Ha például a feldolgozott adatok mérete túl nagy a **Power BI Desktop** számára a számítógépen való kezeléshez, használhat csatolt és számított entitásokat az adatfolyamokban az adatok összesítéséhez (az adatfolyamokon belül), és betöltheti csak az előkészített, összegyűjtött adatokat. 

Ennek megfelelően a nagyméretű adatok feldolgozása online adatfolyamokban történik, nem pedig a **Power BI Desktop** helyben futtatott példányában. Ezt a megközelítés lehetővé teszi, hogy a Power BI Desktop kisebb mennyiségű adatot töltsön be, valamint gyors és jól reagáló marad az adatfolyamok kezelése.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Az adatfolyamok többsége a Power BI szolgáltatás bérlőjében helyezkedik el. A **Power BI Desktop**-felhasználók azonban csak akkor férnek hozzá az Azure Data Lake Storage Gen2-tárfiókokban tárolt adatfolyamhoz, ha az adatfolyam tulajdonosai, vagy külön megadott jogosultsággal rendelkeznek az adatfolyam CDM-mappájához. Figyelje meg a következő példát:

1.  Anna új munkaterületet hoz létre, amelyet úgy konfigurál, hogy a vállalati adattóban tárolja az adatfolyamokat.
2.  Dávid, aki szintén tagja az Anna által létrehozott munkaterületnek, a Power BI Desktop és az adatfolyam-összekötő használatával szeretne adatokhoz jutni az Anna által létrehozott adatfolyamból.
3.  Dávid hibajelenséget tapasztal, ugyanis nem adták hozzá jogosult felhasználóként az adatfolyam data lake-beli CDM-mappájához.

    ![Hiba adatfolyam használatára tett kísérlet esetén](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

A probléma megoldásához Dávidnak olvasási jogot kell adni a CDM-mappára és annak fájljaira. A CDM-mappákhoz való hozzáférés megadásáról [ez a cikk](https://go.microsoft.com/fwlink/?linkid=2029121) tartalmaz további információt.




## <a name="next-steps"></a>Következő lépések
A Power Platform-adatfolyamoknak számos felhasználási módja létezik. További információkért tekintse meg az alábbi forrásanyagokat:

* [Önkiszolgáló adatelőkészítés adatfolyamokkal](service-dataflows-overview.md)
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban (előzetes verzió)](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal (előzetes verzió)](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások a Power Platform-adatfolyamokhoz (előzetes verzió)](service-dataflows-developer-resources.md)

Az Azure Data Lake Storage Gen2-nel való integrációról a következő cikkek írnak részletesebben:

* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)
* [Munkaterület adatfolyam-beállításainak konfigurálása (előzetes verzió)](service-dataflows-configure-workspace-storage-settings.md)
* [CDM-mappa hozzáadása a Power BI-hoz adatfolyamként (előzetes verzió)](service-dataflows-add-cdm-folder.md)
* [Azure Data Lake Storage Gen2 csatlakoztatása adatfolyam-tároláshoz (előzetes verzió)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Vannak még a **Power BI Desktop** alkalmazással kapcsolatos cikkek, amelyeket hasznosnak találhat:

* [Adatforrások a Power BI Desktopban](../connect-data/desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](../connect-data/desktop-shape-and-combine-data.md)
* [Adatok közvetlen bevitele a Power BI Desktopba](../connect-data/desktop-enter-data-directly-into-desktop.md)   
