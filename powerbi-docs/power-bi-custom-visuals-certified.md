---
title: Minősített egyéni Power BI képi megjelenítések
description: Az egyéni vizualizációk minősítésre való beküldésének követelményei és folyamata. Továbbá a már minősített egyéni vizualizációk listája.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 10/30/2018
ms.author: mihart
ms.openlocfilehash: ba6c59d168deb5fb68f4b339f11fba795bae6452
ms.sourcegitcommit: 862faf948468d7f6d464b83f4e0b040d5213a580
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/30/2018
ms.locfileid: "50252399"
---
# <a name="getting-a-custom-visual-certified"></a>Egyéni vizualizáció *minősítésének* megszerzése
## <a name="what-is-meant-by-certified"></a>Mit értünk az alatt, hogy *minősített*?
A *minősített egyéni vizualizáció* olyan vizualizáció, amely megfelel bizonyos kódelőírásoknak, valamint szigorú biztonsági ellenőrzéseken is átment.  Az egyéni vizualizáció a minősítést követően [exportálható PowerPointba](consumer/end-user-powerpoint.md), és megjeleníthető [az egyes jelentésoldalakra feliratkozott](consumer/end-user-subscribe.md) felhasználók által kapott e-mailekben is. Természetesen [hagyományos egyéni vizualizációként](power-bi-custom-visuals.md) is használható, hozzáadható a Power BI szolgáltatáshoz és a Power BI Desktophoz, és megtekinthető a Power BI-mobilalkalmazásban és az Embeddedben.

Ön olyan webfejlesztő, aki szeretne saját képi megjelenítéseket létrehozni, és hozzáadni azokat a [Microsoft AppSource](https://appsource.microsoft.com) listájához? Ehhez tekintse át az [Ismerkedés a fejlesztői eszközökkel](service-custom-visuals-getting-started-with-developer-tools.md) című részt.


## <a name="certification-requirements"></a>Minősítési követelmények
* Microsoft AppSource-jóváhagyás    
* Az egyéni vizualizációt a verzióval ellátott API-k 1.2-es vagy újabb verzióival kell megírni    
* A kódtárat elérhetővé kell tenni felülvizsgálati célokra (például a vizualizáció kódját meg kell osztani velünk a GitHubon keresztül)    
* Csak nyilvánosan véleményezhető OSS-összetevők használata    
* Nem kapcsolódhat külső szolgáltatásokhoz és erőforrásokhoz    

> **TIPP**: Javasoljuk az EsLint az alapértelmezett biztonsági szabálykészlettel való használatát a kód előzetes ellenőrzésére a beküldés előtt.
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Az egyéni vizualizációk minősítésre való beküldésének folyamata
Egyéni vizualizáció beküldése minősítésre:

1. Küldjön egy e-mailt a Power BI egyéni vizualizációk támogatásáért felelő csapatának (pbicvsupport@microsoft.com). Az e-mailben adja meg az alábbi információkat:    

   * Cím: Vizualizáció minősítésére vonatkozó kérelem    
   * A vizualizáció forráskódját tartalmazó GitHub-adattárra mutató hivatkozás    
   * Feleljen meg a követelményeknek (lásd fent)    
   * Sikeres kód- és biztonsági felülvizsgálat    

2. A Microsoft egyéni vizualizációkért felelős csapata értesíti, amint az egyéni vizualizáció megkapja a minősítést, és elérhetővé válik a Minősített listában (alább), illetve a vizualizáció elutasítása esetén megküldi az orvosolandó problémák listáját. A fejlesztő felelőssége, hogy biztosítsa a megfelelő kommunikációt a Microsoft csapatával, és szükség esetén frissítse Minősített vizualizációit.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Minősített egyéni Power BI vizualizációk eltávolítása
A Microsoft saját belátása szerint eltávolíthatja a vizualizációkat a Minősített listáról.  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>A már minősített egyéni vizualizációk listája

| Az AppSource-ra mutató hivatkozás | A videóra mutató hivatkozás |
| --- | --- |
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

## <a name="next-steps"></a>További lépések
[Bevezetés az egyéni vizualizációk fejlesztői eszközeinek használatába (előzetes verzió)](service-custom-visuals-getting-started-with-developer-tools.md)      
[A Microsoft az egyéni vizualizációkat bemutató lejátszási listája a YouTube-on](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Vizualizációk a Power BI-ban](visuals/power-bi-report-visualizations.md)  
[Egyéni vizualizáció a Power BI-ban](power-bi-custom-visuals.md)  
[Egyéni vizualizációk közzététele a Microsoft AppSource-ban](developer/office-store.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

