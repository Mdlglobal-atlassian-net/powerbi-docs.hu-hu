---
title: Az Analysis Services többdimenziós adatai a Power BI Desktopban
description: Az SQL Server Analysis Services (SSAS) többdimenziós adatai a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83287694"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Csatlakozás többdimenziós SSAS-modellekhez a Power BI Desktopban

A Power BI Desktopban hozzáférhet az *SSAS többdimenziós modellekhez* (gyakori nevükön *SSAS MD-khez*).

Ha SSAS MD-adatbázishoz szeretne csatlakozni, válassza az **Adatok beolvasása**, majd az **Adatbázis** > **SQL Server Analysis Services-adatbázis**, végül a **Csatlakozás** lehetőséget:

![SQL Server Analysis Services- (SSAS-) adatbázis, Adatok beolvasása párbeszédpanel, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Az SSAS többdimenziós modelljeit a Power BI szolgáltatás és a Power BI Desktop is támogatja élő kapcsolati módban. Az **SSAS többdimenziós modelleket** élő módban használó jelentéseket közzéteheti és feltöltheti a Power BI szolgáltatásba.

## <a name="capabilities-and-features-of-ssas-md"></a>Az SSAS MD képességei és funkciói

Az alábbi szakaszok a Power BI–SSAS MD kapcsolatok funkcióit és képességeit ismertetik.

### <a name="tabular-metadata-of-multidimensional-models"></a>Többdimenziós modellek táblázatos metaadatai

Az alábbi táblázat a többdimenziós objektumok és a Power BI Desktopba visszaadott metaadatok között fennálló megfeleltetéseket tartalmazza. A Power BI lekérdezi a modellből a táblázatos metaadatokat. A Power BI Desktop a visszaadott metaadatok alapján futtatja a megfelelő DAX-lekérdezéseket az SSAS-ben a vizualizációk, például a táblák, mátrixok, diagramok vagy szeletelők létrehozásakor.

| BISM – többdimenziós objektum | Táblázatos metaadatok |
| --- | --- |
| Kocka |Modell |
| Kockadimenzió |Táblázat |
| Dimenzióattribútumok (kulcsok), név |Oszlopok |
| Mértékcsoport |Táblázat |
| Mérték |Mérték |
| Hozzárendelt mértékcsoport nélküli mértékek |A *Mértékek* elnevezésű táblában |
| Mértékcsoport -> Kockadimenzió-kapcsolat |Kapcsolat |
| Perspektíva |Perspektíva |
| KPI |KPI |
| Felhasználói/szülő-gyermek hierarchiák |Hierarchiák |

### <a name="measures-measure-groups-and-kpis"></a>Mértékek, mértékcsoportok és KPI-k

A többdimenziós kockákban lévő mértékcsoportok szigma (∑) jellel megjelölt táblákként jelennek meg a **Mezők** panelen. A társított mértékcsoport nélküli számított mértékek egy *Mértékek* nevű speciális táblában vannak összegyűjtve a táblázatos metaadatok között.

Az összetett modellek egyszerűsítése érdekében a többdimenziós modellekben a kockákban lévő mértékek vagy KPI-k egy halmazát definiálhatja egy *Megjelenítési mappa* elemeiként. A Power BI felismeri a megjelenítési mappákat a táblázatos metaadatok között, és a mértékeket és KPI-ket azokon belül jeleníti meg. A többdimenziós adatbázisokban lévő KPI-k az *Értékeket*, a *Célokat*, az *Állapotgrafikákat* és a *Trendgrafikákat* támogatják.

### <a name="dimension-attribute-type"></a>Dimenzióattribútum-típus

A többdimenziós modellek támogatják a dimenzióattribútumok társítását adott dimenzióattribútum-típusokhoz. Például a **Földrajz** dimenzióban a *Város*, *Állam-Tartomány*, *Ország* és *Irányítószám* dimenzióattribútumokhoz megfelelő földrajzi típusok vannak rendelve, és a táblázatos metaadatok között szerepelnek. A Power BI felismeri a metaadatokat, így lehetővé teszi a térképek vizualizációját. Ezek a társítások a Power BI **Mezők** panelén az elem mellett szereplő *leképezés* ikonról ismerhetőek fel.

A Power BI emellett képeket is képes renderelni, ha megad egy mezőt, amely a képek URL-címeit tartalmazza. Ezeket a mezőket *ImageURL* típusúakként is megadhatja az SQL Server Data Toolsban (vagy aztán a Power BI-ban). A típusinformáció ekkor a táblázatos metaadatok között lesz megadva a Power BI-nak. A Power BI ez után le tudja kérni az URL-címekről az adott képeket, és meg tudja őket jeleníteni vizualizációként.

### <a name="parent-child-hierarchies"></a>Szülő-gyermek hierarchiák

A többdimenziós modellek támogatják a szülő-gyermek hierarchiákat, amelyek a táblázatos metaadatok között *hierarchiaként* jelennek meg. A szülő-gyermek hierarchia rejtett oszlopként jelenik meg a táblázatos metaadatokban. A szülő-gyermek dimenzió kulcsattribútuma a táblázatos metaadatoknál nem látható.

### <a name="dimension-calculated-members"></a>Dimenziók számított tagjai

A többdimenziós modellek támogatják a *számított tagok* különféle típusainak létrehozását. A számított tagok két leggyakoribb típusa:

* Az attribútumhierarchiákban lévő számított tagok, amelyeknek a *Mind* nem testvére
* A felhasználói hierarchiákban lévő számított tagok

A többdimenziós modellek *az attribútumhierarchiákban lévő számított tagokat* egy oszlop értékeiként jelenítik meg. Az ilyen típusú számított tagok elérhetővé tételéhez kapcsolódik néhány további lehetőség és korlátozás:

* A dimenzióattribútum rendelkezhet egy választható *UnknownMember* taggal.

* A számított tagokat tartalmazó attribútum nem lehet a dimenzió kulcsattribútuma, hacsak nem ez a dimenzió egyetlen attribútuma.

* A számított tagokat tartalmazó attribútum nem lehet szülő-gyermek attribútum.

A felhasználói hierarchiák számított tagjai nem jelennek meg a Power BI-ban. Ehelyett csatlakozhat a felhasználói hierarchiák számított tagjait tartalmazó kockához. A számított tagokat azonban csak akkor fogja látni, ha azokra nem vonatkoznak az előzőkben felsorolt korlátozások.

### <a name="security"></a>Biztonság

A többdimenziós modellek támogatják a dimenzió- és cellaszintű biztonság *szerepköralapú* megvalósítását. Ha a Power BI-jal kapcsolódik egy kockához, a rendszer hitelesíti és ellenőrzi a vonatkozó engedélyeit. Ha a felhasználón *dimenzióbiztonság* érvényesül, a vonatkozó dimenziótagokat nem fogja látni a Power BI-ban. Ha a felhasználó *cellabiztonsági* engedélyt definiált, ahol bizonyos cellák korlátozva vannak, az adott felhasználó a Power BI használatával nem tud a kockához kapcsolódni.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Az SSAS MD használatára bizonyos korlátozások vonatkoznak:

* Az élő kapcsolatokat csak az SQL Server 2014 Enterprise és a BI kiadásai támogatják. Az SQL Server standard kiadása esetén SQL Server 2016 vagy újabb verzió szükséges az élő kapcsolatokhoz.

* A *műveletek* és az *elnevezett halmazok* nem jelennek meg a Power BI-ban. Vizualizációk és jelentések létrehozása céljából továbbra is lehetséges a műveleteket vagy elnevezett halmazokat is tartalmazó kockákhoz kapcsolódni.

* Előfordulhat, hogy amikor a Power BI egy SSAS-modell metaadatait jeleníti meg, a modellből nem lehet adatokat lekérni. Ez a helyzet akkor állhat elő, ha az MSOLAP-szolgáltató 32 bites verziója telepítve van, a 64 bites verzió viszont nincs. Ilyenkor a 64-bites verzió telepítése megoldhatja a problémát.

* Többdimenziós SSAS-modellhez élő kapcsolattal rendelkező jelentés létrehozásakor nem hozhat létre *jelentésszintű* mértékeket. Csak az MD modellben definiált mértékek állnak rendelkezésre.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Az SSAS MD Power BI Desktopban támogatott szolgáltatásai

Az SSAS MD jelenlegi kiadásában az alábbi elemek felhasználása támogatott. A funkciókról a [Power View többdimenziós modellekhez](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014) című cikk nyújt részletes leírást.

* Alapértelmezett tagok
* Dimenzióattribútumok
* Dimenzióattribútum-típusok
* Dimenziók számított tagjai, amelyek:
  * csak egyedülálló valódi tagok lehetnek, ha a dimenziónak több attribútuma is van;
  * csak akkor lehetnek a dimenzió kulcsattribútumai, ha nincs más attribútum; és
  * nem lehetnek szülő-gyermek attribútumok.
* Dimenzióbiztonság
* Megjelenítési mappák
* Hierarchiák
* Képek URL-címei
* KPI-k
* KPI-trendek
* Mértékek (mértékcsoportokkal vagy anélkül)
* Mértékek változatként

## <a name="troubleshooting"></a>Hibaelhárítás

A következő lista tartalmazza az SQL Server Analysis Services (SSAS) szolgáltatáshoz való kapcsolódáskor előforduló összes ismert problémát.

* **Hiba: A modellséma nem tölthető be** – Ez a hiba általában akkor fordul elő, ha az Analysis Serviceshez csatlakozó felhasználó nem rendelkezik hozzáféréssel az adatbázishoz/adatkockához.
