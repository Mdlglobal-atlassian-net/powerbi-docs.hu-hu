---
title: Adathalmaz megosztása (előzetes verzió)
description: Adathalmaz-tulajdonosként adathalmazokat hozhat létre és oszthat meg, hogy mások használhassák azokat. Ismerje meg, hogyan szabályozhatja az Összeállítási engedély használatával, hogy ki férhet hozzá az adatokhoz.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17c3322ed5f24d106412bafb9c4235ee15a626aa
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530511"
---
# <a name="share-a-dataset-preview"></a>Adathalmaz megosztása (előzetes verzió)

Ha *adatmodelleket* hoz létre a Power BI Desktopban, *adathalmazokként* megoszthatja azokat a Power BI szolgáltatásban. A jelentéskészítők így könnyen felfedezhetik és felhasználhatják az Ön által megosztott adathalmazokat. Megismerheti a megosztás módját, és hogy hogyan szabályozhatja az adatokhoz való hozzáférést az Összeállítási engedély használatával.

## <a name="steps-to-sharing-your-dataset"></a>Az adathalmaz megosztásának lépései

1. Először egy .pbix-fájlt hoz létre egy adatmodellel a Power BI Desktopban. Ha azt tervezi, hogy ezt az adathalmazt másoknak kínálja fel jelentések készítéséhez, akkor talán már nem is tervez jelentést a .pbix-fájlban.

    A .pbix-fájlt ajánlott egy Office 365-csoportba menteni.

1. Tegye közzé a .pbix-fájlt egy [új felületű munkaterületen](service-create-the-new-workspaces.md) a Power BI szolgáltatásban.
    
    Ennek a munkaterületnek a többi tagja máris készíthet ezen az adathalmazon alapuló jelentéseket más munkaterületeken.

1. Erről a munkaterületről [alkalmazást is közzétehet](service-create-distribute-apps.md). Ennek során az **Engedélyek** oldalon megadhatja, hogy ki rendelkezik engedélyekkel, és mit tehetnek meg.

    > [!NOTE]
    > Ha a **Teljes vállalat** lehetőséget választja, akkor a vállalatnál senki sem fog Összeállítási engedéllyel rendelkezni. Ez a probléma már ismert. Ehelyett adjon meg e-mail-címeket az **Adott személyek vagy csoportok** beállításnál.  Ha azt szeretné, hogy a vállalatnál mindenki rendelkezzen Összeállítási engedéllyel, adja meg a teljes vállalat egy e-mail-aliasát.

    ![Alkalmazásengedélyek beállítása](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. Válassza az **Alkalmazás közzététele** lehetőséget, vagy az **Alkalmazás frissítése** lehetőséget, ha az már közzé lett téve.

## <a name="build-permissions-for-shared-datasets"></a>Megosztott adathalmazokra vonatkozó összeállítási engedélyek

Az Összeállítási engedély típus csak adathalmazokra értelmezhető. Az ezzel rendelkező felhasználók új tartalmat, például jelentéseket, irányítópultokat, a Q&A-ból rögzített csempéket és Insights-felfedezéseket állíthatnak össze az adathalmaz alapján. Az adathalmazból a Power BI-on kívül, például Excel-munkalapokon is készíthetnek új tartalmat az Elemzés az Excelben funkció, XMLA és exportálás használatával.

A felhasználók többféle módon is megkaphatják az Összeállítási engedélyt:

- Ha legalább közreműködői szerepkörrel rendelkező tag egy munkaterületen, automatikusan összeállítási engedéllyel rendelkezik az adathalmazokhoz, és jogosult a jelentések másolására.
 
- Annak a munkaterületek egy tagja, ahol az adathalmaz található, adott személyekhez vagy biztonsági csoportokhoz rendelheti az engedélyt az Engedélykezelési központban. Válassza az adathalmaz melletti három pontot (...), majd az **Engedélyek kezelése** menüpontot.

    ![A három pont kiválasztása](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    Ezzel megnyitja az adathalmaz Engedélykezelési központját, ahol beállíthatja és módosíthatja az engedélyeket.

    ![Engedélykezelési központ](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- Egy rendszergazda, vagy annak a munkaterületek egy tagja, ahol az adathalmaz található, az alkalmazás közzététele során eldöntheti, hogy az alkalmazásra vonatkozó engedéllyel rendelkező felhasználók a mögöttes adathalmazokra vonatkozó Összeállítási engedéllyel is rendelkezzenek-e. Részletesebb leírást ennek a cikknek az [Adathalmaz megosztásának lépései](#steps-to-sharing-your-dataset) című szakaszában talál.

- Tegyük fel, hogy Újraosztási és Összeállítási engedéllyel rendelkezik egy adathalmazhoz. Amikor egy erre az adathalmazra épülő jelentést vagy irányítópultot oszt meg, beállíthatja, hogy a címzettek a mögöttes adathalmazra vonatkozó Összeállítási engedélyt is megkapják-e.

    ![Összeállítási engedélyek](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Az adathalmazra vonatkozó Összeállítási engedélyeket vissza is vonhatja. Ha ezt teszi, az érintettek továbbra is látni fogják a megosztott adathalmazra épülő jelentést, de többé nem szerkeszthetik azt.

## <a name="more-granular-permissions"></a>Részletesebb engedélyek

A Power BI-ban 2019 júniusában bevezetett Összeállítási engedély a meglévő Olvasási és Újraosztási engedélyt egészíti ki. Azok a felhasználók, akik ekkor alkalmazásengedélyeken, megosztáson vagy munkaterület-hozzáférésen keresztül már Olvasási engedéllyel rendelkeztek, az Összeállítási engedélyt is megkapták ugyanazokra az adathalmazokra. Az Összeállítási engedélyt azért kapták meg automatikusan, mert az Olvasási engedélyük addig is lehetővé tette számukra új tartalom összeállítását az adathalmaz alapján az Elemzés az Excelben funkció vagy exportálás használatával.

A részletesebben beállítható Összeállítás engedéllyel megadhatja, hogy ki az, aki csak megtekintheti a meglévő jelentés vagy irányítópult tartalmát, és ki hozhat létre a mögöttes adathalmazhoz kapcsolódó tartalmat.

Ha az adathalmazt egy annak munkaterületén kívüli jelentés használja, akkor az adathalmazt nem törölheti. Ehelyett hibaüzenet jelenik meg.

Az Összeállítási engedélyeket el is távolíthatja. Ilyen esetben azok, akiknek az engedélyét visszavonta, továbbra is látni fogják a jelentést, de már nem szerkeszthetik azt.

## <a name="track-your-dataset-usage"></a>Adathalmaz használatának nyomon követése

Ha munkaterületén megosztott adathalmazzal rendelkezik, érdemes lehet tudni, hogy más munkaterületeken milyen jelentések épülnek rá.

1. Az Adathalmazlista nézetben válassza a **Kapcsolódók megtekintése** lehetőséget.

    ![Kapcsolódó megtekintése ikont](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. A **Kapcsolódó tartalom** párbeszédpanelen az összes kapcsolódó elem megjelenik. A listában megtekintheti az ezen a munkaterületen, és a **Más munkaterületeken** lévő kapcsolódó elemeket.
 
    ![Kapcsolódó tartalom párbeszédpanel](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Következő lépések

- [Adathalmazok használata több munkaterületen (előzetes verzió)](service-datasets-across-workspaces.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
