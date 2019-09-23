---
ms.openlocfilehash: 4c1a7bce8eb24534974fe6a06a8bada4ba9fb708
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61265125"
---
Ebben a témában közelebbről is szemügyre vesszük, hogyan illeszkedik egymáshoz a Power BI első két része.

* Jelentés létrehozása a **Power BI Desktopban**
* Jelentés közzététele a **Power BI szolgáltatásban**

Először indítsa el a Power BI Desktopot, majd válassza az **Adatok beolvasása** lehetőséget. Megjelenik az adatforrások gyűjteménye, ahonnan kiválaszthat egy adatforrást. Az alábbi képen egy weblap forrásként történő kiválasztása látható. A fenti videóban Will egy **Excel**-munkafüzetet választott ki.

![](media/0-2-get-started-power-bi-desktop/c0a2_1.png)

Függetlenül attól, hogy melyik adatforrást választja, a Power BI ahhoz az adatforráshoz fog kapcsolódni, és az abból az adatforrásból elérhető adatokat fogja mutatni. Az alábbi képen egy másik példa látható: egy különböző államokat és nyugdíjazási statisztikákat elemző weblap.

![](media/0-2-get-started-power-bi-desktop/c0a2_2.png)

A Power BI Desktop **Jelentés** nézetében elkezdhet jelentéseket létrehozni.

A **Jelentés** nézet a következő öt fő területből áll:

1. A menüszalag, amely a jelentésekhez és vizualizációkhoz kapcsolódó általános feladatokat jeleníti meg.
2. A **Jelentés** nézet, vagy más néven vászon. Itt lehet létrehozni és elrendezni a vizualizációkat.
3. Az **Oldalak** lapterület alul, ahol kiválaszthat vagy hozzáadhat jelentésoldalakat.
4. A **Megjelenítések** panel, ahol módosíthatja a vizualizációkat, testreszabhatja a színeket vagy a tengelyeket, szűrőket alkalmazhat, húzással elhelyezheti a mezőket stb.
5. A **Mezők** panel, ahonnan a lekérdezéselemeket és a szűrőket a **Jelentés** nézetbe vagy a **Megjelenítések** panel **Szűrők** területére húzhatja.

![](media/0-2-get-started-power-bi-desktop/c0a2_3.png)

A **Megjelenítések** és a **Mezők** panel összezárható a szélén található kis nyíl kiválasztásával, így több hely marad a **Jelentés** nézetben a vizualizációk összeállítására. A vizualizációk módosításakor ezek a nyilak felfelé vagy lefelé mutatnak, ami azt jelzi, hogy az adott szakasz kibontható vagy összezárható.

![](media/0-2-get-started-power-bi-desktop/c0a2_4.png)

Vizualizációs elem létrehozásához egyszerűen húzzon egy mezőt a **Mezők** listáról a **Jelentés** nézetre. Ebben a példában húzza át a *RetirementStats* (Nyugdíjstatisztikák) State (Állam) mezőjét, és nézze meg, mi történik.

![](media/0-2-get-started-power-bi-desktop/c0a2_5.png)

Nézze... A Power BI Desktop automatikusan létrehozott egy térkép-alapú vizualizációs elemet, mert felismerte, hogy a State (Állam) mező földrajzi helyadatokat tartalmaz.

Most lépjünk előre egy kicsit: néhány vizualizációs elem hozzáadása után a jelentés közzétehető a Power BI szolgáltatásban. A Power BI Desktop **Kezdőlap** menüszalagjáról válassza ki a **Közzététel** lehetőséget.

![](media/0-2-get-started-power-bi-desktop/c0a2_6.png)

A rendszer kérni fogja, hogy jelentkezzen be a Power BI-ba.

![](media/0-2-get-started-power-bi-desktop/c0a2_7.png)

Amikor bejelentkezik, és befejeződik a közzétételi folyamat, az alábbi párbeszédablak jelenik meg. A **Sikeres!** felirat alatt rákattinthat a Power BI szolgáltatásra mutató hivatkozásra, ahol megtekintheti az éppen most közzétett jelentést.

![](media/0-2-get-started-power-bi-desktop/c0a2_8.png)

Amikor bejelentkezik a Power BI szolgáltatásba, látni fogja a szolgáltatásban éppen most közzétett Power BI Desktop-fájlt. Az alábbi képen a Power BI Desktopban létrehozott jelentés a **Jelentések** szakaszban látható.

![](media/0-2-get-started-power-bi-desktop/c0a2_9.png)

Ha a jelentésben rákattint a **Rögzítés** ikonra, a vizualizációs elemet rögzítheti az egyik irányítópulton. A következő képen a rögzítés ikon bekeretezve látható, egy rá mutató nyíllal.

![](media/0-2-get-started-power-bi-desktop/c0a2_10.png)

Az ikon kiválasztásakor az alábbi párbeszédablak jelenik meg, lehetővé téve, hogy a vizualizációs elemet egy már létező irányítópultra rögzítse, vagy létrehozzon egy új irányítópultot.

![](media/0-2-get-started-power-bi-desktop/c0a2_11.png)

Amikor a jelentésből rögzít néhány vizualizációs elemet, azok láthatóvá válnak az irányítópulton.

![](media/0-2-get-started-power-bi-desktop/c0a2_12.png)

A fentieken túl természetesen még sok minden másra használhatja a Power BI-t, például a létrehozott irányítópultok megosztására. A megosztásra a képzés során később még visszatérünk.

Most nézzük meg azt a szolgáltatást, amely automatikusan tud irányítópultokat létrehozni már akkor is, ha egyszerűen csatlakozik egy olyan felhőalapú szolgáltatáshoz, mint amilyen például Facebook vagy a Salesforce.

