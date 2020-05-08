---
title: Jelentéstervezési tippek a Power BI Jelentéskészítőhöz
description: Az alábbi tippek segítségével lapszámozott jelentéseket tervezhet a Power BI Jelentéskészítőben.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 13b9e37d4a64493dfdcac02d9df86a1e19a1c24b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921171"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Jelentéstervezési tippek a Power BI Jelentéskészítőhöz
  Az alábbi tippek segítségével lapszámozott jelentéseket tervezhet a Power BI Jelentéskészítőben.  
  
   
  
##  <a name="designing-reports"></a><a name="DesigningReports"></a> Jelentések tervezése  
  
-   Egy jól megtervezett jelentés információt közvetít és cselekvéshez vezet. Azonosítsa a kérdéseket, amelyeket a jelentés segít megválaszolni. A jelentés tervezése során tartsa szem előtt ezeket a kérdéseket.  
  
-   Hatékony adatvizualizációk tervezéséhez gondolja át, hogyan jeleníthetők meg az információk a jelentés felhasználója számára könnyen megérthető módon. Olyan adatterületet válasszon, amely jól megfelel a vizualizálni kívánt adatoknak. Egy diagram például hatékonyabban mutat be összegzett és összesített információkat, mint egy részletes adatokat tartalmazó sokoldalas táblázat. Egy adathalmaz adatai bármilyen adatterületen megjeleníthetők, beleértve a diagramokat, térképeket, jelzőket, értékgörbéket, adatsávokat és táblázatos adatokat egy rácsos adatterülethez igazodó különböző elrendezésekben. 
  
-   Ha a jelentést egy meghatározott exportálási formátumban tervezi átadni, tesztelje az exportálási formátumot a tervezési folyamat elején. A funkció támogatása a választott megjelenítőtől függően változhat.  
  
-   Ha összetett elrendezést készít, akkor azt lépésenként alakítsa ki. A jelentéselemek szervezésére téglalapokat használhat tárolóként. Adatterületeket közvetlenül a tervezőfelületen készíthet. A lehető legnagyobb munkaterület érdekében a készeket a tároló téglalapba húzhatja. Ha tárolóként téglalapokat használ, azok teljes tartalmát egy lépésben áthelyezheti. A téglalapokkal a jelentéselemek egyes oldalakon való megjelenése is jobban szabályozható.  
  
-   A jelentés zsúfoltságának csökkentése érdekében fontolja meg a feltételes láthatóság használatát egyes elemeknél, hogy a felhasználó dönthessen azok megjelenítéséről. A láthatóság egy paraméter vagy egy szövegdoboz kapcsolója alapján is beállítható. Feltételesen elrejtett szövegdobozokkal a köztes számítási eredményeket is megmutathatja. Ha egy jelentésben nem várt adatok jelennek meg, a köztes eredmények megjelenítése segíthet a képletek hibáinak felderítésében.  
  
-   Ha rácsos adatterületen vagy téglalapokban beágyazott elemekkel dolgozik, különböző háttérszínt állíthat be a tárolóhoz és a tárolt elemekhez. A háttérszín alapértelmezett beállítása: **Nincs szín**. A beállított háttérszínű elemek a **Nincs szín** háttérszín-beállítású elemeken keresztül is látszanak. Ez a technika segít a megfelelő elem kijelölésében az olyan megjelenítési tulajdonságok beállításához, mint a rácscellák szegélyeinek megjelenítése.  
  
 A jelentés tervezésekor megfontolandó szempontokról további információkat talál a [Jelentés tervezése a Jelentéskészítőben](report-builder-planning-report.md) című cikkben.  
  
##  <a name="naming-conventions-for-reports-data-sources-and-datasets"></a><a name="NamingConventions"></a> Jelentések, adatforrások és adathalmazok elnevezési konvenciói  
  
-   Az adatforrásokhoz és adathalmazokhoz használjon az adatok eredetét dokumentáló elnevezési konvenciókat.  
  
    1.  **Adatforrások**. Ha biztonsági okokból nem szeretne valós kiszolgálót vagy adatbázist megnevezni, használjon olyan aliast, amely tudatja a felhasználóval, hogy honnan származnak az adatok.  
  
    2.  **Adathalmazok.** Olyan nevet használjon, amely jelzi, hogy melyik adatforráson alapul.  
  
##  <a name="working-with-data"></a><a name="Data"></a> Az adatok felhasználása  
  
-   Első lépésként érje el, hogy minden adat, amellyel dolgozni szeretne, megjelenjen a Jelentésadatok panelen. Miközben tisztázza a kérdéseket, amelyek megválaszolására a jelentést tervezi, gondolja át, hogyan korlátozhatja a jelentés adathalmazainak adatait csupán a szükségesekre.  
  
-   Általában csak azokat az adatokat foglalja bele a jelentésbe, amelyeket megjelenít. Az adathalmaz-lekérdezésben használjon lekérdezésváltozókat, hogy a felhasználók kiválaszthassák, mely adatokat szeretnék látni a jelentésben. Megosztott adathalmazok létrehozásakor jelentésparamétereken alapuló szűrők megadásával biztosíthatja az egyforma működést.  
  
-   Ha járatos a lekérdezések írásában, akkor tudja, hogy közepes adatmennyiség esetén az adatokat érdemesebb lehet a jelentésben, és nem a lekérdezésben csoportosítani. Ha minden csoportosítást a lekérdezésben végez, akkor a jelentés inkább a lekérdezés eredményhalmazának bemutatása lesz. Nagy mennyiségű adat összesített értékeinek diagramon vagy mátrixban való megjelenítéséhez viszont nincs szükség a részletes adatok belefoglalására.  
  
-   A követelményektől függően a jelentésbeli adatok forrásainak nevét és helyét, az adathalmazt lekérdező parancsok szövegét és a paraméterértékeket is megjelenítheti a jelentésben. Sok új felhasználó először arra kérdez rá, hogy honnan származnak az adatok. A jelentés zsúfoltságának csökkentése érdekében feltételesen elrejtheti az ilyen típusú információk szövegdobozait, így a felhasználók dönthetik el, hogy látni szeretnék-e azokat. Ezt az információt próbálja a jelentés utolsó oldalán elhelyezni. A szövegdoboz láthatóságát egy olyan paraméter alapján állítsa be, amelyet a felhasználó módosíthat.  
  
##  <a name="interacting-with-the-report-design-surface"></a><a name="DesignSurface"></a> A jelentéstervező felület használata  
 A jelentéstervező felület nem alakhű. Amikor jelentéselemeket helyez el a tervezőfelületen, azok egymáshoz viszonyított helyzete határozza meg, hogy hogyan jelennek meg a kész jelentésoldalon. Az üres hely megmarad.  
  
-   Az elemeket az igazítási vonalak és elrendezési gombok segítségével rendezheti el a jelentéstervező felületén. Egymáshoz igazíthatja például a kijelölt elemek tetejét vagy szélét, kiterjeszthet egy elemet, hogy ugyanakkora legyen, mint egy másik elem, vagy beállíthatja az elemek közötti közöket.  
  
-   A tervezőfelületen a nyílbillentyűkkel állíthatja be a kijelölt elemek helyzetét és méretét. Nagyon hasznosak többek között az alábbi billentyűkombinációk:  
  
    -   **Nyílbillentyűk** – A kijelölt jelentéselem mozgatása.  
  
    -   **CTRL+nyílbillentyűk** – A kijelölt jelentéselem elmozdítása.  
  
    -   **CTRL+SHIFT+nyílbillentyűk** – A kijelölt jelentéselem méretének növelése vagy csökkenése.  
  
-   Egy elem téglalaphoz adásához mutasson az egérkurzor bal felső hegyével a elem kezdeti helyére a tároló téglalapban. A kijelölt elemeket elhelyezheti a billentyűkombinációk segítéségével. A téglalap automatikusan kiterjed, hogy a benne lévő elemek elférjenek.  
  
-   Több elemet úgy adhat egy rácsos adatterület egy cellájához, hogy először egy téglalapot ad hozzá, majd az elemeket.  
  
     Alapértelmezés szerint minden rácscella egy szövegdobozt tartalmaz. Amikor a téglalapot hozzáadja a cellához, a téglalap átveszi a szövegdoboz helyét. Ha beágyazott jelzőt például egy rácscellában lévő téglalapban helyez el, akkor egyszerűbben szabályozhatja egy diagram vagy jelző méretének növekedését, amikor módosítja a cellát tartalmazó sor magasságát.  
  
-   A tervezőfelület nézetét a **Nagyítás** vezérlő használatával állíthatja be. Dolgozhat az egész oldallal, vagy az oldal kisebb részeivel.  
  
-   Ha mezőket szeretne áthúzni a Jelentésadatok panelről a Csoportosítás panelre, akkor ne húzza át a mezőt a tervezőfelületen lévő más jelentéselemeken, mert ezzel kijelöli ezt a másik elemet, és megszünteti a rácsos adatterület kijelölését. Húzza a mezőt lefelé a Jelentésadatok panelről, majd húzza át a Csoportosítás panelre.  
  
###  <a name="selecting-items"></a><a name="Selecting"></a> Elemek kijelölése  
 A jelentéstervező felületen a kívánt elem egyszerűbb kijelöléséhez használhatja az ESC billentyűt, a jobb kattintásra megjelenő helyi menüt, a Tulajdonságok panelt és a Csoportosítás panelt.  
  
-   -   Az ESC lenyomásával válhat a tervezőfelület egyazon részén elhelyezkedő, egymást fedő jelentéselemek között.  
  
    -   Bizonyos jelentéselemeken megpróbálhatja a jobb kattintásra megjelenő helyi menüvel kijelölni a jelentéselemet, vagy a jelentéselem kívánt részét.  
  
    -   A Tulajdonságok panelen az aktuális kijelölés tulajdonságai láthatók.  
  
    -   Egy rácsos adatterületen úgy dolgozhat sorcsoportokkal vagy oszlopcsoportokkal, hogy kijelöli a csoportot a Csoportosítás panelen.  

  
##  <a name="working-with-specific-types-of-report-items"></a><a name="ReportItems"></a> Adott típusú jelentéselemek használata  
  
###  <a name="working-with-parameters"></a><a name="Parameters"></a> Paraméterek használata  
  
-   A jelentésparaméterek elsődleges rendeltetéses az adatok szűrése az adatforrásnál, hogy csak az legyen visszaadva, ami a jelentés céljaihoz szükséges.  
  
-   Jelentésparaméterek használatakor meg kell találnia a középutat a kezelhetőség, és felhasználó támogatása között, hogy megkaphassa a kívánt eredményeket. Beállíthat például olyan alapértelmezett értéket egy paraméterhez, amelyről tudja, hogy sokan használják.  
  
###  <a name="working-with-text"></a><a name="Text"></a> Szöveg használata  
  
-   Ha többsoros szöveget illeszt be egy szövegdobozba, az egyetlen folyamatos szövegként lesz hozzáadva. Minden folyamatos szöveg csak egy egységként formázható. A sorok független formázásához szúrjon be a megfelelő helyre sortörést az Enter billentyűvel. Ez után már külön alkalmazhat formázást és stílusokat a szövegdobozban lévő szöveg soraira.  
  
-   Formátumtulajdonságokat és műveleteket állíthat be egy szövegdobozra, vagy a szövegdobozban lévő helyőrző szövegre. Ha csak egy sornyi szöveg van, akkor a tulajdonságokat hatékonyabb a szövegdobozra megadni, mint a szövegre.  
  
###  <a name="working-with-expressions"></a><a name="Expressions"></a> Kifejezések használata  
  
-   Ismerje meg az egyszerű és összetett kifejezésformákat. Egyszerű kifejezést közvetlenül begépelhet szövegdobozokba, tulajdonságokba a Tulajdonságok panelen, vagy a párbeszédpanelek kifejezéseket elfogadó helyeire.
  
-   Kifejezés létrehozásakor egyszerűbb egymástól egyes részeit külön létrehozni, és ellenőrizni azok értékét. Végül az összes részből összeállíthatja a végleges kifejezést. Hasznos technika szövegdobozt felvenni egy mátrixcellába, megjeleníteni a kifejezés összes részét, és feltételes láthatóságot beállítani a szövegdobozra. A rejtett szövegdoboz szegélyének stílusát és színét úgy szabályozhatja, hogy a szövegdobozt először egy téglalapba helyezi, majd a téglalap szegélystílusát és -színét a mátrixéval egyezőre állítja be.  
  
###  <a name="working-with-indicators"></a><a name="Indicators"></a> Jelzők használata  
  
-   A jelzők alapértelmezés szerint legalább három állapotot jelezhetnek. Miután hozzáad egy jelölőt egy jelentéshez, állapotok hozzáadásával vagy eltávolításával konfigurálhatja azt. Hogy a felhasználók jobban megfigyelhessék, olyan jelzőt válasszon, amelynek a színe és az alakja is változik.  
  
##  <a name="controlling-the-rendering-of-report-items-on-the-report-page"></a><a name="Rendering"></a> A jelentésoldalon lévő jelentéselemek megjelenítésének szabályozása  
  
-   A jelentéstervező felületen a jelentéselemek mérete úgy nő, hogy elférjen rajtuk a társított adathalmaz, kifejezés, segédjelentés vagy szöveg tartalma.  
  
    -   Amikor elemet helyez el a jelentésoldalon, az elem és az attól jobbra kezdődő összes többi elem távolsága lesz a minimális távolság, amelyet meg kell tartani a jelentéselem vízszintes növekedésekor. Hasonló módon az elem és a felette lévő elem távolsága lesz az a minimális távolság, amelyet meg kell tartani a jelentéselem függőleges növekedésekor.  
  
    -   A jelentésbeli elemek az adatok befogadásához szükséges mértékben növekednek, és félretolják a társelemeket (a velük közös szülőtárolóban lévő elemeket), az alábbi szabályoknak megfelelően:  
  
    -   Minden elem úgy mozdul el lefelé, hogy megtartsa a minimális távolságot önmaga és a felette végződő elemek között.  
  
    -   Minden elem úgy mozdul el jobbra, hogy megtartsa a minimális távolságot önmaga és a tőle balra végződő elemek között. Jobbról balra elrendezett rendszerek esetén minden elem úgy mozdul el balra, hogy megtartsa a minimális távolságot önmaga és a tőle jobbra végződő elemek között.  
  
    -   A tárolók úgy növekednek, hogy helyet adjanak a gyermekelemeik növekedéséhez. Egy kijelölt elem Tulajdonságok paneljén a Szülő tulajdonság adja meg az elem tárolóját. A Dokumentumvázlat panelt is használhatja a jelentéselemek tartalmazási hierarchiájának megtekintésére.  
  
    -   Az **Elrendezés** eszköztár több gombot is kínál a jelentéselemek szegélyeinek, középpontjainak és közeinek igazítására. Az **Elrendezés** eszköztár engedélyezéséhez mutasson a **Nézet** menü **Eszköztárak** elemére, majd kattintson az **Elrendezés** elemre.  
  
-   Ha azt tervezi, hogy .pdf-fájlként menti a jelentést, a jelentés szélességét pontosan arra az értékre kell beállítania, amely a kívánt eredményt adja az exportfájlformátumban. A jelentésoldal szélességét beállíthatja például pontosan 18,6 centiméterre, a bal- és jobboldali margót pedig 1,2 centiméterre.  
  
-   A jelentéstervező eszköztárán található **Nyomtatási elrendezés** és **Oldalbeállítás** lehetőséggel a nyomtatásnak megfelelő nézetben jelenítheti meg a jelentést. A felesleges üres oldalakat a következő módon távolíthatja el:  
  
    1.  Távolítson el minden üres helyet az adatterületek között és a jelentés szélein.  
  
    2.  Csökkentse az oldalmargókat a **Jelentés tulajdonságai** párbeszédpanelen.  
  
    3.  Használjon **Téglalapokat** tárolóként, hogy egyszerűbben szabályozhassa a jelentéselemek megjelenítését.  
  
    4.  Az oszlopfejlécekben módosítsa a WritingMode szövegdoboz-tulajdonságot, hogy függőleges szöveget használjon.  

 További információ: [Ne legyenek üres lapok a többoldalas jelentések nyomtatásakor](../guidance/report-paginated-blank-page.md).

 Ez a viselkedés, a jelentéselemek szélesség és magasság tulajdonsága, a jelentés törzsének mérete, az oldalmagasság és oldalszélesség beállítása, a szülőjelentés margóbeállításai és az oldaltörések megjelenítőre jellemző támogatása együttesen határozza meg, hogy mely jelentéselemek férnek el együtt egy megjelenített oldalon.
 
## <a name="next-steps"></a>További lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)  
