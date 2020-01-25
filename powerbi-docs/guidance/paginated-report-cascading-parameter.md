---
title: Egymásra épülő paraméterek használata lapszámozott jelentésekben
description: Útmutató az egymásra épülő paraméterekkel készült lapszámozott jelentésekhez.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 2a8dca43077fe12e4903585e3926cc67fe864136
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76162411"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Egymásra épülő paraméterek használata lapszámozott jelentésekben

Ez a cikk a [lapszámozott](../paginated-reports-report-builder-power-bi.md) Power BI-jelentéseket megtervező jelentéskészítők számára készült. Egymásra épülő paraméterek tervezéséhez nyújt forgatókönyveket. Az egymásra épülő paraméterek függőségekkel rendelkező jelentésparaméterek. Amikor egy jelentésfelhasználó kiválaszt egy paraméterértéket (vagy -értékeket), azzal elérhető értékeket állíthat be egy másik paraméterhez.

> [!NOTE]
> A cikk nem foglalkozik az egymásra épülő paraméterek bemutatásával és ezek konfigurálásával. Ha nem ismeri jól az egymásra épülő paramétereket, először olvassa el az [Egymásra épülő paraméterek hozzáadása egy jelentéshez (Jelentéskészítő és SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs) című cikket.

## <a name="design-scenarios"></a>Tervezési forgatókönyvek

Az egymásra épülő paraméterekhez két tervezési forgatókönyv tartozik. Ezek a következőkhöz használhatók hatékonyan:

- Elemek _nagyméretű készleteinek_ szűrése
- _Releváns_ elemek megjelenítése

### <a name="example-database"></a>Példaadatbázis

A cikkben bemutatott példák egy Azure SQL Database-adatbázison alapulnak. Az adatbázis értékesítési műveleteket rögzít, és különböző táblázatokat tartalmaz, amelyek viszonteladókat, termékeket és értékesítési rendeléseket foglalnak magukba.

A **Reseller** (Viszonteladó) tábla viszonteladónként egy rekordot tartalmaz, összesen több ezret. A **Reseller** tábla a következő oszlopokat tartalmazza:

- ResellerCode (egész szám)
- ResellerName
- Ország, régió
- State-Province
- Település
- Irányítószám

Van egy **Sales** nevű tábla is. Ez értékesítési megrendelések rekordjait tárolja, és külső kulcsos kapcsolata van a **Reseller** táblával a **ResellerCode** oszlopban.

### <a name="example-requirement"></a>Példakövetelmény

Az egyik követelmény a viszonteladói profil jelentésének kidolgozása. A jelentést úgy kell megtervezni, hogy egyetlen viszonteladó adatait jelenítse meg. Nem célszerű, hogy a jelentés felhasználója adja meg a viszonteladói kódot, mivel ők ritkán jegyzik meg ezeket.

## <a name="filter-large-sets-of-items"></a>Nagyméretű készletek szűrése

Tekintsünk meg három példát, amellyel elérhető elemek (például viszonteladók) nagyméretű készleteit korlátozhatja. Ezek a következők:

- [Szűrés kapcsolódó oszlopok alapján](#filter-by-related-columns)
- [Szűrés csoportosítási oszlop alapján](#filter-by-a-grouping-column)
- [Szűrés keresési minta alapján](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Szűrés kapcsolódó oszlopok alapján

Ebben a példában a jelentésfelhasználó öt jelentésparaméterrel dolgozik. A country-region (ország/régió), a state-province (állam/tartomány), city (város) és a postal code (irányítószám) paramétert kell kiválasztania. Az utolsó paraméter felsorolja az adott földrajzi helyen található viszonteladókat.

![A képen öt jelentésparaméter látható: Country-region, State-province, City, Postal Code, és Reseller. Az első négy érték van beállítva, a Reseller lista pedig csak négy elemre van szűrve.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Így állíthat be egymásra épülő paramétereket:

1. Hozza létre a megfelelő sorrendben az öt jelentésparamétert.
2. Az alábbi lekérdezési utasítással hozza létre a **CountryRegion** adatkészletet, amely a country-region értékeket kéri le:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Az alábbi lekérdezési utasítással hozza létre a **StateProvince** adatkészletet, amely a kiválasztott country-region state-province értékeit kéri le:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Az alábbi lekérdezési utasítással hozza létre a **City** adatkészletet, amely a kiválasztott country-region és state-province city értékeit kéri le:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Használja ezt a mintát a **PostalCode** adatkészlet létrehozásához is.
6. Az alábbi lekérdezési utasítással hozza létre a **Reseller** adatkészletet, amely lekéri a kiválasztott földrajzi értékek összes viszonteladóját:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Az elsőt kivéve minden adatkészlethez képezze le a lekérdezési paramétereket a megfelelő jelentésparaméterekhez.

> [!NOTE]
> A példákban látható összes lekérdezési paraméter (amely előtt a @ jel található) beágyazható SELECT utasításokba, vagy továbbküldhető tárolt eljárásokhoz.
>
> A tárolt eljárások általában jobb tervezési módszerként szolgálnak. Ez azért van, mert a lekérdezési terveik gyorsítótárazva vannak a gyorsabb végrehajtás érdekében, Ön így kifinomultabb logikát alkalmazhat, amikor szüksége van rá. Ezek azonban jelenleg nem támogatottak átjárók relációs adatforrásaihoz, azaz az SQL Serverhez, az Oracle-höz és a Teradatához.
>
> Végül pedig minden győződjön meg arról, hogy léteznek megfelelő indexek az elegendő mértékű adatlekérés támogatásához. Ellenkező esetben a jelentés paramétereinek feltöltése lassú lehet, az adatbázis pedig túlterheltté válhat. További információ az SQL Server indexeléséről: [SQL Server indexelési architektúra és tervezési útmutató](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017).

### <a name="filter-by-a-grouping-column"></a>Szűrés csoportosítási oszlop alapján

Ebben a példában a jelentésfelhasználó egy jelentésparaméterrel választja ki a viszonteladó első betűjét. A második paraméter ezután listázza azon viszonteladókat, amelyek neve a választott betűvel kezdődik.

![A képen két jelentésparaméter látható: Group (Csoport) és Reseller. Az első paraméter értéke az A betűre van állítva, a Reseller lista pedig az ezzel a betűvel kezdődő számos elemre van szűrve.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Így állíthat be egymásra épülő paramétereket:

1. Hozza létre a **ReportGroup** és a **Reseller** jelentésparamétereket a megfelelő sorrendben rendezve.
2. Az alábbi lekérdezési utasítással hozza létre a **ReportGroup** adatkészletet az összes viszonteladó által használt első betű lekéréséhez:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Az alábbi lekérdezési utasítással hozza létre a **Reseller** adatkészletet a kiválasztott betűvel kezdődő összes viszonteladó lekéréséhez:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Képezze le a **Reseller** adatkészlet lekérdezésparaméterét a megfelelő jelentésparaméterre.

Hatékonyabb módszer a csoportosítási oszlop a **Reseller** táblához való hozzáadása. Megőrizve és a megfelelő indexekkel ellátva ez a legjobb eredmény szolgáltatja. További információ: [Számított oszlopok megadása egy oszlopban](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Ez a technika még ennél is nagyobb potenciállal rendelkezik. Tekintse meg a következő szkriptet, amely egy új csoportosítási oszlopot vesz fel a viszonteladók _előre definiált betűszalagokkal_ való szűréséhez. Emellett létrehoz egy indexet, amely hatékonyan lekéri a jelentésparaméterekhez szükséges adatokat.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Szűrés keresési minta alapján

Ebben a példában a jelentésfelhasználó egy jelentésparaméterrel ad meg egy keresési mintát. A második paraméter ezután listázza azon viszonteladókat, amelyek neve tartalmazza a mintát.

![A képen két jelentésparaméter látható: Search (Keresés) és Reseller. Az első paraméter értéke a „red” szövegre van állítva, a Reseller lista pedig az ezt a szöveget tartalmazó számos elemre van szűrve.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Így állíthat be egymásra épülő paramétereket:

1. Hozza létre a **Search** és a **Reseller** jelentésparamétereket a megfelelő sorrendben rendezve.
2. Az alábbi lekérdezési utasítással hozza létre a **Reseller** adatkészletet a keresési szöveget tartalmazó összes viszonteladó lekéréséhez:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Képezze le a **Reseller** adatkészlet lekérdezésparaméterét a megfelelő jelentésparaméterre.

> [!TIP]
> A terv továbbfejlesztésével részletesebb vezérlést adhat a jelentésfelhasználóknak. Így ők saját mintaegyezési értéket adhatnak meg. A „red%” keresési érték például azon viszonteladókra szűr, amelyek neve a „red” karakterekkel _kezdődik_.
>
> További információ: [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

Az alábbi módon engedélyezheti a jelentés felhasználóinak, hogy saját mintát definiáljanak.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Számos felhasználó, aki kevésbé jártas az adatbázisokban, nem ismeri a százalékjel (%) helyettesítőkaraktert. Azonban a csillag (*) karaktert igen. A WHERE záradék módosításával használhatják ezt a karaktert is.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Releváns elemek megjelenítése

Ebben a forgatókönyvben tényadatokkal korlátozhatja az elérhető értékeket. A jelentés felhasználói rögzített tevékenységekkel rendelkező elemek közül választhatnak.

Ebben a példában a jelentésfelhasználó három jelentésparaméterrel dolgozik. Az első kettő az értékesítési rendelések dátumainak tartományát adja meg. A harmadik paraméter ezután felsorolja azokat a viszonteladókat, amelyekhez az adott időszakban létrejöttek megrendelések.

![A képen három jelentésparaméter látható: Start Order Date (Rendelési dátum kezdete), End Order Date (Rendelési dátum vége), és Reseller. A két dátumparaméter 2020. januárra van beállítva, a Reseller lista pedig azon számos elemre van szűrve, amelyek a hónapban megrendeléseket végzett viszonteladókat képviselik.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Így állíthat be egymásra épülő paramétereket:

1. Hozza létre az **OrderDateStart**, az **OrderDateEnd** és a **Reseller** jelentésparamétereket a megfelelő sorrendben rendezve.
2. Az alábbi lekérdezési utasítással hozza létre a **Reseller** adatkészletet a dátumtartományban rendeléseket létrehozó összes viszonteladó lekéréséhez:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Javaslatok

Amikor csak lehetséges, a jelentéseket javasolt egymásra épülő paraméterekkel megtervezni. Ezek a paraméterek:

- Intuitív és segítőkész élményt nyújtanak a jelentésfelhasználóknak
- Hatékonyak, mivel az elérhető értékekből kisebb készleteket eredményeznek

A következő lépésekkel optimalizálja az adatforrásokat:

- Tárolt eljárások használata minden lehetséges esetben
- Megfelelő indexek hozzáadása a hatékony adatlekérés érdekében
- Oszlopértékek (és sorok) materializálása a költséges lekérdezésbeli értékelések elkerülése érdekében

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Jelentésparaméterek a Power BI Jelentéskészítőben](../report-builder-parameters.md)
- [Egymásra épülő paraméterek hozzáadása egy jelentéshez (Jelentéskészítő és SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com)
