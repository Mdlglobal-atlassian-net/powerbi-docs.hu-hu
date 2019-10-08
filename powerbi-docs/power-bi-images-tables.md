---
title: Képek megjelenítése jelentésbeli táblázatban vagy mátrixban
description: A Power BI Desktopban létrehozhat egy képekre mutató hivatkozásokat tartalmazó oszlopot. Ez után ezeket a hivatkozásokat a Power BI Desktopban vagy a Power BI szolgáltatásban hozzáadhatja egy jelentés táblázatához, mátrixához, szeletelőjéhez vagy többsoros kártyájához, hogy a kép megjelenjen.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: cbb04057c8065e998068dd6520539c830a659f72
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715557"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>Képek megjelenítése jelentésbeli táblázatban, mátrixban vagy szeletelőben

A jelentéseket feldobhatják a hozzájuk adott képek. Bizonyos célokra megfelelnek az oldalon elhelyezett statikus képek. Máskor azonban az a vél, hogy a képek a jelentés adatait is tükrözzék. Ez a témakör a képek táblázatban, mátrixban, szeletelőben vagy többsoros kártyán való megjelenítését ismerteti. 

![Képek URL-címei táblázatban](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>Képek jelentéshez adása

1. Hozzon létre egy oszlopot, amely a képek URL-címeit tartalmazza. A követelményeket a cikk egy későbbi, [Megfontolandó szempontok](#considerations) című szakaszában találja meg.

1. Jelölje ki ezt az oszlopot. A **Modellezés** menüszalagon válassza ki a **Kép URL-címe** **Adatkategóriát**.

    ![Adatkategória beállítása a Kép URL-címe értékre](media/power-bi-images-tables/power-bi-set-url-image.png)

1. Vegye fel ezt az oszlopot egy táblázatba, mátrixba, szeletelőbe vagy többsoros kártyára.

    ![Képeket tartalmazó szeletelő](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>Megfontolandó szempontok

- A kép fájlformátumának a következők egyikének kell lennie: .bmp, .jpg, .jpeg, .gif, .png, vagy .svg
- Az URL-címnek névtelenül elérhetőnek kell lennie, tehát nem lehet bejelentkezést igénylő webhelyen, például a SharePointon sem. Ha a képek mégis a SharePointon vagy a OneDrive-on vannak, beszerezheti a közvetlenül rájuk mutató beágyazási kódot. 


## <a name="next-steps"></a>Következő lépések

[Az oldal elrendezése és formázása](/learn/modules/visuals-in-power-bi/12-formatting)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

