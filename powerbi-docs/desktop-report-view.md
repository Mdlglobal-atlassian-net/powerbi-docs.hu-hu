---
title: Jelentés nézet a Power BI Desktopban
description: Jelentés nézet a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 06b8c9d0be2ec8bc5b350767263bfc5e0ab4ec81
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877869"
---
# <a name="report-view-in-power-bi-desktop"></a>Jelentés nézet a Power BI Desktopban
Ha már dolgozott a Power BI-jal, tudja, milyen egyszerűen hozhatók létre dinamikus perspektívákat és adatelemzést biztosító jelentések. A Power BI speciális funkciókat tesz elérhetővé a Power BI Desktopban. A Power BI Desktoppal többek között létrehozhat összetett lekérdezéseket, egyesíthet különböző forrásokból származó adatokat és kapcsolatot hozhat létre táblák között.

A Power BI Desktop egy **Jelentés nézetet** is tartalmaz, amelyben bármennyi, vizualizációkat tartalmazó jelentésoldalt létrehozhat. A Jelentés nézet felülete nagyjából ugyanazzal a kialakítással rendelkezik, mint egy jelentés Szerkesztési nézete a Power BI szolgáltatásban. Többek között áthelyezheti a vizualizációkat, vagy másolhatja, beillesztheti és egyesítheti őket.

A különbség az, hogy ha a Power BI Desktopot használja, dolgozhat lekérdezésekkel, és modellezheti az adatokat annak érdekében, hogy az adatai a legjobb elemzést tegyék lehetővé a jelentésekben. Ezután mentheti a Power BI Desktop-fájlt bárhová, ahová szeretné, legyen az a helyi lemez vagy a felhő.

## <a name="lets-take-a-look"></a>Nézzük meg mindezt a gyakorlatban!
Ha először tölt be adatokat a Power BI Desktopba, a **Jelentés nézet** egy üres vászonnal jelenik meg.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Ha a bal oldali navigációs ablaktáblán található ikonokra kattint, válthat a **Jelentés nézet**, az **Adat nézet** és a **Kapcsolat nézet** között:

![Jelentés nézet ikonja](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Miután hozzáadott néhány adatot, hozzáadhat mezőket az új vizualizációhoz a vásznon.

![Vizualizáció hozzáadása a Mezők panelről való áthúzással](media/desktop-report-view/pbid_reportview_addvis.gif)

A vizualizáció típusának módosításához kiválaszthatja azt a menüszalagon található **Vizualizáció** csoportból, vagy kattinthat a jobb gombbal, és választhat egy másikat a **Vizualizáció típusának módosítása** ikonnal.

![Vizualizáció módosítása új kijelölésével](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Érdemes kipróbálnia különböző vizualizációtípusokat is. Fontos, hogy a vizualizáció egyértelmű módon közölje az információkat.

Egy jelentés legalább egy üres oldallal kezdődik. Az oldalak a kezelőpanelen jelennek meg, a vászon bal oldalán. Egy oldalhoz sokféle vizualizációt hozzáadhat, de fontos, hogy ne vigye túlzásba őket. A túl sok vizualizáció zsúfolttá teheti az oldalt, és nehézkessé a megfelelő információ megtalálását. Új oldalakat is hozzáadhat a jelentéshez. Ehhez egyszerűen kattintson az **Új oldal** elemre a menüszalagon.

![Új oldal ikon](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Egy oldal törléséhez a Jelentés nézet alján kattintson az **X** elemre az oldal lapján.

![Lap hozzáadása jelentéshez](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> A jelentések és a vizualizációk nem rögzíthetők a Power BI Desktop irányítópultján. Ehhez [közzé kell tennie azokat a Power BI Desktopból](desktop-upload-desktop-files.md) a Power BI-webhelyen.

## <a name="copy-and-paste-between-reports"></a>Jelentések közötti másolás és beillesztés

Egy vizualizáció egyszerűen kimásolható egy Power BI Desktop-jelentésből, és beilleszthető egy másik jelentésbe. A jelentésben lévő vizualizáció egyszerűen kimásolható a **CTRL+C** billentyűparanccsal, majd beilleszthető a másik Power BI Desktop-jelentésbe a **CTRL+V** használatával. Egyszerre egy, vagy egy oldalon belül több másolandó vizualizációt is kijelölhet, és beilleszthet a cél Power BI Desktop-jelentésbe. 

A vizualizációk másolásának és beillesztésének lehetősége azok számára hasznos, akik rendszeresen készítenek és frissítenek több jelentést. A fájlok közötti másoláskor a Formázás panelen explicit módon megadott beállítások és formázások is másolva lesznek, a témára vagy alapértelmezett beállításokra épülő vizuális elemek pedig automatikusan a céljelentés témájának megfelelően lesznek frissítve. Ha tehát egy vizualizációt már megformázott a kívánt módon, átmásolhatja az újabb jelentésekbe, és a formázásba fektetett munka nem vész kárba.

Ha a modellben lévő mezők eltérnek, akkor a vizualizáción hibajelzés jelenik meg, és egy figyelmeztetés tájékoztatja a hiányzó mezőkről. Ez a hiba ahhoz hasonló, amikor törlik a modellnek a vizualizáció által használt egyik mezőjét. 

![Hiba vizualizáció másolásakor/beillesztésekor – hiányzó adatmező](media/desktop-report-view/report-view_07.png)

A hiba javításához elég pótolni a hiányzó mezőket a használni kívánt mezőkkel az abban a jelentésben lévő modellből, ahová a vizualizációt beillesztette. Ha egyéni vizualizációt használ, akkor ezt az egyéni vizualizációt is importálnia kell a céljelentésbe.




## <a name="hide-report-pages"></a>Jelentésoldalak elrejtése

Jelentés létrehozásánál a jelentés egyes lapjait el is rejtheti. Ez akkor lehet hasznos, ha a jelentésben alapul szolgáló adatokat vagy vizualizációkat kell létrehoznia, de nem szeretné, ha ezek az oldalak megjelennének mások számára, például ha olyan táblázatokat vagy vizualizációkat hoz létre, amelyeket más jelentésoldalakhoz szeretne felhasználni. Ezen kívül számos más kreatív oka is lehet annak, hogy egy létrehozott jelentésoldalt el szeretne rejteni egy közzétett jelentésben. 

A jelentésoldal elrejtése egyszerűen elvégezhető. Kattintson jobb gombbal a jelentésoldalt jelző fülre, és a megjelenő menüben válassza az **Elrejt** lehetőséget.

![Oldal elrejtése beállítás](media/desktop-report-view/report-view_05.png)

A jelentésoldal elrejtésénél fontos lehet figyelembe venni néhány szempontot:

* A **Power BI Desktopban** a rejtett jelentésnézet is látható, jóllehet az oldal címe szürkén jelenik meg. Az alábbi képen a 4. oldal (Page 4 címmel) el van rejtve.

    ![szürkén megjelenő, rejtett oldal](media/desktop-report-view/report-view_06.png)

* Ha a jelentést a **Power BI szolgáltatásban** nézik meg, az elrejtett jelentésoldal *nem jelenik meg*.

* A jelentésoldalak elrejtése *nem* biztonsági célokat szolgál. Az oldalt a felhasználók továbbra is elérhetik, és a tartalma is hozzáférhető a részletező elemzés és más módszerek használatával.

* Az elrejtett oldal esetén a Megtekintési módban nem jelennek meg navigációs nyilak.

