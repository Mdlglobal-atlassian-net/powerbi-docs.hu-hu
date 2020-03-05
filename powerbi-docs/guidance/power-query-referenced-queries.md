---
title: Power Query-lekérdezésekre való hivatkozás
description: Útmutató a Power Query-lekérdezésekre való hivatkozáshoz.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 49601798ae920d956441c5580079625bf7408e07
ms.sourcegitcommit: b59ec11a4a0a3d5be2e4d91548d637d31b3491f8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290569"
---
# <a name="referencing-power-query-queries"></a>Power Query-lekérdezésekre való hivatkozás

Ez a cikk a Power BI Desktopot használó adatmodellezőknek szól. Útmutatást nyújt a más lekérdezésekre hivatkozó Power Query-lekérdezések definiálásához.

Tisztázzuk ezt a fogalmat: _Egy második lekérdezésre hivatkozó lekérdezés úgy viselkedik, mintha a második lekérdezés lépései az első lekérdezés lépéseivel lennének összevonva, és azokat megelőzve futnának._

Tekintsünk meg néhány lekérdezést: A **Query1** lekérdezés egy webszolgáltatást használ adatforráskánt, és a betöltése le van tiltva. A **Query2**, a **Query3**, és a **Query4** lekérdezések mindegyike a **Query1**-re hivatkozik, és a kimenetük be lesz töltve az adatmodellbe.

![A lekérdezésfüggőségek képe az előző bekezdésben ismertetett lekérdezések bemutatásával.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Az adatmodell frissítésekor gyakori feltételezés, hogy a Power Query a **Query1** eredményét olvassa be, és a hivatkozott lekérdezések ezt használják újra. Ez a megközelítés téves. Valójában a Power Query külön hajtja végre a **Query2**, a **Query3** és a **Query4** lekérdezéseket.

Ez úgy fogható fel, hogy a **Query1** lépései be vannak ágyazva a **Query2** lekérdezésbe. Ugyanez vonatkozik a **Query3** és a **Query4** lekérdezésre is. Az alábbi ábrán részletesebben látható a lekérdezések végrehajtása.

![A lekérdezésfüggőségek módosított képén a Query 2, a Query 3, és a Query 4 látható. A Query 1 mindhárom lekérdezésbe be van ágyazva.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

A **Query1** végrehajtása háromszor zajlik le. A többszörös végrehajtás lelassíthatja az adatfrissítést, és negatív hatással lehet az adatforrásra.

A [Table.Buffer](/powerquery-m/table-buffer) funkció **Query1**-ben való használata nem küszöböli ki a további adatbeolvasást. Ez a funkció egy táblázatot pufferel a memóriába. A pufferelt táblázat csak egyazon lekérdezés végrehajtásán belül használható fel. Tehát ha a példában található **Query1** pufferelése a **Query2** végrehajtásakor zajlik le, akkor a pufferelt adatok nem használhatók fel a **Query3** és a **Query4** végrehajtásakor. Ezek önállóan fogják még kétszer pufferelni az adatokat. (Ez az eredmény valóban negatív hatást eredményezhet, mert a táblázatot minden hivatkozó lekérdezés pufferelni fogja.)

> [!NOTE]
> A Power Query összetett gyorsítótárazási architektúrája nem kiemelt témája ennek a cikknek. A Power Query az adatforrásból beolvasott adatok gyorsítótárazására képes. Lekérdezés végrehajtásakor azonban egynél többször is beolvashatja az adatforrásból származó adatokat.

## <a name="recommendations"></a>Javaslatok

A lekérdezéslogika duplikálásának elkerülése érdekében általában a lekérdezések hivatkozását javasoljuk. Ez a kialakítás azonban, ahogy a jelen cikk is leírja, az adatfrissítések lassulásához vezethet, és túlterhelheti az adatforrásokat.

Ehelyett inkább egy [adatfolyam](../service-dataflows-overview.md) kialakítását javasoljuk. Az adatfolyam használata lerövidítheti az adatfrissítési időt, és mérsékelheti az adatforrásokra gyakorolt negatív hatást.

Az adatfolyamot kialakíthatja az adatforrások és az átalakítások beágyazására. Mivel az adatfolyam egy megőrzött adattárolás a Power BI-szolgáltatáson belül, az adatbeolvasást gyorsan végzi el. Ezért az adatfrissítések időtartama akkor is rövidebb lehet, ha a lekérdezések hivatkozása többszörös kérelmeket eredményez az adatfolyam számára.

A példánkban szereplő **Query1** adatfolyam-entitásként újratervezett változatát a **Query2**, a **Query3**, és a **Query4** adatforrásként használhatja fel. Ezen kialakítás révén a **Query1** által forrásként használt entitás értékelése csak egyszer zajlik le.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Önkiszolgáló adat-előkészítés a Power BI-ban](../service-dataflows-overview.md)
- [Adatfolyamok létrehozása és használata a Power BI-ban](../service-dataflows-create-use.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
