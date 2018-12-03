---
title: Első lépések a Power BI Desktopban
description: Első lépések a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 5f202597fa641bf68b8e49c461ed5c25ea987c3e
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670927"
---
# <a name="getting-started-with-power-bi-desktop"></a>Első lépések a Power BI Desktopban
Üdvözöljük a **Power BI Desktop Első lépések útmutatójában**. Ebben a rövid bemutatóban megismerkedhet a Power BI Desktop használatával, képességeivel, és megtudhatja, hogyan állíthat össze gyorsan nagy teljesítményű adatmodelleket és lenyűgöző jelentéseket, amelyek megalapozottabb üzleti döntéseket eredményeznek. 

Jobban szeret videókat nézni mint olvasni? [Megtekintheti az első lépéseket bemutató videónkat](desktop-videos.md). Ha pedig szeretné követni a videóban látottakat a megfelelő mintaadatokkal, [letöltheti ezt a minta Excel-munkafüzetet](http://go.microsoft.com/fwlink/?LinkID=521962).

![](media/desktop-getting-started/pbi_gettingstartedsplash_resized.png)

A Power BI Desktop segítségével másokkal könnyen megosztható lekérdezéseket, adatkapcsolatokat és jelentéseket készíthet. A Power BI Desktop integrálja a Microsoft bevált technológiáit (a nagy teljesítményű lekérdezési motort, az adatmodellezést és a vizualizációkat), és zökkenőmentesen működik együtt az online [**Power BI szolgáltatással**](https://app.powerbi.com/).

A **Power BI Desktop** (ahol az elemzők és a többi felhasználó nagy teljesítményű adatkapcsolatokat, modelleket és jelentéseket hozhatnak létre) és a [**Power BI szolgáltatás**](https://preview.powerbi.com/) (ahol a Power BI Desktop-jelentések megoszthatók, így a felhasználók megtekinthetik és használhatják őket) együttes használatával könnyebben modellezhet, hozhat létre, oszthat meg és terjeszthet ki új elemzéseket az adatok világában.

Az adatelemzők megtapasztalhatják, hogy a Power BI Desktop egy hatékony, rugalmas és könnyen elérhető eszköz, amellyel csatlakozhatnak az adatok világához, formázhatják az adatokat, valamint erőteljes modelleket és jól strukturált jelentéseket hozhatnak létre.

## <a name="how-to-use-this-guide"></a>Az útmutató használata
Az útmutató többféleképpen is használható – gyorsan átfuthatja, vagy elolvashat minden fejezetet, hogy alaposan megismerje a Power BI Desktop működését.

Ha kevés ideje van, mindössze néhány perc alatt átlapozhatja az útmutatót, hogy átfogó képet kapjon arról, hogyan működik a Power BI Desktop, és hogyan használható. Az útmutató legnagyobb része a Power BI Desktop működését bemutató képernyőképekből áll.

Ha alaposabban el szeretne mélyedni a témában, elolvashat minden szakaszt, végrehajthatja a lépéseket, és elkészítheti saját Power BI Desktop-fájlját, amelyet közzétehet a **Power BI** szolgáltatásban, és megoszthatja másokkal.

>[!NOTE]
>A [**Power BI jelentéskészítő kiszolgáló**](report-server/get-started.md) a **Power BI** egy speciális, különálló verziója, amely azok számára hasznos, akik a helyszínen szeretnék kezelni adataikat és jelentéseiket. Ezzel a speciális verzióval együtt használható a **Power BI Desktop** egy ugyancsak speciális és különálló verziója, a **Power BI Desktop a Power BI jelentéskészítő kiszolgálóhoz**, amely kizárólag a Power BI jelentéskészítő kiszolgálóval együtt használható. Ebben a cikkben a **Power BI Desktop** standard verzióját ismertetjük.


## <a name="how-power-bi-desktop-works"></a>A Power BI Desktop működése
A Power BI Desktop segítségével *adatokhoz csatlakozhat* (általában több adatforráshoz), *formázhatja az adatokat* (részletes, lenyűgöző adatmodelleket összeállító lekérdezésekkel), és a modellek segítségével *jelentéseket készíthet* (amelyeket mások felhasználhatnak, továbbfejleszthetnek és megoszthatnak).

Ha az igényei szerint elvégezte a lépéseket (a csatlakozást, a formázást és jelentések készítését), a munkáját mentheti Power BI Desktop-fájlformátumban, azaz .pbix fájlkiterjesztéssel. A Power BI Desktop-fájlok más fájlokhoz hasonló módon is megoszthatóak, azonban a leglátványosabban a [**Power BI szolgáltatásba**](https://preview.powerbi.com/) való feltöltéssel oszthatóak meg. 

A Power BI Desktop egyetlen helyre vonja össze, leegyszerűsíti és megkönnyíti az üzletiintelligencia-tárak és -jelentések tervezésének és létrehozásának széttagolt, elkülönülő és fáradságos folyamatát.

Készen áll rá, hogy kipróbálja? Kezdjünk hozzá.



## <a name="install-and-run-power-bi-desktop"></a>A Power BI Desktop telepítése és futtatása
A Power BI Desktop letölthető a **Power BI** szolgáltatásból. Ehhez válassza a **fogaskerék** ikont, majd a **Power BI Desktop** lehetőséget.

![](media/desktop-getting-started/gsg_download.png)

A Power BI Desktop alkalmazásként lesz telepítve, amely a számítógépe asztalán fut.

![](media/desktop-getting-started/designer_gsg_install.png)

A Power BI Desktop futtatásakor megjelenik egy *Üdvözlőképernyő*.

![](media/desktop-getting-started/designer_gsg_startsplashscreen.png)

Az *Üdvözlőképernyőn* lehetősége van **Adatok lekérésére**, megtekintheti a **Legutóbbi forrásokat** vagy **megnyithat más** **jelentéseket** (a bal oldali panelen található hivatkozások segítségével). Ha bezárja ezt a képernyőt (a jobb felső sarokban található **x** gombra kattintva), megjelenik a Power BI Desktop **Jelentés** nézete.

![](media/desktop-getting-started/designer_gsg_blankreport.png)

A Power BI Desktopban három nézet érhető el: **Jelentés** nézet, **Adatok** nézet és **Kapcsolatok** nézet. A Power BI Desktop része a **Lekérdezésszerkesztő** is, amely külön ablakban nyílik meg. A **Lekérdezésszerkesztőben** lekérdezéseket állíthat össze és adatokat alakíthat át, majd betöltheti a finomított adatmodellt a Power BI Desktopba, és jelentéseket hozhat létre.

Az alábbi képernyőn a három nézet ikonja látható a Power BI Desktop bal oldalán: **Jelentés**, **Adatok** és **Kapcsolatok**, felülről lefelé. Az épp megjelenített nézetet sárga sáv jelöli a bal oldalon. Ebben az esetben a **Jelentés** nézet látható. A nézetek között az ikonok kiválasztásával válthat.

![](media/desktop-getting-started/designer_gsg_viewtypes.png)

Ha telepítette a Power BI Desktopot, máris csatlakozhat adatokhoz, formázhatja az adatokat, és jelentéseket készíthet (általában ebben a sorrendben). A következő néhány szakaszban mindhárom lépést bemutatjuk.

## <a name="connect-to-data"></a>Csatlakozás adatokhoz
Ha telepítve van a Power BI Desktop, máris csatlakozhat az adatok egyre bővülő forrásaihoz. A Lekérdezésszerkesztőben *számos különféle* adatforrás elérhető. Az alábbi kép bemutatja, hogyan csatlakozhat adatokhoz a **Kezdőlap** menüszalag **Lekérdezés \> Továbbiak** menüpontjában.

 ![](media/desktop-getting-started/getdatavidsmall.gif)

Ebben a rövid bemutatóban több különböző **webes** adatforráshoz csatlakozunk.

Vegyük például azt az esetet, hogy Ön nyugdíjba megy, és olyan helyen szeretne élni, ahol sokat süt a nap, alacsonyak az adók és jó az egészségügyi ellátás. Vagy adatelemzőként van szüksége ezekre az információkra, hogy segítsen az ügyfeleinek. Például előfordulhat, hogy egy napszemüvegeket forgalmazó kiskereskedőnek segít azokat az értékesítési területeket megcélozni, ahol a legtöbbet süt a nap.

A következő webes forrásanyag mindkét esetben releváns adatokat biztosít:

[*http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx*](http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

Válassza ki a **Lekérdezés \> Web** lehetőséget, és illessze be ezt a címet.

 ![](media/desktop-getting-started/gettingstarted_8.png)

Amikor az **OK** gombra kattint, munkához lát a Power BI Desktop **Lekérdezés** funkciója. A lekérdezés csatlakozik a webes erőforráshoz, és a **Kezelő** ablak visszaadja a webhelyen talált elemeket. Ebben az esetben egy táblázatot (*Table 0*) és a teljes webes dokumentumot. Minket a tábla érdekel, ezért azt választjuk ki a listáról. A **Kezelő** ablak megjelenít egy előnézetet.

 ![](media/desktop-getting-started/datasources_fromnavigatordialog.png)

Ezen a ponton szerkesztheti a lekérdezést, mielőtt betöltené a táblázatot. Ehhez válassza az ablak alján látható **Szerkesztés** gombot. Ha nem szeretné szerkeszteni, csak töltse be a táblázatot.

Miután kiválasztjuk a **Szerkesztés** elemet, elindul a Lekérdezésszerkesztő, és megjelenik a táblázat jellemző nézete. Megjelenik a **Lekérdezés beállításai** panel (ha nem, válassza a **Nézet** lehetőséget a menüszalagról, majd a **Megjelenítés \> Lekérdezés beállításai** lehetőséget a **Lekérdezés beállításai** panel megjelenítéshez). Ez a következőképpen néz ki.

 ![](media/desktop-getting-started/designer_gsg_editquery.png)

További információ az adatokhoz való csatlakozásról: [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md).

A következő szakaszban az igényeink szerint módosítjuk az adatokat. A csatlakoztatott adatok módosításának folyamata az adatok *formázása*.

## <a name="shape-and-combine-data"></a>Adatok formázása és egyesítése
Most, hogy csatlakoztunk egy adatforráshoz, az adatokat módosíthatjuk az igényeinknek megfelelően. A módosítás esetenként az adatok *átalakítását* jelenti, például oszlopok vagy táblázatok átnevezését, szöveg számokká alakítását, sorok eltávolítását, az első sorok fejléccé alakítását stb.

A Power BI Desktop Lekérdezésszerkesztőjében a feladatok nemcsak a menüszalagon érhetők el, hanem a helyi menükben is. Az **Átalakítás** menüszalag elemeinek nagy része egy adott elemre (például oszlopra) a jobb gombbal kattintva megjelenő menüből is elérhető.

## <a name="shape-data"></a>Adatok formázása
Amikor a **Lekérdezésszerkesztőben** formázza az adatokat, részletes utasításokat ad meg a **Lekérdezésszerkesztő** számára, hogy az milyen módosításokat végezzen az adatok betöltésekor és megjelenítésekor. Az eredeti adatforrást nem érintik a változtatások, csak az adatok adott nézete lesz módosítva vagy *formázva*.

A megadott lépéseket (például tábla átnevezése, adattípus átalakítása vagy oszlopok törlése) a **Lekérdezésszerkesztő** rögzíti, és minden alkalommal végrehajtja, amikor a lekérdezés csatlakozik az adatforráshoz, hogy az adatok mindig a meghatározott formázással jelenjenek meg. Ez a folyamat minden alkalommal végbemegy, amikor a Power BI Desktop lekérdezési funkcióját használja, valamint akkor is, ha egy másik felhasználó elindít egy megosztott lekérdezést, például a **Power BI** szolgáltatásban. A lépések a megadott sorrendben rögzítve lesznek a **Lekérdezés beállításai** panel **Alkalmazott lépések** területén.

Az alábbi képen egy formázott lekérdezés **Lekérdezés beállításai** panelje látható – az egyes lépések részletes leírását a következő bekezdésekben találhatja meg.

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Térjünk vissza a nyugdíjazással kapcsolatos adatainkhoz, amelyeket egy webes adatforráshoz kapcsolódva szereztünk, és formázzuk az igényeink szerint ezeket az adatokat.

Először is a legtöbb minősítés egész számként került be a **Lekérdezésszerkesztőbe**, de nem az összes (az egyik oszlop szöveget és számot is tartalmazott, ezért azt nem konvertálta automatikusan a rendszer). Nekünk számformátumban van szükségünk az adatokra. Ez nem jelent problémát. Csak kattintson a jobb gombbal az oszlop fejlécére, és válassza a **Típus módosítása \> Egész szám** lehetőséget az adattípus módosításához. Ha több oszlopot szeretne kijelölni, először jelöljön ki egy oszlopot, majd a **SHIFT** billentyűt lenyomva tartva jelölje ki a szomszédos oszlopokat, és kattintson a jobb gombbal az összes kijelölt oszlop módosításához. Nem szomszédos oszlopokat a **CTRL** billentyűvel jelölhet ki.

 ![](media/desktop-getting-started/designer_gsg_changedatatype.png)

Az oszlopokat módosíthatja is, vagy *átalakíthatja* szövegből fejléccé az **Átalakítás** menüszalagon. A képen az **Átalakítás** menüszalag látható. A nyíl az **Adattípus** gombra mutat, amellyel az adott adattípust egy másikká alakíthatja.

 ![](media/desktop-getting-started/shapecombine_changetype.png)

Vegye figyelembe, hogy a **Lekérdezés beállításai** **Alkalmazott lépések** területén megjelennek a végrehajtott módosítások. Ha el szeretne távolítani egy lépést a formázási folyamatból, egyszerűen válassza ki a lépést, majd kattintson az adott lépés bal oldalán található **X** jelre.

 ![](media/desktop-getting-started/designer_gsg_appliedsteps_changedtype.png)

Végre kell hajtanunk még néhány változtatást, hogy a lekérdezés megfeleljen az igényeinknek:

* *Az első oszlop eltávolítása*: nincs rá szükségünk, mivel csak redundáns sorokból áll, amelyekben a „Check out how your state ranks for retirement” szöveg olvasható. Ennek az az oka, hogy ez egy webes táblázat.

<!-- -->

* *Néhány hiba kijavítása*: a webhelyen az egyik oszlopban vegyesen szöveg és számok is szerepeltek (egyes államok eredményei az adott kategóriában azonosak). Ez egy webhelyen használható, de adatelemzés céljára nem. A kijavítása (ebben az esetben) egyszerű, és ennek során megismerkedhetünk a **Lekérdezésszerkesztő** és az **Alkalmazott lépések** terület hasznos funkcióival és képességeivel.

<!-- -->

* *Táblázatnév megváltoztatása*: a **Table 0** nem túl hasznos leíró név, de könnyű megváltoztatni.

Az összes lépést megtekintheti az **[Adatok formázása és összevonása a Power BI Desktopban](desktop-shape-and-combine-data.md)** című cikkben. Tekintse meg, vagy haladjon tovább ebben a dokumentumban, hogy megtudja, mi a következő lépés. Az alábbi szakasz lépései a fenti módosítások alkalmazása után következnek.

## <a name="combine-data"></a>Adatok összevonása
Érdekes adataink vannak az egyes államokról, amelyeknek még hasznát fogjuk venni újabb elemzések és lekérdezések készítésekor. Ám van egy probléma: a legtöbb helyen az államok a kétbetűs rövidítésükkel szerepelnek, nem a teljes nevükkel. Valahogyan össze kell párosítanunk tehát a neveket a rövidítésekkel.

Szerencsére létezik egy másik nyilvános adatforrás, amely pontosan erre használható. Azonban jelentős formázást kell rajta végrehajtanunk, hogy csatlakoztathassuk a nyugdíjba vonulással kapcsolatos adatokat tartalmazó táblázatunkhoz. Az államok rövidítéseit tartalmazó webes erőforrás a következő címen található:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

A **Lekérdezésszerkesztő** **Kezdőlap** menüszalagján válasszuk a **Lekérdezés \> Web** lehetőséget, írjuk be a webcímet, és kattintsunk az **OK** gombra. A **Kezelő** ablakában ekkor megjelenik a webhelyen talált tartalom.

 ![](media/desktop-getting-started/designer_gsg_usstateabbreviationsnavigator.png)

Válasszuk a **Table[edit]** elemet, mert az tartalmazza a kívánt adatokat. Azonban jelentős formázásra lesz szükség ahhoz, hogy a táblázat tartalma a kívánt adatokra korlátozódjon. Az összes lépést megtekintheti az **[Adatok formázása és összevonása a Power BI Desktopban](desktop-shape-and-combine-data.md)** című cikkben is. A lépések röviden a következőek:

Válasszuk ki a **Szerkesztés** elemet, majd:

* *Távolítsuk el az első két sort.* Ezek a webhelyen létrehozott táblázat maradványai, és nincs szükségünk rájuk.

<!-- -->

* *Távolítsuk el az alsó 26 sort.* Ezek olyan területeket tartalmaznak, amelyekre nincs szükségünk.

<!-- -->
* *Szűrjük ki Washington államot.* A nyugdíjazással kapcsolatos statisztákat tartalmazó táblázatban nem szerepel Washington állam, ezért nem vesszük fel a listánkba.

<!-- -->

* *Távolítsunk el néhány felesleges oszlopot.* Most csak az államneveknek a hivatalos kétbetűs rövidítésükre való leképezésére van szükségünk, így a többi oszlopot törölhetjük.

<!-- -->

* *Alakítsuk az első sort fejléccé.* Mivel eltávolítottuk az első három sort, a jelenlegi legfelső sort szeretnék fejlécként használni.

    >[!NOTE]
    >Itt érdemes megemlíteni, hogy a **Lekérdezésszerkesztőben** az alkalmazott lépések *sorrendje* fontos, mert meghatározhatja, hogyan lesznek formázva az adatok. Érdemes azt is megfontolni, hogy egy adott lépés hogyan befolyásolhatja a soron következő lépéseket. Ha az **Alkalmazott lépések** közül eltávolít egy lépést, lehetséges, hogy a lekérdezés lépéseinek sorrendjéből adódóan a következő lépések nem úgy fognak működni, ahogyan eredetileg tervezte.

* *Nevezzük át az oszlopokat és magát a táblázatot.* Az oszlopok többféleképpen is átnevezhetők, eldöntheti, melyik módszert kívánja használni.

Most, hogy formáztuk *StateCodes* táblázatot, vonjuk össze a két táblázatot vagy lekérdezést. Mivel a táblázataink az adatokon végzett lekérdezéseink eredményei, ezért ezeket gyakran *lekérdezéseknek* nevezzük.

A lekérdezések összevonásának két fő módja van: *egyesítés* és *hozzáfűzés*.

Ha hozzá szeretne adni egy vagy több oszlopot egy másik lekérdezéshez, **egyesítse** a lekérdezéseket. Ha további sorokat szeretne hozzáadni egy meglévő lekérdezéshez, **fűzze őket hozzá** a lekérdezéshez.

Ebben az esetben egyesíteni szeretnénk a lekérdezéseket. Először is válasszuk ki az a lekérdezést, *amellyel* a másik lekérdezést egyesíteni szeretnénk, majd válasszuk a menüszalag **Kezdőlap** fülén a **Lekérdezések egyesítése** lehetőséget.

 ![](media/desktop-getting-started/shapecombine_mergequeries.png)

Megjelenik az **Egyesítés** ablak, ahol kiválaszthatjuk, melyik táblázatot egyesítjük a már kiválasztott táblázattal, majd kijelölhetjük az egyesítéshez használni kívánt oszlopokat. A *RetirementStats* táblázatból (vagy lekérdezésből) válassza ki a *State* oszlopot, majd válassza ki a *StateCodes* lekérdezést. (Ebben az esetben egyszerű a választás, hiszen nincs is másik lekérdezés. Ha több adatforráshoz csatlakozik, több lekérdezés közül választhat.) Miután kiválasztottuk a megfelelő egyező oszlopokat (vagyis a *State* oszlopot a *RetirementStats* táblázatból és a *State Name* oszlopot a *StateCodes* táblázatból), az **Egyesítés** ablak az alábbi képen látható módon néz ki, és az **OK** gomb aktiválódik.

 ![](media/desktop-getting-started/shapecombine_merge.png)

Létrejött egy **NewColumn** nevű oszlop a lekérdezés végén, amely a meglévő lekérdezéssel egyesített táblázat (lekérdezés) adatait tartalmazza. Az egyesített lekérdezés összes oszlopa a **NewColumn** oszlopba lesz sűrítve, de a **Kibontás** lehetőséggel kibonthatja a táblázatot, és tetszőleges oszlopokat adhat hozzá. Az egyesített táblázat kibontásához és a kívánt oszlopok kiválasztásához kattintson a kibontás ikonra (![](media/desktop-getting-started/gettingstarted_29_expandicon.png)). Ekkor megjelenik a **Kibontás** ablak.

 ![](media/desktop-getting-started/shapecombine_mergeexpand.png)

Ebben az esetben kizárólag a *State Code* oszlopra van szükségünk, ezért csak ezt választjuk ki, majd az **OK** gombra kattintunk. Töröljük az **Eredeti oszlopnév használata előtagként** melletti négyzet jelölését, mert nincs szükségünk rá. Ha bejelölve hagyjuk ezt a négyzetet, az egyesített oszlop neve *NewColumn.State Code* lesz (az eredeti oszlopnév, vagyis a *NewColumn*, amelyet egy pont követ, majd a lekérdezéshez adni kívánt oszlop neve).

>[!NOTE]
>Szeretné kipróbálni, milyen további módokon adhatja a *NewColumn* oszlopot a táblázathoz? Nyugodtan kísérletezhet, és ha nem a kívánt eredményt kapja, egyszerűen törölje az adott lépést a **Lekérdezés beállításai** panel **Alkalmazott lépések** listájából. Ekkor a lekérdezés visszatér a **Kibontás** lépés alkalmazása előtti állapotra. Tetszőleges számú alkalommal próbálkozhat, amíg a kibontási folyamattal a kívánt eredményt nem éri el.

Most egyetlen lekérdezésünk (táblázatunk) van, amelyet két, igényeink szerint formázott adatforrás összevonásával hoztunk létre. Ez a lekérdezés alapul szolgálhat számos más érdekes adatkapcsolathoz, például az államokra lebontott lakhatási költségek statisztikái, demográfiai adatok vagy munkalehetőségek megjelenítéséhez.

Az adatok formázási és összevonási lépéseinek részletes leírása: [Adatok formázása és összevonása a Power BI Desktopban](desktop-shape-and-combine-data.md).

Mostanra elegendő adattal rendelkezünk ahhoz, hogy néhány érdekes jelentést készítsünk a Power BI Desktopban. Mivel mérföldkőhöz érkeztünk, mentsük ezt a Power BI Desktop-fájlt. Legyen a neve **Első lépések a Power BI Desktopban**. A **Lekérdezésszerkesztőben** elvégzett módosítások alkalmazásához és Power BI Desktopba való betöltéséhez válassza a **Bezárás és alkalmazás** lehetőséget a **Kezdőlap** menüszalagon.

![](media/desktop-getting-started/shapecombine_closeandapply.png)

## <a name="build-reports"></a>Jelentések összeállítása
A táblázaton a betöltése után további módosításokat is végezhet, és újra betöltheti a modellt az elvégzett módosítások alkalmazásához, de jelenleg ennyi elég is lesz. A Power BI Desktop **Jelentés** nézetében megkezdheti jelentések összeállítását.

A **Jelentés** nézet a következő öt fő területből áll:

1. A menüszalag, amely a jelentésekhez és vizualizációkhoz kapcsolódó általános feladatokat jeleníti meg.
2. A **Jelentés** nézet, vagy más néven vászon. Itt lehet létrehozni és elrendezni a vizualizációkat.
3. Az **Oldalak** lapterület alul, ahol kiválaszthat vagy hozzáadhat jelentésoldalakat.
4. A **Megjelenítések** panel, ahol módosíthatja a vizualizációkat, testreszabhatja a színeket vagy a tengelyeket, szűrőket alkalmazhat, húzással elhelyezheti a mezőket stb.
5. A **Mezők** panel, ahonnan a lekérdezéselemeket és a szűrőket a **Jelentés** nézetbe vagy a **Megjelenítések** panel **Szűrők** területére húzhatja.
   
   ![](media/desktop-getting-started/designer_gsg_reportview.png)

A **Megjelenítések** és a **Mezők** panel összezárható a szélén található kis nyíl kiválasztásával, így több hely marad a **Jelentés** nézetben a vizualizációk összeállítására. A vizualizációk módosításakor ezek a nyilak felfelé vagy lefelé mutatnak, ami azt jelzi, hogy az adott szakasz kibontható vagy összezárható.

 ![](media/desktop-getting-started/designer_gsg_collapsepanes.png)

Vizualizáció létrehozásához egyszerűen húzzon egy mezőt a **Mezők** listából a **Jelentés** nézetbe. Ebben az esetben húzzuk át a *RetirementStats* *State* mezőjét, és lássuk, mi történik.

 ![](media/desktop-getting-started/designer_gsg_reportfirstdrag.png)

Vegyük észre, hogy a Power BI Desktop automatikusan létrehozott egy térképalapú vizualizációt, mert felismerte, hogy a *State* mező földrajzihely-adatokat tartalmaz.

A **Megjelenítések** panelen több különféle típusú vizualizáció közül választhatunk, az ikonok alatti területen pedig a mezőket különböző területekre húzva jelmagyarázatot készíthetünk, vagy másként módosíthatjuk a vizualizációt.

 ![](media/desktop-getting-started/designer_gsg_visualizationtypes.png)

Ugorjunk egy kicsit előre, és nézzük meg, milyen lesz a **Jelentés** nézet, ha hozzáadunk néhány vizualizációt és új jelentésoldalt. További információ a jelentésekről: [Jelentés nézet a Power BI Desktopban](desktop-report-view.md).

Az első jelentésoldal az *Összesített rangsor* alapján mutatja be az adatokat. Amikor kiválasztjuk az egyik vizualizációt, a **Mezők és szűrők** panelen láthatóvá válik, melyik mezők vannak kijelölve, valamint hogy milyen a vizualizáció struktúrája (melyik mezők vannak a **Közös tengelyre**, az **Oszlopértékekre** és a **Sorértékekre** alkalmazva).

 ![](media/desktop-getting-started/designer_gsg_report1.png)

A jelentés hat **oldalt** tartalmaz, mind a hat az adataink bizonyos elemeit jeleníti meg.

1. A fentiekben látható első oldal az *Összesített rangsor* alapján jeleníti meg az összes államot.
2. A második oldal az első tíz államot jeleníti meg az *Összesített rangsor* alapján.
3. A harmadik oldalon a megélhetési költségek szerinti első 10 állam (és a hozzá tartozó adatok) jelenik meg.
4. A negyedik oldal az időjárásra összpontosít a 15 legnaposabb államra szűrve.
5. Az ötödik oldalon a Közösség jólléte szempontjából az első 15 állam látható diagramon.
6. Végül a legalacsonyabb bűnözési statisztikákkal rendelkező első tíz (és egyben utolsó tíz) állam van ábrázolva.

Így néz ki a megélhetési költségre vonatkozó jelentésoldal.

 ![](media/desktop-getting-started/designer_gsg_report2costofliving.png)

Számos érdekes jelentést és vizualizációt hozhat létre.

## <a name="share-your-work"></a>Hogyan oszthatja meg munkáját
Most, hogy van egy nagyjából kész Power BI Desktop-jelentésünk, megoszthatjuk másokkal a **Power BI** szolgáltatásban. A Power BI Desktopban többféleképpen is megoszthatja a munkáját. Közzéteheti a **Power BI** szolgáltatásban, feltöltheti a .pbix fájlt közvetlenül a Power BI szolgáltatásból, vagy mentheti a .pbix fájlt, és elküldheti úgy, mint bármely más fájlt.

Először tekintsük át azt, amikor közvetlenül a Power BI Desktopból teszünk közzé egy fájlt a **Power BI** szolgáltatásba. A **Kezdőlap** menüszalagon válassza a **Közzététel** lehetőséget.

![](media/desktop-getting-started/gsg_syw_1.png)

Lehet, hogy a rendszer arra kéri, hogy jelentkezzen be a Power BI-ba.

![](media/desktop-getting-started/gsg_syw_2.png)

Amikor bejelentkezett, és befejeződött a közzétételi folyamat, az alábbi párbeszédpanel jelenik meg.

![](media/desktop-getting-started/gsg_syw_3.png)

Amikor bejelentkezik a Power BI-ba, a betöltött Power BI Desktop-fájl látható a szolgáltatás **Irányítópultok**, **Jelentések** és **Adatkészletek** szakaszában.

A munkája megosztásának másik módja, ha a **Power BI** szolgáltatásban betölti azt. Az alábbi hivatkozásra kattintva megnyithatja a **Power BI** szolgáltatást a böngészőben:

`https://app.powerbi.com`

A Power BI Desktop-jelentés betöltési folyamatának elindításához válassza az **Adatok lekérése** lehetőséget.

 ![](media/desktop-getting-started/pbi_gsg_getdata1.png)

Megjelenik az **Adatok lekérése** oldal. Itt választhatja ki, honnan kéri le az adatokat. Ebben az esetben a **Beolvasás** elemet választjuk a **Fájlok** mezőben.

![](media/desktop-getting-started/pbi_gsg_getdata2.png)

Megjelenik a **Fájlok** nézet. Ebben az esetben a **Helyi fájl** lehetőséget választjuk.

![](media/desktop-getting-started/pbi_gsg_getdata3.png)

Ha kiválasztja a fájlt, a Power BI feltölti azt.

![](media/desktop-getting-started/pbi_gsg_getdata3a.png)

Amint feltöltődött a fájl, kiválasztható a Power BI szolgáltatás bal oldali paneljének **Jelentések** területén.

![](media/desktop-getting-started/pbi_gsg_getdata4.png)

A **Power BI** szolgáltatás megjeleníti a jelentés első oldalát. Az oldal alján kattintson bármelyik fülre a jelentés adott oldalának megnyitásához.

 ![](media/desktop-getting-started/gsg_share4.png)

Ha módosítani szeretne egy jelentést a **Power BI** szolgáltatásban, válassza a **Jelentés szerkesztése** lehetőséget a jelentés vásznának tetején.

A jelentés mentéséhez válassza a **Fájl \> Mentés másként** lehetőséget a szolgáltatásban. A **Power BI** szolgáltatásban számos különféle érdekes vizualizációt létrehozhat a jelentésből, és ezeket rögzítheti az *irányítópulton*. A **Power BI** szolgáltatás irányítópultjainak megismerése érdekében tekintse meg <strong>[a tökéletes irányítópult megtervezésével kapcsolatos tippeket](service-dashboards-design-tips.md)</strong>.

 ![](media/desktop-getting-started/gsg_share5.png)

A mentés után a fő oldalon válassza a **Megosztás** ikont.

 ![](media/desktop-getting-started/gsg_share6.png)

Innen küldhet e-mailt a munkatársainak, akikkel meg szeretné osztani az irányítópultot.

 ![](media/desktop-getting-started/gsg_share7.png)

További információt az irányítópultok létrehozásáról, megosztásáról és módosításáról az [irányítópultok megosztásával kapcsolatos](service-share-dashboards.md) cikkben találhat.

A Power BI Desktopban és a Power BI szolgáltatásban számos különféle lenyűgöző adategyesítést és vizualizációt hozhat létre. További információért tekintse meg a következő szakaszt.

## <a name="diagnostics"></a>Diagnosztika

A Power BI Desktop támogatja a diagnosztikai portokhoz való csatlakozást. A diagnosztikai port lehetővé teszi, hogy más eszközök csatlakozzanak és diagnosztikai célú nyomkövetést végezzenek. *A modell semmiféle módosítása sem támogatott! A modell megváltoztatása adatsérülést és adatvesztést okozhat.*

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)   