---
title: Minősített Power BI-vizualizációk
description: Az egyéni vizualizációk minősítésre való beküldésének követelményei és folyamata, illetve a minősített Power BI-vizualizációk listája.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: b759d19046ddb375646743a50025689ab9a566c0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82613534"
---
# <a name="get-a-power-bi-visual-certified"></a>Power BI-vizualizáció minősíttetése

A minősített Power BI-vizualizációk azok az [AppSource-on](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) lévő Power BI-vizualizációk, amelyek megfelelnek a Microsoft Power BI csapatának [kódolási előírásainak](#certification-requirements). Ezeket a vizualizációkat tesztelik annak megerősítésére, hogy azok nem férnek hozzá külső szolgáltatásokhoz vagy erőforrásokhoz, és biztonságos kódolási mintákat és irányelveket követnek.

A minősítést szerzett Power BI-vizualizációk több funkcióval bírnak. Például [exportálhatók a PowerPointba](../../consumer/end-user-powerpoint.md), és megjeleníthetők olyan e-mailekben, amelyek akkor érkeznek, amikor egy felhasználó [feliratkozik jelentésoldalakra](../../consumer/end-user-subscribe.md).

A minősítési folyamat nem kötelező. Azok a Power BI-vizualizációk, amelyek nem tanúsítottak, nem feltétlenül nem biztonságosak. Egyes Power BI-vizualizációk azért nincsenek minősítve, mert nem felelnek meg egy vagy több [minősítési követelménynek](power-bi-custom-visuals-certified.md#certification-requirements). Ilyenek például a külső szolgáltatáshoz csatlakozó térkép típusú Power BI-vizualizációk vagy a kereskedelmi kódtárakat használó Power BI-vizualizációk.

> [!NOTE]
> A külső egyéni vizualizációknak nem a Microsoft a készítője. A külső vizualizációk működésének ellenőrzéséhez forduljon közvetlenül a vizualizáció készítőjéhez.

## <a name="certification-requirements"></a>Minősítési követelmények

A Power BI-vizualizáció [minősítéséhez](#get-a-power-bi-visual-certified) a Power BI-vizualizációnak meg kell felelnie az ebben a szakaszban felsorolt követelményeknek. 

### <a name="general-requirements"></a>Általános követelmények

A Power BI-vizualizációnak a Partnerközpont által jóváhagyottnak kell lennie. Ajánlott, hogy a Power BI-vizualizáció már az [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)-ban legyen. A Power BI-vizualizációk közzétételével kapcsolatos további információért lásd: [Power BI-vizualizációk közzététele a Partnerközpontban](office-store.md).

A Power BI-vizualizáció minősítésre való elküldése előtt ellenőrizze, hogy az megfelel-e a [Power BI-vizualizációkra vonatkozó irányelveknek](guidelines-powerbi-visuals.md).

A Power BI-vizualizáció elküldésekor győződjön meg arról, hogy a lefordított csomag pontosan megfelel a beküldött csomagnak.

### <a name="code-repository-requirements"></a>Kódtárkövetelmények

Nem kell nyilvánosan megosztania a kódot a GitHubon, a Power BI csapata számára azonban elérhetővé kell tennie a kódtárat felülvizsgálatra. Ennek az a legjobb módja, ha a (JavaScript- vagy TypeScript-) forráskódot megadja a GitHubban.

Az adattárnak tartalmaznia kell az alábbiakat:
* Kód egyetlen Power BI-vizualizációhoz. Nem tartalmazhatja több Power BI-vizualizáció kódját, vagy nem kapcsolódó kódot.
* Egy **certification** nevű ág. A névnek kisbetűsnek kell lennie. Az ebben az ágban található forráskódnak meg kell egyeznie a beküldött csomaggal. Ezt a kódot csak a következő beküldési folyamat során lehet frissíteni, ha újra beküldi a Power BI-vizualizációt.

Ha a Power BI-vizualizáció privát NPM-csomagokat vagy git-almodulokat használ, hozzáférést kell biztosítania az ezen kódot tartalmazó további adattárakhoz.

Ha kíváncsi arra, hogy miként néz ki egy Power BI-vizualizációkhoz használható adattár, tanulmányozza a [Power BI-vizualizációkhoz készült mintasávdiagram](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) GitHub-adattárát.

### <a name="file-requirements"></a>Fájlkövetelmények

A Power BI-vizualizáció írásához használja az API legújabb verzióját.

A tárháznak tartalmaznia kell a következő fájlokat:
* **.gitignore** – Adja hozzá a `node_modules`, a `.tmp` és a `dist` elemet ehhez a fájlhoz. A kód nem tartalmazhatja a *node_modules*, a *.tmp* vagy a *dist* mappát.
* **capabilities.json** – Ha a Power BI-vizualizáció egy újabb verzióját küldi be a fájlban található tulajdonságok módosításaival, győződjön meg arról, hogy ezek nem okozzák-e a jelentések meghibásodását a meglévő felhasználók számára.
* **pbiviz.json** 
* **package.json**. A vizualizációban telepítve kell lennie az alábbi csomagnak:
   * ["tslint"](https://www.npmjs.com/package/tslint) – 5.18.0-s vagy újabb verzió
   * ["typescript"](https://www.npmjs.com/package/typescript) – 3.0.0-s vagy újabb verzió
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib) – 6.2.0-s vagy újabb verzió
   * A fájlnak tartalmaznia a linter futtatására vonatkozó parancsot – `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Parancskövetelmények

Győződjön meg arról, hogy a következő parancsok nem adnak vissza hibákat.

* `npm install`
* `pbiviz package`
* `npm audit` – Nem adhat vissza közepes vagy magas szintű figyelmeztetéseket.
* [Microsoft TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib) a [szükséges konfigurációval](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Ez a parancs nem eredményezhet lint-hibát.

### <a name="compiling-requirements"></a>Fordítási követelmények

A Power BI-vizualizáció írásához használja a [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) legújabb verzióját.

Le kell fordítania a Power BI-vizualizációt a `pbiviz package` paranccsal. Ha saját buildelési szkriptet használ, adjon meg egy egyéni `npm run package` buildelési parancsot.

### <a name="source-code-requirements"></a>Forráskódra vonatkozó követelmények

Győződjön meg arról, hogy követi a [Power BI-vizualizációk kiegészítő minősítési](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification) szabályzatainak listáját. Ha a beküldés nem követi ezeket az irányelveket, akkor a Partnerközpont elutasítási e-mailje tartalmazni fogja a hivatkozáson felsorolt szabályzatszámokat.

Kövesse a lent felsorolt kódkövetelményeket, és győződjön meg arról, hogy a kód összhangban van a Power BI minősítési szabályzataival.  

**Kötelező**
* Csak nyilvános, ellenőrizhető OSS-összetevőket, például nyilvános JavaScript- vagy TypeScript-kódtárakat használjon.
* A kódnak támogatnia kell az [események renderelési API-ját](event-service.md).
* Győződjön meg arról, hogy a DOM biztonságosan van kezelve. Alkalmazzon tisztítást a felhasználói bevitelre vagy a felhasználói adatokra, mielőtt hozzáadja azokat a DOM-hoz.
* Ezt a [mintajelentést](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) használja tesztelési adatkészletként.

**Nem engedélyezett**
* Kapcsolódás külső szolgáltatásokhoz vagy erőforrásokhoz. Például nem mehet ki HTTP/S- vagy WebSocket-kérelem a Power BI-ból egyetlen szolgáltatáshoz sem.
* Az `innerHTML` vagy a `D3.html(user data or user input)` használatával.
* Ügyeljen arra, hogy a böngésző konzoljában ne legyenek javaScript-hibák vagy -kivételek a bevitt adatokra vonatkozóan.
* Tetszőleges vagy dinamikus kód, például `eval()`, illetve a `settimeout()`, a `requestAnimationFrame()`, a `setinterval(user input function)` és felhasználói adatbevitel vagy felhasználói adatok nem biztonságos használata.
* Minimalizált JavaScript-fájlok vagy -projektek.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Power BI-vizualizáció beküldése minősítésre

A Power BI-vizualizáció hitelesítését a Partnerközpontban kérheti a Power BI csapatától.

>[!TIP]
>A Power BI minősítési folyamata időt vehet igénybe. Új Power BI-vizualizáció létrehozása esetén a Power BI-tanúsítvány igénylése előtt javasoljuk a Power BI-vizualizáció Partnerközponton keresztüli közzétételét. Így gondoskodhat a vizualizáció késlekedés nélküli közzétételéről.

Power BI-minősítés igénylése:

1. Jelentkezzen be a Partnerközpontba.
2. Az **Áttekintés lapon** válassza ki a Power BI-vizualizációt, és lépjen a **Termékbeállítás** lapra.
3. Jelölje be a **Power BI-minősítés igénylése** lehetőséget.
4. Az **Áttekintés és közzététel** oldalon, a **Megjegyzések a minősítéshez** mezőben adja meg a forráskódra mutató hivatkozást és a hozzáféréshez szükséges hitelesítő adatokat.

### <a name="private-repository-submission-process"></a>Privát adattárral történő beküldés folyamata

Ha privát adattárt (például a GitHubot) használva szeretné beküldeni Power BI-vizualizációját tanúsításra, végezze el az ebben a szakaszban található lépéseket.
1. Hozzon létre egy új fiókot az érvényesség-ellenőrzési csapatnak.
2. Állítsa be a fiókjához a [kétfaktoros hitelesítést](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa).
3. [Hozzon létre egy új helyreállításikód-készletet](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. A Power BI-vizualizáció beküldésekor adja meg a következőket:
    * Az adattár hivatkozása
    * Bejelentkezési hitelesítő adatok (köztük a jelszó)
    * Helyreállítási kódok
    * Írásvédett engedélyek a fiókunkhoz ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>Minősített Power BI-vizualizációk jelvényei

A minősített Power BI-vizualizációk egy kijelölt jelvényt kapnak, amely a minősítést jelzi.

### <a name="certified-power-bi-visuals-in-appsource"></a>Minősített Power BI-vizualizációk az AppSource-ban

* Amikor online keresi a [Power BI-vizualizációkat az AppSource-ban](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), a vizualizáció kártyáján egy kis sárga színű jelvény jelzi, hogy minősített Power BI-vizualizációról van szó.

    ![Minősített Power BI-vizualizáció az AppSource-ban](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* Miután a Power BI-vizualizáció kártyájára kattint az AppSource-ban, a *PBI Certified* feliratú sárga színű jelvény jelzi, hogy a szóban forgó Power BI-vizualizáció minősítéssel rendelkezik.

    ![Minősített Power BI-vizualizáció az alkalmazás lapján](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Minősített Power BI-vizualizációk a Power BI felületén

* Power BI-vizualizáció a Power BI-ból (Desktop vagy szolgáltatás) történő importálása esetén kék színű jelvény jelzi, hogy a Power BI-vizualizáció minősített.

    ![Minősített Power BI-vizualizáció a Power BI felületén](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* Csak minősített Power BI-vizualizációk jeleníthetők meg a *Power BI Certified* szűrési lehetőség kiválasztásával.

## <a name="publication-timeline"></a>Közzététel idővonala

Az AppSource-ban való üzembe helyezés eltarthat egy ideig. A Power BI-vizualizáció a folyamat befejezése után lesz letölthető az AppSource-ról.

### <a name="when-will-users-be-able-to-download-my-visual"></a>Mikor töltheti le a felhasználók a vizualizációmat?

* Egy Power BI-vizualizáció első beküldése után a felhasználók néhány órával azt követően tölthetik le, hogy Ön e-mailt kap az AppSource-tól.

* Ha egy meglévő Power BI-vizualizációt frissített, a felhasználók a beküldést követően egy hónapon belül letölthetik azt.

    >[!NOTE]
    > Az AppSource *verzió* mezője arra a napra módosul, amikor a Power BI-t jóváhagyta az AppSource, körülbelül egy héttel a vizualizáció beküldése után. A felhasználók letölthetik a frissített vizualizációt, azonban a frissített funkciók nem alkalmazhatók. A vizualizáció új funkciói körülbelül egy hónappal később használhatók a jelentéseken. 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>Mikor jelenik meg minősítési jelvény a Power BI-vizualizációmon?

* Ha először küldött be egy Power BI-vizualizációt, a minősítési jelvény az AppSource-tól kapott jóváhagyási e-mailt követő napon jelenik meg.

* Ha egy meglévő Power BI-vizualizációhoz kér minősítést, a jelvény a beküldést követő egy hónapon belül jelenik meg.

## <a name="next-steps"></a>Következő lépések

* Ha Ön webfejlesztőként szeretne saját Power BI-vizualizációkat létrehozni és felvenni azokat a  [Microsoft AppSource-ban](https://appsource.microsoft.com), kezdje a  [Power BI-vizualizációk fejlesztése](custom-visual-develop-tutorial.md) című oktatóanyaggal.

* A vizualizációkkal kapcsolatban a [Gyakori kérdések a hitelesített vizualizációkról](power-bi-custom-visuals-faq.md#certified-power-bi-visuals) weblapon talál további információt.

* [Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md)

* [A Microsoft a Power BI-vizualizációkat bemutató lejátszási listája a YouTube-on](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Vizualizációk a Power BI-ban](power-bi-custom-visuals.md)

* [Power BI-vizualizációk közzététele a Microsoft AppSource-ban](office-store.md)

* További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)