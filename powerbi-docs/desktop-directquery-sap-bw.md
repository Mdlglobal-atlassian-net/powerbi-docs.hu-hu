---
title: A DirectQuery és az SAP Business Warehouse (BW) a Power BI-ban
description: Megfontolandó szempontok a DirectQuery és az SAP Business Warehouse (BW) használatakor
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6c47fb847ff5360031f4bfe2974db9c405a4ce5f
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670739"
---
# <a name="directquery-and-sap-business-warehouse-bw"></a>DirectQuery és SAP Business Warehouse (BW)
Az **SAP Business Warehouse- (BW-)** adatforrásokhoz közvetlenül kapcsolódhat a **DirectQuery** használatával. Az SAP BW OLAP/többdimenziós természeténél fogva számos különbség van aközött, ha a DirectQueryt az SAP BW-vel használjuk, vagy ha valamilyen relációs forrással, például az SQL Serverrel. A különbségeket a következőképpen lehet összefoglalni:

* A relációs forrásokkal használt **DirectQuery**ben a mezőlistában elérhető adatokat logikailag lekérdezések határozzák meg (amelyeket az **Adatok lekérése** vagy a **Lekérdezésszerkesztő** párbeszédablakban lehet megadni). Ez *nem* így működik egy OLAP-forráshoz, például az SAP BW-hez való kapcsolódáskor. Ehelyett az SAP-kiszolgálóhoz az **Adatok lekérése** használatával való kapcsolódáskor csak az Infocube vagy BEx Query lekérdezést kell kiválasztani. Ezután a kiválasztott Infocube/BEx Query összes kulcsértéke és dimenziója elérhető lesz a mezőlistában.   
* Ugyanígy, az SAP BW-hez való kapcsolódáskor nincs **Lekérdezésszerkesztő**. Az adatforrások beállításai (például a kiszolgáló neve) a **Lekérdezések szerkesztése > Adatforrás beállításai** kiválasztásával módosíthatók. A paraméterek beállításai a **Lekérdezések szerkesztése > Paraméterek kezelése** elem választásával módosíthatók.
* Az OLAP-források egyedi természeténél fogva további korlátozások is érvényesek (a modellezésre és a vizualizációra vonatkozóan egyaránt) a DirectQuery szokványos korlátozásain felül. A korlátozásokat a cikk egy későbbi része ismerteti.

Mindemellett *kiemelt fontosságú* tisztában lenni azzal, hogy az SAP BW-nek számos olyan funkciója van, amelyeket a Power BI nem támogat, és hogy az SAP BW nyilvános felületének természetéből adódóan előfordulnak olyan, fontos esetek, amikor a Power BI-ban látható eredmények nem egyeznek azokkal az eredményekkel, amelyek egy SAP-eszköz használatakor láthatók. A korlátozásokat a cikk egy későbbi része ismerteti. Tekintse át alaposan a korlátozásokat és a viselkedésbeli különbségeket, hogy megfelelően tudja értelmezni a Power BI-ban látható, az SAP nyilvános felülete által visszaadott eredményeket.  

> [!NOTE]
> A DirectQuery SAP BW-vel való használatának lehetősége a Power BI Desktop 2018. márciusi frissítéséig előzetes verzióként állt rendelkezésre. Az előzetes időszakban kapott visszajelzések olyan fejlesztésekhez vezettek, amelyek az előzetes verzióval készült jelentéseket is érintik. Most, hogy a DirectQuery SAP BW-vel való használata általánosan elérhető, *feltétlenül* vesse el a meglévő (az előzetes verzióra épült), a DirectQueryt az SAP BW-vel használó jelentéseket, amelyeket a korábbi verzióval hozott létre. A DirectQuery SAP BW-vel való használatának általános elérhetősége előtt készült jelentésekben a frissítés kezdeményezésekor hibák fognak fellépni a metaadatoknak az alapjukul szolgáló SAP BW-kocka változásaival való frissítésére tett kísérlet következtében. Ezeket a jelentéseket készítse el újra egy üres jelentésből a DirectQuery SAP BW-vel való használatát biztosító funkció általánosan elérhető verziójával. 

## <a name="additional-modeling-restrictions"></a>További modellezési korlátozások
A DirectQuery SAP BW-vel való használatakor a Power BI-ban a legfőbb további modellezési korlátozások a következők:

* **Nem támogatottak a számított oszlopok:** A számított oszlopok létrehozásának lehetősége le van tiltva. Ez azt is jelenti, hogy a számított oszlopokat létrehozó Csoportosítás és Fürtözés művelet sem érhető el.
* **További mértékkorlátozások:** További, az SAP BW által nyújtott támogatás szintjét tükröző korlátozások vonatkoznak a mértékekben használható DAX-kifejezésekre.
* **Nem támogatott a kapcsolatok meghatározása:** A kapcsolatok a külső SAP-forrásból öröklődnek, és nem lehet a modellekben további kapcsolatokat meghatározni.
* **Nincs adatnézet:** Az **Adatnézet** alapértelmezés szerint megjeleníti a részletességiszint-adatokat a táblákban. Az SAP BW és a hasonló OLAP-források természetéből adódóan az SAP BW-ben ez a nézet nem érhető el.
* **Az oszlopok és mértékek részletei rögzítettek:** A mezőlistában látható oszlopok és mértékek listája a forrásuk miatt rögzített és nem módosítható. Például nem lehet oszlopokat törölni, sem módosítani az adattípusukat (ugyanakkor át lehet őket nevezni).
* **További korlátozások a DAX-ben:** További, a forrás korlátozásait tükröző korlátozások vonatkoznak a mértékekben használható DAX-re. Például nem lehet a táblákban összesítési függvényeket használni.

## <a name="additional-visualization-restrictions"></a>További vizualizációs korlátozások
A DirectQuery SAP BW-vel való használatakor a Power BI-ban a legfőbb további vizualizációs korlátozások a következők:

* **Nincs oszlopösszesítés:** Nem módosítható a vizualizációs oszlopok összesítése, a beállítás mindig *Nincs összegzés*.
* **A mértékek szűrése le van tiltva:** Az SAP BW nyújtotta támogatásnak megfelelően a mértékek szűrése le van tiltva.
* **Többszörös kiválasztás és belefoglalás/kihagyás:** A vizualizációkban több adatpont kiválasztása nem lehetséges, ha a pontok egynél több oszlop értékeit jelölik. Például egy országok szerinti eladásokat megjelenítő oszlopdiagram esetében, ha a kategória a jelmagyarázat része, nem lehet kiválasztani az (Amerikai Egyesült Államok, kerékpárok) vagy (Franciaország, ruhák) pontokat. Ugyanígy azt sem lehet beállítani, hogy az (Amerikai Egyesült Államok, kerékpárok) pont a kijelölése esetén ne jelenjen meg a vizualizációban. Mindkét korlátozás az SAP BW nyújtotta támogatást tükrözi.

## <a name="support-for-sap-bw-features"></a>SAP BW-funkciók támogatása
A következő táblázat felsorolja az SAP BW összes olyan funkcióját, amelyek nem teljesen támogatottak, vagy másképp viselkednek a Power BI használatakor.   

| Funkció | Leírás |
| --- | --- |
| Helyi számítások |A BEx Query-lekérdezésekben megadott helyi számítások más számokat mutatnak a BEx Analyzer és hasonló eszközökkel való megjelenítéskor. Azonban a nyilvános MDX felületen az SAP által visszaadott számok ezt nem tükrözik. <br/> <br/> **Ennélfogva a Power BI-vizualizációkban látható számok nem feltétlenül egyeznek meg az SAP-eszközök vonatkozó vizualizációiban láthatókkal.**<br/> <br/>  Például egy olyan BEx-lekérdezésből származó adatkocka-lekérdezéshez való kapcsolódáskor, amelynél az összesítési beállítás Összevonás (pl.: futó összeg), a Power BI az alapszámokat adja vissza, a beállítás figyelembevétele nélkül.  Ezután az adatelemző nyilván alkalmazhat egy futóösszeg-számítást helyileg a Power BI-ban, de ha ezt nem teszi meg, oda kell figyelnie arra, hogy miként értelmezi a számokat. |
| Összesítések |Bizonyos esetekben (főleg több pénznem használata esetén) az SAP nyilvános felülete által visszaadott összesített számok nem egyeznek az SAP-eszközök által mutatott számokkal. <br/> <br/> **Ennélfogva a Power BI-vizualizációkban látható számok nem feltétlenül egyeznek meg az SAP-eszközök vonatkozó vizualizációiban láthatókkal.** <br/> <br/> Például a BEx Analyzerben különböző pénznemek összegénél egy „*” jelenik meg, az SAP nyilvános felülete viszont visszaad egy összeget, és nem tájékoztat arról, hogy az ilyen összegnek nincs valós jelentése. Ezáltal a Power BI is megjeleníti a számot (ezzel összeadva a például dollárban, euróban és ausztrál dollárban értendő összegeket). |
| Pénznemformátum |A Power BI nem tükrözi a pénznemformátumot (például: $2300 vagy 4000 AUD). |
| Mértékegységek |A Power BI nem türközi a mértékegységeket (például: 230 kg). |
| Kulcs és szöveg (rövid, közepes, hosszú) |Az SAP BW jellemzői, például a CostCenter (Költségközpont) esetében a mezőlista egyetlen CostCenter-oszlopot jelenít meg.  Az oszlop használatakor az alapértelmezett szöveg jelenik meg.  A rejtett mezők megjelenítésével láthatóvá válik az egyedi név oszlopa is (amely egy, az SAP BW által hozzárendelt egyedi nevet ad vissza, amely az egyediség alapja).<br/> <br/>  A kulcs és egyéb szöveges mezők nem érhetők el. |
| Többszörös hierarchiájú jellemzők |Az **SAP**-ben a jellemzők több hierarchiával is rendelkezhetnek. Ez esetben, ha a BEx Analyzerben vagy egy hasonló eszközben a jellemzőt belefoglaljuk egy lekérdezésbe, akkor kiválasztható a használandó hierarchia. <br/> <br/> A **Power BI**-ban a különböző hierarchiák a mezőlistában egyazon dimenzió különböző hierarchiáiként jelennek meg.  Azonban ha egy adott dimenzió két különböző hierarchiájának több szintjét választjuk ki, az SAP üres adatokat ad vissza eredményként. |
| Hézagos hierarchiák kezelése |![](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| Méretezési faktor és előjel-megfordítás |Az SAP-ben a kulcsértékek rendelkezhetnek egy formázási lehetőségként megadott méretezési faktorral (például: 1000), ami azt jelenti, hogy minden megjelenítés e faktor szerint lesz skálázva. <br/> <br/> Ugyanígy egy olyan tulajdonsággal is rendelkezhetnek, amely megfordítja az előjelet. Egy ilyen kulcsérték használata a Power BI-ban (egy vizualizációban vagy egy számítás részeként) azt eredményezi, hogy a rendszer a nem skálázott számot használja (és nem fordítja meg az előjelet). A mögöttes méretezési faktor nem érhető el. A Power BI vizualizációiban a tengelyeken (K, M, B) megjelenő skálázási egységek a vizualizáció formázásának részeként módosíthatók. |
| Hierarchiák, amelyekben a szintek dinamikusan megjelennek és eltűnnek |Az SAP BW-hez való csatlakozáskor a rendszer lekéri a hierarchiaszintekre vonatkozó adatokat, amelyek alapján összeállítja a mezőlistában szereplő mezők készletét. Ezt a rendszer gyorsítótárazza, és ha a szintkészlet változik, a mezőkészlet akkor sem változik, amíg egy frissítési műveletet végre nem hajtanak rajta. <br/> <br/> Ez csak a **Power BI Desktopban** lehetséges. A szinteket érintő változások megjelenítését szolgáló frissítési műveleteket a Power BI szolgáltatásban a közzététel után nem lehet elvégezni. |
| Alapértelmezett szűrő |A BEx-lekérdezések tartalmazhatnak alapértelmezett szűrőket, amelyeket az SAP BEx Analyzer automatikusan alkalmaz. Ezek nincsenek közzétéve, így a Power BI-ban való azonos felhasználásuk nem alkalmazza alapértelmezés szerint ugyanazokat a szűrőket. |
| Rejtett kulcsértékek |A BEx-lekérdezések szabályozhatják a kulcsértékek láthatóságát, és a rejtett kulcsértékek nem jelennek meg az SAP BEx Analyzerben. Ez a nyilvános API-ra nincs hatással, így a rejtett kulcsértékek a mezőlistában továbbra is megjelennek. Azonban a Power BI-ban elrejthetők. |
| Numerikus formázás |A Power BI nem jeleníti meg automatikusan a numerikus formázásokat (tizedesjegyek számát, tizedeselválasztókat stb.). Azonban be lehet állítani ezeket a formázásokat a Power BI-on belül. |
| Hierarchiaverziók |Az SAP BW lehetővé teszi különböző hierarchiaverziók fenntartását, például a költségközpont hierarchia 2007-es és 2008-as verziójáét. A Power BI-ban csak a legfrissebb verzió érhető el, mivel a verziókban található információkat a nyilvános API nem teszi közzé. |
| Időfüggő hierarchiák |A Power BI az időfüggő hierarchiákat az aktuális dátum szerint értékeli ki. |
| Pénznemek átváltása |Az SAP BW támogatja a pénznem az adatkockában található árfolyamok szerinti átváltását. A nyilvános API nem teszi közzé ezt a funkciót, így az a Power BI-ban nem érhető el. |
| Rendezés iránya |Az SAP-ben megadható a jellemzők rendezési sorrendje (szöveg szerint vagy kulcs szerint). Ezt a rendezési sorrendet a Power BI nem tükrözi. Például a hónapok sorrendje megjelenhet így: „Április”, „Augusztus” és így tovább. <br/> <br/> A rendezési sorrend a Power BI-ban nem módosítható. |
| Technikai nevek |Az **Adatok lekérése** esetén a jellemzők és mértékek neve (a leírások) és a technikai nevek egyaránt megjelennek. A mezőlista csak a jellemzők és mértékek nevét (a leírásokat) tartalmazza. |
| Attribútumok |A Power BI-ban a jellemzők attribútumai nem érhetők el. |
| Végfelhasználói nyelvi beállítások |Az SAP BW-ben használt területi beállítás a kapcsolat részleteitől függ, és nem tükrözi a végfelhasználó által használt területi beállításokat. |
| Szöveges változók |Az SAP BW lehetővé teszi, hogy a változók helyőrzőket tartalmazzanak (pl.: „$ÉV$. évi adatok”), amelyeket aztán a kiválasztott érték helyettesít. Például a mező a BEx-eszközökben „2016. évi adatok” néven jelenik meg, ha a változóhoz a 2016-os év lett kiválasztva. <br/> <br/> A Power BI-ban az oszlop neve nem változik a változó értékét tükrözve, hanem „$ÉV$. évi adatok” néven jelenik meg.  Azonban az oszlopnév a Power BI-ban módosítható. |
| Ügyfélkilépési változók | A nyilvános API nem mutatja meg az ügyfélkilépési változót, így az a Power BI-ban nincs támogatva. |
| Jellemző struktúrák | Az alapul szolgáló SAP BW forrás minden Jellemző struktúrája a Power BI-ban megjelenített mértékek „robbanásához” vezet. Ha például a Sales (értékesítések) és a Costs (költségek) mérték van jelen, valamint egy olyan jellemző struktúra, amely a Budget (előirányzat) és az Actual (tényleges) elemeket tartalmazza, akkor négy mérték lesz közzétéve: Sales.Budget, Sales.Actual, Costs.Budget és Costs.Actual. |


## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a DirectQueryről, tekintse át a következő forrásanyagokat:

* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)

