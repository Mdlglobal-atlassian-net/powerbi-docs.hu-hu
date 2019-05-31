---
title: Egyéni vizualizációk a Power BI-ban
description: Egyéni vizualizációk a Power BI-ban
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 3fd2f3e47c9b6dd2144ed5a66d45e65a00c5b92e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051237"
---
# <a name="custom-visuals-in-power-bi"></a>Egyéni vizualizációk a Power BI-ban

Létrehozásakor, vagy a Power BI-jelentés szerkesztése, használhatja a számos különböző vizualizációtípust. Ezek a Vizualizációk a ikonjai megjelennek a **Vizualizációk** ablaktáblán. Ezek a Vizualizációk előrecsomagolt származnak, amikor letölti [Power BI Desktop](https://powerbi.microsoft.com/desktop/) , vagy nyissa meg a [Power BI szolgáltatás](https://app.powerbi.com).

![vizualizációk](media/power-bi-custom-visuals/power-bi-visualizations.png)

Ön azonban nem a Vizualizációk egy készlete korlátozott. Ha kiválasztja a három pontra (...) a lap alján, egy másik forrását jelentésvizualizációk válik érhető el –*egyéni Vizualizációk*.

A fejlesztők az egyéni Vizualizációk SDK használatával egyéni Vizualizációk létrehozása. Ezek a Vizualizációk engedélyezése az üzleti felhasználók számára olyan módon, hogy a leginkább megfelel az üzleti adatok. Jelentések szerzői Ezután importálja az egyéni vizualizációfájlok jelentéseikbe és használja őket, mint bármely más Power BI-Vizualizációk. Egyéni Vizualizációk a Power BI első osztályú állampolgárok és szűrhetők, kiemelt, szerkesztett, megosztott és így tovább.

Egyéni Vizualizációk háromféle módon vannak telepítve:

* Egyéni vizualizációfájlok
* Szervezeti vizualizációk
* Piactér-vizualizációk

## <a name="custom-visual-files"></a>Egyéni vizualizációfájlok

Egyéni Vizualizációk olyan csomagok, a kód szolgáltatott adatok rendereléséhez szükséges őket. Bárki hozzon létre egy egyéni vizualizációt és Becsomagolhatja azt egy `.pbiviz` fájlt, majd importálhatja a Power BI-jelentés.

> [!WARNING]
> Az egyéni Vizualizációk biztonsági vagy adatvédelmi kockázatot kódot tartalmazhatnak. Győződjön meg arról, hogy megbízik a szerzőben és egyéni Vizualizáció forráskódja mielőtt importálná azokat a jelentésbe.

## <a name="organizational-visuals"></a>Szervezeti vizualizációk

Power BI-rendszergazdák hagyja jóvá, és helyezze üzembe az egyéni Vizualizációk szervezet, amely a jelentéskészítők könnyen felderítése, frissítheti, és használja. A rendszergazdák egyszerűen kezelhetik (például verziójának frissítése, letilthatják vagy engedélyezhetik) ezek a Vizualizációk.

 [További információk a szervezeti Vizualizációk](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Piactér-vizualizációk

Közösség tagjai és a Microsoft rendelkezik hozzájárult az egyéni vizualizációikat nyilvános juttatásra, és közzétette őket a [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) Marketplace-en. Ezeket letöltheti a Power BI-jelentések azokat hozzá Vizualizációk. A Microsoft tesztelt és jóváhagyott működés és minőség ezeket az egyéni vizualizációkat.

Mi az az [AppSource](developer/office-store.md)? Legyen a hely, ahol annak alkalmazásokat, beépülő modulok és bővítmények a Microsoft-szoftverekhez. [Appsource-ban](https://appsource.microsoft.com/) millió felhasználójának termékek, például az Office 365, Azure, Dynamics 365, Cortana és a Power BI-megoldásokat, amelyekkel való munkavégzés hatékonyabban, részletgazdagabban, és lenyűgöző formában, mint korábban.

### <a name="certified-visuals"></a>Hitelesített vizualizációk

A Power BI minősítéssel rendelkező Vizualizációk, amelyek megfeleltek a további szigorú minőségi tesztelése és további forgatókönyvek, például a támogatott Piactéri Vizualizációk [e-mailes előfizetések](https://docs.microsoft.com/power-bi/service-report-subscribe), és [exportálás a PowerPointba](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
A minősített egyéni vizualizációk listájának megtekintéséhez vagy saját vizualizáció közzétételéhez lásd a [minősített egyéni vizualizációkat](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) ismertető szakaszt.

Ön olyan webfejlesztő, aki szeretne saját vizualizációkat létrehozni, és hozzáadni azokat az AppSource-hoz? Lásd: [Power BI egyéni Vizualizációk fejlesztésével](developer/custom-visual-develop-tutorial.md) , és ismerje meg, hogyan [egyéni Vizualizációk közzététele az appsource-ban](https://docs.microsoft.com/power-bi/developer/office-store).

### <a name="import-a-custom-visual-from-a-file"></a>Egyéni vizualizáció importálása fájlból

1. Kattintson a három pontra alján a **Vizualizációk** ablaktáblán.

    ![Vizualizációk2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. A legördülő listából válassza az **Importálás fájlból** lehetőséget.

    ![Importálás fájlból](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. A fájl megnyitása menüben válassza a `.pbiviz` fájlt, amelyet szeretne importálni, majd **nyílt**. Az egyéni Vizualizáció ikonja alján hozzáadódik a **Vizualizációk** ablaktáblán, és most használatra kész a jelentés.

    ![Importált egyéni vizualizáció](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Szervezeti vizualizációk importálása

1. Kattintson a három pontra alján a **Vizualizációk** ablaktáblán.

    ![1. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. A legördülő listából válassza az **Importálás a piactérről** lehetőséget.

    ![2. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Válassza a **SAJÁT SZERVEZET** lehetőséget a felső lap menüjében.

    ![3. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Tekintse át a listát, és keresse meg az importálni kívánt vizualizációt.

    ![4. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Válassza ki **Hozzáadás** az egyéni Vizualizáció importálása. Ikonjára alján hozzáadódik a **Vizualizációk** ablaktáblán, és most használatra kész a jelentés.

    ![5. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Egyéni vizualizáció letöltése vagy importálása a Microsoft AppSource-ról

Letöltéséhez és importálásához az egyéni Vizualizációk két lehetősége van: a Power BI-ban, és a a [AppSource webhelyen](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Egyéni vizualizációk importálása a Power BI-on belül

1. Kattintson a három pontra alján a **Vizualizációk** ablaktáblán.

    ![Vizualizációk 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. A legördülő listából válassza az **Importálás a piactérről** lehetőséget.

    ![2. szervezeti vizualizáció](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Tekintse át a listát, és keresse meg az importálni kívánt vizualizációt.

    ![vizualizáció importálása](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Az egyes vizualizációk kijelölésével további információkat tudhat meg róluk.

    ![Kiválasztás](media/power-bi-custom-visuals/power-bi-select.png)

5. A részletek lapon többek között képernyőképeket, videókat és részletes leírásokat tekinthet meg.

    ![Synoptic](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. A képernyő alján értékelések is találhatók.

    ![Értékelések](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Válassza ki **Hozzáadás** az egyéni Vizualizáció importálása. Ikonjára alján hozzáadódik a **Vizualizációk** ablaktáblán, és most használatra kész a jelentés.

    ![Importált vizualizáció](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Egyéni vizualizáció letöltése és importálása a Microsoft AppSource-ról

1. A [Microsoft AppSource](https://appsource.microsoft.com) webhelyről kiindulva válassza az **Alkalmazások** lapot.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Látogasson el az [Alkalmazások találatainak oldalára](https://appsource.microsoft.com/marketplace/apps), ott megtekintheti az egyes kategóriák legnépszerűbb alkalmazásait, beleértve a *Power BI-alkalmazásokat*. Egyéni Vizualizációk, ezért válassza számíthatunk **Power BI-Vizualizációk** a bal oldali navigációs listában az eredmények szűkítéséhez.

    ![AppSource-vizualizációk](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. Az AppSource minden egyes egyéni vizualizációhoz megjelenít egy csempét.  Mindegyik csempe rendelkezik egy egyéni vizuális pillanatkép egy rövid leírást és a egy letöltési hivatkozást. További részletekért kattintson a csempére.

    ![Egyén vizualizáció kiválasztása](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. A részletek lapon többek között képernyőképeket, videókat és részletes leírásokat tekinthet meg. Válassza ki **Letöltés most** az egyéni Vizualizáció letöltéséhez, és a használati feltételeket, majd fogadja el.

    ![Letöltés az AppSource-ból](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Kattintson az egyéni vizualizáció letöltési hivatkozására.

    ![Letöltés](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A letöltési oldalról is útmutatást nyújt az egyéni Vizualizáció importálása a Power BI Desktop és a Power BI szolgáltatásban.

    Egy mintajelentést is letölthet, amely tartalmazza az egyéni vizualizációt, és bemutatja annak képességeit.

    ![Minta kipróbálása](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Mentse a `.pbiviz` fájlt, és nyissa meg a Power bi-ban.

7. Importálás a `.pbiviz` fájlt a jelentésbe. (Lásd a fenti [Egyéni látványelem importálása](#import-a-custom-visual-from-a-file) szakaszt.)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Az egyéni vizualizáció az importálásakor az adott jelentéshez lesz hozzáadva. Ha egy másik jelentésben is használni szeretné a vizualizációt, abba a jelentésbe is importálnia kell. Ha egy egyéni vizualizációval rendelkező jelentést a **Mentés másként** lehetőséggel ment, az új jelentéssel együtt az egyéni vizualizáció egy másolata is mentve lesz.

* Ha nem látja a **Vizualizációk** panelen, amely azt jelenti, hogy az nem rendelkezik a jelentés szerkesztéséhez szükséges engedélyekkel.  Csak azokhoz a jelentésekhez adhat hozzá egyéni vizualizációkat, amelyek szerkesztésére jogosult, az Önnel megosztott jelentésekhez nem.

## <a name="troubleshoot"></a>Hibaelhárítás

Hibaelhárítása: [hibáinak elhárítása a Power BI egyéni vizualizációinak](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>Gyakori kérdések

További információt és válaszokat [az egyéni Power BI-vizualizációkkal kapcsolatos gyakori kérdések](power-bi-custom-visuals-faq.md#organizational-custom-visuals) között talál.

## <a name="next-steps"></a>Következő lépések

* [Vizualizációk a Power BI-jelentések](visuals/power-bi-report-visualizations.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/).
