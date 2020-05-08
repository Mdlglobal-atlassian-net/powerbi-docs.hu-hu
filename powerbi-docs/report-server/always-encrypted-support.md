---
title: Az Always Encrypted szolgáltatás a Power BI Jelentéskészítő kiszolgálón
description: Ez a cikk az Always Encrypted Power BI Jelentéskészítő kiszolgáló általi támogatását részletezi a Microsoft SQL Server és a Microsoft Azure SQL Database adatforrás-típus használata esetén.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710206"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Az Always Encrypted szolgáltatás a Power BI Jelentéskészítő kiszolgálón

Ez a cikk az Always Encrypted Power BI Jelentéskészítő kiszolgáló általi támogatását részletezi a Microsoft SQL Server és a Microsoft Azure SQL Database adatforrás-típus használata esetén. Az SQL Server Always Encrypted szolgáltatással kapcsolatos képességeiről az [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) című cikkben talál további információt.

## <a name="always-encrypted-user-isolation"></a>Always Encrypted felhasználó-elkülönítés

A Power BI Jelentéskészítő kiszolgáló jelenleg nem korlátozza a jelentés mindig titkosított oszlopaihoz való hozzáférést a jelentésekben ha a felhasználó hozzáfér az adott jelentéshez.  Emiatt, ha a kiszolgáló az oszlop főkulcs által hozzáférést kapott az oszloptitkosítási kulcsokhoz, a felhasználók is hozzáférnek az olyan jelentések összes oszlopához, amelyekhez hozzáféréssel rendelkeznek.

## <a name="always-encrypted-column-usage"></a>Mindig titkosított oszlopok használata

### <a name="key-storage-strategies"></a>Kulcstárolási stratégiák

|Storage  |Támogatott  |
|---------|---------|
|Windows-tanúsítványtároló | Igen |
|Azure Key Vault | Nem |
| Cryptography Next Generation (CNG) | Nem |

### <a name="certificate-storage-and-access"></a>Tanúsítványok tárolása és elérése

A tanúsítványhoz a szolgáltatásfióknak kell hozzáférnie. A tanúsítványt a helyi számítógépen, a tanúsítványtárolóban érdemes tárolni. További információ:

- [A Jelentéskészítő kiszolgáló szolgáltatásfiókjának konfigurálása](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- Az SQL Serverről szól „Oszlop-főkulcsok létrehozása és tárolása az Always Encrypted szolgáltatáshoz” című cikk [Tanúsítványok elérhetővé tétele alkalmazások és felhasználók számára](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) szakasza.

### <a name="column-encryption-strategy"></a>Oszloptitkosítási stratégia

A Power BI Jelentéskészítő kiszolgáló oszloptitkosítási stratégiája lehet *determinisztikus* vagy *véletlenszerű*. Az alábbi táblázat a használt stratégiából adódó különbségeket részletezi.

|Használat  |Determinisztikus  |Véletlenszerű  |
|---------|---------|---------|
|Változatlan formában olvasható egy lekérdezés, például SELECT utasítás eredményében. | Igen  | Igen  |
|Group by entitásként használható a lekérdezésben. | Igen | Nem |
|Összesítő mezőként használható, a COUNT és a DISTINCT kivételével. | Nem, a COUNT és a DISTINCT kivételével | Nem |
|Jelentésparaméterként használható | Igen | Nem |

További információk állnak rendelkezésére a [determinisztikus és a véletlenszerű titkosításról](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Paraméterek használata

A paraméterek használata csak a determinisztikus titkosításra vonatkozik.

**Egyértékű paraméter**.  Mindig titkosított oszlophoz használható egyértékű paraméter.

**Többértékű paraméter**. Egynél több értékkel rendelkező többértékű paraméter nem használható mindig titkosított oszlophoz.

**Egymásra épülő paraméterek**. Egymásra épülő paraméterek akkor használhatók az Always Encrypted funkcióval, ha az alábbi feltételek *mindegyike* teljesül:

- Az összes Always Encrypted-oszlop determinisztikus stratégiával van titkosítva.
- Az Always Encrypted-oszlopokhoz használt összes paraméter egyértékű.
- Minden SQL-beli összehasonlítás az Egyenlő (=) operátort használja.

## <a name="datatype-support"></a>Adattípusok támogatása

| SQL-adattípus | Mezőolvasás támogatása | Csoportosítási szempontként való használat támogatása | Támogatott összesítések (COUNT, DISTINCT, MAX, MIN, SUM stb.) | Paraméteres egyenlőségekkel végzett szűrés támogatása | Megjegyzések |
| --- | --- | --- | --- | --- | --- |
| int | Igen | Igen | COUNT, DISTINCT | Igen, egész számként |   |
| lebegőpontos | Igen | Igen | COUNT, DISTINCT | Igen, lebegőpontos számként |   |
| nvarchar | Igen | Igen | COUNT, DISTINCT | Igen, szövegként | A determinisztikus titkosításnak a karakteres oszlopok binary2 sorrendű rendezését kell használnia. További részleteket az [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) című SQL Server-cikkben találhat.  |
| varchar | Igen | Igen | COUNT, DISTINCT | Nem |   |
| tizedes tört | Igen | Igen | COUNT, DISTINCT | Nem |   |
| numerikus | Igen | Igen | COUNT, DISTINCT | Nem |   |
| datetime | Igen | Igen | COUNT, DISTINCT | Nem |   |
| datetime2 | Igen | Igen | COUNT, DISTINCT | Igen, dátum/idő típusúként | Akkor támogatott, ha az oszlop nem ezredmásodperces pontosságú (tehát nem datetime2(0)) |

## <a name="aggregation-alternatives"></a>Összesítési alternatívák

A determinisztikus Always Encrypted oszlopokon jelenleg csak olyan összesítések támogatottak, amelyek közvetlenül az Egyenlő (=) operátort használják. Az SQL Servernek ez a korlátozása az Always Encrypted-oszlopok természetéből adódik. A felhasználóknak az adatbázis helyett a jelentésben kell összesítést végezniük.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted a kapcsolati sztringben

Az Always Encrypted szolgáltatást engedélyezni kell az SQL Server-adatforrás kapcsolati sztringjében. További információk az [Always Encrypted alkalmazás-lekérdezésekben](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries) való engedélyezéséről.

## <a name="next-steps"></a>További lépések

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) az SQL Serverben és az Azure SQL Database-ben

Több kérdése van? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)

