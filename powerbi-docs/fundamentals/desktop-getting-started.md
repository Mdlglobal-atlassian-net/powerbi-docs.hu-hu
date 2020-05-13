---
title: Első lépések a Power BI Desktopban
description: Első lépések a Power BI Desktopban.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 26e9e130c4dc2f19684626144bfbce7f2838a18b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83359542"
---
# <a name="get-started-with-power-bi-desktop"></a>Első lépések a Power BI Desktopban
Üdvözöljük a Power BI Desktoppal tett első lépésekhez szóló útmutatóban. Bemutatjuk a Power BI Desktop működését, képességeit, és hogy hogyan készíthet robusztus adatmodelleket és látványos jelentéseket az üzleti intelligencia erősítéséhez.

A Power BI Desktop működését és használatát gyorsan áttekintheti, ha néhány perc alatt végignézi az útmutató képernyőképeit. Ha alaposabban el szeretne mélyedni a témában, elolvashat minden szakaszt, végrehajthatja a lépéseket, és elkészítheti saját Power BI Desktop-fájlját, amelyet közzétehet a [Power BI szolgáltatásban](https://app.powerbi.com/), és megoszthat másokkal.

![Power BI Desktop-jelentés](media/desktop-getting-started/hero-02.png)

Megtekintheti a [Power BI Desktop – Az első lépések](https://www.youtube.com/watch?v=Qgam9M8I0xA) című videót, és letöltheti a [Pénzügyi minta](https://go.microsoft.com/fwlink/?LinkID=521962) Excel-munkafüzetet a videóban bemutatott lépések követéséhez.

## <a name="how-power-bi-desktop-works"></a>A Power BI Desktop működése
A Power BI Desktop használatával lehetséges:
1. Kapcsolódás adatokhoz, akár több adatforráshoz is.
1. Az adatok átalakítása tényfeltáró, szemléletes adatmodelleket előállító lekérdezésekkel.
1. Vizualizációk és jelentések létrehozása az adatmodellekkel. 
1. Jelentésfájlok megosztása másokkal, akik felhasználhatják azokat, építhetnek rájuk és meg is oszthatják őket. A *.pbix* Power BI Desktop-fájlokat megoszthatja ugyanúgy, mint bármilyen más fájlt, de a leghatékonyabb módszer, ha feltölti ezeket a [Power BI szolgáltatásba](https://preview.powerbi.com/). 

A Power BI Desktop integrálva van Microsoft a jól bevált lekérdezésmotorjával, valamint adatmodellezési és vizualizációs technológiáival. Az adatelemzők és mások is létrehozhatnak lekérdezésekből, adatkapcsolatokból, modellekből és jelentésekből álló gyűjteményeket, amelyeket egyszerűen megoszthatnak másokkal. A Power BI Desktop és a Power BI szolgáltatás együttesével egyszerűbben modellezhetők, készíthetők, megoszthatók és kiterjeszthetők az adatuniverzumból nyert elemzési eredmények.

A Power BI Desktop egyetlen helyre vonja össze, leegyszerűsíti és megkönnyíti az üzletiintelligencia-tárak és -jelentések tervezésének és létrehozásának széttagolt, elkülönülő és fáradságos folyamatát.
Készen áll rá, hogy kipróbálja? Tegyük meg az első lépéseket!

> [!NOTE]
> Olyan adatokhoz és jelentésekhez, amelyeknek helyszínieknek kell maradniuk, a [Power BI jelentéskészítő kiszolgáló](../report-server/get-started.md), a Power BI egy speciális, különálló verziója áll rendelkezésre. A Power BI jelentéskészítő kiszolgáló a Power BI Desktop egy ugyancsak speciális és különálló verzióját használja. Ez a Power BI Desktop a Power BI jelentéskészítő kiszolgálóhoz, amely kizárólag a Power BI jelentéskészítő kiszolgálóval együtt használható. Ez a cikk a Power BI Desktop standard verzióját ismerteti.

## <a name="install-and-run-power-bi-desktop"></a>A Power BI Desktop telepítése és futtatása
A Power BI Desktop letöltéséhez nyissa meg a [Power BI Desktop letöltési oldalát](https://powerbi.microsoft.com/desktop) és válassza az **Ingyenes letöltés** lehetőséget. Más letöltési lehetőségeket a [Letöltési és nyelvi beállítások](https://www.microsoft.com/download/details.aspx?id=58494) lehetőség választásával érhet el. 

A Power BI Desktopot a Power BI szolgáltatásból is letöltheti. Válassza a felső menüsor **Letöltés** ikonját, majd a **Power BI Desktop** elemet.

![A Power BI Desktop letöltése a Power BI szolgáltatásból](media/desktop-getting-started/gsg_download.png)

A Microsoft Store oldalon válassza a **Letöltés** lehetőséget, és az utasításokat követve telepítse a Power BI Desktopot a számítógépére. Indítsa el a Power BI Desktopot a Windows **Start** menüjéből, vagy a Windows tálcán lévő ikonnal.

A Power BI Desktop első indulásakor megjelenik az **Üdvözlőképernyő**.

Az **Üdvözlőképernyőn** **betölthet adatokat**, megtekintheti a **Legutóbbi forrásokat**, megnyithatja a legutóbbi jelentéseket, **Más jelentéseket nyithat meg**, vagy választhat egyéb hivatkozásokat. Azt is kiválaszthatja, hogy indításkor mindig megjelenjen-e az **Üdvözlőképernyő**. Válassza a bezárás ikont az **Üdvözlőképernyő** bezárásához.

![A Power BI Desktop üdvözlő képernyője](media/desktop-getting-started/designer_gsg_startsplashscreen.png)

A Power BI Desktop bal oldalán találhatók a három Power BI Desktop-nézet ikonjai: **Jelentés**, **Adatok** és **Kapcsolatok**, felülről lefelé. Az aktuális nézetet sárga sáv jelöli a bal oldalon, és a nézet az ikonok bármelyikének kiválasztásával megváltoztatható. 

![A három Power BI Desktop-nézet ikon](media/desktop-getting-started/designer_gsg_viewtypes.png)

Az alapértelmezett nézet a **Jelentés**. 

![A Power BI Desktop Jelentés nézete](media/desktop-getting-started/designer_gsg_blankreport.png)

A Power BI Desktop része a **Power Query-szerkesztő** is, amely külön ablakban nyílik meg. A **Power Query-szerkesztőben** lekérdezéseket állíthat össze és adatokat alakíthat át, majd betöltheti a finomított adatmodellt a Power BI Desktopba jelentések létrehozásához.

## <a name="connect-to-data"></a>Csatlakozás adatokhoz
Ha telepítve van a Power BI Desktop, máris csatlakozhat az adatok egyre bővülő forrásaihoz. Ha látni szeretné a sokféle elérhető adatforrást, válassza az **Adatok betöltése** > **Továbbiak** lehetőséget a Power BI Desktop **Kezdőlapján**, majd az **Adatok betöltése** ablakban görgesse végig az **Összes** adatforrás listáját. Ebben a rövid bemutatóban több különböző **webes** adatforráshoz csatlakozhat.

![Webes adatforrás kiválasztása az Adatok betöltése ablakban ](media/desktop-getting-started/getdataweb.png)

Tegyük fel, hogy adatelemzőként dolgozik egy napszemüvegekkel kereskedő vállalatnál. Előfordulhat, hogy olyan értékesítési helyek kiválasztásában szeretne segíteni ügyfelének, ahol a leggyakrabban süt a nap. A Bankrate.com [A nyugdíjba vonuláshoz legjobb és legrosszabb államok](https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/) oldala érdekes adatokat kínál ebben a témában.

A Power BI Desktop **Kezdőlapján** válassza az **Adatok betöltése** > **Web** lehetőséget egy webes adatforráshoz való csatlakozáshoz. 

![Webes adatforrás kiválasztása](media/desktop-getting-started/gsg_syw_2.png)

A **Webhelyről** párbeszédpanelen illessze be a *https:\//www.bankrate.com/retirement/best-and-worst-states-for-retirement/* címet az **URL-cím** mezőbe, majd válassza az **OK** gombot. 

![Webcím beillesztése a Webhelyről párbeszédpanelen](media/desktop-getting-started/gettingstarted_8.png)

Ha a rendszer kéri, válassza a **Csatlakozás** lehetőséget a **Webes tartalom elérése** képernyőn, hogy névtelen hozzáférést használhasson. 

A Power BI Desktop lekérdezési funkciója működésbe lép, és kapcsolódik a webes forráshoz. A **Kezelő** ablakban adja vissza azt, amit a weblapon talált, ebben az esetben egy **Ranking of best and worst states for retirement** (A nyugdíjba vonuláshoz legjobb és legrosszabb államok rangsorolása) nevű táblázatot és egy dokumentumot. Önt a táblázat érdekli, tehát válassza ki azt az előnézete megjelenítéséhez.

Ekkor választhatja a **Betöltés** lehetőséget a táblázat betöltéséhez, vagy az **Adatok átalakítása** lehetőséget, hogy módosításokat végezzen a táblázatban annak betöltése előtt.

![Weblapról származó táblázat előnézete](media/desktop-getting-started/datasources_fromnavigatordialog.png)

Ha az **Adatok átalakítása** lehetőséget választja, elindul a Power Query-szerkesztő a tábla jellemző nézetével. A **Lekérdezés beállításai** panel a jobb oldalon található, de mindig megjelenítheti, ha a Power Query-szerkesztő **Nézet** lapján a **Lekérdezés beállításai** lehetőséget választja. 

![A Power Query-szerkesztő a lekérdezési beállításokkal](media/desktop-getting-started/designer_gsg_editquery.png)

További információ az adatokhoz való csatlakozásról: [Csatlakozás adatokhoz a Power BI Desktopban](../connect-data/desktop-connect-to-data.md).

## <a name="shape-data"></a>Adatok formázása
Az adatforráshoz való csatlakozás után már az igényeihez igazíthatja az adatokat. Az adatok *formálásához* lépésenkénti utasításokat adhat meg a Power Query-szerkesztőnek az adatok betöltés és bemutatás közbeni igazításához. A formálás nem érinti az eredeti adatforrást, csak az adatoknak ezt az aktuális nézetét. 

> [!NOTE]
> Az ehhez az útmutatóhoz használt táblázat idővel változhat. Ennek megfelelően a követendő lépések is változhatnak, így a lépések és eredmények saját helyzetre való alkalmazása némi kreativitást kíván – de ezt tekintse úgy, mint a tanulás izgalmának egyik részét. 

A formálás jelentheti az adatok *átalakítását*, például oszlopok vagy táblák átnevezését, sorok vagy oszlopok eltávolítását vagy adattípusok módosítását is. A Power Query-szerkesztő sorrendben rögzíti ezeket a lépéseket a **Lekérdezés beállításai** panel **Alkalmazott lépések** területén. Ezek a lépések lesznek végrehajtva minden alkalommal, amikor a lekérdezés csatlakozik az adatforráshoz, így az adatok mindig a megadott módon lesznek formálva. Ez a folyamat akkor megy végbe, amikor a Power BI Desktop lekérdezési funkcióját használja, vagy ha egy másik felhasználó elindít egy megosztott lekérdezést, például a Power BI szolgáltatásban. 

Figyelje meg, hogy a **Lekérdezés beállításai** panel **Alkalmazott lépések** területe már tartalmaz néhány lépést. Az egyes lépéseket kijelölve megtekintheti azok hatását a Power Query-szerkesztőben. Először megadott egy webes forrást, majd megtekintette a táblázat előnézetét a **Kezelő** ablakban. A harmadik **Típus megváltoztatva** nevű lépésben a Power BI felismerte az egész számokból álló adatokat az importálás során, és automatikusan **Egész számra** változtatta az eredeti webes **Szöveg** *adattípust*. 

![A Lekérdezés beállításai panel három alkalmazott lépéssel](media/desktop-getting-started/designer_gsg_appliedsteps_changedtype.png)

Ha meg kell változtatnia az adattípust, jelölje ki a módosítandó oszlopot vagy oszlopokat. Több szomszédos oszlop kijelöléséhez tartsa lenyomva **Shift** billentyűt, nem szomszédos oszlopok kijelöléséhez pedig a **Ctrl** billentyűt. Kattintson a jobb gombbal az oszlop fejlécére, válassza az **Adattípus módosítása** lehetőséget, majd válasszon új adattípust a menüből, vagy gördítse le a **Kezdőlap** **Átalakítás** csoportja melletti **Adattípus** listát.

![Adattípus módosítása](media/desktop-getting-started/designer_gsg_changedatatype.png)

> [!NOTE]
> A Power BI Desktopban a Power Query-szerkesztővel elérhető tevékenységekhez a menüszalag vagy a helyi menü használható. A menüszalag **Kezdőlap** vagy **Átalakítás** lapján elérhető feladatok többsége úgy is elvégezhető, hogy a jobb gombbal egy elemre kattint, és az így megjelenő menüből választ.

Mostantól saját módosításokat és átalakításokat végezhet az adatokon, és ezek az elemek megjelennek az **Alkalmazott lépések** között. 

A napszemüvegek értékesítése szempontjából például az időjárási rangsor a leglényegesebb, ezért úgy dönt, hogy a táblázatot az **Overall rank** (Összesített rangsor) helyett a **Weather** (Időjárás) oszlop szerint rendezi. Gördítse le a nyilat a **Weather** fejléc mellett, és válassza a **Rendezés növekvő sorrendbe** lehetőséget. Az adatok most már az időjárási értékelés szerint rendezve jelennek meg, a **Sorok rendezve** lépés pedig megjelenik az **Alkalmazott lépések** között. 

![Sorok növekvő rendezése](media/desktop-getting-started/shapecombine-changetype-b.png)

A legrosszabb időjárású államokban nem nagyon szeretne napszemüveget árulni, ezért úgy dönt, hogy eltávolítja ezeket a táblázatból. A **Kezdőlap** **Sorok számának csökkentése** csoportjából válassza a **Sorok eltávolítása** > **Utolsó sorok eltávolítása** lehetőséget. Az **Utolsó sorok eltávolítása** párbeszédpanelen írja be a *10* értéket, majd válassza az **OK** lehetőséget. 

![Utolsó sorok eltávolítása](media/desktop-getting-started/pbi_gsg_getdata3.png)

A legrosszabb időjárással jellemzett utolsó 10 sor el lett távolítva a táblázatból, az **Utolsó sorok eltávolítása** lépés pedig megjelenik az **Alkalmazott lépések** között.

Úgy dönt, hogy a táblázat túl sok, az Ön számára szükségtelen információt tartalmaz, és hogy eltávolítja a **Affordability** (Megélhetés), **Crime** (Bűnözés), **Culture** (Kultúra) és **Wellness** oszlopokat. Jelölje ki az eltávolítani kívánt oszlopok fejlécét. Több szomszédos oszlop kijelöléséhez tartsa lenyomva **Shift** billentyűt, nem szomszédos oszlopok kijelöléséhez pedig a **Ctrl** billentyűt. 

Ez után válassza az **Oszlopok eltávolítása** lehetőséget a **Kezdőlap** **Oszlopok kezelése** csoportjából. Azt is megteheti, hogy jobb gombbal az kijelölt oszlopfejlécekre kattint, és a menüből választja ki az **Oszlopok eltávolítása** lehetőséget. A kijelölt oszlopok el lesznek távolítva, és az **Oszlopok eltávolítva** lépés megjelenik az **Alkalmazott lépések** között.

![Oszlopok eltávolítása](media/desktop-getting-started/pbi_gsg_getdata3a.png)

Jobban átgondolva rájön, hogy a **Megélhetés** mégis lényeges lehet a napszemüveg-értékesítés szempontjából. Szeretné visszakapni ezt az oszlopot. Az utolsó lépést egyszerűen visszavonhatja az **Alkalmazott lépések** panelen a lépés melletti **X** törlő ikont választva. Most ismételje meg ezt a lépést úgy, hogy csak a törlendő oszlopokat jelöli ki. Rugalmasabb megoldásként külön lépésekben is törölheti az oszlopokat. 

Az **Alkalmazott lépések** panelen bármelyik lépésre rákattinthat a jobb gombbal, így törölheti, átnevezheti, feljebb vagy lejjebb mozgathatja a sorban, és lépéseket vehet fel vagy törölhet utána. Köztes lépések esetén a Power BI Desktop figyelmezteti, hogy a módosítás a későbbi lépéseket is befolyásolhatja, és hibát okozhat a lekérdezésben.  

![Alkalmazott lépések módosítása](media/desktop-getting-started/designer_gsg_install.png)

Ha például nem szeretné a **Weather** (Időjárás) érték szerint rendezni a táblázatot, megpróbálhatja törölni a **Sorok rendezve** lépést. A Power BI Desktop figyelmezteti, hogy a lépés törlése miatt a lekérdezés hibás lehet. Az utolsó 10 sort az időjárás szerinti rendezés után távolította el, tehát a rendezés kiiktatása után más sorok lesznek eltávolítva. Akkor is figyelmeztetést kap, ha kijelöli a **Sorok rendezve** lépést, és új köztes lépést kísérel meg felvenni ezen a ponton.  

![Lépés törlésére vonatkozó figyelmeztetés](media/desktop-getting-started/deletestepwarning.png)

Végül a táblázat címét szeretné módosítani, hogy az időjárás helyett a napszemüveg-kereskedelemre utaljon. A **Lekérdezés beállításai** panel **Tulajdonságok** területén írja át a régi címet a *Napszemüvegek árusítására legalkalmasabb államok* szövegre.

Az átformált adatokra vonatkozó kész lekérdezés az alábbihoz lesz hasonló:

![Kész lekérdezés](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Az adatok átalakításáról az [Adatok átalakítása és egyesítése a Power BI Desktopban](../connect-data/desktop-shape-and-combine-data.md) című cikk nyújt további információkat.

## <a name="combine-data"></a>Adatok összevonása
Érdekes adataink vannak az egyes államokról, amelyeknek még hasznát fogjuk venni újabb elemzések és lekérdezések készítésekor. Ám van egy probléma: a legtöbb helyen az államok nem a teljes nevükkel, hanem kétbetűs rövidítésükkel szerepelnek. Az adatok használatához valahogyan le kell képeznie a rövidítéseket az államok nevére.

Szerencséje van. Egy másik nyilvános adatforrás éppen erre szolgál, de az adatokat alaposan át kell alakítania ahhoz, hogy a napszemüveg-kereskedelmi táblázattal *együtt* használhassa.

Az államnevek rövidítéseinek adatait úgy töltheti be a Power Query-szerkesztőbe, hogy az **Új forrás** > **Web** lehetőséget választja a menüszalag **Kezdőlap** lapján az **Új lekérdezés** csoportban. 

![Új forrás](media/desktop-getting-started/pbi_gettingstartedsplash_resized.png)

A **Webhelyről** párbeszédpanelen írja be az államnevek rövidítéseit tartalmazó webhely URL-címét: *https:\//en.wikipedia.org/wiki/List_of_U.S._state_abbreviations*.

A **Kezelő** ablakban jelölje ki a **Codes and abbreviations for U.S. states, federal district, territories, and other regions** (Az USA államainak, szövetségi körzeteinek, területeinek és más régióinak kódjai és rövidítései) táblázatot, majd válassza az **OK** gombot. A táblázat megnyílik a Power Query-szerkesztőben.

Távolítsa el az összes oszlopot a **Name and status of region** (Régió neve és állapota), **Name and status of region2** (Régió neve és állapota 2), and **ANSI** kivételével. Az oszlopok megtartásához tartsa lenyomva a **Ctrl** billentyűt és jelölje ki az oszlopokat. Ez után vagy kattintson az oszlopfejlécekre, és válassza a **Többi oszlop eltávolítása** lehetőséget, vagy válassza a **Többi oszlop eltávolítása** lehetőséget a **Kezdőlap** **Oszlopok kezelése** csoportjában. 

Gördítse le a **Name and status of region2** oszlopfejléc melletti nyilat, majd válassza a **Szűrők** > **Egyenlő** lehetőséget. A **Sorok szűrése** párbeszédpanelen gördítse le az **Egyenlő** melletti **Érték megadása vagy kiválasztása** mezőt, majd válassza a **State** (Állam) elemet. 

Válassza a **Vagy** relációt, majd az **Egyenlő** második mezője után válassza a **State ("Commonwealth")** (Állam (Nemzetközösségi)) elemet. Válassza az **OK** lehetőséget. 

![Sorok szűrése](media/desktop-getting-started/filterrows.png)

Az olyan további értékek eltávolításával, mint a **Federal district** és az **island** egy 50 állam nevéből és azok hivatalos kétbetűs rövidítéseiből álló listát kap. Az oszlopokat át is nevezheti beszédesebb nevekre, mint például: **Állam neve**, **Állapot** és **Rövidítés**, ha a jobb gombbal az oszlop fejlécére kattint, és az **Átnevezés** lehetőséget választja.

Figyelje meg, hogy a **Lekérdezés beállításai** panel **Alkalmazott lépések** területén minden lépés rögzítve van.

Az átalakított táblázat ekkor az alábbihoz hasonló:

![Államkódok átalakított táblázata](media/desktop-getting-started/statecodes.png)

Változtassa meg a táblázat címét az *Államkódok* értékre a **Lekérdezés beállításai** **Tulajdonságok** mezőjében. 

Az **Államkódok** tábla megformálása után egyetlen táblázatban *egyesítheti* a kettőt. Mivel a jelenlegi táblázatok az adatokra alkalmazott lekérdezések eredményei, ezeket is *lekérdezéseknek* nevezzük. A lekérdezések összevonásának két fő módja az *egyesítés* és az *összefűzés*. 

Ha egy vagy több oszlopot szeretne hozzáadni egy másik lekérdezéshez, akkor *egyesíti* a lekérdezéseket. Ha további adatsorokat szeretne hozzáadni egy meglévő lekérdezéshez, *összefűzi* a lekérdezéseket.

Ebben az esetben *egyesíteni* szeretné az **Államkódok** táblázatot a **Napszemüvegek árusítására legalkalmasabb államok** táblázatával. A lekérdezések egyesítéséhez váltson át a **Napszemüvegek árusítására legalkalmasabb államok** táblázatra úgy, hogy kiválasztja azt a Power Query-szerkesztő bal oldalán található **Lekérdezések** panelen. Ez után válassza a **Lekérdezések egyesítése** lehetőséget a menüszalag **Kezdőlapjának** **Összevonás** csoportjából.

Az **Egyesítés** ablakban gördítse le a mezőt, hogy a rendelkezésre állók közül kiválaszthassa az **Államkódok** táblázatot. Mindkét táblázatban jelölje ki a megfeleltetéshez használandó mezőt. Ez ebben az esetben a **Napszemüvegek árusítására legalkalmasabb államok** táblázat **State** (Állam) oszlopa és az **Államkódok** táblázat **Állam neve** oszlopa. 

Ha megjelenik az **Adatvédelmi szintek** párbeszédpanel, válassza az **Adatvédelmi szintek figyelmen kívül hagyása ennél a fájlnál** beállítást, majd a **Mentés** lehetőséget. Válassza az **OK** lehetőséget. 

![Lekérdezések egyesítése](media/desktop-getting-started/shapecombine_merge.png)

A **Napszemüvegek árusítására legalkalmasabb államok** táblázat jobb szélén megjelenik egy új, **Államkódok** nevű oszlop. Ez az államok kódjait megadó lekérdezést tartalmazza, amelyet a Napszemüvegek árusítására legalkalmasabb államok lekérdezéssel egyesített. Az egyesített táblázat összes oszlopa az **Államkódok** oszlopba van tömörítve. *Kibonthatja* az egyesített táblázatot, hogy csak a kívánt oszlopokat foglalja bele. 

![Egyesített lekérdezésoszlop](media/desktop-getting-started/mergedquery.png)

Az egyesített táblázat kibontásához és a kívánt oszlopok kiválasztásához kattintson a **Kibontás** ikonra az oszlop fejlécében. A **Kibontás** párbeszédpanelen válassza ki a **Rövidítés** oszlopot. Szüntesse meg az **Eredeti oszlopnév használata előtagként** beállítás bejelölését, majd válassza az **OK** gombot. 

![Kibontott oszlop kiválasztása az egyesített táblázatból](media/desktop-getting-started/shapecombine_mergeexpand.png)

> [!NOTE]
> Kísérletezhet az **Államkódok** táblázat bevonásával. Próbálkozzon nyugodtan, és ha nem elégedett az eredménnyel, egyszerűen törölje ezt a lépés az **Alkalmazott lépések** listájából a **Lekérdezés beállításai** panelen. Tetszőleges számú alkalommal próbálkozhat, amíg a kibontási folyamattal a kívánt eredményt nem éri el.

Az adatok formázási és összevonási lépéseinek részletes leírása: [Adatok formázása és összevonása a Power BI Desktopban](../connect-data/desktop-shape-and-combine-data.md).

Most egyetlen lekérdezési táblája van, amelyben két, igényei szerint formázott adatforrás van összevonva. Erre a lekérdezésre sok további érdekes adatkapcsolat épülhet, például az államok demográfiai, jóléti vagy kikapcsolódási lehetőségekkel kapcsolatos adataival.

![Formázott és egyesített lekérdezések](media/desktop-getting-started/mergedcolumn.png)

Mostanra elegendő adattal rendelkezik ahhoz, hogy érdekes jelentést készítsen a Power BI Desktopban. Mivel ez fontos fordulópont, alkalmazza a **Power Query-szerkesztőben** végzett módosításokat, és töltse be azokat a Power BI Desktopba úgy, hogy a **Bezárás és alkalmazás** lehetőséget választja a menüszalag **Kezdőlapján**. Választhatja önmagában az **Alkalmazás** lehetőséget is, hogy a lekérdezés megnyitva maradjon a Power Query-szerkesztőben, amíg Ön a Power BI Desktoppal dolgozik. 

![Bezárás és a módosítások alkalmazása](media/desktop-getting-started/shapecombine_closeandapply.png)

A táblázaton további módosítások végezhetők, ha az már be van töltve a Power BI Desktopba, a modell ismételt betöltésével pedig alkalmazni tudja a végzett módosításokat. A **Power Query-szerkesztőt** úgy nyithatja meg újra a Power BI Desktopból, hogy a Power BI Desktop menüszalagjának **Kezdőlapján** a **Lekérdezések szerkesztése** lehetőséget választja. 

## <a name="build-reports"></a>Jelentések összeállítása
A Power BI Desktop **Jelentés** nézetében vizualizációkat és jelentéseket készíthet. A **Jelentés** nézet hat fő területből áll:

![A Power BI Desktop Jelentés nézete](media/desktop-getting-started/designer_gsg_reportview.png)

1. A felső menüszalag, amely a jelentésekhez és vizualizációkhoz kapcsolódó általános feladatokat jeleníti meg.
2. A középső vászon, ahol vizualizációkat hozhat létre és rendezhet el.
3. Az oldalfülek alsó területe, ahol jelentésoldalakat választhat ki és hozhat létre.
4. A **Szűrők** panel, ahol az adatvizualizációkat szűrheti.
5. A **Vizualizációk** panel, ahol vizualizációkat vehet fel, módosíthat és szabhat testre, valamint részletezéseket alkalmazhat.
6. A **Mezők** panel, amely a lekérdezésekben elérhető mezőket mutatja. Ezeket a mezőket a vászonra, a **Szűrők** panelre vagy a **Vizualizációk** panelre áthúzva vizualizációkat hozhat létre vagy módosíthat.

A **Szűrők**, **Vizualizációk** és **Mezők** panelt a panel felső részén látható nyilak kiválasztásával bonthatja ki és csukhatja össze. A panelek összecsukásával több helyhez juthat a vásznon a látványos vizualizációk kialakításához. 

![Panelek kibontása vagy összecsukása](media/desktop-getting-started/designer_gsg_collapsepanes.png)

Egy egyszerű vizualizáció létrehozásához elég kiválasztani bármelyik mezőt a mezőlistából, vagy áthúzni a mezőt a vászonra a **Mezők** panelről. Húzza a vászonra például a **Napszemüvegek árusítására legalkalmasabb államok** táblázat **State** (Állam) mezőjét, és figyelje meg, hogy mi történik.

![Az Állam mező áthúzása térkép-vizualizáció létrehozásához](media/desktop-getting-started/designer_gsg_reportfirstdrag.png)

Figyelje meg jól! A Power BI Desktop felismerte, hogy a **State** mező földrajzihely-adatokat tartalmaz, és automatikusan térképalapú vizualizációt hozott létre. A vizualizáció az adatmodellben szereplő 40 államhoz mutat adatpontokat. 

A **Vizualizációk** panelen a vizualizációval kapcsolatos információkat láthatja és módosíthatja. 

![A Vizualizációk panel](media/desktop-getting-started/designer_gsg_visualizationtypes.png)

1. Az ikonokon a létrehozott vizualizáció típusa látható. Egy kijelölt vizualizáció típusát úgy változtathatja meg, hogy másik ikont választ. Új vizualizációt hozhat létre, ha meglévő vizualizáció kijelölése nélkül választ ki egy ikont. 
2. A **Vizualizációk** panel **Mezők** területén adatmezőket húzhat a panel **Jelmagyarázat** és más mezőgyűjtőibe. 
3. A **Formázás** beállítással formázást és más vezérlőket alkalmazhat a vizualizációkra. 

A **Mezők** és a **Formázás** területen elérhető beállítások köre az aktuális vizualizáció és adatok típusától függ.

Azt szeretné, hogy a térkép-vizualizáción csak a 10 legjobb időjárású állam jelenjen meg. Ahhoz, hogy csak az első 10 állam jelenjen meg, a **Mezők** panelen vigye a kurzort a **State (Összes)** elemre, és bontsa ki azt a megjelenő nyíllal. A **Szűrő típusa** területen gördítse le a listát és válassza a **Felső N** elemet. Az **Elemek megjelenítése** területen válassza az **Alsó** beállítást, mert a legkisebb számértékkel rangsorolt elemeket szeretné megjeleníteni, a következő mezőbe pedig írja be a *10* számot.

Húzza a **Weather** mezőt a **Mezők** panelről az **Érték szerint** mezőre, majd válassza a **Szűrő alkalmazása** lehetőséget. 

![A 10 legjobb időjárású állam szűrése](media/desktop-getting-started/gsg_share5.png)

A térkép-vizualizáción már csak a 10 legjobb időjárású állam látható. 

Változtassa meg a vizualizáció címét a **Vizualizációk** panel **Formázás** ikonját, majd a **Cím** elemet választva. Ez után a **Cím szövege** területen begépelheti *A 10 legjobb időjárású állam* címet. 

![Cím megváltoztatása](media/desktop-getting-started/designer_gsg_report1.png)

Most vegyen fel egy olyan vizualizációt, amely a 10 legjobb időjárású állam nevét és 1-től 10-ig terjedő azok rangsorolását is bemutatja. Ehhez válasszon egy üres területet a vásznon, majd válassza ki az **Oszlopdiagram** ikont a **Vizualizációk** panelen. A **Mezők** panelen jelölje ki a **State** és a **Weather** mezőt. A lekérdezésben szereplő 40 államot a legmagasabb numerikus rangsor-értéktől a legalacsonyabbig, tehát a legrosszabbtól a legjobb időjárás felé rendezve bemutató oszlopdiagram. 

![Oszlopdiagram-vizualizáció](media/desktop-getting-started/gsg_share7.png)

A sorrend megfordításához, hogy az 1. sorszám álljon legelöl, válassza a **További lehetőségeket** kínáló három pontot a vizualizáció jobb felső sarkában, majd a menüből válassza a **Rendezés növekvő sorrendbe** lehetőséget. 

![Rendezés növekvő sorrendbe](media/desktop-getting-started/shapecombine_mergequeries.png)

Ahhoz, hogy a táblázatból csak az első 10 állam jelenjen meg, alkalmazza ugyanazt a szűrést, amelyet a térkép-vizualizáción. 

A vizualizáció címét ugyanúgy változtathatja meg, mint a térkép-vizualizációét. Szintén a **Vizualizációk** panel **Formázás** területén módosítsa az **Y tengely** > **Tengely címe** értéket a **Weather** értékről az *Időjárási rangsor* szövegre, hogy érthetőbb legyen. Ez után kapcsolja **Ki** az **Y-tengely** kapcsolóját, az **Adatcímkék** mellettit pedig kapcsolja **Be**. 

A 10 legjobb időjárású állam így már sorrendben jelenik meg, a sorszámával együtt. 

![Befejezett oszlopdiagram](media/desktop-getting-started/shapecombine_changetype.png)

Hasonló vagy más vizualizációkat készíthet a **Affordability** (Megélhetés) és az **Overall ranking** (Összesített rangsor) mezőkről is, de több mezőt is kombinálhat egyetlen vizualizációban. Számos érdekes jelentést és vizualizációt hozhat létre. Az alábbi **Táblázat** és **Vonal- és fürtözött oszlopdiagram** vizualizációk a 10 legjobb időjárású államot mutatják be a megélhetéssel és az összesített rangsorolással együtt:

![Táblázat, vonal és fürtözött oszlop vizualizációk](media/desktop-getting-started/designer_gsg_report2costofliving.png)

Különböző jelentésoldalakon különböző vizualizációkat jeleníthet meg. Új oldal felvételéhez válassza a meglévő oldalak melletti **+** szimbólumot az oldalak sávjában, vagy válassza a menüszalag **Kezdőlapjának** **Beszúrás** > **Új oldal** elemét. Egy oldal átnevezéséhez kattintson duplán az oldal nevére az oldalak sávján, vagy kattintson rá a jobb gombbal, és válassza az **Oldal átnevezése** elemet, majd írja be az új nevet. A jelentés egy másik oldalára úgy léphet át, hogy kiválasztja az oldalt az oldalak sávján. 

![Oldalválasztó sáv](media/desktop-getting-started/pages.png)

A jelentésoldalakra a **Kezdőlap** **Beszúrás** csoportjában vehet fel szövegdobozokat, képeket és gombokat. A vizualizációk formátumbeállításainak módosításához jelölje ki a vizualizációt, majd válassza a **Formázás** ikont a **Vizualizációk** panelen. Az oldalméret, a hátterek és egyéb oldalinformációk konfigurálásához válassza a **Formázás** ikont úgy, hogy egy vizualizáció sincs kijelölve.

Ha végzett az oldalak és vizualizációk létrehozásával, válassza a **Fájl** > **Mentés** menüpontot és mentse a jelentést. 

![Kész Power BI Desktop-jelentésoldal](media/desktop-getting-started/finished-report.png)

További információ a jelentésekről: [Jelentés nézet a Power BI Desktopban](../create-reports/desktop-report-view.md).

## <a name="share-your-work"></a>Hogyan oszthatja meg munkáját
Az elkészült Power BI Desktop-jelentést másokkal is megoszthatja. A munkáját több módon is megoszthatja. A jelentést ugyanúgy terjesztheti *.pbix* fájlként, mint bármely más fájlt, feltöltheti a *.pbix* fájlt a Power BI szolgáltatásból, vagy közzéteheti közvetlenül a Power BI Desktopból a Power BI szolgáltatásba. Ahhoz, hogy jelentést tehessen közzé vagy tölthessen fel a Power BI szolgáltatásba, rendelkeznie kell Power BI-fiókkal. 

A Power BI Desktopból a **Power BI** szolgáltatásba történő közzétételhez válassza a menüszalag **Kezdőlapjának** **Közzététel** elemét.

![A Közzététel lehetőség kiválasztása](media/desktop-getting-started/gsg_syw_1.png)

A rendszer felkérheti, hogy jelentkezzen be a Power BI-ba, vagy hogy válasszon célt.

Amikor befejeződött a közzétételi folyamat, az alábbi párbeszédpanel jelenik meg:

![Sikeres Power BI-közzététel](media/desktop-getting-started/gsg_syw_3.png)

Amikor kiválasztja a hivatkozást, hogy megnyissa a jelentést a Power BI-ban, a jelentés az Ön Power BI-webhelyén nyílik meg a **Saját munkaterület** > **Jelentések** területen. 

A munkája megosztásának másik módja, ha a **Power BI** szolgáltatásban betölti azt. Nyissa meg a Power BI-t egy böngészőben a *https:\//app.powerbi.com* webhely megnyitásával. A Power BI **Kezdőlapján** válassza az bal alsó sarokban található **Adatok betöltése** lehetőséget a Power BI Desktop-jelentés betöltési folyamatának megkezdéséhez.

![Az Adatok betöltése lehetőség kiválasztása a Power BI kezdőlapján](media/desktop-getting-started/pbi_gsg_getdata1.png)

A következő oldalon válassza a **Betöltés** lehetőséget a **Fájlok** területen.

![Fájlok lekérése](media/desktop-getting-started/pbi_gsg_getdata2.png)

A következő oldalon válassza a **Helyi fájl** lehetőséget. Tallózással jelölje ki a *.pbix* Power BI Desktop-fájlt, majd válassza a **Megnyitás** lehetőséget. 

A fájl az importálása után megjelenik a **Saját munkaterület** > **Jelentések** területen a Power BI szolgáltatás bal oldali paneljén.

![A Power BI-ba importált Power BI Desktop-fájl](media/desktop-getting-started/pbi_gsg_getdata4.png)

A fájl kijelölésekor a jelentés első oldala jelenik meg. Az oldalakat a jelentéstől balra található fülekkel választhatja ki. 

Ha módosítani szeretne egy jelentést a **Power BI** szolgáltatásban, válassza a **További lehetőségek** > **Szerkesztés** lehetőséget a jelentés vásznának tetején. A módosítások mentéséhez válassza a **Másolat mentése** lehetőséget.

![Jelentés szerkesztése és másolat mentése](media/desktop-getting-started/gsg_share4.png)

A **Power BI** szolgáltatásban számos különféle érdekes vizualizációt létrehozhat a jelentésből, és ezeket rögzítheti egy *irányítópulton*. A **Power BI** szolgáltatás irányítópultjainak megismerése érdekében tekintse meg [a tökéletes irányítópult megtervezésével kapcsolatos tippeket](../create-reports/service-dashboards-design-tips.md). További információt az irányítópultok létrehozásáról, megosztásáról és módosításáról az [irányítópultok megosztásával kapcsolatos](../collaborate-share/service-share-dashboards.md) cikkben találhat.

Jelentés vagy irányítópult megosztásához válassza a megnyitott jelentés- vagy irányítópult-oldal felső részén található **Megosztás** lehetőséget, vagy válassza a jelentés vagy irányítópult neve melletti **Megosztás** ikont a **Saját munkaterület** > **Jelentések** vagy a **Saját munkaterület** > **Irányítópultok** listában.

Töltse ki a **Jelentés megosztása** vagy az **Irányítópult megosztása** képernyőt, ahol e-mailt küldhet, vagy előállíthat egy hivatkozást, amellyel megoszthatja másokkal a jelentést vagy az irányítópultot. 

![Jelentés megosztása](media/desktop-getting-started/gsg_share6.png)

A Power BI Desktopban és a Power BI szolgáltatásban számos lenyűgöző adategyesítést és vizualizációt hozhat létre. 

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop támogatja a diagnosztikai portokhoz való csatlakozást. A diagnosztikai port lehetővé teszi, hogy más eszközök csatlakozzanak és diagnosztikai célú nyomkövetést végezzenek. A diagnosztikai port használata során *a modell semmiféle módosítása sem támogatott. A modell megváltoztatása adatsérülést és adatvesztést okozhat.*

A Power BI Desktop sokféle képességéről az alábbi forrásanyagokban talál további információt:

* [Lekérdezések áttekintése a Power BI Desktopban](../transform-model/desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](../connect-data/desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](../connect-data/desktop-connect-to-data.md)
* [Oktatóanyag: Adatok formázása és kombinálása a Power BI Desktoppal](../connect-data/desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](../transform-model/desktop-common-query-tasks.md)   
