---
title: Képek megjelenítése jelentésbeli táblázatban vagy mátrixban
description: A Power BI Desktopban létrehozhat egy képekre mutató hivatkozásokat tartalmazó oszlopot. Ez után ezeket a hivatkozásokat a Power BI Desktopban vagy a Power BI szolgáltatásban hozzáadhatja egy jelentés táblázatához, mátrixához, szeletelőjéhez vagy többsoros kártyájához, hogy a kép megjelenjen.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 95b1dc1be3421f19fa8220629ca2003469658480
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874491"
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

## <a name="considerations"></a>Szempontok

- A kép fájlformátumának a következők egyikének kell lennie: .bmp, .jpg, .jpeg, .gif, .png, vagy .svg
- Az URL-címnek névtelenül elérhetőnek kell lennie, tehát nem lehet bejelentkezést igénylő webhelyen, például a SharePointon sem. Ha a képek mégis a SharePointon vagy a OneDrive-on vannak, beszerezheti a közvetlenül rájuk mutató beágyazási kódot. 


## <a name="next-steps"></a>További lépések

[Az oldal elrendezése és formázása](/learn/modules/visuals-in-power-bi/12-formatting)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

