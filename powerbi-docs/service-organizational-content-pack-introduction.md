---
title: "Bevezetés a Power BI szervezeti tartalomcsomagjainak használatába"
description: "Ebben a cikkben arról olvashat, miként rendezheti olyan szervezeti tartalomcsomagokba irányítópultjait, jelentéseit, Excel-munkafüzeteit és adatkészleteit, amelyeket aztán megoszthat munkatársaival."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00ddec3dbf4087935a7c3583138dabb2a83f0ae5
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/24/2018
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Bevezetés a Power BI szervezeti tartalomcsomagjainak használatába
> [!NOTE]
> Hallott már az új *alkalmazásokról*? Az alkalmazásokkal új módon oszthatja meg a nagyközönséggel a tartalmakat a Power BI-ban. Javasoljuk az alkalmazások használatát a vállalati tartalomcsomagok vagy csak olvasható munkaterületek helyett. [További információ az alkalmazásokról](service-install-use-apps.md).
> 
> 

Rendszeresen oszt meg jelentéseket a csapatával e-mailben? Próbálja inkább így: csoportosítsa irányítópultjait, jelentéseit, Excel-munkafüzeteit és adatkészleteit, és tegye őket közzé a csapatában *szervezeti tartalomcsomagok* formájában. Az így létrehozott tartalomcsomagokat a csapattagok könnyen elérhetik az AppSource-katalógusban. A csomagok részét képezik a Power BI-nak, így minden funkcióját képesek kihasználni, beleértve az interaktív adatáttekintést, az új vizualizációs lehetőségeket, a Q&A szolgáltatást, a más adatforrásokkal történő integrációt, az adatfrissítést és egyebeket.

![](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

Ha tartalomcsomagokat hoz létre, az különbözik irányítópultok puszta megosztásától és az alkalmazás-munkaterületen folytatott közös használatától. Az [Irányítópultok és jelentések közös használata és megosztása](service-how-to-collaborate-distribute-dashboards-reports.md) című cikkben leírtak segítenek kiválasztani az Ön számára optimális megoldást. 

Az AppSource-ban böngészheti és megkeresheti az egész szervezettel, valamint a terjesztési vagy biztonsági csoportokkal megosztott tartalomcsomagokat, és aztán [hozzáadhatja őket saját Office 365-csoportjaihoz](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Ha nem tagja egy adott csoportnak, akkor nem láthatja a csoporttal megosztott tartalomcsomagokat. A csoport minden tagja csak olvasási hozzáféréssel rendelkezik a tartalomcsomaghoz, a jelentésekhez, a munkafüzetekhez és az irányítópultokhoz (hacsak az adatforrás nem SQL Server Analysis Services (SSAS) típusú, mert ez esetben az adatforrásra vonatkozó jogosultságok érvényesülnek).

Az irányítópultok, a jelentések és az Excel-munkafüzetek írásvédettek, de az irányítópultokat és a jelentéseket másolhatja, és kiindulási pontként használhatja személyre szabott tartalomcsomagok létrehozásában.

> [!NOTE]
> A szervezeti tartalomcsomagok csak akkor érhetők el, ha Ön és kollégái is rendelkeznek a [Power BI Próval](service-free-vs-pro.md).
> 
> 

## <a name="what-is-appsource"></a>Mi az az *AppSource*?
A közzétett szervezeti tartalomcsomagok az AppSource-ban jelennek meg.  Ebben a központi tárházban a tagok könnyen böngészhetik és megkereshetik a nekik szánt irányítópultokat, jelentéseket és adatkészleteket.  

* Az AppSource-ot a **Lekérdezés** > **Saját szervezet** > **Beolvasás** elemre kattintva nyithatja meg.

További információ [a szervezeti tartalomcsomagok kereséséről és megnyitásáról](service-organizational-content-pack-find-and-open.md).

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>A szervezeti tartalomcsomagok életciklusa
Minden Power BI Pro-felhasználó létrehozhat, közzétehet és elérhet szervezeti tartalomcsomagokat. Azonban a munkafüzet és az adatkészlet módosítására, a frissítés ütemezésére és a törlésre csak a tartalomcsomag létrehozója jogosult.

Az életciklus nagyjából így alakul:

1. Szabolcs létrehozza a tartalomcsomagot a Power BI Próban, és közzéteszi a Marketing terjesztési csoportban. A frissítési beállítások az adatkészlettel öröklődnek, és csak Szabolcs módosíthatja őket.
   
   > [!NOTE]
   > Ha Szabolcs olyan [Power BI-alkalmazás-munkaterületen](service-create-distribute-apps.md) hozza létre a tartalomcsomagot, amelynek tagja, akkor mások átvehetik a csomag tulajdonjogát, ha Szabolcs esetleg elhagyja a munkaterületet.
   > 
   > 
2. Szabolcs e-mailben értesíti a terjesztési csoport tagjait az új tartalomcsomagról.
3. A Power BI Próban Borbála, a Marketing terjesztési csoport tagja rátalál erre a tartalomcsomagra, és kapcsolódik hozzá az AppSource-ban. Ezzel egy csak olvasható példányhoz jut hozzá.  Tisztában van vele, hogy a csomag csak olvasható, mert a navigációs panelen a megosztást jelző ikon látható az irányítópult neve és a jelentés neve mellett. És amikor kiválasztja az irányítópultot, egy lakatot ábrázoló ikon jelzi neki, hogy egy tartalomcsomag irányítópultjával van dolga. 
4. Tegyük fel, hogy testre szabja a csomagot. Így már saját példánya van az irányítópultból és a jelentésekből. A munkája nem érinti a forrást, sem az eredeti tartalomcsomagot, és a terjesztési csoport többi tagját sem. Az irányítópult és a jelentés saját példányán dolgozik.
5. Szabolcs módosítja az irányítópultot, és amikor elkészült, közzéteszi a tartalomcsomag új verzióját.
   
   * Géza, a terjesztési csoport egy másik tagja nem szabta testre az eredeti tartalomcsomagot. A módosítások így automatikusan érvénybe lépnek a tartalomcsomag ezen verziójában.  
   * Borbála azonban testre szabta a tartalomcsomagot. Értesítést kap az új verzióról.  Ha megnyitja az AppSource-ot, akkor letöltheti a frissített tartalomcsomagot, de a saját verziója is megmarad. Ezzel már két verziója van: a személyre szabott és a frissített tartalomcsomag.
6. Tegyük fel, hogy Szabolcs módosítja a biztonsági beállításokat. Géza és Borbála ettől kezdve nem fér hozzá a tartalomhoz. Vagy feltételezzük azt, hogy törlik őket a Marketing terjesztési csoportból.
   
   * Géza nem szabta testre az eredeti tartalomcsomagot, így a tartalom automatikusan törlődik. 
   * Borbála azonban testre szabta a tartalomcsomagot. Amikor legközelebb megnyitja az irányítópultot, már egyetlen csempe sem jelenik meg az eredeti tartalomcsomagból, de a más (számára még most is elérhető) jelentésekből általa rögzített csempék továbbra is láthatók. Az adatkészlet és a kapcsolódó jelentések már nem érhetők el (és nem jelennek meg a bal oldali navigációs panelen).
7. Vagy például Szabolcs törli a tartalomcsomagot.
   
   * Géza nem szabta testre az eredeti tartalomcsomagot, így a tartalom automatikusan törlődik. 
   * Borbála azonban testre szabta a tartalomcsomagot. Amikor legközelebb megnyitja az irányítópultot, már egyetlen csempe sem jelenik meg az eredeti tartalomcsomagból, de a más jelentésekből általa rögzített csempék továbbra is láthatók. Az adatkészlet és a kapcsolódó jelentések már nem érhetők el (és nem jelennek meg a bal oldali navigációs panelen).

## <a name="data-security"></a>Adatbiztonság
A terjesztési csoport minden tagja ugyanolyan jogosultságokkal rendelkezik az adatokra vonatkozóan, mint a tartalomcsomag létrehozója. Ez alól csak a helyszíni táblázatos SQL Server Analysis Services-adatkészletek (SSAS-adatkészletek) adatkészletek képeznek kivételt. Mivel a jelentések és az irányítópultok élőben csatlakoznak a helyszíni SSAS-modellhez, ezért a terjesztési csoport egyes tagjainak hitelesítő adatai határozzák meg, hogy mely adatokhoz fér hozzá az adott felhasználó.

## <a name="next-steps"></a>Következő lépések
* [Szervezeti tartalomcsomag létrehozása és közzététele](service-organizational-content-pack-create-and-publish.md)
* [Alkalmazások létrehozása és terjesztése a Power BI-ban](service-create-distribute-apps.md) 
* [Power BI – Alapfogalmak](service-basic-concepts.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

