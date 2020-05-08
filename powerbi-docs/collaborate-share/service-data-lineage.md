---
title: Adatéletút
description: A modern üzletiintelligencia-projektekben az adatok adatforrásból a célba történő eljutásának megértése kulcsfontosságú kihívást jelent számos ügyfél számára.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 02/27/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: fc1f55fbadfaa6c25dd9140a41064eaa876013df
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525399"
---
# <a name="data-lineage"></a>Adatéletút
A modern üzletiintelligencia-projektekben az adatok adatforrásból a célba történő eljutásának megértése kihívást jelenthet. A kihívás még nagyobb a több adatforráson, összetevőn és függőségen átívelő speciális elemzési projektek esetén. Nehéz választ adni az olyan kérdésekre, hogy például mi történik egy adat módosításakor, vagy hogy miért nem naprakész egy jelentés. Ezek megértéséhez szakértői csapatokra vagy mélyreható vizsgálatra van szükség. A kérdések megválaszolásában egy adatéletút-nézet lesz a segítségére.

![A Power BI életútnézete](media/service-data-lineage/service-data-lineage-view.png)
 
A Power BI számos különböző összetevőtípussal rendelkezik, például irányítópultokkal, jelentésekkel, adatkészletekkel és adatfolyamokkal. Számos adatkészlet és adatfolyam külső adatforrásokhoz (például SQL Server), illetve más munkaterületeken megtalálható külső adatkészletekhez csatlakozik. Az Ön tulajdonában álló munkaterületen kívüli adatkészletek az IT-részleg egy tagja vagy egy másik elemző birtokában lévő munkaterületen lehetnek. A külső adatforrások és adatkészletek végső soron megnehezíthetik az adatok származási helyének kiderítését. Ezért bevezettük az összetett és egyszerűbb projektekhez is használható származtatott nézetet.

A származtatott nézetben az egy munkaterületen lévő összes összetevő közötti adatéletút-kapcsolat látható, valamint azok minden külső függősége is. A nézetben az összes munkaterület-összetevő közötti kapcsolatok láthatók, a felfelé és lefelé irányuló adatfolyamokkal létesített kapcsolatokat is beleértve.

## <a name="explore-lineage-view"></a>A származtatott nézet felfedezése

Minden munkaterülethez (legyen az új vagy klasszikus) tartozik egy életútnézet, amelynek megtekintéséhez legalább Közreműködő szerepkörrel kell rendelkeznie az adott munkaterületen. Erről részletesen a jelen cikk [Engedélyek](#permissions) című szakaszában tájékozódhat.

* A származtatott nézet eléréséhez lépjen a munkaterület listanézetébe. Koppintson a **Listanézet** elemre, és válassza a **Származtatott nézet** lehetőséget.

   ![Váltás az életútnézetre](media/service-data-lineage/service-data-lineage-view-select.png)

Ebben a nézetben az összes munkaterület-összetevő, valamint az adatok egyik összetevőből másik összetevőbe áramlásának módja látható.

**Adatforrások**

Láthatja azokat az adatforrásokat, amelyekből az adatkészletek és az adatfolyamok nyerik az adatokat. Az adatforráskártyákon további információk jelennek meg, amelyek segítenek a forrás azonosításában. Az Azure SQL Server esetében például az adatbázis neve is látható.

![A származtatott nézet adatforrása átjáró nélkül](media/service-data-lineage/service-data-lineage-data-source-card.png)
 
**Átjárók**

Ha egy adatforrás egy helyszíni átjárón keresztül csatlakozik, az átjáró adatai is megjelennek az adatforráskártyán. Ha rendelkezik átjáró-rendszergazdaként vagy adatforrás-felhasználóként kapott engedélyekkel, további információkat is láthat (például az átjáró nevét).

![A származtatott nézet adatforrása átjáróval](media/service-data-lineage/service-data-lineage-data-gateway-card.png)

**Adatkészletek és adatfolyamok**
 
Adatkészletek és adatfolyamok esetén a legutóbbi frissítés időpontján kívül azt is láthatja, hogy tanúsított vagy előléptetett-e az adatkészlet vagy az adatfolyam.

![Előléptetett és tanúsított adatkészletek az életútnézetben](media/service-data-lineage/service-data-lineage-promoted-certified.png)
 
Ha a munkaterület valamelyik jelentése egy másik munkaterületen lévő adatkészletre vagy adatfolyamra épül, akkor a forrásoldali munkaterület nevét is láthatja az adatkészlet vagy az adatfolyam kártyáján. A forrásoldali munkaterületre ugráshoz válassza ki annak nevét.

* Az egyes összetevőkhöz rendelkezésre álló lehetőségek menüjének megnyitásához válassza a **További lehetőségek** (...) elemet. Ebben a menüben ugyanazokat a műveleteket találja, mint a listanézetben.

Ha további metaadatokat szeretne megjeleníteni bármely összetevőről, válassza ki az összetevő kártyáját. Az összetevő további adatai megjelennek egy oldalsó panelen. Az alábbi képen a kijelölt adatkészlet metaadatait mutató oldalsó panel látható.

![A további információkat tartalmazó oldalsó panel](media/service-data-lineage/service-data-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Egy tetszőleges összetevő adatéletútjának megjelenítése 

Tegyük fel, hogy meg szeretné tekinteni egy adott összetevő adatéletútját.

* Válassza az összetevő alatti dupla nyilat.

   ![Egy adott összetevő életútjának kiemelése](media/service-data-lineage/service-data-lineage-specific-artifact.png)

   A Power BI kiemeli az adott összetevőhöz kapcsolódó összetevőket, a többit pedig elhalványítja. 

## <a name="navigation-and-full-screen"></a>Navigálás és teljes képernyő 

A származtatott nézet egy interaktív vászon. Az egér és az érintőpad használatával lépegethet a vásznon, és nagyíthatja vagy kicsinyítheti is.

* A nagyításhoz vagy a kicsinyítéshez a jobb alsó sarokban lévő menüt, valamint az egeret vagy az érintőpadot használhatja.
* Ha több helyet szeretne a diagramnak, váltson teljes képernyőre a jobb alsó sarokban lévő gombbal. 

    ![Nagyítás, kicsinyítés vagy teljes képernyő](media/service-data-lineage/service-data-lineage-zoom.png)

## <a name="permissions"></a>Engedélyek

* A származtatott nézet megjelenítéséhez Power BI Pro-licencre van szüksége.
* A származtatott nézetet csak a munkaterülethez hozzáféréssel rendelkező felhasználók érhetik el.
* A felhasználóknak Rendszergazda, Tag vagy Közreműködő szerepkörrel kell rendelkezniük a munkaterületen. A Megtekintő szerepkörrel rendelkező felhasználók nem válthatnak adatéletút nézetre.


## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

- A származtatott nézet nem érhető el az Internet Explorerben. További információt [A Power BI használatát támogató böngészők](../power-bi-browsers.md) című cikkben talál.

## <a name="next-steps"></a>További lépések

* [Adathalmazok használata több munkaterületen (előzetes verzió)](../service-datasets-across-workspaces.md)
* [Adatkészletek hatáselemzése](service-dataset-impact-analysis.md)
