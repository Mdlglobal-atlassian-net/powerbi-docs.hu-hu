---
title: 'Hiba: Nem található adat az Excel-munkafüzetben'
description: 'Hiba: Nem található adat az Excel-munkafüzetben'
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 04/30/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1976567029454445f625ff400fb1d87ae6c01219
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83310625"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Hiba: Nem található adat az Excel-munkafüzetben

>[!NOTE]  
>Ez a cikk az Excel 2007-es vagy újabb verzióira vonatkozik.

Excel-munkafüzet Power BI-ba történő importálásakor a következő hiba jelenhet meg:

*Hiba: Nem található táblázatként formázott adat. Ha az Excelből szeretne a Power BI szolgáltatásba importálni, táblázatként kell formáznia az adatokat. Válassza ki a táblázatba foglalni kívánt adatokat, majd nyomja le a Ctrl+T billentyűkombinációt.*

![Nem található adat a munkafüzetben](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>Gyors megoldás
1. Szerkessze a munkafüzetet az Excelben.
2. Válassza ki az adatokat tartalmazó cellatartományt. Az első sornak az oszlopfejléceket (oszlopneveket) kell tartalmaznia.
3. Táblázat létrehozásához nyomja le a **Ctrl + T** billentyűket.
4. Mentse a munkafüzetet.
5. Térjen vissza a Power BI-ba, és importálja ismét a munkafüzetet, vagy ha az Excel 2016-ban dolgozik, és a OneDrive Vállalati verzióban mentette a munkafüzetet, kattintson a Fájl > Közzététel lehetőségre az Excelben.

## <a name="details"></a>Részletek
### <a name="cause"></a>Ok
Az Excelben cellatartományokból hozhat létre **táblázatot**, ami megkönnyíti az adatok rendezését, szűrését és formázását.

Excel-munkafüzet importálásakor a Power BI ezeket a táblázatokat keresi, majd egy adatkészletbe importálja őket, ha pedig nem talál táblázatot, akkor ez a hibaüzenet jelenik meg.

### <a name="solution"></a>Megoldás
1. Nyissa meg a munkafüzetet az Excelben. 
    >[!NOTE]
    >Ezek a képek az Excel 2013-ból valók. Ha más verziót használ, a megjelenés eltérő lehet, de a lépések ugyanazok.
    
    ![Munkafüzet megnyitása](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. Válassza ki az adatokat tartalmazó cellatartományt. Az első sornak az oszlopfejléceket (oszlopneveket) kell tartalmaznia:
   
    ![Cellatartomány kijelölése](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. A **BESZÚRÁS** lap menüszalagján kattintson a **Táblázat** elemre. (Vagy használja a **Ctrl + T** billentyűparancsot.)
   
    ![Táblázat beszúrása](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. A következő párbeszédpanel jelenik meg. Ellenőrizze, hogy a **Táblázatban vannak fejlécek** lehetőség ki van jelölve, majd nyomja le az **OK** gombot:
   
    ![Táblázat létrehozása](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. Az adatok most már táblázatként vannak formázva:
   
    ![Táblázatként formázott adatok](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. Mentse a munkafüzetet.
7. Térjen vissza a Power BI-ba. Kattintson az Adatok lekérése elemre a navigációs panel alján.
   
    ![Adatok lekérése](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. A **Fájlok** mezőben válassza a **Beolvasás** lehetőséget.
   
    ![Fájlok lekérése](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Importálja újra az Excel-munkafüzetet. Az importálási folyamatnak most már sikeresen meg kell találnia a táblázatot.
   
    Ha az importálás még mindig sikertelen, hozza a tudomásunkra a Súgó menü **Közösség ** lehetőségére kattintva:
   
    ![Közösségi hivatkozás](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
