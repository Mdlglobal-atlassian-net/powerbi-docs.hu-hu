---
title: Az Analysis Services többdimenziós adatai a Power BI Desktopban
description: Az Analysis Services többdimenziós adatai a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b68cbafd3572100d5983eb8b17f07464d39baf3f
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56217068"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Csatlakozás SSAS többdimenziós modellekhez a Power BI Desktopban
A Power BI Desktopban hozzáférhet az **SSAS többdimenziós modellekhez** (gyakori nevükön **SSAS MD-khez**).

Ha **SSAS MD**-adatbázishoz szeretne csatlakozni, válassza az **Adatok lekérése &gt; Adatbázis &gt; SQL Server Analysis Services-adatbázis** lehetőséget az alábbi ábrának megfelelően:

![](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Az **SSAS többdimenziós modellek** csatlakoztatása élő kapcsolati módban a Power BI szolgáltatásban és a Power BI Desktopban egyaránt támogatott. Az **SSAS többdimenziós modelleket** élő módban használó jelentéseket közzé is tehet és fel is tölthet a Power BI szolgáltatásba.

## <a name="capabilities-and-features-of-ssas-md"></a>Az SSAS MD képességei és funkciói
Az alábbi szakaszok a Power BI–SSAS MD kapcsolatok funkcióit és képességeit ismertetik.

### <a name="tabular-metadata-of-multidimensional-models"></a>Többdimenziós modellek táblázatos metaadatai
Az alábbi táblázat a többdimenziós objektumok és a Power BI Desktopba visszaadott metaadatok között fennálló megfeleltetéseket tartalmazza. A Power BI lekérdezi a modellből a táblázatos metaadatokat, majd azok alapján futtatja a megfelelő DAX-lekérdezéseket az Analysis Servicesben a vizualizációk, például a táblák, mátrixok, diagramok vagy szeletelők létrehozásakor.

| BISM – többdimenziós objektum | Táblázatos metaadatok |
| --- | --- |
| Kocka |Modell |
| Kockadimenzió |Tábla |
| Dimenzióattribútumok (kulcsok), Név |Oszlopok |
| Mértékcsoport |Tábla |
| Mérték |Mérték |
| Hozzárendelt mértékcsoport nélküli mértékek |A *Mértékek* elnevezésű táblában |
| Mértékcsoport -> Kockadimenzió-kapcsolat |Kapcsolat |
| Perspektíva |Perspektíva |
| KPI |KPI |
| Felhasználói/szülő-gyermek hierarchiák |Hierarchiák |

### <a name="measures-measure-groups-and-kpis"></a>Mértékek, mértékcsoportok és KPI-k
A többdimenziós kockákban lévő mértékcsoportok a Power BI-ban táblákként jelennek meg, amelyek a ∑ jellel vannak jelölve a **Mezők** panelen. A társított mértékcsoporttal nem rendelkező számított mértékek egy *Mértékek* nevű speciális táblában vannak összegyűjtve a táblázatos metaadatok között.

A többdimenziós modellekben a kockákban lévő mértékek vagy KPI-k egy halmazát definiálhatja egy *Megjelenítési mappa* elemeiként, ami segít leegyszerűsíteni az összetettebb modelleket. A Power BI felismeri a megjelenítési mappákat a táblázatos metaadatok között, és a mértékeket és KPI-ket azokon belül jeleníti meg. A többdimenziós adatbázisokban lévő KPI-k az *Értékeket*, a *Célokat*, az *Állapotgrafikákat* és a *Trendgrafikákat* támogatják.

### <a name="dimension-attribute-type"></a>Dimenzióattribútum-típus
A többdimenziós modellek támogatják a dimenzióattribútumok társítását adott dimenzióattribútum-típusokhoz. Például a **Földrajz** dimenzióban a *Város*, *Állam-Tartomány*, *Ország* és *Irányítószám* dimenzióattribútumokhoz megfelelő földrajzi típusok vannak rendelve, és a táblázatos metaadatok között szerepelnek. A Power BI felismeri a metaadatokat, így lehetővé teszi a térképek vizualizációját. Ezek a társítások a Power BI **Mező** panelén az elem mellett szereplő *leképezés* ikonról ismerhetőek fel.

A Power BI emellett képeket is képes renderelni, ha megad egy mezőt, amely a képek URL-címeit tartalmazza. Az ilyen mezőket *ImageURL* típusúként adhatja meg az SQL Server Data Toolsban (vagy utána a Power BI-ban), és a típusadatokat a Power BI a táblázatos metaadatok között kapja meg. A Power BI ezután le tudja kérni az URL-címekről az adott képeket, és meg tudja őket jeleníteni vizualizációként.

### <a name="parent-child-hierarchies"></a>Szülő-gyermek hierarchiák
A többdimenziós modellek támogatják a szülő-gyermek hierarchiákat, amelyek a táblázatos metaadatok között *hierarchiaként* jelennek meg. A szülő-gyermek hierarchia rejtett oszlopként jelenik meg a táblázatos metaadatokban. A szülő-gyermek dimenzió kulcsattribútuma a táblázatos metaadatoknál nem látható.

### <a name="dimension-calculated-members"></a>Dimenziók számított tagjai
A többdimenziós modellek támogatják a *számított tagok* különféle típusainak létrehozását. A számított tagok két leggyakoribb típusa:

* Az attribútumhierarchiákban lévő számított tagok, amelyeknek a *Mind* nem testvére
* A felhasználói hierarchiákban lévő számított tagok

A többdimenziós modellek *az attribútumhierarchiákban lévő számított tagokat* egy oszlop értékeiként jelenítik meg. Az ilyen típusú számított tagok megjelenítéséhez kapcsolódik néhány további lehetőség és korlátozás:

* A dimenzióattribútum rendelkezhet egy választható *UnknownMember* taggal.
* A számított tagokat tartalmazó attribútum nem lehet a dimenzió kulcsattribútuma, hacsak nem ez a dimenzió egyetlen attribútuma.
* A számított tagokat tartalmazó attribútum nem lehet szülő-gyermek attribútum.

A felhasználói hierarchiák számított tagjai nem jelennek meg a Power BI-ban. A felhasználói hierarchiákban számított tagokkal rendelkező kockákhoz lehetséges csatlakozni, de a számított tagok nem lesznek láthatók, ha nem felelnek meg az előző felsorolásban említett korlátozásoknak.

### <a name="security"></a>Biztonság
A többdimenziós modellek támogatják a dimenzió- és cellaszintű biztonság *szerepköralapú* megvalósítását. Ha a Power BI-jal kapcsolódik egy kockához, a rendszer hitelesíti és ellenőrzi a vonatkozó engedélyeit. Ha a felhasználón *dimenzióbiztonság* érvényesül, a vonatkozó dimenziótagokat nem fogja látni a Power BI-ban. Ha a felhasználó rendelkezik definiált *cellabiztonsági* engedéllyel, ahol bizonyos cellák korlátozva vannak, az adott felhasználó a Power BI használatával nem tud a kockához kapcsolódni.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
Az **SSAS MD** használatára bizonyos korlátozások vonatkoznak:

* A kiszolgálóknak az Analysis Services SQL Server 2012 SP1 CU4 vagy azt követő verzióját kell futtatniuk, hogy a Power BI Desktop SSAS MD-összekötője megfelelően működjön.
* A *Műveletek* és az *Elnevezett készletek* nem jelennek meg a Power BI-ban, azonban továbbra is lehet kapcsolódni a *Műveleteket* vagy *Elnevezett készleteket* is tartalmazó kockákhoz, és vizualizációkat és jelentéseket is létre lehet hozni.
* Előfordulhat olyan hiba, hogy bár a Power BI megjeleníti az SSAS-modell metaadatait, de mégsem tud adatokat beolvasni a modellből. Ez olyankor fordulhat elő, amikor a rendszerre csak az MSOLAP-szolgáltató 32-bites verziója van telepítve, és nem rendelkezik a 64-bites verzióval. Ilyenkor a 64-bites verzió telepítése megoldhatja a problémát.
* Többdimenziós SSAS-modellhez élő kapcsolattal rendelkező jelentés létrehozásakor nem hozhat létre „jelentésszintű” mértékeket. Csak az MD modellben definiált mértékek állnak rendelkezésre.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Az SSAS MD támogatott szolgáltatásai a Power BI Desktopban
Az SSAS MD következő szolgáltatásai támogatottak a Power BI Desktopban:

* Az alábbi elemek használata támogatott az **SSAS MD** jelen kiadásában (a szolgáltatásokkal kapcsolatban [további információk](https://msdn.microsoft.com/library/jj969574.aspx) is rendelkezésre állnak):
  * Megjelenítési mappák
  * KPI-trendek
  * Alapértelmezett tagok
  * Dimenzióattribútumok
  * Dimenziók számított tagjai (önálló valós tagnak kell lennie, ha a dimenzió több attribútummal is rendelkezik, csak akkor lehet a dimenzió kulcsattribútuma, ha ez az egyetlen attribútum, valamint nem lehet szülő-gyermek attribútum)
  * Dimenzióattribútum-típusok
  * Hierarchiák
  * Mértékek (mértékcsoportokkal vagy anélkül)
  * Mértékek változatként
  * KPI-k
  * Képek URL-címei
  * Dimenzióbiztonság

## <a name="troubleshooting"></a>Hibaelhárítás 
A következő lista tartalmazza az SQL Server Analysis Services (SSAS) szolgáltatáshoz való kapcsolódáskor előforduló összes ismert problémát. 

* **Hiba: A modellséma nem tölthető be** – Ez a hiba általában akkor fordul elő, ha az Analysis Serviceshez csatlakozó felhasználó nem rendelkezik hozzáféréssel az adatbázishoz/adatkockához.
