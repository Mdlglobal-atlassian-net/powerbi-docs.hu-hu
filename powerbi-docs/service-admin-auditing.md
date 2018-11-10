---
title: Naplózás használata a cégnél
description: Megtudhatja, hogyan használhatja a Power BI naplózási funkcióját a végrehajtott műveletek figyelésére és vizsgálatára. Ehhez a biztonsági és megfelelőségi központot vagy a PowerShellt használhatja.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 294fb3a0142908ce0ab068e075ce39f950a0b124
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973350"
---
# <a name="using-auditing-within-your-organization"></a>Naplózás használata a cégnél

Ha tisztában van azzal, hogy a Power BI-bérlőn ki, milyen műveletet és mely elemeken végez el, sokat segíthet a munkahelyének a követelményeknek (például a jogszabályi követelményeknek és a rekordkezelésnek) való megfelelésben. A Power BI naplózási funkcióját a felhasználók által végzett műveletek, például a „Jelentés megtekintése” vagy az „Irányítópult megtekintése” naplózására használhatja. Nem használhatja a naplózást engedélyek naplózására.

A naplózással kapcsolatos munkát az Office 365 Biztonsági és megfelelőségi központjában, vagy a PowerShell használatával végezheti el. Ez a cikk mindkettőt ismerteti. A naplózási adatokat dátumtartomány, felhasználó, irányítópult, jelentés, adatkészlet és tevékenységtípus szerint szűrheti. A tevékenységeket le is töltheti egy CSV-fájlban, és offline elemezheti.

## <a name="requirements"></a>Követelmények

Az auditnaplók eléréséhez az alábbi követelményeknek kell megfelelnie:

- Az Office 365 Biztonsági és megfelelőségi központ naplózási szakaszának eléréséhez Exchange Online-licenccel kell rendelkeznie (melyet a Office 365 nagyvállalati E3 és E5 csomagra való előfizetések tartalmaznak).

- Globális rendszergazdának kell lennie, vagy pedig olyan Exchange-rendszergazdai szerepkörrel kell rendelkeznie, mely hozzáférést biztosít az auditnaplóhoz. Az Exchange-rendszergazdai szerepkörök az Exchange Felügyeleti központban szabályozhatók. További információ: [Az Exchange Online engedélyei](/exchange/permissions-exo/permissions-exo/).

- Ha rendelkezik hozzáféréssel az auditnaplóhoz, de nem globális rendszergazda vagy a Power BI szolgáltatás rendszergazdája, nem lesz hozzáférése a Power BI felügyeleti portáljához. Ebben az esetben az [Office 365 Biztonsági és megfelelőségi központra](https://sip.protection.office.com/#/unifiedauditlog) mutató közvetlen hivatkozást kell beszereznie.

- A Power BI-hoz készült auditnaplóknak a bérlőben történő megtekintéséhez a bérlőben szükség van legalább egy Exchange-postaláda licencre.

## <a name="accessing-your-audit-logs"></a>A naplók elérése

Naplókhoz csak akkor fér hozzá, ha a naplózás engedélyezve van a Power BI-ban. További információt a felügyeleti portál dokumentációjának [Auditnaplók](service-admin-portal.md#audit-logs) című szakaszában talál. Akár 48 órás késés is lehet a naplózás engedélyezése és a naplózási adatok megtekinthetővé válása között. Ha nem látja azonnal adatokat, ellenőrizze később az auditnaplókat. Hasonló késés lehet az auditnaplók megtekintési engedélyének megkapása és a naplók elérésének lehetővé válása között.

A Power BI auditnaplói közvetlenül az [Office 365 Biztonsági és megfelelőségi központon](https://sip.protection.office.com/#/unifiedauditlog) keresztül érhetők el. A Power BI felügyeleti portálon is talál egy oda mutató hivatkozást:

1. A Power BI-ban válassza jobb felső **fogaskerékikont**, majd a **Felügyeleti portál** lehetőséget.

   ![Felügyeleti portál](media/service-admin-auditing/powerbi-admin.png)

1. Válassza a **Naplók** lehetőséget.

1. Válassza az **Ugrás az O365 felügyeleti központjára** lehetőséget.

   ![Ugrás az O365 felügyeleti központjára](media/service-admin-auditing/audit-log-o365-admin-center.png)

Ha a nem rendszergazdai fiókoknak hozzáférést szeretne adni a naplóhoz, az engedélyeket az Exchange Online Felügyeleti központban kell kiadnia. Hozzáadhat például egy felhasználót egy meglévő szerepkörcsoporthoz, például a Szervezetfelügyelet csoporthoz, vagy létrehozhat egy új szerepkörcsoportot a Naplók szerepkörrel. További információ: [Az Exchange Online engedélyei](/exchange/permissions-exo/permissions-exo/).

## <a name="search-only-power-bi-activities"></a>Keresés csak Power BI-tevékenységek között

A keresési eredményeket az alábbi lépésekkel korlátozhatja kizárólag Power BI-tevékenységekre. A tevékenységek listáját a cikk későbbi, [A Power BI által naplózott tevékenységek listája](#list-of-activities-audited-by-power-bi) című szakaszában találja meg.

1. A **Naplókeresés** lapon válassza a **Keresés** lehetőség alatti **Tevékenységek** elem legördülő menüjét.

2. Válassza a **Power BI-tevékenységek** lehetőséget.

   ![Keresés auditnaplókban](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. A mező bezárásához kattintson bárhová a mezőn kívül.

A keresések ekkor csak a Power BI-tevékenységekre korlátozódnak.

## <a name="search-the-audit-logs-by-date"></a>Naplók keresése dátum szerint

A naplók között kereshet dátumtartomány szerint a **Kezdő dátum** és a **Záró dátum** mezőkkel. Az elmúlt hét nap alapértelmezés szerint ki van jelölve. A dátum és idő az Egyezményes világidő (UTC) formátumában jelenik meg. A megadható maximális dátumtartomány 90 nap. 

Ha a dátumtartomány nagyobb 90 napnál, hibaüzenet jelenik meg. Ha a maximális értéket (90 napot) adta meg, **kezdődátumnak** a jelenlegi időt írja be. Ellenkező esetben hibaüzenet jelenik meg, mely szerint a kezdő dátum korábban van a záró dátumnál. Ha az elmúlt 90 napban kapcsolta be a naplózást, a dátumtartomány nem kezdődhet a naplózás bekapcsolásának napja előtt.

![](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Naplók keresése felhasználók szerint

A naplóbejegyzések között kereshet adott felhasználók által elvégzett tevékenységeket. Ehhez írjon be egy vagy több felhasználónevet a **Felhasználók** mezőbe. A felhasználónév e-mail-címre hasonlít; ezzel a fiókkal jelentkezik be a felhasználó a Power BI-ba. Ha a szervezet minden felhasználójáról (és szolgáltatásfiókjáról) szeretne eredményt kapni, hagyja üresen a mezőt.

![Keresés dátum szerint](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Keresési eredmények megtekintése

Az eredmények a **Keresés** lehetőség kiválasztása után néhány másodperccel megjelennek az **Eredmények** területen. A keresés befejeztével megjelenik a keresési eredmények száma. Legfeljebb 1000 esemény jelenhet meg egyszerre. Ha több mint 1000 esemény felel meg a keresési feltételeknek, csak a legutóbbi 1000 esemény jelenik meg.

### <a name="view-the-main-results"></a>A fő találatok megtekintése

Az **Eredmények** terület az alábbi adatokat tartalmazza a keresés által visszaadott egyes eseményekről. Kattintson az **Eredmények** terület egyik oszlopfejlécére az eredmények rendezéséhez.

| **Oszlop** | **Definíció** |
| --- | --- |
| Dátum |Az esemény dátuma és időpontja (UTC formátumban). |
| IP-cím |Az esemény naplózásakor használt eszköz IP-címe. Az IP-cím IPv4 vagy IPv6 formátumban jelenik meg. |
| Felhasználó |Az eseményt előidéző műveletet végrehajtó felhasználó (vagy szolgáltatásfiók). |
| Tevékenység |A felhasználó által végrehajtott tevékenység. Ez az érték megfelel a **Tevékenységek** legördülő menüben kiválasztott tevékenységeknek. Az Exchange felügyeleti naplójának eseményei esetén ez az érték egy Exchange-parancsmag. |
| Elem |A megfelelő tevékenység által létrehozott vagy módosított objektum. Például a megtekintett vagy módosított fájl, vagy a frissített felhasználói fiók. Nem minden tevékenységhez jelenik meg érték ebben az oszlopban. |
| Részlet |A tevékenységek további részletei. Nem minden tevékenységhez jelenik meg érték ebben az oszlopban sem. |

### <a name="view-the-details-for-an-event"></a>Az esemény részleteinek megtekintése

Ha további részletekre kíváncsi egy eseménnyel kapcsolatban, válassza az esemény rekordját a keresési eredmények listájában. Ekkor megjelenik a **Részletek** lap, ahol megtekintheti az eseményrekord részletes tulajdonságait. A megjelenő tulajdonságok típusa az esemény helyéül szolgáló Office 365-szolgáltatástól függ. 

Ezeknek a részleteknek a megjelenítéséhez válassza a **További információ** lehetőséget. Minden Power BI-bejegyzés RecordType tulajdonságának értéke 20. Más tulajdonságokkal kapcsolatban a [Tulajdonságok részletei az auditnaplóban](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/) című szakasz tartalmaz további információkat.

   ![Naplózás részletei](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Keresési eredmények exportálása

A Power BI-naplót a következő lépésekkel exportálhatja CSV-fájlba.

1. Válassza az **Eredmények exportálása** lehetőséget.

1. Válassza a **Betöltött eredmények mentése** vagy **Az összes eredmény letöltése** lehetőséget.

    ![Eredmények exportálása](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Keresés auditnaplókban a PowerShell használatával

A naplókhoz a bejelentkezésétől függően PowerShell-lel is hozzáférhet. Az alábbi példa a [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) parancs használatát mutatja be Power BI-auditnaplóbejegyzések lekérésére.

A [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession/) parancs használatához a fiókjának Exchange Online-licenccel kell rendelkeznie, Önnek pedig hozzá kell férnie a bérlő naplójához. További információ az Exchange Online-hoz való csatlakozásról: [Csatlakozás az Exchange Online-hoz a PowerShell-lel](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Egy másik példát a PowerShell auditnaplókkal való használatára a [Power BI Pro-licencek hozzárendelése a Power BI naplóival és a PowerShell-lel](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) című cikkben talál.

## <a name="activities-audited-by-power-bi"></a>A Power BI által naplózott tevékenységek

A Power BI az alábbi tevékenységeket naplózza.

* AddDatasourceToGateway (Adatforrás hozzáadása átjáróhoz)
* AddGroupMembers (Csoporttagok hozzáadása)
* AnalyzedByExternalApplication (Külső alkalmazásban elemezve)
* AnalyzeInExcel (Elemzés az Excelben)
* AttachDataflowStorageAccount (Adatfolyam-tárfiók csatolása)
* BindToGateway (Kötés átjáróhoz)
* ChangeCapacityState (Kapacitásállapot módosítása)
* ChangeGatewayAdministrators (Átjáró-rendszergazdák módosítása)
* ChangeGatewayDatasourceUsers (Átjáróadatforrás-felhasználók módosítása)
* CreateApp (Alkalmazás létrehozása)
* CreateDashboard (Irányítópult létrehozása)
* CreateDataflow (Adatfolyam létrehozása)
* CreateDataset (Adatkészlet létrehozása)
* CreateEmailSubscription (E-mail-feliratkozás létrehozása)
* CreateFolder (Mappa létrehozása)
* CreateGateway (Átjáró létrehozása)
* CreateGroup (Csoport létrehozása)
* CreateOrgApp (Szervezeti alkalmazás létrehozása)
* CreateReport (Jelentés létrehozása)
* DeleteComment (Megjegyzés törlése)
* DeleteDashboard (Irányítópult törlése)
* DeleteDataflow (Adatfolyam törlése)
* DeleteDataset (Adatkészlet törlése)
* DeleteEmailSubscription (E-mail-feliratkozás törlése)
* DeleteFolder (Mappa törlése)
* DeleteGateway (Átjáró törlése)
* DeleteGroup (Csoport törlése)
* DeleteGroupMembers (Csoporttagok törlése)
* DeleteOrgApp (Szervezeti alkalmazás törlése)
* DeleteReport (Jelentés törlése)
* DownloadReport (Jelentés letöltése)
* EditDataset (Adatkészlet szerkesztése)
* EditReport (Jelentése szerkesztése)
* ExportDataflow (Adatfolyam exportálása)
* ExportReport (Jelentés exportálása)
* ExportTile (Csempe exportálása)
* GenerateDataflowSasToken (Adatfolyam-SAS-token generálása)
* GenerateEmbedToken (Beágyazott token generálása)
* GetDatasources (Adatforrások beszerzése)
* Import (Importálás)
* InstallApp (Alkalmazás telepítése)
* MigrateWorkspaceIntoCapacity (Munkaterület migrálása kapacitásba)
* OptInForProTrial (Regisztráció a Pro csomag próbaverziójára)
* PostComment (Megjegyzés közzététele)
* PrintDashboard (Irányítópult nyomtatása)
* PrintReport (Jelentés nyomtatása)
* PublishToWebReport (Jelentés közzététele a weben)
* RefreshDataset (Adatkészlet frissítése)
* RemoveDatasourceFromGateway (Adatforrás eltávolítása átjáróból)
* RemoveWorkspacesFromCapacity (Munkaterületek eltávolítása kapacitásból)
* RenameDashboard (Irányítópult átnevezése)
* SetAllConnections (Az összes kapcsolat beállítása)
* SetScheduledRefresh (Ütemezett frissítés beállítása)
* SetScheduledRefreshOnDataflow (Adatfolyam ütemezett frissítésének beállítása)
* ShareDashboard (Irányítópult megosztása)
* ShareReport (Jelentés megosztása)
* TakeOverDataset (Adatkészlet átvétele)
* TakeOverDatasource (Adatforrás átvétele)
* UnpublishApp (Alkalmazás közzétételének visszavonása)
* UpdateApp (Alkalmazás frissítése)
* UpdateCapacityAdmins (Kapacitás-rendszergazdák frissítése)
* UpdateCapacityDisplayName (Kapacitás megjelenített neve)
* UpdateCapacityResourceGovernanceSettings (Kapacitásforrás szabályozási beállításai)
* UpdateCapacityUsersAssignment (Felhasználói hozzárendelések a kapacitásban)
* UpdatedAdminFeatureSwitch (Frissített rendszergazdai funkciókapcsoló)
* UpdateDataflow (Adatfolyam frissítése)
* UpdateDatasetParameters (Adatkészlet-paraméterek frissítése)
* UpdateDatasourceCredentials (Adatforrás hitelesítő adatainak frissítése)
* UpdateDatasources (Adatforrások frissítése)
* UpdateEmailSubscription (E-mail-feliratkozás frissítése)
* UpdateFolder (Mappa frissítése)
* UpdateFolderAccess (Mappahozzáférés frissítése)
* ViewDashboard (Irányítópult megtekintése)
* ViewDataflow (Adatfolyam megtekintése)
* ViewReport (Jelentés megtekintése)
* ViewTile (Csempe megtekintése)
* ViewUsageMetrics (Használati metrikák megtekintése)

## <a name="next-steps"></a>Következő lépések

[Mit jelent a Power BI-felügyelet?](service-admin-administering-power-bi-in-your-organization.md)  

[Power BI Felügyeleti portál](service-admin-portal.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
