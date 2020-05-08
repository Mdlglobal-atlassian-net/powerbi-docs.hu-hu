---
title: Használati metrikák figyelése az új munkaterületi felhasználói felületen
description: A Power BI-irányítópultok és jelentések használati metrikáinak megtekintése, mentése és használata az új munkaterületi felhasználói felületen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/22/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: d3f359ad4c968407dff143458b65954844f9a22d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76829282"
---
# <a name="monitor-usage-metrics-in-the-new-workspace-experience"></a>Használati metrikák figyelése az új munkaterületi felhasználói felületen

A tartalom felhasználási módjának ismerete segít az eredményesség szemléltetésében és a feladatok fontossági sorrendjének felállításában. Egy használati metrika megmutathatja, hogy az egyik jelentést naponta használja a szervezet egy jelentős része, vagy éppen azt, hogy egy létrehozott irányítópultot senki sem tekint meg. Az ilyen visszajelzés felbecsülhetetlen értékű útmutatást nyújt a munkaszervezésben.

Ha modern munkaterületeken készít jelentéseket, jobb használatimetrika-jelentésekhez juthat, amelyekkel megtudhatja, hogy hogyan használják a jelentéseket a vállalatnál, és hogy kik használják azokat. A teljesítménnyel kapcsolatos magas szintű problémákat is azonosíthatja. A modern munkaterületi felhasználói felület továbbfejlesztett használati jelentései a [Power BI-irányítópultok és -jelentések használati metrikáinak figyelése](service-usage-metrics.md) című cikkben dokumentált meglévő használati metrikai jelentések helyét veszik át.

![Az új használatmetrikai-jelentés](media/service-modern-usage-metrics/power-bi-modern-usage-metrics.png)

> [!NOTE]
> Használati metrikai jelentéseket csak a Power BI szolgáltatásban futtathat. A mentett, vagy irányítópulton rögzített használati metrikák azonban mobileszközökön is megnyithatók és kezelhetők.

## <a name="prerequisites"></a>Előfeltételek

- A használati metrikai adatok futtatásához és eléréséhez Power BI Pro-licenc szükséges. A használati metrika funkció azonban a hozzájuk rendelt licenc típusától függetlenül minden felhasználónál rögzíti a használattal kapcsolatos adatokat.
- Egy jelentés fejlett használati metrikáit csak akkor érheti el, ha a jelentés egy modern munkaterületen helyezkedik el, Önnek pedig a jelentésre vonatkozó szerkesztési hozzáféréssel kell rendelkeznie.
- A tartalomkészítők számára a Power BI-rendszergazda által engedélyezve kell lenniük a használati metrikáknak. A Power BI-rendszergazda a felhasználónkénti adatok használati metrikákban való gyűjtését is engedélyezheti. Tovább tájékozódhat [ezeknek a beállításoknak a felügyeleti portálon való engedélyezéséről](service-admin-portal.md#control-usage-metrics).

## <a name="create--view-an-improved-usage-metrics-report"></a>Fejlett használatimetrika-jelentés létrehozása és megtekintése

A továbbfejlesztett használatimetrika-jelentéseket csak a rendszergazda, tag vagy közreműködő engedélyekkel rendelkező felhasználók tekinthetik meg. A megtekintő engedélyek nem elégségesek. Ha Ön legalább közreműködő azon a modern munkaterületen, ahol a jelentés található, az alábbi eljárással jelenítheti meg a fejlett használati metrikákat:

1. Nyissa meg a munkaterületet, ahol az a jelentés található, amelynek használati metrikáit elemezni szeretné.
2. A munkaterület tartalomlistáján a jelentés helyi menüjét megnyitva kiválaszthatja a **Használatimetrika-jelentés megtekintése** lehetőséget. Egy másik módszer, hogy a jelentést megnyitása után megnyitja a parancssáv helyi menüjét, és a **Használati metrikák** lehetőséget választja.

    ![A Használati metrikák lehetőség kiválasztása](media/service-modern-usage-metrics/power-bi-modern-view-usage-metrics.png)

1. Amikor először teszi ezt, a Power BI létrehozza a használati metrikai jelentést, és értesíti önt, amikor elkészült.

    ![A használatimetrika-jelentés elkészült](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-ready.png)

1. Az eredmény megtekintéséhez válassza a **Használati metrikák megtekintése** lehetőséget.
2. Amikor először teszi ezt, a Power BI esetleg a régi használatimetrika-jelentést nyitja meg. A továbbfejlesztett metrikajelentés megjelenítéséhez állítsa **Be** helyzetbe a jobb felső sarokban található Új használati jelentés kapcsolót.

    ![Átváltás a modern használatimetrika-jelentésre](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-on.png)

    > [!NOTE]
    > Az Új használati jelentés kapcsoló csak akkor jelenik meg, ha a jelentés modern munkaterületen van. Az örökölt munkaterületek nem kínálnak továbbfejlesztett használatimetrika-jelentéseket.

## <a name="about-the-improved-usage-metrics-report"></a>Tudnivalók a továbbfejlesztett használatimetrika-jelentésről

Ha a továbbfejlesztett használatimetrika-jelentést a fenti eljárással jeleníti meg, a Power BI egy előre elkészített jelentést generál a tartalom elmúlt 30 napi használati metrikáival. A jelentés azokhoz a már jól ismert Power BI-jelentésekhez hasonló. Szeletelhető az alapján, hogy a felhasználók hogyan kaptak hozzáférést, és hogy weben, mobilalkalmazáson vagy más lehetőségen keresztül érték el. A jelentések változásait az új adatokkal naponta frissülő használatimetrika-jelentések is tükrözik.

> [!NOTE]
> A használatimetrika-jelentések nem jelennek meg a Legutóbbiak, a Munkaterületek, a Kedvencek vagy más tartalomlistákon. Nem lehet őket hozzáadni egy alkalmazáshoz. Ha egy használati metrikai jelentésből származó csempét hozzáad egy irányítópulthoz, akkor az az irányítópult már nem adható hozzá alkalmazáshoz.

### <a name="usage-metrics-report-dataset"></a>Használatimetrika-jelentés adathalmaza

A továbbfejlesztett használatimetrika-jelentés a Usage Metrics Report adathalmazra épül, amelyet a Power BI automatikusan hoz létre a továbbfejlesztett használatimetrika-jelentés első megnyitásakor. A Power BI ezt követően naponta frissíti ezt az adathalmazt. Bár a frissítési ütemezést nem módosíthatja, a Power BI által használt hitelesítő adatok módosításával frissítheti a használati metrikai adatokat. Ez szükséges is lehet az ütemezett frissítés folytatásához akkor, ha a hitelesítő adatok lejártak, vagy ha eltávolította a használatimetrika-jelentést először elindító felhasználót a munkaterületről, amelyen az adathalmaz található.

### <a name="usage-metrics-report-pages"></a>Használatmetrikai-jelentés oldalai

A továbbfejlesztett használatimetrika-jelentés a következő jelentésoldalakat tartalmazza:

- **Jelentés használata**    A jelentés megtekintéseiről és a megtekintőkről nyújt információkat, például hogy naponta hány felhasználó tekintette meg a jelentést.
- **Jelentésteljesítmény**    A jelentés megnyitásához általában szükséges időt mutatja meg felhasználási módszer és böngészőtípus szerinti bontásban.
- **GYIK**     Választ kínál az olyan gyakran feltett kérdésekre, mint: Mit jelent a „Megtekintő”, és mit a „Megtekintés” kifejezés?

### <a name="which-metrics-are-reported"></a>Melyik metrikák szerepelnek a jelentésben?

| **Oldal** | **Metrika** | **Leírás** |
| --- | --- | --- |
| Használat jelentése | Jelentések megtekintése | Jelentésmegtekintés lesz rögzítve minden alkalommal, amikor valaki megnyit egy jelentést. Figyelje meg, hogy a megtekintés definíciója eltér a korábbi használati metrikai jelentésekben használttól. A jelentésoldalak közötti váltás már nem számít újabb megtekintésnek. |
| Használat jelentése | Egyedi megtekintők | Megtekintő az, aki legalább egyszer megnyitotta a jelentést az időszakban (az AAD-beli felhasználói fiók alapján). |
| Használat jelentése | Megtekintési trend | A megtekintési trend a megtekintések számának időbeli változását tükrözi. A kijelölt időszak első felét hasonlítja össze a másodikkal. |
| Használat jelentése | Dátumszeletelő | Az időszak a Jelentés használata oldalon változtatható meg például a hetenkénti vagy kéthetenkénti trendek kiszámításához. A Jelentés használata oldalon meghatározhatja azt a legkorábbi és legkésőbbi dátumot, amelyre a kijelölt jelentés használati adatai elérhetők. |
| Használat jelentése | Sorszám | A rangsor a megtekintések száma alapján mutatja meg egy jelentés népszerűségét az összes vállalati jelentéséhez viszonyítva.   |
| Használat jelentése | Jelentés megtekintései naponta | A naponkénti megtekintések teljes száma. |
| Használat jelentése | A jelentés megtekintőinek száma naponta | A jelentést megtekintő különböző felhasználók teljes száma (az AAD-felhasználói fiók alapján). |
| Használat jelentése | Terjesztési mód | Az a mód, ahogyan a felhasználók hozzáférést szereznek a jelentéshez például azáltal, hogy egy munkaterület tagjai, megosztották velük a jelentést vagy telepítettek egy alkalmazást. |
| Használat jelentése | Platformszeletelő | Azt mutatja meg, hogy a jelentést a Power BI szolgáltatáson (powerbi.com) keresztül, a Power BI Embeddeden vagy mobileszközön érték el. |
| Használat jelentése | A jelentést megtekintő felhasználók | Azoknak a felhasználóknak a megtekintések száma szerint rendezett listáját mutatja meg, akik a jelentést megnyitották. |
| Használat jelentése | Oldalak | Ha a jelentés terjedelme egy oldalnál nagyobb, akkor az a megtekintett oldal(ak) szerint vizsgálható. Ha a listában „Üres” elem látható, az azt jelenti, hogy egy oldalt a közelmúltban adtak hozzá a jelentéshez (az új oldal tényleges neve 24 órán belül megjelenik a szűrési listában) és/vagy azt, hogy a jelentésből oldalakat töröltek. Az "Üres" elem ezeket az eseteket jelzi. |
| Jelentésteljesítmény | Megnyitás jellemző időtartama | A jelentés jellemző megnyílási ideje a jelentés megnyitásához szükséges időtartamok 50 százalékának felel meg. Másként fogalmazva ez az az idő, amennyi alatt a jelentésmegnyitási műveletek 50%-a befejeződik. A Jelentésteljesítmény oldal felhasználási mód és böngészőtípus szerint is lebontja a megnyitás jellemző időtartamát.   |
| Jelentésteljesítmény | Megnyitási idő trendje | A megnyitási idő trendje a jelentés teljesítményének időbeli alakulását tükrözi. Összehasonlítja a jelentés megnyitásához szükséges időtartamokat a kijelölt időszak első és második felében. |
| Jelentésteljesítmény | Dátumszeletelő | Az időszak a Jelentésteljesítmény oldalon változtatható meg például a hetenkénti vagy kéthetenkénti trendek kiszámításához. A Jelentésteljesítmény oldalon meghatározhatja azt a legkorábbi és legkésőbbi dátumot, amelyre a kijelölt jelentés használati adatai elérhetők. |
| Jelentésteljesítmény | Napi teljesítmény | A jelentésmegnyitási műveletek 10, 50 és 90%-ának teljesítménye az egyes napokra kiszámítva. |
| Jelentésteljesítmény | Hétnapos teljesítmény | A jelentésmegnyitási műveletek 10, 50 és 90%-ának teljesítménye az egyes dátumokat megelőző 7 napra kiszámítva. |
| Jelentésteljesítmény | Felhasználási mód | Azt mutatja meg, hogy a jelentést hogyan nyittották meg, például a Power BI szolgáltatáson (powerbi.com) keresztül, a Power BI Embeddeden vagy mobileszközön. |
| Jelentésteljesítmény | Böngészők | A felhasználó által a jelentés megnyitásához használt böngésző, például Firefox, Edge vagy Chrome. |

## <a name="update-usage-metrics-report-credentials"></a>Használatimetrika-jelentés hitelesítő adatainak frissítése

Az alábbi eljárással tulajdonba vehet egy Usage Metrics Report adathalmazt, és módosíthatja a hitelesítő adatokat.

1. Nyissa meg a munkaterületet, ahol az a jelentés található, amelynek Usage Metrics Report adathalmazát módosítani szeretné.
2. A felső fekete fejlécsávon válassza a **Beállítások** ikont, majd a **Beállítások** lehetőséget.

    ![Beállítások kiválasztása](media/service-modern-usage-metrics/power-bi-settings-settings.png)

3. Váltson az **Adathalmazok** lapra.

1. Jelölje ki a Usage Metrics Report adathalmazt. 

    ![Használati metrikai adathalmaz kijelölése](media/service-modern-usage-metrics/power-bi-select-usage-metrics.png)
    
    Ha nem Ön az adathalmaz jelenlegi tulajdonosa, tulajdonba kell vennie azt az adatforrásbeli hitelesítő adatok módosításához. 
    
5. Válassza a **Saját tulajdonba vétel** gombot, majd az **Adathalmaz-beállítások saját tulajdonba vételet** párbeszédpanelen válassza ismét a **Saját tulajdonba vétel** lehetőséget.

1. Az **Adatforrásbeli hitelesítő adatok** területen válassza a **Hitelesítő adatok szerkesztése** lehetőséget.

    ![Hitelesítő adatok szerkesztése](media/service-modern-usage-metrics/power-bi-usage-metrics-edit-credentials.png)

2. A **Használatimetrika-jelentések konfigurálása** párbeszédpanelen válassza a **Bejelentkezés** lehetőséget.

    ![A Bejelentkezés lehetőség kiválasztása](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-configure.png)

1. Fejezze be a bejelentkezési folyamatot, és figyelje meg az adatforrás sikeres módosításáról szóló értesítést.

    > [!NOTE]
    > A Usage Metrics Report adathalmaz az utolsó 30 nap használati adatait tartalmazza. Az új használati adatok importálása 24 órát is igénybe vehet. Nem kezdeményezhet manuális frissítést a Power BI felhasználói felületén.


## <a name="disable-usage-metrics-reports"></a>Használatimetrika-jelentések letiltása

A használati metrikai jelentés olyan funkció, amelyet a Power BI vagy Office 365 rendszergazdája kapcsolhat be vagy ki. A rendszergazdák részletesen szabályozhatják, hogy mely felhasználók férnek hozzá a használati metrikákhoz. Ez alapértelmezés szerint a szervezet összes felhasználójánál engedélyezve van. Ezeket a beállításokat a Felügyeleti portálról szóló cikk [Használati metrikák szabályozása](service-admin-portal.md#control-usage-metrics) című szakasza ismerteti részletesen.

> [!NOTE]
> Csak a Power BI-bérlő rendszergazdái látják a Felügyeleti portált és a szerkesztési beállításokat.

## <a name="exclude-user-information-from-usage-metrics-reports"></a>Felhasználó adatok kizárása használatimetrika-jelentésekből

Alapértelmezés szerint a felhasználónkénti adatok engedélyezve vannak a használati metrikákhoz, a tartalomfelhasználói fiókadatok pedig szerepelnek a metrikajelentésekben. Ha a rendszergazdák nem szeretnék elérhetővé tenni egyes felhasználók adatait, vagy egyikét sem, kizárhatják a felhasználói adatokat a használati jelentésből, ha letiltják a felhasználónkénti adatokat a használati metrikákban a tartalomkészítők számára a megadott biztonsági csoportokban vagy az egész vállalatnál a Power BI felügyeleti portáljának beállításai között.

1. A felügyeleti portál **Bérlő beállításai** lapjának **Naplózási és használati beállítások** területén bontsa ki a **Felhasználónkénti adatok a metrikákban tartalomkészítők számára** elemet, és válassza a **Letiltva** lehetőséget.

2. Döntse el, hogy szükséges-e **Minden meglévő felhasználónkénti adat törlése az aktuális használati metrikák tartalmából**, majd válassza az **Alkalmazás** lehetőséget.

    ![Felhasználónkénti metrikák letiltása](media/service-modern-usage-metrics/power-bi-admin-disable-per-user-metrics.png)

A felhasználói adatok kizárása esetén a használati jelentés minden felhasználóra Névtelenként hivatkozik.

Amikor a teljes vállalatnál letiltja a használati metrikákat, a rendszergazda a Teljes meglévő használati metrikai tartalom törlése lehetőséggel törölni tud minden meglévő jelentést és irányítópult-csempét, amely a használati metrikai jelentések használatával készült. Ezen a módon minden használati metrikai adat hozzáférhetetlenné válik a szervezet valamennyi felhasználója számára, akik esetleg már használják is azokat. A meglévő használati metrikai tartalom törlése nem vonható vissza.

> [!NOTE]
> A felügyeleti portált megtekinteni és a Felhasználónkénti adatok a metrikákban tartalomkészítők számára beállítást konfigurálni csak rendszergazdák tudják.

## <a name="customize-the-usage-metrics-report"></a>A használatimetrika-jelentés testreszabása

A jelentés adatainak részletes vizsgálatára vagy a mögöttes adathalmazra épülő saját jelentés készítésére több lehetősége van:

- **[Másolatot készíthet a jelentésről](#create-a-copy-of-the-usage-report) a Power BI szolgáltatásban.**   A **Másolat mentése** lehetőséggel létrehozhatja a használatimetrika-jelentés egy külön példányát, amelyet sajátos igényeinek megfelelően szabhat testre.
- **[Csatlakozhat az adathalmazhoz](#create-a-new-usage-report-in-power-bi-desktop) egy új jelentéssel.**   Az adathalmaz neve minden munkaterülethez „Usage Metrics Report”, a korábbi, [Használatimetrika-jelentés adathalmaza](#usage-metrics-report-dataset) című szakaszban leírtaknak megfelelően. A Power BI Desktop használatával egyéni használatimetrika-jelentést készíthet a mögöttes adathalmaz alapján.
- **[Használhatja az Elemzés az Excelben funkciót](#analyze-usage-data-in-excel).**   A Microsoft Excel 2010 SP1 vagy újabb verziójának kimutatásait, diagramjait és szeletelőit is felhasználhatja a Power BI használati adatainak elemzéséhez. További információk az [Elemzés az Excelben](service-analyze-in-excel.md) funkcióról.

### <a name="create-a-copy-of-the-usage-report"></a>Használati jelentés másolatának létrehozása

Amikor másolatot készít a csak olvasható, előre elkészített használati jelentésről, a Power BI a jelentés egy szerkeszthető példányát hozza létre. Első látásra ugyanolyannak tűnhet. Csakhogy a jelentés most már megnyitható Szerkesztő nézetben, hozzáadhat vizualizációkat, szűrőket és oldalakat, módosíthat vagy törölhet meglévő vizualizációkat, és további lehetőségek is megnyílnak. A Power BI az aktuális munkaterületre menti az új jelentést.

1. Az új használatimetrika-jelentésben válassza a **További lehetőségek** (...) menüt, majd a **Másolat mentése** menüpontot.

    ![Másolat készítése a jelentésről](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-save.png)

2. A **Jelentés mentése** párbeszédpanelen adjon meg egy nevet, majd válassza a **Mentés** lehetőséget.

    A Power BI szerkeszthető Power BI-jelentést hoz létre, amelyet az aktuális munkaterületre ment, és megnyitja a jelentés másolatát. 

3. Váltson Szerkesztés módra a **További lehetőségek** (...) menüt, majd a **Szerkesztés** menüpontot választva. 

    Módosíthat például szűrőket, felvehet új oldalakat, készíthet új vizualizációkat, formázhatja a betűtípusokat és színeket, stb.

1. Az új jelentés az aktuális munkaterület Jelentések lapjára lesz mentve, és fel lesz véve a Legutóbbi tartalomlistára.

    ![Az új jelentés a Jelentések lapon](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-new-report.png)

### <a name="create-a-new-usage-report-in-power-bi-desktop"></a>Új használati jelentés létrehozása a Power BI Desktopban

Új jelentést hozhat létre a Power BI Desktopban a Usage Metrics Report adathalmaz alapján. Ahhoz, hogy kapcsolatot hozhasson létre a Usage Metrics Report adathalmazzal és saját jelentést hozhasson létre, a Power BI Desktopban be kell jelentkeznie a Power BI szolgáltatásba. 

1. Nyissa meg a Power BI Desktopot.

2. Ha nincs bejelentkezve a Power BI szolgáltatásba, válassza a **Fájl** menü **Bejelentkezés** elemét.

1. A Usage Metics Report adathalmazhoz való csatlakozáshoz válassza a **Kezdőlap** menüszalag **Adatok beolvasása** elemét.

4. A bal oldali panelen válassza a **Power Platform** elemet, majd a **Power BI-adathalmazok** > **Csatlakozás** lehetőséget.

    ![Adatok beolvasása > Power Platform](media/service-modern-usage-metrics/power-bi-desktop-get-data.png)

1. Görgessen a kívánt adathalmazhoz, vagy gépelje be a keresőmezőbe a *Usage Metrics Report* szöveget. 

6. Ellenőrizze a megfelelő adathalmaz kijelölését a Munkaterület oszlopban, majd válassza a **Létrehozás** lehetőséget. 

    ![A Usage Metrics Report adathalmaz kijelölése](media/service-modern-usage-metrics/power-bi-desktop-select-usage-metrics.png)

7. A Power BI Desktopban ellenőrizze a Mezők listát, ahol a kijelölt adathalmaz tábláihoz, oszlopaihoz és mértékeihez férhet hozzá.

    ![A Usage Metrics Report mezőlistájának megtekintése](media/service-modern-usage-metrics/power-bi-desktop-fields-list.png)

1. Ettől kezdve egyéni használati jelentéseket hozhat létre és oszthat meg ugyanannak a Usage Metrics Report adathalmaznak az alapján.

### <a name="analyze-usage-data-in-excel"></a>Használati adatok elemzése az Excelben

Ha az Excelben csatlakozik a használati adatokhoz, az előre definiált mértékeket használó kimutatásokat készíthet. Tudnia kell, hogy az Excel-kimutatások Power BI-adathalmazhoz való csatlakozáskor nem támogatják a numerikus mezők kattintással és húzással végzett összesítését.

1. Először – ha még nem tette meg – [hozzon létre másolatot a használatimetrika-jelentésről](#create-a-copy-of-the-usage-report). 

2. Nyissa meg az új használatimetrika-jelentést, válassza a **További lehetőségek** (...) menüt, majd az **Elemzés az Excelben**.

    ![Elemzés az Excelben](media/service-modern-usage-metrics/power-bi-export-excel.png)

1. Ha az **Először néhány Excel-frissítésre van szükség** párbeszédpanel jelenik meg, válassza a **Letöltés** lehetőséget, majd telepítse a Power BI-kapcsolat legújabb frissítéseit, vagy válassza a **Már telepítettem ezeket a frissítéseket** lehetőséget.

    ![Excel-frissítések](media/service-modern-usage-metrics/power-bi-excel-updates.png)

    > [!NOTE]
    > Egyes cégeknél olyan csoportházirendek lehetnek érvényben, amelyek megakadályozzák az Elemzés az Excelben funkció használatához szükséges Excel-frissítések telepítését. Ha nem tudja telepíteni ezeket a frissítéseket, forduljon a rendszergazdájához.

1. A böngészőnek a Usage Metrics Report.odc fájllal végzendő műveletre rákérdező párbeszédpanelén válassza a **Megnyitás** lehetőséget.

    ![A .odc-fájl megnyitása](media/service-modern-usage-metrics/power-bi-open-odc-file.png)

1. A Power BI elindítja az Excelt. Ellenőrizze a .odc-fájl nevét és elérési útját, majd válassza az **Engedélyezés** lehetőséget.

    ![Az Excel biztonsági figyelmeztetése](media/service-modern-usage-metrics/power-bi-excel-security-notice.png)

1. Miután az Excel megnyílik, az üres kimutatás Sorok, Oszlopok, Szűrők és Értékek területeire húzott mezőkkel a használati adatok egyéni nézetét hozhatja létre.

    ![Kimutatás az Excelben](media/service-modern-usage-metrics/power-bi-pivottable-excel.png)

## <a name="usage-metrics-in-national-clouds"></a>Használati metrikák az országos felhőkben

A Power BI elérhető különálló országos felhőkben. Ezek a felhők ugyanolyan szintű biztonságot, adatvédelmet, megfelelőséget és átláthatóságot kínálnak, mint a Power BI globális verziója, de a szolgáltatásnyújtás, az adatok tárolási helye, a hozzáférés és a vezérlés terén a helyi jogszabályoknak megfelelő egyedi modellel kombinálva. Ennek a helyi jogszabályok szerint kialakított egyedi modellnek köszönhetően a használati metrikák az országos felhőkben nem érhetők el. További információért lásd az [szuverén felhők](https://powerbi.microsoft.com/clouds/) weblapját.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Fontos tisztában lenni a továbbfejlesztett használatimetrika-jelentések és az elődjeik összehasonlításakor jelentkező különbségekkel és azok magyarázatával. Nevezetesen, a jelentések használati metrikái már a Power BI szolgáltatásból gyűjtött tevékenységi adatokon alapulnak. A használatimetrika-jelentés korábbi verziói ügyfél-telemetriára épültek, ez pedig nem mindig egyezik meg a szolgáltatásból gyűjtött használati metrikákkal. Ezen felül a továbbfejlesztett használatimetrika-jelentésben más a „Megtekintés” definíciója. Megtekintésnek számít egy jelentésmegnyitás esemény, amilyet a szolgáltatás minden alkalommal rögzít, ha valaki megnyit egy jelentést. A jelentésoldalak közötti váltás már nem számít újabb megtekintésnek.

> [!NOTE]
> Mivel a továbbfejlesztett használatimetrika-jelentés a Power BI szolgáltatásból gyűjtött tevékenységadatokra épül, a használati metrikák már megegyeznek az auditnaplókban és tevékenységnaplókban rögzített tevékenységek összesített számával. A megtekintők és megtekintések száma többé nem torzul amiatt, hogy a rendszer több vagy kevesebb tevékenységet számol az akadozó hálózati kapcsolat, a reklámblokkolók vagy más ügyféloldali problémák következtében.

A korábbi és a továbbfejlesztett használatimetrika-jelentések fenti eltérései mellett az előzetes kiadásban az alábbi korlátozásokat is figyelembe kell venni:

- Az irányítópult-használati metrikák továbbra is a használatimetrika-jelentés korábbi verziójára épülnek.
- Továbbfejlesztett használatimetrika-jelentések csak modern munkaterületeken lévő jelentésekhez érhetők el. Az örökölt munkaterületeken lévő jelentések csak a használatimetrika-jelentések korábbi verzióját támogatják.
- A jelentésteljesítmény-metrikák ügyfél-telemetriára épülnek. A teljesítménymérés nem terjed ki a megtekintések bizonyos típusaira. Ha a felhasználó például egy e-mailben választ ki egy jelentésre mutató hivatkozást, a megtekintés beleszámít a jelentéshasználatba, de a teljesítménymetrikák szempontjából nem történt esemény.
- A jelentésteljesítmény metrikái többoldalas jelentésekhez nem érhetők el. Ilyen típusú jelentésekről a Jelentés használata oldal Oldalak lapján és a Jelentésteljesítmény oldal diagramjain sem jelennek meg adatok.
- Beágyazott csoportok használata esetén a felhasználók elrejtése nem az elvárható módon működik. Ha a vállalat letiltotta a Felhasználónkénti adatok a metrikákban tartalomkészítők számára lehetőséget a Power BI felügyeleti portálján a bérlői beállításokban, akkor csak a legfelső szint tagjai lesznek elrejtve. Az alcsoportok tagjai továbbra is láthatók lesznek.
- A Usage Metrics Report adathalmaz inicializálása eltarthat néhány percig, emiatt pedig üres használatimetrika-jelentés lesz látható, mert a Power BI felhasználói felülete nem vár a frissítés befejezéséig. A Usage Metrics Report adathalmaz beállításaiban, a frissítési előzmények között ellenőrizheti, hogy a frissítési művelet sikeres volt-e.
- A Usage Metrics Report adathalmaz inicializálása sikertelen is lehet a frissítés során keletkező időtúllépés miatt. A probléma megoldásához tekintse át az alábbi Hibaelhárítás szakaszt.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

A fenti szempontokon és korlátozásokon kívül a használati metrikákkal kapcsolatos alábbi kérdések és válaszok is hasznosak lehetnek felhasználók és rendszergazdák számára:

**KÉRDÉS:** Nem tudok használati metrikát futtatni egy jelentésen.

**VÁLASZ:** Használati metrikát csak olyan jelentéshez használhat, amelynek tulajdonosa, vagy amelyhez szerkesztési jogosultsága van.

**KÉRDÉS:** Miért nem jelenik meg az Új használati jelentés váltógombja a meglévő használatimetrika-jelentés jobb felső sarkában?

**VÁLASZ:** A továbbfejlesztett használatimetrika-jelentés csak modern munkaterületeken lévő jelentésekhez érhető el.

**KÉRDÉS:** Milyen időszakot ölel fel a jelentés?

**VÁLASZ:** A használati jelentés az utolsó 30 nap tevékenységadataira épül, az aktuális napi tevékenységek nélkül. Az időszak a Jelentés használata oldalon lévő Dátumszeletelővel szűkíthető le például az utolsó heti adatok elemzésére.

**KÉRDÉS:** Mikor jelennek meg a legújabb tevékenységi adatok?

**VÁLASZ:** A használati jelentés az UTC időzóna szerinti utolsó teljes napig tartalmaz tevékenységi adatokat. A jelentésben megjelenő adatok az adathalmaz frissítésének időpontjától is függnek. A Power BI naponta egyszer frissíti az adathalmazt.

**KÉRDÉS:** Úgy látom, hogy az adatok nem naprakészek.

**VÁLASZ:** Vegye figyelembe, hogy akár 24 óra is eltelhet, mire az új tevékenységadatok megjelennek a használati jelentéseben.

**KÉRDÉS:** Mi a használati adatok adatforrása?

**VÁLASZ:** A Usage Metrics Report adathalmaz a Power BI belső használatimetrika-tárából importál adatokat egy Usage Metrics Data Connector nevű egyéni összekötővel. A Usage Metrics Data Connector hitelesítő adatait a Usage Metrics Report adathalmaz beállításainak oldalán módosíthatja.

**KÉRDÉS:** Hogyan csatlakozhatok az adatokhoz? Hogyan módosíthatom az alapértelmezett jelentést?

**VÁLASZ:** Létrehozhatja a csak olvasható előre elkészített jelentés másolatát. A jelentés másolata ugyanahhoz a Usage Metrics Report adathalmazhoz kapcsolódik, és lehetővé teszi a jelentés részletes szerkesztését.

**KÉRDÉS:** Mi a „Megtekintő” és a „Megtekintés”?

**VÁLASZ:** Megtekintő az, aki legalább egyszer megnyitotta a jelentést az időszakban. Megtekintés a jelentés megnyitása esemény. Jelentésmegtekintés lesz rögzítve minden alkalommal, amikor valaki megnyit egy jelentést.

Figyelje meg, hogy a megtekintés definíciója eltér a korábbi használati metrikai jelentésekben használttól. A jelentésoldalak közötti váltás már nem számít újabb megtekintésnek.

**KÉRDÉS:** Hogyan van kiszámítva a „Megtekintési trend”?

**VÁLASZ:** A megtekintési trend a megtekintések számának időbeli változását tükrözi. A kijelölt időszak első felét hasonlítja össze a másodikkal. Az időszak a Dátumszeletelővel változtatható meg a Jelentés használata oldalon például a hetenkénti vagy kéthetenkénti trendek kiszámításához.

**KÉRDÉS:** Mit jelent az „Eloszlás” és a „Platform”?

**VÁLASZ:** Az eloszlás megmutatja, hogy hogyan kaptak a megtekintők hozzáférést egy jelentéshez: közvetlen megosztással, munkaterület-hozzáférésen keresztül vagy alkalmazáson keresztül.

A Platform azt a technológiát jelenti, amelyet a megtekintő a jelentés megnyitására használt: PowerBI.com, Mobile vagy Embedded.

**KÉRDÉS:** Hogyan működik a jelentések rangsorolása?

**VÁLASZ:** A rangsor a megtekintések száma alapján mutatja meg egy jelentés népszerűségét az összes vállalati jelentéséhez viszonyítva.

**KÉRDÉS:** Kik a „Névtelen felhasználók”?

**VÁLASZ:** A vállalat dönthet úgy, hogy kizárja a felhasználói adatokat a használati jelentésből. Ezek kizárása esetén a használati jelentés minden felhasználóra Névtelenként hivatkozik.

**KÉRDÉS:** Mi a „Jelentés jellemző megnyílási ideje”?

**VÁLASZ:** A jelentés jellemző megnyílási ideje a jelentés megnyitásához szükséges időtartamok 50 százalékának felel meg. Másként fogalmazva ez az az idő, amennyi alatt a jelentésmegnyitási műveletek 50%-a befejeződik. A Jelentésteljesítmény oldal felhasználási mód és böngészőtípus szerint is lebontja a megnyitás jellemző időtartamát.

**KÉRDÉS:** Hogyan van kiszámítva a „Megnyitási idő trendje”?

**VÁLASZ:** A megnyitási idő trendje a jelentés teljesítményének időbeli alakulását tükrözi. Összehasonlítja a jelentés megnyitásához szükséges időtartamokat a kijelölt időszak első és második felében. Az időszak a Dátumszeletelővel változtatható meg a Jelentésteljesítmény oldalon például a hetenkénti vagy kéthetenkénti trendek kiszámításához.

**KÉRDÉS:**  A használatimetrika-jelentés korábbi verziójában négy jelentés szerepel, a továbbfejlesztett verzióban viszont csak három jelenik meg.

**VÁLASZ:**  A továbbfejlesztett használatimetrika-jelentés csak az elmúlt 30 nap során megnyitott jelentésekre terjed ki, a korábbi verzió pedig az elmúlt 90 napot öleli fel. Ha egy jelentés nem szerepel a továbbfejlesztett használatimetrika-jelentésben, akkor azt feltehetően nem használták az elmúlt 30 nap folyamán.

## <a name="troubleshoot-delete-the-dataset"></a>Hibaelhárítás: Adatkészlet törlése

Ha adatkonzisztenciával vagy frissítéssel kapcsolatos problémára gyanakszik, érdemes lehet törölni a meglévő Usage Metrics Report adathalmazt. Ez után a Használati metrikák megtekintése lehetőséggel új adathalmazt generálhat a hozzá tartozó továbbfejlesztett használatimetrika-jelentéssel együtt. Hajtsa végre az alábbi lépéseket.

### <a name="delete-the-dataset"></a>Adatkészlet törlése

1. Nyissa meg a munkaterületet, ahol az a jelentés található, amelynek Usage Metrics Report adathalmazát alaphelyzetbe szeretné állítani.

2. A felső fekete fejlécsávon válassza a **Beállítások** ikont, majd a **Beállítások** lehetőséget.

    ![Beállítások kiválasztása](media/service-modern-usage-metrics/power-bi-settings-settings.png)

3. Váltson az **Adathalmazok** lapra, majd jelölje ki a Usage Metrics Report adathalmazt. 

    ![Használati metrikák adathalmaza](media/service-modern-usage-metrics/power-bi-settings-usage-report-dataset.png)

5. Másolja ki a munkaterület és az adathalmaz azonosítóját a böngésző címsorában megjelenő URL-címből.

    ![Használati metrikák adathalmazának URL-címe](media/service-modern-usage-metrics/power-bi-usage-metrics-url.png)

1. A böngészőben nyissa meg a [https://docs.microsoft.com/rest/api/power-bi/datasets/deletedatasetingroup](https://docs.microsoft.com/rest/api/power-bi/datasets/deletedatasetingroup) oldalt, és válassza a **Kipróbálás** gombot.

    ![Adathalmaz-törlés kipróbálása](media/service-modern-usage-metrics/power-bi-delete-dataset-try-it.png)

1. Jelentkezzen be a Power BI-ba, illessze be a munkaterület azonosítóját a **groupId** szövegmezőbe, az adathalmaz azonosítóját pedig a **datasetId** szövegmezőbe, majd válassza a **Futtatás** lehetőséget. 

    ![A REST API kipróbálása](media/service-modern-usage-metrics/power-bi-rest-api-try-it.png)

1. A **Futtatás** gomb alatti mezőben ellenőrizze, hogy a szolgáltatás a **200** válaszkódot adja vissza. Ez a kód jelzi, hogy az adathalmaz és az ahhoz tartozó használatimetrika-jelentések törlése sikeres volt.

    ![A 200-as válaszkód](media/service-modern-usage-metrics/power-bi-response-code-200.png)

### <a name="create-a-fresh-usage-metrics-report"></a>Friss használatimetrika-jelentés létrehozása

1. A Power BI-szolgáltatásba visszatérve láthatja, hogy az adathalmaz eltűnt.

    ![Nincs használatmetrikai-jelentés](media/service-modern-usage-metrics/power-bi-no-usage-metrics-dataset.png)

2. Ha a használatimetrika-jelentés még látható a Jelentések listában, frissítse a böngészőablak tartalmát.

3. [Hozzon létre friss használatimetrika-jelentést](#create--view-an-improved-usage-metrics-report).

## <a name="next-steps"></a>Következő lépések

[A Power BI felügyelete a felügyeleti portálon](service-admin-portal.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
