---
title: Excel-munkafüzetek importálása a Power BI Desktopba
description: Excel-munkafüzetek importálása a Power BI Desktopba
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b6b74682f1c74ab78f27be857dbec42efa29347
ms.sourcegitcommit: 2116af72f435cd30f1401bb9c7afdcbc76b1c3ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65454171"
---
# <a name="import-excel-workbooks-into-power-bi-desktop"></a>Excel-munkafüzetek importálása a Power BI Desktopba
A **Power BI Desktop** segítségével egyszerűen importálhatja a Power Query lekérdezéseket, Power Pivot modelleket és Power View munkalapokat tartalmazó Excel-munkafüzeteket a Power BI Desktopba. A jelentéseket és a vizualizációkat a rendszer automatikusan létrehozza az Excel-munkafüzet alapján, és ha importálta, tovább is fejlesztheti ezeket a jelentéseket a Power BI Desktoppal a meglévő szolgáltatások és a Power BI Desktop havi frissítéseivel megjelenő új szolgáltatások segítségével.

A tervek szerint a jövőben további kommunikációt alakítunk ki az Excel és a Power BI Desktop között (például importálás/exportálás). A jelenlegi képességgel, amellyel importálhatók munkafüzetek a Power BI Desktopba, az Excel-felhasználók elkezdhetnek ismerkedni a Power BI Desktoppal.

## <a name="how-do-i-import-an-excel-workbook"></a>Hogyan importálhatok egy Excel-munkafüzetet?
Egy munkafüzet importálásához válassza a Power BI Desktopban a **Fájl –\> Importálás –\> Excel-munkafüzet tartalma** lehetőséget.

![](media/desktop-import-excel-workbooks/importexceltopbi_1.png)

Megjelenik egy ablak, ahol kiválaszthatja az importálni kívánt munkafüzetet. Jelenleg nincs korlátozás érvényben a munkafüzet méretére vagy a benne található objektumok számára vonatkozóan, de a nagyobb munkafüzetek elemzése és importálása tovább tart a Power BI Desktop számára.

> [!NOTE]
> Ha a **megosztott OneDrive Vállalati verzió** mappáiból vagy az **Office 365 csoport** mappáiból szeretne Excel-fájlokat betölteni vagy importálni, használja az Excel-fájl URL-jét, és adja meg be a Power BI Desktop **webes** adatforrásában. Néhány lépést el kell végezni a **OneDrive Vállalati verzió** URL megfelelő formázásához, további információ és a lépések helyes sorrendje: [A OneDrive Vállalati verzió hivatkozásainak használata a Power BI Desktopban](desktop-use-onedrive-business-links.md).
> 
> 

Ha kiválasztott egy munkafüzetet, a Power BI Desktop elemzi a munkafüzetet, és egy Power BI Desktop-fájllá (.pbix) konvertálja. Ez egy egyszeri esemény. Ha ezen lépéseket követve létrejött a Power BI Desktop-fájl, a továbbiakban már független az eredeti Excel-munkafüzettől, módosíthatja (és mentheti, megoszthatja) anélkül, hogy az hatással lenne az eredeti munkafüzetre.

![](media/desktop-import-excel-workbooks/importexceltopbi_2.png)

Ha elkészült az importálással megjelenik egy **Összegzés** lap, amely ismerteti a konvertált elemeket, és felsorolja azokat az elemeket, amelyeket nem sikerült importálni.

![](media/desktop-import-excel-workbooks/importexceltopbi_3.png)

Ha a **Bezárás** gombra kattint, a jelentést a rendszer betölti a Power BI Desktopba. Az alábbi képen a Power BI Desktop látható, miután importálva lett egy Excel-munkafüzet: A Power BI Desktop a munkafüzet tartalma alapján automatikusan betöltötte a jelentést.

![](media/desktop-import-excel-workbooks/importexceltopbi_4.png)

Most, hogy importálta a munkafüzetet, folytathatja a munkát a jelentésen – létrehozhat új vizualizációkat, hozzáadhat adatokat, vagy létrehozhat új jelentésoldalakat. Ehhez a Power BI Desktop összes szolgáltatását és képességét használhatja.

## <a name="which-workbook-elements-are-imported"></a>A munkafüzet mely elemei importálhatók?
A Power BI Desktop az alábbi, az Excelben általában *objektumnak* nevezett elemeket képes importálni.

| Objektum az Excel-munkafüzetben | Végeredmény a Power BI Desktop-fájlban |
| --- | --- |
| Power Query lekérdezések |A rendszer az összes exceles Power Query lekérdezést Power BI Desktop lekérdezéssé konvertálja. Ha az Excel-munkafüzetben meg vannak határozva lekérdezéscsoportok, a Power BI Desktop replikálja ugyanezt a szerkezetet. A rendszer minden kapcsolatot betölt, kivéve azokat, amelyeknek „Csak kapcsolat létrehozás” beállítása van az Excelben. A betöltési viselkedés testreszabható a Power BI Desktop **Lekérdezésszerkesztőjének** **Kezdőlapján** a **Tulajdonságok** párbeszédablakban. |
| Power Pivot külső adatkapcsolatok |A rendszer az összes Power Pivot külső adatkapcsolatot Power BI Desktop lekérdezéssé konvertálja. |
| Hivatkozott táblák vagy a munkafüzet aktuális táblái |Ha az Excel egyik munkalaptáblája az Adatmodellhez vagy egy lekérdezéshez kapcsolódik (az M *Táblázatból* vagy *Excel.CurrentWorkbook()* függvénye használatával), az alábbi lehetőségek vannak: <ol><li>Importálhatja a táblát a Power BI Desktop-fájlba. Ez a táblázat egy egyszeri pillanatfelvétel az adatokról, ezután nem szerkesztheti a tábla adatait a Power BI Desktopban. Az ezzel a lehetőséggel létrehozott táblákra vonatkozik egy 1 millió karakteres korlátozás (a teljes karakterszámot tekintve, oszlopfejlécekkel és cellákkal együtt).</li><li>Megőrizheti az eredeti munkafüzettel létesített kapcsolatot. Egy másik megoldás, ha megtartja a kapcsolatot az eredeti Excel-munkafüzettel, és a Power BI Desktop minden frissítéssel lekéri ennek a táblának a legfrissebb tartalmát, mint minden más, a Power BI Desktopban egy Excel-munkafüzeten létrehozott lekérdezés esetében.</li></ul> |
| Adatmodell számított oszlopok, mértékek, KPI-k, adatkategóriák és kapcsolatok |Ezeket az adatmodell-objektumokat a rendszer a Power BI Desktop megfelelő objektumaivá konvertálja. Ügyeljen rá, hogy vannak olyan adatkategóriák, amelyek a Power BI Desktopban nem érhetők el, például a **Kép**. Ezekben az esetekben az Adatkategória információ alaphelyzetbe áll vissza a kérdéses oszlopoknál. |
| Power View-munkalapok |Az Excel minden Power View-munkalapjához létrejön egy új jelentésoldal. Ezen jelentésoldalak neve és sorrendje megfelel az eredeti Excel-munkafüzetben találhatónak. |

## <a name="are-there-any-limitations-to-importing-a-workbook"></a>Vonatkozik valamilyen korlátozás egy munkafüzet importálására?
Csak néhány korlátozás vonatkozik egy munkafüzet Power BI Desktopba való importálására, ezek a következők:

* **Külső kapcsolatok az Analysis Services táblázatos modelljéhez:** Az Excel 2013-ban kapcsolat hozható létre az SQL Server Analysis Services táblázatos modellekkel, és létrehozhatók Power View jelentések ezeken a modelleken anélkül, hogy importálni kellene az adatokat. Ez a típusú kapcsolat jelenleg nem támogatott az Excel-munkafüzetek Power BI Desktopba való importálásának részeként. Áthidaló megoldásként ezeket a külső kapcsolatokat újra létre kell hoznia a Power BI Desktopban.
* **Hierarchiák:** Ez a típusú adatmodell-objektum jelenleg nem támogatott a Power BI Desktopban. Ezért a rendszer kihagyja a hierarchiákat az Excel-munkafüzetek Power BI Desktopba való importálása során.
* **Bináris adatoszlopok:** Ez a típusú adatmodell-oszlop jelenleg nem támogatott a Power BI Desktopban. A bináris adatokat tartalmazó oszlopokat a rendszer eltávolítja a Power BI Desktopban kapott táblából.
* **Nem támogatott Power View-elemek:** A Power View néhány szolgáltatása a Power BI Desktopban nem érhető el. Ilyenek a témák és bizonyos típusú vizualizációk (pontdiagram lejátszási tengellyel, részletes elemzési viselkedések és hasonlók.). Ezek a nem támogatott vizualizációk *Nem támogatott vizualizáció* üzeneteket eredményeznek a Power BI Desktop jelentés megfelelő helyein. Ezek törölhetők vagy igény szerint újrakonfigurálhatók.
* **A Power Queryben a** ***Táblázatból*** **függvényt vagy az M-ben** ***Excel.CurrentWorkbook*** **függvényt használó névvel ellátott tartományok:** Ezeknek a névvel ellátott tartományoknak a Power BI Desktopba való importálása jelenleg nem támogatott, de a Power BI Desktop egyik tervezett frissítése tartalmazni fogja. Jelenleg a rendszer ezeket a névvel ellátott tartományokat egy külső Excel-munkafüzetre mutató kapcsolatként tölti be a Power BI Desktopba.
* **PowerPivot – SSRS:** Az SQL Server Reporting Services (SSRS) felé mutató PowerPivot külső kapcsolatok jelenleg nem támogatottak, mert az adatforrás jelenleg nem érhető el a Power BI Desktopban.

