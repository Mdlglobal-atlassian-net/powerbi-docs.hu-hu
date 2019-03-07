---
title: Adatfolyamok a Power BI-ban
description: Adatfolyamok működése a Power BI-ban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4c32f27a04b055eb67015d9c8308866b972c06a7
ms.sourcegitcommit: 364ffa1178cdfb0a20acffc0fd79922ebc892d72
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2019
ms.locfileid: "57226089"
---
# <a name="self-service-data-prep-in-power-bi-preview"></a>Önkiszolgáló adat-előkészítés a Power BI-ban (előzetes verzió)

Az adatmennyiség növekedésével egyre nagyobb kihívássá válik az adatok megfelelően formázott, döntéstámogató információkká való alakítása. Olyan adatokkal szeretünk dolgozni, amelyek elemzésre készek, és feltölthetők velük a vizualizációk, a jelentések és az irányítópultok, így gyorsan döntéstámogató elemzésekké formálhatjuk őket. A big data típusú adatok **önkiszolgáló adat-előkészítése** a Power BI-ban lehetővé teszi, hogy néhány kattintással Power BI-elemzéseket készítsen az adatokból.

![Adatfolyamok használata a Power BI-ban](media/service-dataflows-overview/powerbi-dataflows_01.png)

A Power BI **adatfolyamokkal** segít szervezeteknek egységesíteni a különféle forrásokból származó adatokat, valamint előkészíteni azokat modellezésre. Az elemzők könnyen, jól ismert és önkiszolgáló eszközökkel hozhatnak létre adatfolyamokat. Az adatfolyamokkal big data típusú adatokat tölthet be, alakíthat át, integrálhat és egészíthet ki. Ehhez adatforrás-kapcsolatokat, ETL logikát, frissítésütemezést és egyéb funkciókat definiálhat. Az adatfolyamok új modellalapú számítási motorja emellett könnyebben kezelhetővé, determinisztikusabbá és egyszerűbbé teszi az adat-előkészítést adatelemzők és jelentéskészítők számára. A táblázatok érintett képleteinek újraszámításához hasonlóan az adatfolyamok is az Ön nevében kezelik egy entitás vagy adatelem módosításait, valamint automatizálják a frissítéseket és feleslegessé teszik az időigényes logikai ellenőrzéseket. Az adatfolyamokkal a korábban adatszakértők felügyeletét (és több órát vagy akár napokat is) igénylő feladatok mostantól néhány kattintással kezelhetők elemzők és jelentéskészítők által. 

Az adatok entitásként vannak tárolva [a **Common Data Service-ben**](https://docs.microsoft.com/powerapps/common-data-model/overview), az Azure Data Lake Storage Gen2 részeként. Adatfolyamokat a Power BI szolgáltatással, alkalmazás-munkaterületeken hozhat létre és kezelhet.  

> [!NOTE]
> Az adatfolyamok előzetes verzióban állnak rendelkezésre, és az általánosan elérhetővé válás előtt módosulhatnak és frissülhetnek.

 
Az **adatfolyamok** a **Common Data Service**, a Microsoft által kiadott szabványosított, moduláris, kiterjeszthető adatséma-gyűjtemény használatához lettek kialakítva, amellyel könnyebben fejleszthet, használhat és elemezhet adatokat. Ezzel a modellel szinte terhelés nélkül válthat adatforrásokról Power BI-irányítópultokra.

Adatfolyamokkal számos – és egyre növekvő számú – helyszíni és felhőalapú adatforrásból beölthet adatokat, így a Dynamics 365, a Salesforce, az Azure SQL Database, az Excel, a SharePoint és egyéb szolgáltatásokból.

Az adatokat szabványos entitásokhoz társíthatja a Common Data Service-ben, valamint módosíthatja és kibővítheti a meglévő entitásokat és egyéni entitásokat hozhat létre. A haladó felhasználók teljes mértékben testreszabott adatfolyamokat hozhatnak létre egy önkiszolgáló, kevés vagy semennyi kódot nem igénylő, beépített Power Query-s módszerrel, a Power BI Desktop- és Excel-felhasználók által már jól ismert Power Query-felületen.  

Miután létrehoz egy adatfolyamot, a Power BI Desktop és a Power BI szolgáltatás használatával olyan adathalmazokat, jelentéseket, irányítópultokat és alkalmazásokat hozhat létre, amelyek a Common Data Service előnyeit kihasználva mély elemzéseket nyújtanak az üzleti tevékenységekről. 

Az adatkészletekhez hasonlóan az adatfrissítés ütemezését közvetlenül arról a munkaterületről kezelheti, amelyben az adatfolyam létre lett hozva. 

## <a name="how-dataflows-work"></a>Az adatfolyamok működése

Íme néhány példa az adatfolyamok működéséről:

* Szervezetek szabványos entitásokhoz társíthatják az adataikat a Common Data Service-ben, vagy saját egyéni entitásokat hozhatnak létre. Ezekkel az entitásokkal aztán jelentések, irányítópultok és alkalmazások hozhatók létre, amelyek azonnal használatra készek, és a teljes szervezetben terjeszthetők a felhasználók számára. 

* A Microsoft-adatösszekötők széles tárházának használatával a szervezetek adatfolyamokhoz csatlakoztathatják saját adatforrásaikat, a Power Query segítségével pedig az eredetüknél képezhetik le az adatokat, és átemelhetik a Power BI-ba. Az adatok adatfolyammal történő importálása (és megadott gyakoriságú frissítése) után az adatfolyam entitásaival a Power BI Desktopban meggyőző jelentéseket és irányítópultokat készíthet. 

## <a name="how-to-use-dataflows"></a>Adatfolyamok használata

Az előző szakasz ismertette az adatfolyamok néhány használati forgatókönyvét Power BI-beli hatékony elemzések létrehozásához. Ebben a szakaszban bemutatjuk, milyen gyorsan készíthet jelentéseket adatfolyamokkal, hogyan hozzák létre saját adatfolyamaikat a Power BI-szakértők, valamint hogyan szabják testre saját szervezetük elemzéseit.

> [!NOTE]
> Adatfolyamok használatához előfizetéses Power BI-fiókkal kell rendelkeznie, például Power BI Pro- vagy Power BI Premium-fiókkal, de az adatfolyamok használatáért nem számítunk fel külön díjat. 

### <a name="extend-the-common-data-model-for-your-business-needs"></a>A Common Data Service kibővítése az üzleti igényekhez
A Common Data Service (CDM) szolgáltatás kibővíteni kívánó szervezetek adatfolyamai lehetővé teszik az üzleti intelligencia szakértői számára, hogy szabványos entitásokat szabjanak testre vagy újakat hozzanak létre. Az adatmodell eme önkiszolgáló megközelítését az adatfolyamokkal együtt használva egy szervezet igényei szerint testreszabott alkalmazások és Power BI-irányítópultok hozhatók létre.

### <a name="define-dataflows-programmatically"></a>Adatfolyamok programozott módon történő definiálása
Érdemes lehet saját programozott megoldásokat fejleszteni adatfolyamok létrehozásához. A nyilvános API-kkal és az egyéni adatfolyam-definíciós fájlok (model.json) létrehozásának lehetőségével olyan egyéni megoldást készíthet, amely alkalmazkodik szervezete adatokkal és elemzésekkel kapcsolatos egyéni igényeihez. 

A nyilvános API-kkal a fejlesztők egyszerűen és könnyen dolgozhatnak a Power BI-jal és az adatfolyamokkal.

### <a name="extend-your-capabilities-with-azure"></a>A lehetőségek kibővítése az Azure-ral
Az Azure Data Lake Storage Gen2 minden fizetős Power BI-előfizetés része (felhasználónként 10 GB, P1 csomópontonként 100 TB). Így könnyen használatba veheti az önkiszolgáló adat-előkészítés funkciót az Azure Data Lake-ben. 

A Power BI-t úgy konfigurálhatja, hogy az adatfolyam adatait a szervezeti Azure Data Lake Storage Gen2-fiókban tárolja. Az Azure-előfizetés a Power BI-jal való összekapcsolásával az adatfejlesztők és adatszakértők olyan hatékony Azure-termékeket vehetnek igénybe, mint az Azure Machine Learning, az Azure Databricks, az Azure Data Factory és számos más.

A Power BI emellett sematikus, Common Data Service formátumú adatokat tartalmazó mappákhoz is csatlakozhat, amelyek a vállalata Azure Data Lake Storage-fiókjában találhatók. Ezek a mappák Azure-adatszolgáltatásokkal hozhatók létre. A mappákhoz való csatlakozással az elemzők zökkenőmentesen dolgozhatnak az adatokkal a Power BI-ban. 

Az Azure Data Lake Storage Gen2 és az adatfolyamok integrációjáról, így a vállalati Azure Data Lake-ben elhelyezkedő adatfolyamok létrehozásáról az [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md) című cikkből tájékozódhat.

## <a name="dataflow-capabilities-on-power-bi-premium"></a>Adatfolyam-funkciók a Power BI Premiumban

A Power BI Premium-előfizetésben használt adatfolyam-funkciókhoz és számítási feladatokhoz be kell kapcsolni az adatfolyam számítási feladatait az adott Prémium szintű kapacitásban. A következő táblázat ismerteti az adatfolyam-funkciókat és azok kapacitásait Power BI Pro-fiók használata esetén, illetve ezek összehasonlítását a Power BI Premiummal.


|Adatfolyam-funkció | Power BI Pro |   Power BI Premium |
|---------|---------|---------|
|Ütemezett frissítés| Naponta 8|  48|
|Összes tárhely| 10 GB/felhasználó  |100 TB/csomópont|
|Adatfolyam-készítés a Power Query Online-nal|    +   |+|
|Adatfolyam-kezelés a Power BI-ban|   +|  +|
|Adatfolyamok adatösszekötője a Power BI Desktopban|  +|  +|
|Azure-integráció|    +|  +|
|Számított entitások (tárhelyen belüli átalakítások az M-en keresztül) | |   +|
|Új összekötők|    +|  +|
|Adatfolyamok növekményes frissítése|  |   +|
|Futtatás Power BI Premium-kapacitáson/Átalakítások párhuzamos végrehajtása|   |   +|
|Adatfolyamokhoz csatolt entitások| |        +|
|Szabványosított séma/Beépített támogatás a Common Data Service-hez|  +|  +|

Az adatfolyamok számítási feladatainak prémium szintű kapacitásban történő engedélyezéséről lásd a [Számítási feladatok konfigurálása prémium szintű kapacitásban](service-admin-premium-workloads.md) cikket. Adatfolyam számítási feladatok több földrajzi helyes kapacitásokban jelenleg nem érhetők el.

## <a name="summary-of-self-service-data-prep-for-big-data-in-power-bi"></a>A big data típusú adatok önkiszolgáló adat-előkészítésének összefoglalása – Power BI
Ahogy korábban említettük, több olyan forgatókönyv és példa is létezik, amelyben az **adatfolyamok** nagyobb mértékű vezérlést és gyorsabb elemzést biztosítanak az üzleti adatokhoz. A Common Data Servcie által meghatározott szabványos adatmodellel (sémával) az adatfolyamok importálhatják a fontos üzleti adatokat, és rövid idő alatt előkészíthetik azokat modellezéshez és BI-elemzésekhez. Mindez korábban hónapokig, vagy akár tovább is eltarthatott. 

Az üzleti adatok a **Common Data Service** szabványosított formátumában való tárolásával a BI-szakértők (vagy a fejlesztők) olyan alkalmazásokat hozhatnak létre, amelyek gyors, könnyű és automatikus vizualizációkat és jelentéseket készítenek. Íme néhány (nem kimerítő) példa:


* Az adatok társítása szabványos entitásokkal a Common Data Service-ben az adatok egységesítéséhez és az ismert séma azonnal alkalmazható elemzések készítéséhez való használatához
* Saját egyéni entitások létrehozása a szervezeti adatok egységesítéséhez 
* **Külső adatok** használata és frissítése adatfolyam részeként, valamint ezen adatok importálásának engedélyezése elemzésekhez
* Adatfolyamok kezdeti lépései fejlesztőknek


## <a name="next-steps"></a>Következő lépések

Ez a cikk áttekintést nyújtott a big data típusú adatok Power BI-beli önkiszolgáló adat-előkészítéséről és annak számos használati módjáról. A következő cikkekben részletes információkat találhat az adatfolyamok gyakori használati forgatókönyveiről. 

* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban (előzetes verzió)](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal (előzetes verzió)](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások a Power BI-adatfolyamokhoz (előzetes verzió)](service-dataflows-developer-resources.md)
* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)

A Power Queryvel és az ütemezett frissítésekkel kapcsolatos további információt a következő cikkekben talál:
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Ütemezett frissítés beállítása](refresh-scheduled-refresh.md)

A Common Data Modellel kapcsolatos további információt a témát áttekintő cikkben talál:
* [Common Data Model – áttekintés](https://docs.microsoft.com/powerapps/common-data-model/overview)

