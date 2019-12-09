---
title: Nagyméretű modellek a Power BI Premiumban (előzetes verzió)
description: A nagyméretű modellek funkciója lehetővé teszi, hogy az adathalmazok mérete meghaladja a 10 GB-ot a Power BI Premiumban.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/29/2019
LocalizationGroup: Premium
ms.openlocfilehash: 934f045e2546893c48211729402a773b4bbe2aa0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696761"
---
# <a name="large-models-in-power-bi-premium-preview"></a>Nagyméretű modellek a Power BI Premiumban (előzetes verzió)

A Power BI-adathalmazokban az adatok nagy mértékben tömörített és a memóriában gyorsítótárazott állapotban tárolhatók a lekérdezések optimális teljesítménye érdekében. Így a felhasználók gyorsabban tudnak dolgozni a nagyméretű adathalmazokon. A nagyméretű modellek funkciója lehetővé teszi, hogy az adathalmazok mérete meghaladja a 10 GB-ot a Power BI Premiumban. Az adathalmazok méretét csak a Power BI Premium kapacitásmérete korlátozza. Ez hasonló ahhoz, ahogy a modellméretek korlátozása érvényesül az Azure Analysis Servicesben. A Power BI Premium kapacitásméreteivel kapcsolatos további információkat a Kapacitás csomópontok alatt talál. A nagyméretű modellek beállíthatók az összes prémium P és beágyazott A termékváltozathoz, de csak az [új munkaterületeken](service-create-the-new-workspaces.md) működnek.

A nagyméretű modellek nem befolyásolják a feltöltési PBIX-méretet, amely továbbra is 10 GB-ra van korlátozva. Ehelyett az adathalmazok mérete frissítéskor nőhet 10 GB-nál nagyobbra. Az adathalmazok a növekményes frissítéssel konfigurálhatók úgy, hogy 10 GB-nál nagyobbra nőjenek.

## <a name="enable-large-models"></a>A nagyméretű modellek engedélyezése

Egy 10 GB-nál nagyobb adathalmaz létrehozásához kövesse az alábbi lépéseket:

1. Hozzon létre egy adathalmazt a Power BI-ban, és konfiguráljon [növekményes frissítést](service-premium-incremental-refresh.md).

1. Tegye közzé az adathalmazt a Power BI Premium szolgáltatásban.

1. Engedélyezze az adathalmazban a nagyméretű modelleket az alábbi PowerShell-parancsmagok futtatásával. A parancsmagok miatt a Power BI az adathalmazt az Azure Premium Files szolgáltatásban tárolja, és nem érvényesíti a 10 GB-os méretkorlátot.

1. Kezdeményezzen egy frissítést az előzményadatok betöltéséhez a növekményes frissítési szabályzat alapján. Az első frissítés során hosszabb ideig is eltarthat az előzmények betöltése. A későbbi frissítések várhatóan már gyorsabbak lesznek, mivel növekményesek.

### <a name="powershell-cmdlets"></a>PowerShell-parancsmagok

A nagyméretű modellek jelenlegi verziójában az adathalmaz Premium Filesban való tárolása PowerShell-parancsmagokkal engedélyezhető. A PowerShell-parancsmagok futtatásához kapacitás-rendszergazdai és munkaterület-rendszergazdai jogosultságok szükségesek.

1. Keresse meg az adathalmaz azonosítóját (GUID). A GUID a munkaterület **Adathalmazok** lapján, az adathalmaz-beállítások alatt, az URL-címben található.

    ![Adathalmaz GUID-je](media/service-premium-large-models/dataset-guid.png)

1. Egy PowerShell-rendszergazdai parancssorból telepítse a [MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/) modult.

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. Futtassa a következő parancsmagokat a bejelentkezéshez és az adathalmaz tárolási módjának ellenőrzéséhez.

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    A következő választ kell kapnia. A tárolási mód az ABF (Analysis Services biztonsági mentési fájl), ami az alapértelmezett mód.

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. Futtassa a következő parancsmagokat a Premium Filesban való tárolás beállításához és ellenőrzéséhez. Az átállás a Premium Files használatára eltarthat néhány másodpercig.

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    A következő választ kell kapnia. Az adathalaz tárolási helye mostantól a Premium Files.

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

Az adathalmaz Premium Filesra (vagy onnan) való konvertálásának állapotát a [Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus) parancsmaggal ellenőrizheti.

## <a name="dataset-eviction"></a>Adathalmazok kizárása

A Power BI dinamikus memóriakezelést használ, hogy az inaktív adathalmazokat kizárja a memóriából. Erre azért van szükség, hogy más adathalmazok is betölthetők legyenek a felhasználói lekérdezések megválaszolása érdekében. A dinamikus memóriakezelés lehetővé teszi, hogy az adathalmazok összesített mérete jelentősen nagyobb legyen, mint a kapacitásban rendelkezésre álló memória mennyisége, de az egyes adathalmazoknak külön-külön mindenképpen be kell férniük a memóriába. További információ a dinamikus memóriakezelésről: [A kapacitások működése](service-premium-what-is.md#how-capacities-function).

Érdemes átgondolni, milyen hatással jár a nagyméretű modellek kizárása. A viszonylag gyors adathalmaz-betöltési idők ellenére a felhasználók továbbra is észrevehető késést tapasztalhatnak, ha várniuk kell a kizárt adathalmazok újbóli betöltésére. Ezért jelen formájukban a nagyméretű modellek használata elsősorban az olyan kapacitások esetében ajánlott, amelyeket dedikáltan vállalati BI-követelményekhez használnak, nem pedig önkiszolgáló BI-követelményekkel vegyesen. A vállalati BI-követelményekhez dedikált kapacitások ritkábban váltanak ki kizárást, így ritkábban kell újra betölteni az adathalmazokat. Az önkiszolgáló BI-kapacitásokban azonban számos kisebb adathalmaz lehet, amelyeket gyakran kell a memóriába betölteni, majd onnan kizárni.

## <a name="checking-dataset-size"></a>Adathalmaz méretének ellenőrzése

Az előzményadatok betöltése után az [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) segítségével az [XMLA-végponton](service-premium-connect-tools.md) keresztül ellenőrizhető az adathalmaz becsült mérete a modell tulajdonságainak ablakában.

![Adathalmaz becsült mérete](media/service-premium-large-models/estimated-dataset-size.png)

Az adathalmaz mérete a következő DMV-lekérdezésekkel is ellenőrizhető az SSMS-ből. Adja össze a kimenet DICTIONARY\_SIZE és USED\_SIZE oszlopainak értékeit, hogy megkapja az adathalmaz méretét bájtban.

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="current-feature-restrictions"></a>A funkció jelenlegi korlátozásai

Vegye figyelembe az alábbi korlátozásokat a nagyméretű modellek használatakor:

- **Bring Your Own Key (BYOK, saját kulcsos) titkosítás**: A Premium Filesban tárolható adathalmazoknál nincs [BYOK](service-encryption-byok.md)-titkosítás.
- **Multi-Geo támogatás**: A Premium Filesban tárolt adathalmazok nem használhatók olyan kapacitások esetében, amelyeknél a [Multi-Geo](service-admin-premium-multi-geo.md) is engedélyezve van.

- **Letöltés Power BI Desktopba**: A Premium Filesban tárolt adathalmazokat nem lehet [.pbix-fájlként letölteni](service-export-to-pbix.md).
- **Támogatott régiók**: A nagyméretű modellek a következő régiókban támogatottak:
  - Kelet-Ausztrália
  - Délkelet-Ausztrália
  - USA középső régiója
  - Kelet-Ázsia
  - USA keleti régiója
  - USA 2. keleti régiója
  - Kelet-Japán
  - Nyugat-Japán
  - Korea középső régiója
  - Korea déli régiója
  - USA északi középső régiója
  - Észak-Európa
  - USA déli középső régiója
  - Délkelet-Ázsia
  - Egyesült Királyság déli régiója
  - Egyesült Királyság nyugati régiója
  - Nyugat-Európa
  - USA nyugati régiója
  - USA 2. nyugati régiója