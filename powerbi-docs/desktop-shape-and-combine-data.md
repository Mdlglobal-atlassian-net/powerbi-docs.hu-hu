---
title: Több adatforrásból származó adatok formázása és kombinálása
description: Ebben az oktatóanyagban azt ismertetjük, hogyan lehet adatokat formázni és kombinálni a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 2835dd34ce5ba2d7bc6be8659b87eb1f550fdc28
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514596"
---
# <a name="tutorial-shape-and-combine-data-in-power-bi-desktop"></a>Oktatóanyag: Adatok formázása és összevonása a Power BI Desktopban

A **Power BI Desktoppal** számos különféle típusú adatforráshoz csatlakozhat, és igény szerint formázhatja az adatokat, így létrehozhat olyan jelentéseket, amelyeket másokkal is megoszthat. A *formázás* az adatok átalakítását jelenti, például oszlopok vagy táblázatok átnevezését, szöveg számokká alakítását, sorok eltávolítását, az első sorok fejléccé alakítását stb. Az adatok *összevonásakor* két vagy több adatforráshoz csatlakozik, amelyeket igény szerint formázhat, majd egyetlen, hasznos lekérdezéssé vonhat össze.

Az útmutatóban a következőkről szerezhet ismereteket:

* Adatok formázása a **Lekérdezésszerkesztővel**
* Kapcsolódás adatforráshoz
* Kapcsolódás másik adatforráshoz
* Az adatforrások kombinálása és jelentésekben felhasználható adatmodell létrehozása

Ez az oktatóanyag bemutatja a lekérdezések formázását a Power BI Desktoppal, és kiemel néhány gyakran használt feladatot. Az itt használt lekérdezés részletesebb leírását – például teljesen új lekérdezés létrehozásának lépéseit – az [Első lépések a Power BI Desktopban](desktop-getting-started.md) című témakörben találja.

Érdemes tudni, hogy a Power BI Desktop **Lekérdezésszerkesztőjében** a funkciók a menüszalagon és helyi menükben is elérhetőek. Az **Átalakítás** menüszalag elemeinek nagy része egy adott elemre (például oszlopra) a jobb gombbal kattintva megjelenő menüből is elérhető.

## <a name="shape-data"></a>Adatok formázása
Amikor a Lekérdezésszerkesztőben formázza az adatokat, részletes utasításokat ad meg a Lekérdezésszerkesztő számára, hogy az milyen módosításokat végezzen az adatok betöltésekor és megjelenítésekor. Az eredeti adatforrást nem érintik a változtatások, csak az adatok adott nézete lesz módosítva vagy *formázva*.

A megadott lépéseket (például tábla átnevezése, adattípus átalakítása vagy oszlopok törlése) a Lekérdezésszerkesztő rögzíti, és minden alkalommal végrehajtja, amikor a lekérdezés csatlakozik az adatforráshoz, hogy az adatok mindig a meghatározott formázással jelenjenek meg. Ez a folyamat minden alkalommal végbemegy, amikor a Power BI Desktop Lekérdezésszerkesztő funkcióját használja, valamint akkor is, ha egy másik felhasználó elindít egy megosztott lekérdezést, például a **Power BI** szolgáltatásban. A lépések a megadott sorrendben rögzítve lesznek a **Lekérdezés beállításai** panel **Alkalmazott lépések** területen.

Az alábbi képen egy formázott lekérdezés **Lekérdezés beállításai** panelje látható – az egyes lépések részletes leírását a következő bekezdésekben találhatja meg.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished2.png)

Használjuk az [Első lépések a Power BI Desktopban](desktop-getting-started.md) témakörben található, nyugdíjba vonulással kapcsolatos adatokat, amelyeket egy webes adatforráshoz csatlakozva találtunk meg. Formáljuk ezeket az adatokat az igényeink szerint.

Első lépésként adjunk hozzá egy egyéni oszlopot, amely kiszámítja az összes, egyenlő tényezőként szereplő adat rangsorát, majd hasonlítsuk ezt össze a meglévő _Rangsor_ oszloppal.  Itt látható az **Oszlop hozzáadása** sáv, az egyéni oszlop hozzáadását lehetővé tevő **Egyéni oszlop** gombra mutató nyíllal.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumn.png)

Az **Egyéni oszlop** párbeszédpanelen, az **Új oszlop neve** lehetőségnél adja meg az _Új rangsort_, majd az **Egyéni oszlop képlete** helyre írja be a következőt:

    ([Cost of living] + [Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 8

Ellenőrizze, hogy az állapotüzenet a következő: _'No syntax errors have been detected'_ (Nem találhatók szintaktikai hibák), majd kattintson az **OK** elemre.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumndialog.png)

Ahhoz, hogy az oszlop adatai konzisztensek maradjanak, alakítsuk egész számokká az új oszlop értékeit. Kattintson a jobb gombbal az oszlop fejlécére, és válassza a **Típus módosítása \> Egész szám** lehetőséget a módosításhoz. 

Ha egynél több oszlopot szeretne kiválasztani, először jelöljön ki egy oszlopot, majd a **SHIFT** billentyűt lenyomva tartva jelölje ki a szomszédos oszlopokat, és kattintson a jobb gombbal az összes kijelölt oszlop módosításához. A **CTRL** billentyűvel nem szomszédos oszlopokat is kijelölhet.

![](media/desktop-shape-and-combine-data/shapecombine_changetype2.png)

Az oszlop adattípusait az **Átalakítás** menüszalagról is *átalakíthatja*. A képen az **Átalakítás** menüszalag látható. A nyíl az **Adattípus** gombra mutat, amellyel az adott adattípust egy másikká alakíthatja.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Vegye figyelembe, hogy a **Lekérdezés beállításai** panel **Alkalmazott lépések** területén minden végrehajtott adatformázási lépés megjelenik. Ha el szeretne távolítani egy lépést a formázási folyamatból, egyszerűen csak kattintson az adott lépés bal oldalán található **X** jelre. Az alábbi képen az **Alkalmazott lépések** listában láthatók az eddigi lépések: csatlakozás a webhelyhez (**Forrás**), tábla kiválasztása (**Navigálás**). Emellett a Lekérdezésszerkesztő a táblázat betöltésekor automatikusan megváltoztatta a szövegalapú számoszlopok adattípusát *Szövegről* *Egész számra* (**Típus módosítva**). Az utolsó két lépés a korábban végrehajtott **Egyéni oszlop hozzáadva** és **Típus módosítva1** műveleteket mutatja. 

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly2.png)

Mielőtt használhatnánk a lekérdezést, végre kell hajtanunk néhány változtatást, hogy az adatok az igényeink szerint a helyükre kerülhessenek:

* *Rangsor módosítása egy oszlop eltávolításával* – úgy döntöttünk, hogy az eredményeinkben a **Megélhetési költségek** nem lesz tényező. Az oszlop eltávolítása után azt a problémát tapasztaljuk, hogy az adatok változatlanok maradtak, pedig a Power BI Desktop könnyű megoldást kínál, hiszen ez az **Alkalmazott lépések** egyik nagyszerű funkciója a Lekérdezésen belül.
* *Hibák kijavítása* – Mivel az előbb eltávolítottunk egy oszlopot, most módosítanunk kell a számításainkat az **Új rangsor** oszlopban. Ehhez egy képlet módosítása is hozzátartozik.
* *Adatok rendszerezése* – az **Új rangsor**és a **Rangsor** oszlop alapján. 
* *Adatok lecserélése* – Kiemelt leírást adunk egy adott érték lecseréléséről, és arról hogy szükség van egy **Alkalmazott lépés** beillesztésére is.
* *Táblanév módosítása* – a **Tábla 0** elnevezés nem mond túl sokat, de könnyen módosítható.

A **Megélhetési költségek** oszlop eltávolításához egyszerűen kattintson az oszlopra, majd a menüszalagról a **Kezdőlap** fülre, és végül az **Oszlopok eltávolítása** elemre, az alábbi ábra szerint.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnscostofliving.png)

Figyelje meg, hogy az _Új rangsor_ értékei nem változtak meg; ez a lépések sorrendje miatt van így. Mivel a Lekérdezésszerkesztő sorrendben, de egymástól függetlenül rögzíti a lépéseket, lehetősége van minden **alkalmazott lépést** feljebb vagy lejjebb mozgatni a sorrendben. Kattintson a jobb gombbal bármelyik lépésre. Ekkor a Lekérdezésszerkesztő megjelenít egy menüt, amelyben a következő lehetőségek közül választhat: **Átnevezés**, **Törlés**, **Összes** **további törlése** (az adott lépés és az utána következő összes lépés eltávolítása), **Feljebb** vagy **Lejjebb**. A továbbiakban helyezze az _Oszlopok eltávolítva_ lépést közvetlenül az _Egyéni oszlop hozzáadva_ lépés fölé.

![](media/desktop-shape-and-combine-data/shapecombine_movestep.png)

Ezután kattintson az _Egyéni oszlop hozzáadva_ lépésre. Figyelje meg, hogy az adatokban a _Hiba_ szó látható, amire megoldást kell találni. 

![](media/desktop-shape-and-combine-data/shapecombine_error2.png)

Íme néhány módszer, amellyel további információt tudhatunk meg az egyes hibákról. Kijelölheti az adott cellát (anélkül, hogy a **Hiba** szóra kattintana), vagy közvetlenül a **Hiba** szóra is kattinthat. Ha úgy jelöli ki a cellát, hogy *nem* kattint közvetlenül a **Hiba** szóra, a Lekérdezésszerkesztő az ablak alsó részében megjeleníti a hibával kapcsolatos információkat.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo2.png)

Ha közvetlenül a *Hiba* szóra kattint, a lekérdezés egy **alkalmazott lépést** hoz létre a **Lekérdezés beállításai** panelen, és megjeleníti a hibával kapcsolatos információkat. Erre most nincsen szükségünk, ezért kattintson a **Mégse** elemre.

A hibák kijavításához kattintson az _Új rangsor_ oszlopra, majd a **Megtekintés** szalag megnyitásával és a **Szerkesztőléc** jelölőnégyzet kijelölésével jelenítse meg az oszlop adatait. 

![](media/desktop-shape-and-combine-data/shapecombine_formulabar.png)

Most már eltávolíthatja a _Megélhetési költségek_ paramétert, és a képlet módosításával csökkentheti az osztót az alábbiak szerint: 

    Table.AddColumn(#"Removed Columns", "New Rank", each ([Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 7)

Kattintson a képlet bal oldalán lévő zöld pipa jelre, vagy nyomja le az **Enter** billentyűt. Ekkor az adatokat felváltják a felülvizsgált értékek, és az **Egyéni oszlop hozzáadva** lépés *hiba nélkül* fejeződik be.

> [!NOTE]
> Lehetősége van a **Hibák eltávolítása** művelet elvégzésére is (a menüszalagon vagy a helyi menüben), ami minden hibát tartalmazó sort eltávolít. Ebben az esetben minden sort eltávolítottunk volna az adatok közül, de nem így döntöttünk, hiszen minden adat fontos nekünk, és szeretnénk, ha a táblán maradnának.

Most rendeznünk kell az adatokat az **Új rangsor** oszlop adatai alapján. Először válassza ki a **Típus módosítva1** lépést a lista alján, a legfrissebb adatok megkereséséhez. Ezután válassza ki a **Új rangsor** oszlop fejléce melletti legördülő listát, és ott kattintson az **Növekvő sorrend** lehetőségre.

![](media/desktop-shape-and-combine-data/shapecombine_sort.png)

Figyelje meg, hogy az adatok most már az **Új rangsor** szerint szerepelnek.  Ennek ellenére a **Rangsor** oszlopot megvizsgálva azt fogja látni, hogy ott, ahol az **Új rangsor** is ugyanazt az értéket tartalmazza, nem megfelelő az elrendezés. Ennek kijavításához kattintson az **Új rangsor** elemre, és módosítsa a következőképpen a **szerkesztőlécen** látható függvényt:

    = Table.Sort(#"Changed Type1",{{"New Rank", Order.Ascending},{"Rank", Order.Ascending}})

Kattintson a képlet bal oldalán lévő zöld pipa jelre, vagy nyomja le az **Enter** billentyűt. Ekkor a sorok elrendezése az _Új rangsor_ és a _Rangsor_ oszlopnak egyaránt meg fog felelni.

Továbbá kiválaszthat egy **alkalmazott lépést** bárhol a listában, és onnantól folytathatja az adatok formázását. A Lekérdezésszerkesztő automatikusan beszúr egy új lépést közvetlenül a kiválasztott **alkalmazott lépés** után. Próbáljuk is ki.

Először válassza ki az egyéni oszlop hozzáadása előtti **Alkalmazott lépést**; ez az _Oszlopok eltávolítva_ lépés lesz. Itt az _Időjárás_ arizonai adatának rangsorértékét fogjuk lecserélni. Kattintson a jobb gombbal arra a cellára, amely Arizona _Időjárás_ adatának rangsorértékét tartalmazza, majd válassza ki a megjelenő menüből az *Értékek lecserélése...* lehetőséget. Figyelje meg, hogy melyik **Alkalmazott lépés** van kijelölve (az _Egyéni oszlop hozzáadva_ lépést megelőző lépés).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues2.png)

Mivel be szeretnénk szúrni egy lépést, a Lekérdezésszerkesztő figyelmeztet ennek veszélyeire: az ezt követő lépések a lekérdezés meghibásodását okozhatják. Ezért óvatosan kell eljárnunk. Mivel ez egy útmutató, amelynek célja, hogy bemutassa lépések létrehozását, törlését, beszúrását és étrendezését a Lekérdezésszerkesztőben, folytatjuk tovább, és kiválasztjuk a **Beszúrás** lehetőséget.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Módosítsa az értéket _51_-re, és az Arizonához tartozó adat lecserélődik. Amikor új alkalmazott lépést hoz létre, a Lekérdezésszerkesztő a művelet alapján nevezi el. Ebben az esetben az **Érték felülírva** nevet kapja. Ha több azonos nevű lépés szerepel a lekérdezésben, a Lekérdezésszerkesztő (egymást követő) sorszámozással tesz különbséget az **alkalmazott lépések** között.

Most pedig kattintson az utolsó **Alkalmazott lépésre** (ez a _Sorok rendezve_ lépés), és figyelje meg, hogy az Arizonára vonatkozó adatok megváltoztak.  Ez azért történt, mert jó helyre, vagyis az _Egyéni oszlop hozzáadva_ lépés elé szúrtuk be a _Érték felülírva_ lépést.

Ez talán kicsit összetett, azonban jól mutatja, hogy a Lekérdezésszerkesztő milyen hatékony és sokoldalú eszköz.

Utolsó lépésként módosítsuk a táblázat nevét egy leíró névre. Amikor nekilátunk jelentések készítésének, nagyon hasznos, ha a táblázatok neve jól leírja azok tartalmát. Ez főleg abban az esetben igaz, ha egyszerre több adatforráshoz csatlakozunk, és a táblázatok listája megjelenik a **Jelentés** nézet **Mezők** panelében.

A táblázat neve egyszerűen módosítható: a **Lekérdezés beállításai** panel **Tulajdonságok** területén gépelje be a tábla új nevét, ahogyan az a lenti képen látható, majd nyomja le az **Enter** billentyűt. Adjuk a táblázatnak a *RetirementStats* nevet.

![](media/desktop-shape-and-combine-data/shapecombine_renametable2.png)

Most már az adatok formázása olyan, amilyet szerettünk volna. Csatlakozzunk egy másik adatforráshoz, és vonjuk össze az adatokat.

## <a name="combine-data"></a>Adatok összevonása
Érdekes adataink vannak az egyes államokról, amelyeknek még hasznát fogjuk venni újabb elemzések és lekérdezések készítésekor. Ám van egy probléma: a legtöbb helyen az államok a kétbetűs rövidítésükkel szerepelnek, nem a teljes nevükkel. Valahogyan össze kell párosítanunk tehát a neveket a rövidítésekkel.

Szerencsére létezik egy másik nyilvános adatforrás, amely pontosan erre használható. Azonban jelentős formázást kell rajta végrehajtanunk, hogy csatlakoztathassuk a nyugdíjba vonulással kapcsolatos adatokat tartalmazó táblázatunkhoz. Az államok rövidítéseit tartalmazó webes erőforrás a következő címen található:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

A Lekérdezésszerkesztő **Kezdőlap** menüszalagjáról válasszuk ki az **Új forrás \> Web** lehetőséget, írjuk be a webcímet, majd kattintsunk a **Kapcsolódás** gombra. Ekkor a Kezelőben megjelenik a webhelyen talált tartalom.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator2.png)

Válasszuk ki a **Kódok és rövidítések...** lehetőséget, mert ez tartalmazza a kívánt adatokat. De ahhoz, hogy a táblázat tartalma a számunkra fontos adatokra korlátozódjon, még jelentős formázásra lesz szükség.

> [!TIP]
> Létezik egyszerűbb módja az alábbi lépések végrehajtásának? Igen, létrehozhatunk egy *kapcsolatot* a két táblázat között, és ez alapján is formázhatjuk az adatokat. A következő lépések hasznosak, hiszen a segítségükkel megismerheti a táblázatok kezelését, de érdemes tudni, hogy a kapcsolatok segítségével gyorsan felhasználhat több táblázatból származó adatokat.
> 
> 

Az adatok formázásához hajtsuk végre a következő lépéseket:

* Távolítsa el a felső sort – ez a webhelyen létrehozott táblázat maradványa, és nincs szükség rá. A **Kezdőlap** menüszalagról válassza a **Sorok számának csökkentése \> Sorok eltávolítása \> Legelső sorok eltávolítása** lehetőséget.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

Ekkor megjelenik a **Legelső sorok eltávolítása** ablak, amelyben megadhatja a törölni kívánt sorok számát.

>[!NOTE]
>Ha a Power BI véletlenül sorként importálja a tábla fejléceit az adattáblába, a javításhoz válassza az **Első sor használata fejlécként** lehetőséget a **Kezdőlap** vagy az **Átalakítás** lapról.

* Távolítsa el az alsó 26 sort. Ezek olyan területeket tartalmaznak, amelyekre nincs szükségünk. A **Kezdőlap** menüszalagról válassza a **Sorok számának csökkentése \> Sorok eltávolítása \> Utolsó sorok eltávolítása** lehetőséget.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Mivel a RetirementStats táblázat nem tartalmaz adatokat Washington államról, ezt az államot ki kell szűrnünk a listánkból. A Region Status oszlop melletti legördülő nyílra kattintva törölje a jelölést a **Federal district** melletti jelölőnégyzetből.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Távolítsunk el néhány felesleges oszlopot. Most csak az államneveknek a hivatalos kétbetűs rövidítésükre való leképezésére van szükségünk, így a következő oszlopokat törölhetjük: **1. oszlop**, **3. oszlop**, **4. oszlop**, majd a **6. oszloptól** a **11. oszlopig** mindet. Először jelölje ki a **Column1** oszlopot, majd a **CTRL** billentyű lenyomva tartása mellett jelölje ki a többi eltávolítandó oszlopot (így egyszerre több, nem egymás melletti oszlopot is kiválaszthat). A menüszalag Kezdőlap területéről válassza az **Oszlopok eltávolítása \> Oszlopok eltávolítása** lehetőséget.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

>[!NOTE]
>Itt érdemes megemlíteni, hogy a Lekérdezésszerkesztőben az alkalmazott lépések *sorrendje* fontos, mert meghatározhatja, hogyan lesznek formázva az adatok. Érdemes azt is megfontolni, hogy egy adott lépés hogyan befolyásolhatja a soron következő lépéseket. Ha az Alkalmazott lépések közül eltávolít egy lépést, lehetséges, hogy a lekérdezés lépéseinek sorrendjéből adódóan a következő lépések nem úgy fognak működni, ahogyan eredetileg tervezte.

>[!NOTE]
>Ha átméretezi a Lekérdezésszerkesztő ablakát, például csökkenti a szélességét, a menüszalag egyes elemei összecsukódnak a látható terület legjobb kihasználása érdekében. Ha növeli a Lekérdezésszerkesztő ablakának szélességét, a menüszalag elemei kibomlanak, hogy a lehető legjobban kihasználják a nagyobb menüszalag területét.

* Nevezze át az oszlopokat és magát a táblázatot. Az oszlopok többféleképpen is átnevezhetők. Először is válassza ki az oszlopot, majd válassza az **Átnevezés** lehetőséget a menüszalag **Átalakítás** területén, vagy kattintson a jobb gombbal, és válassza az **Átnevezés…** lehetőséget. a megjelenő helyi menüből. Az alábbi képen mindkét lehetőséget nyíl mutatja. Ezek közül elég az egyiket kiválasztania.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Nevezzük át az oszlopokat a következőképpen: *State Name* és *State Code*. A táblázat átnevezéséhez egyszerűen írja be a nevet a **Lekérdezés beállításai** panel **Név** mezőjébe. Adjuk a táblázatnak a *StateCodes* nevet.

Most, hogy a kívánt módon formáztuk StateCodes táblázatot, vonjuk össze a két táblázatot vagy lekérdezést. Mivel a két táblázatunk az adatokon végzett lekérdezéseink eredményei, ezért ezeket gyakran *lekérdezéseknek* nevezzük.

A lekérdezések összevonásának két fő módja van: *egyesítés* és *hozzáfűzés*.

Ha hozzá szeretne adni egy vagy több oszlopot egy másik lekérdezéshez, **egyesítse** a lekérdezéseket. Ha további sorokat szeretne hozzáadni egy meglévő lekérdezéshez, **fűzze őket hozzá** a lekérdezéshez.

Ebben az esetben érdemes egyesíteni a lekérdezéseket. Első lépésként a Lekérdezésszerkesztő bal oldali paneljén válassza ki azt a lekérdezést, *amellyel* a másik lekérdezést egyesíteni szeretnénk. Ebben az esetben ez a *RetirementStats*. Ezután válassza az **Összevonás \> Lekérdezések egyesítése** lehetőséget a menüszalag **Kezdőlap** fülén.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

A rendszer felkérheti az adatvédelmi szintek beállítására. Ezzel elkerülheti, hogy nem kívánt adatokat jelöljön ki vagy helyezzen át az adatok összevonásakor.

Ezután megjelenik az **Egyesítés** ablak, ahol kiválaszthatjuk, melyik táblázatot egyesítjük a már kiválasztott táblázattal, majd kijelölhetjük az egyesítéshez használni kívánt oszlopokat. A *RetirementStats* táblázatból (vagy lekérdezésből) válassza ki a State oszlopot, majd válassza ki a *StateCodes* lekérdezést. (Ebben az esetben egyszerű a választás, hiszen nincs is másik lekérdezés. Ha több adatforráshoz csatlakozik, több lekérdezés közül választhat.) Miután kiválasztottuk a megfelelő egyező oszlopokat (vagyis a **State** oszlopot a *RetirementStats* táblázatból és a **State Name** oszlopot a *StateCodes* táblázatból), az **Egyesítés** ablak az alábbi képen látható módon néz ki, és az **OK** gomb aktiválódik.

![](media/desktop-shape-and-combine-data/shapecombine_merge2.png)

Létrejött egy **NewColumn** nevű oszlop a lekérdezés végén, amely a meglévő lekérdezéssel egyesített táblázat (lekérdezés) adatait tartalmazza. Az egyesített lekérdezés összes oszlopa a **NewColumn** oszlopba lesz sűrítve, de a **Kibontás** lehetőséggel kibonthatja a táblázatot, és tetszőleges oszlopokat adhat hozzá.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Az egyesített táblázat kibontásához és a kívánt oszlopok kiválasztásához kattintson a kibontás ikonra (![Kibontás](media/desktop-shape-and-combine-data/icon.png)). Ekkor megjelenik a **Kibontás** ablak.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

Ebben az esetben kizárólag a **State Code** oszlopra van szükségünk, ezért csak ezt választjuk ki, majd az **OK** gombra kattintunk. Töröljük az Eredeti oszlopnév használata előtagként melletti négyzet jelölését, mert nincs szükségünk rá. Ha bejelölve hagyjuk ezt a négyzetet, az egyesített oszlop neve **NewColumn.State Code** lesz (az eredeti oszlopnév, vagyis a **NewColumn**, amelyet egy pont követ, majd a lekérdezéshez adni kívánt oszlop neve).

>[!NOTE]
>Szeretné kipróbálni, milyen további módokon adhatja a **NewColumn** oszlopot a táblázathoz? Nyugodtan kísérletezhet, és ha nem a kívánt eredményt kapja, egyszerűen törölje az adott lépést a **Lekérdezés beállításai** panel **Alkalmazott lépések** listájából. Ekkor a lekérdezés visszatér a **Kibontás** lépés alkalmazása előtti állapotra. Tetszőleges számú alkalommal próbálkozhat, amíg a kibontási folyamattal a kívánt eredményt nem éri el.

Most egyetlen lekérdezésünk (táblázatunk) van, amelyet két, igényeink szerint formázott adatforrás összevonásával hoztunk létre. Ez a lekérdezés alapul szolgálhat számos más érdekes adatkapcsolathoz, például az államokra lebontott lakhatási költségek statisztikái, demográfiai adatok vagy munkalehetőségek megjelenítéséhez.

A módosítások mentéséhez és a Lekérdezésszerkesztő bezárásához kattintson a **Bezárás és alkalmazás** elemre a menüszalag **Kezdőlap** fülén. Az átalakított adatkészlet ezután megjelenik a Power BI Desktopban, és elérhető jelentések készítéséhez.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)   

