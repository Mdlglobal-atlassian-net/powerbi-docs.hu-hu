---
title: Külső R IDE használata a Power BI-ban
description: Elindíthat és használhat egy külső IDE környezetet a Power BI-jal
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7d087e8d6b643d836be865a48b9570066af1af6f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274743"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>Külső R IDE használata a Power BI-ban
A **Power BI Desktoppal** használhatja a külső R IDE környezetet (integrált fejlesztőkörnyezetet) R-szkriptek létrehozásához és pontosításához, majd ezután használhatja ezeket a szkripteket a Power BI-ban.

![](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>Külső R IDE környezet engedélyezése
Korábban az R-szkriptszerkesztőt kellett használni a **Power BI Desktopban** R-szkriptek létrehozásához és futtatásához. Ettől a kiadástól kezdve a külső R IDE környezetet a **Power BI Desktopból** is elindíthatja, és az adatokat automatikusan importálhatja és megjelenítheti az R IDE környezetben. Majd módosíthatja a szkriptet a külső R IDE-ben, illetve visszamásolhatja a **Power BI Desktopba** Power BI-vizualizációk és -jelentések létrehozásához.

A **Power BI Desktop** 2016 szeptemberi kiadásától kezdve (2.39.4526.362-es verzió) megadhatja, hogy melyik R IDE környezetet szeretné használni, és automatikusan elindíthatja a **Power BI Desktopon** belül.

### <a name="requirements"></a>Követelmények
A funkció használatához telepítenie kell egy **R IDE** környezetet a helyi számítógépen. A **Power BI Desktop** nem tartalmazza, helyezi üzembe vagy telepíti az R-motort, ezért külön kell telepítenie az **R**-t a helyi számítógépen. A következő lehetőségekkel kiválaszthatja, melyik R IDE környezetet szeretné használni:

* Telepítheti kedvenc R IDE környezetét, amelyek közül számos ingyen elérhető, például a [Revolution Open letöltőoldalról](https://mran.revolutionanalytics.com/download/) vagy a [CRAN tárból](https://cran.r-project.org/bin/windows/base/).
* A **Power BI Desktop** szintén támogatja az [R Studiót](https://www.rstudio.com/) és az [*R Tools for Visual Studio*](https://beta.visualstudio.com/vs/rtvs/) szerkesztőkkel rendelkező **Visual Studio 2015**-öt.
* Másik R IDE is telepíthető, és az alábbiak elvégzésével beállíthatja a **Power BI Desktopot** úgy, hogy elindítsa ezt az **R IDE** környezetet:
  
  * **.R**-fájlokat társíthat ahhoz a külső IDE-hez, amelyet a **Power BI Desktopban** futtatni szeretne.
  * Megadhatja azt az .exe fájlt, amelyet a **Power BI Desktopnak** futtatnia kell, ha kiválasztja az *Egyéb* lehetőséget a **Beállítások** párbeszédpanel **R-szkript beállításai** szakaszából. A **Beállítások** párbeszédpanelt úgy jelenítheti meg, hogy a **Fájl > Lehetőségek és beállítások > Beállítások** szakaszhoz lép.
    
    ![](media/desktop-r-ide/r-ide_1b.png)

Ha több R IDE van telepítve, a **Beállítások** párbeszédpanel *Észlelt R IDE környezetek* legördülő menüjéből kiválasztva megadhatja, hogy melyik induljon el.

Alapértelmezés szerint a **Power BI Desktop** az **R Studiót** indítja el külső R IDE-ként, ha az telepítve van a helyi számítógépen. Ha az **R Studio** nincs telepítve, viszont az **R Tool for Visual Studio** eszközzel rendelkező **Visual Studio 2015** igen, akkor ez lesz elindítva. Ha ezek közül egyik R IDE sincs telepítve, az **.R**-fájlokkal társított alkalmazás lesz elindítva.

Ha nincs **.R**-fájltársítás, lehetőség van egy egyéni IDE környezetre mutató elérési út megadására a **Beállítások** párbeszédpanel *Tallózás az előnyben részesített R IDE kiválasztásához* szakaszában. Egy eltérő R IDE környezetet is elindíthat, ha az **R IDE indítása** nyílikon melletti **Beállítások** fogaskerékikonra kattint a **Power BI Desktopban**.

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>R IDE indítása a Power BI Desktopból
Az R IDE a **Power BI Desktopból** történő indításához hajtsa végre az alábbi lépéseket:

1. Adatok betöltése a **Power BI Desktopba**.
2. Válasszon ki néhány mezőt a **Mezők** panelről, amelyekkel dolgozni szeretne. Ha még nem engedélyezte a szkriptvizualizációkat, a rendszer ezt kérni fogja.
   
   ![](media/desktop-r-ide/r-ide_3.png)
3. A szkriptvizualizációk engedélyezése után a **Vizualizációk** panelről kiválaszthat egy R-vizualizációt, amely egy üres, a szkript eredményeinek megjelenítésére készen álló R-vizualizációt hoz létre. Megjelenik az **R-szkriptszerkesztő** ablaktábla is.
   
   ![](media/desktop-r-ide/r-ide_4.png)
4. Most kiválaszthatja, hogy mely mezőket szeretné használni az R-szkriptben. Ha kiválaszt egy mezőt, az **R-szkriptszerkesztő** mező automatikusan létrehoz egy, a kiválasztott mezőn vagy mezőkön alapuló szkriptkódot. Létrehozhatja (vagy beillesztheti) az R-szkriptet közvetlenül az **R-szkriptszerkesztő** ablaktáblán, vagy üresen hagyhatja azt.
   
   ![](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > Az R-vizualizációk összesítésének alapértelmezett típusa a *nincs összegzés*.
   > 
   > 
5. Mostantól közvetlenül a **Power BI Desktopból** indíthatja el az R IDE környezetet. Kattintson az **R IDE indítása** gombra, amely az **R-szkriptszerkesztő** címsorának jobb oldalán található, ahogy az a lenti képen is látható.
   
   ![](media/desktop-r-ide/r-ide_6.png)
6. A megadott R IDE környezetet a Power BI Desktop indítja el, ahogy az az alábbi képen is látható (ezen a képen az **RStudio** az alapértelmezett R IDE).
   
   ![](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > A szkript első három sorát a **Power BI Desktop** adja hozzá, így az importálni tudja az adatokat a **Power BI Desktopból** a szkript futtatása után.
   > 
   > 
7. Bármely szkript, amelyet a **Power BI Desktop** **R-szkriptszerkesztő ablaktábláján** hozott létre, a 4. sortól kezdve jelenik meg az R IDE környezetben. Ekkor létrehozhat egy R-szkriptet az R IDE környezetben. Miután az R-szkript elkészült az R IDE környezetben, ki kell másolnia és be kell illesztenie azt a **Power BI Desktop** **R-szkriptszerkesztő** ablaktáblájába, *kivéve* a szkript azon első három sorát, amelyet a **Power BI Desktop** hozott automatikusan létre. A szkript első három sorát ne másolja vissza a **Power BI Desktopba**, azokat a sorokat csak az adatok a **Power BI Desktopból** az R IDE környezetbe történő importálásához használta a rendszer.

### <a name="known-limitations"></a>Ismert korlátozások
Ha az R IDE indítása közvetlenül a Power BI Desktopból történik, az néhány korlátozással jár:

* A szkript R IDE környezetből **Power BI Desktopba** való automatikus exportálása nem támogatott.
* Az **R-ügyfél**szerkesztő (RGui.exe) nem támogatott, mert maga a szerkesztő nem támogatja fájlok megnyitását.

## <a name="next-steps"></a>Következő lépések
Tekintse meg az alábbi, az R programozási nyelv Power BI-ban történő használatára vonatkozó további információkat.

* [R-szkriptek futtatása a Power BI Desktopban](desktop-r-scripts.md)
* [Power BI-vizualizációk létrehozása az R használatával](desktop-r-visuals.md)

