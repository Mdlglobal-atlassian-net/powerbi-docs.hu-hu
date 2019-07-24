---
title: Útmutató adatátjáró üzembe helyezéséhez a Power BI számára
description: A Power BI-átjáró telepítéséhez ajánlott eljárások és a telepítés szempontjai.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271723"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Útmutató adatátjáró üzembe helyezéséhez a Power BI számára

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

A cikk útmutatást nyújt a Power BI-hoz használható adatátjáró hálózati környezetben történő telepítéséhez, és ismerteti a telepítés szempontjait.

A helyszíni adatátjáró letöltéséről, telepítéséről, konfigurálásáról és kezeléséről a [Mi az a helyszíni adatátjáró](/data-integration/gateway/service-gateway-onprem) című cikkben olvashat részletesen. A helyszíni adatátjáróról és a Power BI-ról további információt talál a [Microsoft blogján](https://powerbi.microsoft.com/blog/) és a [Microsoft Power BI-közösség](https://community.powerbi.com/) webhelyén is.

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>A helyszíni átjáró telepítésének szempontjai

Mielőtt telepítené a helyszíni adatátjárót a Power BI felhőszolgáltatáshoz, néhány szempontot figyelembe kell vennie. A következő szakaszok ezeket a szempontokat ismertetik.

### <a name="number-of-users"></a>Felhasználók száma

A felhasználók száma, akik az átjáró használatával fognak a jelentésekkel dolgozni, fontos szempont annak eldöntésében, hogy hová telepítsük az átjárót. Néhány szempont, amelyet érdemes figyelembe venni:

* A felhasználók eltérő napszakokban használják ezeket a jelentéseket?
* Milyen típusú kapcsolatot használnak (DirectQueryt vagy importálást)?
* Minden felhasználó ugyanazt a jelentést használja?

Ha a felhasználók minden nap ugyanakkor kívánják elérni az adott jelentést, akkor gondoskodni kell róla, hogy az átjáró egy olyan számítógépen legyen telepítve, amely képes az összes kérelmet kezelni (segítségképpen a következő szakaszokból megismerheti a teljesítményszámlálókat és a minimális hardverkövetelményeket).

A **Power BI** szolgáltatásban van egy korlátozás, amely szerint *jelentésenként* csak *egy* átjáró használható, tehát hiába használ a jelentés több adatforrást, az összes adat ezen az egy átjárón fog áthaladni. Viszont, egy olyan irányítópultnál, amely *több* jelentésen alapul, mindegyik jelentéshez egy-egy dedikált átjárót használhat, így eloszthatja az átjárók terhelését az irányítópultot alkotó jelentések között.

### <a name="connection-type"></a>Kapcsolat típusa

A **Power BI-ban** kétféle kapcsolattípus áll rendelkezésre: A **DirectQuery** és az **Importálás**. Nem mindegyik adatforrás támogatja mindkét kapcsolattípust, és több szemponttól is függ, mikor melyiket érdemes használni, például a biztonsági követelményektől, a teljesítménytől, az adatkorláttól és az adatmodell méretétől. A kapcsolattípusokról és a támogatott adatforrásokról bővebben az [elérhető adatforrástípusok listájában](service-gateway-data-sources.md#list-of-available-data-source-types) olvashat.

A használt kapcsolat típusától függően az átjáróhasználat mértéke eltérő lehet. Például, amikor csak lehet, különítse el a **DirectQuery** típusú adatforrásokat az **Ütemezett frissítés** típusú adatforrásoktól (feltéve, hogy különböző jelentésekben vannak, és elkülöníthetőek). Ezzel megakadályozható, hogy DirectQuery-kérelmek ezreinek kelljen várni sorukra az átjárónál addig, amíg a cég fő irányítópultjához használt nagy méretű adatmodell reggeli ütemezett frissítése történik. Lássuk milyen szempontokat érdemes figyelembe venni a kapcsolattípusoknál:

* **Ütemezett frissítés**: A lekérdezések mérete és a napi frissítések száma alapján eldöntheti, hogy elég a javasolt minimális hardverkövetelményeknek megfelelő számítógépet használni, vagy nagyobb teljesítményű számítógépre lesz szüksége. Ha az adott lekérdezés nem kiszolgáló oldali transzformációkból áll, akkor a transzformációkat az átjáró fogja végezni, és ilyenkor hasznos lehet, ha a számítógépen, amelyen az átjáró telepítve van, több memória áll rendelkezésre.

* **DirectQuery**: A rendszer lekérdezést küld minden esetben, amikor egy felhasználó megnyitja a jelentést, vagy adatokat tekint meg. Ezért, ha várhatóan több mint 1000 felhasználó fog egyidejűleg hozzáférni az adatokhoz, érdemes gondoskodni arról, hogy a számítógép kellőképp robusztus és hatékony hardverrel rendelkezzen. **DirectQuery**-kapcsolat esetén több processzormag nagyobb teljesítményt eredményez.

Arról, hogy milyen követelmények vonatkoznak arra a gépre, amelyen a telepítést végzi, a helyszíni adatátjáró [telepítési követelményeiben](/data-integration/gateway/service-gateway-install#requirements) olvashat.

### <a name="location"></a>Hely

Az átjáró földrajzi helyzete jelentős hatással lehet a lekérdezési teljesítményre, ezért a hálózati késleltetés minimalizálása érdekében gondoskodjon róla, hogy az átjáró, az adatforrások és a Power BI-bérlő földrajzilag a lehető legközelebb helyezkedjenek el egymáshoz. A Power BI-bérlő földrajzi helyzetének meghatározásához a Power BI szolgáltatásban válassza a **?** ikont a jobb felső sarokban, majd válassza **A Power BI névjegye** lehetőséget.

![A Power BI-bérlő helyének meghatározása](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Ha a Power BI-átjárót az Azure Analysis Services szolgáltatással együtt használja, ügyeljen rá, hogy a kettő adatrégiója megegyezzen. [Ebben a videóban](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/) bővebb információt talál arról, hogyan lehet adatrégiókat beállítani több szolgáltatáshoz.

## <a name="next-steps"></a>Következő lépések

* [Proxybeállítások konfigurálása](/data-integration/gateway/service-gateway-proxy)  
* [Átjárók hibaelhárítása – Power BI](service-gateway-onprem-tshoot.md)  
* [Helyszíni adatátjáró – GYIK – Power BI](service-gateway-power-bi-faq.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

