---
title: Gyakori lekérdezési feladatok a Power BI Desktopban
description: Gyakori lekérdezési feladatok a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: dc6aa42691c7caa2593b28e441f96985b1e3bcda
ms.sourcegitcommit: b11e908650379913d00673215e3eaf25d712b122
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65239427"
---
# <a name="common-query-tasks-in-power-bi-desktop"></a>Gyakori lekérdezési feladatok a Power BI Desktopban
A Power BI Desktop **Lekérdezésszerkesztő** ablakában elérhető néhány gyakran használt feladat. Ez a dokumentum ezeket a gyakori feladatokat mutatja be, és további információkra mutató hivatkozásokat is tartalmaz. 

A bemutatott gyakori lekérdezési feladatok a következők:

* Csatlakozás adatokhoz
* Adatok formázása és egyesítése
* Sorok csoportosítása
* Oszlopok forgatása
* Egyéni oszlopok létrehozása
* Lekérdezési képletek

A feladatok végrehajtásához néhány adatkapcsolatot fogunk használni. Az adatokat Ön is szabadon letöltheti vagy csatlakozhat hozzájuk, amennyiben szeretné maga is végrehajtani a feladatokat.

Az első adatkapcsolat egy Excel-munkafüzet, amelyet [innen](http://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx) tölthet le. A másik egy webes forrásanyag (ezt a Power BI Desktop egyéb súgói is alkalmazzák), amely a következő helyen érhető el:

[*http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx*](http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

A két adatforráshoz való kapcsolódáshoz szükséges lépésekkel kezdődnek a gyakori lekérdezési feladatok.

## <a name="connect-to-data"></a>Csatlakozás adatokhoz
A Power BI Desktopban az adatokhoz való kapcsolódáshoz kattintson a **Lekérdezés** gombra a **Kezdőlap** szalagon. Ekkor megjelenik a Power BI Desktop leggyakoribb adatforrásokat tartalmazó menüje. Az adatforrások teljes listájához, amelyekhez a Power BI Desktop csatlakoztatható, kattintson a menü alján a **Továbbiak...** gombra. További információért lásd [a Power BI Desktop adatforrásait](https://docs.microsoft.com/power-bi/desktop-data-sources).

![](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

Első lépésként válassza az **Excel** lehetőséget, és keresse meg, majd jelölje ki a munkafüzetet. A lekérdezés átvizsgálja a munkafüzetet, majd a talált adatokat a **Kezelő** ablakban jeleníti meg.

![](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

A **Szerkesztés** gombbal módosíthatja, más néven *formázhatja* az adatokat, mielőtt betöltené azokat a Power BI Desktopba. A lekérdezések betöltés előtti szerkesztése akkor igazán hasznos, ha nagyobb adatkészletekkel dolgozik, amelyeket le szeretne szűkíteni a betöltés előtt. Pontosan ezt szeretnénk tenni, ezért kiválasztjuk a **Szerkesztés** gombot.

Más típusú adatokhoz is ugyanilyen egyszerűen kapcsolódhat. Egy webes erőforráshoz is szeretnénk kapcsolódni. Válassza a **Lekérdezés \> Továbbiak...**, majd az **Egyéb \> Web** lehetőséget.

![](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

Megnyílik a **Webes tartalomból** ablak, amelyben megadhatja a weboldal URL-címét.

![](media/desktop-common-query-tasks/datasources_fromwebbox.png)

Kattintson az **OK** gombra, és a Power BI Desktop az előző lépéshez hasonlóan átvizsgálja a munkafüzetet, és a talált adatokat megjeleníti a **Kezelő** ablakban.

A többi adatkapcsolat is hasonlóan működik. Ha valamely adatkapcsolat létrehozásához hitelesítés szükséges, a Power BI Desktop megkéri, hogy adja meg a megfelelő hitelesítő adatokat.

A Power BI Desktop-adatkapcsolatok létrehozásával kapcsolatos lépésenkénti útmutatóért lásd a témakört, amely azzal foglalkozik, [hogyan kapcsolódhat adatokhoz a Power BI Desktopban](https://docs.microsoft.com/power-bi/desktop-connect-to-data).

## <a name="shape-and-combine-data"></a>Adatok formázása és egyesítése
A Lekérdezésszerkesztővel egyszerűen formázhatja és egyesítheti az adatokat. Ebben a szakaszban bemutatunk néhány példát az adatok formázására. Az adatok formázásának és egyesítésének részletesebb bemutatójáért lásd: **[Adatok formázása és egyesítése a Power BI Desktoppal](https://docs.microsoft.com/power-bi/desktop-shape-and-combine-data)**.

Az előző szakaszban két adatkészletet csatlakoztattunk, egy Excel-munkafüzetet és egy webes erőforrást. Miután betöltöttük az adatokat a Lekérdezésszerkesztőbe, a következőt látjuk, ha a webes erőforrás lekérdezése van kiválasztva (a Lekérdezésszerkesztő ablak bal oldalán, a **Lekérdezések** panelen felsorolt elérhető lekérdezések között).

![](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

Az adatok formázása során az adatokat olyan formába és formátumba alakítjuk, amely megfelel az igényeinknek. Ebben az esetben az első, *Header* (Fejléc) című oszlopra nincs szükségünk, ezért eltávolítjuk.

A **Lekérdezésszerkesztőben** számos parancs található a menüszalagon és a környezetfüggő helyi menüben is. Például a jobb gombbal a *Header* oszlopra kattintva a megjelenő menü megfelelő elemével törölheti az oszlopot. Azt is megteheti, hogy kijelöli az oszlopot, majd a menüszalag **Oszlopok eltávolítása** gombjával töröli.

![](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

A lekérdezés adatait rengeteg egyéb módon is átalakíthatja: bármennyi sort törölhet felülről vagy alulról; hozzáadhat oszlopokat vagy feloszthatja a meglévőket; cserélheti az értékeket, továbbá egyéb alakítási műveletekkel is utasíthatja a Lekérdezésszerkesztőt, hogy a kívánt formába öntse az adatokat.

## <a name="group-rows"></a>Sorok csoportosítása
A Lekérdezésszerkesztőben több sor értékét csoportosítással egyetlen értékké vonhatjuk össze. Ez hasznos lehet például akkor, ha összesíteni szeretné az árajánlatokban szereplő termékek darabszámát, az összes értékesítést vagy a diákok számát.

Ebben a példában egy oktatási regisztrációs adatkészlet sorait csoportosítjuk. Az adatok egy Excel-munkafüzetből származnak, és a Lekérdezésszerkesztőben már megformáztuk őket, így csak a szükséges oszlopok maradtak, nevezze át a táblát, és hajtson végre néhány más átalakítást is.

Lássuk, hány Ügynökség (ez jelenthet iskolakörzetet vagy egyéb oktatási ügynökségeket, például regionális szolgáltatási körzeteket) van az egyes államokban. Jelölje ki a *State Abbr* oszlopot, majd kattintson a menüszalagon az **Átalakítás** vagy a **Kezdőlap** **Csoportosítási szempont** gombjára (a **Csoportosítási szempont** gomb mindkét lapon elérhető).

![](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

Megnyílik a **Csoportosítási szempont...** ablak. A sorok csoportosításakor a Lekérdezésszerkesztő egy új oszlopot hoz létre, amelyben a **Csoportosítási szempont** eredményeit helyezi el. A **Csoportosítási szempont** művelet a következők szerint állítható be:

1. *Csoportosítási szempont* – Ez a csoportosítandó oszlop. A Lekérdezésszerkesztő a kijelölt oszlopot választja ki, de ebben az ablakban bármely másik oszlopot is kiválaszthatja.
2. *Új oszlop neve* – A Lekérdezésszerkesztő javaslatot tesz az új oszlop nevére a csoportosított oszlopon végrehajtott művelet alapján, de az új oszlopot ettől függetlenül bármilyen névre átnevezheti.
3. *Művelet* – Itt adhatja meg a Lekérdezésszerkesztő által alkalmazott műveletet.
4. *Csoportosítás hozzáadása* és *Összesítés hozzáadása* – ezek a lehetőségek a **Speciális** beállítás kiválasztása után jelennek meg. Egyszerre több oszlopra kiterjedő összesítési műveleteket (**Csoportosítási szempont** műveleteket) is végrehajthat, és egyszerre több összesítést is elvégezhet a **Csoportosítási szempont** ablakban, egyetlen művelet részeként. A Lekérdezésszerkesztő létrehoz egy új oszlopot (az ebben az ablakbon kiválasztott beállítások szerint), amely több oszlopot kezel majd. 

Válassza a **Csoportosítás hozzáadása** vagy az **Összesítés hozzáadása** gombot, ha további csoportosításokat vagy összesítéseket szeretne hozzáadni a **Csoportosítási szempont** művelethez. Az oszlopokat vagy összesítéseket törölheti, ha rákattint a **...** ikonra, majd a **Törlés** lehetőséget választja, így nyugodtan kísérletezhet a funkció használatával.
   
   ![](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

Az **OK** gombra kattintva a lekérdezés végrehajtja a **Csoportosítási szempont** műveletet, és visszaadja az eredményeket. Az a helyzet, hogy Ohióban, Texasban, Illinoisban és Kaliforniában is most már több mint ezer ügynökség található!

![](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

A Lekérdezésszerkesztőben az utolsó alakítási művelet mindig visszavonható az épp végrehajtott lépés melletti **X** gombbal. Nyugodtan kísérletezhet, újra és újra megismételhet egy lépést a Lekérdezésszerkesztővel, amíg az adatok el nem érik a kívánt formát.

## <a name="pivot-columns"></a>Oszlopok forgatása
A Power BI Desktopban az oszlopok forgatásával olyan táblákat hozhat létre, amelyek összesített értékeket tartalmaznak egy adott oszlop minden egyedi értékére vonatkozóan. Például ha tudni szeretné, hogy hány különböző termék van az egyes termékkategóriákban, gyorsan létrehozhat egy táblát, amely pontosan ezt mutatja ki.

Lássunk erre egy példát. Az alábbi **Termékek** tábla úgy lett kialakítva, hogy csak az egyes egyedi termékeket jelenítse meg (név alapján), illetve azt, hogy melyik termék melyik kategóriába tartozik. Egy olyan új tábla létrehozásához, amely az egyes kategóriákban lévő termékek számát mutatja (a *CategoryName*, Kategória neve oszlop alapján), jelölje ki az oszlopot, majd kattintson a **Forgatott oszlop** gombra a menüszalag **Átalakítás** lapján.

![](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

Megnyílik a **Forgatott oszlop** ablak, amely tájékoztatja, hogy mely oszlop értékei alapján jönnek létre az új oszlopok (1), és ha kibontja a **Speciális beállítás** területet (2), kiválaszthatja az összesített értékekre alkalmazandó függvényt (3).

![](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

Az **OK** gombra kattintva a Lekérdezésszerkesztő megjeleníti a táblát a **Forgatott oszlop** ablakban megadott átalakítási utasítások alapján.

![](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>Egyéni oszlopok létrehozása
A Lekérdezésszerkesztőben létrehozhat olyan egyéni képleteket, amelyek a tábla több oszlopán futnak, majd az ilyen képletek eredményét tárolhatja egy új (egyéni) oszlopban. A Lekérdezésszerkesztő segítségével egyszerűen hozhat létre egyéni oszlopokat.

A Lekérdezésszerkesztőben kattintson az **Egyéni oszlop** gombra a menüszalag **Oszlop hozzáadása** lapján.

![](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

Az alábbi ablak jelenik meg. A következő példában egy *Percent ELL* nevű egyéni oszlopot hozunk létre, amely az angol nyelvet tanuló (English Language Learners, ELL) diákok százalékos arányát számítja ki.

![](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Ahogy a Lekérdezésszerkesztőben végrehajtott összes többi lépés esetében, ha az új egyéni oszlop nem azokat az eredményeket adja, amelyekre számított, egyszerűen törölheti a lépést a **Lekérdezés beállításai** panel **Alkalmazott lépések** szakaszában. Ehhez válassza ki az **Egyéni oszlop hozzáadva** lépés melletti **X** gombot.

![](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>Lekérdezési képletek
A Lekérdezésszerkesztő által létrehozott lépések szerkeszthetők, és egyéni képleteket is létrehozhat, amelyekkel pontosabban szabályozhatja az adatok csatlakoztatását és alakítását. Amikor a Lekérdezésszerkesztő valamilyen műveletet hajt végre az adatokon, az alkalmazott képlet megjelenik a **képletsávban**. A **képletsáv** megjelenítéséhez jelölje be a **Képletsáv** jelölőnégyzetét a menüszalag **Nézet** lapján.

![](media/desktop-common-query-tasks/queryformulas_formulabar.png)

A Lekérdezésszerkesztő az egyes lekérdezések alkalmazott lépéseit szövegként megőrzi, amely megtekinthető és módosítható. Az egyes lekérdezések szövegét a **Speciális szerkesztő** használatával tekintheti meg és módosíthatja, amely a szalag **Nézet** lapján, a **Speciális szerkesztő** gombra kattintva jeleníthető meg.

![](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

A **Speciális szerkesztő** a következőképpen néz ki, amikor éppen az **USA\_StudentEnrollment** lekérdezés lépéseit jeleníti meg. Ezek a lépések a Power Query képletnyelv – gyakori nevén az **M** – használatával íródtak. További információkért lásd: [További tudnivalók a Power Query-képletekről](https://support.office.com/article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f). A nyelvi specifikáció megtekintéséhez lásd [az Excelhez készült Microsoft Power Query képletnyelv specifikációját](http://go.microsoft.com/fwlink/?linkid=320633).

![](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

A Power BI Desktop számos képletkategória használatát teszi lehetővé. További információkért és a Lekérdezésszerkesztő képleteinek teljes referenciájáért lásd a [Power Query képletkategóriáit](https://support.office.com/article/Power-Query-formula-categories-125024ec-873c-47b9-bdfd-b437f8716819) ismertető témakört.

A Lekérdezésszerkesztő az alábbi képletkategóriákat kínálja:

* Szám
  * Állandók
  * Információ
  * Átalakítás és formázás
  * Formátum
  * Kerekítés
  * Műveletek
  * Véletlenszerű
  * Trigonometria
  * Bájt
* Szöveg
  * Információ
  * Szöveg-összehasonlítások
  * Kigyűjtés
  * Módosítás
  * Tagság
  * Átalakítások
* Logikai
* Dátum
* Idő
* Dátum/idő
* Dátum/időzóna
* Időtartam
* Rekord
  * Információ
  * Átalakítások
  * Kiválasztás
  * Szerializálás
* Lista
  * Információ
  * Kiválasztás
  * Átalakítás
  * Tagság
  * Halmazműveletek
  * Rendezés
  * Átlagolás
  * Összeadás
  * Numerikus
  * Generátorok
* Tábla
  * Táblakészítés
  * Átalakítások
  * Információ
  * Sorműveletek
  * Oszlopműveletek
  * Tagság
* Értékek
* Aritmetikai műveletek
* Paramétertípusok
* Metaadatok
* Adatok elérése
* URI
* Bináris formátumok
  * Számok olvasása
* Bináris
* Vonalak
* Kifejezés
* Függvény
* Hiba
* Összehasonlító
* Felosztó
* Egyesítő
* Lecserélő
* Típus

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)

