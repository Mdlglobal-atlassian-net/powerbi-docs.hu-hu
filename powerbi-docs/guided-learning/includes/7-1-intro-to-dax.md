---
ms.openlocfilehash: 3966521d158c244487638be4117f98ea570e1f28
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799902"
---
Üdvözli a Power BI **DAX** bemutatására készített **oktatócsomagja**.

A **DAX** a **Data Analysis Expressions** rövidítése, és egy, a Power BI-on belül (a háttérben is) használt képletnyelvet takar. A DAX a Microsoft egyéb, például Power Pivot és SSAS táblázatos ajánlataiban is megtalálható, de ezek a témakörök a DAX Power BI-ban való használatára fókuszálnak.

## <a name="dax-and-this-guided-learning-video-series"></a>A DAX és a jelen interaktív tanulási videósorozat
A jelen **interaktív tanulási** szakasz célja az, hogy megtanítsa a DAX alapjait és alapelveit – egy neves DAX-szakértő ([Alberto Ferrari](https://www.sqlbi.com/learning-dax)) tolmácsolásában, aki elmagyarázza, hogyan gondolkodjunk a DAX-ról, hogyan működik, és mik a leghasznosabb funkciói tapasztalatai szerint.

![Alberto Ferrari portréja](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

Az ezen **interaktív tanulási** lap **DAX** szakaszában található videók alapvető útmutatást nyújtanak a DAX képletnyelvének működését illetően. Ez a teljesen új DAX-képletek létrehozásakor is hasznos, de annak a megértéséhez is, hogyan miként hozza létre a Power BI ezeket a DAX-képleteket, amikor lekérdezéseket hoz létre a **Lekérdezésszerkesztőben**.

## <a name="in-this-video---introduction-to-dax"></a>Ebben a videóban – Bevezetés a DAX-ba
A DAX alapfogalmai egyszerűek és magától értetődők, de a DAX hatékony. A DAX egyedi programozási fogalmakat és mintákat használ, ami megnehezítheti a teljes körű kihasználását és megismerését. A nyelvek tanulásának hagyományos módszerei nem feltétlenül a legjobb megközelítések a DAX esetében, ezért a videó célja azon fogalmak és elmélet megtanítása, amelyek később segíthetnek a Power BI-ban való munkában.

A DAX egy *funkcionális nyelv*, ami azt jelenti, hogy a teljes végrehajtott kód egy függvényen belül szerepel.

A DAX-ban a függvények további beágyazott függvényeket, feltételes utasításokat és értékhivatkozásokat tartalmazhatnak. A végrehajtás a DAX-ban a legbelső függvénytől vagy paramétertől indul, és belülről kifelé halad. A Power BI-ban a DAX-képletek egy sorba vannak írva, ezért az olvashatóság érdekében fontos a függvények formázása.

A DAX táblázatokkal való használatra készült, így csak két elsődleges adattípusa van: **Numerikus** és **Egyéb**. A **Numerikus** értékek *egész számokat*, *tizedes tört* és *pénznem* típusú értékeket tartalmazhatnak. Az **Egyéb** típusú értékek *sztringeket* és *bináris objektumokat* tartalmazhatnak. Ez azt jelenti, hogy ha egyfajta számmal való használatra készít DAX-függvényt, biztos lehet benne, hogy minden más számadattal működni fog.

A DAX operátor-túlterhelést használ, ami azt jelenti, hogy a számításokban kombinálhatja az adattípusokat, és az eredmények a bemeneti adatok típusától függően változnak. A konverzió automatikusan végbemegy, ez pedig azt jelenti, hogy nem szükséges ismerni a Power BI-ban használt oszlopok adattípusát, de azt is, hogy időnként nem várt módon átalakításra kerülhet sor. Célszerű megismerni a használt adatokat, hogy az operátorok a várt módon működjenek.

Van egy adattípus, amellyel valószínűleg gyakran fog dolgozni a Power BI-ban: **Dátum/idő**. A **DateTime** típus lebegőpontos értékként tárolódik, amely egész és tizedes tört részt is tartalmaz. A DateTime bármely 1900. március 1. utáni időszak esetében használható pontos számításokhoz.

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](https://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

