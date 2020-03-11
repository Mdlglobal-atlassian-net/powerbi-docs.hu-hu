---
title: Jelentések előnézete a Power BI Jelentéskészítőben
description: Amikor egy lapszámozott jelentést készít a Jelentéskészítőben, hasznos lehet áttekinteni annak előnézetét, hogy ellenőrizze, hogy a kívánt elemek jelennek-e meg rajta.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922942"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Jelentések előnézete a Power BI Jelentéskészítőben
  Amikor egy lapszámozott jelentést készít a Jelentéskészítőben, hasznos lehet áttekinteni annak előnézetét, hogy ellenőrizze, hogy a kívánt elemek jelennek-e meg rajta. A jelentés előnézetének megtekintéséhez kattintson a **Futtatás** lehetőségre. A jelentés megjelenik az előnézeti módban.  
  
 A Jelentéskészítő hatékonyabb előnézetet biztosít szerkesztési munkamenetekkel, amennyiben egy jelentéskészítő kiszolgálóhoz csatlakozik. A szerkesztési munkamenet létrehoz egy adatgyorsítótárat, annak adatkészleteit pedig elérhetővé teszi ismételt jelentés-előnézetekhez. A szerkesztési munkamenet nem olyan funkció, amelyet Ön közvetlenül vezérel, azonban ha tisztában van vele, hogy mikor frissül a gyorsítótárazott adatkészlet, az segít növelni a teljesítményt egy jelentés előnézetének megtekintésekor, valamint megérteni, hogy miért renderel gyorsan vagy lassan.  

  
> [!NOTE]  
> A Jelentéskészítőben való előnézet és a böngészőben való megtekintés között található néhány eltérés. A naptárvezérlő, amelyet egy Dátum/Idő típusú paraméter megadásakor ad hozzá a jelentéshez, eltér a Jelentéskészítőben és a böngészőben. 
  
## <a name="improving-preview-performance"></a>Az előnézet teljesítményének növelése  
 A jelentések létrehozásának és frissítésének módja befolyásolja, hogy milyen gyorsan renderel a jelentés előnézete. Amikor először tekinti meg egy kiszolgálóhivatkozásra épülő jelentés előnézetét, létrejön egy szerkesztési munkamenet, a rendszer pedig hozzáadja a jelentés futtatásakor használt adatokat a tárolt adatgyorsítótárhoz. Amikor olyan módosításokat végez a jelentésen, amely nincs hatással az adatokra, a jelentés az adatok gyorsítótárazott másolatát használja. Ez azt jelenti, hogy nem látja az adatok változását a jelentés minden előnézeti megtekintésekor. Ha új adatokat szeretne látni, kattintson a menüszalag **Frissítés** gombjára.  
  
 A következő műveletek frissítik a gyorsítótárat, és lelassítják a jelentés renderelését a következő előnézet megnyitásakor:  
  
-   Adatkészlet hozzáadása, módosítása vagy törlése. A gyorsítótárazott adatkészlet a jelentés által használt összes adatkészletet tartalmazza, amelyek bármelyikének módosítása érvényteleníti a gyorsítótárazott adatkészletet. Ide tartozik az adatkészlet nevének, lekérdezéseinek vagy mezőinek módosítása.  
  
    > [!NOTE]  
    >  Ha az adatkészlet számos olyan mezőt tartalmaz, amelyet várhatóan nem fog használni, frissítse úgy a készletet, hogy ezeket kihagyja belőle. Bár ezzel egy új szerkesztési munkamenet jön létre, a jelentés első előnézete pedig lassabb lesz, a kisebb méretű gyorsítótárazott adatkészlet összességében jó hatással van a jelentéskészítő kiszolgáló teljesítményére.  
  
-   Adatforrás hozzáadása, módosítása vagy törlése. Ide tartozik az adatforráshoz, az adatforrás adatfeldolgozási bővítményéhez, vagy az adatforrás kapcsolati tulajdonságaihoz tartozó név vagy tulajdonságok módosítása.  
  
-   A jelentés által használt adatforrás módosítása.  
  
-   A jelentés nyelvének módosítása.  
  
-   A jelentés által használt szerelvények vagy egyéni kód módosítása.  
  
-   A jelentés lekérdezési paramétereinek vagy a paraméterértékek hozzáadása, módosítása vagy törlése.  
  
 A jelentés elrendezésének és adatformázásának módosítása nincs hatással a gyorsítótárazott adatkészletre. A következő műveleteket végezheti el a gyorsítótárazott adatkészlet frissítése nélkül:  
  
-   Adatrégiók (táblázatok, mátrixok vagy diagramok) hozzáadása vagy eltávolítása.  
  
-   A jelentés oszlopainak hozzáadása vagy eltávolítása. Az adatkészlet minden mezője használható a jelentésben. A jelentés mezőinek hozzáadása vagy eltávolítása nincs hatással az adatkészletre.  
  
-   A táblázatok és mátrixok mezőinek sorrendjének módosítása.  
  
-   Sor- és oszlopcsoportok hozzáadása, módosítása vagy törlése.  
  
-   Mezők adatértékeihez tartozó formázás hozzáadása, módosítása vagy törlése.  
  
-   Képek, sorok vagy szövegmezők hozzáadása, módosítása vagy törlése.  
  
-   Oldaltörések módosítása.  
  
A szerkesztési munkamenet a jelentés első előnézeti megtekintésekor jön létre. Alapértelmezés szerint ez 7200 másodpercig (2 óráig) tart. A munkamenet a jelentés minden futtatásakor visszaáll két órára. Amikor lejár a szerkesztési munkamenet, az adatgyorsítótár törlődik. Ha lejár a szerkesztési munkamenet, egy új automatikusan létrejön a jelentés következő előnézeti megtekintésekor.
  
Az adatgyorsítótár alapértelmezés szerint öt adatkészletet képes tárolni. Ha számos különböző paraméterérték-kombinációt használ, a jelentésnek több adatra lehet szüksége. Ehhez frissíteni kell a gyorsítótárat, a jelentés pedig lassabban renderel a következő előnézeti megtekintéskor. 
  
## <a name="concurrency-of-report-updates"></a>A jelentésfrissítések egyidejűsége  
A jelentések előnézeti megtekintése gyakran a jelentés frissítési és mentési folyamatának egy lépése a Power BI szolgáltatásban. Egy jelentés frissítésekor előfordulhat, hogy valaki más is éppen akkor frissíti, majd menti a jelentést. A legutóbb mentett jelentés a jövőbeni megtekintéshez és frissítéshez rendelkezésre álló jelentésverzió. Ez azt jelenti, hogy az előnézetként megtekintett jelentésverzió nem feltétlenül lesz az ismét megnyitott verzió. A jelentést mentheti új névvel a Jelentéskészítő menüjének **Mentés másként** lehetőségével.  
  
## <a name="external-report-items"></a>Külső jelentéselemek  
 A jelentés olyan elemeket is tartalmazhat, mint külső képek, amelyek a jelentéstől külön vannak tárolva. Mivel ezek külön tárolt elemek, áthelyezhetők máshová, vagy törölhetők. Ilyen esetben előfordulhat, hogy nem tekinthető meg a jelentés előnézete. Frissítheti a jelentést úgy, hogy az jelezze az elem új helyét; ha az elemet törölték, lecserélheti egy meglévőre; vagy el is távolíthatja az elemre való hivatkozást a jelentésből.  
  
## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
  
