---
title: Nagyméretű adathalmazok Power BI Premium-támogatása
description: A Power BI Premium mostantól támogatja a legfeljebb 10 GB méretű adathalmazok használatát.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 0449d7953b5cefb4c76d89f05ec5b3fa70e9c0da
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679382"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Nagyméretű adathalmazok Power BI Premium-támogatása

A Power BI Premium támogatja a legfeljebb 10 GB méretű Power BI Desktop- (.pbix-) fájlok feltöltését. Feltöltés után az adatkészlet frissíthet legfeljebb 12 GB méretig. Egy nagyméretű adathalmaz használatához tegye azt közzé egy prémium szintű kapacitáshoz társított munkaterületen.
 
## <a name="best-practices"></a>Ajánlott eljárások

Ez a szakasz ismerteti a nagyméretű adathalmazok használatának ajánlott eljárásait.

**A nagyméretű modellek rendkívül erőforrás-igényesek lehetnek** az Ön kapacitásán. Ajánlott legalább a P1 termékváltozat alkalmazása minden 1 GB-nál nagyobb méretű modell esetén. Bár nagy modellek legfeljebb A3-as SKU-kra épülő munkaterületre való közzététele sikeres lehet, a frissítésük nem.

A következő táblázatban a különböző méretű .pbix-fájlokhoz ajánlott termékváltozatok vannak megadva:

   |Termékváltozat  |A .pbix-fájl mérete   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | legfeljebb 10 GB   |

A Power BI Embedded A4 termékváltozata a P1 SKU-val, az A5 a P2-vel, az A6 pedig a P3-mal egyezik meg. Fontos tudni, hogy nagy modellek A és EM SKU-kba való közzététele olyan hibát eredményezhet, amely nem a megosztott kapacitásbeli modellméret-korlátozási hibával függ össze. Nagy modellek A és EM SKU-kban fellépő frissítési hibái feltehetően időtúllépésre utalnak. Dolgozunk az ilyen helyzetekben kapott hibaüzenetek érthetőbbé tételén.

**A .pbix-fájlok nagy mértékben tömörített állapotban tartalmazzák az adatokat**. Az adatok mérete valószínűleg többszörösére fog nőni a memóriába való betöltéskor, és ehhez képest is a többszörösére nőhet az adatok frissítése során.

**A nagyméretű adathalmazok ütemezett frissítése hosszú időt vehet igénybe**, és rendkívül erőforrás-igényes lehet. Ennek megfelelően nem ütemezzen túl sok egymással átfedő frissítést. Azt is fontos megjegyezni, hogy az ütemezett frissítési feladatok időkorlátja minden adathalmaz esetében a duplájára, négy órára lett növelve ebben az esetben. Javasoljuk, a [növekményes frissítés](service-premium-incremental-refresh.md) használatát, mert gyorsabb, megbízhatóbb, és kevesebb erőforrást használ fel.

**A jelentés kezdeti betöltése a nagyméretű adathalmazok esetében hosszú időt vehet igénybe**, ha már eltelt némi idő az adathalmaz utolsó használata óta, mivel a modell a prémium szintű kapacitáshoz tartozó memóriába van betöltve. A hosszabb ideig töltődő jelentések esetében egy betöltési folyamatjelző mutatja a betöltés előrehaladását.

**Ha a munkaterületet eltávolítja a prémium szintű kapacitásból**, a modell és az ahhoz társított összes jelentés és irányítópult sem fog működni.

**Bár a lekérdezésenkénti memória- és időkorlátozások a Premium szintű kapacitás esetében jóval magasabbak**, erősen ajánlott a vizualizációkat szűrőkkel és szeletelőkkel kizárólag a szükséges elemek megjelenítésére korlátozni.

**Következő lépések**

[Mi az a Power BI Premium?](service-premium.md)
[A Power BI Premium kibocsátási megjegyzései](service-premium-release-notes.md)
[Microsoft Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)
[A Power BI nagyvállalati üzembehelyezési előkészületeit bemutató tanulmány](https://aka.ms/pbienterprisedeploy)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
