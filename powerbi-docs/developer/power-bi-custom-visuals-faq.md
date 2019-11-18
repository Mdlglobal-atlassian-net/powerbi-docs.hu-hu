---
title: Gyakori kérdések a Power BI-vizualizációkról
description: Az alábbiakban a Power BI-vizualizációkkal kapcsolatos gyakori kérdések és válaszok listáját tekintheti át
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 0b5677e7f3acab464f8d9e4c293ed1df9d0bdd0f
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74102157"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>Gyakori kérdések a Power BI-vizualizációkról

## <a name="organizational-visuals"></a>Szervezeti vizualizációk

A felügyeleti portál segítségével kezelheti a szervezetéhez tartozó Power BI-vizualizációkat.

### <a name="how-can-the-admin-manage-the-organizational-power-bi-visuals"></a>Hogyan felügyelheti a rendszergazda a szervezeti Power BI-vizualizációkat?

A felügyeleti portál „Szervezeti vizualizációk” lapján a rendszergazda megtekintheti és [felügyelheti a vállalat összes szervezeti Power BI-vizualizációját](../service-admin-portal.md#organizational-visuals): hozzáadhat, letilthat, engedélyezhet és törölhet.
Most már nem kell ezeket a vizualizációkat e-mailek vagy megosztott mappák segítségével megosztani. A szervezeti adattárban való üzembe helyezésük után a szervezet felhasználói könnyedén megtalálhatják azokat, és közvetlenül a Power BI Desktopból vagy szolgáltatásból importálhatják a szervezeti vizualizációkat a jelentéseikbe. A szervezeti vizualizációk a beépített áruházból érhetők el (az asztali verzióban és a szolgáltatásban is), a *SAJÁT SZERVEZET* lapon. Miután a rendszergazda feltölti egy egyéni szervezeti vizualizáció új verzióját, a szervezet összes tagja megkapja ugyanazt a frissített verziót. A jelentések létrehozóinak nem kell törölniük a vizualizációt a jelentésükből a vizualizáció új verziójának beszerzéséhez, és a rendszer automatikusan frissíti az adott vizualizációt használó összes jelentést! A frissítési mechanizmus hasonló a piactéren beszerzett vizualizációkéhoz.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Ha egy rendszergazda feltölt egy egyéni vizualizációt a nyilvános piactérről a szervezet áruházába, az automatikusan frissül, ha a készítője frissíti a nyilvános piactéren a vizualizációt?

Nem, a nyilvános piactérről nem érkezik automatikusan a frissítés.
A szervezeti vizualizációk verziójának frissítése a rendszergazda feladata.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Van lehetőség a szervezeti áruház letiltására?

Nem, a felhasználók számára mindig megjelenik a „SAJÁT SZERVEZET” lap a Power BI Desktopban és a szolgáltatásban. A rendszergazda letilthatja vagy törölheti az összes szervezeti vizualizációt a felügyeleti portálról, így a szervezeti áruház üres lesz.
  
### <a name="if-the-administrator-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-visuals"></a>Ha a rendszergazda letiltja az egyéni Power BI-vizualizációkat a felügyeleti portálon (Bérlői beállítások), a felhasználók attól még hozzáféréssel rendelkeznek a szervezeti vizualizációkhoz?

Igen. Az, hogy a rendszergazda letiltja a vizualizációkat a felügyeleti portálon, nincs hatással a szervezeti áruházra. Bizonyos szervezetek letiltják a Power BI-vizualizációkat, és csak olyan, válogatott vizualizációk használatát engedélyezik, amelyeket a Power BI-rendszergazda importált és töltött fel a szervezeti áruházba. A Power BI-vizualizációnak a felügyeleti portálon történő letiltása nem lesz érvényesítve a Power BI Desktopban. Az asztali verzió felhasználói a jelentéseikben továbbra is hozzáadhatnak és használhatnak a nyilvános piactérről származó Power BI-vizualizációkat. Ezek a nyilvános Power BI-vizualizációk azonban nem jelennek meg a Power BI szolgáltatásban való közzététel után, és kiváltják a megfelelő hibaüzenetet. A Power BI szolgáltatás használatakor nem importálhatók Power BI-vizualizációk a nyilvános piactérről. Csak a szervezeti áruházból származó vizualizációk importálhatók, mert a Power BI-vizualizációk a felügyeleti portálon megadott beállítása érvényesítve lesz a Power BI szolgáltatásban.

### <a name="why-does-the-organizational-store-and-organizational-visuals-make-a-great-enterprise-solution"></a>Miért számít kiváló nagyvállalati megoldásnak a szervezeti áruház és a szervezeti vizualizációk használata?

* Mindenki a vizualizáció azonos verzióját kapja, amely felett a Power BI-rendszergazda gyakorol irányítást. Ha a rendszergazda frissíti a vizualizáció verzióját a felügyeleti portálon, a szervezet összes felhasználója automatikusan megkapja a frissített verziót.

* Többé nem kell megosztani e-mailben vagy megosztott mappákban a vizualizációs fájlokat. Az összes bejelentkezett felhasználó látja ezt a központi helyet.

* Biztonságos, és számos támogatási lehetőséget biztosít. A szervezeti vizualizációk új verziói automatikusan frissülnek minden jelentésben, akárcsak a piactérről beszerzett vizualizációk.

* A szervezet szervezeti vizualizációkat használó felhasználóinak be kell jelentkezniük, hogy lássák és használhassák a szervezet számára biztonsági tényezőnek számító szervezeti vizualizációkat.

* A rendszergazdák szabályozhatják, hogy mely Power BI-vizualizációk legyenek elérhetők a szervezetben.

* A rendszergazdák a felügyeleti portálról engedélyezhetik/letilthatják a vizualizációkat tesztelési célból. A biztonsági szabályok jobban kikényszeríthetők, hiszen a vizualizációkhoz csak a szervezet tagjai férhetnek hozzá.

## <a name="certified-power-bi-visuals"></a>Minősített Power BI-vizualizációk

### <a name="what-are-certified-power-bi-visuals"></a>Melyek a minősített Power BI-vizualizációk?

A minősített Power BI-vizualizációk azok a [piactéren](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) lévő vizualizációk, amelyek megfelelnek [bizonyos](power-bi-custom-visuals-certified.md), a Power BI csapata által megadott kódolási és tesztelési előírásoknak.  A végrehajtott tesztek célja annak ellenőrzése, hogy a vizualizáció nem kapcsolódik-e külső szolgáltatásokhoz vagy erőforrásokhoz. A külső felek Power BI-vizualizációinak azonban nem a Microsoft a készítője, ezért azt javasoljuk ügyfeleinknek, hogy közvetlenül a készítővel kapcsolatba lépve ellenőrizzék az ilyen vizualizációk működését.

### <a name="what-tests-are-done-during-the-certification-process"></a>Milyen teszteket végeznek a minősítési folyamat során?

A minősítési folyamat tesztjei egyebek mellett a következők: Kódellenőrzés, statikus kódelemzés, adatszivárgás, adatbizonytalanság, behatolásvizsgálat, XSS-hozzáférési teszt, rosszindulatú adatok injektálása, bemenő adatok érvényesítése és funkcionális tesztelés.
 
### <a name="do-you-certify-visuals-every-submission"></a>Minden beküldés alkalmával minősítik a vizualizációkat?

Igen. Valahányszor egy minősített vizualizáció új verziója be van küldve a Marketplace-re, a vizualizáció frissítése ugyanezeken a minősítési ellenőrzéseken megy keresztül.

Megjegyzés fejlesztők számára: minősített vizualizáció verziófrissítésének benyújtásakor nem szükséges külön e-mailt küldeni, mint az [első minősítéskérés](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification) alkalmával. A verziófrissítés minősítése automatikusan megtörténik, és a visszautasítást eredményező szabálysértésekről a javításhoz szükséges teendőket is elmagyarázó e-mailt küldünk. 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>Lehetséges, hogy egy minősített vizualizáció egy új frissítés után már nem lesz minősített?

Nem, ez nem lehetséges. Egy vizualizáció minősítését nem szüntetheti meg egy új frissítés. A frissítés lesz elutasítva.
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>Meg kell osztanom a kódomat egy nyilvános adattárban, ha minősítési eljárásra adom be?

Nem, a kódját nem kell nyilvánosan megosztania. Nekünk viszont olvasási jogosultságot kell adnia, hogy ellenőrizhessük a vizualizáció kódját. Például egy privát adattárban a GitHubon.
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>[Közzé kell tennünk](https://docs.microsoft.com/power-bi/developer/office-store) a vizualizációt a [Marketplace-en](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) a minősítéshez?

Igen. A vizualizációnak a Marketplace-en való előzetes közzététele a minősítés kötelező feltétele.
Egy egyéni vizualizáció minősítéséhez annak a mi kiszolgálóinkon kell lennie. Privát vizualizációkat nem tudunk minősíteni.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Mennyi időt vesz igénybe a vizualizációm minősítése?

Frissített verzió esetén 3 hétig tarthat. Újonnan (első minősítésre) benyújtott vizualizációknál 4 hetet is igénybe vehet. 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>Biztosítja a minősítési eljárás, hogy ne léphessen fel adatszivárgás?

A végrehajtott tesztek célja annak ellenőrzése, hogy a vizualizáció nem kapcsolódik-e külső szolgáltatásokhoz vagy erőforrásokhoz. A külső felek Power BI-vizualizációinak azonban nem a Microsoft a készítője, ezért azt javasoljuk ügyfeleinknek, hogy közvetlenül a készítővel kapcsolatba lépve ellenőrizzék az ilyen vizualizációk működését.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Biztonságos a nem minősített Power BI-vizualizációk használata?

A nem minősített Power BI-vizualizációk nem feltétlenül jelentenek nem biztonságos vizualizációkat.
Egyes vizualizációk azért nincsenek minősítve, mert nem felelnek meg egy vagy több [minősítésbeli követelménynek](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Például egy külső szolgáltatáshoz (például egy térképvizualizációhoz) vagy egy kereskedelmi könyvtárakat használó vizualizációhoz csatlakozik.
 
## <a name="visuals-with-additional-purchases"></a>Vizualizációkon belüli további vásárlás

### <a name="what-is-a-visual-with-additional-purchases"></a>Mi a vizualizációkon belüli további vásárlás?

A további vásárlásokat tartalmazó vizualizációk a piactéren lévő, alkalmazáson belüli vásárlást (IAP) lehetővé tevő bővítményekhez hasonlítanak. Az ilyen bővítmények áránál fel van tüntetve, hogy **további vásárlásra lehet szükség**.

A Power BI IAP-vizualizációi ingyenesen letölthetők – a felhasználóknak nem kell fizetniük, ha letöltik ezeket a vizualizációkat a piactérről. Az IAP-vizualizációk speciális funkciók alkalmazáson belüli megvásárlásának lehetőségét kínálják fel.  

### <a name="whats-the-benefit-to-developers"></a>Milyen előnyökkel jár ez a fejlesztőkre nézve?

A Power BI AppSource-beli egyéni IAP-vizualizációira naponta sok látogató találhat rá, értékes forgalmat hozva létre, így a Power BI IAP-vizualizációi és Ön mint azok fejlesztője is szélesebb körben válnak ismertté.

Ha ezeket a vizualizációkat eddig saját webhelyén keresztül kezelte, most beküldheti azokat az AppSource-ba. Az IAP-vizualizációk így könnyebben felfedezhetővé és láthatóbbá válnak a Power BI-közösség számára.

Az AppSource-beli vizualizációk egyik előnye az egyéni IAP-vizualizációt használó ügyfelek közvetlen visszajelzési lehetősége az áruház véleményezési és értékelési rendszerén keresztül.  

Miután az AppSource bíráló csapata jóváhagyta az IAP-vizualizációt, azt minősítésre is benyújthatja. Ez az eljárás nem kötelező.  

A Power BI IAP-vizualizációja a minősítést követően exportálható PowerPointba, és megjeleníthető az egyes jelentésoldalakra feliratkozó felhasználóknak küldött e-mailekben is. A piactérre most beküldött IAP-vizualizációk tehát minősíthetők, és további funkciókat is támogathatnak.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Mindenképpen minősíteni kell az IAP-vizualizációkat?

A minősítési folyamat választható. Ahogyan az ingyenes vizualizációk esetében, a Power BI IAP-vizualizációi minősítéséről is a fejlesztő dönt.

### <a name="what-is-changing-in-the-submission-process"></a>Mi változik a beküldés folyamatában?

A Power BI IAP-vizualizációi piactérre küldésének folyamata ugyanaz, mint az ingyenes vizualizációké. Ez az értékesítő irányítópulton keresztül történik.  A beküldési folyamat egyetlen eltérése az, hogy az értékesítő irányítópulton a következő szöveget kell elhelyezni a fejlesztői megjegyzésekben: „Alkalmazáson belüli vásárlást lehetővé tevő vizualizáció”. Amennyiben a fizetős/speciális funkciók érvényesítéséhez ez szükséges, licenckulcsot/jogkivonatot is meg kell adnia.  

Az értékesítő irányítópulton nem lesz új, *alkalmazáson belüli vásárlást lehetővé tevő ingyenes* lehetőség. IAP-vizualizációt *ingyenesként* kell beküldenie.

Ezen felül az áruházbeli hosszú leírásban is tájékoztassa a felhasználókat arról, hogy mely funkciók ingyenesek, és melyek működése igényel további vásárlást.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>Mi a teendőm az egyéni IAP-vizualizációm beküldése előtt?

Ha egyéni IAP-vizualizáción dolgozik, vagy már rendelkezik eggyel, akkor ellenőrizze, hogy az mindenben eleget tesz-e az irányelveknek.  

Ha az egyéni vizualizáció logót tartalmaz, akkor ellenőrizze, hogy az megfelel-e a logóra vonatkozó irányelveknek (szín, elhelyezés, méret, művelet indítása).

Az irányelvek az ajánlott eljárásokra vonatkozó jegyzeteket is tartalmaznak.  
> [!Note]
> Az összes szabad vizualizáció megőrizheti ugyanazokat a korábban kínált ingyenes funkciókat. A régi ingyenes funkciók mellett felvehet választható, speciális fizetett funkciókat. Javasoljuk, hogy a speciális funkciókkal rendelkező IAP-vizualizációkat új vizualizációkként vegye fel, és ne a régi ingyeneseket frissítse.

### <a name="can-i-get-my-iap-custom-visual-certified"></a>Minősíttethetem az egyéni IAP-vizualizációmat?

Igen, ugyanúgy, mint az ingyenes vizualizációkat.  Miután az AppSource csapata jóváhagyta az Ön egyéni IAP-vizualizációját, benyújthatja azt minősítési eljárásra.

Vizualizációjának a minősítéshez eleget kell tennie a minősítési követelményeknek, például nem kapcsolódhat külső szolgáltatáshoz a licenc ellenőrzésére.

Mint tudja, a minősítés választható eljárás. Ön döntheti el, hogy minősíttetni kívánja-e IAP-vizualizációját.

## <a name="additional-questions"></a>További kérdések

### <a name="how-to-get-support"></a>Hogyan kérhetek segítséget?

Ha bármilyen kérdése, megjegyzése vagy problémája van, vegye fel a kapcsolatot a Power BI-vizualizációk csapatával a  *pbicvsupport@microsoft.com*   címen.  

## <a name="next-steps"></a>Következő lépések

Bővebben a [Power BI-vizualizációk hibáinak elhárítását](power-bi-custom-visuals-troubleshoot.md) ismertető cikkből tájékozódhat.