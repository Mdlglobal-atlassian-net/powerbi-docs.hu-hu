---
title: Naplózás használata a cégnél
description: Megtudhatja, hogyan használhatja a Power BI naplózási funkcióját a végrehajtott műveletek figyelésére és vizsgálatára. Ehhez a biztonsági és megfelelőségi központot vagy a PowerShellt használhatja.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 27776b251734d025e4dcde9f525f321008647455
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383485"
---
# <a name="using-auditing-within-your-organization"></a>Naplózás használata a cégnél

Ha tisztában van azzal, hogy a Power BI-bérlőn ki, milyen műveletet és mely elemeken végez el, sokat segíthet a munkahelyének a követelményeknek (például a jogszabályi követelményeknek és a rekordkezelésnek) való megfelelésben. A Power BI naplózási funkcióját a felhasználók által végzett műveletek, például a „Jelentés megtekintése” vagy az „Irányítópult megtekintése” naplózására használhatja. Nem használhatja a naplózást engedélyek naplózására.

A naplózással kapcsolatos munkát az Office 365 Biztonsági és megfelelőségi központjában, vagy a PowerShell használatával végezheti el. A naplózás az Exchange Online funkcióin alapul, amelynek automatikusan megtörténik a kiépítése a Power BI támogatásához.

A naplózási adatokat dátumtartomány, felhasználó, irányítópult, jelentés, adatkészlet és tevékenységtípus szerint szűrheti. A tevékenységeket le is töltheti egy CSV-fájlban, és offline elemezheti.

## <a name="requirements"></a>Követelmények

Az auditnaplók eléréséhez az alábbi követelményeknek kell megfelelnie:

* Az auditnapló eléréséhez globális rendszergazdának kell lennie, vagy az auditnaplók vagy auditnaplók (csak megtekintés) szerepkör tagjának kell lennie az Exchange Online-ban. Alapértelmezés szerint ezek a szerepkörök a megfelelőség kezelése vagy a szervezet kezelése szerepkörcsoporthoz vannak hozzárendelve az Exchange felügyeleti központjának **Engedélyek** oldalán.

    Ha nem rendszergazdai fiókoknak hozzáférést szeretne adni az auditnaplóhoz, akkor fel kell vennie a felhasználót ezeknek a szerepkörcsoportoknak az egyikébe. Másik lehetőségként létrehozhat egy egyéni szerepkörcsoportot az Exchange felügyeleti központjában, hozzárendelheti az auditnaplók vagy auditnaplók (csak megtekintés) szerepkört ehhez a csoporthoz, majd felveheti a nem rendszergazdai fiókot az új szerepkörcsoportba. További információ: [Szerepkörcsoportok kezelése az Exchange Online-ban](/Exchange/permissions-exo/role-groups).

    Ha a Microsoft 365 Felügyeleti központjából nem éri el az Exchange felügyeleti központját, lépjen a https://outlook.office365.com/ecp weblapra, és jelentkezzen be a hitelesítő adataival.

* Ha rendelkezik hozzáféréssel az auditnaplóhoz, de nem globális rendszergazda vagy a Power BI szolgáltatás rendszergazdája, nem lesz hozzáférése a Power BI felügyeleti portáljához. Ebben az esetben az [Office 365 Biztonsági és megfelelőségi központra](https://sip.protection.office.com/#/unifiedauditlog) mutató közvetlen hivatkozást kell használnia.

## <a name="accessing-your-audit-logs"></a>A naplók elérése

Naplókhoz csak akkor fér hozzá, ha a naplózás engedélyezve van a Power BI-ban. További információt a felügyeleti portál dokumentációjának [Auditnaplók](service-admin-portal.md#audit-logs) című szakaszában talál. Akár 48 órás késés is lehet a naplózás engedélyezése és a naplózási adatok megtekinthetővé válása között. Ha nem látja azonnal adatokat, ellenőrizze később az auditnaplókat. Hasonló késés lehet az auditnaplók megtekintési engedélyének megkapása és a naplók elérésének lehetővé válása között.

A Power BI auditnaplói közvetlenül az [Office 365 Biztonsági és megfelelőségi központon](https://sip.protection.office.com/#/unifiedauditlog) keresztül érhetők el. A Power BI felügyeleti portálon is talál egy oda mutató hivatkozást:

1. A Power BI-ban válassza jobb felső **fogaskerékikont**, majd a **Felügyeleti portál** lehetőséget.

   ![Felügyeleti portál](media/service-admin-auditing/powerbi-admin.png)

1. Válassza a **Naplók** lehetőséget.

1. Válassza **A Microsoft 365 Felügyeleti központ megnyitása** lehetőséget.

   ![A Microsoft 365 Felügyeleti központ megnyitása](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Keresés csak Power BI-tevékenységek között

A keresési eredményeket az alábbi lépésekkel korlátozhatja kizárólag Power BI-tevékenységekre. A tevékenységek listáját a cikk későbbi, [A Power BI által naplózott tevékenységek listája](#activities-audited-by-power-bi) című szakaszában találja meg.

1. A **Naplókeresés** lapon válassza a **Keresés** lehetőség alatti **Tevékenységek** elem legördülő menüjét.

2. Válassza a **Power BI-tevékenységek** lehetőséget.

   ![Keresés auditnaplókban](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. A mező bezárásához kattintson bárhová a mezőn kívül.

A keresések ekkor csak a Power BI-tevékenységekre korlátozódnak.

## <a name="search-the-audit-logs-by-date"></a>Naplók keresése dátum szerint

A naplók között kereshet dátumtartomány szerint a **Kezdő dátum** és a **Záró dátum** mezőkkel. Az elmúlt hét nap alapértelmezés szerint ki van jelölve. A dátum és idő az Egyezményes világidő (UTC) formátumában jelenik meg. A megadható maximális dátumtartomány 90 nap. 

Ha a dátumtartomány nagyobb 90 napnál, hibaüzenet jelenik meg. Ha a maximális értéket (90 napot) adta meg, **kezdődátumnak** a jelenlegi időt írja be. Ellenkező esetben hibaüzenet jelenik meg, mely szerint a kezdő dátum korábban van a záró dátumnál. Ha az elmúlt 90 napban kapcsolta be a naplózást, a dátumtartomány nem kezdődhet a naplózás bekapcsolásának napja előtt.

![Keresés dátum szerint](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Naplók keresése felhasználók szerint

A naplóbejegyzések között kereshet adott felhasználók által elvégzett tevékenységeket. Ehhez írjon be egy vagy több felhasználónevet a **Felhasználók** mezőbe. A felhasználónév e-mail-címre hasonlít; ezzel a fiókkal jelentkezik be a felhasználó a Power BI-ba. Ha a szervezet minden felhasználójáról (és szolgáltatásfiókjáról) szeretne eredményt kapni, hagyja üresen a mezőt.

![Keresés felhasználók szerint](media/service-admin-auditing/search-audit-log-by-user.png)

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

A naplókhoz a bejelentkezésétől függően PowerShell-lel is hozzáférhet. Az alábbi példa azt mutatja be, hogyan csatlakozhat az Exchange Online PowerShellhez, majd használhatja a [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) parancsot a Power BI auditnapló-bejegyzéseinek lekérésére. A szkript futtatásához rendelkeznie kell a megfelelő engedélyekkel, amint az a [Követelmények](#requirements) szakaszban szerepel.

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

További információ az Exchange Online-hoz való csatlakozásról: [Csatlakozás az Exchange Online-hoz a PowerShell-lel](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Egy másik példát a PowerShell auditnaplókkal való használatára a [Power BI Pro-licencek hozzárendelése a Power BI naplóival és a PowerShell-lel](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) című cikkben talál.

## <a name="activities-audited-by-power-bi"></a>A Power BI által naplózott tevékenységek

A Power BI az alábbi tevékenységeket naplózza.

| Felhasználóbarát név                                     | Művelet neve                              | Megjegyzések                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Adatforrás hozzáadása Power BI-átjáróhoz             | AddDatasourceToGateway (Adatforrás hozzáadása átjáróhoz)                      |                                          |
| Power BI-mappahozzáférés hozzáadása                      | AddFolderAccess                             | Jelenleg nem használt                       |
| Power BI-csoporttagok hozzáadása                      | AddGroupMembers (Csoporttagok hozzáadása)                             |                                          |
| Egy rendszergazda adatfolyam-tárfiókot csatolt egy bérlőhöz | AdminAttachedDataflowStorageAccountToTenant | Jelenleg nem használt                       |
| Power BI-adatkészlet elemezve                         | AnalyzedByExternalApplication (Külső alkalmazásban elemezve)               |                                          |
| Power BI-jelentés elemzése                          | AnalyzeInExcel (Elemzés az Excelben)                              |                                          |
| Power BI-adatkészlet kötése egy átjáróhoz                | BindToGateway (Kötés átjáróhoz)                               |                                          |
| Kapacitásállapot módosítása                            | ChangeCapacityState (Kapacitásállapot módosítása)                         |                                          |
| Kapacitás felhasználó-hozzárendelésének módosítása                  | UpdateCapacityUsersAssignment (Felhasználói hozzárendelések a kapacitásban)               |                                          |
| Power BI-adathalmaz-kapcsolatok módosítása              | SetAllConnections (Az összes kapcsolat beállítása)                           |                                          |
| Power BI-átjáró rendszergazdái módosítva                   | ChangeGatewayAdministrators (Átjáró-rendszergazdák módosítása)                 |                                          |
| A Power BI-átjáró adatforrásának felhasználói módosultak        | ChangeGatewayDatasourceUsers (Átjáróadatforrás-felhasználók módosítása)                |                                          |
| Vállalati Power BI-tartalomcsomag létrehozása      | CreateOrgApp (Szervezeti alkalmazás létrehozása)                                |                                          |
| Power BI-alkalmazás létrehozása                              | CreateApp (Alkalmazás létrehozása)                                   |                                          |
| Power BI-irányítópult létrehozása                        | CreateDashboard (Irányítópult létrehozása)                             |                                          |
| Power BI-adatfolyam létrehozása                         | CreateDataflow (Adatfolyam létrehozása)                              |                                          |
| Power BI-adathalmaz létrehozása                          | CreateDataset (Adatkészlet létrehozása)                               |                                          |
| Power BI e-mail-feliratkozás létrehozása               | CreateEmailSubscription (E-mail-feliratkozás létrehozása)                     |                                          |
| Power BI-mappa létrehozása                           | CreateFolder (Mappa létrehozása)                                |                                          |
| Power BI-átjáró létrehozva                          | CreateGateway (Átjáró létrehozása)                               |                                          |
| Power BI-csoport létrehozása                            | CreateGroup (Csoport létrehozása)                                 |                                          |
| Power BI-jelentés létrehozása                           | CreateReport (Jelentés létrehozása)                                |                                          |
| Adatfolyam migrálása külső tárfiókba     | DataflowMigratedToExternalStorageAccount    | Jelenleg nem használt                       |
| Adatfolyam-engedélyek hozzáadása                        | DataflowPermissionsAdded                    | Jelenleg nem használt                       |
| Adatfolyam-engedélyek eltávolítása                      | DataflowPermissionsRemoved                  | Jelenleg nem használt                       |
| Vállalati Power BI-tartalomcsomag törlése      | DeleteOrgApp (Szervezeti alkalmazás törlése)                                |                                          |
| Power BI-megjegyzés törlése                          | DeleteComment (Megjegyzés törlése)                               |                                          |
| Power BI-irányítópult törlése                        | DeleteDashboard (Irányítópult törlése)                             | Jelenleg nem használt                       |
| Power BI-adatfolyam törlése                         | DeleteDataflow (Adatfolyam törlése)                              | Jelenleg nem használt                       |
| Power BI-adathalmaz törlése                          | DeleteDataset (Adatkészlet törlése)                               |                                          |
| Power BI e-mail-feliratkozás törlése               | DeleteEmailSubscription (E-mail-feliratkozás törlése)                     |                                          |
| Power BI-mappa törlése                           | DeleteFolder (Mappa törlése)                                |                                          |
| Power BI-mappahozzáférés törlése                    | DeleteFolderAccess                          | Jelenleg nem használt                       |
| Power BI-átjáró törölve                          | DeleteGateway (Átjáró törlése)                               |                                          |
| Power BI-csoport törlése                            | DeleteGroup (Csoport törlése)                                 |                                          |
| Power BI-jelentés törlése                           | DeleteReport (Jelentés törlése)                                |                                          |
| Power BI-adathalmaz adatforrásainak felderítése          | GetDatasources (Adatforrások beszerzése)                              |                                          |
| Letöltött Power BI-jelentés                        | DownloadReport (Jelentés letöltése)                              |                                          |
| Power BI tanúsítási engedélyek szerkesztése          | EditCertificationPermission                 | Jelenleg nem használt                       |
| Power BI-irányítópult szerkesztése                         | EditDashboard (Irányítópult szerkesztése)                               | Jelenleg nem használt                       |
| Power BI-adathalmaz szerkesztése                           | EditDataset (Adatkészlet szerkesztése)                                 |                                          |
| Power BI-adathalmaz tulajdonságainak szerkesztése                | EditDatasetProperties                       | Jelenleg nem használt                       |
| Power BI-jelentés szerkesztése                            | EditReport (Jelentése szerkesztése)                                  |                                          |
| Power BI-adatfolyam exportálása                        | ExportDataflow (Adatfolyam exportálása)                              |                                          |
| Power BI-jelentés vizualizációs adatainak exportálása              | ExportReport (Jelentés exportálása)                                |                                          |
| Power BI-csempeadatok exportálása                       | ExportTile (Csempe exportálása)                                  |                                          |
| Adatfolyam-engedélyek sikertelen hozzáadása                | FailedToAddDataflowPermissions              | Jelenleg nem használt                       |
| Adatfolyam-engedélyek sikertelen eltávolítása             | FailedToRemoveDataflowPermissions           | Jelenleg nem használt                       |
| Power BI-adatfolyam SAS-jogkivonatának generálása             | GenerateDataflowSasToken (Adatfolyam-SAS-token generálása)                    |                                          |
| Beágyazott Power BI-token generálása                    | GenerateEmbedToken (Beágyazott token generálása)                          |                                          |
| Fájl importálása a Power BI-ba                         | Importálás                                      |                                          |
| Power BI-alkalmazás telepítése                            | InstallApp (Alkalmazás telepítése)                                  |                                          |
| Munkaterület kapacitásba migrálása                  | MigrateWorkspaceIntoCapacity (Munkaterület migrálása kapacitásba)                |                                          |
| Power BI-megjegyzés közzététele                           | PostComment (Megjegyzés közzététele)                                 |                                          |
| Power BI-irányítópult nyomtatása                        | PrintDashboard (Irányítópult nyomtatása)                              |                                          |
| Power BI-jelentésoldal nyomtatása                      | PrintReport (Jelentés nyomtatása)                                 |                                          |
| Power BI-jelentés webes közzététele                  | PublishToWebReport (Jelentés közzététele a weben)                          |                                          |
| Power BI-adatfolyam titkos kódjának fogadása a Key Vaultból  | ReceiveDataflowSecretFromKeyVault           | Jelenleg nem használt                       |
| Adatforrás törölve a Power BI-átjáróból         | RemoveDatasourceFromGateway (Adatforrás eltávolítása átjáróból)                 |                                          |
| Power BI-csoporttagok eltávolítása                    | DeleteGroupMembers (Csoporttagok törlése)                          |                                          |
| Munkaterület eltávolítása kapacitásból                 | RemoveWorkspacesFromCapacity (Munkaterületek eltávolítása kapacitásból)                |                                          |
| Power BI-irányítópult átnevezése                        | RenameDashboard (Irányítópult átnevezése)                             |                                          |
| Power BI-adatfolyam frissítésének kérése               | RequestDataflowRefresh                      | Jelenleg nem használt                       |
| Power BI-adathalmaz frissítésének kérése                | RefreshDataset (Adatkészlet frissítése)                              |                                          |
| Power BI-munkaterületek fogadása                     | GetWorkspaces                               |                                          |
| Power BI-adatfolyam ütemezett frissítésének beállítása        | SetScheduledRefreshOnDataflow (Adatfolyam ütemezett frissítésének beállítása)               |                                          |
| Power BI-adathalmaz ütemezett frissítésének beállítása         | SetScheduledRefresh (Ütemezett frissítés beállítása)                         |                                          |
| Power BI-irányítópult megosztása                         | ShareDashboard (Irányítópult megosztása)                              |                                          |
| Power BI-jelentés megosztása                            | ShareReport (Jelentés megosztása)                                 |                                          |
| Megkezdett Power BI-próbaidőszak (kiterjesztett)                   | OptInForExtendedProTrial                    | Jelenleg nem használt                       |
| Power BI-próbaidőszak megkezdése                            | OptInForProTrial (Regisztráció a Pro csomag próbaverziójára)                            |                                          |
| Power BI-adatforrás átvétele                   | TakeOverDatasource (Adatforrás átvétele)                          |                                          |
| Power BI-adathalmaz átvétele                        | TakeOverDataset (Adatkészlet átvétele)                             |                                          |
| Közzé nem tett Power BI-alkalmazás                          | UnpublishApp (Alkalmazás közzétételének visszavonása)                                |                                          |
| Kapacitásforrás szabályozási beállításainak frissítése      | UpdateCapacityResourceGovernanceSettings (Kapacitásforrás szabályozási beállításai)    | Jelenleg nem a Microsoft 365 Felügyeleti központjában van |
| Kapacitás-rendszergazda frissítése                            | UpdateCapacityAdmins (Kapacitás-rendszergazdák frissítése)                        |                                          |
| Kapacitás megjelenített nevének frissítése                     | UpdateCapacityDisplayName (Kapacitás megjelenített neve)                   |                                          |
| Vállalati Power BI-beállítások frissítése          | UpdatedAdminFeatureSwitch (Frissített rendszergazdai funkciókapcsoló)                   |                                          |
| Power BI-alkalmazás frissítése                              | UpdateApp (Alkalmazás frissítése)                                   |                                          |
| Power BI-adatfolyam frissítése                         | UpdateDataflow (Adatfolyam frissítése)                              |                                          |
| Power BI-adathalmaz adatforrásainak frissítése             | UpdateDatasources (Adatforrások frissítése)                           |                                          |
| Power BI-adathalmaz paramétereinek frissítése               | UpdateDatasetParameters (Adatkészlet-paraméterek frissítése)                     |                                          |
| Power BI e-mail-feliratkozás frissítése               | UpdateEmailSubscription (E-mail-feliratkozás frissítése)                     |                                          |
| Power BI-mappa frissítése                           | UpdateFolder (Mappa frissítése)                                |                                          |
| Power BI-mappahozzáférés frissítése                    | UpdateFolderAccess (Mappahozzáférés frissítése)                          |                                          |
| Power BI-átjáró adatforráshoz tartozó hitelesítő adatainak frissítése  | UpdateDatasourceCredentials (Adatforrás hitelesítő adatainak frissítése)                 |                                          |
| Power BI-irányítópult megtekintése                         | ViewDashboard (Irányítópult megtekintése)                               |                                          |
| Power BI-adatfolyam megtekintése                          | ViewDataflow (Adatfolyam megtekintése)                                |                                          |
| Power BI-jelentés megtekintése                            | ViewReport (Jelentés megtekintése)                                  |                                          |
| Power BI-csempe megtekintése                              | ViewTile (Csempe megtekintése)                                    |                                          |
| Power BI-használati metrikák megtekintése                     | ViewUsageMetrics (Használati metrikák megtekintése)                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Következő lépések

[Mit jelent a Power BI-felügyelet?](service-admin-administering-power-bi-in-your-organization.md)  

[Power BI Felügyeleti portál](service-admin-portal.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
