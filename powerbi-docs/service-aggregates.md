---
title: Működnek az összesítések (összeg, átlag, és így tovább) a Power BI szolgáltatásban
description: Megtudhatja, hogyan módosítható a vizualizációs diagram (összeg, átlag, maximum és stb.) a Power BI szolgáltatásban.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710667"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Működnek az összesítések (összeg, átlag, és így tovább) a Power BI szolgáltatásban

## <a name="what-is-an-aggregate"></a>Mi az az összesítés?

Néha szükség van az adatok értékeinek matematikai összevonására. A matematikai művelet lehet összeg, átlag, maximum, száma és így tovább. Ha kombinálja értékek az adatokban, nevezzük *összesítésével*. Az ilyen matematikai műveletek eredménye az *összesítési érték*.

Amikor a Power BI szolgáltatás és a Power BI Desktop vizualizációkat hoz létre, előfordulhat, hogy összesítés is történik. Az így létrehozott összesítés gyakran éppen megfelelő a célnak, de előfordulhat, hogy az értékeket másféle módon szükséges összesíteni.  Ilyen lehet például, ha összeg helyett átlagot szeretnénk. Többféleképpen is eltérő kezeléséhez, és módosítsa az összesítést, a Vizualizációk a Power BI használja.

Először vessünk egy pillantást adatok *típusok* , mert az adatok típusát határozza meg, hogyan és kell-e a Power BI is összesíteni.

## <a name="types-of-data"></a>Adattípusok

A legtöbb adathalmazban többféle adattípus található. A legalapvetőbb szinten, az adatokat a nem numerikus vagy azt. A Power BI összesítheti az összeg, átlag, száma, minimum, variancia és még sok más numerikus adatokat. A szolgáltatás még összesítheti szöveges adatok, vagy más néven *kategorikus* adatokat. Ha kategorikus mező összegezni úgy, hogy a hasonló csak numerikus kérelemegységeket **értékek** vagy **elemleírások**, a Power BI megszámlálni az egyes kategóriák vagy distinct megszámlálni az egyes fog kategória. Speciális adattípusok, például a dátumok néhány saját összegzési rendelkezik: legkorábbi, legújabb, első és utolsó.

Az alábbi példában:

- A **Units Sold** és a **Manufacturing Price** oszlopok numerikus adatokat tartalmaznak

- A **Segment**, **Country**, **Product**, **Month**, és **Month Name** nevű oszlopok kategóriaadatokat tartalmaznak

   ![Képernyőkép: egy minta adatkészlet.](media/service-aggregates/power-bi-aggregate-chart.png)

Vizualizációk létrehozása a Power bi-ban, ha a szolgáltatás szerint összesítő numerikus mezők (az alapértelmezett érték *sum*) néhány kategóriaadat.  Például "eladott mennyiség ***termék szerint***", "eladott mennyiség ***hónap szerint***" és "Manufacturing Price ***szegmens***". A Power BI hivatkozik, néhány számmezőt **mértékek**. Könnyen azonosíthatja a mértékek a Power BI Jelentésszerkesztő – a **mezők** lista mértékek mellettük a ∑ jellel jelennek meg. Lásd: [a Jelentésszerkesztő... bemutató](service-the-report-editor-take-a-tour.md) további információ.

![Képernyőkép a Power bi-bA a mezők listában kiemeltük.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Miért nem az elvártnak megfelelően működnek az összesítések?

Az összesítések használata a Power bi-ban bonyolult lehet. Már van egy numerikus mező, és a Power BI nem engedélyezi az összesítés módosítását. Vagy esetleg olyan mezőről van szó (például évszám), amelynek nem kellene szerepelnie az összesítésben, csak az ahhoz tartozó előfordulások számát szeretnénk megszámlálni.

A mögöttes probléma általában a mező definíció az adatkészletben. Talán az adatkészlet tulajdonosa definiált szövegként a mezőt, és tájékoztat arról, hogy a Power BI miért nem összegzi vagy átlagolja azt. Sajnos [csak az adatkészlet tulajdonosa tudja módosítani a mezők kategóriáját](desktop-measures.md). Ha tulajdonosi engedélye az adatkészlethez, akár a Desktopban vagy a (például Excel), adatkészlet létrehozásához használt program, így is a probléma megoldásához. Ellenkező esetben azonban az adathalmaz tulajdonosától kell segítséget kérnie.  

A cikk végén található egy külön szakasz [ **megfontolandó szempontok és hibaelhárítás**](#considerations-and-troubleshooting). Tippek és útmutatást biztosít. Ha nem találja a választ, tegye fel kérdését a [Power BI közösségi fórumában](http://community.powerbi.com). Ahol gyors választ fog kapni közvetlenül a Power BI-csapattól.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Számmezők összevonásának módosítása

Tegyük fel, hogy egy diagramban különböző termékekhez tartozó értékesítési adatok összesítése szerepel, de Ön inkább átlagot szeretne számolni.

1. Hozzon létre egy **fürtözött oszlopdiagram** , amely használja egy mérték, és a egy kategóriát. Ebben a példában a „Units Sold by Product” (értékesített egységek termék szerint) összesítést használjuk.  Alapértelmezés szerint a Power BI létrehoz egy diagram, amely összegzi az értékesített egységeket (húzza be az mértékcsoport a **érték** is) az egyes termékek (húzza be a kategóriát a **tengely** is).

   ![A diagram, a Vizualizációk panelen és a mezők listában képernyőképe az összeg kiemeltük.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Az a **Vizualizációk** ablaktáblán, kattintson a jobb gombbal a mérték, és válassza ki a kívánt összesítési típust kell. Ebben az esetben azt választjuk **átlagos**. Ha nem látja az összesítés van szüksége, megjelenik a [ **megfontolandó szempontok és hibaelhárítás** ](#considerations-and-troubleshooting) szakaszban.

   ![Átlagos összesített lista – képernyőfelvétel a kijelölt és kiemeltük.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > A legördülő listából válassza ki a rendelkezésre álló beállítások (1) a kijelölt mező függően változhat, és (2) a következő módon: az adatkészlet tulajdonosa kategorizált ezt a mezőt.

1. A vizualizáció most már az átlag szerinti összesítést használja.

   ![Képernyőkép – a diagramon most már megjelenítése átlagos az eladott egységek termékek szerint.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Az adatok összesítésének módjai

A mezők összesítésekor esetlegesen rendelkezésre álló lehetőségek:

- **Összegzés mellőzése**. A lehetőség a Power BI abban a mezőben minden érték külön-külön kezeli, és nem foglalják össze őket. Használja ezt a beállítást, ha olyan Számazonosítós oszlopról, amely a szolgáltatás nem összeg.

- **Összeg**. Összeadja a mezőben szereplő összes értéket.

- **Átlag**. Az értékek számtani középértékét számítja ki.

- **Minimum**. A legkisebb értéket mutatja.

- **Maximum**. A legnagyobb értéket mutatja.

- **Darabszám (nem üres).** Nem üres mezőkben lévő értékek megszámlálása.

- **Darabszám (eltérők).** A mezőkben lévő különböző értékek darabszámát adja vissza.

- **Szórás.**

- **Variancia**.

- **Medián**.  A mediánt (középértéket) mutatja. Ez az az érték, amely képest ugyanannyi számú nála nem kisebb és nem nagyobb elem van.  Ha két mediánról van szó, a Power BI átlagolja őket.

Nézzük például az alábbi adatokat:

| Ország | Összeg |
|:--- |:--- |
| Amerikai Egyesült Államok |100 |
| Egyesült Királyság |150 |
| Kanada |100 |
| Németország |125 |
| Franciaország | |
| Japán |125 |
| Ausztrália |150 |

Ezek az alábbi eredményeket adnák vissza:

- **Összegzés mellőzése**: Minden érték külön jelenik meg

- **Összeg**: 750

- **Átlag**: 125

- **Maximum**:  150

- **Minimum**: 100

- **Darabszám (nem üres):** 6

- **Darabszám (eltérők):** 4

- **Szórás:** 20,4124145...

- **Variancia:** 416,666...

- **Medián:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Összesítés létrehozása a kategória- (szöveg-) mező használatával

Nem numerikus mezőt is lehet összesíteni. Ha például egy Terméknév nevű mezőről van szó, felveheti értékként, majd beállíthatja azt a **Darabszám** vagy a **Darabszám (eltérők)** , az **Első** vagy **Utolsó** használatára.

1. Húzza a **termék** mezőt a **értékek** is. A **értékek** jól általában numerikus mezőkben szerepel. A Power BI felismeri, hogy ez a mező egy szövegmező, az összesített állítja **mellőzése**, és egy egyoszlopos tábla jeleníti meg.

   ![Képernyőkép – a termék mezője az értékek területre.](media/service-aggregates/power-bi-aggregate-value.png)

1. Ha módosítja az összesítést az alapértelmezett **mellőzése** való **darabszám (eltérők)** , a Power BI megszámlálja a különböző termékek. Ebben az esetben nincsenek négy.
  
   ![Képernyőkép – a különböző termékek száma.](media/service-aggregates/power-bi-aggregate-count.png)

1. Ha az összesítést a **Darabszám** lehetőségre módosítja, a Power BI a teljes darabszámot adja vissza. Ebben az esetben tételt tartalmaz hét **termék**.

   ![Képernyőfelvétel a termékek száma.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Ugyanazt a mezőt húzza (ebben az esetben **termék**), a **értékek** jól, és hagyja az alapértelmezett összesítés **összegzés mellőzése**, a Power BI húzzuk szerint termék.

   ![Képernyőkép a termék, a termékek száma.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

KÉRDÉS:  Miért nem látható az **Összegzés mellőzése** lehetőség?

VÁLASZ:  A kijelölt mező valószínűleg számított mérték, vagy olyan speciális mérték, amelyet a Excelben vagy a [Power BI Desktopban](desktop-measures.md) hoztak létre. Minden számított mértékhez saját nem változtatható képlet tartozik. A Power BI az összesítés nem módosítható. Ha az például összeg, akkor csak összeg maradhat. A **mezők** listájában *számított mértékek* a Számológép szimbólummal.

KÉRDÉS:  A mező **számalapú**. Miért csak a **Darabszám** és a **Darabszám (eltérők)** lehetőséget lehet kiválasztani?

VÁLASZ1:  A valószínű magyarázat az, hogy az adatkészlet tulajdonosa *nem* besorolni a mező egy számot. Ha például egy adatkészlet rendelkezik egy **év** mezőt, az adatkészlet tulajdonosa kategorizálása előfordulhat, hogy az a szöveges érték. Valószínűbb, hogy a Power bi-ban végzett munkája beleszámít a **év** mező (például született, 1974 személyek számát). Ez kevésbé valószínű, hogy a Power BI összegzi, vagy átlagos azt. Ha Ön a tulajdonosa, nyissa meg az adatkészletet a Power BI Desktopban, és használja a **modellezés** lapon módosíthatja az adattípust.

VÁLASZ2: Ha a mező a Számológép ikonnal rendelkező, azt jelenti, hogy van egy *számított mértéknek*. Minden számított mértékhez saját változtatható képlet, amely csak az adatkészlet tulajdonosa tudja módosítani. Power BI az számítás lehet egyszerű összesítés, mint például átlagolás vagy összeadás. Emellett lehet több bonyolult az valami, például egy "szülőkategóriához való hozzájárulás százaléka szülőkategória" vagy "Göngyölített összeg év kezdete óta a". A Power BI nem összegzi vagy átlagolja az eredményeket fogja. Ehelyett azt fogja csak újraszámítása (a változtatható képlet használatával) az egyes.

VÁLASZ3:  Egy másik lehetőség az, hogy az adott mezőt egy olyan *gyűjtőbe* helyezte, amely csak kategóriaértékeket engedélyez.  Ebben az esetben csak a Darabszám és a Darabszám (eltérők) típus érhető el.

VÁLASZ4:  Egy negyedik lehetőség pedig, hogy tengelyen használ a mező. Például a sávdiagramok tengelyén a Power BI egy sávot jelenít meg mindegyik eltérő értékhez kapcsolódóan – és egyáltalán nem összesíti a mezőértékeket.

>[!NOTE]
>Az egyetlen kivételt e szabály alól a pontdiagram képviseli, amely *megköveteli* az összesített értékek használatát az X és az Y tengelyeken.

KÉRDÉS:  Miért nem lehet összesíteni a szöveges mezőket az SQL Server Analysis Services- (SSAS-) adatforrásoknál?

VÁLASZ:  A többdimenziós SSAS-modellekkel való élő kapcsolat nem engedélyezi ügyféloldali összesítés, így a first, last, avg, min, max, és sum használatát sem.

KÉRDÉS:  Pontdiagramot használok, és szeretném, ha az adott mező *nem* szerepelne az összesítésben.  Hogyan?

VÁLASZ:  A **Részletek** gyűjtőbe vegye fel a mezőt, ne az X vagy Y tengelyhez tartozó gyűjtőbe.

KÉRDÉS:  Számmezők vizualizációhoz való hozzáadásakor azok többsége alapértelmezés szerint összeadásban szerepel, de a rendszer egyes mezőket átlagoláshoz, számláláshoz vagy egyéb összesítéshez használ.  Miért nem mindig ugyanazt az alapértelmezett összesítést használja a rendszer?

VÁLASZ:  Az adatkészlet tulajdonosa állíthatja be az alapértelmezett összesítést az egyes mezőkhöz. Ha Ön az adatkészlet tulajdonosa, módosítsa az alapértelmezett összesítést a a **modellezés** Power BI Desktop lapján.

KÉRDÉS:  Adatkészlet-tulajdonos vagyok, és azt szeretném, hogy a rendszer egy adott mezőt soha ne használjon összesítéshez.

VÁLASZ:  A Power BI Desktop **Modellezés** lapján állítsa be az **Adattípus** lehetőséget **Szöveg** típusra.

KÉRDÉS:  Nem látom **mellőzése** lehetőséget a legördülő listából válassza ki a.

VÁLASZ:  Próbálja eltávolítani a mezőt, majd vegye fel újra.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)