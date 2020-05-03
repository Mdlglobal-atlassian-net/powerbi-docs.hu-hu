---
title: Kibővített metaadatok használata adatkészletekhez a Power BI Desktopban (előzetes verzió)
description: Ez a cikk az adathalmazok kibővített metaadatainak Power BI-beli használatát ismerteti.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 301d6397e4a3ae4498234bae3ad8a49aa7552722
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584665"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Adathalmazok kibővített metaadatainak használata (előzetes verzió)

Amikor a Power BI Desktop jelentést hoz létre, adathalmaz-metaadatokat is létrehoz a megfelelő PBIX- és PBIT-fájlokban. A metaadatok korábban a Power BI Desktop saját formátumában voltak tárolva. Base64 kódolású M-kifejezéseket és adatforrásokat használt, és feltételezésekkel élt a metaadatok tárolásával kapcsolatban.

A **bővített adathalmaz-metaadatok** funkció kibocsátásával sok ilyen korlátozás megszűnik. A **bővített adathalmaz-metaadatok** funkció engedélyezése esetén a Power BI Desktoppal létrehozott metaadatok formátuma az Analysis Services táblázatos modelljeiben használthoz hasonló, és a [Táblázatos objektummodellre](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) épül.


A **bővített adathalmaz-metaadatok** stratégiai és alapvető funkció, mert a jövőben a Power BI működése is ezekre a metaadatokra fog épülni. A bővített adathalmaz-metaadatok előnyeit kihasználó további képesség például a Power BI-adathalmazok kezelésére szolgáló [XMLA olvasás/írás](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite), valamint az Analysis Services számítási feladatok Power BI-ba migrálása a funkciók új generációjának kihasználása érdekében.



## <a name="enable-enhanced-dataset-metadata"></a>A bővített adathalmaz-metaadatok engedélyezése

A **bővített adathalmaz-metaadatok** funkció jelenleg előzetes verzióban érhető el. A bővített adathalmaz-metaadatok engedélyezéséhez a Power BI Desktopban válassza a **Fájl > Lehetőségek és beállítások > Beállítások > Előzetes funkciók** menüpontot, majd jelölje be az **Adathalmazok tárolása a bővített metaadat-formátum használatával** jelölőnégyzetet az alábbi ábrán látható módon. 

![Az előzetes verziójú funkció engedélyezése](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

A rendszer a Power BI Desktop újraindítását kéri.

![Újraindítási kérés](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Az előzetes funkció engedélyezése után a Power BI kísérletet tesz a korábbi metaadat-formátumot használó PBIX- és PBIT-fájlok frissítésére. 

> [!IMPORTANT]
> A **bővített adathalmaz-metaadatok** funkció engedélyezése a jelentések nem visszavonható frissítését eredményezi. A **bővített adathalmaz-metaadatok** engedélyezésekor a Power BI Desktoppal betöltött vagy létrehozott Power BI-jelentések mindegyike visszavonhatatlanul a bővített adathalmaz-metaadatok formátumára lesz konvertálva.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Az előzetes verzióban az alábbi korlátozások érvényesek az előzetes funkció engedélyezése esetén.

### <a name="unsupported-features-and-connectors"></a>Nem támogatott funkciók és összekötők
Nem frissített meglévő PBIX- vagy PBIT-fájl megnyitásakor a frissítés sikertelen lesz, ha az adathalmaz az alábbi funkciók vagy összekötők bármelyikét tartalmazza. A sikertelenség nem jár a felhasználó által tapasztalható közvetlen következménnyel, és a Power BI Desktop továbbra is a korábbi metaadat-formátumot fogja használni.

* Python-szkriptek
* Egyéni összekötők
* Azure DevOps Server
* BI-összekötő
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* Az oszlopnevekben bizonyos karakterkombinációkat (például „\\n”) tartalmazó M-kifejezések
* Ha a **bővített adathalmaz-metaadatok** funkció engedélyezése mellett használ adathalmazokat, az egyszeri bejelentkezést (SSO) használó adathalmazok nem állíthatók be a Power BI szolgáltatásban

Ezeken kívül a **bővített adathalmaz-metaadatok** használatára frissített PBIX- és PBIT-fájlok *nem* használhatják a fenti funkciókat és összekötőket az aktuális verzióban.

### <a name="lineage-view"></a>Adatéletút nézet
Az új metaadat-formátumot használó adathalmazok jelenleg nem jelenítik meg az adatfolyamokra mutató hivatkozásokat a Power BI szolgáltatás Adatéletút nézetében.

## <a name="next-steps"></a>Következő lépések

A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [A Power BI Desktop újdonságai](desktop-latest-update.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adattípusok a Power BI Desktopban](desktop-data-types.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)

