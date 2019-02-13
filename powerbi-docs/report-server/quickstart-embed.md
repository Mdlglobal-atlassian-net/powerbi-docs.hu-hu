---
title: Jelentés beágyazása iFrame használatával
description: Power BI jelentéskészítő kiszolgálóval készült jelentés beágyazása iFrame-keretben a SharePoint Serverben
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 4730bef0e7f1fc47a4a59a0129640760714fe2e0
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56223329"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Rövid útmutató: Power BI jelentéskészítő kiszolgálóval készült jelentés beágyazása iFrame-keretben a SharePoint Serverben

Ezzel a rövid útmutatóval megtanulhatja egy Power BI jelentéskészítő kiszolgálóval készült jelentés iFrame használatával történő beágyazását egy SharePoint oldalba. Ha a SharePoint Online-nal dolgozik, akkor a Power BI jelentéskészítő kiszolgálónak nyilvánosan elérhetőnek kell lennie. A SharePoint Online-ban a Power BI szolgáltatással együttműködő Power BI jelentéskijelző nem működik együtt a Power BI jelentéskészítő kiszolgálóval. 

![iFrame-minta](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Előfeltételek
* Szüksége lesz a telepített és konfigurált [Power BI jelentéskészítő kiszolgálóra](https://powerbi.microsoft.com/report-server/).
* A [Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopnak](install-powerbi-desktop.md) telepítve kell lennie.
* Szüksége lesz még egy telepített és konfigurált [SharePoint](https://docs.microsoft.com/sharepoint/install/install)-környezetre.

## <a name="creating-the-power-bi-report-server-report-url"></a>A Power BI jelentéskészítő kiszolgálóval készült jelentés URL-címének létrehozása

1. Töltse le a mintát a GitHubról – [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples).

    ![minta PBIX-fájl letöltése](media/quickstart-embed/quickstart_embed_14.png)

2. Nyissa meg a GitHubról származó PBIX-fájlt a **Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopban**.

    ![PBI RS asztali eszköz](media/quickstart-embed/quickstart_embed_02.png)

3. Mentse a jelentést a **Power BI jelentéskészítő kiszolgálóra**. 

    ![PBI RS mentés](media/quickstart-embed/quickstart_embed_03.png)

4. Jelentés megtekintése a **webes portálon**.

    ![webes portál](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>Az URL-paraméter rögzítése

Ha megvan az URL-cím, létrehozhat egy SharePoint-oldalon egy iFrame-et, amely megjeleníti a jelentést. A Power BI jelentéskészítő kiszolgálóval készült jelentések URL-címéhez hozzáfűzhető a `?rs:embed=true` lekérdezési sztring amely egy iFrame-be ágyazza be a jelentést. 

   Például:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Power BI jelentéskészítő kiszolgálóval készült jelentés beágyazása SharePoint iFrame-keretben

1. Nyissa meg a SharePoint **Webhely tartalma** oldalát.

    ![Webhely tartalma oldal](media/quickstart-embed/quickstart_embed_05.png)

2. Válassza ki az oldalt, amelyhez hozzá kívánja adni a jelentést.

    ![Webhely tartalma oldal alkalmazás](media/quickstart-embed/quickstart_embed_06.png)

3. Válassza a jobb felső sarokban lévő fogaskerék ikont, majd az **Oldal szerkesztése** lehetőséget.

    ![Oldal szerkesztése lehetőség](media/quickstart-embed/quickstart_embed_07.png)

4. Válassza a **Kijelző hozzáadása** lehetőséget.

    ![Kijelző hozzáadása](media/quickstart-embed/quickstart_embed_08.png)

5. A **Kategóriák** alatt válassza a **Média és tartalom** elemet, a **Kijelzők** között pedig a **Tartalomszerkesztő** elemet, majd a **Hozzáadás** lehetőséget.

    ![Tartalomszerkesztő webes kijelző kiválasztása](media/quickstart-embed/quickstart_embed_09.png) ![Hozzáadás kiválasztása](media/quickstart-embed/quickstart_embed_091.png)

6. Válassza az **Új tartalom hozzáadásához kattintson ide** elemet.

    ![Új tartalom hozzáadása](media/quickstart-embed/quickstart_embed_10.png)

7. A szalagon válassza a **Szöveg formázása** lapot, majd a **Forrás szerkesztése** lehetőséget.

     ![Forrás szerkesztése](media/quickstart-embed/quickstart_embed_11.png)

8. A Forrás szerkesztése ablakban illessze be iFrame-kódját és válassza az OK lehetőséget.

    ![iFrame-kód](media/quickstart-embed/quickstart_embed_12.png)

     Például:
     ```html
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. A szalagon válassza az **Oldal** lapot, majd a **Szerkesztés befejezése** lehetőséget.

    ![Szerkesztés befejezése](media/quickstart-embed/quickstart_embed_13.png)

10. A jelentésnek meg kell jelennie az oldalon.

    ![iFrame-minta](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Következő lépések

[Rövid útmutató: Power BI-jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz](quickstart-create-powerbi-report.md)  
[Rövid útmutató: Többoldalas jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz](quickstart-create-paginated-report.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/) 