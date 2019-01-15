---
title: Csatlakozás Power BI-adatfolyamok által létrehozott adatokhoz a Power BI Desktopban (bétaverzió)
description: Egyszerű csatlakozás adatfolyamokhoz, és azok használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 27d686bd1be8a5cf73c7fa5bafc54d4a58dc7a5b
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279343"
---
# <a name="connect-to-data-created-by-power-bi-dataflows-in-power-bi-desktop-beta"></a>Csatlakozás Power BI-adatfolyamok által létrehozott adatokhoz a Power BI Desktopban (bétaverzió)
A **Power BI Desktopban** ugyanúgy csatlakozhat a **Power BI-adatfolyamok** által létrehozott adatokhoz, mint bármely más adatforráshoz.

![Csatlakozás adatfolyamokhoz](media/desktop-connect-dataflows/connect-dataflows_01.png)

A **Power BI-adatfolyamok (bétaverzió)** összekötője lehetővé teszi az adatfolyamok által létrehozott entitásokhoz való csatlakozást a Power BI szolgáltatásban. 

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

A **Power BI-adatfolyamok összekötője** ezen verziójának használatához a **Power BI Desktop** legújabb verzióját kell futtatnia. Bármikor [letöltheti a Power BI Desktopot](desktop-get-the-desktop.md), és telepítheti a számítógépére, hogy mindig a legújabb verzióval rendelkezzen.  

> [!NOTE]
> A Power BI-adatfolyamok összekötőjének előző verziójához szükséges volt letölteni egy .MEZ-fájlt, és elhelyezni azt egy mappában. A **Power BI Desktop** aktuális verziója tartalmazza a Power BI-adatfolyamok összekötőjét, így ez a fájl már nem szükséges, és az összekötő mellékelt verziójával való ütközést okozhat. Ha manuálisan a mappába helyezte ezt a . MEZ-fájlt, akkor törölnie *kell* a letöltött .MEZ-fájlt a **Dokumentumok > Power BI Desktop > Egyéni összekötők** mappából az ütközések elkerülése érdekében. 

## <a name="desktop-performance"></a>Asztali teljesítmény
A **Power BI Desktop** helyben fut azon a számítógépen, amelyen telepítve van. Az adatfolyamok adatbetöltési teljesítményét számos tényező befolyásolja. Ezen tényezők közé tartozik az adatok mérete, a számítógép CPU-ja és RAM-ja, a hálózati sávszélesség, az adatközponttól való távolság és más tényezők.

Javíthatja az adatfolyamok adatbetöltési teljesítményét. Ha például a feldolgozott adatok mérete túl nagy a **Power BI Desktop** számára a számítógépen való kezeléshez, használhat csatolt és számított entitásokat az adatfolyamokban az adatok összesítéséhez (az adatfolyamokon belül), és betöltheti csak az előkészített, összegyűjtött adatokat. Ennek megfelelően a nagyméretű adatok feldolgozása online adatfolyamokban történik, nem pedig a **Power BI Desktop** helyben futtatott példányában. Ezt a megközelítés lehetővé teszi, hogy a Power BI Desktop kisebb mennyiségű adatot töltsön be, valamint gyors és jól reagáló marad az adatfolyamok kezelése.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Az adatfolyamok többsége a Power BI szolgáltatás bérlőjében helyezkedik el. A **Power BI Desktop**-felhasználók azonban csak akkor férnek hozzá az Azure Data Lake Storage Gen2-tárfiókokban tárolt adatfolyamhoz, ha az adatfolyam tulajdonosai, vagy külön megadott jogosultsággal rendelkeznek az adatfolyam CDM-mappájához. Figyelje meg a következő példát:

1.  Anna új alkalmazás-munkaterületet hoz létre, amelyet úgy konfigurál, hogy a vállalati data lake-ben tárolja az adatfolyamokat.
2.  Dávid, aki szintén tagja az Anna által létrehozott munkaterületnek, a Power BI Desktop és az adatfolyam-összekötő használatával szeretne adatokhoz jutni az Anna által létrehozott adatfolyamból.
3.  Dávid hibajelenséget tapasztal, ugyanis nem adták hozzá jogosult felhasználóként az adatfolyam data lake-beli CDM-mappájához.

    ![Hiba adatfolyam használatára tett kísérlet esetén](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

A probléma megoldásához Dávidnak olvasási jogot kell adni a CDM-mappára és annak fájljaira. A CDM-mappákhoz való hozzáférés megadásáról [ez a cikk](https://go.microsoft.com/fwlink/?linkid=2029121) tartalmaz további információt.




## <a name="next-steps"></a>Következő lépések
A Power BI-adatfolyamokkal mindenféle érdekes dolgot végezhet. További információkért tekintse meg az alábbi forrásanyagokat:

* [Önkiszolgáló adatelőkészítés adatfolyamokkal](service-dataflows-overview.md)
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban (előzetes verzió)](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal (előzetes verzió)](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások a Power BI-adatfolyamokhoz (előzetes verzió)](service-dataflows-developer-resources.md)

Az Azure Data Lake Storage Gen2-nel való integrációról a következő cikkek írnak részletesebben:

* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)
* [Munkaterület adatfolyam-beállításainak konfigurálása (előzetes verzió)](service-dataflows-configure-workspace-storage-settings.md)
* [CDM-mappa hozzáadása a Power BI-hoz adatfolyamként (előzetes verzió)](service-dataflows-add-cdm-folder.md)
* [Azure Data Lake Storage Gen2 csatlakoztatása adatfolyam-tároláshoz (előzetes verzió)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Vannak még a **Power BI Desktop** alkalmazással kapcsolatos cikkek, amelyeket hasznosnak találhat:

* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   

