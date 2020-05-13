---
title: Külső Python IDE használata a Power BI-jal
description: Elindíthat és használhat egy külső IDE környezetet a Power BI-jal
author: otarb
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2018
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: dbdd4076c9944cf0335ed1f6b6aa43a2a3887189
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83291719"
---
# <a name="use-an-external-python-ide-with-power-bi"></a>Külső Python IDE használata a Power BI-jal
A **Power BI Desktoppal** használhatja a külső Python IDE környezetet (integrált fejlesztőkörnyezetet) Python-szkriptek létrehozásához és pontosításához, majd ezután használhatja ezeket a szkripteket a Power BI-ban.

![](media/desktop-python-ide/python-ide-1.png)

## <a name="enable-an-external-python-ide"></a>Külső Python IDE környezet engedélyezése
A külső Python IDE környezetet a **Power BI Desktopból** is elindíthatja, és az adatokat automatikusan importálhatja és megjelenítheti a Python IDE környezetben. Majd módosíthatja a szkriptet a külső Python IDE-ben, illetve visszamásolhatja a **Power BI Desktopba** Power BI-vizualizációk és -jelentések létrehozásához.

Megadhatja, hogy melyik Python IDE-t szeretné használni, és automatikusan elindíthatja a **Power BI Desktopról**.

### <a name="requirements"></a>Követelmények
A funkció használatához telepítenie kell egy **Python IDE** környezetet a helyi számítógépen. A **Power BI Desktop** nem tartalmazza, helyezi üzembe vagy telepíti a Python-motort, ezért külön kell telepítenie a **Pythont** a helyi számítógépen. A következő lehetőségekkel kiválaszthatja, melyik Python IDE környezetet szeretné használni:

* Telepítheti kedvenc Python IDE környezetét, amelyek közül számos ingyen elérhető, például a [Visual Studio Code letöltőoldaláról](https://code.visualstudio.com/download/).
* A **Power BI Desktop** a **Visual Studiót** is támogatja.
* Másik Python IDE is telepíthető, és az alábbiak elvégzésével beállíthatja a **Power BI Desktopot** úgy, hogy elindítsa ezt a **Python IDE** környezetet:
  
  * **.PY** fájlokat társíthat ahhoz a külső IDE-hez, amelyet a **Power BI Desktopban** futtatni szeretne.
  * Megadhatja azt az .exe fájlt, amelyet a **Power BI Desktopnak** futtatnia kell. Ehhez válassza az *Egyéb* lehetőséget a **Beállítások** párbeszédpanel **Python-szkript beállításai** szakaszából. A **Beállítások** párbeszédpanelt úgy jelenítheti meg, hogy a **Fájl > Lehetőségek és beállítások > Beállítások** szakaszhoz lép.
    
    ![](media/desktop-python-ide/python-ide-2.png)

Ha több Python IDE van telepítve, a *Beállítások* párbeszédpanel **Észlelt Python IDE-k** legördülő menüjéből kiválasztva megadhatja, hogy melyik induljon el.

Alapértelmezés szerint a **Power BI Desktop** a **Visual Studio Code-ot** indítja el külső Python IDE-ként, ha az telepítve van a helyi számítógépen. Ha a **Visual Studio Code** nincs telepítve, a **Visual Studio** azonban igen, akkor az lesz elindítva. Ha ezek közül egyik Python IDE sincs telepítve, a **.PY** fájlokhoz társított alkalmazás lesz elindítva.

Ha nincs **.PY** fájltársítás, lehetőség van egy egyéni IDE környezetre mutató elérési út megadására a *Beállítások* párbeszédpanel **Tallózás az előnyben részesített Python IDE kiválasztásához** szakaszában. Egy eltérő Python IDE környezetet is elindíthat, ha a **Python IDE indítása** nyílikon melletti **Beállítások** fogaskerék ikonra kattint a **Power BI Desktopban**.

## <a name="launch-a-python-ide-from-power-bi-desktop"></a>Python IDE indítása a Power BI Desktopból
A Python IDE a **Power BI Desktopból** történő indításához hajtsa végre az alábbi lépéseket:

1. Adatok betöltése a **Power BI Desktopba**.
2. Válasszon ki néhány mezőt a **Mezők** panelről, amelyekkel dolgozni szeretne. Ha még nem engedélyezte a szkriptvizualizációkat, a rendszer ezt kérni fogja.
   
   ![](media/desktop-python-ide/python-ide-3.png)
3. A szkriptvizualizációk engedélyezése után a **Vizualizációk** panelről kiválaszthat egy Python-vizualizációt, amely egy üres, a szkript eredményeinek megjelenítésére készen álló Python-vizualizációt hoz létre. Megjelenik a **Python-szkriptszerkesztő** ablaktábla is.
   
   ![](media/desktop-python-ide/python-ide-4.png)
4. Most kiválaszthatja, mely mezőket szeretné használni a Python-szkriptben. Ha kiválaszt egy mezőt, a **Python-szkriptszerkesztő** mező automatikusan létrehoz egy, a kiválasztott mezőn vagy mezőkön alapuló szkriptkódot. Létrehozhatja (vagy beillesztheti) a Python-szkriptet közvetlenül a **Python-szkriptszerkesztő** ablaktáblán, vagy üresen hagyhatja azt.
   
   ![](media/desktop-python-ide/python-ide-5.png)
   
   > [!NOTE]
   > A Python-vizualizációk összesítésének alapértelmezett típusa a *nincs összegzés*.
   > 
   > 
5. Mostantól közvetlenül a **Power BI Desktopból** indíthatja el a Python IDE környezetet. Kattintson a **Python IDE indítása** gombra, amely a **Python-szkriptszerkesztő** címsorának jobb oldalán található, ahogy az a lenti képen is látható.
   
   ![](media/desktop-python-ide/python-ide-6.png)
6. A megadott Python IDE környezetet a Power BI Desktop elindítja, ahogy az az alábbi képen is látható (ezen a képen a **Visual Studio Code** az alapértelmezett Python IDE).
   
   ![](media/desktop-python-ide/python-ide-7.png)
   
   > [!NOTE]
   > A szkript első három sorát a **Power BI Desktop** adja hozzá, így az importálni tudja az adatokat a **Power BI Desktopból** a szkript futtatása után.
   > 
   > 
7. Bármely szkript, amelyet a **Power BI Desktop** **Python-szkriptszerkesztő ablaktábláján** hozott létre, a 4. sortól kezdve jelenik meg a Python IDE környezetben. Ekkor létrehozhat egy Python-szkriptet a Python IDE környezetben. Miután a Python-szkript elkészült a Python IDE környezetben, ki kell másolnia és be kell illesztenie azt a **Power BI Desktop** **Python-szkriptszerkesztő** ablaktáblájába, *kivéve* a szkript azon első három sorát, amelyet a **Power BI Desktop** hozott automatikusan létre. A szkript első három sorát ne másolja vissza a **Power BI Desktopba**, azokat a sorokat csak az adatok a **Power BI Desktopból** a Python IDE környezetbe történő importálásához használta a rendszer.

### <a name="known-limitations"></a>Ismert korlátozások
Ha a Python IDE indítása közvetlenül a Power BI Desktopból történik, az néhány korlátozással jár:

* A szkript Python IDE környezetből **Power BI Desktopba** való automatikus exportálása nem támogatott.

## <a name="next-steps"></a>További lépések
Tekintse meg az alábbi, a Python programozási nyelv Power BI-ban történő használatára vonatkozó további információkat.

* [Python-szkriptek futtatása a Power BI Desktopban](desktop-python-scripts.md)
* [Power BI-vizualizációk létrehozása a Python használatával](desktop-python-visuals.md)

