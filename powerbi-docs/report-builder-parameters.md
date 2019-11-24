---
title: Jelentésparaméterek a Power BI Jelentéskészítőben
description: Ez a témakör sok más mellett a Power BI Lapszámozott jelentéskészítő jelentésparamétereinek gyakori használati módjait és a beállítható tulajdonságokat ismerteti.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/06/2019
ms.openlocfilehash: d31036676a5960f7f6eb0f346c2c02ab979ff9bc
ms.sourcegitcommit: 01de0b01f66f28ca45b8d309d7864f261d6c9a85
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/16/2019
ms.locfileid: "74128419"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Jelentésparaméterek a Power BI Jelentéskészítőben

Ez a témakör sok más mellett a Power BI Lapszámozott jelentéskészítő jelentésparamétereinek gyakori használati módjait és a beállítható tulajdonságokat ismerteti. Jelentésparaméterekkel szabályozhatja a jelentés adatait, összekötheti a kapcsolódó jelentéseket, és megváltoztathatja a jelentések bemutatásának módját. A Jelentéskészítőben létrehozott lapszámozott jelentésekben jelentésparamétereket használhat.

## <a name="bkmk_Common_Uses_for_Parameters"></a> A paraméterek gyakori felhasználási módjai

 Az alábbiakban a paraméterek használatának néhány leggyakoribb módját ismertetjük.  
  
**Lapszámozott jelentés adatinak szabályozása**
  
- A lapszámozott jelentés adatai az adatforrásnál szűrhetők változókat tartalmazó lekérdezések írásával.  
  
- A felhasználók értékeket adhatnak meg a lapszámozott jelentés adatainak testreszabásához. Két paraméterre megadható például az értékesítési adatok kezdő és záró dátuma.  
  
**A jelentés megjelenésének módosítása**
  
- A felhasználók a jelentés megjelenésének testreszabásában szerepet játszó értékeket adhatnak meg. Megadhatnak például egy logikai paramétert, amely az egymásba ágyazott sorcsoportok összecsukását vagy kibontását dönti el.  
  
- A felhasználók képletekbe foglalt paraméterekkel szabályozhatják egy jelentés adatait és megjelenését.  
  
## <a name="UserInterface"></a> Jelentés megtekintése paraméterekkel

Paraméterekkel rendelkező jelentés megtekintésekor a jelentésmegjelenítő eszközsávján minden paraméter megjelenik, így értékük interaktív módon állítható be. Az alábbi ábrán egy jelentés paraméterterülete látható a @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota és @SalesDate paraméterekkel.  

![Paraméterekkel rendelkező jelentés megtekintése](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Paraméterekkel rendelkező jelentés megtekintése")
  
1. **Paraméterek panel** – A jelentésmegjelenítő eszköztáron minden paraméterhez megjelenik egy beviteli mező az alapértelmezett értékkel. A paraméterek elrendezését a Paraméterek panelen szabhatja testre.  
  
2. **@SalesDate paraméter** – A @SalesDate paraméter adattípusa **Dátum/Idő**. A beviteli mező melletti felirat: Válassza ki a dátumot. A dátum módosításához gépeljen be új dátumot a szövegmezőbe, vagy használja a Naptár vezérlőt.  
  
3. **@ShowAll paraméter** – A @ShowAll paraméter adattípusa **logikai**. A választógombok használatával **Igaz** vagy **Hamis** értékre állítható be.  
  
4. **Fogópont a paraméterterület megjelenítéséhez vagy elrejtéséhez** A jelentésmegjelenítő eszköztáron erre a nyílra kattintva elrejtheti vagy megjelenítheti a Paraméterek panelt.  
  
5. **@CategoryQuota paraméter** – A @CategoryQuota paraméter adattípusa **lebegőpontos**, tehát numerikus értéket fogad el.  A @CategoryQuota úgy van beállítva, hogy több értéket is elfogad.  
  
6. **Jelentés megtekintése** – A paraméterértékek bevitele után kattintson a **Jelentés megtekintése** gombra a jelentés futtatásához. Ha minden paraméter rendelkezik alapértelmezett értékkel, a jelentés automatikusan lefut az első megtekintésekor.  
  
## <a name="bkmk_Create_Parameters"></a> Paraméterek létrehozása

Jelentésparamétereket több módon is létrehozhat.
  
> [!NOTE]
>  Nem minden adatforrás támogatja a paramétereket.
  
**Adathalmaz-lekérdezés vagy tárolt eljárás paraméterekkel**
  
 Hozzáadhat változókat tartalmazó adathalmaz-lekérdezést, vagy az adathalmazbeli tárolt eljárást, amely bemeneti paramétereket tartalmaz. Minden változóhoz vagy bemeneti paraméterhez adathalmaz-paraméter lesz létrehozva, és minden adathalmaz-paraméterhez jelentésparaméter lesz létrehozva.  
  
![Jelentéskészítő paraméter-adathalmaz tulajdonságai](media/report-builder-parameters/report-builder-parameter-dataset.png "Jelentéskészítő paraméter-adathalmaz tulajdonságai")

  
 A Jelentéskészítő fenti képernyőképén a következők láthatók:  
  
1.  A jelentés paraméterei a Jelentésadatok panelen.  
  
2.  Az adathalmaz a paraméterekkel.  
  
3.  A Paraméterek panel.  
  
4.  Az Adathalmaz tulajdonságai párbeszédpanelen felsorolt paraméterek.  
  
**Paraméter manuális létrehozása**
  
Manuálisan hozhat létre paramétert a Jelentésadatok panelről. A jelentésparamétereket konfigurálhatja úgy, hogy a felhasználók interaktív módon adhassanak meg értékeket a jelentés tartalmának vagy megjelenésének testreszabására. A jelentésparaméterek úgy is konfigurálhatók, hogy a felhasználók ne módosíthassák az előre konfigurált értékeket.  
  
> [!NOTE]  
>  Mivel a paraméterek a kiszolgálón egymástól függetlenül vannak kezelve, a fő jelentés új paraméterbeállításokkal való ismételt közzététele nem írja felül a jelentés meglévő paramétereit.  

### <a name="parameter-values"></a>Paraméterértékek

 A paraméterek kiválasztása a jelentésben történhet az alábbi módokon.  
  
- Egyetlen paraméter választható egy legördülő listából.  
  
- Több paraméter választható egy legördülő listából.  
  
- Egy paraméter értéke kiválasztható egy legördülő listából, ez pedig meghatározza, hogy mely értékek jelenjenek meg egy másik paraméter legördülő listájában. Ezek a paraméterek egymásra épülnek. Egymásra épülő paraméterekkel a paraméterértékek több lépésben szűrhetők, így több ezer érték kezelhető mennyiségre szűkíthető.  
  
- A jelentés paraméterérték előzetes kiválasztása nélkül futtatható, mert a paraméterhez létre lett hozva egy alapértelmezett érték.  
  
## <a name="bkmk_Report_Parameters"></a> Jelentésparaméter tulajdonságai

 A jelentésparaméter tulajdonságait a Jelentés tulajdonságai párbeszédpanelen módosíthatja. Az alábbi táblázat az egyes paraméterekhez beállítható tulajdonságokat foglalja össze:  
  
|Tulajdonság|Leírás|  
|--------------|-----------------|  
|Név|Begépelheti a paraméter kis- és nagybetűket megkülönböztető nevét. A névnek betűvel kell kezdődnie, és betűkből, számokból és aláhúzásjelekből (_) állhat. A név nem tartalmazhat szóközt. Automatikusan generált paraméterek esetén a név az adathalmaz-lekérdezésbeli paraméterével egyezik. A manuálisan létrehozott paraméterek alapértelmezett neve a JelentesParameter1 mintához hasonló.|  
|Rákérdezés|A jelentésmegjelenítő eszköztáron a paraméter mellett megjelenő szöveg.|  
|Adattípus|A jelentésparaméterek adattípusának az alábbiak egyikének kell lennie:<br /><br /> **Logikai**. A felhasználó választógombbal adhat meg Igaz vagy Hamis értéket.<br /><br /> **Dátum/idő**. A felhasználó egy Naptár vezérlőelemből választhat ki egy dátumot.<br /><br /> **Egész**. A felhasználó egy szövegmezőbe gépelheti be az értéket.<br /><br /> **Lebegőpontos**. A felhasználó egy szövegmezőbe gépelheti be az értéket.<br /><br /> **Szöveg**. A felhasználó egy szövegmezőbe gépelheti be az értéket.<br /><br /> Ha egy paraméterhez meg vannak adva a használható értékek, akkor a felhasználó legördülő listából választ értékeket, még **Dátum/idő** típusú adatok esetén is.|  
|Üres érték engedélyezése|Ezt a lehetőséget akkor válassza, ha a paraméter értéke üres sztring, vagy kitöltetlen is lehet.<br /><br /> Ha megadja egy paraméter elérhető értékeit, és azt szeretné, hogy a kitöltetlen érték is használható legyen, akkor azt is bele kell foglalnia a megadott értékek egyikeként. Ennek a beállításnak a választása nem teszi automatikusan elérhetővé a kitöltetlen értéket.|  
|Null érték engedélyezés|Válassza ezt a lehetőséget, ha a paraméter értéke NULL is lehet.<br /><br /> Ha megadja egy paraméter elérhető értékeit, és azt szeretné, hogy a null érték is használható legyen, akkor azt is bele kell foglalnia a megadott értékek egyikeként. Ennek a beállításnak a választása nem teszi automatikusan elérhetővé a null értéket.|  
|Több érték engedélyezése|Az elérhető értékek megadásával legördülő listát hozhat létre, amelyből a felhasználók választhatnak. Ez jó módszer annak biztosítására, hogy az adathalmaz-lekérdezésnek csak érvényes értékek legyenek átadva.<br /><br /> Ezt a lehetőséget akkor válassza, ha a paraméternek több értéke is lehet, amelyek egy legördülő listában jelennek meg. A null érték nem megengedett. Ha ezt a lehetőséget választja, jelölőnégyzetek jelennek meg az elérhető értékek mellett a paraméter legördülő listájában. A lista elején külön jelölőnégyzet szolgál az **Összes kijelölésére**. A felhasználók bejelölhetik a kívánt értékeket.<br /><br /> Ha az értékeket biztosító adatok gyorsan változnak, akkor a felhasználónál megjelenő lista esetleg nem aktuális.|  
|Látható|Ha ezt a beállítást választja, a jelentés paramétere megjelenik a futó jelentés felső részén. Ez lehetővé teszi a felhasználók számára, hogy futás közben válasszanak paraméterértékeket.|  
|Rejtett|Ezzel a beállítással elrejtheti a jelentésparamétert a közzétett jelentésben. A jelentésparaméter értékei továbbra is beállíthatók a jelentés URL-címében, egy feliratkozás definíciójában vagy a jelentéskészítő kiszolgálón.|  
|Belső|Ezzel a beállítással elrejtheti a jelentésparamétert. A jelentésparaméter a közzétett jelentésben csak a jelentésdefinícióban lesz megtekinthető.|  
|Elérhető értékek|Ha megadta egy paraméter elérhető értékeit, akkor az érvényes értékek mindig legördülő listaként jelennek meg. Ha például egy **Dátum/idő** típusú paraméterhez ad meg értékeket, a paraméterpanelen Naptár vezérlőelem helyett dátumokból álló legördülő lista jelenik meg.<br /><br /> Annak érdekében, hogy az értékek listája egységes legyen a jelentésben és a segédjelentésekben, az adatforráson beállítható, hogy egyetlen tranzakciót használjon az adatforrással társított adathalmazok összes lekérdezéséhez.<br /><br /> **Biztonsági megjegyzés**: A **Szöveg** típusú paramétert tartalmazó jelentéseknél mindig az elérhető értékek (érvényes értékek) listáját használja, hogy a jelentést futtató felhasználók biztosan csak a jelentésbeli adatok megtekintéséhez szükséges engedélyekkel rendelkezzenek.|  
|Alapértelmezett értékek|Alapértelmezett értékeket lekérdezésből vagy statikus listából is beállíthat.<br /><br /> Ha minden paraméternek van alapértelmezett értéke, a jelentés automatikusan lefut az első megtekintésekor.|  
|Speciális|Beállíthatja a **UsedInQuery** jelentésdefiníciós attribútumot, amelynek értéke azt jelzi, hogy ez a paraméter érinti-e közvetlenül vagy közvetve a jelentésbeli adatokat.<br /><br /> **Frissítés időpontjának automatikus meghatározása**<br /> Ezt a beállítást akkor válassza, ha azt szeretné, hogy ennek az értéknek a beállítását a jelentés feldolgozója határozza meg. Az érték **Igaz** lesz, ha a jelentésfeldolgozó erre a paraméterre közvetlenül vagy közvetetten hivatkozó adathalmaz-lekérdezést észlel, vagy ha a jelentéshez segédjelentések tartoznak.<br /><br /> **Mindig frissít**<br /> Válassza ezt a beállítást, ha a jelentésparaméter közvetlenül vagy közvetve használva van egy adathalmaz-lekérdezésben vagy paraméteres kifejezésben. Ez a beállítás a **UsedInQuery** értékét Igazra állítja.<br /><br /> **Soha nem frissít**<br /> Válassza ezt a beállítást, ha a jelentésparaméter nincs közvetlenül vagy közvetve adathalmaz-lekérdezésben vagy paraméteres kifejezésben használva. Ez a beállítás a **UsedInQuery** értékét Hamisra állítja.<br /><br /> **Figyelmeztetés**: A **Soha nem frissít** beállítást körültekintően használja. A jelentéskészítő kiszolgálón a **UsedInQuery** a jelentésadatok és a megjelenítésre alkalmas jelentések gyorsítótárazási beállításainak, valamint a jelentés-pillanatképek paraméterbeállításainak szabályozásához van felhasználva. A **Soha nem frissít** helytelen beállítása nem megfelelő jelentésadatok vagy jelentések gyorsítótárazásához vezethet, vagy azt okozhatja, hogy a jelentés-pillanatképek következetlen adatokat tartalmaznak. |  
  
##  <a name="bkmk_Dataset_Parameters"></a> Adathalmaz-lekérdezés  
 Az adathalmaz-lekérdezésbeli adatok szűrésére korlátozó záradékot használhat, amely az eredményhalmazba belefoglalandó, vagy abból kizárandó értékek megadásával korlátozza a visszaadott adatokat.  
  
 Paraméteres lekérdezést az adatforrás lekérdezéstervezőjének segítségével készíthet.  
  
-   Transact-SQL lekérdezések esetén a különböző adatforrások különböző paraméterezési szintaxisokat támogatnak. Ezek köre a lekérdezésbeli helyük alapján azonosított paraméterektől a név szerintiekig terjed. A relációs lekérdezéstervezőben egy paraméteres lekérdezés létrehozásához egy szűrőt paraméteresnek kell beállítania.   
  
-   Többdimenziós adatforráson, például Microsoft SQL Server Analysis Servicesen alapuló lekérdezésekhez megadhatja, hogy létre legyen-e hozva paraméter egy lekérdezéstervezőben megadott szűrő alapján. 
  
##  <a name="bkmk_Manage_Parameters"></a> Közzétett jelentés paramétereinek kezelése  
 Jelentés tervezésekor a jelentésparaméterek a jelentésdefinícióba lesznek mentve. Jelentés közzétételekor a jelentésparaméterek a jelentésdefiníciótól külön vannak mentve és kezelve.  
  
 Közzétett jelentés esetén a következőket használhatja:  
  
-   **Jelentésparaméter tulajdonságai.** A jelentésparaméterek értékei közvetlenül a jelentéskészítő kiszolgálón, a jelentésdefiníciótól függetlenül módosíthatók.  
  
-   **Jelentés-feliratkozások.** Az adatok szűréséhez és a jelentések kézbesítéséhez feliratkozáson keresztül is megadhat paraméterértékeket. 
  
 A közzétett jelentések paraméter-tulajdonságai a jelentésdefiníció újbóli közzétételekor megmaradnak. Ha a jelentésdefiníció ugyanazon jelentésként van újra közzétéve, és a paraméterek nevei és adattípusai ugyanazok maradnak, akkor a tulajdonságok beállításai meg lesznek tartva. Ha a jelentésdefinícióban paramétereket ad hozzá vagy töröl, vagy módosítja egy meglévő paraméter nevét vagy adattípusát, akkor szükséges lehet a közzétett jelentés paramétertulajdonságainak módosítása.  
  
 Nem minden paraméter módosítható minden esetben. Ha egy jelentésparaméter egy adathalmaz-lekérdezésből kap alapértelmezett értéket, akkor ez az érték a közzétett jelentésben és a jelentéskészítő kiszolgálón sem módosítható. A futtatás során használt érték a lekérdezés futásakor, kifejezésalapú paraméter esetén pedig a kifejezés kiértékelésekor lesz meghatározva.  
  
 A paraméterek feldolgozásának módját a jelentés végrehajtási beállításai is befolyásolhatják. Pillanatképként futó jelentések csak akkor használhatnak lekérdezésből származó paramétereket, ha a lekérdezés alapértelmezett értékeket is tartalmaz a paraméterekhez.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Feliratkozás paraméterei  
 Igény szerinti vagy pillanatkép-jelentéshez feliratkozást definiálhat, és megadhat a feliratkozás feldolgozása során használandó paramétereket.  
  
-   **Igény szerinti jelentés.**  Igény szerinti jelentés esetén a jelentéshez felsorolt összes paraméterhez megadhat a közzétett értéktől különböző paraméterértéket. Tegyük fel például, hogy egy telefonos ügyfélszolgálati jelentés az *Időszak* paraméter használatával adja vissza az aktuális nap, hét vagy hónap ügyfélszolgálati kéréseit. Ha a jelentés paraméternek alapértelmezett értékeként **ma** van beállítva, a feliratkozás más paraméterérték (például **hét** vagy **hónap**) használatával állíthat elő a heti vagy havi adatokat tartalmazó jelentést.  
  
## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)  
 
 
