---
title: Vizualizációk a Power BI-ban
description: Egyéni vizualizációk a Power BI-ban
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: e68d886564552d1b1cb2dc9e7c018c65a5cca039
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265210"
---
# <a name="visuals-in-power-bi"></a>Vizualizációk a Power BI-ban

Power BI-jelentések létrehozása vagy szerkesztése során számos különböző vizualizációtípust használhat. Ezeknek a vizualizációknak az ikonjai a **Vizualizációk** panelen jelennek meg. Ezek a vizualizációk azonnal elérhetők a [Power BI Desktop](https://powerbi.microsoft.com/desktop/) letöltésekor vagy a [Power BI szolgáltatás](https://app.powerbi.com) megnyitásakor.

![vizualizációk](media/power-bi-custom-visuals/power-bi-visualizations.png)

Azonban nem csupán ezek a vizualizációk állnak rendelkezésére. Ha az alsó **További lehetőségek** (...) elemet választja, elérhetővé válik a jelentésvizualizációk egy másik forrása – a *Power BI-vizualizációk*.

A fejlesztők a Power BI-vizualizációk SDK-val hozzák létre ezeket a vizualizációkat. Ezekkel a vizualizációkkal az üzleti felhasználók az üzletüknek leginkább megfelelő módon jeleníthetik meg adataikat. A jelentéskészítők importálhatják az egyéni vizualizációkat a jelentéseikbe, és azokat a többi Power BI-vizualizációhoz hasonlóan használhatják. A Power BI-vizualizációk kiemelt helyet élveznek a Power BI szolgáltatáson belül, így szűrhetők, kiemelhetők, szerkeszthetők, megoszthatók és egyéb műveletekkel használhatók.

A Power BI-vizualizációk terjesztésének három módja van:

* Egyéni vizualizációfájlok
* Szervezeti vizualizációk
* Piactér-vizualizációk

## <a name="custom-visual-files"></a>Egyéni vizualizációfájlok

A Power BI-vizualizációk olyan csomagok, amelyek a nekik szolgáltatott adatok rendereléséhez szükséges kódot tartalmazzák. Egyéni vizualizációt bárki létrehozhat, valamint becsomagolhatja azt `.pbiviz`-fájlként, amelyet aztán egy Power BI-jelentésbe importálhat.

> [!WARNING]
> Az egyéni vizualizációk biztonsági és adatvédelmi kockázatokat tartalmazó kódot is tartalmazhatnak. Fontolja meg, hogy megbízik-e a szerzőben és az egyéni vizualizációban, mielőtt importálná azt a jelentésébe.

## <a name="organizational-visuals"></a>Szervezeti vizualizációk

A Power BI-rendszergazdák jóváhagyhatják és telepíthetik vállalatuknál a Power BI-vizualizációkat, amelyeket a jelentéskészítők egyszerűen felfedezhetnek, módosíthatnak és használhatnak. A rendszergazdák számára is egyszerű ezeknek a vizualizációknak a kezelése (például verziófrissítés, letiltás/engedélyezés).

 [További információk a vállalati vizualizációkról](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Piactér-vizualizációk

A közösség tagjai mellett a Microsoft is nyilvánosan megosztotta Power BI-vizualizációit az [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) piactéren. Ezeket a vizualizációkat Ön is letöltheti, és hozzáadhatja Power BI-jelentéseihez. Ezeket a Power BI-vizualizációkat a Microsoft tesztelte, és működés és minőség szempontjából is jóváhagyta.

Mi az az [AppSource](office-store.md)? Az a hely, ahol a Microsoft-szoftverekhez alkalmazásokat, beépülő modulokat és bővítményeket találhat. Az AppSource többek között az Office 365, az Azure, a Dynamics 365 és a Power BI több millió felhasználóját köti össze olyan megoldásokkal, amelyekkel minden eddiginél hatékonyabban, részletgazdagon és látványosan dolgozhatnak.

### <a name="certified-visuals"></a>Hitelesített vizualizációk

A Power BI-minősítéssel rendelkező vizualizációk olyan vizualizációk, amelyek a piactéren érhetők el, további szigorú minőségteszteken feleltek meg, és további forgatókönyvek, például [e-mailes előfizetések](../service-report-subscribe.md) és [PowerPointba történő exportálás](../consumer/end-user-powerpoint.md) esetén is támogatottak.
A minősített Power BI-vizualizációk listájának megtekintéséhez vagy saját vizualizáció közzétételéhez lásd a [minősített Power BI-vizualizációkat](power-bi-custom-visuals-certified.md) ismertető szakaszt.

Ön olyan webfejlesztő, aki szeretne saját vizualizációkat létrehozni, és hozzáadni azokat az AppSource-hoz? Az [Egyéni Power BI-vizualizáció fejlesztése](visuals/custom-visual-develop-tutorial.md) című cikkből megtudhatja, hogyan [tehet közzé egyéni vizualizációkat az AppSource-on](office-store.md).

### <a name="import-a-custom-visual-from-a-file"></a>Egyéni vizualizáció importálása fájlból

1. Válassza a **Vizualizációk** panel alján található három pontot.

    ![Vizualizációk2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. A legördülő listából válassza az **Importálás fájlból** lehetőséget.

    ![Importálás fájlból](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. A **Fájl megnyitása** menüben válassza ki az importálni kívánt `.pbiviz`-fájlt, majd válassza a **Megnyitás** lehetőséget. Az egyéni vizualizáció ikonja ekkor megjelenik a **Vizualizációk** panel alján, és már használhatja is a jelentésben.

    ![Importált egyéni vizualizáció](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Szervezeti vizualizációk importálása

1. Válassza a **Vizualizációk** panel alján található három pontot.

    ![1\. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. A legördülő listából válassza az **Importálás a piactérről** lehetőséget.

    ![2\. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Válassza a **SAJÁT SZERVEZET** lehetőséget a felső lap menüjében.

    ![3\. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Tekintse át a listát, és keresse meg az importálni kívánt vizualizációt.

    ![4\. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Az egyéni vizualizáció importálásához válassza a **Hozzáadás** parancsot. Az ikonja ekkor megjelenik a **Vizualizációk** panel alján, és már használhatja is a jelentésben.

    ![5\. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-power-bi-visuals-from-microsoft-appsource"></a>Power BI-vizualizáció letöltése vagy importálása a Microsoft AppSource-ról

A Power BI-vizualizációk letöltésének és importálásának két módja van. Megteheti ezt a Power BI-on belülről és az [AppSource webhelyről](https://appsource.microsoft.com/).

### <a name="import-power-bi-visuals-from-within-power-bi"></a>Power BI-vizualizációk beszerzése a Power BI-on belül

1. Válassza a **Vizualizációk** panel alján található három pontot.

    ![Vizualizációk 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. A legördülő listából válassza az **Importálás a piactérről** lehetőséget.

    ![2\. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Tekintse át a listát, és keresse meg az importálni kívánt vizualizációt.

    ![vizualizáció importálása](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Az egyes vizualizációk kijelölésével további információkat tudhat meg róluk.

    ![Kiválasztás](media/power-bi-custom-visuals/power-bi-select.png)

5. A részletek lapon többek között képernyőképeket, videókat és részletes leírásokat tekinthet meg.

    ![Synoptic](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. A képernyő alján értékelések is találhatók.

    ![Értékelések](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Az egyéni vizualizáció importálásához válassza a **Hozzáadás** parancsot. Az ikonja ekkor megjelenik a **Vizualizációk** panel alján, és már használhatja is a jelentésben.

    ![Importált vizualizáció](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-power-bi-visuals-from-microsoft-appsource"></a>Power BI-vizualizáció letöltése és importálása a Microsoft AppSource-ról

1. A [Microsoft AppSource](https://appsource.microsoft.com) webhelyről kiindulva válassza az **Alkalmazások** lapot.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Látogasson el az [Alkalmazások találatainak oldalára](https://appsource.microsoft.com/marketplace/apps), ott megtekintheti az egyes kategóriák legnépszerűbb alkalmazásait, beleértve a *Power BI-alkalmazásokat*. Power BI-vizualizációkat keresünk, ezért szűkítse az eredményeket a navigációs panel listájában található **Power BI-vizualizációk** lehetőség kiválasztásával.

    ![AppSource-vizualizációk](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. Az AppSource minden egyes egyéni vizualizációhoz megjelenít egy csempét.  Minden csempe tartalmaz egy pillanatképet az egyéni vizualizációról, illetve egy rövid leírást és egy letöltési hivatkozást. További részletekért kattintson a csempére.

    ![Egyén vizualizáció kiválasztása](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. A részletek lapon többek között képernyőképeket, videókat és részletes leírásokat tekinthet meg. Az egyéni vizualizáció letöltéséhez kattintson a **Letöltés most** hivatkozásra, és fogadja el a használati feltételeket.

    ![Letöltés az AppSource-ból](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Kattintson az egyéni vizualizáció letöltési hivatkozására.

    ![Letöltés](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A letöltési oldal az egyéni vizualizációnak a Power BI Desktopba és a Power BI szolgáltatásba történő importálásával kapcsolatos útmutatást is tartalmaz.

    Egy mintajelentést is letölthet, amely tartalmazza az egyéni vizualizációt, és bemutatja annak képességeit.

    ![Minta kipróbálása](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Mentse a `.pbiviz`-fájlt, majd nyissa meg a Power BI-t.

7. Importálja a `.pbiviz`-fájlt a jelentésbe. (Lásd a fenti [Egyéni látványelem importálása](#import-a-custom-visual-from-a-file) szakaszt.)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Az egyéni vizualizáció az importálásakor az adott jelentéshez lesz hozzáadva. Ha egy másik jelentésben is használni szeretné a vizualizációt, abba a jelentésbe is importálnia kell. Ha egy egyéni vizualizációval rendelkező jelentést a **Mentés másként** lehetőséggel ment, az új jelentéssel együtt az egyéni vizualizáció egy másolata is mentve lesz.

* Ha nem látja a **Vizualizációk** panelt, akkor nem rendelkezik a jelentés szerkesztéséhez szükséges engedélyekkel.  Csak azokhoz a jelentésekhez adhat hozzá Power BI-vizualizációkat, amelyek szerkesztésére jogosult, az Önnel csak megosztott jelentésekhez nem.

## <a name="troubleshoot"></a>Hibaelhárítás

A hibaelhárításról a [Power BI-vizualizációk hibaelhárítása](power-bi-custom-visuals-troubleshoot.md) című cikkből tájékozódhat.

## <a name="faq"></a>Gyakori kérdések

További információt és válaszokat [a Power BI-vizualizációkkal kapcsolatos gyakori kérdések](power-bi-custom-visuals-faq.md#organizational-visuals) között talál.

## <a name="next-steps"></a>Következő lépések

* [Vizualizációk Power BI-jelentésekben](../visuals/power-bi-report-visualizations.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/).
