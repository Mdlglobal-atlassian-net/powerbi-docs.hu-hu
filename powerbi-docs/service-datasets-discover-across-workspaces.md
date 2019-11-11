---
title: Jelentések létrehozása más munkaterületen lévő adathalmazok alapján (előzetes verzió) – Power BI
description: Útmutató adathalmaz megosztásához a vállalat több felhasználójával. Így mind jelentéseket készíthetnek az Ön adathalmaza alapján a saját munkaterületükön.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 371507eb86e1b68225e9d66ee3a1363b0e163d4f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877176"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>Jelentések létrehozása más munkaterületen lévő adathalmazok alapján (előzetes verzió)

Elsajátíthatja jelentések saját munkaterületein való létrehozását más munkaterületeken lévő adathalmazok alapján. Ha meglévő adathalmaz alapján szeretne jelentést készíteni, kiindulhat a Power BI Desktopból vagy a Power BI szolgáltatásból, a Saját munkaterületen vagy egy [új munkaterületi felhasználói felületen](service-create-the-new-workspaces.md).

- A Power BI szolgáltatásban: **Adatok lekérése** > **Közzétett adathalmazok**.
- A Power BI Desktopban: **Adatok lekérése** > **Power BI-adathalmazok**.

    ![Csatlakozás meglévő adathalmazhoz](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
Az adathalmaz-felfedezési felület mindkét esetben az **Adathalmaz kijelölése jelentés létrehozásához** párbeszédpanelen indul el. Itt az összes adathalmaz látható, amelyhez hozzáfér, függetlenül azok helyétől:

![Adathalmaz kijelölése](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Megfigyelheti, hogy az első a **Meghirdetett** címkével van ellátva. Erről a cikk egy későbbi, [Támogatott adathalmaz keresése](#find-an-endorsed-dataset) című szakaszában lesz szó.

Az ebben a listában megjelenő adathalmazok az alábbi feltétek közül legalább egynek eleget tesznek:

- Az adathalmaz az új munkaterületi felülettel rendelkező munkaterületek egyikén van, és Ön tagja ennek a munkaterületnek. Lásd: [Megfontolandó szempontok és korlátozások](service-datasets-across-workspaces.md#considerations-and-limitations).
- Ön Összeállítási engedéllyel rendelkezik az adathalmazon, amely új munkaterületi felülettel rendelkező munkaterületen van.
- Az adathalmaz az Ön saját munkaterületén van.

> [!NOTE]
> Ha Ön ingyenes felhasználó, akkor csak a Saját munkaterületen lévő adathalmazokat látja, valamint azokat a prémium szintű kapacitásbeli munkaterületeken lévőket, amelyekhez Összeállítási engedéllyel rendelkezik.

Ha a **Létrehozás** lehetőségre kattint, élő kapcsolatot hoz létre az adathalmazzal, és a jelentéskészítő felület úgy nyílik meg, hogy a teljes adathalmaz elérhető. Nem készített másolatot az adathalmazról. Az adathalmaz továbbra is az eredeti helyén található. Az adathalmaz összes tábláját és mértékét felhasználhatja a saját jelentései összeállításához. Az adathalmazra vonatkozó sorszintű biztonsági (RLS) korlátozások érvényben vannak, így csak azokat az adatokat fogja látni, amelyekre az RLS-szerepköre alapján jogosult.

A jelentést mentheti az aktuális munkaterületen a Power BI szolgáltatásban, vagy közzéteheti egy munkaterületen a Power BI Desktopból. A Power BI automatikusan létrehoz egy elemet az adathalmazok listájában, ha a jelentés alapja a munkaterületen kívüli adathalmaz. Ennek az adathalmaznak az ikonja más, mint a munkaterületen lévő adathalmazoké: ![Megosztott adathalmaz ikonja](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

A munkaterület tagjai így láthatják, hogy mely jelentések és irányítópultok használnak a munkaterületen kívüli adathalmazokat. A listaelem az adathalmazzal kapcsolatos információk mellett néhány műveletet is feltüntet.

![Adathalmaz-műveletek](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Támogatott adathalmaz keresése

Kétféle támogatott adathalmaz létezik. Az adathalmaz-tulajdonosok *Meghirdethetik* az Önnek ajánlott adathalmazokat. A Power BI-beli bérlői rendszergazda a vállalaton belüli szakértőket is kijelölhet, akik *minősítik* a mindenki által használható adathalmazokat. A meghirdetett és a minősített adathalmazok is *jelvénnyel* jelennek meg, amely az adathalmaz keresésekor és az adathalmazok munkaterületen belüli listájában is látható. Az adathalmaz minősítőjének neve elemleírásban jelenik meg az adathalmazok felderítési felületén. Akkor látható, ha a kurzort a **Minősített** címkére viszik.

- A Power BI szolgáltatásban: **Adatok lekérése** > **Közzétett adathalmazok**.
- A Power BI Desktopban: **Adatok lekérése** > **Power BI-adathalmazok**.

    Az **Adathalmaz kiválasztása** párbeszédpanelen a támogatott adathalmazok alapértelmezés szerint a lista elején helyezkednek el. 

    ![Meghirdetett adathalmaz](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Következő lépések

- [Adathalmazok használata több munkaterületen (előzetes verzió)](service-datasets-across-workspaces.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
