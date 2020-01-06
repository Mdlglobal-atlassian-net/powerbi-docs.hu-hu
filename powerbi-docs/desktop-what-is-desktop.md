---
title: Mi az a Power BI Desktop?
description: Ismerkedjen meg a Power BI Desktoppal és használatának első lépéseivel
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 01e5effcf5f72dd110005815e2ba86c9a6731a70
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/06/2020
ms.locfileid: "73865132"
---
# <a name="what-is-power-bi-desktop"></a>Mi az a Power BI Desktop?

A **Power BI Desktop** egy ingyenes alkalmazás, amelyet a helyi számítógépén telepíthet, és amellyel csatlakozhat adatokhoz, amelyeket átalakíthat és vizualizációkkal megjeleníthet. A **Power BI Desktop** használatával több különféle adatforráshoz csatlakozhat, és ezeket adatmodellekbe kombinálhatja (ezt modellezésnek is hívjuk), amelyekkel vizualizációkat és vizualizáció-csoportokat hozhat létre, majd jelentésekként megoszthatja őket a cégen belüli más felhasználókkal. Az üzleti intelligenciát alkalmazó projekteken dolgozó legtöbb felhasználó a **Power BI Desktop** használatával hoz létre jelentéseket, amelyeket a **Power BI szolgáltatással** oszt meg másokkal.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

A **Power BI Desktop** leggyakoribb alkalmazási helyzetei az alábbiak:

* Csatlakozás adatokhoz
* Az adatok átalakítása és megtisztítása és adatmodell létrehozása
* Vizualizációk, például diagramok és grafikonok létrehozása, amelyekkel vizuálisan bemutathatók az adatok
* Vizualizációkból álló jelentések létrehozása egy vagy több jelentésoldalon
* A jelentés megosztása másokkal a **Power BI szolgáltatás** használatával

Az ilyen feladatokat végzőket általában *adatelemzőknek* nevezzük (ritkábban egyszerűen *elemzőknek* is) vagy üzleti intelligenciával foglalkozó szakembereknek (őket gyakran *jelentéskészítőknek* is nevezzük). Ezzel együtt azonban nagyon sokan használják még a **Power BI Desktopot**, akik nem tekintik magukat elemzőnek vagy jelentéskészítőnek, de szeretnének lenyűgöző jelentéseket létrehozni, vagy sok különféle forrásból származó adatból adatmodelleket szeretnének létrehozni, amelyeket aztán megosztanak a cégen belüli munkatársakkal.

A Power BI Desktopban három nézet található, amelyek a vászon bal oldalán jelennek meg. Ezek a következők (megjelenési sorrendben):
* **Jelentés nézet** – Itt hozhat létre jelentéseket és vizualizációkat, és a kreatív folyamat nagy része itt zajlik.
* **Adatnézet** – Itt láthatja a jelentéshez tartozó adatmodellben használt táblákat, mértékeket és egyéb adatokat, és itt alakíthatja át az adatokat a jelentésmodellhez leginkább megfelelő formában.
* **Modellnézet** – Ebben a nézetben megtekintheti és kezelheti az adatmodell tábláinak kapcsolatait.

A következő képen a vászon bal oldalán látható három nézet található:

![különböző nézetek](media/desktop-what-is-desktop/what-is-desktop-07.png)


A **Power BI Desktoppal** összetett és gazdag vizualizációkkal rendelkező jelentéseket hozhat létre sok különféle adatforrás használatával, és mindezt egyetlen jelentésként oszthatja meg a cég többi munkatársával. 

## <a name="connect-to-data"></a>Csatlakozás adatokhoz
A **Power BI Desktoppal** való munka első lépéseként csatlakoznia kell az adatokhoz. A **Power BI Desktop** használatával számos adatforráshoz csatlakozhat. Adatokhoz való csatlakozáshoz válassza ki a **Kezdőlap** menüszalagot, majd az **Adatok beolvasása > Továbbiak** lehetőséget. Az alábbi képen az **Adatok beolvasása** ablak látható, amelyen látható, milyen sokféle adatforráshoz lehet csatlakozni a Power BI Desktoppal.

![Adatok lekérése a Power BI Desktopban](media/desktop-what-is-desktop/what-is-desktop_02.png)

Az adattípus kiválasztásánál a rendszer kérni fog néhány információt, például az URL-címet és a hitelesítő adatokat, amelyekre a Power BI Desktopnak szüksége van ahhoz, hogy az Ön nevében csatlakozni tudjon az adatforráshoz.

![Csatlakozás SQL Server-adatbázishoz a Power BI Desktopban](media/desktop-what-is-desktop/what-is-desktop_03.png)

Miután csatlakozott egy vagy több adatforráshoz, az adatokat bizonyára át kell alakítania, hogy használni tudja őket.

## <a name="transform-and-clean-data-create-a-model"></a>Adatok átalakítása és megtisztítása, adatmodell létrehozása

A Power BI Desktopban a beépített **Lekérdezésszerkesztő** használatával alakíthatja át és tisztíthatja meg az adatokat. A Lekérdezésszerkesztővel módosításokat végezhet az adatokon, például megváltoztathatja az adattípust, eltávolíthat oszlopokat, vagy több forrásból származó adatokat kombinálhat. Hasonlít ez kissé a szobrászathoz: egy nagyobb tömb agyaggal kezdi (esetünkben az adatokkal), és szükség szerint elkezd kisebb darabokat levágni, esetleg újabbakat hozzátenni egészen addig, amíg az adatok pontosan úgy nem néznek ki, ahogy azt Ön szeretné. 

![Lekérdezésszerkesztő a Power BI Desktopban](media/desktop-getting-started/designer_gsg_editquery.png)

Az elvégzett adatátalakítási lépéseket (például tábla átnevezése, adattípus átalakítása vagy oszlopok törlése) a **Lekérdezésszerkesztő** rögzíti, és minden alkalommal végrehajtja, amikor a lekérdezés csatlakozik az adatforráshoz, hogy az adatok mindig a meghatározott formázással jelenjenek meg.

Az alábbi képen egy olyan lekérdezéssel látható a **Lekérdezésszerkesztő**, amelyet már formáztak és adatmodellé alakítottak át.

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Ha az adtok formájával meg van elégedve, létrehozhat vizualizációkat. 

## <a name="create-visuals"></a>Vizualizációk létrehozása 

Ha már rendelkezik adatmodellel, a jelentésvászonra húzhat *mezőket*, és így hozhat létre *vizualizációkat*. A *vizualizáció* a modellben lévő adatok grafikus megjelenítése. Az alábbi vizualizáció egy egyszerű oszlopdiagramot mutat. 

![Vizualizáció a Power BI Desktopban](media/desktop-what-is-desktop/what-is-desktop_04.png)

A Power BI Desktopban számos különféle vizualizáció közül választhat. Ha vizualizációt szeretne létrehozni vagy módosítani szeretné valamelyiket, a **Vizualizációk** panelen válassza a vizualizáció ikont. Ha a jelentésvásznon már ki van választva egy vizualizáció, az az Ön által kiválasztott típusúra módosul. Ha nincs kiválasztva vizualizáció, ekkor létrejön egy új vizualizáció a kiválasztás alapján.

![A Vizualizációk panel a Power BI Desktopban](media/desktop-what-is-desktop/what-is-desktop_05.png)

## <a name="create-reports"></a>Jelentések létrehozása

A leggyakrabban több vizualizációból álló csoportot érdemes létrehozni, amelyek a Power BI Desktop adatmodelljének létrehozásához használt adatok különféle aspektusait világítják meg. A vizualizációk csoportját a Power BI Desktop-fájlban *jelentésnek* nevezzük. A jelentés egy vagy több oldalból is állhat, ahogyan egy Excel-fájl is tartalmazhat több munkalapot is. Az alábbi képen egy Power BI Desktop-jelentés első oldala látható Overview (Áttekintés) névvel (a lapfül a kép alján látható). Ez a jelentés tíz oldalt tartalmaz.

![Tízoldalas Power BI Desktop-jelentés](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Jelentések megosztása

Ha a jelentéssel elkészült, és az már megosztható másokkal, a jelentést **közzéteheti** a **Power BI szolgáltatásban**, és így elérhetővé teheti a cégen belül mindenki számára, aki rendelkezik Power BI-licenccel. Ha közzé szeretne tenni egy Power BI Desktop-jelentést, a Power BI Desktop **Kezdőlap** menüszalagján válassza a **Közzététel** elemet.

![Jelentés közzététele a Power BI Desktopból](media/desktop-what-is-desktop/what-is-desktop_06.png)

A **Közzététel** kiválasztásakor a Power BI Desktop az Ön Power BI-fiókjának használatával csatlakozik a **Power BI szolgáltatáshoz**, majd kérni fogja, hogy adja meg, hogy a Power BI szolgáltatásban hol szeretné megosztani a jelentést – ez lehet az Ön saját munkaterülete, egy csapat munkaterülete vagy valamilyen más hely a Power BI szolgáltatásban. Ahhoz, hogy jelentéseket oszthasson meg a Power BI szolgáltatásban, Power BI-licenccel kell rendelkeznie.


## <a name="next-steps"></a>Következő lépések

A **Power BI Desktop** használatának megkezdéséhez először töltse le és telepítse az alkalmazást. A **Power BI Desktopot** kétféle módon szerezheti be:

* [A Power BI Desktopot letöltheti az internetről](desktop-get-the-desktop.md)
* [A Power BI Desktopot beszerezheti a Windows Áruházból](https://aka.ms/pbidesktopstore)
