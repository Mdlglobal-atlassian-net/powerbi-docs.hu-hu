---
title: Jelentések tervezése a Power BI Jelentéskészítőben
description: A Power BI lapszámozott jelentéskészítőjével számos típusú lapszámozott jelentést készíthet. Hasznos és könnyen értelmezhető jelentések készítése előtt célszerű megtervezni azokat.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fd4a318d7a61f6f2298de6b9d5d23ad2ae063d28
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840510"
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
  
     Sometimes, your data source and datasets do not contain the exact fields that you need for your report. In that situation, you might have to create your own calculated fields. For example, you might want to multiply the price per unit times the quantity to get a line item sales amount. Expressions are also used to provide conditional formatting and other advanced features. For more information, see [Expressions in Power BI Report Builder](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>El szeretne rejteni bizonyos elemeket?
  
Fontolja meg, hogy a jelentés első futtatásakor érdemes-e bizonyos jelentésbeli tételeket elrejtenie, például adatrégiókat, vagy csoportokat és oszlopokat. Például elsőként bemutathat egy összefoglaló táblázatot, majd részletezheti annak adatait. 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>Hogyan fogja terjeszteni a jelentést?  
  
     You can save your report to your local computer and continue to work on it, or run it locally for your own information. However, to share your report with others, you need to save the report to Power BI. Saving it to Power BI lets others run it whenever they want to. Alternatively, you can set up a subscription and e-mail delivery of the report to other individuals. You can have the report delivered in a specific export format if you prefer. 
  
## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
