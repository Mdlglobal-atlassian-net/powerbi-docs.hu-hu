---
title: DirectQuery az SAP HANA-hoz a Power BI Desktopban
description: Megfontolandó szempontok a DirectQuery SAP HANA-val való használatakor
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9d7c5415d084ea7ca9b6a6dd4da3e84662fc6349
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61303797"
---
# <a name="directquery-and-sap-hana"></a>A DirectQuery és az SAP HANA
Az **SAP HANA**-adatforrásokhoz közvetlenül kapcsolódhat a **DirectQuery** használatával. Az SAP HANA-hoz való kapcsolódás kétféle módszerrel is elvégezhető:

* **Az SAP HANA többdimenziós forrásként való kezelése (alapértelmezett):**  Ebben az esetben a rendszer hasonlóan viselkedik ahhoz, amikor a Power BI más többdimenziós forrásokhoz, például az SAP Business Warehouse-hoz vagy az Analysis Serviceshez kapcsolódik. Ha az SAP HANA-hoz ezzel a beállítással kapcsolódik, egyetlen elemzési vagy számítási nézet lesz kiválasztva, és ennek a nézetnek a mértékei, hierarchiái és attribútumai lesznek elérhetők a mezőlistában. A vizualizációk létrehozásakor az adatok összesítése mindig az SAP HANA-ból lesz lekérdezve. Ez az ajánlott módszer, és egyúttal az alapértelmezett beállítás is az SAP HANA-t használó új DirectQuery-jelentéseknél.

* **Az SAP HANA relációs forrásként való kezelése:** Ebben az esetben a Power BI relációs forrásként kezeli az SAP HANA-t. Ez nagyobb rugalmasságot biztosít. Ennél a módszernél ügyelni kell arra, hogy a mértékek az elvárt módon legyenek összesítve, és hogy ne merüljenek fel teljesítménybeli problémák.

A kapcsolódási módszert egy globális beállítással lehet meghatározni, amelyet a **Fájl > Lehetőségek és beállítások**, majd a **Beállítások > DirectQuery** kiválasztásával, azután **Az SAP HANA relációs forrásként való kezelése** választásával lehet beállítani, ahogy az alábbi képen látható. 

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

Ha a HANA relációs forrásként való kezelését választotta, az az SAP HANA-ra vonatkozó DirectQueryt használó minden létrehozott *új* kapcsolatot is befolyásol. Az aktuális jelentésben már meglévő SAP HANA-kapcsolatokra azonban nincs hatással, ahogyan a többi megnyitott jelentés kapcsolatait sem befolyásolja. Ezért ha ez a beállítás nincs engedélyezve, akkor ha az **Adatok beolvasása** lehetőséggel új SAP HANA-kapcsolatot ad hozzá, akkor ez a kapcsolat az SAP HANA-t többdimenziós forrásként kezeli majd. Ha azonban megnyit egy másik jelentést, amely már kapcsolódik az SAP HANA-hoz, akkor az a jelentés továbbra is azt a beállítást alkalmazza, amelyet *a jelentés létrehozásakor* meghatározott. Ez azt is jelenti, hogy azok a 2018 februárja előtt létrehozott jelentések, amelyek már rendelkeznek SAP HANA-kapcsolattal, továbbra is relációs forrásként kezelik az SAP HANA-t. 

A két megközelítés eltérő működésmóddal jár, és egy már meglévő jelentést nem lehetséges egyikről a másikra módosítani. 

Az alábbiakban részletesen is megvizsgáljuk a két megközelítést.

## <a name="treat-sap-hana-as-a-multi-dimensional-source-default"></a>Az SAP HANA többdimenziós forrásként való kezelése (alapértelmezett)

Alapértelmezés szerint minden új SAP HANA-kapcsolat ezt az új módszert alkalmazza, azaz többdimenziós forrásként kezeli az SAP HANA-t. Ha az SAP HANA-kapcsolatot relációs forrásként szeretné kezelni, a **Fájl > Lehetőségek és beállítások > Beállítások** területen jelölje be a **Direct Query > Az SAP HANA relációs forrásként való kezelése** jelölőnégyzetet. Amíg ez a funkció **előzetes** verzióban van, a többdimenziós megközelítés használatával létrehozott jelentések *nem tehetők közzé* a Power BI szolgáltatásban, és közzétételük esetén hiba jelentkezik, ha a jelentést megnyitják a Power BI szolgáltatásban.  

Ha az SAP HANA-hoz mint többdimenziós forráshoz kapcsolódik, az alábbi szempontok érvényesek:

* Az **Adatok beolvasása navigátorban** egyetlen SAP HANA-nézet választható ki. Egyedi mértékek vagy attribútumok nem választhatók ki. A kapcsolódás idején nincs definiálva lekérdezés, ellentétben az adatimportálással vagy a DirectQuery használatával, amikor az SAP HANA-t relációs forrásként kezeli a rendszer. Ez azt is jelenti, hogy ezzel a kapcsolódási módszerrel nem lehet SAP HANA SQL-lekérdezést közvetlenül használni.

* A mezőlistában megjelenik a kiválasztott nézethez tartozó összes mérték, hierarchia és attribútum. 

* Mivel a mérték a vizualizációban használatos, a mérték értékét a vizualizációhoz szükséges összesítés szintjén kérdezi le a rendszer az SAP HANA-tól. Ezért a nem additív mértékek esetén (például számlálók, arányok stb.) minden összesítést az SAP HANA végez el, a Power BI-ban már nem történik további összesítés. 

* Ahhoz, hogy midig a helyes összesített értékeket lehessen lekérni az SAP HANA-tól, bizonyos korlátozásokat be kell tartani. Például nem lehetséges hozzáadni számított oszlopokat, vagy ugyanabban a jelentésben több SAP HANA-nézetből származó adatokat kombinálni. 

Az SAP HANA többdimenziós forrásként való kezelése nem biztosítja a *relációs* megközelítésnél tapasztalható nagyobb rugalmasságot, de egyszerűbb annál, és helyes összesített értékeket nyújt bonyolultabb SAP HANA-mértékek esetén is, és általában jobb teljesítményt eredményez. 

A **mezők** listája az SAP HANA-nézethez tartozó összes mértéket, attribútumot és hierarchiát tartalmazza. Ennek a módszernek a használatánál az alábbi viselkedés tapasztalható:

* A legalább egy hierarchiában megtalálható attribútumok mindegyike alapértelmezés szerint el lesz rejtve. Szükség esetén azonban meg is jeleníthetőek. Ehhez a mezőlista helyi menüjében válassza a **Rejtettek megjelenítése** lehetőséget. Ugyanebben a helyi menüben szükség esetén meg is jeleníthetőek.

* Az SAP HANA-ban meghatározható, hogy az attribútumok címkeként egy másik attribútumot használjanak. Az 1, 2, 3 stb. értékeket tartalmazó **Product** például címkeként használhatja a **ProductName** attribútumot, amely a Bicikli, Ing, Kesztyű stb. értékeket tartalmazza. Ebben az esetben a mezőlistában egyetlen mezőként a **Product** jelenik meg, amelynek az értékei Bicikli, Ing, Kesztyű stb., de amelynek rendezési alapja és az egyedisége az 1,2,3 kulcsértékek alapján lesz meghatározva. Emellett létre lesz hozva a rejtett **Product.Key** oszlop is, amely lehetővé teszi, hogy szükség esetén hozzá lehessen férni az alapul szolgáló értékekhez is. 

Az alapul szolgáló SAP HANA-nézetben definiált minden változó megjelenik a kapcsolódáskor, és a szükséges értékek így megadhatók. Ezek az értékek később meg is változtathatók. Ehhez a menüszalagon válassza a **Lekérdezések szerkesztése**, majd a **Paraméterek kezelése** lehetőséget a legördülő listából. 

A megengedett modellezési műveletekre szigorúbb korlátozások vonatkoznak, mint általában a DirectQuery használatánál, mivel biztosítani szükséges, hogy az SAP HANA-ból mindig a megfelelő összesített adatok legyenek lekérdezve. Ezzel együtt azonban számos kiegészítés és módosítás is engedélyezett, többek között mértékek definiálása, mezők átnevezése és elrejtése vagy a megjelenítési formátum meghatározása. Az ilyen változások mind megmaradnak frissítés után is, és az SAP HANA-n végzett nem ütköző módosítások is alkalmazva lesznek. 

### <a name="additional-modeling-restrictions"></a>További modellezési korlátozások

A DirectQuery SAP HANA-val való használatakor (azt többdimenziós forrásként kezelve) a legfőbb további modellezési korlátozások a következők: 

* **Nem támogatottak a számított oszlopok:** A számított oszlopok létrehozásának lehetősége le van tiltva. Ez azt is jelenti, hogy a számított oszlopokat létrehozó Csoportosítás és Fürtözés művelet sem érhető el.
* **További mértékkorlátozások:** További, az SAP HANA által nyújtott támogatás szintjét tükröző korlátozások vonatkoznak a mértékekben használható DAX-kifejezésekre.
* **Kapcsolatok definiálása nem támogatott:** Egy jelentésen belül csak egyetlen nézetet lehet lekérdezni, és ezért nem lehetséges kapcsolatokat definiálni.
* **Nincs adatnézet:** Az **Adatnézet** alapértelmezés szerint megjeleníti a részletességiszint-adatokat a táblákban. Az SAP HANA és a hasonló OLAP-források természetéből adódóan az SAP HANA-ban ez a nézet nem érhető el.
* **Az oszlopok és mértékek részletei rögzítettek:** A mezőlistában látható oszlopok és mértékek listája a forrásuk miatt rögzített és nem módosítható. Például nem lehet oszlopokat törölni, sem módosítani az adattípusukat (ugyanakkor át lehet őket nevezni).
* **További korlátozások a DAX-ben:** További, a forrás korlátozásait tükröző korlátozások vonatkoznak a mértékekben használható DAX-re. Például nem lehet a táblákban összesítési függvényeket használni.

### <a name="additional-visualization-restrictions"></a>További vizualizációs korlátozások

A DirectQuery SAP HANA-val való használatakor (azt többdimenziós forrásként kezelve) a vizualizációkat érintik bizonyos korlátozások: 
* **Nincs oszlopösszesítés:** Nem módosítható a vizualizációs oszlopok összesítése, a beállítás mindig *Nincs összegzés*.

## <a name="treat-sap-hana-as-a-relational-source"></a>Az SAP HANA relációs forrásként való kezelése 

Ha az SAP HANA-hoz mint relációs forráshoz kapcsolódik, elérhetővé válik néhány további lehetőség. Például létrehozhatók számított oszlopok, több SAP HANA-nézetből is felhasználhatók adatok, és az eredményül kapott táblák között kapcsolatok hozhatók létre. Ha azonban ilyen módszerrel használja az SAP HANA-t, fontos tisztában lennie a kapcsolat kezelését érintő néhány szemponttal, amelyek az alábbiakat érintik: 

* A várt eredmények akkor jelennek meg, ha az SAP HANA-nézet nem additív mértékeket tartalmaz (például különböző számadatokat, vagy átlagértékeket egyszerű összegek helyett).
* A kapott lekérdezések hatékonyak

Érdemes gondot fordítani a relációs forrás, például az SQL Server működésének tisztázására, amikor az **Adatok lekérése** utasításban vagy a **Lekérdezésszerkesztőben** meghatározott lekérdezés összesítést végez. A következő példában egy **Lekérdezésszerkesztőben** meghatározott lekérdezés *ProductID* (termékazonosító) szerint rendezve adja vissza az átlagárat.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Ha a Power BI-ba importálja az adatokat (a DirectQuery helyett), az az alábbiakat eredményezi:

* Az adatok importálása a **Lekérdezésszerkesztőben** létrehozott lekérdezés által meghatározott összesítési szinten történik. Például átlagár termékek szerint rendezve. Ennek eredményeként egy *ProductID* (termékazonosító) és egy *AveragePrice* (átlagár) oszlopokat tartalmazó tábla jön létre, amely vizualizációkban használható.
* Egy vizualizáción belül minden további összesítés (pl. *Sum*, *Average*, *Min* stb.) az importált adatok felhasználásával történik. Ha például belefoglalja az *AveragePrice* (átlagár) értéket egy vizualizációba, akkor a rendszer alapértelmezés szerint a *Sum* (összeg) összesítést fogja használni, és az *AveragePrice* összegét fogja visszaadni minden *ProductID*-hez (termékazonosítóhoz) – amely ebben a példában 13,67. Ugyanez vonatkozik a vizualizációban használt minden alternatív összegzési függvényre (pl. *Min*, *Average* stb.). Az *Average* (átlag) függvény például az *AveragePrice* esetében a 6,66, a 4 és a 3 átlagát fogja visszaadni, ami 4,56, nem pedig az alapul szolgáló tábla hat rekordjában szereplő *Price* (ár) értékek átlagát, ami 5,17.
  
Ha importálás helyett a **DirectQueryt** használja (ugyanazzal a relációs forrással), akkor is ugyanaz a szemantika, és az eredmények is pontosan ugyanazok lesznek:  

* Ugyanazon lekérdezés esetén logikusan ugyanazok az adatok kerülnek a jelentéskészítési rétegbe, még ha az adatok nem is lettek importálva.

* Egy vizualizáción belül minden további összesítés (*Sum*, *Average*, *Min* stb.) a lekérdezésből származó logikai tábla felhasználásával történik. Az *Average* függvény az *AveragePrice* esetében ekkor is ugyanazt az értéket (4,56) adja vissza.
  
Most vizsgáljuk meg az SAP HANA-t, amikor a kapcsolatot relációs forrásként kezeli. A Power BI az SAP HANA *Analitikus nézetével* és *Számítási nézetével* is működik, és mindkettő tartalmazhat mértékeket. Az SAP HANA jelenlegi módszere viszont szintén az előzőleg ebben a szakaszban bemutatott alapelveket használja: az **Adatok lekérése** utasításban vagy a **Lekérdezésszerkesztőben** meghatározott lekérdezés határozza meg az elérhető adatokat, és a vizualizáción belüli minden további összesítéshez azokat az adatokat használja fel. Ez az importálás és a DirectQuery használata esetén is igaz.  
Azonban az SAP HANA természetéből adódóan a kezdeti **Adatok lekérése** párbeszédablakban vagy a **Lekérdezésszerkesztőben** meghatározott lekérdezés mindig összesítő lekérdezés, és általában olyan mértékeket is tartalmaz, amelyekben a tényleges lekérdezést az SAP HANA-nézet határozza meg.

Az SQL Serverből vett fenti példa megfelelője, hogy adott egy *ID* (azonosító), *ProductID* (termékazonosító) és *DepotID* (raktár-azonosító) adatokból álló SAP HANA-nézet, amely többek között az *AveragePrice* (átlagérték) mértéket is tartalmazza (a nézetben *Average of Price* (ár átlaga) néven van meghatározva).  
    
Ha az **Adatok lekérése** utasítás használatakor kiválasztotta a **ProductID** és az **AveragePrice** mértékeket, akkor az határozza meg a lekérdezést a nézetben, és ezeket az összesített adatokat kéri le (az előző példában az egyszerűség kedvéért egy ál-SQL szerepel, amely nem felel meg tökéletesen az SAP HANA SQL szintaxisának). Ekkor a vizualizáción belül meghatározott minden további összesítés tovább összesíti az ilyen lekérdezések eredményét. Az SQL Server esetében fentebb leírtakhoz hasonlóan ez szintén érvényes az importálásra és a DirectQuery használatára is. A DirectQuery esetében a rendszer az **Adatok lekérése** utasításból vagy a **Lekérdezésszerkesztőből** származó lekérdezést az SAP HANA-hoz küldött egyetlen lekérdezés részkiválasztásaként használja, így valójában nem történik meg az összes adat beolvasása a további összesítés előtt.  

Mindezek a szempontok és viselkedésmódok az alábbi megfontolásokat teszik szükségessé a DirectQuery SAP HANA-val való használatánál:  

* A vizualizációkban elvégzett minden további összesítésre oda kell figyelni, amikor az SAP HANA-beli mérték nem additív (például nem egyszerű *Sum*, *Min* vagy *Max*).

* Az **Adatok lekérése** utasításban vagy a **Lekérdezésszerkesztőben** csak a szükséges oszlopokat kell kiválasztani a szükséges adatok lekéréséhez, hiszen az eredmény lekérdezés lesz, amelynek az SAP HANA-hoz továbbítható ésszerű lekérdezésnek kell lennie. Ha például több tucat oszlopot választott ki azzal az elgondolással, hogy későbbi vizualizációkban még szüksége lehet rájuk, akkor a részkiválasztásban használt összesítő lekérdezés még egy DirectQuery használatával indított egyszerű lekérdezés esetén is tartalmazni fogja azt a több tucat oszlopot, így az általános teljesítmény gyenge lesz.
  
Lássunk erre egy példát. Az alábbi példában öt oszlop van kiválasztva (a **CalendarQuarter**, a **Color**, a **LastName**, a **ProductLine** és a **SalesOrderNumber**) az **Adatok lekérése** párbeszédablakban, illetve az *OrderQuantity* mérték, ez pedig azt jelenti, hogy később egy a Min OrderQuantity (Minimális rendelési mennyiség) mértéket tartalmazó egyszerű vizualizációt kiválasztva az eredmény a következő SQL-lekérdezést küldi az SAP HANA-hoz. Az árnyékolt szakasz a részkiválasztást jelöli, amely az **Adatok lekérése** / **Lekérdezésszerkesztőből** származó lekérdezést tartalmazza. Ha ez a részkiválasztás magas számosságú eredményt ad, az valószínűleg gyenge SAP HANA-teljesítményt is eredményez.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
Ennek következtében ajánlott az **Adatok lekérése** utasításban vagy a **Lekérdezésszerkesztőben** kiválasztott elemeket csak a szükséges elemekre korlátozni úgy, hogy közben továbbra is ésszerű SAP HANA-lekérdezést eredményezzenek.  

## <a name="best-practices"></a>Ajánlott eljárások 

Az SAP HANA-hoz való kapcsolódás mindkét módszerénél a DirectQueryvel kapcsolatos ajánlások az SAP HANA-ra is vonatkoznak, különösképpen a megfelelő teljesítményre vonatkozóak. Ezekről az ajánlásokról részletesen olvashat a [DirectQuery használata a Power BI-ban](desktop-directquery-about.md) című témakörben.
   
## <a name="limitations"></a>Korlátozások

A következő listában található az SAP HANA összes olyan funkciója, amelyek nem teljesen támogatottak, vagy másképp viselkednek a Power BI használatakor. 

* **Szülő-gyermek hierarchiák** – A szülő-gyermek hierarchiák nem lesznek láthatók a Power BI-ban.
Ennek az az oka, hogy a Power BI az SQL-interfészen keresztül érti el az SAP HANA-t, SQL-en keresztül azonban nem érhetők el teljes mértékben a szülő-gyermek hierarchiák.
* **Egyéb hierarchia-metaadatok** – A Power BI megjeleníti a hierarchiák alapvető struktúráját, de egyes hierarchia-metaadatoknak (például hézagos hierarchiák viselkedésének felügyelete) nem lesz hatásuk.
Ez ugyancsak az SQL-interfész használata okozta korlátozások miatt van így.
* **Kapcsolódás SSL használatával** – Importálás módú és többdimenziós forrásokhoz kapcsolódhat SSL-lel, nem kapcsolódhat azonban SAP HANA példányokhoz, amelyek úgy vannak konfigurálva, hogy SSL-t használjanak a relációs összekötőhöz.
* **Attribútum-nézet támogatása** – A Power BI kapcsolódni tud az Elemzési és a Számítási nézetekhez, de nem tud közvetlenül kapcsolódni az Attribútum nézethez.
* **Katalógus objektumok támogatása** – A Power BI nem tud kapcsolódni Katalógus objektumokhoz.
* **Változók módosítása közzétételt követően** – A jelentés közzététele után a Power BI szolgáltatásban közvetlenül nem lehetséges módosítani az SAP HANA-változók értékét. 
 
## <a name="known-issues"></a>Ismert problémák 
Az alábbiakban minden olyan problémát felsorolunk, amely akkor merülhet fel, ha az SAP HANA-hoz a Power BI használatával (DirectQuery) kapcsolódik. 

* **Az SAP HANA-val kapcsolatos probléma számlálók vagy más mértékek lekérdezésénél** – Az SAP HANA helytelen értékeket ad vissza, ha Elemzési nézethez kapcsolódik, és ugyanabban a vizualizációban számláló vagy más, arányt tartalmazó mérték is szerepel. Ezt a viselkedést az SAP 2128928 számú megjegyzése ismerteti (Váratlan eredmények számított oszlop és számláló lekérdezésénél). Az arány mérték ilyen esetben hibás lesz. 

* **Több Power BI-oszlop egy SAP HANA-oszlopból** – Egyes számítási nézeteknél, ahol az SAP HANA-oszlop több hierarchiában is használatos, az SAP HANA az egyetlen oszlopot két külön attribútumként jeleníti meg. Ez azt eredményezi, hogy a Power BI két oszlopot hoz létre.  Ezek az oszlopok alapbeállítás szerint rejtve vannak, és a hierarchiát vagy az oszlopokat érintő minden lekérdezés helyesen működik majd. 
 
## <a name="next-steps"></a>Következő lépések

Ha többet szeretne megtudni a DirectQueryről, tekintse át a következő forrásanyagokat:

* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [Helyszíni adatátjáró](service-gateway-onprem.md)

