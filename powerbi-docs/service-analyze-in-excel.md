---
title: Elemzés az Excelben a Power BI-hoz
description: Ismerje meg, hogyan elemezhet Power BI-adatkészleteket az Excelben
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/17/2019
ms.author: davidi
LocalizationGroup: Reports
ms.openlocfilehash: f72d29e7f5bc7f93abd43f4c14cf0e53ef18f8d3
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223732"
---
# <a name="analyze-in-excel"></a>Elemzés az Excelben
Előfordulhat, hogy az Excel használatával szeretne megnézni és kezelni egy Power BI-adatkészletet. Az **Elemzés az Excelben** funkció segítségével pontosan ezt teheti meg, valamit elérheti az Excel kimutatás-, diagram- és szeletelő funkcióit a Power BI-ban létező adatkészletre vonatkozóan.

## <a name="requirements"></a>Követelmények
Az **Elemzés az Excelben** funkció használatának van néhány követelménye:

* Az **Elemzés az Excelben** funkciót a Microsoft Excel 2010 SP1 és újabb változatai támogatják.

* Az Excel-kimutatások nem támogatják a numerikus mezők áthúzással való összevonását. A Power BI-adatkészletnek *rendelkeznie kell előre meghatározott mértékekkel*.
* Egyes cégeknél olyan csoportházirendek lehetnek érvényben, amelyek megakadályozzák az **Elemzés az Excelben** funkció használatához szükséges Excel-frissítések telepítését. Ha nem tudja telepíteni ezeket a frissítéseket, forduljon a rendszergazdájához.
* Az **Elemzés az Excelben** funkcióhoz az szükséges, hogy az adatkészlet a Power BI Premiumban legyen, vagy hogy a felhasználó rendelkezzen Power BI Pro-licenccel. A különböző licenctípusok eltérő funkcióiról a [Power BI díjszabásában](https://powerbi.microsoft.com/pricing/), a _Power BI-funkciók összehasonlítása_ részben olvashat bővebben.
* A felhasználók akkor csatlakozhatnak adatkészlethez az Elemzés az Excelben használatával, ha az adott adatkészlethez olvasási jogosultsággal rendelkeznek.  A felhasználó ezzel többféle módon is rendelkezhet: ha tagja egy olyan munkaterületnek, amely az adatkészletet tartalmazza; rendelkezik egy olyan jelentéssel vagy irányítópulttal, amely az adatkészletet használja; vagy hozzáférése van egy olyan alkalmazáshoz, amely az adatkészletet tartalmazza.
* Az **Elemzés az Excelben** a Power BI szolgáltatás egyik funkciója, amely nem érhető el a Power BI jelentéskészítő kiszolgálóban és a Power BI Embeddedben. 
* Az **Elemzés az Excelben** lehetőség csak Microsoft Windows rendszerű számítógépeken támogatott.

## <a name="how-does-it-work"></a>Hogyan működik?
Amikor a **Power BI**-ban egy adatkészlet vagy jelentés három pont (...) menüjéből kiválasztja az **Elemzés az Excelben** lehetőséget, a Power BI létrehoz egy .ODC-fájlt, és letölti azt a böngészőből a számítógépre.

![](media/service-analyze-in-excel/power-bi-analyze-in-excel.png)

Ha a fájlt megnyitja az Excelben, megjelenik egy üres **kimutatás** és egy **mező**lista, benne a Power BI adatkészletből származó táblákkal, mezőkkel és mértékekkel. Ugyanúgy hozhat létre kimutatásokat, diagramokat és elemezheti az adatkészletet, mintha egy helyi adatkészlettel dolgozna az Excelben.

Az .ODC-fájl egy MSOLAP kapcsolati sztringgel kapcsolódik a Power BI-adatkészlethez. Az adatok elemzésekor vagy használatakor az Excel lekérdezi ezt a Power BI-adatkészletet, majd az eredményeket az Excelbe adja vissza. Ha az adatkészlet egy élő adatforráshoz kapcsolódik a DirectQueryvel, akkor a Power BI lekérdezi az adatforrást, és az eredményeket az Excelbe adja vissza.

Az **Elemzés az Excelben** különösen hasznos olyan adatkészletek és jelentések esetében, amelyek *Analysis Services – táblázatos* vagy *többdimenziós* adatbázisokhoz kapcsolódnak, vagy olyan Power BI Desktop-fájlok vagy Excel-munkafüzetek esetében, amelyek adatmodelljeinek mértékeit adatelemzési (DAX) kifejezések használatával hozták létre.

## <a name="get-started-with-analyze-in-excel"></a>Első lépések az Elemzés az Excelben szolgáltatással
A Power BI-ban válassza ki egy jelentés vagy adatkészlet neve melletti három pont (...) menüt, és a menüből válassza az **Elemzés az Excelben** lehetőséget.

![](media/service-analyze-in-excel/power-bi-analyze-menu.png)

### <a name="install-excel-updates"></a>Excel-frissítések telepítése
Az **Elemzés az Excelben** első használatakor telepíteni kell néhány frissítést az Excel kódtárába. A rendszer kéri az Excel-frissítések letöltésére és futtatására (ez elindítja az *SQL_AS_OLEDDB.msi* Windows-telepítőcsomag telepítését). Ez a csomag telepíti a **Microsoft AS OLE DB Provider for SQL Server 2016 RC0 (előzetes verzió)** eszközt.

> [!NOTE]
> Ügyeljen arra, hogy jelölje be a **Ne jelenjen meg többé ez az üzenet** lehetőséget az **Excel-frissítések telepítése** párbeszédablakban. A frissítést csak egyszer kell telepíteni.
> 
> 

![](media/service-analyze-in-excel/pbi_anlz_excel_dontshow.png)

Ha újra le kell tölteni az **Elemzés az Excelben** funkcióhoz szükséges frissítéseket, letöltheti őket a Power BI **Letöltés** ikonjára kattintva, ahogy az a következő képen látható.

![](media/service-analyze-in-excel/pbi_anlz_excel_download_again.png)

### <a name="sign-in-to-power-bi"></a>Bejelentkezés a Power BI-ba
Bár a böngészőjében bejelentkezett a Power BI-ba, azonban amikor először nyit meg az Excelben egy új .ODC-fájlt, akkor a rendszer kérheti, hogy jelentkezzen be a Power BI-ba a Power BI-fiókjával. Ez hitelesíti az Excel kapcsolódását a Power BI-hoz.

### <a name="users-with-multiple-power-bi-accounts"></a>Több Power BI-fiókkal rendelkező felhasználók
Bizonyos felhasználók több Power BI-fiókkal is rendelkeznek, és olyan helyzetbe kerülhetnek, hogy az egyik fiókkal bejelentkeztek a Power BI-ba, de az Elemzés az Excelben szolgáltatásban használt adatkészlethez egy másik fiókjuknak van hozzáférése. Ilyen esetekben egy **Tiltott** hibaüzenet vagy sikertelen bejelentkezési hibaüzenet jelenhet meg, amikor a felhasználó megpróbál hozzáférni egy Elemzés az Excelben-munkafüzetben használt adatkészlethez.

Ekkor lehetősége van újra bejelentkezni azzal a Power BI-fiókkal, amelynek hozzáférése van az Elemzés az Excelben által elért adatkészlethez. Másik lehetőségként kiválaszthatja az Excel **Power BI** menüszalagjának **Profil** elemét, ami azonosítja, hogy jelenleg melyik fiókkal van bejelentkezve, és megad hivatkozást, amelyen keresztül a felhasználó kijelentkezhet (majd újra be, egy másik fiókkal). Ha még nincs telepítve, [letöltheti az Excelhez készült Power BI Publisher](https://www.microsoft.com/download/details.aspx?id=50729) alkalmazást, amellyel telepíthető a Power BI-menüszalag az Excelben.

![](media/service-analyze-in-excel/pbi_anlz_excel_profile.png)

### <a name="enable-data-connections"></a>Adatkapcsolatok engedélyezése
A Power BI-adatok Excelben való elemzéséhez a rendszer kéri, hogy erősítse meg az .odc-fájl nevét és elérési útját, majd kattintson az **Engedélyezés** lehetőségre.

![](media/service-analyze-in-excel/pbi_anlz_excel_enable.png)

> [!NOTE]
> A Power BI-bérlők rendszergazdái a *Power BI felügyeleti portál* használatával letilthatják az **Elemzés az Excelben** funkciót az Analysis Services-adatbázisokban tárolt helyszíni adatbázisok esetében. Ha ez a lehetőség le van tiltva, akkor az **Elemzés az Excelben** nem érhető el az Analysis Services-adatbázisok esetében, de továbbra is elérhető más típusú adatkészletekhez.
> 
> 

## <a name="analyze-away"></a>Elemzés
Most hogy megnyitotta az Excelt és van egy üres kimutatási táblája, készen áll arra, hogy különféle elemzéseket végezzen a Power BI-adatkészleten. Akárcsak a helyi munkafüzetek esetében, az Elemzés az Excelben használatakor is létrehozhat kimutatásokat és diagramokat, adatokat adhat hozzá más forrásokból és így tovább. Emellett természetesen különböző munkalapokat is létrehozhat, amelyek különféle módon nyújtanak betekintést az adatokba.

![](media/service-analyze-in-excel/pbi_anlz_excel_chart.png)

> [!NOTE]
> Fontos tudni, hogy az **Elemzés az Excelben** funkció minden részletszintű adatot elérhetővé tesz minden olyan felhasználó számára, akinek jogosultsága van az adatkészlet hozzáféréséhez.
> 
> 

## <a name="save"></a>Mentés
A Power BI-adatkészlethez kapcsolt munkafüzetet ugyanúgy lehet menteni, mint minden más munkafüzetet. Nem lehet azonban a munkafüzetet a Power BI-ban közzétenni vagy visszaimportálni, mivel a Power BI-ban csak olyan munkafüzetek tehetők közzé vagy importálhatók, amelyek az adatokat táblákban vagy egy adatmodellben tárolják. Mivel az új munkafüzetnek csupán egy kapcsolata van a Power BI-adatkészlethez, ezért a Power BI-ban való közzététel vagy importálás körkörös hivatkozást eredményezne.

## <a name="share"></a>Megosztás
A munkafüzetet a mentés után megoszthatja más Power BI-felhasználókkal a cégen belül.

Ha egy felhasználó megnyitja a munkafüzetet, akivel Ön megosztotta azt, akkor úgy fogja látni a kimutatásokat és az adatokat, ahogyan azok a munkafüzet utolsó mentésekor voltak, ami nem feltétlenül egyezik meg az adatok legfrissebb verziójával. A legújabb adatok lekéréséhez a felhasználóknak a **Frissítés** gombot kell használniuk az **Adatok** menüszalagon. Mivel a munkafüzet egy Power BI-adatkészlethez kapcsolódik, így a munkafüzetet frissíteni szándékozó felhasználónak be kell jelentkeznie a Power BI-ba és telepítenie kell az Excel-frissítéseket, amikor első alkalommal kísérli meg a munkafüzetet ily módon frissíteni.

Mivel a felhasználóknak frissíteniük kell az adatkészletet, és az Excel Online nem támogatja a külső kapcsolatok frissítését, ezért javasoljuk, hogy a felhasználók a számítógépükön az Excel asztali verziójával nyissák meg a munkafüzetet.

## <a name="troubleshooting"></a>Hibaelhárítás
Előfordulhat az Elemzés az Excelben funkció használata során, hogy nem várt eredményt kap, vagy nem a kívánt módon működik. [Ez az oldal az Elemzés az Excelben használata során felmerülő gyakori problémákra nyújt megoldást](desktop-troubleshooting-analyze-in-excel.md)

## <a name="next-steps"></a>Következő lépések

Az alábbi cikkeket is érdekesnek találhatja:

* [Jelentésközi részletezés a Power BI Desktopban](desktop-cross-report-drill-through.md)
* [Szeletelők használata a Power BI Desktopban](visuals/power-bi-visualization-slicers.md)

