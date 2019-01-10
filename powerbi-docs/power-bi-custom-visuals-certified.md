---
title: Minősített egyéni Power BI-vizualizációk
description: Az egyéni vizualizációk minősítésre való beküldésének követelményei és folyamata. Továbbá a már minősített egyéni vizualizációk listája.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 11/21/2018
ms.openlocfilehash: e839fabffc685ac0f97146cb7ee5218039df1c18
ms.sourcegitcommit: 88ae40a25ea54ef7153885dd04ef57d12522d4e1
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54056179"
---
# <a name="certified-custom-visuals"></a>Minősített egyéni vizualizációk

## <a name="what-are-certified-custom-visuals"></a>Mik azok a **_minősített_** egyéni vizualizációk?

A minősített egyéni vizualizációk azok a **piactéren** lévő vizualizációk, amelyek megfelelnek **bizonyos**, a **Microsoft Power BI csapata** által jóváhagyott és tesztelt kódolási előírásoknak. A minősítést szerzett egyéni vizualizációk több funkcióval bírnak. Például [exportálhatók a PowerPointba](consumer/end-user-powerpoint.md), és megjeleníthetők olyan e-mailekben, amelyek akkor érkeznek, amikor egy felhasználó [feliratkozik jelentésoldalakra](consumer/end-user-subscribe.md).

**A minősített egyéni vizualizációk** a [szabványos egyéni vizualizációkhoz](power-bi-custom-visuals.md) hasonlóan működnek. A minősített egyéni vizualizációk hozzáadhatók a **Power BI szolgáltatáshoz** és a **Power BI Desktop jelentéseihez**, valamint megtekinthetők a **Power BI-mobilalkalmazásban** és a **Power BI Embeddedben**.

A végrehajtott tesztek célja, hogy ellenőrizze, hogy a vizualizáció nem kapcsolódik külső szolgáltatásokhoz vagy erőforrásokhoz. *Nem* a **Microsoft** a készítője a külső felek egyéni vizualizációinak, ezért azt javasoljuk az ügyfeleinknek, hogy közvetlenül a készítővel kapcsolatba lépve ellenőrizzék az ilyen vizualizációk működését.

A minősítési folyamat nem kötelező, így a fejlesztők hatásköre eldönteni, hogy szeretnék-e minősíttetni a piactéri vizualizációjukat.  

**A nem minősített egyéni vizualizációk** nem feltétlenül jelentenek nem biztonságos vizualizációkat. Egyes vizualizációk azért nincsenek minősítve, mert nem felelnek meg egy vagy több [minősítésbeli követelménynek](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Például egy külső szolgáltatáshoz (például egy térképvizualizációhoz) vagy egy kereskedelmi könyvtárakat használó vizualizációhoz csatlakozik.

Ön olyan webfejlesztő, aki szeretne saját képi megjelenítéseket létrehozni, és hozzáadni azokat a  **[Microsoft AppSource](https://appsource.microsoft.com)** listájához? Ennek módját az  **[Egyéni Power BI-vizualizáció fejlesztése](developer/custom-visual-develop-tutorial.md)** című cikk ismerteti.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Minősített egyéni Power BI vizualizációk eltávolítása

A Microsoft saját belátása szerint eltávolíthatja a vizualizációkat a [Minősített listáról](#list-of-custom-visuals-that-have-been-certified).

## <a name="getting-a-custom-visualcertified"></a>Egyéni vizualizáció minősítése

### <a name="certification-requirements"></a>Minősítési követelmények

Az egyéni vizualizáció [minősítéséhez](#certified-custom-visuals) győződjön meg róla, hogy az megfelel az alábbi feltételeknek:  

* Microsoft AppSource-jóváhagyás. Az egyéni vizualizáció megtalálható a [piactéren](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* Az egyéni vizualizációt a verzióval ellátott API-k 1.2-es vagy újabb verzióival kell megírni.
* A Power BI csapata által áttekinthető kódtár (például elérhetővé tett forráskód [JavaScript vagy TypeScript] emberileg olvasható formátumban a GitHubon).

    >[!Note]
    > Nem kell nyilvánosan megosztania a kódot a GitHubon.

* Csak nyilvánosan véleményezhető OSS-összetevők használata (nyilvános JS-kódtárak vagy nyilvános TypeScript. A forráskód véleményezhető, és nincsenek ismert biztonsági rései). Kereskedelmi összetevővel rendelkező egyéni vizualizációt nem minősíthetünk.

* Nem fér hozzá külső szolgáltatásokhoz vagy erőforrásokhoz, így többek között HTTP/S- vagy WebSocket-kérelmeket sem küld a Power BI-ból más szolgáltatásokba. 

> [!TIP]
> Javasoljuk az EsLint az alapértelmezett biztonsági szabálykészlettel való használatát a kód előzetes ellenőrzésére a beküldés előtt.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Az egyéni vizualizációk minősítésre való beküldésének folyamata

Egyéni vizualizáció beküldése minősítésre:

1. Küldjön egy e-mailt a Power BI egyéni vizualizációk támogatásáért felelő csapatának (pbicvsupport@microsoft.com). Az e-mailben adja meg az alábbi információkat:
    * Cím: Vizualizáció minősítésére vonatkozó kérelem
    * Az emberileg olvasható forráskódot tartalmazó GitHub-adattárra mutató hivatkozás
    * [Feleljen meg a követelményeknek](#certification-requirements)
    * Sikeres kódfelülvizsgálat

2. A Microsoft egyéni vizualizációkért felelős csapata értesíti, amint az egyéni vizualizáció megkapja a minősítést, és elérhetővé válik a [Minősített listában](#list-of-custom-visuals-that-have-been-certified), illetve a vizualizáció elutasítása esetén megküldi az orvosolandó problémák listáját. A fejlesztő felelőssége, hogy biztosítsa a megfelelő kommunikációt a Microsoft csapatával, és szükség esetén frissítse Minősített vizualizációit.

## <a name="list-of-custom-visuals-that-have-been-certified"></a>A már minősített egyéni vizualizációk listája

| Az AppSource-ra mutató hivatkozás | A videóra mutató hivatkozás |
| --- | --- |
| [3AG Systems – oszlopdiagram relatív eltéréssel](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381803) | |
| [Őszirózsa diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [Csokornyakkendő diagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [Videó](https://youtu.be/So5xKMSpVJI) |
| [Doboz diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [Doboz diagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [Videó](https://youtu.be/JoHaFLfhXdo) |
| [Tégladiagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [Videó](https://youtu.be/hA3DOsvn2xY) |
| [Buborékdiagram az Akvelontól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [Skáladiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [Videó](https://youtu.be/AOlsFYkfkcw) |
| [Skáladiagram az OKViztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [Videó](https://youtu.be/mtvUNl9bMjA) |
| [Naptár a Tallantól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [Gyertya a OKViztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [Videó](https://youtu.be/nT_18gyRxPo) |
| [Államokkal ellátott kártyák az OKviztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Gombsorszeletelő](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [Húr](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [Videó](https://youtu.be/AQvd2FhRyCI) |
| [Kör alakú mérőműszer a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [Videó](https://youtu.be/9NHXALkBXuY) |
| [Fürttérkép](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [Hengeres mérőműszer a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [Videó](https://youtu.be/DgdoWi7Gcxo) |
| [Tárcsa alakú mérőműszer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [Pöttydiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [Pöttydiagram az OKViztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [Videó](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [Lefúrásos oszlopdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [Videó](https://youtu.be/lBy2gQQ5YsQ) |
| [Lefúrásos oszlopdiagram időalapú adatokhoz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [Videó](https://youtu.be/T_mRou18vx0) |
| [Lefúrásos fánkdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [Videó](https://youtu.be/AUVFrSHmPeo) |
| [Kettős KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Dinamikus elemleírás a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380983) | [Videó](https://youtu.be/Z-tl97BpEr0) |
| [Bővített pont](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [Videó](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Gofridiagram az Enlightentől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Lista szerinti szűrés Devscope alapján](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381413) | [Videó](https://youtu.be/RetEWGwBu0I) |
| [Erőgrafikon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [Videó](https://youtu.be/YsTa7uyJ4sg) |
| [Tölcsér forrással a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [Videó](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [Videó](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt-diagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [Videó](https://youtu.be/vJLV9JRCpI8) |
| [Földgömb adatsávok](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [Rács a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380825) | [Videó](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchiadiagram az Akvelontól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [Videó](https://youtu.be/0ZGzJaq_KT4) |
| [Hisztogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [Pontokkal rendelkező hisztogram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [Videó](https://youtu.be/-ILF--wExrw) |
| [Vízszintes tölcsér a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [Videó](https://youtu.be/SudZei68PPo) |
| [Image a CloudScope-tól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [Képrács](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [Infografika-tervező](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [KPI-diagram az Akvelontól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [KPI-oszlop a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380996) | [Videó](https://youtu.be/rU0xoOlIq1U) |
| [KPI-rács a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380947) | [Videó](https://youtu.be/dM4PvZh71V0) |
| [KPI-kijelző](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [KPI-szalagcím a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [Videó](https://youtu.be/cudG4gsZ2V8) |
| [Lineáris mérőműszer a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [Videó](https://youtu.be/7_jFaM30dkc) |
| [Vonalpontos diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [Mekko diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [Videó](https://youtu.be/90FLCKpgicA) |
| [Több KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381763) | |
| [Áttekintés a CloudScope-tól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381477) | |
| [Lejátszási tengely (dinamikus szeletelő)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Nagy teljesítményű KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [Videó](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [Videó](https://youtu.be/1enze8pcGzY) |
| [Pulzusdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | [Videó](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant-diagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [Videó](https://youtu.be/ppBnyhqWNC0) |
| [Sugárdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [Gyűrűdiagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [Videó](https://youtu.be/pDToHDFHnq8) |
| [Forgó diagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [Videó](https://youtu.be/d5xBCMmb3hU) |
| [Sankey diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [Videó](https://youtu.be/WWP9wVUHGaA) |
| [Pontdiagram az Akvelontól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381703) | |
| [Görgető](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Intelligens szűrő az OKViztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [Videó](https://youtu.be/gcJsDDRQq28) |
| [Értékgörbe az OKViztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [Videó](https://youtu.be/0m3Vnvso9tY) |
| [Adatfolyam-grafikon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Többszintű gyűrű](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [Szinoptikus panel az OKViztől](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380873) | |
| [Hőtérképtábla](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [Fordulatszámmérő](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [Videó](https://youtu.be/C3OXdETbS9o) |
| [Szövegszűrő](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [Szövegburkoló a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Hőmérő a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380847) | [Videó](https://youtu.be/SPX9mgrAdBc) |
| [Időecset-szeletelő](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380798) | |
| [Idővonal-szeletelő](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [Videó](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline a CloudScope-tól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381427) | [Videó](https://youtu.be/szNi9YgXFJc) |
| [Tornádó diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [Videó](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Kereskedelmi diagram a MAQ Software-től](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [Videó](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate variancia](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [Videó](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [Videó](https://youtu.be/0BZsVCQdEkc) |
| [Felhasználólista a CloudScope-tól](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [Gofri diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [Videó](https://youtu.be/1vRqYUsm3Vk) |
| [Szófelhő](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [Videó](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>Következő lépések

* [Egyéni Power BI-vizualizáció fejlesztése](developer/custom-visual-develop-tutorial.md)
* [A Microsoft az egyéni vizualizációkat bemutató lejátszási listája a YouTube-on](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Vizualizációk a Power BI-ban](visuals/power-bi-report-visualizations.md)  
* [Egyéni vizualizáció a Power BI-ban](power-bi-custom-visuals.md)  
* [Egyéni vizualizációk közzététele a Microsoft AppSource-ban](developer/office-store.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
