---
title: Jelentések másolása más munkaterületekről (előzetes verzió) – Power BI
description: Útmutató adathalmaz megosztásához a vállalat több felhasználójával. Így mind jelentéseket készíthetnek az Ön adathalmaza alapján a saját munkaterületükön.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461465"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Jelentések másolása más munkaterületekről (előzetes verzió)

Megtudhatja, hogyan másolhat ki egy jelentést egy munkaterületről, és hogyan mentheti azt egy másik munkaterületen. Ezt követően módosíthatja a jelentést, vizualizációkat vagy más elemeket adhat hozzá vagy törölhet.

Ha egy munkaterületen vagy alkalmazásban Önnek megfelelő jelentést talál, másolatot készíthet róla, amelyet igényeinek megfelelően módosíthat. Az adatmodell elkészítésével nem kell foglalkoznia. Azt már létrehozták az Ön számára. Egy meglévő jelentést ráadásul sokkal egyszerűbb módosítani, mint egy üresből kiindulni.

## <a name="save-a-copy-of-a-report"></a>Jelentés másolatának mentése

1. Egy alkalmazásban vagy munkaterületen nyissa meg a Jelentéslista nézetet.

1. A **Műveletek** alatt válassza a **Másolat mentése** lehetőséget.

    ![Jelentés másolatának mentése](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    A **Másolat mentése** ikon csak akkor jelenik meg, ha a jelentés új felületű munkaterületen van, és Ön [Összeállítási engedéllyel](service-datasets-build-permissions.md#build-permissions-for-shared-datasets) rendelkezik. Akkor is Összeállítási engedéllyel kell rendelkeznie az adathalmazhoz, ha a munkaterülethez rendelkezik hozzáféréssel.

3. A **Jelentés másolatának mentése** párbeszédpanelen adja meg a jelentés nevét, és válassza ki a célmunkaterületet.

    ![Másolat mentése párbeszédpanel](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    A jelentést az aktuális munkaterületre, vagy másikra is mentheti a Power BI szolgáltatásban. Csak azokat az új felületű munkaterületeket látja, amelyeknek tagja.
  
4. Kattintson a **Mentés** gombra.

    Amikor menti a jelentés másolatát, élő kapcsolatot hoz létre az adathalmazzal, és úgy nyithatja meg a jelentéskészítő felület, hogy a teljes adathalmaz elérhető lesz. Nem készített másolatot az adathalmazról. Az adathalmaz továbbra is az eredeti helyén található. Az adathalmaz összes tábláját és mértékét felhasználhatja a saját jelentésében. Az adathalmazra vonatkozó sorszintű biztonsági (RLS) korlátozások érvényben vannak, így csak azokat az adatokat fogja látni, amelyekre az RLS-szerepköre alapján jogosult.

    A Power BI automatikusan létrehoz egy elemet az adathalmazok listájában, ha a jelentés alapja a munkaterületen kívüli adathalmaz. Ennek az adathalmaznak az ikonja más, mint a munkaterületen lévő adathalmazoké: ![Megosztott adathalmaz ikonja](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    A munkaterület tagjai így láthatják, hogy mely jelentések és irányítópultok használnak a munkaterületen kívüli adathalmazokat. A listaelem az adathalmazzal kapcsolatos információk mellett néhány műveletet is feltüntet.

    ![Adathalmaz-műveletek](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Kapcsolódó adathalmazok megtekintése

A munkaterületén lévő jelentésekről érdemes tudni, hogy melyik adathalmazon alapulnak.

1. A Jelentéslista nézetben válassza a **Kapcsolódók megtekintése** lehetőséget.

    ![Kapcsolódó megtekintése ikont](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. A **Kapcsolódó tartalom** párbeszédpanelen az összes kapcsolódó elem megjelenik. Ebben a listában az adathalmaz nem különbözik a többitől. Nem látható rajta, hogy más munkaterületen helyezkedik el. Ez a probléma ismert.
 
    ![Kapcsolódó tartalom párbeszédpanel](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Következő lépések

- [Adathalmazok használata több munkaterületen (előzetes verzió)](service-datasets-across-workspaces.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
