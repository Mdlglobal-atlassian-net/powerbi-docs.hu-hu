---
title: Lapszámozott Power BI-jelentések segédjelentései
description: Ebből a cikkből megtudhatja, hogy milyen adatforrásokat támogatnak a Power BI szolgáltatás többoldalas jelentései, és megismerheti az Azure SQL Database-adatforrások csatlakoztatásának módját.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 784e3fd3883adb9fc5b773cc730b992135d7ef8b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272810"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Lapszámozott Power BI-jelentések segédjelentései

A *segédjelentés* egy lapszámozott jelentéselem, amely egy másik lapszámozott jelentést jelenít meg egy lapszámozott főjelentés törzsében. A jelentések segédjelentései hasonlóak a weblapok kereteihez. Segítségükkel egy jelentést ágyazhat be egy jelentésbe. Bármilyen jelentés lehet segédjelentés. A segédjelentésként megjelenített jelentés a szülőjelentéssel megegyező Premium-munkaterületen található. A szülőjelentés kialakítható úgy, hogy paramétereket küldjön a segédjelentésnek. A segédjelentések ismétlődhetnek adatrégiókon belül, és egy paraméterrel szűrik a segédjelentés minden példányának adatait.  
  
 ![Segédjelentés egy lapszámozott jelentésben](media/subreports/paginated-report-subreport.png "Lapszámozott jelentés segédjelentése")  
  
 Ezen az ábrán a Sales Order (Értékesítési megrendelés) jelentésben látható kapcsolattartási adatok egy Contacts (Névjegyek) nevű segédjelentésből származnak.  
  
A lapszámozott jelentések (.rdl) fájljait a Power BI Jelentéskészítőben készítheti el és módosíthatja. Az SQL Server Reporting Services szolgáltatásban tárolt segédjelentéseket feltöltheti egy Power BI Premium-munkaterületre. A főjelentéseket és a segédjelentéseket azonos munkaterületen kell közzétenni. Telepítse a [Power BI Jelentéskészítőt](https://go.microsoft.com/fwlink/?linkid=2086513).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>A Jelentéskészítő és a Power BI szolgáltatás használata

Power BI Jelentéskészítő a számítógépen található lapszámozott jelentésekkel (más néven helyi jelentésekkel) vagy a Power BI szolgáltatásban tárolt jelentésekkel használható.  Jelentéskészítő első megnyitásakor be kell jelentkeznie a Power BI-fiókjába. Ha nem jelenik meg erre vonatkozó üzenet, válassza a **Bejelentkezés** lehetőséget a jobb felső sarokban.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Bejelentkezés a Power BI-ba":::

A bejelentkezést követően megjelenik egy **Power BI szolgáltatás** lehetőség a Power BI Jelentéskészítő **Fájl** menüjének **Megnyitás** és **Mentés másként** lehetőségeinél. Amikor a **Power BI szolgáltatás** lehetőséget választja egy jelentés mentéséhez, élő kapcsolatot hoz létre a Power BI Jelentéskészítő és a Power BI szolgáltatás között. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Megnyitás a Power BI szolgáltatásból":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Helyi jelentés mentése a Power BI szolgáltatásban

Mielőtt segédjelentést adhatna hozzá egy főjelentéshez, először létre kell hoznia két jelentést, majd elmentenie őket ugyanazon a Power BI Premium-munkaterületen. 

1. Meglévő helyi jelentés megnyitásához a **Fájl** menüben válassza a **Megnyitás** > **Ez a számítógép** lehetőséget, majd válasszon ki egy. rdl-fájlt.  

2. A **Fájl** menüben válassza a**Mentés másként** > **Power BI szolgáltatás** elemet.  További információ: [Lapszámozott jelentés közzététele a Power BI szolgáltatásban](paginated-reports-save-to-power-bi-service.md).

    > [!NOTE]
    > Jelentést a Power BI szolgáltatásból is feltölthet. További információt erről szintén a [Lapszámozott jelentés közzététele a Power BI szolgáltatásban](paginated-reports-save-to-power-bi-service.md) című cikkben találhat.

3. A **Mentés másként** párbeszédpanelen válasszon ki egy Power BI Premium-munkaterületet, ahol a lapszámozott jelentéseket tárolhatja.  A Premium-munkaterületek neve mellett egy gyémánt ikon látható ![prémium gyémánt ikon](media/subreports/report-builder-premium-diamond.png).

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Mentés másként a Power BI szolgáltatásban":::

4. Kattintson a **Mentés** gombra.

## <a name="add-a-subreport-to-a-report"></a>Segédjelentés hozzáadása egy jelentéshez

Most, hogy mindkét jelentést elmentette ugyanarra a Premium-munkaterületre, az egyiket hozzáadhatja a másikhoz segédjelentésként. Segédjelentés kétféleképpen adható hozzá. 

1. A **Beszúrás** menüszalagon válassza a **Segédjelentés** gombot, vagy kattintson a jobb gombbal a jelentésvászonra, és válassza a **Beszúrás** > **Segédjelentés** lehetőséget.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Segédjelentés beszúrása egy jelentésbe":::

    Megnyílik a **Segédjelentés tulajdonságai** párbeszédpanel.  

2. Válassza a **Tallózás** gombot > lépjen a segédjelentésként használni kívánt jelentésre > adja meg a segédjelentés nevét a **Név** szövegmezőben.

3. Igény szerint konfigurálja a többi tulajdonságot, így a [paramétereket](#use-parameters-in-subreports) is.

## <a name="use-parameters-in-subreports"></a>Paraméterek használata segédjelentésekben  
 Ha paramétereket szeretne küldeni a szülőjelentésből a segédjelentésbe, definiáljon egy jelentésparamétert a segédjelentésként használt jelentésben. Amikor elhelyezi a segédjelentést a szülőjelentésben, kiválaszthatja a jelentésparamétert és egy értéket, amelyeket a szülőjelentésből a segédjelentés jelentésparaméterének küld.  
  
> [!NOTE]  
> A segédjelentésből kiválasztott paraméter egy *jelentésparaméter*, nem pedig *lekérdezési* paraméter.  
  
 A segédjelentést a jelentés fő törzsében vagy egy adatrégióban helyezheti el. Ha egy segédjelentést egy adatrégióban helyez el, az az adatrégió minden csoportjának vagy sorának példányával együtt ismétlődik. A segédjelentésnek a csoportból vagy sorból küldhet értéket. A segédjelentés értéktulajdonságában használjon egy mezőkifejezést ahhoz a mezőhöz, amely a segédjelentés paraméterének elküldeni kívánt értéket tartalmazza.  
  
 További információ a paraméterek és segédjelentések használatáról az SQL Server Reporting Services dokumentációjának [Segédjelentés és paraméterek hozzáadása](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs) című cikkében találhat.  

## <a name="preview-paginated-reports-in-report-builder"></a>Lapszámozott jelentések előnézete a Jelentéskészítőben

A jelentések előnézetét a Jelentéskészítőben tekintheti meg.

- A **Kezdőlap** menüszalagon válassza a **Futtatás** lehetőséget. 

Mivel a Jelentéskészítő egy tervezési eszköz, a jelentés előnézete eltérhet a Power BI-ban megjelenített, renderelt változattól.

### <a name="notes-about-previewing"></a>Megjegyzések az előnézetről

- A Jelentéskészítő nem tárolja a jelentésekben használt adatforrások hitelesítő adatait.  A Jelentéskészítő minden hitelesítő adatot bekér az előnézet során.  
- Ha a jelentés adatforrásai a helyszínen találhatók, konfigurálnia kell egy átjárót, miután elmentette a jelentést a Power BI-munkaterületre.
- Ha Jelentéskészítő hibát észlel az előnézet során, egy általános üzenetet ad vissza.  Ha a hiba nehezen orvosolható, célszerű lehet inkább a Power BI szolgáltatásban renderelni a jelentést.  

## <a name="considerations"></a>Megfontolandó szempontok

### <a name="maintaining-the-connection"></a>A kapcsolat fenntartása

A Jelentéskészítő nem tartja meg a kapcsolatot a Power BI-hoz a fájl bezárásakor.  Egy helyi főjelentés segédjelentései tárolhatók a Power BI-munkaterületen. A jelentés bezárása előtt győződjön meg arról, hogy elmentette a főjelentést a Power BI-munkaterületen.  Ha ezt nem teszi meg, előfordulhat, hogy egy „nem található” típusú üzenet jelenik meg az előnézet során, mivel nincs élő kapcsolat a Power BI szolgáltatáshoz.  Ebben az esetben lépjen egy segédjelentésre, és válassza ki annak tulajdonságait.  Nyissa meg újra a segédjelentést a Power BI szolgáltatásban.  Ez újra létrehozza a kapcsolatot, így minden további segédjelentésnek megfelelően kell működnie.

### <a name="renaming-a-subreport"></a>Segédjelentés átnevezése

Ha átnevez egy segédjelentést a munkaterületen, módosítania kell a névhivatkozást a főjelentésben is. Ellenkező esetben a segédjelentés nem fog megjelenni. A főjelentés továbbra is megjelenik, azonban hibaüzenetet jelez a segédjelentés elemében.

## <a name="migrate-large-reports"></a>Nagyméretű jelentések migrálása

Ha nagyméretű jelentéseket migrál a Power BI-ra, érdemes lehet az [RdlMigration eszközt](../guidance/migrate-ssrs-reports-to-power-bi.md) használni.  A RdlMigration eszközt frissítettük, így más segédjelentésnév-másolatokat is képes kezelni.  Ismétlődő segédjelentésnevek akkor fordulhatnak elő, ha kettő vagy több jelentés azonos névvel rendelkezik, azonban eltérő alkönyvtárakban találhatók.  Ha a nevek nem egyedi módon vannak feloldva, a rendszer csak az első segédjelentést ismeri fel.

Ha a Jelentéskészítővel szeretne nagyméretű jelentéseket migrálni, elsőként a segédjelentésekkel kell dolgoznia. Mentse mindegyiket a Power BI-munkaterületen, hogy ne fordulhassanak elő ismétlődő jelentésnevek.

## <a name="share-reports-with-subreports"></a>Jelentések megosztása segédjelentésekkel

Ahogy már említettük, a főjelentésnek és a segédjelentéseknek ugyanazon a munkaterületen kell lenniük. Ellenkező esetben a segédjelentés nem fog megjelenni. A főjelentés megosztásakor a segédjelentéseket is meg kell osztania. Ha egy alkalmazásban osztja meg a főjelentést, bele kell foglalnia a segédjelentéseket is. Ha közvetlenül felhasználókkal vagy felhasználói csoportokkal osztja meg a főjelentést, a segédjelentéseket is meg kell osztania velük.
  
## <a name="next-steps"></a>Következő lépések

[Lapszámozott Power BI-jelentések segédjelentéseinek hibaelhárítása](subreports-troubleshoot.md)

[Lapszámozott jelentés megtekintése a Power BI szolgáltatásban](../consumer/paginated-reports-view-power-bi-service.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
