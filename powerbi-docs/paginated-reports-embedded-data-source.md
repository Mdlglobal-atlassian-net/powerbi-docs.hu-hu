---
title: Beágyazott adatforrások lapszámozott jelentésekhez a Power BI szolgáltatásban
description: Ebből a cikkből beágyazott adatforrások lapszámozott jelentésekben való létrehozását és módosítását sajátíthatja el a Power BI szolgáltatásban.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 06/06/2019
ms.openlocfilehash: 83e3ffbae43d25e89cf52077acaa731cdee9b502
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68270825"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Beágyazott adatforrás létrehozása lapszámozott jelentésekhez a Power BI szolgáltatásban

Ebből a cikkből beágyazott adatforrások lapszámozott jelentésekhez való létrehozását és módosítását sajátíthatja el a Power BI szolgáltatásban. Beágyazott adatforrást egyetlen jelentéshez definiálhat, és csak ebben a jelentésben használhatja fel. A Power BI szolgáltatásban közzétett lapszámozott jelentések jelenleg beágyazott adathalmazokat és beágyazott adatforrásokat igényelnek, és a következő adatforrásokhoz kapcsolódhatnak:

- Azure Analysis Services
- Azure SQL Database és 
- Azure SQL Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

A következő adatforrások esetében használja az [SQL Server Analysis Services-kapcsolat](service-premium-connect-tools.md) lehetőséget:

- Power BI Premium-adatkészletek

A lapszámozott jelentések átjárón keresztül kapcsolódnak a [Power BI-átjáróhoz](service-gateway-onprem.md). Az átjárót azután állíthatja be, hogy a jelentést közzéteszi a Power BI szolgáltatásban.

További információ: [Jelentésadatok a Power BI Jelentéskészítőben](report-builder-data.md).

## <a name="create-an-embedded-data-source"></a>Beágyazott adatforrás létrehozása
  
1. Nyissa meg a Power BI Jelentéskészítőt.

1. A Jelentésadatok panel eszköztárán válassza az **Új** > **Adatforrás** lehetőséget. Ekkor megnyílik az **Adatforrás tulajdonságai** párbeszédpanel.

    ![Új adatforrás](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
2.  A **Név** szövegmezőbe írja be az adatforrás nevét, vagy fogadja el az alapértelmezett nevet.  
  
3.  Válassza **A jelentésbe ágyazott kapcsolat használata** lehetőséget.  
  
1.  A **Kapcsolattípus kiválasztása** listában válassza ki az adatforrás típusát. 

1.  Adjon meg egy kapcsolati sztringet az alábbi módszerek egyikével:  
  
    -   Gépelje be a kapcsolati sztringet közvetlenül a **Kapcsolati sztring** szövegmezőbe. 
  
    -   Válassza a kifejezésgombot (**fx**) egy olyan kifejezés létrehozásához, amelynek kiértékelése megadja a kapcsolati sztringet. A Kifejezés párbeszédablakban írja be a kifejezést a **Kifejezés** mezőbe. Kattintson az **OK** gombra. 
  
    -   Válassza a **Build** lehetőséget a 2. lépésben választott adatforráshoz tartozó **Kapcsolat tulajdonságai** párbeszédablak megnyitásához.  
  
        Töltse ki a **Kapcsolat tulajdonságai** párbeszédablak mezőit az adatforrás típusának megfelelően. A kapcsolat tulajdonságai közé tartozik az adatforrás típusa, az adatforrás neve és a használni kívánt hitelesítő adatok. Miután megadta az értékeket ebben a párbeszédablakban, a **Kapcsolat tesztelése** lehetőséggel ellenőrizze, hogy az adatforrás elérhető-e, és a megadott hitelesítő adatok helyesek-e.  
  
4.  Válassza a **Hitelesítő adatok** lehetőséget.  
  
     Adja meg az ehhez az adatforráshoz használni kívánt hitelesítő adatokat. A támogatott hitelesítőadat-típusokat az adatforrás tulajdonosa határozza meg. További információt a [Hitelesítő adatok és kapcsolati adatok megadása jelentésadat-forrásokhoz](https://docs.microsoft.com/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources) című cikkben talál.
  
5.  Kattintson az **OK** gombra.  
  
     Az adatforrás megjelenik a Jelentésadatok panelen.  
     
## <a name="limitations-and-considerations"></a>Korlátozások és megfontolandó szempontok

A Power BI-adatkészletekhez csatlakozó többoldalas jelentések kisebb eltérésektől eltekintve ugyanazokat a szabályokat követik, mint amelyek a Power BI-beli megosztott adatkészletekre vonatkoznak.  Annak érdekében, hogy a felhasználók megfelelően tudják megtekinteni a Power BI-adatkészleteket használó többoldalas jelentéseket, és hogy kötelezővé tegye a sorszintű biztonság (RLS) engedélyezését a megtekintéshez, mindenképpen kövesse az alábbi szabályokat:

### <a name="classic-apps-and-app-workspaces"></a>Klasszikus alkalmazások és alkalmazás-munkaterületek

- .rdl ugyanabban a munkaterületben, mint az adatkészlet (ugyanazon tulajdonos): Támogatott
- .rdl más munkaterületben, mint az adatkészlet (ugyanazon tulajdonos): Támogatott
- Megosztott .rdl: Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén
- Megosztott alkalmazás: Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén
- .rdl ugyanabban a munkaterületben, mint az adatkészlet (eltérő tulajdonos): Támogatott
- .rdl más munkaterületben, mint az adatkészlet (eltérő tulajdonos): Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén
- Sorszintű biztonság: Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén a kötelezővé tételhez.

### <a name="new-experience-apps-and-app-workspaces"></a>Új felhasználói móddal rendelkező alkalmazások és alkalmazás-munkaterületek

- .rdl ugyanabban a munkaterületben, mint az adatkészlet: Támogatott
- .rdl más munkaterületben, mint az adatkészlet (ugyanazon tulajdonos): Támogatott
- Megosztott .rdl: Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén
- Megosztott alkalmazás: Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén
- .rdl ugyanabban a munkaterületben, mint az adatkészlet (eltérő tulajdonos) – támogatott
- .rdl más munkaterületben, mint az adatkészlet (eltérő tulajdonos): Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén
- Sorszintű biztonság: Buildelési engedélyeket kell hozzárendelni a jelentést megtekintő minden felhasználóhoz az adatkészlet szintjén a kötelezővé tételhez

## <a name="next-steps"></a>Következő lépések

- [Beágyazott adathalmaz létrehozása lapszámozott jelentéshez a Power BI szolgáltatásban](paginated-reports-create-embedded-dataset.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
