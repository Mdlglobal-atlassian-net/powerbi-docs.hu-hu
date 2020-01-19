---
title: A továbbfejlesztett számítási motor használata adatfolyamokkal
description: Megtudhatja, hogyan használhatja a továbbfejlesztett számítási motort adatfolyamokkal a Power BI Premiumban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1d2bd150d33d95f2ec8759f9e876b3920eede3b6
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75840070"
---
# <a name="the-enhanced-compute-engine"></a>A továbbfejlesztett számítási motor

A Power BI továbbfejlesztett számítási motorjával a Power BI Premium-előfizetők a kapacitással optimalizálhatják az adatfolyamok használatát. A továbbfejlesztett számítási motor használata a következő előnyöket nyújtja:

* Drasztikusan csökkenti a kiszámított entitásokon hosszú ideig futó ETL-lépések (*illesztések*, *eltérők*, *szűrők* és *csoportosítások*) frissítési idejét
* DirectQuery-lekérdezések végzése entitásokon (2020. február)

Az alábbi szakaszok a továbbfejlesztett számítási motor engedélyezését ismertetik, valamint gyakori kérdésekre adnak választ.


## <a name="using-the-enhanced-compute-engine"></a>A továbbfejlesztett számítási motor használata

A továbbfejlesztett számítási motor a Power BI szolgáltatás **Kapacitásbeállítások** lapján, az **adatfolyamok** szakaszban engedélyezhető. A továbbfejlesztett számítási motor alapértelmezés szerint **ki van kapcsolva**. A bekapcsoláshoz váltsa a gombot **bekapcsolt** állapotba az alábbi képnek megfelelően, majd mentse a beállításokat. 

![A továbbfejlesztett számítási motor bekapcsolása](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

A továbbfejlesztett számítási motor bekapcsolása után lépjen vissza az adatfolyamokhoz, ahol teljesítménybeli növekedést kell látnia az azonos kapacitáson meglévő kapcsolt entitásokból létrehozott adatfolyamokon összetett műveleteket (például *illesztéseket* vagy *csoportosítást*) végző számított entitásoknál. 

A számítási motor leghatékonyabb kihasználásához ossza az ETL szakaszt két különálló adatfolyamra az alábbi módon:

* **1. adatfolyam** – ez az adatfolyam csak a kötelező elemeket tölti be az adatforrásból, majd a 2. adatfolyamba helyezi őket.
* **2. adatfolyam** – minden ETL-műveletet ebben az adatfolyamban kell végezni, azonban gondoskodnia kell arról, hogy hivatkozzon az 1. adatfolyamra, amelynek ugyanazon kapacitásban kell lennie. A számítási motor kihasználtságának biztosítása érdekében győződjön meg emellett arról, hogy elsőként a fold lépést (szűrés, csoportosítás, eltérés, illesztés) végrehajtó műveleteket végezze el.

## <a name="common-questions-and-answers"></a>Gyakori kérdések és válaszok

**Kérdés:** Bekapcsoltam a továbbfejlesztett számítási motort, a frissítéseim azonban lelassultak. Miért?

**Válasz:** A továbbfejlesztett számítási motor bekapcsolása után tapasztalt lassabb frissítésekre két lehetséges magyarázat létezik:

 - A továbbfejlesztett számítási motor bekapcsolása után annak memóriára van szüksége a működéshez. A frissítéshez szükséges memória így csökken, ami megnöveli a várakozó frissítések valószínűségét, ami pedig az egyidejűleg frissülő adatfolyamok számát csökkenti. A megoldás az lehet, ha a továbbfejlesztett számítás engedélyezésekor megnöveli az adatfolyamokhoz rendelt memória mértékét, így gondoskodva arról, hogy az egyidejű adatfolyam-frissítésekhez használható memória változatlan marad.

 - A lassabb frissítések másik oka az lehet, hogy a számítási motor csak a meglévő entitásokon dolgozik. Ha az adatfolyam olyan adatforrásra hivatkozik, amely nem adatfolyam, nem fog javulást tapasztalni. Nem láthat teljesítménynövekedést, mivel egyes big data-forgatókönyvekben az adatforrásból történő kezdeti beolvasás lelassul, az adatoknak ugyanis el kell jutniuk a továbbfejlesztett számítási motorhoz.  

**Kérdés:** Nem látom továbbfejlesztett számítási motor kapcsológombját. Miért?

**Válasz:** A továbbfejlesztett számítási motort fokozatosan jelentetjük meg a világ különböző régióiban. A motor várhatóan 2020 végére lesz mindenhol támogatva.

**Kérdés:** Milyen adattípusokat támogat a számítási motor?

**Válasz:** A továbbfejlesztett számítási motor és az adatfolyamok jelenleg a következő adattípusokat támogatják. Ha az adatfolyamnem az alábbi adattípusok egyikét használja, hiba történik a frissítéskor:

* Dátum/idő
* Tizedes tört
* Szöveg
* Egész szám
* Dátum/idő/zóna
* Igaz/Hamis
* Dátum
* Idő

## <a name="next-steps"></a>Következő lépések

Ez a cikk a továbbfejlesztett számítási motor adatfolyamokkal történő használatáról nyújtott információt. A következő cikkek szintén hasznosak lehetnek:

* [Önkiszolgáló adatelőkészítés adatfolyamokkal](service-dataflows-overview.md)
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban](service-dataflows-computed-entities-premium.md)
* [Fejlesztői erőforrások Power BI-adatfolyamokhoz](service-dataflows-developer-resources.md)

A Power Queryvel és az ütemezett frissítésekkel kapcsolatos további információt a következő cikkekben talál:
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Ütemezett frissítés beállítása](refresh-scheduled-refresh.md)

A Common Data Modellel kapcsolatos további információt a témát áttekintő cikkben talál:
* [Common Data Model – áttekintés](https://docs.microsoft.com/powerapps/common-data-model/overview)

