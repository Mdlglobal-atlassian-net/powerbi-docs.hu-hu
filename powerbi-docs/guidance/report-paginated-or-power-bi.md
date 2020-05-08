---
title: Többoldalas jelentések használata a Power BI-ban
description: Útmutató többoldalas Power BI-jelentések használatát indokló helyzetekhez.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 049b6ac14c6d35d68815eac32520a4eaa654ad42
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920741"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Többoldalas jelentések használata a Power BI-ban

Ez a cikk a Power BI-hoz jelentéseket tervező jelentéskészítőknek szól. Javaslatokat kínál annak eldöntéséhez, hogy mikor érdemes [többoldalas Power BI-jelentést](../paginated-reports/paginated-reports-report-builder-power-bi.md) készíteni.

> [!NOTE]
> A többoldalas Power BI-jelentések közzétételéhez Power BI Premium-előfizetés szükséges. A jelentések csak akkor lesznek renderelve, ha olyan dedikált kapacitásban lévő munkaterületen vannak, amelyen [engedélyezve van a Többoldalas jelentések számítási feladat](../service-admin-premium-workloads.md#paginated-reports).

A Power BI többoldalas jelentései általában **nyomtatáshoz** vagy **PDF-létrehozáshoz** vannak optimalizálva. Lehetőséget biztosítanak aprólékosan formázott, gondosan kivitelezett elrendezések kialakítására is. A többoldalas jelentések ezáltal ideálisak az olyan üzemeltetési jelentésekhez, mint az értékesítési számlák.

A Power BI-jelentések ezzel szemben **áttekinthetőségre és kezelhetőségre** vannak optimalizálva. Arra is alkalmasak, hogy a legmodernebb vizualizációk széles választékával szemléltessék az adatokat. A Power BI-jelentések tehát elemzési jelentésekhez ideálisak, lehetővé téve a felhasználóknak az adatok feltárását, összefüggések és mintázatok felderítését.

A többoldalas Power BI-jelentések használatát a következő helyzetekben érdemes mérlegelni:

- Tudja, hogy a jelentést ki kell nyomtatni, vagy PDF-kimenetet kell előállítani belőle.
- Az adatrács-elrendezések terjeszkedhetnek és túlnőhetnek a korlátokon. Mint tudja, egy Power BI-jelentésbeli táblázat vagy mátrix nem méreteződik át dinamikusan az összes adat megjelenítéséhez, ehelyett görgetősávokat jelenít meg. Nyomtatásban azonban nem lehet görgetéssel felfedni a nézeten kívüli adatokat.
- Előnyösnek bizonyulnak a Power BI többoldalas funkciói és képességei. A cikk egy későbbi része sok ilyen jelentéskészítési helyzetet bemutat.

## <a name="legacy-reports"></a>Örökölt jelentések

Ha már rendelkezik az SQL Server Reporting Services (SSRS) [Report Definition Language (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) nyelvű jelentéseivel, újra elkészítheti azokat [Power BI-jelentésekként](../consumer/end-user-reports.md), vagy többoldalas jelentésekként migrálhatja őket a Power BI-ba. További információ: [SQL Server Reporting Services-jelentések migrálása a Power BI-ba](migrate-ssrs-reports-to-power-bi.md).

Az egy Power BI-munkaterületen történt közzététel után a többoldalas jelentések is rendelkezésre állnak a Power BI-jelentések mellett. Ez után egyszerűen terjeszthetők [Power BI-alkalmazások](../service-create-distribute-apps.md) segítségével.

Az SSRS-jelentések migrálása helyett érdemesebb lehet azokat újra elkészíteni. Ez különösen azokra a jelentésekre igaz, amelyeket elemzési felületre szánnak. Ilyen esetekben valószínűleg a Power BI-jelentések biztosítanak jobb felhasználó felületet.

## <a name="paginated-report-scenarios"></a>Többoldalas jelentések felhasználási helyzetei

Sok olyan helyzet van, amelyben nyomós érvek szólnak egy többoldalas Power BI-jelentést készítése mellett. Ezek sokszor a Power BI-jelentések által nem támogatott funkciók vagy képességek.

- **Nyomtatásra kész**: A többoldalas jelentések nyomtatáshoz vagy PDF-létrehozáshoz vannak optimalizálva. Szükség esetén a terjeszkedő adatterületek szabályozott módon nyúlnak át más oldalakra. A jelentés elrendezésében meghatározhatók a margók, valamint az oldalfejlécek és -láblécek.
- **Renderelési formátumok**: A Power BI többféle formátumban képes renderelni a többoldalas jelentéseket. Ilyen formátumok többek között a következők: Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML és MHTML. (Az MHTML formátumot a Power BI szolgáltatás használja a jelentések renderelésére.) A jelentések felhasználói választhatják ki az igényeiknek megfelelő exportálási formátumot.
- **Precíz elrendezés**: Részletesen megformázott, képpont-szinten pontos elrendezéseket tervezhet, a centiméter törtrészeiben konfigurált pontos méretezéssel és elhelyezéssel.
- **Dinamikus elrendezés**: Rendkívül rugalmas elrendezéseket hozhat létre a VB.NET-kifejezéseket használó számos jelentéstulajdonság beállításával. A kifejezések a .NET-keretrendszer sok alapvető kódtárához hozzáférnek.
- **Renderelés-specifikus elrendezés**: Kifejezések használatával a jelentés elrendezése az alkalmazott renderelési formátumnak megfelelően módosítható. Tervezhet például olyan jelentést, amely letiltja a láthatóság ki-bekapcsolását (lefúrás vagy felhatolás megvalósításához), ha nem interaktív formátumban, például PDF-fájlként van renderelve.
- **Natív lekérdezések**: Nem kell előre Power BI-adathalmazt fejlesztenie. Bármely [támogatott adatforráshoz](../paginated-reports/paginated-reports-data-sources.md) írhat natív lekérdezéseket (vagy használhat tárolt eljárásokat). A lekérdezések paraméterezéseket is tartalmazhatnak.
- **Grafikus lekérdezéstervezők**: A Power BI jelentéskészítőjéhez grafikus lekérdezéstervezők is tartoznak, amelyek segítenek az adathalmazok lekérdezéseinek megírásában és tesztelésében.
- **Statikus adathalmazok**: Definiálhat egy adathalmazt, és az adatokat közvetlenül a jelentés definíciójában adhatja meg. Ez a képesség különösen hasznos bemutatók támogatásához, vagy megvalósíthatósági vizsgálatok elvégzéséhez.
- **Adatintegráció**: Kombinálhatja a különböző adatforrásokból vagy statikus adathalmazokból származó adatokat. Ezt VB.NET-kifejezéseket használó egyéni mezők létrehozásával teheti meg.
- **Paraméterezés**: Nagy mértékben testreszabható paraméterezési felületeket tervezhet, akár adatvezérelt és egymásra épülő paraméterekkel is. A paraméterek alapértelmezett értékei is meghatározhatók. Ilyen felületek megtervezésével segíthet a jelentés felhasználóinak a megfelelő szűrők gyors beállításában. A paramétereknek nem is kell a jelentés adatait szűrniük. Felhasználhatók feltételes helyzetek támogatására, vagy dinamikus szűrésre vagy stílus-beállításra.
- **Képadatok**: A jelentés képes képeket renderelni, ha azok bináris formátumban vannak tárolva az adatforrásban.
- **Egyéni kód**: VB.NET-függvényekből álló kódblokkokat fejleszthet és használhat bármely jelentésbeli kifejezésben.
- **Segédjelentések**: A jelentésbe más többoldalas Power BI-jelentéseket is beágyazhat (ugyanarról a munkaterületről).
- **Rugalmas adatrácsok**: A rácsos adatrégió használatával részletesen szabályozhatja a rácsos elrendezéseket. Ez az összetett elrendezéseket, köztük a beágyazott és szomszédos csoportokat is támogatja. Úgy is konfigurálható, hogy ha több oldalra van kinyomtatva, ismételje a jelentés fejlécét. Segédjelentést vagy más vizualizációt, például adatsávokat, értékgörbéket és kijelzőket is beágyazhat.
- **Térbeli adattípusok**: A térkép adatterület képes az [SQL Server térbeli adattípusainak](/sql/relational-databases/spatial/spatial-data-sql-server) megjelenítésére. Ennek köszönhetően a GEOGRAPHY és a GEOMETRY adattípus is használható pontok, vonalak vagy sokszögek megjelenítésére. ESRI-alakzatfájlokban definiált sokszögek is megjeleníthetők.
- **Modern kijelzők**: A KPI-értékek és -állapotok megjelenítésére tárcsák és lineáris kijelzők is használhatók. Ezek akár rácsos adatrégiókba is beágyazhatók, a csoportokban ismétlődve.
- **HTML-renderelés**: Részletesen formázott szöveget jeleníthet meg, ha az HTML-ként van tárolva.
- **Körlevél**: Helyőrző szövegmezők használatával szúrhat be adatokat egy szövegbe. Ezen a módon körlevél-jelentést hozhat létre.
- **Interaktivitási funkciók**: Az interaktivitási funkciók közé tartozik a láthatóság ki-bekapcsolása (lefúráshoz vagy felhatoláshoz), a hivatkozások, az interaktív rendezés és az elemleírások. Olyan hivatkozásokat is megadhat, amelyek Power BI-jelentések vagy más többoldalas Power BI-jelentések részletezésére mutatnak. A hivatkozások mutathatnak akár egy másik helyre is ugyanazon jelentésen belül.
- **Előfizetések**: A Power BI képes ütemezett e-mailekként kézbesíteni a többoldalas jelentéseket, a támogatott formátumú mellékletekkel.
- **Felhasználóra szabott elrendezés**: Készíthet rugalmas elrendezést a jelentést megnyitó hitelesített felhasználó alapján. A jelentést megtervezheti úgy, hogy másként szűrje az adatokat, adatterületeket vagy vizualizációkat rejtsen el, más formátumokat alkalmazzon, vagy felhasználóspecifikus alapértelmezéseket állítson be a paraméterekhez.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Mik a lapszámozott jelentések a Power BI Premiumban?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [SQL Server Reporting Services-jelentések migrálása a Power BI-ba](migrate-ssrs-reports-to-power-bi.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
