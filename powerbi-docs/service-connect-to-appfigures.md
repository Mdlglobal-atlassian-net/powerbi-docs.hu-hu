---
title: Csatlakozás az appFigures-hoz a Power BI használatával
description: appFigures a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 2a19cc832f7e03acfd224c6ab2409016ce8da770
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61179813"
---
# <a name="connect-to-appfigures-with-power-bi"></a>Csatlakozás az appFigures-hoz a Power BI használatával
A Power BI és az appFigures-tartalomcsomag segítségével egyszerűen nyomon követheti az alkalmazásait leíró fontos statisztikákat. A Power BI adatokat kér le többek között az alkalmazás értékesítéséről, letöltéseiről és hirdetési statisztikáiról, majd felépít egy alapértelmezett irányítópultot, és létrehozza a kapcsolódó jelentéseket.

Csatlakozzon az [appFigures-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/appfigures), vagy tájékozódjon bővebben [az appFigures és a Power BI integrációjáról.](https://powerbi.microsoft.com/integrations/appfigures)

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-appfigures/pbi_getdata.png)
2. A **Szolgáltatások** mezőben válassza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-appfigures/pbi_getservices.png)
3. Kattintson az **appFigures** \>  **Get** elemre.
   
   ![](media/service-connect-to-appfigures/appfigures.png)
4. A **Hitelesítési módszer** beállításánál válassza az **oAuth2** \> **Bejelentkezés** lehetőséget. Amikor a rendszer kéri, adja meg az appFigures-beli hitelesítő adatait, majd haladjon végig a hitelesítés folyamatán.
   
   Az első kapcsolódás alkalmával a Power BI kérni fogja, hogy engedélyezze az olvasási hozzáférést a fiókjához. Az **Engedélyezés** elemre kattintva kezdje el az importálási folyamatot. Ez a fiókban tárolt adatok mennyiségétől függően néhány percet is igénybe vehet.
   
   ![](media/service-connect-to-appfigures/appfiguresdoc_06.png)
5. Miután a Power BI importálta az adatokat, a bal oldali navigációs ablaktáblán egy új irányítópult, jelentés és adatkészlet jelenik meg. Az új elemeket sárga csillag jelöli \*:
   
    ![](media/service-connect-to-appfigures/pbi_appfigures3.png)
6. Válassza ki az appFigures irányítópultját. A Power BI ezt az alapértelmezett irányítópultot hozta létre az adatok megjelenítésére. Az irányítópultot igény szerint módosíthatja, hogy az adatok a kívánt módon jelenjenek meg.
   
    ![](media/service-connect-to-appfigures/appfiguresdoc_01.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A Power BI-ban a következő, appFigures-ból származó adatok érhetők el.

| **Tábla neve** | **Leírás** |
| --- | --- |
| Országok |Ez a táblázat az országnevekről ad tájékoztatást. |
| Dátumok |Ez a táblázat az appFigures-fiókban lévő aktív és látható alkalmazásokhoz tartozó dátumokat tartalmazza a mai naptól visszamenőleg az adatok közzétételének (PublishDate) legkorábbi időpontjáig. |
| Események |Ez a táblázat a letöltések, értékesítések és hirdetések napi adatait tartalmazza országok szerint az egyes alkalmazásokról. Vegye figyelembe, hogy az alkalmazásértékesítési és az alkalmazáson belüli értékesítési adatok egyaránt ebben a táblázatban szerepelnek – a különbségtételre a <strong>Típus</strong> oszlopot használhatja. |
| Alkalmazáson belüli vásárlások |Ez a táblázat az appFigures-fiókban lévő aktív és látható alkalmazásokhoz hozzárendelt különböző típusú alkalmazáson belüli vásárlások adatait tartalmazza. |
| Termékek |Ez a táblázat az appFigures-fiókban lévő különféle aktív és látható alkalmazások adatait tartalmazza. |

## <a name="troubleshooting"></a>Hibaelhárítás
Ha egy alkalmazás adatai nem jelennek meg a Power BI-ban, ellenőrizze, hogy az alkalmazás látható és aktív-e az appFigures-oldal **alkalmazások** lapján.

![](media/service-connect-to-appfigures/appfiguresdoc_11.png)

## <a name="next-steps"></a>Következő lépések
* [Első lépések a Power BI-ban](service-get-started.md)
* [Adatok lekérése a Power BI-ban](service-get-data.md)

