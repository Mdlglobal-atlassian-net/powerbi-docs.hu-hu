---
title: Jelentésadatok a Power BI Jelentéskészítőben
description: Ha jelentést készít a Power BI Jelentéskészítőjében, első lépésként a jelentésadatokat képviselő adatforrásokat és adatkészleteket kell létrehoznia.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: f8f7d3b43cfc2d5a51b686598c1657ec21b44130
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527269"
---
# <a name="report-data-in-power-bi-report-builder"></a>Jelentésadatok a Power BI Jelentéskészítőben

A jelentésadatok számos szervezeti adatforrásból származhatnak. Ha jelentést készít a Power BI jelentéskészítőjében, első lépésként a jelentésadatokat képviselő adatforrásokat és adatkészleteket kell létrehoznia. Minden adatforrás adatkapcsolati adatokat tartalmaz. Minden adatkészlet tartalmaz egy lekérdezési parancsot, amely meghatározza az adatforrás adatként használandó mezőit. Az adatkészletek adatainak megjelenítéséhez adjon hozzá egy adatterületet, például egy táblázatot, mátrixot, diagramot vagy térképet. A jelentés feldolgozása után a lekérdezések lefutnak az adatforráson, az adatterületek pedig szükség szerint kiterjednek és megjelenítik az adatkészlet lekérdezési eredményeit.  

Megtudhatja, hogyan [hozhat létre beágyazott adatforrást lapszámozott jelentésekhez a Power BI jelentéskészítőjében](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Feltételek  
  
- **Adatkapcsolat.** Más néven *adatforrás*. Az adatkapcsolat egy nevet és a kapcsolat típusától függő kapcsolati tulajdonságot tartalmazza. Kialakításából fakadóan az adatkapcsolat nem tartalmaz hitelesítő adatokat. Az adatkapcsolat nem szabja meg, hogy milyen adatokat kérjen le a külső adatforrásból. Ehhez egy lekérdezést kell megadni az adatkészlet létrehozásakor.  
  
- **Kapcsolati sztring.** Kapcsolati sztring az adatforráshoz való csatlakozáshoz szükséges kapcsolati tulajdonságok karakterláncos verziója. A kapcsolati tulajdonságok adatkapcsolati típusonként különböznek.  
  
- **Beágyazott adatforrás.** Más néven *jelentésspecifikus adatforrás*. Egy, a jelentésben definiált adatforrás, amelyet csak az a jelentés használ.  
  
- **Hitelesítő adatok.** A hitelesítő adatok olyan információk, amelyeket meg kell adni a külső adatok eléréséhez.  
  
##  <a name="BkMk_ReportDataTips"></a> Tippek a jelentés adatainak megadásához

 A jelentésadatokra vonatkozó stratégiát a következő útmutatás segítségével alakítsa ki.  
  
- **Adatok szűrése** A jelentésadatok szűrhetők a lekérdezésben vagy a jelentésben. Adatkészletekkel és lekérdezési változókkal létrehozhat egymásra épülő paramétereket, valamint engedélyezheti a felhasználóknak, hogy több ezer kijelölés közül kevesebb elemre szűkítsék a lehetőségek számát. A táblázatok vagy diagramok adatait paraméterértékek vagy egyéb megadott értékek alapján szűrheti.  
  
- **Parameters** Az adatkészlet azon lekérdezési parancsai, amik lekérdezési változókat tartalmaznak, automatikusan létrehoznak egyező jelentésparamétereket. Paraméterek manuálisan is létrehozhatók. Egy jelentés megtekintésekor a jelentés eszköztára megjeleníti a paramétereket. A felhasználók értékek kijelölésével vezérelhetik a jelentésadatokat vagy a jelentés megjelenését. Ha adott közönségek számára szeretné testreszabni a jelentésadatokat, jelentésparaméter-készleteket hozhat létre, amelyekben különböző alapértelmezett értékeket kapcsol ugyanazon jelentésdefinícióhoz, vagy használhatja a beépített **UserID** mezőt. 
  
- **Adatok csoportosítása és összesítése** A jelentésadatok csoportosíthatók és összesíthetők a lekérdezésben vagy a jelentésben. Ha egy lekérdezés értékeit összesíti, a jelentéssel bíró értékeket tovább egyesítheti a jelentésben.  
  
- **Adatok rendezése** A jelentésadatok rendezhetők a lekérdezésben vagy a jelentésben. Táblázatokban egy interaktív rendezőgombot is elhelyezhet, amellyel a felhasználók szabályozhatják a rendezési sorrendet.  
  
- **Kifejezésen alapuló adatok** Mivel a legtöbb tulajdonság kifejezésen alapul, a kifejezések pedig tartalmazhatnak adatkészletek mezőire és jelentésparaméterekre mutató hivatkozásokat, Ön hatékony kifejezéseket készíthet, amelyekkel a jelentés adatait és megjelenését szabályozhatja. Engedélyezheti a felhasználók számára, hogy vezéreljék a megjelenő adatokat a paraméterek definiálásával.  
  
- **Adatok megjelenítése egy adatkészletből** Az adatkészletek adatai általában egy vagy több adatterületen jelennek meg, például egy táblázatban és egy diagramon.  
  
- **Adatok megjelenítése több adatkészletből**  Egy adatterületen egy értékeket kereső vagy más adatkészleteket összesítő adatkészleten alapuló kifejezéseket írhat. Egy adatkészleten alapuló táblázatban segédjelentéseket adhat meg, amelyek egy másik adatforrás adatait jelenítik meg.  
  
 Az alábbi lista segítségével meghatározhatja egy jelentés adatforrásait.  
  
- A szervezeti szoftveres adatréteg-architektúra megértése és az adattípusok potenciális problémái. Az adatbővítmények és az adatfeldolgozási bővítmények a lekérdezési eredményekre gyakorolt hatásának megértése. Az adattípusok eltérnek a különböző adatforrások, adatszolgáltatók és a jelentésdefiníció (.rdl) fájljában tárolt adattípusok között.  
  
- Az adatforrásokat és adatkészleteket a jelentésen belül hozzák létre, majd teszik közzé a Power BI szolgáltatásban. A közzététel után a hitelesítő adatok közvetlenül a Power BI szolgáltatásban vagy a vállalati átjáróban konfigurálhatók. 

## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)  
- [Adatlekérési útmutató lapszámozott jelentésekhez](guidance/report-paginated-data-retrieval.md)
