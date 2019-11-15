---
title: SAP-változók szerkesztése a Power BI szolgáltatásban (előzetes verzió)
description: Az Azure és a Power BI
author: Sujata994
ms.author: sunaraya
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: d78124045767323cca657fa41d4415ca2e929f3d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881913"
---
# <a name="edit-sap-variables-in-the-power-bi-service-preview"></a>SAP-változók szerkesztése a Power BI szolgáltatásban (előzetes verzió)

Az SAP Business Warehouse vagy az SAP HANA DirectQueryvel való használatakor a jelentéskészítők mostantól szerkeszteni tudják az SAP-változókat a **Power BI szolgáltatásban** prémium szintű munkaterületek esetén.

![Változók szerkesztése párbeszédpanel](media/service-edit-sap-variables/sap-edit-variables-dialog.png)

Ez a dokumentum a változók Power BI-beli szerkesztésének feltételeit, az előzetes verziójú funkció engedélyezését és a Power BI szolgáltatás változók szerkesztésére alkalmas részét ismerteti.

## <a name="requirements-for-sap-edit-variables"></a>SAP-változók szerkesztésének előfeltételei

Az SAP-változók szerkesztésére alkalmas funkció használatának van néhány előfeltétele. A következő lista ezeket a követelményeket sorolja fel.

**Szükséges az új szűrési felület** – a jelentéshez engedélyezve kell lennie az [új szűrési felületnek](power-bi-report-filter.md). Ezt a következőképpen engedélyezheti a jelentéshez a Power BI Desktopban:
- A Power BI Desktopban válassza a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** lehetőséget.
- A navigációs panelen az **Aktuális fájl** területen válassza a **Jelentésbeállítások** szakaszt.
- A **Szűrési felület** területen válassza a **Frissített szűrőpanel engedélyezése** lehetőséget.

**DirectQuery-kapcsolatok szükségesek** – az SAP-adatforráshoz DirectQuery használatával kell kapcsolódni. Az Importálás módú kapcsolódás nem támogatott.

**Power BI Premium-előfizetés szükséges** – az SAP-változók szerkesztésének funkciója jelenleg csak Power BI Premium-előfizetésekben működik.

**SSO beállítása szükséges** – a funkció működéséhez konfigurálva kell lennie az egyszeri bejelentkezésnek (SSO). További információt az [egyszeri bejelentkezés (SSO) áttekintésében](service-gateway-sso-overview.md) talál.

**Új átjáró-összetevők szükségesek** – Töltse le a legújabb átjárót és frissítse a meglévő átjárót. További információt a [szolgáltatás-átjáró](service-gateway-onprem.md) leírásában talál.

**SAP HANA esetén többdimenziós forrás szükséges** – SAP HANA esetén az SAP-változók szerkesztésének funkciója csak többdimenziós modellekkel működik, relációs forrásokkal nem.

**Szuverén felhőkben nem támogatott** – A Power Query Online jelenleg nem érhető el szuverén felhőben, ezért ez a funkció szuverén felhőkben nem támogatott.

## <a name="how-to-enable-the-feature"></a>A funkció engedélyezése

Az **SAP-változók szerkesztése** funkció engedélyezéséhez csatlakozzon egy SAP HANA- vagy SAP BW-adatforráshoz a Power BI Desktopban. Ez után nyissa meg a **Fájl > Lehetőségek és beállítások > Beállítások** panelt, és a bal oldali panel aktuális fájl szakaszában válassza a **DirectQuery** lehetőséget. Ennek kiválasztásakor a jobb oldali panelen megjelennek a DirectQuery beállítási lehetőségei, és egy **A végfelhasználók módosíthatják az SAP-változókat a jelentésben (előzetes verzió)** jelölőnégyzetet, ahogyan az alábbi ábrán látható.

![DirectQuery-beállítások](media/service-edit-sap-variables/sap-preview-setting-in-desktop.png)

## <a name="use-sap-edit-variables-in-power-bi-desktop"></a>SAP-változók szerkesztése a Power BI Desktopban

A Power BI Desktopban az SAP-változók szerkesztése funkcióval úgy szerkesztheti a változókat, hogy a Változók szerkesztése elemet választja a menüszalagon a **Lekérdezések szerkesztése** menüből. Ezzel megnyílik az alábbi párbeszédpanel. Ez a funkció a Power BI Desktopban már elérhető egy ideje. A jelentéskészítők az alábbi párbeszédpanelen választhatják ki a változókat a jelentéshez.

![Elemek hozzáadása](media/service-edit-sap-variables/sap-variables-add-items.png)

## <a name="use-sap-edit-variables-in-the-service"></a>SAP-változók szerkesztése a szolgáltatásban

A jelentés Power BI szolgáltatásban történő közzétételét követően a felhasználók már láthatják a **Változók szerkesztése** hivatkozást az új Szűrés panelen. Ha először teszi közzé a jelentést, akár 5 perc is eltelhet a Változók szerkesztése hivatkozás megjelenéséig. Ha a hivatkozás nem jelenik meg, akkor manuálisan kell frissítenie az adathalmazt.
Ezt a következő módon teheti meg:

1. A Power BI szolgáltatásban válassza az **Adathalmazok** fület egy munkaterület tartalomlistájában.

2. Keresse meg az adathalmazt, amelyet frissítenie kell, majd válassz a **Frissítés** ikont.

    ![Változók szerkesztése](media/service-edit-sap-variables/sap-edit-variables-link.png)

3. A Változók szerkesztése hivatkozás kiválasztásakor megnyílik a **Változók szerkesztése** párbeszédablak, amelyben a felhasználók felülírhatják a változókat. Az **Alaphelyzetbe állítás** gomb visszaállítja a változók eredeti értékeit, amelyek a párbeszédpanel megnyitásakor jelentek meg.

    ![Változók szerkesztése párbeszédpanel](media/service-edit-sap-variables/sap-edit-variables-dialog.png)

4. A **Változók szerkesztése** panelen végzett módosítások csak az aktuális felhasználó számára maradnak meg (a Power BI többi megőrzési viselkedéséhez hasonlóan). Az alábbi képen bemutatott **Alapértelmezések visszaállítása** lehetőség választása visszaállítja a jelentés készítője által kialakított állapotot a változókkal együtt.

    ![Alaphelyzetbe állítás](media/service-edit-sap-variables/reset-to-default.png)

Ha SAP HANA-t vagy SAP BW-t használó közzétett jelentésen dolgozik a Power BI szolgáltatásban, és a **Változók szerkesztése** funkció engedélyezve van, a jelentés tulajdonosa megváltoztathatja ezeket az alapértelmezéseket. A jelentés tulajdonosa szerkesztési módban módosíthatja a változókat, majd a jelentés mentésével engedélyezi, hogy ezek a beállítások legyenek a jelentés *új alapértelmezett beállításai*. A jelentéshez az annak tulajdonosa által végrehajtott ilyen módosítás után hozzáférő többi felhasználó az új beállításokat fogja látni alapértelmezettként.

## <a name="issues-and-considerations"></a>Problémák és megfontolandó szempontok

Az SAP-változók szerkesztésének funkciója alkalmazásokban jelenleg nincs támogatva.

## <a name="next-steps"></a>Következő lépések

Az SAP HANA-val, az SAP BW-vel és a DirectQueryvel kapcsolatos további információkat talál az alábbi cikkekben:

- [Az SAP HANA használata a Power BI Desktopban](desktop-sap-hana.md)
- [DirectQuery és SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
- [DirectQuery használata a Power BI-ban](desktop-directquery-about.md)