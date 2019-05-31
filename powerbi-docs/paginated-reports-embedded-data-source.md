---
title: Beágyazott adatforrások lapszámozott jelentésekhez a Power BI szolgáltatásban (előzetes verzió)
description: Ebből a cikkből beágyazott adatforrások lapszámozott jelentésekben való létrehozását és módosítását sajátíthatja el a Power BI szolgáltatásban.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/16/2019
ms.openlocfilehash: 4dd9ad935a9f7b286aa64d977a78364f2aed0e0f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65853382"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service-preview"></a>Beágyazott adatforrás létrehozása lapszámozott jelentésekhez a Power BI szolgáltatásban (előzetes verzió)

Ebből a cikkből beágyazott adatforrások lapszámozott jelentésekhez való létrehozását és módosítását sajátíthatja el a Power BI szolgáltatásban. Beágyazott adatforrást egyetlen jelentéshez definiálhat, és csak ebben a jelentésben használhatja fel. A Power BI szolgáltatásban közzétett lapszámozott jelentések jelenleg beágyazott adathalmazokat és beágyazott adatforrásokat igényelnek, és a következő adatforrásokhoz kapcsolódhatnak:

- Azure SQL Database és Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

Ezeket az adatforrásokat, használja a [SQL Server Analysis Services-kapcsolat](service-premium-connect-tools.md) lehetőséget:

- Azure Analysis Services
- A Power BI prémium szintű adatkészleteiket

A lapszámozott jelentések átjárón keresztül kapcsolódnak a helyszíni adatforrásokhoz. Az átjárót azután állíthatja be, hogy a jelentést közzéteszi a Power BI szolgáltatásban. További információ a [Power BI-átjárókról](service-gateway-getting-started.md). 

## <a name="create-an-embedded-data-source"></a>Beágyazott adatforrás létrehozása
  
1. Nyissa meg a Power BI jelentéskészítő.

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
- [Mik azok a lapszámozott jelentések a Power BI Premiumban? (előzetes verzió)](paginated-reports-report-builder-power-bi.md)
