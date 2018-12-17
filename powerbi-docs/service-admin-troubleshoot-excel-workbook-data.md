---
title: 'Hiba: Nem található adat az Excel-munkafüzetben'
description: 'Hiba: Nem található adat az Excel-munkafüzetben'
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ea5312178d33986ebc3f4b9e8610012c87d54216
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026031"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Hiba: Nem található adat az Excel-munkafüzetben

>[!NOTE]
>Ez a cikk az Excel 2007-es vagy újabb verzióira vonatkozik.

Excel-munkafüzet Power BI-ba történő importálásakor a következő hiba jelenhet meg:

*Hiba: Nem található adat az Excel-munkafüzetben. Lehet, hogy az adatok nem megfelelő formátumúak. A munkafüzetet szerkesztenie kell az Excelben, majd újra kell importálnia.*

![Nem található adat a munkafüzetben](media/service-admin-troubleshoot-excel-workbook-data/pbi_wecouldntfindanydata.png)

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
    
    ![Munkafüzet megnyitása](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht1.png)
2. Válassza ki az adatokat tartalmazó cellatartományt. Az első sornak az oszlopfejléceket (oszlopneveket) kell tartalmaznia:
   
    ![Cellatartomány kijelölése](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht2.png)
3. A **BESZÚRÁS** lap menüszalagján kattintson a **Táblázat** elemre. (Vagy használja a **Ctrl + T** billentyűparancsot.)
   
    ![Táblázat beszúrása](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht3.png)
4. A következő párbeszédpanel jelenik meg. Ellenőrizze, hogy a **Táblázatban vannak fejlécek** lehetőség ki van jelölve, majd nyomja le az **OK** gombot:
   
    ![Táblázat létrehozása](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlcreatetbl.png)
5. Az adatok most már táblázatként vannak formázva:
   
    ![Táblázatként formázott adatok](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xltbl.png)
6. Mentse a munkafüzetet.
7. Térjen vissza a Power BI-ba. Kattintson az Adatok lekérése elemre a bal oldali navigációs ablaktábla alján.
   
    ![Adatok lekérése](media/service-admin-troubleshoot-excel-workbook-data/pbi_getdata.png)
8. A **Fájlok** mezőben válassza a **Beolvasás** lehetőséget.
   
    ![Fájlok lekérése](media/service-admin-troubleshoot-excel-workbook-data/pbi_getfiles.png)
9. Importálja újra az Excel-munkafüzetet. Az importálási folyamatnak most már sikeresen meg kell találnia a táblázatot.
   
    Ha az importálás még mindig sikertelen, hozza a tudomásunkra a Súgó menü **Közösség ** lehetőségére kattintva:
   
    ![Közösségi hivatkozás](media/service-admin-troubleshoot-excel-workbook-data/pbi_questionmenucommunity.png)
