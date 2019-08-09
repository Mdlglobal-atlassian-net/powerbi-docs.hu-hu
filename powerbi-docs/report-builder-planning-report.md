---
title: Jelentések tervezése a Power BI Jelentéskészítőben
description: A Power BI lapszámozott jelentéskészítőjével számos típusú lapszámozott jelentést készíthet. Hasznos és könnyen értelmezhető jelentések készítése előtt célszerű megtervezni azokat.
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 33cdb53ab411e0d2f4686f7cc9a41bb3f0fe4cb6
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68623875"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Jelentések tervezése a Power BI Jelentéskészítőben

A Power BI lapszámozott jelentéskészítőjével számos típusú lapszámozott jelentést készíthet. Létrehozhat például olyan jelentéseket, amelyek összefoglalásokat vagy részletes értékesítési adatokat, marketing- vagy értékesítési trendeket, működési jelentéseket vagy irányítópultokat tartalmaznak. Emellett részletesen formázott szöveget alkalmazó jelentéseket is készíthet, például értékesítési megrendelésekhez, termékkatalógusokhoz vagy sablonlevelekhez. Az ilyen jelentések a Jelentéskészítő építőelemeinek különböző kombinációival készíthetők el. Hasznos és könnyen értelmezhető jelentések készítése előtt célszerű megtervezni azokat. Íme néhány dolog, amit célszerű figyelembe venni az első lépések előtt:  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>Milyen formátumban szeretné megjeleníteni a jelentést?
  
A jelentéseket online, egy böngészőben is megjelenítheti (például a Power BI portálon), vagy exportálhatja őket más formátumokba, például Excelbe, Wordbe vagy PDF-be. A jelentés végleges formátuma fontos szempont, mivel nem minden funkció érhető el minden exportálási formátumban. 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>Milyen struktúrában szeretné megjeleníteni az adatokat?
  
Az adatok megjelenítéséhez választhat táblázatos, mátrix (lapközi vagy kimutatáshoz hasonló), diagram, vagy kötetlen struktúrák közül választhat, de ezek kombinációit is használhatja. További információ: [Táblázatok, mátrixok és listák a Power BI Jelentéskészítőben](report-builder-tables-matrices-lists.md).  
  
## <a name="how-do-you-want-your-report-to-look"></a>Milyen külsőt képzel el a jelentésnek?
  
A Jelentéskészítő számos jelentésbeli tétellel szolgál, amelyet a jelentéshez adva azt könnyebben olvashatóvá teheti, kiemelheti a fontos adatokat, vagy segíthet a közönségnek az eligazodásban. A jelentés megjelenésének elképzelése azt is megszabja, hogy szükség lesz-e olyan jelentésbeli tételekre, mint a szövegmezők, téglalapok, képek és sorok. Célszerű lehet emellett megjeleníteni vagy elrejteni egyes elemeket, felvenni egy dokumentumtérképet, részletezéses jelentéseket vagy segédjelentéseket hozzáadni, vagy hivatkozni további jelentésekre.   
  
## <a name="should-the-data-be-filtered"></a>Szükséges szűrni az adatokat?
  
A jelentés hatókörét célszerű lehet adott felhasználókra vagy helyekre, esetleg egy adott időszakra korlátozni. A jelentésadatok szűréséhez paraméterekkel kérheti le és jelenítheti meg a kívánt adatokat. További információ: [Jelentésparaméterek a Power BI Jelentéskészítőben](paginated-reports-parameters.md).  
  
## <a name="do-you-need-to-create-calculations"></a>Szükséges létrehozni számításokat? 
  
Előfordulhat, hogy az adatforrás és az adatkészletek nem tartalmazzák azokat a mezőket, amelyekre szüksége van a jelentéshez. Ebben az esetben létrehozhatja saját számított mezőit. Előfordulhat például, hogy meg szeretné szorozni az egységenkénti árat a mennyiséggel, hogy megkapja a sorelem értékesítési mennyiségét. A kifejezések feltételes formázást és egyéb fejlett funkciókat is lehetővé tesznek. További információ: [Kifejezések a Power BI Jelentéskészítőben](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>El szeretne rejteni bizonyos elemeket?
  
Fontolja meg, hogy a jelentés első futtatásakor érdemes-e bizonyos jelentésbeli tételeket elrejtenie, például adatrégiókat, vagy csoportokat és oszlopokat. Például elsőként bemutathat egy összefoglaló táblázatot, majd részletezheti annak adatait. 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>Hogyan fogja terjeszteni a jelentést?  
  
A jelentést elmentheti a helyi gépen, ahol tovább szerkesztheti, vagy helyileg futtathatja. Azonban ha meg szeretné osztani másokkal, el kell mentenie a Power BI-ban. A mentéssel mások is igény szerint futtathatják. Másik lehetőségként beállíthat egy feliratkozást és e-mailes kézbesítést a jelentéshez, amelyet más felhasználók használhatnak. Igény szerint adott exportálási formátumban küldheti el a jelentést. 
  
## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
