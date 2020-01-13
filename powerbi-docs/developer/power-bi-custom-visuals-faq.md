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
ms.openlocfilehash: 01fe7056c844a9eed96356e478cc23d5593809bd
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75759060"
---
# <a name="power-bi-visuals-faq"></a>Power BI-vizualizációk – GYIK

## <a name="organizational-power-bi-visuals"></a>Vállalati vizualizációk a Power BI-ban

A felügyeleti portál segítségével kezelheti a szervezetéhez tartozó Power BI-vizualizációkat.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Hogyan felügyelheti a rendszergazda a szervezeti Power BI-vizualizációkat?

A felügyeleti portál *Szervezeti vizualizációk* lapján a rendszergazda megtekintheti és [felügyelheti a vállalat összes szervezeti Power BI-vizualizációját](../service-admin-portal.md#organizational-visuals). Többek között hozzáadhat, letilthat, engedélyezhet és törölhet is Power BI-vizualizációkat.

A szervezet felhasználói könnyedén megtalálhatják a Power BI-vizualizációkat, és közvetlenül a Power BI Desktopból vagy szolgáltatásból importálhatják azokat a jelentéseikbe.

Miután a rendszergazda feltölti egy szervezeti Power BI-vizualizáció új verzióját, a szervezet összes tagja megkapja ugyanazt a frissített verziót. A frissített Power BI-vizualizációkat használó jelentések automatikusan frissülnek.

A szervezeti felhasználók a szervezeti Power BI-vizualizációkat a beépített Power BI Desktop- és Power BI szolgáltatási szervezeti tárolóban találhatják meg a *SAJÁT SZERVEZET* panelen. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Ha egy rendszergazda feltölt egy Power BI-vizualizációt a nyilvános piactérről a szervezet áruházába, az automatikusan frissül, ha a készítője frissíti a nyilvános piactéren a vizualizációt?

Nem, a nyilvános piactérről nem érkezik automatikusan a frissítés. A szervezeti Power BI-vizualizációk verziójának frissítése a rendszergazda feladata.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Van lehetőség a szervezeti áruház letiltására?

Nem, a felhasználók számára mindig megjelenik a *SAJÁT SZERVEZET* lap a Power BI Desktopban és a Power BI szolgáltatásban. Ha a rendszergazda letiltja vagy törli az összes szervezeti Power BI-vizualizációt a felügyeleti portálról, a szervezeti tároló üres lesz.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Ha a rendszergazda letiltja a Power BI-vizualizációkat a felügyeleti portálon (Bérlői beállítások), a felhasználók attól még hozzáféréssel rendelkeznek a szervezeti Power BI-vizualizációkhoz?

Igen. Az, hogy a rendszergazda letiltja a vizualizációkat a felügyeleti portálon, nincs hatással a szervezeti áruházra.

Bizonyos szervezetek letiltják a Power BI-vizualizációkat, és csak olyan, válogatott vizualizációk használatát engedélyezik, amelyeket a Power BI-rendszergazda importált és töltött fel a szervezeti áruházba.

A Power BI-vizualizációnak a felügyeleti portálon történő letiltása nem lesz érvényesítve a Power BI Desktopban. Az asztali verzió felhasználói a jelentéseikben továbbra is hozzáadhatnak és használhatnak a nyilvános piactérről származó Power BI-vizualizációkat. Ezek a nyilvános Power BI-vizualizációk azonban nem jelennek meg a Power BI szolgáltatásban való közzététel után, és kiváltják a megfelelő hibaüzenetet. 

Ha a felügyeleti portálon kényszerítve van a Power BI-vizualizációk beállítás, a Power BI szolgáltatás felhasználói nem importálhatnak Power BI-vizualizációkat a nyilvános piactérről. Csak a szervezeti tárolóból származó vizualizációkat lehet importálni.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Mik a Power BI-vizualizációk előnyei a szervezeti tárolóban?

* Mindenki a vizualizáció azonos verzióját kapja, amely felett a Power BI-rendszergazda gyakorol irányítást. Ha a rendszergazda frissíti a vizualizáció verzióját a felügyeleti portálon, a szervezet összes felhasználója automatikusan megkapja a frissített verziót.

* Többé nem kell megosztani e-mailben vagy megosztott mappákban a vizualizációs fájlokat. A szervezeti tárolóban elérhető ajánlatok az összes bejelentkezett tag számára láthatók.

* Biztonságos, és számos támogatási lehetőséget biztosít. A szervezeti Power BI-vizualizációk új verziói automatikusan frissülnek minden jelentésben.

* A rendszergazdák szabályozhatják, hogy mely Power BI-vizualizációk legyenek elérhetők a szervezetben.

* A rendszergazdák a felügyeleti portálról engedélyezhetik/letilthatják a vizualizációkat tesztelési célból.

## <a name="certified-power-bi-visuals"></a>Minősített Power BI-vizualizációk

### <a name="what-are-certified-power-bi-visuals"></a>Melyek a minősített Power BI-vizualizációk?

A minősített Power BI-vizualizációk olyan Power BI-vizualizációk, amelyek megfelelnek bizonyos [követelményeknek](power-bi-custom-visuals-certified.md), és amelyeket a Microsoft minősített.

A [Marketplace-en](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) a minősített Power BI-vizualizációk sárga jelvénnyel jelennek meg, amely igazolja, hogy a minősítésük megtörtént.

A külső egyéni vizualizációknak nem a Microsoft a készítője. Ügyfeleinknek azt javasoljuk, hogy közvetlenül a készítővel kapcsolatba lépve ellenőrizzék a külső vizualizációk működését.

### <a name="what-tests-are-done-during-the-certification-process"></a>Milyen teszteket végeznek a minősítési folyamat során?

A minősítési folyamat tesztjei egyebek mellett a következők: 
* Kódok véleményezése
* Statikus kód elemzése
* Adatszivárgás
* Adatok zavarossága
* Behatolás tesztelése
* XSS-hozzáférési teszt
* Rosszindulatú adatinjektálás
* Bemeneti ellenőrzés
* Funkcionális tesztelés
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Minden új beküldéssel (frissítéssel) ismét ellenőrizve lesznek a tanúsított Power BI-vizualizációk?

Igen. Valahányszor egy minősített vizualizáció új verziója be van küldve a Marketplace-re, a vizualizáció frissítése ugyanezeken a minősítési ellenőrzéseken megy keresztül.

A verziófrissítési minősítés automatikus. Ha a rendszer a követelmények olyan megsértését észleli, amely a frissítés elutasítását okozza, e-mailt küld a fejlesztőnek, amelyben le lesz írva, hogy mit kell kijavítani.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>A minősítéssel rendelkező Power BI-vizualizáció elveszítheti a tanúsítványát egy új frissítést követően?

Nem, ez nem lehetséges. A minősítéssel rendelkező vizualizáció nem veszítheti el a tanúsítványát egy új frissítéssel. A frissítés lesz elutasítva.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Meg kell osztani a kódot egy nyilvános adattárban, ha minősítem a Power BI-vizualizációt?

Nem, a kódját nem kell nyilvánosan megosztania.

Adjon olvasási engedélyeket a Power BI-vizualizáció kódjának ellenőrzéséhez. Ezt megteheti például a GitHub privát adattárának használatával.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>A minősített Power BI-vizualizációnak a piactéren kell lennie?

Igen. A privát vizualizációk nincsenek minősítve.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Mennyi időt vesz igénybe a vizualizációm minősítése?

Az új Power BI-vizualizáció minősítése (az első minősítés) akár négy hétig is eltarthat. 

Power BI-vizualizáció frissített verziójának minősítése akár három hétig is eltarthat. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Biztosítja a minősítési eljárás, hogy ne léphessen fel adatszivárgás?

A végrehajtott tesztek célja annak ellenőrzése, hogy a vizualizáció nem kapcsolódik-e külső szolgáltatásokhoz vagy erőforrásokhoz. 

A külső egyéni vizualizációknak nem a Microsoft a készítője. Ügyfeleinknek azt javasoljuk, hogy közvetlenül a készítővel kapcsolatba lépve ellenőrizzék a külső Power BI-vizualizációk működését.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Biztonságos a nem minősített Power BI-vizualizációk használata?

A nem minősített Power BI-vizualizációk nem feltétlenül jelentenek nem biztonságos vizualizációkat.

Egyes vizualizációk azért nincsenek minősítve, mert nem felelnek meg egy vagy több [minősítésbeli követelménynek](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Például egy külső szolgáltatáshoz (például egy térképvizualizációhoz) vagy egy kereskedelmi könyvtárakat használó vizualizációhoz csatlakozik.
 
## <a name="visuals-with-additional-purchases"></a>Vizualizációkon belüli további vásárlás

### <a name="what-is-a-visual-with-additional-purchases"></a>Mi a vizualizációkon belüli további vásárlás?

A további vásárlásokat tartalmazó vizualizációk hasonlóak az alkalmazáson belüli vásárlási bővítményekhez (IAP). Ezek bővítmények tartalmaznak egy **További vásárlásra is szükség lehet** árcímkét.

Az IAP típusú Power BI-vizualizációk ingyenes és letölthető Power BI-vizualizációk. A felhasználók semmit sem fizetnek a piactéren a Power BI-vizualizációk letöltéséért.

Az IAP-vizualizációk speciális funkciók alkalmazáson belüli megvásárlásának lehetőségét kínálják fel.  

### <a name="what-is-changing-in-the-submission-process"></a>Mi változik a beküldés folyamatában?

A Power BI IAP-vizualizációi piactérre küldésének folyamata ugyanaz, mint az ingyenes Power BI-vizualizációké. Power BI-vizualizációt a [Partnerközpont](https://docs.microsoft.com/partner-center/) használatával lehet minősítésre beküldeni.


A Power BI-vizualizáció regisztrálásakor lépjen a *Termékbeállítás* lapra, és jelölje be az *A termékhez szolgáltatás megvásárlása szükséges* jelölőnégyzetet.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Mi a teendőm az IAP típusú Power BI-vizualizációm beküldése előtt?

Ha egyéni IAP típusú Power BI-vizualizáción dolgozik, akkor ellenőrizze, hogy az mindenben eleget tesz-e az [irányelveknek](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Az IAP-funkcióval rendelkező ingyenes Power BI-vizualizációknak meg kell tartaniuk mindazokat az ingyenes funkciókat, melyeket korábban kínáltak. A régi ingyenes funkciók mellett felvehet választható, speciális fizetett funkciókat. Javasoljuk, hogy a speciális funkciókkal rendelkező Power BI IAP-vizualizációkat új Power BI-vizualizációkként vegye fel, és ne a régi ingyeneseket frissítse.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Mindenképpen minősíteni kell az IAP típusú Power BI-vizualizációkat?

A [minősítési](power-bi-custom-visuals-certified.md) folyamat választható. A Power BI IAP-vizualizációi minősítéséről a fejlesztő dönt.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Minősíttethetem az egyéni IAP típusú Power BI-vizualizációmat?

Igen. Miután az AppSource csapata jóváhagyta az Ön IAP típusú Power BI-vizualizációját, benyújthatja azt [minősítési](power-bi-custom-visuals-certified.md) eljárásra.

A minősítés választható eljárás. Ön döntheti el, hogy minősíttetni kívánja-e IAP-vizualizációját.

## <a name="additional-questions"></a>További kérdések

### <a name="how-to-get-support"></a>Hogyan kérhetek segítséget?

Ha bármilyen kérdése, megjegyzése vagy problémája van, vegye fel a kapcsolatot a Power BI-vizualizációk csapatával a pbicvsupport@microsoft.com címen.  

## <a name="next-steps"></a>Következő lépések

Bővebben a [Power BI-vizualizációk hibáinak elhárítását](power-bi-custom-visuals-troubleshoot.md) ismertető cikkből tájékozódhat.
