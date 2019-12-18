---
title: Útmutató Power BI-vizualizációkhoz
description: Megtudhatja, hogyan teheti közzé egyéni vizualizációit a Microsoft AppSource-on, amelyeket aztán mások is megtalálhatnak és megvásárolhatnak.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 07/16/2019
ms.openlocfilehash: 6bf7610a010a72248a3d2fdd96718eea513a68da
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000089"
---
# <a name="guidelines-for-power-bi-visuals"></a>Útmutató Power BI-vizualizációkhoz
Mielőtt [közzétenné](https://docs.microsoft.com/power-bi/developer/office-store) a Power BI-vizualizációt a Microsoft AppSource-on, hogy azt mások is felfedezhessék és használhassák, ügyeljen rá, hogy az útmutatók használatával magas színvonalú felhasználói élményt alakítson ki.

## <a name="power-bi-visuals-with-additional-purchases"></a>Power BI-vizualizációkon belüli további vásárlás

A Piactéren (Microsoft AppSource) ingyenes Power BI-vizualizációkat is közzétehet. A Microsoft AppSource-on olyan Power BI-vizualizációkat is közzétehet, amelyek egy „További vásárlásra lehet szükség” címkével vannak megjelölve. A „További vásárlásra lehet szükség” típusú Power BI-vizualizációk az Office áruházában található, alkalmazáson belüli vásárlást (IAP-t) lehetővé tevő bővítményekhez hasonlóak. 

Az ingyenes Power BI-vizualizációkhoz hasonlóan az IAP Power BI-vizualizációhoz is lehet minősítést szerezni. Mielőtt elküldi a IAP Power BI-vizualizációt a minősítéshez, ellenőrizze, hogy az megfelel-e a [minősítési követelményeinek](../power-bi-custom-visuals-certified.md). 

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>Mik az IAP-funkciókkal rendelkező Power BI-vizualizációk?

A Power BI IAP-vizualizációk *ingyenes funkciókat* kínáló, *ingyenes* vizualizációk. Ezen kívül speciális funkciókkal is rendelkeznek, amelyek használatához további díjat kell fizetni. A fejlesztőknek a Power BI-vizualizáció leírásában értesíteniük kell a felhasználókat arról, hogy mely funkciók használatához van szükség további vásárlásra. A Microsoft jelenleg nem nyújt natív API-kat az alkalmazások és bővítmények vásárlásának támogatásához.

A fejlesztők bármilyen külső fizetési rendszert használhatnak az ilyen vásárlásokhoz. További információt [üzletszabályzatunkban](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) talál.


>[!IMPORTANT]  
> Ha a Power BI-vizualizációt az ingyenesről „További vásárlásra lehet szükség” szintűre frissíti, a felhasználók ugyanazon szintű funkciókkal fognak rendelkezni, mint a frissítés előtt. A meglévő ingyenes funkciók mellett felvehet választható, speciális fizetett funkciókat.

### <a name="watermarks"></a>Vízjelek

Használhat vízjeleket, hogy az ügyfelek az IAP speciális funkcióit továbbra is használhassák fizetés nélkül. 

A vízjelekkel be lehet mutatni a Power BI-vizualizáció teljes funkcionalitását a vásárlás előtt. 

* A vízjelek csak az érvényes licenc nélkül használt, fizetős funkciókkal használhatók.
* A vízjelek nem használhatók *ingyenes* árcímkézésű Power BI-vizualizációkban.
* Az IAP-vizualizációkban nem használhatóak a vízjelek, ha a felhasználó ingyenes szolgáltatásokat használ. 

### <a name="pop-up-window"></a>Előugró ablak

Az előugró ablakban tájékoztatást adhat arról, hogyan vásárolható meg a licenc, ha a Power BI IAP-vizualizációját érvénytelen (vagy lejárt) licenccel használják.

### <a name="submission-process"></a>Beküldési folyamat

Kövesse a [beküldési folyamatot](office-store.md#submitting-to-appsource), majd lépjen a *Termékbeállítás* lapra, és jelölje be az *A termékhez szolgáltatás megvásárlása szükséges* jelölőnégyzetet.

A Power BI-vizualizáció ellenőrzése és jóváhagyása után a Microsoft AppSource jelzi a Power BI IAP-vizualizáció díjszabási beállításainál, hogy ahhoz további vásárlásra lehet szükség.

>[!NOTE]
>Ha a Power BI-vizualizációt már elküldte az [Értékesítői irányítópult](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) használatával, és hozzá szeretne adni egy IAP-funkciót, az Értékesítői irányítópult megjegyzésénél be kell írnia a „Vizualizáció alkalmazáson belüli vásárlással” szöveget. Emellett licenckulcsot vagy tokent kell szolgáltatnia, amellyel az ellenőrző csapat ellenőrizheti az IAP-funkciókat.

## <a name="context-menu"></a>Helyi menü
A helyi menü egy jobb gombbal történő kattintással előhozható menü, amely akkor jelenik meg, amikor a felhasználó a vizualizáció fölé viszi a kurzort.
A Power BI minden vizualizációnál engedélyezni kell a helyi menüt, hogy egységes felhasználói élményt nyújthasson. [Ebben a cikkben](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md) talál információt arról, hogyan adható hozzá helyi menü.

## <a name="commercial-logo"></a>Üzleti embléma
Ez a szakasz az üzleti emblémák Power BI-vizualizációkhoz való hozzáadásának részleteit ismerteti. Az üzleti emblémák nem kötelezőek. Ha szerepelnek, akkor követniük kell ezeket az irányelveket.

> [!NOTE]
> * Az ebben a cikkben szereplő „üzleti embléma” szó bármely kereskedelmi vállalati ikonra vonatkozik az alábbi képeken szereplő leírásoknak megfelelően.
> * Ebben a cikkben a Microsoft üzleti emblémáját csak példaként használjuk. A Power BI-vizualizációnál használja saját üzleti emblémáját.

> [!IMPORTANT]
> Az üzleti emblémák *csak Szerkesztési módban* használhatók. Az üzleti emblémák *nem* jelennek meg Megtekintési módban.

### <a name="commercial-logo-type"></a>Üzleti embléma típusa

Az üzleti emblémáknak háromféle típusa létezik:
* **Embléma** – Az embléma két elemből áll: egy ikonból és egy névből.

    ![Microsoft-embléma](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Szimbólum** – Egy szöveg nélküli grafikus elem.

    ![A Microsoft szimbóluma](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Emblémaszöveg** – Ikon nélküli embléma, amely csak szövegből áll.

    ![A Microsoft szimbóluma](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Az üzleti embléma színe

Üzleti embléma használatakor az embléma színének szürkének kell lennie (hexadecimális kódja: #C8C8C8). Az üzleti emblémához ne adjon hozzá effektusokat, például színátmenetet.

* **Embléma**

    ![A Microsoft szimbóluma](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Szimbólum** – Egy szöveg nélküli grafikus elem.

    ![A Microsoft szimbóluma](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Emblémaszöveg** – Ikon nélküli embléma, amely csak szövegből áll.

    ![A Microsoft szimbóluma](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Ha a Power BI-vizualizációja grafikát is tartalmaz, érdemes lehet fehér hátteret hozzáadni az emblémához 10px méretű margókkal.
> * Lehet, hogy érdemes lehet árnyékolást (30%-os fekete átlátszatlansággal) alkalmazni az emblémára.

### <a name="commercial-logo-size"></a>Az üzleti embléma mérete

A Power BI-vizualizációkhoz két üzleti embléma szükséges, egy a nagy méretű csempékhez, egy pedig a kis méretű csempékhez. Helyezze az emblémát a határolókeret jobb felső vagy alsó sarkába 4 px méretű margóval.

Az alábbi táblázat a Power BI-vizualizációk méretével kapcsolatos szempontokat ismerteti.

|  |Kis méretű Power BI-vizualizáció  |Nagy méretű Power BI-vizualizáció  |
|---------|---------|---------|
|*Embléma szélessége*    |Legfeljebb 240 px         |Nagyobb mint 240 px         |
|*Embléma magassága*     |Legfeljebb 160 px         |Nagyobb mint 160 px         |
|*Határolókeret mérete*     |40 x 15 px         |101 x 30 px         |
|*Példa üzleti emblémára*     |![A Microsoft szimbóluma](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Microsoft-embléma](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Példa határolókeretre*    |![példa kis emblémára](media/guidelines-powerbi-visuals/small-logo-box.png)         |![példa nagy emblémára](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Üzleti embléma viselkedése

Az üzleti emblémák csak Szerkesztési módban használhatók. Ha rákattintanak, az üzleti embléma csak a következő funkciókat veheti fel:

* Az üzleti emblémára való kattintás átirányít az Ön webhelyére.

* Az üzleti emblémára kattintás megnyit egy felugró ablakot, ahol további információk láthatók. Az előugró ablakot két szakaszra kell osztani:
    * Egy marketing célú terület, amely tartalmazhatja az üzleti emblémát, a vizualizációt és a piaci értékeléseket.
    * Egy információs terület, amely információkat és hivatkozásokat tartalmazhat.    


### <a name="things-to-avoid"></a>Fontos megfontolások

* Az üzleti emblémák nem jelenhetnek meg megtekintési módban.

* Az animált üzleti embléma legfeljebb öt másodpercig jelenítheti meg az animációt.

* Ha a Power BI-vizualizáció információs ikonokat (i) tartalmaz olvasási módban, akkor a fentiekben leírtak szerint meg kell felelniük az üzleti embléma színének, méretének és helyének.

* Ne használjon színes vagy fekete emblémát. Üzleti emblémának szürkének kell lennie (hexadecimális kódja: #C8C8C8).

    ![Nem engedélyezett színes embléma](media/guidelines-powerbi-visuals/no-color-logo.png) ![Nem engedélyezett fekete embléma](media/guidelines-powerbi-visuals/black-logo.png)

* Effektusokkal, például színátmenettel vagy erős árnyékkal rendelkező üzleti embléma.

    ![Nem engedélyezett emblémastílus](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Ajánlott eljárások

Power BI-vizualizációk közzétételekor vegye figyelembe az alábbi javaslatokat, hogy a felhasználóknak nagyszerű élményt nyújthasson.

### <a name="visual-landing-page"></a>Vizualizáció kezdőlapja

A kezdőlapon tudathatja a felhasználókkal, hogy hogyan használhatják a Power BI-vizualizációt, és hol vásárolhatnak licencet. Ne használjon automatikusan induló videókat. Csak olyan anyagot adjon hozzá, amely hozzájárul a felhasználói élményhez, például licencvásárlással vagy az IAP-funkció használatával kapcsolatos információk vagy hivatkozások.

### <a name="license-key-and-token"></a>Licenckulcs és token

Az egyszerűbb használat érdekében a licenckulccsal vagy tokenekkel kapcsolatos mezőket a formázási panel tetején helyezze el.

## <a name="faq"></a>Gyakori kérdések

A Power BI-vizualizációkkal kapcsolatban a [Gyakori kérdések a Power BI-vizualizációkon belüli további vásárlásokról](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases) weblapon talál további információt.

## <a name="next-steps"></a>Következő lépések

Megtudhatja, hogyan teheti közzé Power BI-vizualizációit a [Microsoft AppSource-on](office-store.md), amelyeket aztán mások is megtalálhatnak és használhatnak.