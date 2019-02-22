---
title: További vásárlásra lehet szükség – útmutatás Power BI-vizualizációkhoz
description: Megtudhatja, hogyan teheti közzé egyéni vizualizációit az AppSource-ban, amelyeket aztán mások is felfedezhetnek és használhatnak vásárlással.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 4cbd17a08a8cb7c7253f60f29a19341598c9800f
ms.sourcegitcommit: 654fae0af739bd599e029d692f142faeba0a502f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56426539"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Útmutató további vásárlásos Power BI-vizualizációkhoz

Mostanáig a **piactér (AppSource)** csak ingyenes Power BI-vizualizációkat fogadott el. Ez a szabályzat módosul, így a „További vásárlásra lehet szükség” árcédulával rendelkező vizualizációk is beküldhetők az **AppSource-hoz**. A További vásárlásra lehet szükség típusú vizualizációk az Office áruházában található, alkalmazáson belüli vásárlást (IAP-t) lehetővé tevő bővítményekhez hasonlóak. Ilyen vizualizációkat a fejlesztők is beküldhetnek minősítésre, miután az **AppSource** csapata jóváhagyta azokat, illetve meggyőződtek arról, hogy megfelelnek a minősítési feltételeknek (amelyeket a [minősített egyéni vizualizációkról szóló cikk](../power-bi-custom-visuals-certified.md) ismertet).

> [!Note]
> A vizualizáció minősítéséhez az nem kapcsolódhat külső szolgáltatásokhoz és erőforrásokhoz.

> [!Note]
> Az összes szabad vizualizáció megőrizheti ugyanazokat a korábban kínált ingyenes funkciókat. A régi ingyenes funkciók mellett felvehet választható, speciális fizetett funkciókat. Javasoljuk, hogy a speciális funkciókkal rendelkező IAP-vizualizációkat új vizualizációkként vegye fel, és ne a régi ingyeneseket frissítse.


## <a name="whats-changing-in-the-submission-process"></a>Mi változik a beküldési folyamatban?

A fejlesztők az Értékesítői információ-központról tölthetik fel az IAP-vizualizációikat az AppSource-ba, ahogyan az ingyenes vizualizációkkal is tették. A fejlesztőknek az alábbi jegyzetet kell feltüntetniük az irányítópult értékesítői megjegyzései között, így jelezve, hogy a vizualizáció IAP-funkciókkal rendelkezik: „Alkalmazáson belüli vásárlást tartalmazó vizualizáció”. A fejlesztőknek emellett licenckulcsot vagy tokent kell szolgáltatniuk, amellyel az ellenőrző csapat ellenőrizheti az IAP-funkciókat. A vizualizáció ellenőrzése és jóváhagyása után az AppSource jelzi az IAP-vizualizáció díjszabási beállításainál, hogy ahhoz további vásárlásra lehet szükség.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>Mik az IAP-funkciókkal rendelkező Power BI-vizualizációk?

Az IAP-vizualizációk ingyenesek, ingyenes funkciókkal, azonban további speciális funkciókat támogatnak, amelyek használatához külön díjszabás kapcsolódhat. A fejlesztőknek értesítenie kell a felhasználókat a vizualizáció leírásában arról, hogy mely funkciókhoz van szükség további vásárlásra. A Microsoft jelenleg nem nyújt natív alkalmazásprogramozási felületeket (API-kat) az alkalmazásokon és bővítményeken belüli vásárlások támogatásához. A fejlesztők bármilyen külső fizetési rendszert használhatnak az ilyen vásárlásokhoz. Tekintse meg az áruházzal kapcsolatos [szabályzatunkat](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).

> [!NOTE]
> Az ingyenes funkciókkal a vízjelek nem használhatóak. A fejlesztők előugró ablakot vagy vízjelet jeleníthetnek meg, ha a speciális, fizetős funkciókat érvényes licenc nélkül használják.  

## <a name="logo-guidelines"></a>Embléma-irányelvek

Ez a szakasz az emblémák és logotipiák vizualizációkhoz való hozzáadásának részleteit ismerteti.

> [!NOTE]
> Az emblémák csak Szerkesztő módban használhatók. Az emblémák nem jelennek meg Megtekintési módban.

![definíciók](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![things-to-keep](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![things-to](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![size-and-format ](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![margins-and](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![edit-mode](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Ajánlott eljárások

### <a name="visual-landing-page"></a>Vizualizáció kezdőlapja

A kezdőlapon tudathatja a felhasználókkal, hogy hogyan használhatják a vizualizációt, és hol vásárolhatnak licencet. Ne használjon automatikusan induló videókat. Csak olyan anyagot adjon hozzá, amely hozzájárul a felhasználói élményhez, például licencvásárlással vagy az IAP-funkció használatával kapcsolatos információk vagy hivatkozások.

### <a name="license-key-and-token"></a>Licenckulcs és token

A felhasználói élmény javítása érdekében helyezzen el licenckulccsal vagy tokenekkel kapcsolatos mezőket a formázási panel tetején, így a felhasználók könnyebben megtalálhatják őket.

## <a name="faq"></a>Gyakori kérdések

További információkért és válaszokért látogasson el a [Gyakori kérdések a vizualizációkon belüli további vásárlásokról](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases) weblapra.

## <a name="next-steps"></a>Következő lépések

Megtudhatja, hogyan teheti közzé egyéni vizualizációit az [AppSource-ban](office-store.md), amelyeket aztán mások is felfedezhetnek és használhatnak.
