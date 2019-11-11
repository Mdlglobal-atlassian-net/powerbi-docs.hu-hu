---
title: Jelentés szűrése lekérdezésisztring-paraméterek URL-címben való használatával
description: A jelentések szűrhetők az URL-cím lekérdezési sztringjének paramétereivel, akár egynél több mezőre is.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/23/2019
LocalizationGroup: Reports
ms.openlocfilehash: be45941e67417cbed15433405953cf728fe0aa8d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876933"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Jelentés szűrése lekérdezésisztring-paraméterek URL-címben való használatával

A Power BI szolgáltatásban megnyitott jelentések minden egyes oldalának saját egyedi URL-címe van. Az adott jelentésoldal a jelentésvászon Szűrők paneljének használatával szűrhető.  A jelentés előzetes szűréséhez az URL-címhez is hozzáadhat lekérdezésisztring-paramétereket. Tegyük fel, hogy egy jelentést meg szeretne mutatni a munkatársainak, és előre szűrni szeretné azt a számukra. A szűrés egyik módja az, hogy a jelentés alapértelmezett URL-címéhez szűrési paramétereket ad, majd a teljes új URL-címet küldi el e-mailben.

![Power BI-jelentés a szolgáltatásban](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>Lekérdezésisztring-paraméterek felhasználási módjai

Tegyük fel, hogy a Power BI Desktopban dolgozik. Más Power BI-jelentésekre mutató hivatkozásokat tartalmazó jelentést kíván létrehozni – de a más jelentésekben lévő információnak csak egy részét szeretné megjeleníteni. Megteheti, hogy először lekérdezésisztring-paraméterek használatával szűri a jelentéseket, majd menti az URL-címeket. Ez után létrehoz egy, ezeket az új jelentés-URL-címeket tartalmazó táblázatot a Desktopban.  Végül közzéteszi és megosztja a jelentést.

A lekérdezésisztring-paraméterek másik felhasználási módja speciális Power BI-megoldások létrehozásához való.  A DAX használatával olyan jelentés hozható létre, amely dinamikusan generál szűrt jelentés-URL-címet az alapján, hogy mit jelölt ki éppen az ügyfél az aktuális jelentésben. Az URL-címet választó ügyfelek csak a nekik szánt információt látják. 

## <a name="query-string-parameter-syntax-for-filtering"></a>Lekérdezésisztring-paraméterek szintaxisa szűréshez

Paraméterek használatával a jelentés egy vagy több értékre szűrhető még akkor is, ha az értékek szóközöket vagy speciális karaktereket tartalmaznak. Az alapvető szintaxis nagyon egyszerű – kezdje a jelentés URL-címével, adjon hozzá egy kérdőjelet, majd a szűrési szintaxist.

URL-cím?filter=***Tábla***/***Mező*** eq '***érték***'

![URL-cím szűrővel](media/service-url-filters/power-bi-filter-urls7b.png)

* A **Tábla** és a **Mező** nevei megkülönböztetik a kis- és nagybetűket, az **érték** viszont nem.
* A jelentésnézetben rejtett mezők is szűrhetők.

### <a name="reports-in-apps"></a>Jelentések az alkalmazásokban

Ha URL-szűrőt szeretne felvenni egy alkalmazás egyik jelentésébe, annak formázása kissé eltérő lesz. Az alkalmazáson belüli jelentések hivatkozásai lekérdezésparamétert (ctid-t) tartalmaznak, amely az URL-hez kapcsolódik. A lekérdezési paramétereket egy és jellel (&) válassza el. Tartsa meg a „? filter =” kifejezést, és helyezze át a ctId paramétert az URL-cím végére, elé pedig egy és jelet (&) tegyen. 

Íme egy példa:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=*Table*/*Field* eq '*value*&'ctid=*ctid*

### <a name="field-types"></a>Mezőtípusok

A mezőtípus lehet szám, dátum és idő vagy sztring, és a használt típusnak egyeznie kell az adathalmazban megadottal.  Egy tábla oszlopának „sztring” beállítása például nem működik, ha dátum, idő vagy numerikus értéket keres egy adathalmaz dátumként beállított oszlopában, például a Table/StringColumn eq 1 oszlopban.

* A **sztringeket** aposztrófok között kell megadni – „vezető neve”.
* A **számok** nem igényelnek különleges formázást. További információt a [Numerikus adattípusok](#numeric-data-types) című cikkben találhat.
* **Dátumok és időpontok** – Lásd a cikk [Dátum adattípusok](#date-data-types) című szakaszát. 

Ha egyelőre nem minden világos, akkor olvasson tovább, és bővebb kifejtést is találhat.  

## <a name="filter-on-a-field"></a>Szűrés egy mező alapján

Tegyük fel például, hogy a jelentés URL-címe a következő.

![URL indítása](media/service-url-filters/power-bi-filter-urls6.png)

A térkép-vizualizáción (fent) látható, hogy üzleteink vannak Észak-Karolinában.

>[!NOTE]
>Ez a példa a [Kiskereskedelmi elemzési mintán](sample-datasets.md) alapszik.
> 

Ha úgy szeretné szűrni a jelentést, hogy csak az Észak-Karolinában („NC”) található üzletek adatait jelenítse meg, akkor fűzze hozzá az URL-címhez a következőt;

?filter=Store/Territory eq 'NC'

![URL-cím szűrővel](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>Az *NC* (North Carolina, Észak-Karolina) érték a **Store** (Üzlet) tábla **Territory** (Terület) mezőjében található meg.
> 

A jelentés szűrve lett Észak-Karolinára, és a jelentés oldalán található összes vizualizáció csak Észak-Karolina adatait jeleníti meg.

![A jelentés Észak-Karolinára szűrve](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>Szűrés több mező alapján

Ha további paramétereket fűz az URL-címhez, több mező alapján is végezhet szűrést. Térjünk vissza az eredeti szűrési paraméterhez.

```
?filter=Store/Territory eq 'NC'
```

További mezők alapján úgy szűrhet, hogy az „**and**” kulcsszót és egy újabb mezőt ad meg a fentinek megfelelő formátumban. Íme egy példa.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="operators"></a>Operátorok

A Power BI az „**and**” operátoron kívül sok továbbit is támogat. Ezek az operátorok az alábbi táblázatban az általuk támogatott tartalomtípussal együtt vannak felsorolva.

|operátor  | definíció | sztring  | szám | Dátum |  Példa|
|---------|---------|---------|---------|---------|---------|
|**and**     | és |  igen      | igen |  igen|  termék/ár le 200 and ár gt 3.5 |
|**eq**     | egyenlő |  igen      | igen   |  igen       | Cím/Város eq ’Kalocsa’ |
|**ne**     | nem egyenlő |   igen      | igen  | igen        |  Cím/Város ne ’Sopron’ |
|**ge**     |  nagyobb vagy egyenlő, mint       | nem | igen |igen |  termék/ár ge 10
|**gt**     | nagyobb, mint        |nem | igen | igen  | termék/ár gt 20
|**le**     |   kisebb vagy egyenlő, mint      | nem | igen | igen  | termék/ár le 100
|**lt**     |  kisebb, mint       | nem | igen | igen |  termék/ár lt 20
|**in\*\***     |  a következők között van       | igen | igen |  igen | Diák/Életkor in (27, 29)


\*\* az **in** használatakor az **in** operátortól jobbra lévő értékek zárójelek közötti, vesszővel elválasztott listaként, vagy egy kollekciót megadó kifejezésként adhatók meg.

### <a name="numeric-data-types"></a>Numerikus adattípusok

A Power BI URL-címekben a szűrők az alábbi formátumú számokat tartalmazhatják.

|Számtípus  |Példa  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5 L vagy 5 l      |
|**double**     |   5.5 vagy 55e-1 vagy 0.55e+1 vagy 5D vagy 5d vagy 0.5e1D vagy 0.5e1d vagy 5.5D vagy 5.5d vagy 55e-1D vagy 55e-1d     |
|**decimal**     |   5 M vagy 5 m vagy 5,5 M vagy 5,5 m      |
|**float**     | 5 F vagy 5 f vagy 0,5e1 F vagy 0,5e-1 d        |

### <a name="date-data-types"></a>Dátum adattípusok

A Power BI az OData V3 és V4 **Date** és **DateTimeOffset** adattípusokat is támogatja. Odata V3 estén a dátumokat aposztrófok között kell megadni, és eléjük be kell szúrni a datetime szót. Az Odata V4 esetén nincs szükség az aposztrófokra és a datetime szóra. 
  
A dátumok az EDM formátum (2019-02-12T00:00:00) használatával vannak ábrázolva: Ha a dátum ÉÉÉÉ-HH-NN formátumban van megadva, akkor a Power BI azt ÉÉÉÉ-HH-NNT00:00:00 formátumban értelmezi. Ügyeljen arra, hogy a hónap és nap kétjegyű formátumú legyen, HH és NN.

Miért számít ez a megkülönböztetés? Tegyük fel, hogy létrehoz egy **Table/Date gt 2018-08-03** lekérdezésisztring-paramétert.  Az eredmények között lesz 2018. augusztus 3., vagy csak 2018. augusztus 4-étől kezdődnek? A Power BI a lekérdezést **Table/Date gt '2018-08-03T00:00:00'** formátumra fordítja le. Az eredményekben így minden nem nulla időösszetevővel rendelkező dátum szerepel, mert azok a **’2018-08-03T00:00:00’** dátumnál nagyobbak.

A V3 és a V4 között további különbségek is megfigyelhetők. Az OData V3 nem támogatja a dátumokat, csak a DateTime formátumot. A V3 formátum használata esetén így a teljes dátumot és időt meg kell adni. A V3 nem támogatja a „datetime'2019-05-20'” típusú adatkonstansokat. A V4 formátumban azonban elég a „2019-05-20” szöveget használnia. Íme két egyenértékű szűrőlekérdezés V3, illetve V4 formátumban:

- OData V4 formátum: filter=Table/Date gt 2019-05-20
- OData V3 formátum: filter=Table/Date gt datetime'2019-05-20T00:00:00'


## <a name="special-characters-in-url-filters"></a>Speciális karakterek URL-szűrőkben

A speciális karakterek és szóközök igényelnek némi további formázást. Ha a lekérdezés szóközöket, kötőjeleket vagy egyéb nem ASCII-karaktereket tartalmaz, a speciális karakterek előtagjaként használjon olyan *feloldókaraktert*, amely aláhúzásjellel és egy X karakterrel ( **_x**) kezdődik, majd a 4 számjegyű **Unicode**-karakter után még egy aláhúzásjelet tartalmaz. Ha a Unicode-karakter kevesebb mint négy számjegyből áll, akkor nullákkal kell kiegészítenie. Az alábbiakban néhány példa következik.

|Azonosító  |Unicode  | Kódolás a Power BI-ban  |
|---------|---------|---------|
|**Táblázat neve**     | A szóköz kódja: 0x20        |  Table_x0020_Name       |
|**Column**@**Number**     |   A @ kódja: 0x40     |  Column_x0040_Number       |
|**[Column]**     |  [ egyenlő 0x005B ] egyenlő 0x005D       |  _x005B_Column_x005D_       |
|**Column+Plus**     | A + kódja: 0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![speciális karaktereket megjelenítő táblázatvizualizáció](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![speciális karaktereket megjelenítő táblázatvizualizáció](media/service-url-filters/power-bi-special-characters2.png)

## <a name="use-dax-to-filter-on-multiple-values"></a>Szűrés több értékre a DAX használatával

A szűrés egy másik módja, ha létrehoz egy számított oszlopot, amely két mezőt egyetlen értékké fűz össze. Ezt követően már szűrhet erre az értékre.

Legyen például két mezőnk: Territory (terület) és Chain (üzletlánc). [Hozzon létre egy új számított oszlopot](desktop-tutorial-create-calculated-columns.md) (Mezőt) a Power BI Desktopban, TerritoryChain (TerületÜzletlánc) néven. Ne feledje, hogy a **Mező** neve nem tartalmazhat szóközöket. Az oszlop DAX-képlete a következő.

TerritoryChain = [Territory] & " - " & [Chain]

Tegye közzé a jelentést a Power BI szolgáltatásban, majd az URL-cím lekérdezési sztringjével szűrje azt úgy, hogy csak az Észak-Karolinában található Lindseys üzletek adatait jelenítse meg.

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Szűrt jelentésből származó csempe rögzítése

Miután lekérdezésisztring-paraméterek használatával szűrte a jelentést, abból származó vizualizációkat rögzíthet az irányítópulton.  Az irányítópulton található csempe a szűrt adatokat jeleníti meg, az irányítópult csempéjére kattintva pedig megnyílik a létrehozásához használt jelentés.  Az URL-címmel végrehajtott szűrés azonban nem lesz mentve a jelentéssel együtt. Amikor kiválasztja a csempét az irányítópulton, a jelentés szűretlen állapotban nyílik meg.  Tehát az irányítópult csempéjén megjelenített adatok nem egyeznek a jelentésben szereplő vizualizációban megjelenített adatokkal.

Ez az eltérés akkor hasznos, ha különböző eredményeket szeretne megjeleníteni: a szűrt adatokat az irányítópulton, a nem szűrt adatokat pedig a jelentésben.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

Lekérdezésisztring-paraméterek használatakor néhány szemponttal érdemes tisztában lenni.

* Az *in* használatakor az *in* operátortól jobbra lévő értékeket zárójelek közötti, vesszővel elválasztott listaként kell megadni.    
* A Power BI jelentéskészítő kiszolgálón [adhat át jelentésparamétereket](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md) úgy, hogy belefoglalja őket a jelentés URL-címébe. Ezek az URL-paraméterek nincsenek előtaggal ellátva, mert a rendszer közvetlenül átadja őket a jelentésfeldolgozó motornak.
* A lekérdezési sztringgel végzett szűrés a [Webes közzététel](service-publish-to-web.md) vagy az [Exportálás PDF-be](consumer/end-user-pdf.md) használatával együtt nem működik.
* [A SharePoint Online-ban jelentéskijelzővel történő beágyazás](service-embed-report-spo.md) nem támogatja az URL-szűrőket.
* A long adattípus maximális értéke a JavaScript korlátozásai miatt 2^53-1.
* A jelentés URL-címének szűrői legfeljebb 10 kifejezést tartalmazhatnak (10 kifejezést, AND operátorral).

## <a name="next-steps"></a>Következő lépések

[Vizualizáció rögzítése az irányítópulton](service-dashboard-pin-tile-from-report.md)  
[Regisztráljon ingyenes próbára](https://powerbi.microsoft.com/get-started/)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
