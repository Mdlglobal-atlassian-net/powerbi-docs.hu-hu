---
title: A DirectQuery használata a Power BI Desktopban
description: A DirectQuery vagy más néven élő kapcsolatok használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/18/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 775abf014f571b508832c5cb9a52a62aad455a7b
ms.sourcegitcommit: fe8a25a79f7c6fe794d1a30224741e5281e82357
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68324799"
---
# <a name="use-directquery-in-power-bi-desktop"></a>A DirectQuery használata a Power BI Desktopban
A **Power BI Desktop** használatával az adatforrásokhoz való kapcsolódáskor mindig importálhat egy másolatot az adatokról a **Power BI Desktopba**. Egyes adatforrások esetében egy alternatív módszer is használható: ha közvetlenül kapcsolódik az adatforráshoz a **DirectQuery** használatával.

## <a name="supported-data-sources"></a>Támogatott adatforrások
A **DirectQuery** használatát támogató adatforrások teljes listájáért tekintse meg [A DirectQuery által támogatott adatforrásokat](desktop-directquery-data-sources.md) ismertető cikket.

## <a name="how-to-connect-using-directquery"></a>Kapcsolódás a DirectQuery használatával
Amikor az **Adatok lekérése** funkcióval egy, a **DirectQuery** által támogatott adatforráshoz kapcsolódik, a kapcsolódási ablakban kiválaszthatja a kapcsolódás módját.  

![](media/desktop-use-directquery/directquery_2a.png)

Az **importálás** és a **DirectQuery** közötti különbségek a következők:

**Importálás** – Ezzel a módszerrel a táblákat és oszlopokat importálja a **Power BI Desktopba**. A vizualizációk létrehozása és használata során a **Power BI Desktop** az importált adatokat használja. Az alapul szolgáló adatok a kezdeti importálás vagy a legutóbbi frissítés óta történt változásainak megtekintéséhez frissítenie kell az adatokat, ami a teljes adatkészletet ismételt importálását jelenti.

**DirectQuery** – Ezzel a módszerrel nem importál vagy másol adatokat a **Power BI Desktopba**. A relációs források esetében a kiválasztott táblák és oszlopok jelennek meg a **Mezők** listában. A többdimenziós források esetében, amilyen az SAP Business Warehouse is, a kiválasztott kocka dimenziói és mértékei jelennek meg a **Mezők** listában. A vizualizációk létrehozása és használata során a **Power BI Desktop** az alapul szolgáló adatforrásból kéri le az adatokat, azaz mindig az aktuális adatokat jeleníti meg.

A **DirectQuery** használatával számos adatmodellezési és -átalakítási művelet elérhető, bár vannak bizonyos korlátozások. A vizualizációk létrehozása és használata során az adatokat a háttérforrásból kell lekérni, és a vizualizáció frissítéséhez szükséges idő a háttéradatforrás teljesítményétől függ. Ha egy kérés kiszolgálásához szükséges adatok nemrégiben már le lettek kérve, a Power BI Desktop a már lekért adatok használatával csökkenti a vizualizáció megjelenítéséhez szükséges időt. A **Kezdőlap** szalag **Frissítés** gombjával az összes vizualizációban frissítheti az adatokat az aktuális adatokra.

A **DirectQueryt** [a Power BI és a DirectQuery használatát bemutató](desktop-directquery-about.md) cikk írja le részletesen. Tekintse át továbbá a következő szakaszokat is, amelyek a **DirectQuery** használatának előnyeit, korlátait és fontos szempontjait ismertetik.

## <a name="benefits-of-using-directquery"></a>A DirectQuery használatának előnyei
Íme a **DirectQuery** használatának néhány előnye:

* A **DirectQuery** segítségével nagyon nagy adatkészletekhez készíthet vizualizációkat, amelyek esetében egyébként megoldhatatlan lenne az adatok megelőző importálása előzetes összesítéssel
* A mögöttes adatok változásai szükségessé tehetik az adatok frissítését, és egyes jelentések esetében az aktuális adatok megjelenítése nagy mennyiségű adat átvitelével járhat, ami az adatok ismételt importálását megoldhatatlanná tenné. Ezzel szemben a **DirectQuery**-jelentések mindig aktuális adatokra épülnek.
* Az 1 GB-os adatkészletkorlát a **DirectQueryre** *nem* vonatkozik

## <a name="limitations-of-directquery"></a>A DirectQuery korlátozásai
Íme a **DirectQuery** használatának néhány korlátozása:

* Ha nem [kompozit modelleket](desktop-composite-models.md) használ, minden táblának egyetlen adatbázisból kell származnia
* Ha a **Lekérdezésszerkesztőben** megadott lekérdezés túl összetett, hiba történik. A hiba javításához törölnie kell a **Lekérdezésszerkesztőben** a problémás lépést, vagy a **DirectQuery** használata helyett *importálnia* kell az adatokat. A többdimenziós forrásokhoz, amilyen az SAP Business Warehouse is, nincs **Lekérdezésszerkesztő**.
* A kapcsolatok szűrése az egyik irányra van korlátozva mindkét irány helyett (bár már elérhető a kétirányú keresztszűrés a **DirectQueryvel**). A többdimenziós forrásokhoz, amilyen az SAP Business Warehouse is, nincsenek kapcsolatok meghatározva a modellben.
* Az időintelligencia-képességek nem érhetők el a **DirectQueryben**. Például a dátumoszlopok (év, negyedév, hónap, nap stb.) speciális kezelése **DirectQuery** módban nem támogatott.
* Annak érdekében, hogy biztosítható legyen a háttéradatforrásra küldött lekérdezések elfogadható teljesítménye, a mértékekben megengedett DAX-kifejezésekre korlátozások vonatkoznak.
* A **DirectQuery** használatával legfeljebb egy millió sornyi adat adható vissza. Ez csak a visszaadott sorok számát érinti, a **DirectQuery** használatával visszaadott adatkészlet létrehozásához alkalmazott összesítéseket és számításokat nem. Például akár 10 millió sort is összesíthet egy, az adatforráson futó lekérdezéssel, és pontosan visszaadathatja az összesítésadatait a Power BI-ba a **DirectQuery** használatával, ha a Power BI-ba visszaadott sorok száma nem haladja meg az 1 milliót. Ha 1 milliónál több sort kellene visszaadnia a **DirectQueryből**, a Power BI hibát jelez.

## <a name="important-considerations-when-using-directquery"></a>Lényeges szempontok a DirectQuery használatához
A **DirectQuery** használata érdemes számításba vennie a következő három szempontot:

* **Teljesítmény és terhelés** – A rendszer minden egyes **DirectQuery**-lekérdezést a forrásadatbázisra küld, ezért a vizualizációk frissítéséhez szükséges idő attól függ, hogy az adott háttérforrás milyen gyorsan adja vissza a lekérdezés (vagy lekérdezések) eredményeit. Az ajánlott válaszidő (a kért adatok visszaadása) a **DirectQuery** használatával vizualizációk esetében legfeljebb öt másodperc, a maximális ajánlott eredmény-visszaadási idő pedig 30 másodperc. Ennél hosszabb idők esetén a jelentések felhasználói élménye elfogadhatatlanul gyenge szintre csökken. Emellett a Power BI szolgáltatásban közzétett jelentésekben a néhány percnél tovább tartó lekérdezések időtúllépést eredményeznek, és a felhasználó hibaüzenetet kap.
  
  A forrásadatbázis terhelését is érdemes figyelembe vennie a közzétett jelentést használó Power BI-felhasználók száma alapján. A *Sorszintű biztonság* (RLS) használatának is jelentős hatása lehet a teljesítményre: a több felhasználó által megosztott, nem sorszintű biztonságra konfigurált irányítópultcsempék egyetlen lekérdezést küldenek az adatbázisnak, a sorszintű biztonság használatával azonban *felhasználónként* egy lekérdezés szükséges a csempe frissítéséhez, ami jelentősen növeli a forrásadatbázis terhelését, így gyengülhet a teljesítmény.
  
  A Power BI a lehető leghatékonyabb lekérdezéseket állítja elő. Bizonyos helyzetekben azonban az összeállított lekérdezés nem elég hatékonyan kerüli el a sikertelen frissítéseket. Egy példa egy ilyen helyzetre, amikor egy előállított lekérdezés túlzottan nagy számú (1 milliónál több) sort kérne le a háttéradatforrásból, és ebben az esetben a következő hiba lép fel:
  
      The resultset of a query to external data source has exceeded
      the maximum allowed size of '1000000' rows.
  
  Ez a helyzet olyan egyszerű diagramok esetén fordulhat elő, amelyek tartalmaznak egy nagyon nagy számosságú oszlopot, és amelyekben az összesítési beállítás az *Összegzés mellőzése*. A vizualizáció legfeljebb 1 milliós számosságú oszlopokat tartalmazhat, vagy megfelelő szűrőket kell alkalmazni rá.
* **Biztonság** – A közzétett jelentéseket használó minden felhasználó a Power BI szolgáltatásban való közzététel után megadott hitelesítő adatokkal kapcsolódik a háttéradatforrásra. Ez ugyanaz a helyzet, mint az importált adatok esetében: minden felhasználó ugyanazokat az adatokat látja, függetlenül a háttérforráson definiált biztonsági szabályoktól. A felhasználószintű biztonságra vágyó ügyfeleknek DirectQuery-forrásokat és sorszintű biztonságot érdemes használniuk. [További információk a sorszintű biztonságról](service-admin-rls.md).
* **Támogatott szolgáltatások** – A **DirectQuery** módban a **Power BI Desktop** egyes funkciói korlátozottan vagy nem működnek. Emellett a Power BI szolgáltatás néhány funkciója (például a *Gyors elemzések*) a **DirectQuery**-alapú adatkészletekkel nem használható. Ezért ezeknek a szolgáltatásoknak a **DirectQuery** használata során érvényes korlátozásait érdemes figyelembe vennie a **DirectQuery** használatának mérlegelésekor.   

## <a name="publish-to-the-power-bi-service"></a>Közzététel a Power BI szolgáltatásban
A **DirectQuery** használatával létrehozott jelentések közzétehetők a Power BI szolgáltatásban.

Ha a használt adatforráshoz nem szükséges a **helyszíni adatátjáró** (**Azure SQL Database**, **Azure SQL Data Warehouse** vagy **Redshift**), meg kell adnia a hitelesítő adatokat, mielőtt a közzétett jelentés megjelenne a Power BI szolgáltatásban.

A hitelesítő adatok megadásához kattintson a **Beállítások** fogaskerék ikonjára a Power BI-ban, majd válassza a **Beállítások** lehetőséget.

![](media/desktop-use-directquery/directquery_3.png)

A Power BI megjeleníti a **Beállítások** ablakot. Itt lépjen az **Adatkészletek** lapra, és válassza ki a **DirectQueryt** alkalmazó adatkészletet, majd kattintson a **Hitelesítő adatok szerkesztése** elemre.

![](media/desktop-use-directquery/directquery_4.png)

A hitelesítő adatok megadásáig az ilyen adatforrásokra mutató **DirectQuery**-kapcsolaton keresztül közzétett jelentés megnyitása vagy adatkészlet feltárása hibát jelez.

Az **Azure SQL Database**, az **Azure SQL Data Warehouse** és a **Redshift** kivételével a DirectQueryt használó minden adatforrás esetében telepítenie kell egy **helyszíni adatátjárót**, valamint regisztrálnia kell az adatforrást az adatkapcsolat kiépítéséhez. [A helyszíni adatátjárókkal itt talál további információt](http://go.microsoft.com/fwlink/p/?LinkID=627094).

## <a name="next-steps"></a>Következő lépések
A **DirectQueryvel** kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
* [Helyszíni adatátjáró](service-gateway-onprem.md)

