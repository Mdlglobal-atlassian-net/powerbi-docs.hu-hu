---
title: Jelentések másolása más alkalmazásokból vagy munkaterületekről (előzetes verzió) – Power BI
description: Megtudhatja, hogyan készíthet másolatot a jelentésekről, és hogyan mentheti a saját munkaterületére.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/16/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8716a304e5b117c027d75db149ebcc8d95efebfe
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83312626"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Jelentések másolása más munkaterületekről (előzetes verzió)

Ha egy munkaterületen vagy alkalmazásban Önnek megfelelő jelentést talál, másolatot készíthet róla, amelyet egy másik munkaterületre menthet. Ezt követően módosíthatja a jelentés másolatát, és vizualizációkat vagy más elemeket adhat hozzá vagy törölhet. Az adatmodell elkészítésével nem kell foglalkoznia. Azt már létrehozták az Ön számára. Egy meglévő jelentést ráadásul sokkal egyszerűbb módosítani, mint egy üresből kiindulni. Azonban amikor a saját munkaterületén hoz létre egy alkalmazást, előfordulhat, hogy nem teheti közzé az alkalmazásban a jelentés másolatát. További információt az [„Adathalmazok használata több munkaterületen” című cikk szempontjai és korlátozásai](service-datasets-across-workspaces.md#considerations-and-limitations) között találhat.

> [!NOTE]
> Másolat készítéséhez Pro-licencre van szüksége, még akkor is, ha az eredeti jelentés egy Premium-kapacitásbeli munkaterületen található.

## <a name="save-a-copy-of-a-report-in-a-workspace"></a>A jelentés másolatának mentése a munkaterületen

1. Egy munkaterületen nyissa meg a Jelentéslista nézetet.

    ![Jelentéslista nézet](media/service-datasets-copy-reports/power-bi-report-list-view.png)

1. A **Műveletek** alatt válassza a **Másolat mentése** lehetőséget.

    ![Jelentés másolatának mentése](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    A **Másolat mentése** ikon csak akkor jelenik meg, ha a jelentés új felületű munkaterületen van, és [Összeállítási engedéllyel](service-datasets-build-permissions.md) rendelkezik. Akkor is Összeállítási engedéllyel kell rendelkeznie az adathalmazhoz, ha a munkaterülethez rendelkezik hozzáféréssel.

3. A **Jelentés másolatának mentése** párbeszédpanelen adja meg a jelentés nevét, és válassza ki a célmunkaterületet.

    ![Másolat mentése párbeszédpanel](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    A jelentést az aktuális munkaterületre, vagy másikra is mentheti a Power BI szolgáltatásban. Csak azokat az új felületű munkaterületeket látja, amelyeknek tagja. 
  
4. Kattintson a **Mentés** gombra.

    A Power BI automatikusan létrehoz egy másolatot a jelentésről, valamint egy elemet az adathalmazok listájában, ha a jelentés alapja a munkaterületen kívüli adathalmaz. Ennek az adathalmaznak az ikonja más, mint a munkaterületen lévő adathalmazoké: ![Megosztott adathalmaz ikonja](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)
    
    A munkaterület tagjai így láthatják, hogy mely jelentések és irányítópultok használnak a munkaterületen kívüli adathalmazokat. A listaelem az adathalmazzal kapcsolatos információk mellett néhány műveletet is feltüntet.

    ![Adathalmaz-műveletek](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

    További információt a jelentésről és a kapcsolódó adatkészletről a cikk [A jelentés saját másolata](#your-copy-of-the-report) című szakaszában találhat.

## <a name="copy-a-report-in-an-app"></a>Jelentés másolása egy alkalmazásban

1. Az alkalmazásban nyissa meg a másolni kívánt jelentést.
2. A menüsávon válassza a **További lehetőségek** ( **...** ) > **Másolat mentése** lehetőséget.

    ![Másolat készítése a jelentésről](media/service-datasets-copy-reports/power-bi-save-copy.png)

    A **Másolat mentése** lehetőség csak akkor jelenik meg, ha a jelentés új felületű munkaterületen van, és [Összeállítási engedéllyel](service-datasets-build-permissions.md) rendelkezik.

3. Adjon nevet a jelentésnek, majd válassza a **Mentés** elemet.

    ![A jelentésmásolat elnevezése](media/service-datasets-copy-reports/power-bi-save-report-from-app.png)

    A rendszer automatikusan menti a másolatot a saját munkaterületére.

4. A másolat megnyitásához válassza az **Ugrás a jelentés** lehetőséget.

## <a name="your-copy-of-the-report"></a>A jelentés másolata

Amikor menti a jelentés másolatát, élő kapcsolatot hoz létre az adathalmazzal, és úgy nyithatja meg a jelentéskészítő felület, hogy a teljes adathalmaz elérhető lesz. 

![A jelentés másolatának szerkesztése](media/service-datasets-copy-reports/power-bi-edit-report-copy.png)

Nem készített másolatot az adathalmazról. Az adathalmaz továbbra is az eredeti helyén található. Az adathalmaz összes tábláját és mértékét felhasználhatja a saját jelentésében. Az adathalmazra vonatkozó sorszintű biztonsági (RLS) korlátozások érvényben vannak, így csak azokat az adatokat fogja látni, amelyekre az RLS-szerepköre alapján jogosult.

## <a name="view-related-datasets"></a>Kapcsolódó adathalmazok megtekintése

Ha egy munkaterületen egy másik munkaterület egyik adatkészletén alapuló jelentés található, célszerű többet megtudnia az alapul szolgáló adatkészletről.

1. A Jelentéslista nézetben válassza a **Kapcsolódók megtekintése** lehetőséget.

    ![Kapcsolódó megtekintése ikont](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. A **Kapcsolódó tartalom** párbeszédpanelen az összes kapcsolódó elem megjelenik. Ebben a listában az adathalmaz nem különbözik a többitől. Nem látható rajta, hogy más munkaterületen helyezkedik el. Ez a probléma ismert.
 
    ![Kapcsolódó tartalom párbeszédpanel](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>Jelentés és megosztott adathalmaz törlése

Dönthet úgy, hogy többé nem kívánja munkaterületén tartani a jelentést és az azzal társított megosztott adathalmazt.

1. Törölje a jelentést. A munkaterületen a jelentések listájában válassza a **Törlés** ikont.

    ![Jelentés törlése ikon](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. Az adathalmazok listájában azt láthatja, hogy a megosztott adathalmazokhoz nem tartozik **Törlés** ikon. Frissítse az oldalt, vagy lapozzon másik oldalra, és térjen vissza. Az adathalmaz már nem lesz ott. Ha nem így van, ellenőrizze a **Kapcsolódó elemek megtekintése** lehetőséget. Lehetséges, hogy egy másik táblához kapcsolódik a munkaterületen belül.

    ![Kapcsolódó megtekintése ikont](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > A megosztott adathalmaz törlése erről a munkaterületről nem törli az adathalmazt. Csak az arra való hivatkozás lesz törölve.


## <a name="next-steps"></a>További lépések

- [Adathalmazok használata több munkaterületen (előzetes verzió)](service-datasets-across-workspaces.md)
- Kérdései vannak? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)
