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
ms.openlocfilehash: 7b687fd67f844e000811ae00a53772ab9403ab90
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/12/2019
ms.locfileid: "66838932"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Beágyazott adatforrás létrehozása lapszámozott jelentésekhez a Power BI szolgáltatásban

Ebből a cikkből beágyazott adatforrások lapszámozott jelentésekhez való létrehozását és módosítását sajátíthatja el a Power BI szolgáltatásban. Beágyazott adatforrást egyetlen jelentéshez definiálhat, és csak ebben a jelentésben használhatja fel. A Power BI szolgáltatásban közzétett lapszámozott jelentések jelenleg beágyazott adathalmazokat és beágyazott adatforrásokat igényelnek, és a következő adatforrásokhoz kapcsolódhatnak:

- Azure SQL Database és Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

A következő adatforrások esetében használja az [SQL Server Analysis Services-kapcsolat](service-premium-connect-tools.md) lehetőséget:

- Azure Analysis Services
- Power BI Premium-adatkészletek

A lapszámozott jelentések átjárón keresztül kapcsolódnak a [Power BI-átjáróhoz](service-gateway-getting-started.md). Az átjárót azután állíthatja be, hogy a jelentést közzéteszi a Power BI szolgáltatásban.

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

## <a name="next-steps"></a>Következő lépések

- [Beágyazott adathalmaz létrehozása lapszámozott jelentéshez a Power BI szolgáltatásban](paginated-reports-create-embedded-dataset.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
