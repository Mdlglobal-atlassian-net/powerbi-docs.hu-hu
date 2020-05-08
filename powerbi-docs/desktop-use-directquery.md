---
title: A DirectQuery használata a Power BI Desktopban
description: A DirectQuery vagy más néven élő kapcsolatok használata a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d8432ae10afab6cbf12c017a8f315fd55825212d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "77427231"
---
# <a name="use-directquery-in-power-bi-desktop"></a>A DirectQuery használata a Power BI Desktopban
A *Power BI Desktop* használatával az adatforrásokhoz való kapcsolódáskor mindig importálhat egy másolatot az adatokról a Power BI Desktopba. Egyes adatforrások esetében egy alternatív módszer is használható: ha közvetlenül kapcsolódik az adatforráshoz a DirectQuery használatával.

## <a name="supported-data-sources"></a>Támogatott adatforrások
A DirectQuery használatát támogató adatforrások teljes listáját [A DirectQuery által támogatott adatforrások](power-bi-data-sources.md) című cikkben találhatja meg.

## <a name="how-to-connect-using-directquery"></a>Kapcsolódás a DirectQuery használatával
Amikor az **Adatok betöltése** funkcióval egy, a DirectQuery által támogatott adatforráshoz kapcsolódik, a kapcsolódási párbeszédpanelen kiválaszthatja a kapcsolódás módját. Választhatja például a Power BI Desktop **Kezdőlap** menüszalagján az **Adatok betöltése** > **SQL Server** lehetőséget. Az **SQL Server-adatbázis** párbeszédpanelen az **Adatkapcsolati mód** az **Importálás** és a **DirectQuery** beállítást kínálja fel:

![Az Importálás és a DirectQuery beállítás az SQL Server-adatbázis párbeszédpanelen a Power BI Desktopban](media/desktop-use-directquery/directquery_sqlserverdb.png)

Az **Importálás** és a **DirectQuery** kiválasztása közötti különbségek a következők:

- **Importálás**: A kijelölt táblák és oszlopok importálva lesznek a Power BI Desktopba. A vizualizációk létrehozása és használata során a Power BI Desktop az importált adatokat használja. A mögöttes adatoknak az első importálás vagy az utolsó frissítés utáni változásai csak akkor jelennek meg, ha frissíti az adatokat, ezzel pedig ismét importálja a teljes adathalmazt.

- **DirectQuery**: Ezzel a módszerrel nem importál vagy másol adatokat a Power BI Desktopba. A relációs források esetében a kiválasztott táblák és oszlopok jelennek meg a **Mezők** listában. A többdimenziós források esetében, amilyen az SAP Business Warehouse is, a kiválasztott kocka dimenziói és mértékei jelennek meg a **Mezők** listában. A vizualizációk létrehozása és használata során a Power BI Desktop a mögöttes adatforrásból kéri le az adatokat, tehát mindig az aktuális adatokat jeleníti meg.

A DirectQuery használatával számos adatmodellezési és -átalakítási művelet elérhető, bár vannak bizonyos korlátozások. A vizualizációk létrehozása vagy kezelése során le kell kérdeznie a mögöttes forrást. A vizualizáció frissítéséhez szükséges idő a háttéradatforrás teljesítményétől függ. Ha egy kérés kiszolgálásához szükséges adatok nemrégiben már le lettek kérve, a Power BI Desktop a már lekért adatok használatával csökkenti a vizualizáció megjelenítéséhez szükséges időt. A **Kezdőlap** menüszalag **Frissítés** gombjával az összes vizualizációban frissítheti az adatokat az aktuális adatokra.

A DirectQueryt [a Power BI és a DirectQuery](desktop-directquery-about.md) használatát bemutató cikk írja le részletesen. Tekintse át továbbá a következő szakaszokat is, amelyek a DirectQuery használatának előnyeit, korlátait és fontos szempontjait ismertetik.

## <a name="benefits-of-using-directquery"></a>A DirectQuery használatának előnyei
A DirectQuery használatának néhány előnye:

- A DirectQuery segítségével nagyon nagy adatkészletekhez készíthet vizualizációkat, amelyek esetében egyébként megoldhatatlan lenne az adatok megelőző importálása előzetes összesítéssel.
- A mögöttes adatok változása adatfrissítést tehet szükségessé. Egyes jelentések esetében az aktuális adatok megjelenítése nagy mennyiségű adat átvitelével járhat, ami az adatok ismételt importálását megoldhatatlanná tenné. Ezzel szemben a DirectQuery-jelentések mindig aktuális adatokra épülnek.
- Az 1 GB-os adathalmaz-korlát a DirectQueryre *nem* vonatkozik.

## <a name="limitations-of-directquery"></a>A DirectQuery korlátozásai
A DirectQuery használata jelenleg néhány korlátozással jár:

- Ha a **Lekérdezésszerkesztőben** megadott lekérdezés túl összetett, hiba történik. A hiba javításához a **Lekérdezésszerkesztőben** törölheti a problémás lépést, vagy a DirectQuery használata helyett *importálhatja* az adatokat. A többdimenziós forrásokhoz, amilyen az SAP Business Warehouse is, nincs **Lekérdezésszerkesztő**.

- Az időintelligencia-képességek nem érhetők el a DirectQueryben. Például a dátumoszlopok (amilyen az év, negyedév, hónap vagy nap) speciális kezelése DirectQuery módban nem támogatott.

- Annak érdekében, hogy biztosítható legyen a háttéradatforrásra küldött lekérdezések elfogadható teljesítménye, a mértékekben megengedett DAX-kifejezésekre korlátozások vonatkoznak.

- A DirectQuery használatával legfeljebb egymillió sornyi adat adható vissza, kivéve, ha Premium-kapacitást használ. Ez a DirectQuery használatával visszaadott adathalmaz létrehozásához alkalmazott összesítéseket és számításokra nem vonatkozik. Csak a visszaadott sorokat érinti. A Premium-kapacitások beállíthatják a maximális sorkorlátokat, amint az [ebben a bejegyzésben](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/) szerepel. 

    Az adatforráson futó lekérdezéssel összesíthet például 10 millió sort. A lekérdezés a DirectQuery használatával pontosan visszaadja a Power BI-nak az összesítés eredményét, ha a visszaadott Power BI-adatok kevesebb, mint 1 millió sorból állnak. Ha a DirectQuery több mint 1 millió sort ad vissza, a Power BI hibajelzést ad (kivéve a Premium-kapacitásban, ha a sorok száma a rendszergazda által megadott korlát alatti).

## <a name="important-considerations-when-using-directquery"></a>Lényeges szempontok a DirectQuery használatához
A DirectQuery használata során érdemes számításba vennie a következő három szempontot:

- **Teljesítmény és terhelés**: Minden egyes DirectQuery-lekérdezés a forrásadatbázishoz van elküldve, ezért a vizualizáció frissítéséhez szükséges idő attól függ, hogy az adott háttérforrás milyen gyorsan adja vissza a lekérdezés (vagy lekérdezések) eredményeit. Az ajánlott válaszidő (a kért adatok visszaadására) a DirectQuery használatával vizualizációk esetében legfeljebb öt másodperc, a maximális ajánlott idő pedig 30 másodperc. Ennél hosszabb idők esetén a jelentések felhasználói élménye elfogadhatatlanul gyenge szintre csökken. A Power BI szolgáltatásban már közzétett jelentésekben a néhány percnél tovább tartó lekérdezések időtúllépést eredményeznek, és a felhasználó hibaüzenetet kap.
  
    A forrásadatbázis terhelését is érdemes figyelembe vennie a közzétett jelentést használó Power BI-felhasználók száma alapján. A **sorszintű biztonság** (RLS) használata is jelentős következményekkel járhat. A több felhasználóval megosztott, sorszintű biztonság nélküli irányítópult-csempék egyetlen lekérdezést küldenek az adatbázisnak. Sorszintű biztonságot használó csempék esetén azonban a csempe frissítéséhez általában *felhasználónként* egy lekérdezés szükséges, ezáltal jelentősen nő a forrás-adatbázis terhelése, ez pedig a teljesítményt is befolyásolhatja.
  
    A Power BI a lehető leghatékonyabb lekérdezéseket állítja elő. Bizonyos helyzetekben azonban az összeállított lekérdezés nem elég hatékonyan kerüli el a sikertelen frissítéseket. Ilyen helyzet áll elő például akkor, ha a generált lekérdezés rendkívül sok sort kér le a háttérbeli adatforrásból. Ebben az esetben a következő hiba keletkezik:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Ez a helyzet olyan egyszerű diagramok esetén fordulhat elő, amelyek tartalmaznak egy nagyon nagy számosságú oszlopot, és amelyekben az összesítési beállítás az **Összegzés mellőzése**. A vizualizáció legfeljebb 1 milliós számosságú oszlopokat tartalmazhat, vagy megfelelő szűrőket kell alkalmaznia.

- **Biztonság**: Alapértelmezés szerint a közzétett jelentéseket használó minden felhasználó a Power BI szolgáltatásban való közzététel után megadott hitelesítő adatokkal csatlakozik a háttéradatforráshoz. Ez ugyanaz az eljárás, mint az importált adatok esetében: minden felhasználó ugyanazokat az adatokat látja, függetlenül a háttérforráson definiált biztonsági szabályoktól.

    A DirectQuery-forrásokkal implementált felhasználószintű biztonságra vágyó ügyfeleknek sorszintű biztonságot vagy a forrásra vonatkozó, Kerberos által korlátozott hitelesítést érdemes használniuk. A Kerberos nem minden forráshoz érhető el. [További információk a sorszintű biztonságról](service-admin-rls.md). [További információk a Kerberos a DirectQueryben történő használatáról](service-gateway-sso-kerberos.md).

- **Támogatott funkciók**: A Power BI Desktop egyes funkciói DirectQuery módban nem, vagy csak bizonyos korlátozásokkal támogatottak. Emellett a Power BI szolgáltatás néhány funkciója (például a *Gyors elemzések*) sem érhető el DirectQueryt használó adathalmazokhoz. Ha a DirectQuery használatáról kell döntenie, érdemes figyelembe venni ezeket a funkciókra vonatkozó korlátozásokat.

## <a name="publish-to-the-power-bi-service"></a>Közzététel a Power BI szolgáltatásban
A DirectQuery használatával létrehozott jelentések közzétehetők a Power BI szolgáltatásban.

Ha a használt adatforráshoz nem szükséges a **helyszíni adatátjáró** (**Azure SQL Database**, **Azure SQL Data Warehouse** vagy **Redshift**), hitelesítő adatokat kell megadnia ahhoz, hogy a Power BI szolgáltatás megjelenítse a közzétett jelentést. A hitelesítő adatok megadásához kövesse az alábbi utasításokat:

1. Jelentkezzen be a [Power BI-ba](https://www.powerbi.com/).
2. A Power BI szolgáltatásban válassza a **Beállítások** fogaskerék ikonját, majd a **Beállítások** menüpontot.

    ![Beállítások, Power BI szolgáltatás](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. A Power BI szerkesztés **Beállítások** oldalán lépjen az **Adathalmazok** lapra, jelölje ki a DirectQueryt használó adathalmazt, majd válassza a **Hitelesítő adatok szerkesztése** lehetőséget.

4. Vegye fel a hitelesítő adatokat. Ellenkező esetben hiba lép fel, amikor megnyitja a közzétett jelentést, vagy olyan adathalmaz kezel, amely DirectQuery-kapcsolattal lett létrehozva.

Adatkapcsolat kiépítéséhez az **Azure SQL Database**, az **Azure SQL Data Warehouse** a **Redshift** és a **Snowflake Data Warehouse** kivételével a DirectQueryt használó minden adatforrás esetében telepítenie kell egy **helyszíni adatátjárót**, valamint regisztrálnia kell az adatforrást. További információ: [Mi az a helyszíni adatátjáró?](service-gateway-onprem.md)

## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a DirectQueryről, tekintse át a következő forrásanyagokat:

- [DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
- [A DirectQuery által támogatott adatforrások](power-bi-data-sources.md)
- [DirectQuery és SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
- [Mi az a helyszíni adatátjáró?](service-gateway-onprem.md)
