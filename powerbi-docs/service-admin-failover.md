---
title: Gyakori kérdések a Power BI-beli magas rendelkezésre állással, feladatátvétellel és vészhelyreállítással kapcsolatban
description: Ismertető a Power BI szolgáltatás által a felhasználók számára biztosított magas rendelkezésre állásról, üzletmenet-folytonosságról és vészhelyreállításról.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 3dd50d4f57b3146135cde5e91062ed3b2a0eecc1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "77527338"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Gyakori kérdések a Power BI-beli magas rendelkezésre állással, feladatátvétellel és vészhelyreállítással kapcsolatban

Ez a cikk a Power BI szolgáltatás által a felhasználók számára biztosított magas rendelkezésre állásról, üzletmenet-folytonosságról és vészhelyreállításról nyújt tájékoztatást. A cikk elolvasása után jobban megértheti, mi biztosítja a magas rendelkezésre állást, milyen körülmények esetén hajt végre a Power BI feladatátvételt, és mi várható el a szolgáltatástól ilyen esetben.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Mit jelent a „magas rendelkezésre állás” a Power BI esetében?

A Power BI teljes mértékben felügyelt szoftverszolgáltatás (SaaS).  A Microsoft úgy tervezi és működteti, hogy ellenálló legyen az infrastruktúra hibáival szemben, így a felhasználók mindig hozzáférjenek jelentéseikhez.  A szolgáltatást [99,9%-os szolgáltatói szerződés](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) támogatja.

## <a name="what-is-a-power-bi-failover"></a>Mit jelent a Power BI-feladatátvétel?

A Power BI minden összetevőnek több példányát tartja fenn Azure-adatközpontokban (más néven régiókban), hogy garantálhassa az üzletmenet folytonosságát. Kimaradás, vagy olyan hiba esetén, amely miatt a Power BI elérhetetlen vagy működésképtelen lesz egy régióban, a Power BI minden régióbeli összetevőjének feladatát egy tartalék példány veszi át. A feladatátvétel új régióban (általában ugyanazon a földrajzi helyen belül, a [Microsoft Adatvédelmi Központ](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) által közölt módon) állítja helyre a Power BI szolgáltatási példány elérhetőségét és működőképességét.

A feladatátvételt végző Power BI szolgáltatási példány csak _olvasási műveleteket_ támogat, tehát feladatátvétel idején a következő műveletek nem támogatottak: frissítés, jelentés-közzétételi műveletek, irányítópultok vagy jelentések módosítása, valamint a Power BI metaadatainak megváltozásával járó további műveletek (például megjegyzés beszúrása egy jelentésbe).  Az olyan olvasási műveletek, mint az irányítópultok vagy jelentések megjelenítése (amelyek nem DirectQueryn, vagy helyszíni adatforrásokkal való élő kapcsolaton alapulnak) továbbra is a megszokott módon működnek.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Hogyan lesznek a biztonságimásolat-példányok mindig szinkronizálva az adataimmal?

A Power BI szolgáltatás minden összetevője rendszeresen szinkronizálja biztonsági másolati példányait. Törekszünk a Power BI-ban feltöltött vagy módosított tartalom 15 percen belüli szinkronizálására. Feladatátvétel esetén a Power BI az [Azure Storage georedundáns replikáció](/azure/storage/common/storage-redundancy-grs) és az [Azure SQL georedundáns replikáció](/azure/sql-database/sql-database-active-geo-replication) használatával garantálja a biztonsági másolati példányok más régiókbeli meglétét, így feladatátvétel esetén azok használhatók.

## <a name="where-are-the-failover-clusters-located"></a>Hol helyezkednek el a feladatátvevő fürtök?

A biztonsági másolati példányok a vállalata Power BI-beli regisztrációja során választott földrajzi helyen (geo) belül helyezkednek el, hacsak a [Microsoft Adatvédelmi Központban](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) más nincs megadva. Egy geo több régiót is tartalmazhat, a Microsoft pedig az adatrugalmasság érdekében az adott geón belül bármelyik régióba replikálhatja az adatokat. A Microsoft nem replikálja vagy helyezi át ügyfelek adatait a geón kívülre. A Power BI által kínált geók és az azokban lévő régiók leképezését a [Microsoft Adatvédelmi Központban](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) találja meg.

## <a name="how-does-microsoft-decide-to-failover"></a>Hogyan dönt a Microsoft a feladatátvétel végrehajtásáról?

Két különböző rendszer jelzi, ha feladatátvételre lehet szükség:

- A külső és belső figyelési mintavételek az elérhetőség vagy a helyes működés hiányára utalnak. Ilyen jelek származhatnak a Power BI-összetevőinek, esetleg egy vagy több, a Power BI által igényelt szolgáltatásnak az észlelt kimaradásából.
- A Microsoft Azure központi üzemeltetési csapata értesít minket egy régióban történt kritikus szolgáltatáskimaradásról.

Mindkét esetben a Power BI vezetőségének tagjai döntenek a feladatátvételről. Maga a döntéshozatal nincs automatizálva. Miután a döntést meghozták, a feladatátvétel folyamata automatikusan megy végbe.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Honnan tudhatom, hogy a Power BI feladatátvételi módban van-e?

Értesítés jelenik meg a Power BI támogatási oldalán ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). Az értesítés tartalmazza a feladatátvétel idején nem elérhető fő műveleteket, amilyen a közzététel, a frissítés, az irányítópultok létrehozása, az irányítópultok duplikálása és a jogosultságok módosítása.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Mennyi időt vesz igénybe a Power BI feladatátvétele?

A Power BI körülbelül 15 perccel az után lesz újra működőképes, hogy észleli a feladatátvétel szükségességét. A feladatátvétel szükségességének felismeréséhez szükséges idő a megszakadt tevékenységtől függően változó. 

Ha feladatátvételre kerül sor, a Power BI Azure Storage georeplikációt használ a feladatátvétel végrehajtásához. Az ilyen replikációknak általában 15 perces visszatérési pontja van, azonban [az Azure Storage nem garantálja ezt az időkeretet](https://docs.microsoft.com/azure/storage/common/storage-redundancy) SLA-val, ezért a Power BI sem garantálhat időkeretet. 


## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Mikor tér vissza a Power BI-példányom az eredeti régióba?

A Power BI szolgáltatás példányai a feladatátvételt okozó probléma megoldása után térnek vissza az eredeti régióba. Kísérje figyelemmel a Power BI támogatási oldalát: A probléma megoldása után a Power BI csapata eltávolítja a feladatátvételt leíró értesítést. Ettől kezdve a megszokott működést kell tapasztalnia.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Én vagyok a felelős a Power BI-megoldásom elérhetőségéért?

Ha a vállalatánál használt Power BI-megoldásnak része az alábbi elemek egyike, akkor a megoldás magas rendelkezése állásának garantálása érdekében Önnek is meg kell tennie bizonyos intézkedéseket:

- Ha vállalata a Power BI Premiumot használja, gondoskodjon róla, hogy a prémium szintű kapacitás az üzemelő példány követelményeinek megfelelően legyen méretezve.  A [Power BI Premium tervezéséről és üzembe helyezéséről szóló tanulmány](https://aka.ms/Premium-Capacity-Planning-Deployment), valamint a [Power BI Premium-kapacitásmetrikák alkalmazás](service-admin-premium-monitor-capacity.md) segíthet ennek a követelménynek a tervezésében és betartásában. Segítségképpen a metrikaalkalmazáshoz és a felügyeleti portálhoz rendszeresen adunk új funkciókat a Power BI-ban.
- Ha vállalata helyszíni adatátjáró használatával fér hozzá helyszíni adatforrásokhoz, akkor az átjárót az [ebben a cikkben ismertetett módon](/data-integration/gateway/service-gateway-high-availability-clusters) kell beállítania, hogy támogassa a magas rendelkezésre állást. Kövesse ezt az útmutatót, ha importálás módban frissít jelentéseket, vagy ha DirectQuery vagy élő kapcsolat használatával fér hozzá adatokhoz vagy adatmodellekhez.

## <a name="will-gateways-function-when-in-failover-mode"></a>Működnek az átjárók feladatátvételi módban?

Nem. A helyszíni adatforrásokból igényelt adatok (DirectQueryn vagy élő kapcsolaton alapuló jelentések és irányítópultok) feladatátvétel idején nem működnek. Az átjáró konfigurációja azonban nem változik: Amint a Power BI-példány eredeti állapota helyreáll, az átjárók ismét a szokott módon működnek tovább.
