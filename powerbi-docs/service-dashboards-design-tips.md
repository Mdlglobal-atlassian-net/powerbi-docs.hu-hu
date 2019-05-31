---
title: Tippek a tökéletes Power BI-irányítópult megtervezéséhez
description: Tippek a tökéletes Power BI-irányítópult megtervezéséhez
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: a113cf75ae238b19cdc54b03ffc049bdcdfb8368
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61150331"
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>Tippek a tökéletes Power BI-irányítópult megtervezéséhez
Most, hogy létrehozta az irányítópultot, és hozzáadott néhány csempét is, gondolja át, hogyan tehetné irányítópultját egyszerre ízlésessé és célratörővé. Ennek a legjobb módja, ha a legfontosabb információ a legfeltűnőbb, amelynek megjelenése letisztult és rendezett.

Íme, néhány tipp.

> [!TIP]
> A jelentésekre vonatkozó tervezési elvek közül jó néhány az irányítópultra is igaz.  Olvassa el következő tanulmányunkat: [A legjobb tervezési elvek jelentések és vizualizációk elkészítéséhez](visuals/power-bi-visualization-best-practices.md).
>
>

## <a name="watch-the-dashboard-makeover-webinarhttpsinfomicrosoftcomco-powerbi-wbnr-fy16-05may-12-dashboard-makeover-registrationhtml"></a>Tekintse meg az [irányítópultok átalakításával foglalkozó webes szemináriumot](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html)
Megtekintheti, ahogy Marc Reguera (a Microsoft fő programmenedzsere, a Power BI-irányítópultok szakértője) [irányítópultokat alakít át](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html).

## <a name="consider-your-audience"></a>Mindig gondoljon a közönségére
Mely kulcsfontosságú mérőszámok segítik őket leginkább a döntéshozatalban? Hogy fogják használni az irányítópultot? Milyen tanult vagy kulturális előfeltevések befolyásolhatják a tervezés során hozott döntéseket? Milyen információkra van szüksége a közönségének a sikerhez?

Ne feledje, hogy az irányítópult az áttekintés eszköze, amelynek segítségével egy helyen követheti nyomon az adatok aktuális állapotát. Az irányítópult az alapul szolgáló jelentéseken és adatkészleteken alapszik, és ezek rengeteg részletet tartalmaznak. Az olvasók az irányítópulton keresztül érhetik el a jelentéseket. Ezért hacsak nem a részleteket monitorozzák az olvasók, ne az irányítópulton jelenítse azokat meg.

Hol fog megjelenni az irányítópult? Ha egy nagyobb képátmérőjű monitoron jeleníti meg, akkor több tartalmat is elhelyezhet rajta. Ha azonban az olvasók a táblagépükön tekintik meg az irányítópultot, az olvashatóság érdekében használjon kevesebb csempét.

## <a name="tell-a-story-and-keep-it-to-one-screen"></a>Mondja el a történetet egyetlen képernyő használatával
Mivel az irányítópultok célja, hogy egyetlen pillantás alatt leolvashassuk a legfontosabb információkat, a legjobb, ha minden csempét egyetlen képernyőn jelenít meg. El tudja kerülni a görgetősávok használatát az irányítópulton?

Túlságosan zsúfolt az irányítópult?  A legfontosabb, könnyen olvasható és értelmezhető információk kivételével távolítson el minden további adatot.

## <a name="make-use-of-full-screen-mode"></a>Használja a teljes képernyős módot
Irányítópultját minden felesleges információ nélkül, [Teljes képernyős](consumer/end-user-focus.md) módban jelenítse meg.

## <a name="make-the-most-important-information-biggest"></a>A legfontosabb információt jelenítse meg a legnagyobbként
Ha az irányítópulton található szövegek és a vizualizációk azonos méretűek, az olvasóknak nehezére esik majd a legfontosabb információra összpontosítani. A kártyavizualizációk segítségével például hatásosan tudja megjeleníteni a fontos számokat:  
![Kártyavizualizáció](media/service-dashboards-design-tips/pbi_card.png)

De ügyeljen arra, hogy a kontextust is megadja.  

Olvassa el a [csupán egyetlen számmal ellátott csempe létrehozására](visuals/power-bi-visualization-card.md) vonatkozó részt.

## <a name="put-the-most-important-information-in-the-upper-corner"></a>A legfontosabb információt helyezze a felső sarokba
A legtöbb ember fentről lefelé kezd olvasni, így célszerű a képernyő tetején elhelyezni a legfontosabb részletet, és a közönség olvasási irányának megfelelően növelni a részletsűrűséget (balról jobbra, jobbról balra).

## <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>Használja az adatoknak leginkább megfelelő vizualizációt, a formázással pedig igyekezzen elősegíteni a könnyű olvasást
Pusztán a változatosság kedvéért ne változtasson a vizualizáción.  A vizualizáció célja egy adott kép könnyen „olvasható” és értelmezhető ábrázolása.  Bizonyos adatok és vizualizációk esetében egy egyszerű grafikus vizualizáció is elegendő. Más esetekben azonban összetettebb vizualizációkra lehet szükség, ezért a csempék és címkék használatával, illetve további testreszabással igyekezzen segíteni az olvasót.  

* [Megfelelő adatvizualizációt válasszon](https://www.youtube.com/watch?v=-tdkUYrzrio). Legyen óvatos a valóságot eltorzító, azaz 3D diagramok használatával. Ne feledje, hogy az emberi agy számára nehézséget jelent a körkörös alakok értelmezése. Bár a tortadiagramok, fánkdiagramok, mérőműszerek és egyéb kör alakú diagramok tetszetősek, az adatvizualizáció szempontjából nem ez az ajánlott eljárás.
* A diagramokon belül használja következetesen a tengelyeken található diagramméreteket, a diagramméret-elrendezést és a diagramértékekhez használt színeket.
* Ügyeljen arra, hogy ízlésesen kódolja a mennyiségi adatokat. A számok megjelenítésénél három vagy négy számjegynél ne használjon többet. A tizedesvesszőtől egy vagy két hellyel balra található számjegyeket jelenítse meg, és léptékezze a számokat ezres vagy milliós nagyságrendre, tehát 3,4 millió 3 400 000 helyett.
* A pontosság és az időpont szintjét soha ne keverje. Győződjön meg róla, hogy az időkeretek jól értelmezhetők.  Ne helyezzen egy, a múlt hónapot és az év egy más hónapját szemléltető szűrt diagramot egymás mellé.
* Ne keverje a kis és nagy értékeket ugyanazon a skálán, tehát például egy vonal - vagy oszlopdiagramon.  Vegyük például azt az esetet, amikor az egyik érték milliós, a másik pedig ezres nagyságrendben van.  A skála nagysága miatt ebben az esetben nehéz lenne látni az ezres nagyságrendű értékek különbségeit.  Ha kevernie kell az értékek nagyságrendjeit, válasszon olyan vizualizációt, amely lehetővé teszi egy második tengely használatát.
* Feleslegesen ne tűzdelje tele adatcímkékkel a diagramokat. Az oszlopdiagramokon szereplő értékek általában a konkrét számok megjelenítése nélkül is könnyen értelmezhetőek.
* Ügyeljen a [diagramok rendezési](consumer/end-user-change-sort.md) módjára.  A legmagasabb vagy legalacsonyabb számok kiemeléséhez rendezze az adatokat a mértékek szerint.  Ha azt szeretné, hogy a felhasználók könnyedén megtaláljanak egy adott kategóriát a többi között, rendezze az adatokat a tengelyek szerint.  
* Az ideális tortadiagramok kevesebb mint nyolc kategóriát tartalmaznak. Mivel a tortadiagramban nem lehet két értéket egymás mellett megjeleníteni, ezért jóval nehezebb az értékek összehasonlítása, mint egy oszlopdiagramon. A tortadiagramok alkalmasabbak a rész-egész viszonyok szemléltetésére, mint az egyes részek összehasonlítására. A mérőműszer-diagramokkal rendkívül jól lehet szemléltetni egy aktuális állapotot az adott cél tekintetében.

A vizualizációval kapcsolatos további segítségért olvassa el a következő részt: [Vizualizációtípusok a Power BI-ban](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learning-more-about-best-practice-dashboard-design"></a>További információk az ajánlott irányítópult-tervezési eljárásokról
A tökéletes irányítópult-tervezés elsajátításához érdemes megismerkedni a vizuális érzékelés alapvető Gestalt-elveivel, valamint a gyakorlatban is használható információk kontextusban történő, egyértelmű kommunikációjával. Szerencsére számtalan széles körben, többek között a blogjainkon is elérhető forrásanyag áll rendelkezésre. Itt van néhány kedvenc könyveink közül:

* Stephen Few *Information Dashboard Design* című könyve  
* Stephen Few *Show Me the Numbers* című könyve  
* Stephen Few *Now You See It* című könyve  
* Edward Tufte *Envisioning Information* című könyve  
* Andrew Abela *Advanced Presentations* című könyve   

## <a name="next-steps"></a>Következő lépések
[Irányítópult létrehozása jelentésből](service-dashboard-create.md)  
[Power BI – Alapfogalmak](consumer/end-user-basic-concepts.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
