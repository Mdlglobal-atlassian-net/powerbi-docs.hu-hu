---
title: Kapcsolódás a Power BI szolgáltatásban lévő adatkészletekhez a Power BI Desktopból
description: Közös adatkészlet használata több Power BI Desktop-jelentéshez és a jelentés életciklusának kezelése
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3679a2f3ab98e1f54ead364e4ef4bf65d382a9d5
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578589"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Kapcsolódás a Power BI szolgáltatásban lévő adatkészletekhez a Power BI Desktopból
Létrehozhat élő kapcsolatot a Power BI szolgáltatás egy megosztott adatkészletével, és számos különböző jelentést hozhat létre ugyanabból az adatkészletből. Ez azt jelenti, hogy létrehozhatja a tökéletes adatmodellt a Power BI Desktopban, közzéteheti azt a Power BI szolgáltatásban, majd mások létrehozhatnak több különböző jelentést (külön .pbix fájlokban) a közös adatmodellből. Ennek a szolgáltatásnak **Élő kapcsolat Power BI szolgáltatással** a neve.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

A szolgáltatásnak számos előnye van, beleértve a jelen cikkben később tárgyalt ajánlott eljárásokat. Vonatkozik rá néhány megfontolandó szempont és korlátozás is, olvassa el azokat is alaposan – a cikk végén találja őket.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Az Élő kapcsolat Power BI-szolgáltatással használata a jelentések életciklusának kezeléséhez
A Power BI népszerűségével kapcsolatban az egyik kihívást a jelentések, irányítópultok és az alapul szolgáló adatmodellek elterjedése jelenti. Ennek a következő az oka: egyszerű lenyűgöző jelentéseket létrehozni a **Power BI Desktopban**, majd megosztani ([közzétenni](desktop-upload-desktop-files.md)) ezeket a jelentéseket a **Power BI szolgáltatásban**, majd nagyszerű irányítópultokat létrehozni az adatkészletekből. Minthogy oly sokan tettek így, az azonos (vagy majdnem azonos) adatkészletek használata, annak észben tartása, hogy melyik jelentés melyik adatkészleten alapult – és melyik adatkészlet mennyire naprakész –, gyakran már komoly kihívást jelent. Az **Élő kapcsolat Power BI-szolgáltatással** a válasz erre a kihívásra, hiszen egyszerűbbé és konzisztenssé teszi a közös adatkészleten alapuló jelentések és irányítópultok létrehozását, megosztását és bővítését.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Mindenki által használható adatkészletek létrehozása, majd megosztása
Tegyük fel, hogy Anna (egy üzleti elemző) a csapata tagja, és nagyon ért a jó adatmodellek (más néven adatkészletek) létrehozásához. Anna a szakértelmére támaszkodva létrehoz egy adatkészletet és egy jelentést, majd megosztja a jelentést a **Power BI szolgáltatásban**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Mindenki rajong a jelentésért és az adatkészletért, és itt kezdődik a gond – a csapat összes tagja megpróbálja létrehozni Anna adatkészletéből a *saját verzióját*, majd megosztják a jelentéseket a csapattal. Hirtelen különböző adatkészletekre támaszkodó jelentések egész hada jelenik meg a csapat munkaterületén a **Power BI szolgáltatásban**. Melyik a legújabb? Egyeznek vajon az adatkészletek, vagy csak majdnem? Milyen különbségeik vannak? Az **Élő kapcsolat Power BI-szolgáltatással** révén a helyzet sokkal egyszerűbbé válik. A következő szakaszban meglátjuk, hogyan tudják felhasználni mások Anna közzétett adatkészletét a saját jelentéseikhez, és hogyan használhatja mindenki ugyanazt a stabil, ellenőrzött és megosztott adatkészletet a saját egyedi jelentéseihez.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Csatlakozás a Power BI szolgáltatás adatkészletéhez élő kapcsolattal
Amint Anna létrehozza a jelentést (és az adatkészletet, amelyen az alapul), és közzéteszi a **Power BI szolgáltatásban**, megjelenik a csapata munkaterületén a Power BI szolgáltatásban. Most már a munkaterületen mindenki látja és használhatja is.

További információ a munkaterületekről: [Alkalmazás-munkaterületek](service-create-workspaces.md).

A munkaterület más tagjai ekkor létrehozhatnak egy élő kapcsolatot Anna megosztott adatmodelljével (az **Élő kapcsolat Power BI-szolgáltatással** szolgáltatás révén), és létrehozhatják az *ő eredeti adatkészlete* alapján a saját egyedi jelentéseiket.

A következő ábrán láthatjuk, hogy Anna létrehoz egy **Power BI Desktop**-jelentést, majd közzéteszi (az adatmodellel együtt) a **Power BI szolgáltatásban**. Ekkor a munkaterület más tagjai csatlakozhatnak Anna adatmodelljéhez az **Élő kapcsolat Power BI-szolgáltatással** használatával, és létrehozhatják a saját egyedi jelentéseiket Anna adatkészlete alapján.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Az adatkészletek csak egy munkaterületen vannak megosztva. Az Élő kapcsolat Power BI-szolgáltatással létrehozásához az adatkészletnek, amelyhez csatlakozni kíván, egy olyan megosztott munkaterületen kell lennie, amelynek Ön a tagja.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Lépésenkénti útmutató az Élő kapcsolat Power BI-szolgáltatással használatához
Most, hogy már tudjuk, milyen hasznos az **Élő kapcsolat Power BI-szolgáltatással** funkció, és hogyan használhatjuk ajánlott eljárásként a jelentések életciklusának kezeléséhez, nézzük végig, hogyan jutottunk el Anna nagyszerű jelentésétől (és adatkészletétől) egy olyan adatkészletig, amelyet a Power BI-munkaterületet használó csapattársai is használhatnak.

### <a name="publish-a-power-bi-report-and-dataset"></a>Power BI-jelentés és -adatkészlet közzététele
Az első lépés, ha egy jelentés életciklusát az **Élő kapcsolat Power BI-szolgáltatással** használatával kezeljük, hogy olyan jelentésünk (és adatkészletünk) legyen, amelyet a csapattársaink is szívesen használnának. Tehát Annának előbb **közzé kell tennie** a jelentését a **Power BI Desktopból**. Ehhez a Power BI Desktop **Kezdőlap** szalagján a **Közzététel** lehetőséget választja.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Ha nincs bejelentkezve a Power BI szolgáltatásfiókjába, a rendszer felkéri erre.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Innen kiválaszthatja a cél munkaterületet, ahol közzéteszi a jelentést és az adatkészletet. Ne feledje, csak olyan csapattagok férhetnek hozzá a jelentés adatkészletéhez az **Élő kapcsolat Power BI-szolgáltatással** segítségével, akik rendelkeznek hozzáféréssel a munkaterülethez, ahol a jelentés közzé van téve.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

Megkezdődik a közzétételi folyamat, és a **Power BI Desktop** megjeleníti a folyamatot.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Ha kész, a **Power BI Desktop** tájékoztatja a sikerről, és biztosítja a hivatkozásokat, amelyekkel elérhető maga a jelentés a **Power BI szolgáltatásban**, illetve amelyekkel **gyors elemzéseket** kérhet le a jelentésről.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Ezután nézzük meg, hogyan csatlakozhatnak az adatkészlethez, majd hozhatják létre a saját jelentéseiket a csapattársak, akiknek hozzáférésük van a munkaterülethez, ahol a jelentés (és az adatkészlet) közzé lett téve.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Az Élő kapcsolat Power BI-szolgáltatással létrehozása a közzétett adatkészlethez
Ha csatlakozni szeretne a közzétett jelentéshez, és létre szeretné hozni a saját jelentését a közzétett adatkészlet alapján, válassza az **Adatok lekérése** lehetőséget a **Power BI Desktop** **Kezdőlap** menüszalagján, és válassza a **Power BI szolgáltatás** lehetőséget. Ezt elérheti az a következőképp is: **Adatok lekérése > Online szolgáltatások > Power BI szolgáltatás**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_08.png)

Ha még nem jelentkezett be a Power BI-ba, a rendszer felkéri erre. Ha már bejelentkezett, megjelenik egy ablak, amely mutatja, melyik munkaterületeken tag. Innen kiválaszthatja, melyik munkaterület tartalmazza az adatkészletet, amelyhez létre szeretné hozni az **Élő kapcsolat Power BI-szolgáltatással** kapcsolatot.

A munkaterület mellett zárójelben látható szám azt jelzi, hogy hány megosztott adatkészlet érhető el az adott munkacsoportban, a balra látható háromszög kiválasztásával pedig kibonthatja a munkaterületet, hogy kiválaszthassa a megosztott adatkészletet.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_09a.png)

Érdemes megfigyelni néhány elemet az előző **Élő kapcsolat Power BI-szolgáltatással** ablakból:

* Kereshet megosztott adatkészletre, de a keresési eredmények a kibontott elemekre korlátozódnak, és nem fog közöttük még nem kibontott munkaterület szerepelni.
* A keresés bővítéséhez egynél több munkaterületet is kibonthat.

Amikor a **Betöltés** lehetőséget választja az ablakban, létrehoz egy élő kapcsolatot a kiválasztott adatkészlettel, azaz a látott adatok (a mezők és a hozzá tartozó értékek) valós időben töltődnek be a **Power BI Desktopba**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Ekkor létrehozhat és megoszthat (ahogy mások is) egyéni jelentéseket ugyanabból az adatkészletből. Ideális megoldás, ha egy hozzáértő személy (mint Anna) hozza létre a megfelelően kialakított adatkészletet, és több csapattag is használhatja ezt a megosztott adatkészletet a saját jelentéseihez.

> [!NOTE]
> Amikor a **Power BI szolgáltatással** létrehozott élő kapcsolat segítségével hoz létre adatkészleten alapuló jelentéseket, csak a használt adatkészletet tartalmazó Power BI szolgáltatás munkaterületén teheti közzé.
> 
> 

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
Az **Élő kapcsolat Power BI-szolgáltatással** használatára vonatkozik néhány korlátozás és egyéb szempont.

* A munkaterület csak olvasási jogosultsággal rendelkező tagjai nem csatlakozhatnak a **Power BI Desktop** adatkészleteihez.
* A közzétett adatkészletekhez csak azok a felhasználók csatlakozhatnak az **Élő kapcsolat Power BI-szolgáltatással** segítségével, akik ugyanazon **Power BI szolgáltatás** munkaterületének tagjai. A felhasználók tartozhatnak (és gyakran tartoznak is) egynél több munkaterülethez.
* Mivel ez egy élő kapcsolat, a bal oldali navigációs sáv és a modellezés le van tiltva, hasonlóan ahhoz, amikor az **SQL Server Analysis Services** szolgáltatáshoz kapcsolódik.
* Mivel ez egy élő kapcsolat, az RLS (sor- és szerepkörszintű biztonság), a OneDrive Vállalati verzió és más hasonló kapcsolati viselkedések kényszerítettek, épp úgy, mint amikor az **SQL Server Analysis Services** szolgáltatáshoz csatlakozik.
* Amikor kiválasztja, hogy mely adatkészlethez csatlakozik a **Power BI szolgáltatásban**, a keresőmező csak a kibontott munkaterületekre vonatkozik.
* Ha tulajdonos módosítja az eredeti .pbix fájlt, azzal felülírja a **Power BI szolgáltatásban** megosztott adatkészletet és jelentést.
* Munkaterület tagjai az eredetileg megosztott jelentést nem cserélhetik ki. Ha ezzel próbálkozik, a rendszer felszólítja a fájl átnevezésére és közzétételére.
* Ha törli a **Power BI szolgáltatásban** megosztott adatkészletet, akkor más **Power BI Desktop**-fájlok (.pbix) nem működnek jól, vagy nem tudják megjeleníteni a vizualizációkat.
* Tartalomcsomagok esetében először létre kell hoznia egy másolatot a tartalomcsomagról, mielőtt alapul használhatná egy .pbix jelentés és adatkészlet megosztására a **Power BI szolgáltatásban**.
* A *Saját szervezet* tartalomcsomagjai esetében, ha már másolva lettek, nem lehet kicserélni a szolgáltatáson létrehozott jelentést és/vagy egy élő kapcsolattal rendelkező tartalomcsomag másolása részeként létrehozott jelentést. Ha ezzel próbálkozik, a rendszer felszólítja a fájl átnevezésére és közzétételére. Ebben a helyzetben csak a közzétett élő kapcsolattal rendelkező jelentéseket cserélheti le.
* Amikor a **Power BI szolgáltatással** létrehozott élő kapcsolat segítségével hoz létre adatkészleten alapuló jelentést, csak a használt adatkészletet tartalmazó Power BI szolgáltatás munkaterületén teheti közzé.
* Ha töröl egy megosztott adatkészletet a **Power BI szolgáltatásból**, akkor nem lesz tovább hozzáférése ahhoz az adatkészlethez a **Power BI Desktopban**.

