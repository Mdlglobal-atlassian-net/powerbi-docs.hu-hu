---
title: Használja a Cortanát keresése és a jelentések és irányítópultok – Power bi-ban
description: Használja a Cortanát a Power BI-hoz, hogy válaszokat nyerjen ki adataiból. Jelenleg jelentésekkel és irányítópultokkal használható.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 6d53ddcfc4121e8937810bd6f734f91cd7a9fa39
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375282"
---
# <a name="find-and-view-your-power-bi-data-with-cortana-for-power-bi"></a>Keresse meg és a Cortana a Power BI-adatok megtekintése a Power bi-hoz
Használja a Cortanát Windows 10-eszközein, ha azonnali választ szeretne kapni fontos üzleti kérdéseire. A Power BI-jal való integráció által a Cortana képes közvetlenül a Power BI-irányítópultokból és -jelentésekből kinyerni a lényeges információkat. Nem kell hozzá más, csak a Windows 10 2015. november 10-einél nem korábbi verziója, a Cortana, a Power BI és hozzáférés legalább egy adatkészlethez.

> [!IMPORTANT]
> Cortana-integráció a Power bi-ban elavulttá válik. Június 11-től kezdődően Cortana nem fog működni az irányítópultok és jelentések sem.

![A Cortana keresőmező](media/service-cortana-intro/power-bi-cortana-searchbox.png)

## <a name="preview-the-new-cortana-dashboard-search-experience-for-windows-10"></a>A Cortana Windows 10 rendszerre készült új *irányítópult*-kereső felületének előzetes verziója
Már egy ideje lehetőség van [a Cortana használatára bizonyos típusú jelentésoldalak lekéréséhez](service-cortana-answer-cards.md). Most **új funkcióval** bővítettük – irányítópultokat is lekérhet vele. Próbálja ki és [küldjön visszajelzést a Power BI ötleteket](https://ideas.powerbi.com/forums/265200-power-bi). Az *új funkció* tovább bővül, és a Cortana jelentések között is képes lesz keresni.  Az új funkció egyik fő előnye, hogy a beállítása nem igényel különösebb előkészületet – nem kell engedélyezni Cortanát vagy konfigurálni a Windows 10-et. Egyszerűen csak működik.

> [!NOTE]
> Ha mégsem működne azonnal, akkor a [hibaelhárításról szóló cikkben](service-cortana-troubleshoot.md) talál segítséget.
> 
> 

A funkció alapjául szolgáló technológia a [Microsoft Azure Search szolgáltatást](https://docs.microsoft.com/azure/search/) használja. Ez a keresési szolgáltatás olyan további képességeket biztosít, mint az intelligens rangsorolás, a hibajavítás és az automatikus kiegészítés.

Két Cortana-változat egymás mellett is létezik.

## <a name="cortana-for-power-bi-documentation"></a>A Power BI-hoz használt Cortana dokumentációja
Négy dokumentumok beállítása és a Power BI-hoz használt Cortana segítségével nyújt útmutatást.

**1. cikk** (ez a cikk): A Cortana és a Power BI együttműködésének ismertetése

**2. cikk**: [A Power BI-jelentések keresése: A Cortana, a Power BI és a Windows integrációjának engedélyezése](service-cortana-enable.md)

**3. cikk**: [A Power BI-jelentések keresése: speciális létrehozása *Cortana-válaszkártyák*](service-cortana-answer-cards.md)

**4. cikk**: [Hibaelhárítással kapcsolatos kérdések](service-cortana-troubleshoot.md)

## <a name="how-cortana-and-power-bi-work-together"></a>Hogyan működik együtt Cortana és a Power bi-ban
Amikor Ön kérdést tesz fel a Cortanának, akkor az többek között a Power BI-ban keresi a választ. A Power BI-ban a Cortana bőséges adatokon alapuló válaszokat találhat a Power BI-jelentésekben (amelyek egy különleges jelentésoldalt, úgynevezett *Cortana-válaszkártyát* tartalmaznak) és a Power BI-irányítópultokban.

Ha a Cortana egyezést talál, akkor közvetlenül az Ön Cortana-képernyőjén jeleníti meg az irányítópult vagy jelentésoldal nevét. Az irányítópult vagy jelentésoldal a Power BI-ban megnyitható. A jelentésoldalak közvetlenül a Cortanában is vizsgálhatók – interaktívak.

![interaktív jelentésoldal a Cortanában](media/service-cortana-intro/power-bi-report-cortana-s.png)

### <a name="cortana-and-dashboards-the-new-experience"></a>A Cortana és az irányítópultok (az *új funkció*)
A Cortana az Ön tulajdonában lévő és az Önnel megosztott irányítópultokon is keresi a válaszokat. A Cortanának feltett kérdésekben használhat címeket, kulcsszavakat, tulajdonosok neveit, munkaterületek neveit, alkalmazások neveit és sok mást is.

Ahhoz, hogy Cortana választ találjon, a kérdésnek legalább két szóból kell állnia. Ha olyan irányítópulton keres, amelynek egyszavas neve van (Marketing), akkor fűzze hozzá a „show” (megjelenítés), „Power BI” szavakat vagy a tulajdonos nevét a kérdéshez, például: „show Marketing (Marketing megjelenítése)” vagy „michele hart sample (michele hart minta)”. 

Ha az irányítópult címe egynél több szóból áll, Cortana csak akkor adja vissza az irányítópultot, ha a keresés egyezik a szavak közül legalább kettővel, vagy eggyel és a tulajdonos nevével. Angol nyelvű példák egy "Customer Profitability Sample" nevű irányítópulttal: 

* "show me customer" *nem* egy Power BI-irányítópult eredményt adja vissza.   
* "utterances például a"show me customer profitability","customer p","customer s","profitability sample","michele hart sample","show customer profitability sample"és"show me customer p" *tegye* visszaadni Power BI-beli eredményt.
* Hozzáadás, a "powerbi" szó egyikének számít a két szükséges szó, ezért "powerbi sample" *does* visszaadni Power BI-beli eredményt. 
  
    ![Cortana-keresés legalább két szó alapján](media/service-cortana-intro/power-bi-cortana-2-words.png)

### <a name="cortana-and-reports"></a>A Cortana és a jelentések
 A Cortana olyan jelentésekben talál válaszokat, amelyeknek [kimondottan a Cortanával való megjelenítéshez tervezett oldalai vannak](service-cortana-answer-cards.md). Elég olyan kérdéseket feltennie, amelyekben ennek a különleges jelentésoldalnak a címe vagy egyik kulcsszava szerepel.  

A jelentések használata az alapul szolgáló technológiát [Power BI Q & A](power-bi-tutorial-q-and-a.md).

Amikor Ön feltesz egy kérdést a Cortanában, a Power BI ad választ a kimondottan a Cortanához tervezett jelentésoldalak alapján. A válaszlehetőségeket a Cortana menet közben határozza meg közvetlenül a Power BI-ban már létrehozott Cortana-*válaszkártyákból*.  Egy válasz további vizsgálatához nyissa meg az eredményt a Power BI-ban.

> [!NOTE]
> Ahhoz, hogy a Cortana válaszokat kereshessen Power BI-jelentéseiben, először [engedélyeznie kell ezt a funkciót a Power BI szolgáltatásban, és be kell állítania a Windowst, hogy kommunikáljon a Power BI-jal](service-cortana-enable.md).  
> 
> 

## <a name="using-cortana-to-get-answers-from-power-bi"></a>Válaszkeresés a Power BI-ban a Cortana használatával
1. Kezdje a Cortanában. A Cortana többféleképpen is *megnyitható*: válassza a Cortana-ikont a tálcán (ábra alább), használjon hangparancsokat vagy koppintson Windows-mobileszköze keresés ikonjára.
   
     ![](media/service-cortana-intro/power-bi-cortana-searchbox.png)
2. Ha a Cortana készen áll, gépelje vagy diktálja be kérdését a Cortana keresőmezőbe. A Cortana megjeleníti a rendelkezésre álló válaszokat. Ha van a kérdésnek megfelelő Power BI-irányítópult, akkor az a **Legjobb egyezés** vagy a **Power BI** alatt jelenik meg.
   
     ![A Cortana-keresés Power BI-irányítópultot talál](media/service-cortana-intro/power-bi-cortana-search-hr.png "A Cortana Power BI-irányítópultot talál")
   
   > [!NOTE]
   > Jelenleg csak az angol nyelv támogatott.
   > 
   > 
3. Válassza ki az irányítópultot a Cortanával való megnyitásához.

    ![A Power BI-irányítópult kiválasztása](media/service-cortana-intro/power-bi-cortana-dashboard.png "A Power BI-irányítópult kiválasztása")

    Az [irányítópult *telefonos nézetének* szerkesztésével](service-create-dashboard-mobile-phone-view.md) módosíthatja az elrendezést. 

1. Cortanával arra is megvan a lehetősége, hogy a Power BI szolgáltatásban vagy a Power BI mobilverziójában nyissa meg az irányítópultot. A **Megnyitás a weben** lehetőséget választva nyissa meg az irányítópultot a Power BI szolgáltatásban. 
   
   ![Irányítópult megnyitása a Cortanából](media/service-cortana-intro/power-bi-dashboard-opens.png "Irányítópult megnyitása a Cortanából")   
4. Most használja a Cortanát egy jelentések közötti kereséshez. Tudnia kell egy olyan [jelentésről, amelynek van egy Cortana-válaszkártyát tartalmazó oldala](service-cortana-answer-cards.md). Ebben a példában egy "Cortana-New-Stores" nevű jelentésnek van egy "cortana stores" nevű Cortana-válaszkártya oldala.  
   
     Gépelje vagy diktálja be kérdését a Cortana keresőmezőjébe. A Cortana megjeleníti a rendelkezésre álló válaszokat. Ha van a kérdésnek megfelelő Power BI-jelentésoldal, akkor az a **Legjobb egyezés** vagy a **Power BI** alatt jelenik meg. Ebben a példában a válaszkártya létrehozásához használt .pbix-fájl (és annak biztonsági másolata) is megjelenik – a **Dokumentumok** alatt.
   
     ![Keresés jelentések között](media/service-cortana-intro/power-bi-cortana-search3-m.png "keresés jelentések között") 
5. Jelölje ki a **Cortana stores** jelentésoldalt, hogy megjelenjen a Cortana ablakában.
   
    ![A Cortanában megnyíló jelentésoldal](media/service-cortana-intro/power-bi-report-cortana-opens.png "A Cortanában megnyíló jelentésoldal")   
   
    Ne feledje, hogy a *válaszkártyák* az adatkészlet tulajdonosa által létrehozott különleges Power BI-jelentésoldalak.  További információ: [Cortana-válaszkártya létrehozása](service-cortana-answer-cards.md).
6. Ám ez még nem minden. A válaszkártya vizualizációi ugyanúgy használhatók, mint a Power BI-ban.
   
   * Kijelölheti például egy vizualizáció egy elemét a válaszkártya többi vizualizációján megjelenő keresztszűréshez és kiemeléshez.
     
     ![](media/service-cortana-intro/power-bi-cortana-filtered-new.png)
   * Dönthet úgy is, hogy természetes nyelvű szűrést alkalmaz az eredményeken.  Felteheti például a "Cortana stores for Lindseys" (Cortana Lindseys-üzletek) kérdést, és a kártyán csak a Lindseys üzletlánc adatai fognak látszani.
     
     ![keresztszűrés a Cortanában](media/service-cortana-intro/power-bi-cortana-filtered-2.png "keresztszűrés a Cortanában")
7. Folytassa az ismerkedést. Görgessen a Cortana ablakának aljára, és válassza a **Megnyitás a Power BI-ban** lehetőséget.
   
     ![](media/service-cortana-intro/power-bi-cortana-open-new.png)
8. A jelentésoldal megnyílik a Power BI-ban.    
     ![Jelentés megnyitása a Cortanából](media/service-cortana-intro/power-bi-cortana-open2.png "Cortana-válaszkártya nyílik meg Cortana-keresésben")

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
* Cortana hozzáférése nem bármely Cortana-kártyákhoz, amelyek még nem lett [engedélyezve van a Power bi](service-cortana-enable.md).
* Továbbra sem tudja a Power BI-jal használni Cortanát?  Próbálkozzon a [Cortana hibaelhárító eszközével](service-cortana-troubleshoot.md).
* A Power BI-hoz használt Cortana jelenleg csak angol nyelven érhető el.
* A Power BI-hoz használt Cortana csak Windows rendszerű mobileszközökön érhető el.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/).
Visszajelzést szeretne küldeni? [Visszajelzés küldése a Power BI Ideas oldalán](https://ideas.powerbi.com/forums/265200-power-bi).

## <a name="next-steps"></a>Következő lépések
[A Cortana, a Power BI és a Windows integrációjának engedélyezése jelentésekhez](service-cortana-enable.md)

