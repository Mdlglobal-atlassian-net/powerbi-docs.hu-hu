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
ms.date: 02/17/2020
ms.openlocfilehash: 52a99380f8e1afc39ddfc59a401418e61fe6ad58
ms.sourcegitcommit: ec4d2d0f52d737e8e0583f6a7b16e6fd87382510
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782415"
---
# <a name="get-a-power-bi-visual-certified"></a>Power BI-vizualizáció minősíttetése

A minősített Power BI-vizualizációk azok az [AppSource-on](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) lévő Power BI-vizualizációk, amelyek megfelelnek a Microsoft Power BI csapatának [kódolási előírásainak](#certification-requirements). Ezeket a vizualizációkat tesztelik annak megerősítésére, hogy azok nem férnek hozzá külső szolgáltatásokhoz vagy erőforrásokhoz, és biztonságos kódolási mintákat és irányelveket követnek.

A minősítést szerzett Power BI-vizualizációk több funkcióval bírnak. Például [exportálhatók a PowerPointba](../consumer/end-user-powerpoint.md), és megjeleníthetők olyan e-mailekben, amelyek akkor érkeznek, amikor egy felhasználó [feliratkozik jelentésoldalakra](../consumer/end-user-subscribe.md).

A minősítési folyamat nem kötelező. Azok a Power BI-vizualizációk, amelyek nem tanúsítottak, nem feltétlenül nem biztonságosak. Egyes Power BI-vizualizációk azért nincsenek minősítve, mert nem felelnek meg egy vagy több [minősítésbeli követelménynek](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Ilyenek például a külső szolgáltatáshoz csatlakozó térkép típusú Power BI-vizualizációk vagy a kereskedelmi kódtárakat használó Power BI-vizualizációk.

> [!NOTE]
> A külső egyéni vizualizációknak nem a Microsoft a készítője. A külső vizualizációk működésének ellenőrzéséhez forduljon közvetlenül a vizualizáció készítőjéhez.

## <a name="certification-requirements"></a>Minősítési követelmények

A Power BI-vizualizáció [minősítéséhez](#get-a-power-bi-visual-certified) a Power BI-vizualizációnak meg kell felelnie az ebben a szakaszban felsorolt követelményeknek. 

### <a name="general-requirements"></a>Általános követelmények

A Power BI-vizualizációnak az Értékesítői információközpont vagy a Partnerközpont által jóváhagyottnak kell lennie. Ajánlott, hogy a Power BI-vizualizáció már az [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)-ban legyen. A Power BI-vizualizációk közzétételével kapcsolatos további információért lásd: [Power BI-vizualizációk közzététele a Partnerközpontban](office-store.md).

A Power BI-vizualizáció minősítésre való elküldése előtt ellenőrizze, hogy az megfelel-e a [Power BI-vizualizációkra vonatkozó irányelveknek](./guidelines-powerbi-visuals.md).

A Power BI-vizualizáció elküldésekor győződjön meg arról, hogy a lefordított csomag pontosan megfelel a beküldött csomagnak.

### <a name="code-repository-requirements"></a>Kódtárkövetelmények

Habár nem kell nyilvánosan megosztania a kódot a GitHubon, a Power BI csapata számára elérhetővé kell tennie a kódtárat felülvizsgálatra. Ennek az a legjobb módja, ha a (JavaScript- vagy TypeScript-) forráskódot megadja a GitHubban.

Az adattárnak tartalmaznia kell az alábbiakat:
* Kód egyetlen Power BI-vizualizációhoz. Nem tartalmazhatja több Power BI-vizualizáció kódját, vagy nem kapcsolódó kódot.
* Egy **certification** nevű ág. A névnek kisbetűsnek kell lennie. Az ebben az ágban található forráskódnak meg kell egyeznie a beküldött csomaggal. Ezt a kódot csak a következő beküldési folyamat során lehet frissíteni, ha újra beküldi a Power BI-vizualizációt.

Ha a Power BI-vizualizáció privát NPM-csomagokat vagy git-almodulokat használ, hozzáférést kell biztosítania az ezen kódot tartalmazó további adattárakhoz.

Ha kíváncsi arra, hogy miként néz ki egy Power BI-vizualizációkhoz használható adattár, tanulmányozza a [Power BI-vizualizációkhoz készült mintasávdiagram](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi) GitHub-adattárát.

### <a name="file-requirements"></a>Fájlkövetelmények

A Power BI-vizualizáció írásához használja az API legújabb verzióját.

A tárháznak tartalmaznia kell a következő fájlokat:
* **.gitignore** – Adja hozzá a `node_modules` mappát ehhez a fájlhoz. A kód nem tartalmazhatja a *node_modules* mappát.
* **capabilities.json** – Ha a Power BI-vizualizáció egy újabb verzióját küldi be a fájlban található tulajdonságok módosításaival, győződjön meg arról, hogy ezek nem okozzák-e a jelentések meghibásodását a meglévő felhasználók számára.
* **pbiviz.json**
* **package.json**
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Parancskövetelmények

Győződjön meg arról, hogy a következő parancsok nem adnak vissza hibákat.

* `npm install`
* `pbiviz package`
* `npm audit` – Nem adhat vissza közepes vagy magas szintű figyelmeztetéseket.
* [Microsoft TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib), felülbírált konfiguráció nélkül. Ez a parancs nem eredményezhet lint-hibát.

### <a name="compiling-requirements"></a>Fordítási követelmények

A Power BI-vizualizáció írásához használja a [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) legújabb verzióját.

Le kell fordítania a Power BI-vizualizációt a `pbiviz package` paranccsal. Ha saját buildelési szkriptet használ, adjon meg egy egyéni `npm run package` buildelési parancsot.



### <a name="source-code-requirements"></a>Forráskódra vonatkozó követelmények

Győződjön meg arról, hogy követi a [Power BI-vizualizációk kiegészítő minősítési](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification) szabályzatainak listáját. Ha a beküldés nem követi ezeket az irányelveket, akkor a Partnerközpont elutasítási e-mailje tartalmazni fogja a hivatkozáson felsorolt szabályzatszámokat.

Kövesse a lent felsorolt kódkövetelményeket, és győződjön meg arról, hogy a kód összhangban van a Power BI minősítési szabályzataival.  

**Kötelező**
* Csak nyilvános, ellenőrizhető OSS-összetevőket, például nyilvános JavaScript- vagy TypeScript-kódtárakat használjon.
* A kódnak támogatnia kell az [események renderelési API-ját](./visuals/event-service.md).
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

>[!NOTE]
> Ha már megkezdte egy Power BI-vizualizáció beküldésének folyamatát, és az [Értékesítői irányítópultot](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (a régi kezelőeszközt) kell használnia, akkor tekintse át a [Beküldése az Értékesítői irányítópult használatával](seller-dashboard.md#seller-dashboard-certification-submission-process) című útmutatót.

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

## <a name="certified-power-bi-visuals"></a>Minősített Power BI-vizualizációk

A minősített Power BI-vizualizációk az alábbiakban vannak felsorolva. A Power BI-vizualizáció AppSource-ban történő megnyitásához kattintson a hivatkozásra. Ha rendelkezésre áll videó, akkor azt a videó-hivatkozásra kattintva tekintheti meg.

* [3AG Systems – sávdiagram abszolút eltéréssel](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems – sávdiagram relatív eltéréssel](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG Systems – oszlopdiagram relatív eltéréssel](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems – oszlopdiagram eltéréssel](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Speciális gyűrűvizualizáció (teljes kiadás)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Speciális gyűrűvizualizáció (egyszerűsített kiadás)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Speciális gráfvizualizáció](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Speciális hálózati vizualizáció](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Speciális idősoros vizualizáció (teljes kiadás)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Őszirózsa diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Csokornyakkendő diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Doboz diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Doboz diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Tégladiagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Buborékdiagram az Akvelontól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Skáladiagram vizualizáció](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755), **[videó-hivatkozás](https://youtu.be/AOlsFYkfkcw)**
* [Skáladiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Skáladiagram (készítette: OKViz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[videó-hivatkozás](https://youtu.be/mtvUNl9bMjA)**
* [Naptár (készítette: MAQ Software)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Naptár a Tallantól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Gyertya (készítette: OKViz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[videó-hivatkozás](https://youtu.be/nT_18gyRxPo)**
*  [Államokkal ellátott kártyák az OKviztől](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Gombsorszeletelő](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Körszeletdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[videó-hivatkozás](https://youtu.be/AQvd2FhRyCI)**
*  [Kör alakú mérőműszer a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Fürttérkép](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Egyéni naptár (készítette Akvelon)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Hengeres mérőműszer a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Tárcsadiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Pöttydiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Pöttydiagram (készítette: OKViz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[videó-hivatkozás](https://youtu.be/By16pX9KT40)**
*  [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Lefúrásos oszlopdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[videó-hivatkozás](https://youtu.be/lBy2gQQ5YsQ)**
*  [Lefúrásos oszlopdiagram időalapú adatokhoz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[videó-hivatkozás](https://youtu.be/T_mRou18vx0)**
*  [Lefúrásos fánkdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[videó-hivatkozás](https://youtu.be/AUVFrSHmPeo)**
*  [Kettős KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dinamikus elemleírás a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Bővített pontdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[videó-hivatkozás](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Gofridiagram az Enlightentől](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Lista szerinti szűrés (készítette: Devscope)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[videó-hivatkozás](https://youtu.be/RetEWGwBu0I)**
*  [Erőgrafikon](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[videó-hivatkozás](https://youtu.be/YsTa7uyJ4sg)**
*  [Tölcsér forrással a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[videó-hivatkozás](https://youtu.be/qJ7s_KrGiUU)**
* [Gantt-diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Földgömb adatsávok](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Rács a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchiadiagram (készítette: Akvelon)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[videó-hivatkozás](https://youtu.be/0ZGzJaq_KT4)**
*  [Hisztogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Pontokkal rendelkező hisztogram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Vízszintes sávdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Vízszintes tölcsér a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Image a CloudScope-tól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Képrács](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infografika-tervező](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [KPI-diagram az Akvelontól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [KPI-oszlop a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [KPI-rács a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI-kijelző](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI-szalagcím a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Lineáris mérőműszer a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [Vonalpontos diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[videó-hivatkozás](https://youtu.be/90FLCKpgicA)**
*  [Több KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Áttekintés a CloudScope-tól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Lejátszási tengely (dinamikus szeletelő)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Nagy teljesítményű KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) [videó-hivatkozás](https://youtu.be/IvfIP3E6-1Q)
*  [Nagy teljesítményű KPI-mátrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) **[videó-hivatkozás](https://youtu.be/1enze8pcGzY)**
*  [Pulzusdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[videó-hivatkozás](https://youtu.be/DQWdcQtjDVw)**
*  [Quadrant-diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Sugárdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Gyűrűdiagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Forgó diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[videó-hivatkozás](https://youtu.be/WWP9wVUHGaA)**
*  [Pontdiagram az Akvelontól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Görgető](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Intelligens szűrő (készítette: OKViz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[videó-hivatkozás](https://youtu.be/gcJsDDRQq28)**
*  [Értékgörbe (készítette: OKViz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[videó-hivatkozás](https://youtu.be/0m3Vnvso9tY)**
*  [Adatfolyam-grafikon](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Többszintű gyűrű](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Szinoptikus panel az OKViztől](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Hőtérképtábla](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Fordulatszámmérő](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[videó-hivatkozás](https://youtu.be/C3OXdETbS9o)**
*  [Szövegszűrő](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Szövegburkoló a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Hőmérő a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Időecset-szeletelő](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Idővonal-szeletelő](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[videó-hivatkozás](https://youtu.be/ozMtZ4_NZ10)**
*  [Idővonal (készítette: CloudScope)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [videó-hivatkozás](https://youtu.be/szNi9YgXFJc)
*  [Tornádódiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[videó-hivatkozás](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Kereskedelmi diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI-kártya](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate variancia](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[videó-hivatkozás](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[videó-hivatkozás](https://youtu.be/0BZsVCQdEkc)**
*  [Felhasználólista a CloudScope-tól](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Venn-diagram a MAQ Software-től](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Hegedűdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio-vizualizáció](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Gofridiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[videó-hivatkozás](https://youtu.be/1vRqYUsm3Vk)**
*  [Szófelhő](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[videó-hivatkozás](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Gyakori kérdések

A vizualizációkkal kapcsolatban a [Gyakori kérdések a hitelesített vizualizációkról](power-bi-custom-visuals-faq.md#certified-power-bi-visuals) weblapon talál további információt.

## <a name="next-steps"></a>Következő lépések

* [Egyéni Power BI-vizualizáció fejlesztése](../developer/custom-visual-develop-tutorial.md)
* [A Microsoft az egyéni vizualizációkat bemutató lejátszási listája a YouTube-on](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Vizualizációk a Power BI-ban](../visuals/power-bi-report-visualizations.md)  
* [Egyéni vizualizációk a Power BI-ban](power-bi-custom-visuals.md)  
* [Power BI-vizualizációk közzététele a Microsoft AppSource-ban](../developer/office-store.md) 
* Ha Ön webfejlesztőként szeretne saját Power BI-vizualizációkat létrehozni és felvenni azokat a  [Microsoft AppSource-ban](https://appsource.microsoft.com), kezdje a  [Power BI-vizualizációk fejlesztése](visuals/custom-visual-develop-tutorial.md) című oktatóanyaggal. 

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
