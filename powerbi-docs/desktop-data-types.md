---
title: Adattípusok a Power BI Desktopban
description: Adattípusok a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f153ea866404066ce2ada6ab509de2aa8259d6a5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54293056"
---
# <a name="data-types-in-power-bi-desktop"></a>Adattípusok a Power BI Desktopban
A cikk a Power BI Desktop és a Data Analysis Expressions (DAX) által támogatott adattípusokat ismerteti. 

A Power BI Desktop az adatok betöltésekor megkísérli a forrásoszlop adattípusát egy olyan adattípussá alakítani, amely jobban támogatja a hatékonyabb tárolást, számítást és adatvizualizációt. Például ha egy, az Excelből importált oszlop adatai között nincsenek törtszámok, a Power BI Desktop átalakítja a teljes adatoszlopot Egész szám adattípusúvá, amely jobban használható az egész számok tárolásához.

Ez azért lényeges, mert egyes DAX-függvények speciális adattípus-követelményekkel rendelkeznek. Bár sok esetben a DAX implicit módon konvertálja az adattípust, bizonyos esetekben ez mégsem történik meg.  Például, ha egy adott DAX-függvény Dátum típusú adatot vesz fel, az oszlop azonban Szöveg típusú adatokat tartalmaz, a DAX-függvény nem működik majd megfelelően.  Ezért fontos és hasznos is megfelelően megadni az oszlop adatainak típusát. Az implicit konverzióról a cikk későbbi részében lesz szó.

## <a name="determine-and-specify-a-columns-data-type"></a>Oszlop adattípusának megállapítása és megadása
A Power BI Desktopban az oszlopok adattípusát a Lekérdezésszerkesztőben, illetve az Adat- vagy Jelentésnézetben állapíthatja és adhatja meg:

**Adattípusok a Lekérdezésszerkesztőben**

![](media/desktop-data-types/pbiddatatypesinqueryeditort.png)

**Adattípusok az Adat- vagy Jelentésnézetben**

![](media/desktop-data-types/pbiddatatypesindatareportview.png)

A Lekérdezésszerkesztő Adattípus legördülő menüje tartalmaz két olyan adattípust, amelyek az Adat- és a Jelentésnézetben jelenleg nem érhetők el: Ez a **Dátum/idő/időzóna** és az **Időtartam**. Ha egy ilyen adattípusú oszlopot tölt be a modellbe, majd az Adat- vagy Jelentésnézetben tekinti meg, a Dátum/idő/időzóna típusú oszlop Dátum/idő típusúvá, az Időtartam típusú oszlop Tizedes tört típusúvá lesz konvertálva.

### <a name="number-types"></a>Számtípusok
A Power BI Desktop három számtípust támogat:

**Tizedes tört** – Egy 64 bites (nyolc bájtos), lebegőpontos számot jelöl. Ez a leggyakoribb számtípus, hiszen a számokra általában ebben a formában gondolunk.  Bár ez az adattípus tört értékű számok kezelésére lett kitalálva, egész számok kezelésére is alkalmas.  A Tizedes tört típus által kezelt értékek: negatív értékek -1,79E +308 és -2,23E -308 között, 0, pozitív értékek 2,23E -308 és 1,79E +308 között. Például a 34, a 34,01 és a 34,000367063 mind érvényes tizedes tört szám. A Tizedes tört típus által megjeleníthető legnagyobb érték 15 számjegy hosszúságú.  A tizedeselválasztó bármelyik pozícióban lehet. A Tizedes tört típus megfelel annak, ahogy az Excel tárolja a számokat.

**Fixpontos tizedes tört** – A tizedeselválasztó rögzített helyen található. A tizedeselválasztótól jobbra minden esetben négy számjegy található, és a szám legfeljebb 19 helyiértéket tartalmazhat.  A legnagyobb érték 922 337 203 685 477,5807 lehet (pozitív vagy negatív).  A Fixpontos tizedes tört típus olyan esetekben hasznos, amikor a kerekítés hibákhoz vezethet.  Ha sok olyan számmal dolgozik, amelyeknek kicsi a tört része, ezek összeadódhatnak, és az eredmény hibás lehet.  Mivel a tizedesjeltől több mint négy pozícióval jobbra található értékek le vannak vágva, a Fixpontos tizedes tört segít elkerülni ezeket a hibákat.   Amennyiben jártas az SQL Server használatában, ez az adattípus megegyezik az SQL Server Tizedes tört (19,4) típusával vagy a Power Pivot Pénznemadat típusával. 

**Egész szám** – Egy 64 bites (nyolc bájtos), egész számot jelöl. Mivel egész számról van szó, nincsenek számjegyek a tizedeselválasztótól jobbra. Legfeljebb 19 számjegyet tartalmazhat, és pozitív vagy negatív egész számokat jelölhet -9 223 372 036 854 775 808 (-2^63) és 9 223 372 036 854 775 807 (2^63-1) között.  A különféle szám adattípusok közül ez a típus jelölheti a lehető legnagyobb értékű számot.  Ahogy a Fixpontos tizedes tört szám típus, az Egész szám típus is hasznos lehet olyan esetekben, ahol felügyelet alatt szeretné tartani a kerekítést. 

> [!NOTE]
>  A Power BI Desktop-adatmodell 64 bites egész számokat támogat, de a vizualizációk által biztonságosan kifejezhető legnagyobb szám 9 007 199 254 740 991 (2^53-1) a JavaScript-korlátozások miatt. Ha az adatmodellben ennél nagyobb számokkal dolgozik, akkor számításokkal csökkentheti azokat, mielőtt hozzáadná egy vizualizációhoz 
> 
>

### <a name="datetime-types"></a>Dátum/idő típusok
A Power BI Desktop öt Dátum/idő adattípust támogat a Lekérdezésnézetben, és hármat a Jelentésnézetben és a modellben.   A modellbe való betöltéskor a Dátum/idő/időzóna és az Időtartam típus konvertálva lesz.

**Dátum/idő** – Egy dátum és egy idő értéket jelöl egyszerre.  A háttérben a Dátum/idő érték Tizedes tört típusúként van tárolva.  Így lényegében átalakíthatja ez értékeket az egyik típusból a másikba.   A dátum idő része 1/300 másodperc (3,33 ezredmásodperc) egész többszöröseiként van tárolva.  Az 1900. és 9999. közötti dátumok használata támogatott.

**Dátum** – Csak egy dátumot jelöl (időmegjelölés nélkül).  A modellbe való konvertáláskor a Dátum típus ugyanúgy viselkedik, mint a Dátum/idő típus, ahol a törtrész nulla.

**Idő** – Csak egy időpontot jelöl (dátummegjelölés nélkül).  A modellbe való konvertáláskor az Idő típus ugyanúgy viselkedik, mint a Dátum/idő típus, ahol az egész rész értéke nulla.

**Dátum/idő/időzóna** – Egy UTC-ben megadott dátum/idő értéket jelöl.  Jelenleg ez a típus Dátum/idő típussá lesz konvertálva a modellbe való betöltéskor.

**Időtartam** – Egy bizonyos hosszúságú időszeletet jelöl. Ez a típus Tizedes tört típusúvá lesz konvertálva a modellbe való betöltéskor.  Tizedes tört típusként megfelelő eredményt ad, ha hozzáadják vagy kivonják a Dátum/idő mezőkből.  Tizedes tört típusként könnyen használható nagyságrendet jelző vizualizációkban.

### <a name="text-type"></a>Szöveg típus
**Szöveg** – Egy Unicode kódolású adatsztring. Ez lehet szöveg formátumban jelölt sztring, szám vagy dátum. A sztring maximális hossza 268 435 456 Unicode-karakter (256 mega karakter) vagy 536 870 912 bájt.

### <a name="truefalse-type"></a>Igaz/hamis típus
**Igaz/hamis** – Egy logikai érték, amely vagy Igaz vagy Hamis.

### <a name="blanksnulls-type"></a>Üres/null érték típus
**Üres** – DAX-adattípus, amely az SQL nullértékeit jelöli és helyettesíti. Üres értékeket a [BLANK](http://msdn.microsoft.com/library/ee634820.aspx) függvénnyel hozhat létre, a meglévőket pedig az [ISBLANK](https://msdn.microsoft.com/library/ee634204.aspx) logikai függvénnyel ellenőrizheti.

### <a name="table-data-type"></a>Tábla adattípus
A DAX a tábla adattípust sok függvényben használja, például összesítésekben és időintelligencia-számításokban. Egyes függvényekben táblára mutató hivatkozást kell megadni, más függvények pedig táblákat adnak vissza, amelyek más függvényeknek átadhatók. Egyes táblát váró függvényeknek átadhatók függvényt visszaadó kifejezések, míg más függvényeknek csak alaptáblák adhatók át. Az egyes függvények követelményeivel kapcsolatos információkért lásd a [DAX-függvények referencia-útmutatóját](https://msdn.microsoft.com/library/ee634396.aspx).

## <a name="implicit-and-explicit-data-type-conversion-in-dax-formulas"></a>Implicit és explicit adattípus-konverzió a DAX-képletekben
Mindegyik DAX-függvény saját követelményekkel rendelkezik a bemeneti és kimeneti adatok típusát illetően. Például egyes függvények egész számot várnak egyes argumentumokra, dátumokat másokra, más függvények pedig szövegeket vagy táblákat várnak.

Ha az argumentumként megadott oszlopban lévő adatok típusa nem kompatibilis a függvény adattípus-követelményével, a DAX sok esetben hibát jelez. Azonban, ha csak lehetséges, a DAX megkísérli implicit módon konvertálni az adatokat a szükséges adattípusra. Például:

* Beírhat egy dátumot szövegként, és a DAX megkísérli kielemezni a sztringet, és ráhúzni valamelyik windowsos dátum- és időformátumra.
* Az IGAZ + 1 képlet eredménye 2 lesz, mivel az IGAZ értéket a rendszer implicit módon az 1 értékre konvertálja, majd elvégzi az 1+1 műveletet.
* Ha két külön oszlopban ad meg értékeket, és az egyik történetesen szöveges értékeket tartalmaz ("12"), míg a másik számokat (12), a DAX implicit módon számmá konvertálja a sztringet, majd elvégzi az összeadást, és egy numerikus értéket ad vissza. A következő kifejezés értéke tehát 44 lesz: = "22" + 22.
* Ha két számot próbál összefűzni, az Excel sztringként jeleníti meg, majd összefűzi azokat. A következő kifejezés értéke tehát "1234" lesz: = 12 & 34.

### <a name="table-of-implicit-data-conversions"></a>Az implicit adatkonverziókat bemutató táblázat
A végrehajtott konverzió típusát az operátor határozza meg, amely először átalakítja a szükséges értékeket, mielőtt elvégezné a kért műveleteket. Az alábbi táblázatok sorolják fel az operátorokat, és azt mutatják, hogy a vízszintesen jelölt adattípusok mivé lesznek konvertálva, ha az operátor a függőlegesen jelölt adattípusokkal köti össze őket.

> [!NOTE]
>  A táblázatok a Szöveg adattípusait nem tartalmazzák. A szöveges formátumban megadott számok esetében a Power BI bizonyos esetekben megpróbálja meghatározni a Szám típust, és számként megjeleníteni az értéket.
> 
> 

**Összeadás (+)**

| Operátor (+) | EGÉSZ SZÁM | PÉNZNEM | VALÓS SZÁM | Dátum/idő |
| --- | --- | --- | --- | --- |
| EGÉSZ SZÁM |EGÉSZ SZÁM |PÉNZNEM |VALÓS SZÁM |Dátum/idő |
| PÉNZNEM |PÉNZNEM |PÉNZNEM |VALÓS SZÁM |Dátum/idő |
| VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |Dátum/idő |
| Dátum/idő |Dátum/idő |Dátum/idő |Dátum/idő |Dátum/idő |

Például ha egy Valós számot egy Pénznem adattal együtt alkalmaz egy összeadásban, a rendszer mindkét adatot konvertálja VALÓS SZÁMMÁ, és eredményként is VALÓS SZÁMOT ad.

**Kivonás (-)**

A következő táblázatban a sorok a kisebbítendőt (bal oldal), az oszlopok a kivonandót (felül) jelzik.

| Operátor (-) | EGÉSZ SZÁM | PÉNZNEM | VALÓS SZÁM | Dátum/idő |
| --- | --- | --- | --- | --- |
| EGÉSZ SZÁM |EGÉSZ SZÁM |PÉNZNEM |VALÓS SZÁM |VALÓS SZÁM |
| PÉNZNEM |PÉNZNEM |PÉNZNEM |VALÓS SZÁM |VALÓS SZÁM |
| VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |
| Dátum/idő |Dátum/idő |Dátum/idő |Dátum/idő |Dátum/idő |

Például ha egy Dátumot bármely más adattípussal együtt használ egy kivonási műveletben, a rendszer mindkét értéket Dátummá alakítja, és az értéket szintén Dátumként adja vissza.

> [!NOTE]
>    Az adatmodellek az egyoperandusú operátort (-, negatív) is támogatják, ez az operátor azonban nem módosítja az operandus adattípusát.
> 
> 

**Szorzás (*)**

| Operátor (\*) | EGÉSZ SZÁM | PÉNZNEM | VALÓS SZÁM | Dátum/idő |
| --- | --- | --- | --- | --- |
| EGÉSZ SZÁM |EGÉSZ SZÁM |PÉNZNEM |VALÓS SZÁM |EGÉSZ SZÁM |
| PÉNZNEM |PÉNZNEM |VALÓS SZÁM |PÉNZNEM |PÉNZNEM |
| VALÓS SZÁM |VALÓS SZÁM |PÉNZNEM |VALÓS SZÁM |VALÓS SZÁM |

Például ha egy Egész számot egy Valós számmal ötvöz egy szorzási műveletben, a rendszer mindkét számot Valós számmá alakítja, és az értéket szintén VALÓS SZÁMKÉNT adja vissza.

**Osztás (/)**

A következő táblázatban a sorok az osztandót, az oszlopok az osztót jelzik.

| Operátor (/) (sor/oszlop) | EGÉSZ SZÁM | PÉNZNEM | VALÓS SZÁM | Dátum/idő |
| --- | --- | --- | --- | --- |
| EGÉSZ SZÁM |VALÓS SZÁM |PÉNZNEM |VALÓS SZÁM |VALÓS SZÁM |
| PÉNZNEM |PÉNZNEM |VALÓS SZÁM |PÉNZNEM |VALÓS SZÁM |
| VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |
| Dátum/idő |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |

Például ha egy Egész számot egy Pénznem típusú értékkel ötvöz egy osztási műveletben, a rendszer mindkét értéket Valós számmá alakítja, és az értéket szintén Valós számként adja vissza.

### <a name="comparison-operators"></a>Összehasonlító operátorok
Az összehasonlítási kifejezésekben a logikai értékek nagyobbnak számítanak a sztringértékeknél, ezek pedig nagyobbak a numerikus vagy Dátum/idő értékeknél, míg ez utóbbi két kategória egyenrangúnak számít. A rendszer a logikai és sztringértékeket implicit módon nem konvertálja. Az ÜRES vagy az üres értékek 0/""/hamis értékké lesznek konvertálva, az összehasonlított érték adattípusának megfelelően.

Ezt a viselkedést az alábbi DAX-függvények jól példázzák:

Az =IF(FALSE()\>"true";"A kifejezés igaz";"A kifejezés hamis") kifejezés „A kifejezés igaz” értéket adja vissza.

Az =IF("12"\>12;"A kifejezés igaz";"A kifejezés hamis") kifejezés „A kifejezés igaz” értéket adja vissza

Az =IF("12"=12;"A kifejezés igaz";"A kifejezés hamis") kifejezés „A kifejezés hamis” értéket adja vissza.

A numerikus és a Dátum/idő típus esetén a konverzió implicit módon történik a következő táblázatban foglaltaknak megfelelően:

| Összehasonlító operátor | EGÉSZ SZÁM | PÉNZNEM | VALÓS SZÁM | Dátum/idő |
| --- | --- | --- | --- | --- |
| EGÉSZ SZÁM |EGÉSZ SZÁM |PÉNZNEM |VALÓS SZÁM |VALÓS SZÁM |
| PÉNZNEM |PÉNZNEM |PÉNZNEM |VALÓS SZÁM |VALÓS SZÁM |
| VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |
| Dátum/idő |VALÓS SZÁM |VALÓS SZÁM |VALÓS SZÁM |Dátum/idő |

### <a name="handling-blanks-empty-strings-and-zero-values"></a>Üres értékek, üres sztringek és nullértékek kezelése
A DAX nyelvben a nullértékeket, az üres értékeket, az üres cellákat és a hiányzó értékeket ugyanaz az új ÜRES értéktípus jelöli. Üres értékeket a BLANK függvénnyel is létrehozhat, a meglévőket pedig az ISBLANK függvénnyel ellenőrizheti.

Az üres értékek viselkedését a különféle műveletekben, például összeadásokban és összefűzésekben az egyes függvények határozzák meg. Az alábbi táblázat az üres értékek a DAX- és a Microsoft Excel-függvényekben való viselkedésének különbségeit foglalja össze:

| Kifejezés | DAX | Excel |
| --- | --- | --- |
| ÜRES + ÜRES |ÜRES |0 (nulla) |
| ÜRES + 5 |5 |5 |
| ÜRES * 5 |ÜRES |0 (nulla) |
| 5/ÜRES |Végtelen |Hiba |
| 0/ÜRES |NaN |Hiba |
| ÜRES/ÜRES |ÜRES |Hiba |
| HAMIS VAGY ÜRES |HAMIS |HAMIS |
| HAMIS ÉS ÜRES |HAMIS |HAMIS |
| IGAZ VAGY ÜRES |IGAZ |IGAZ |
| IGAZ ÉS ÜRES |HAMIS |IGAZ |
| ÜRES VAGY ÜRES |ÜRES |Hiba |
| ÜRES ÉS ÜRES |ÜRES |Hiba |

