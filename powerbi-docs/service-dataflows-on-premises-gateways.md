---
title: Adatfolyamok használata helyszíni adatforrásokkal
description: Helyszíni adatok használata adatfolyamokban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 31cf660a969e1779625c205c6834ceaca92325d1
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51268004"
---
# <a name="using-dataflows-with-on-premises-data-sources-preview"></a>Adatfolyamok használata helyszíni adatforrásokkal (előzetes verzió)

Az **adatfolyamokkal** létrehozhat adatgyűjteményt többféle forrásból, kitisztíthatja és átalakíthatja az adatokat, majd betöltheti a Power BI-tárba. Adatfolyam létrehozásakor érdemes lehet helyszíni adatforrásokat használni. Ez a cikk tisztázz az adatfolyamok létrehozásával kapcsolatos követelményeket és a **vállalati átjáró** konfigurálásának módját a kapcsolatok engedélyezéséhez.

![Adatfolyamok és átjárók](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

> [!NOTE]
> Az adatfolyamok funkció előzetes verzióban áll rendelkezésre, és az általánosan elérhetővé válás előtt módosulhat és frissülhet.
 
## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Vállalati átjáró konfigurálása az adatfolyamokkal való használatra

Helyszíni adatforrás adatfolyamban való használatához az adatfolyamot létrehozó minden felhasználónak rendelkeznie kell egy telepített és konfigurált **vállalati átjáróval**. Az adatfolyamot létrehozó felhasználónak a vállalati átjáró rendszergazdájának kell lennie annak érdekében, hogy ezt az átjárót használja az adatfolyamhoz.

> [!NOTE]
> Az adatfolyamok csak vállalati átjárók használatakor támogatottak.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Helyszíni adatforrás használata egy adatfolyamban

Adatfolyam létrehozásakor válasszon egy helyszíni adatforrást az adatforrások listájából amint az a következő képen látható.

![Helyszíni adatforrás kiválasztása](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

Miután elvégezte a kijelölést, meg kell adnia a vállalati átjáró csatlakozási adatait, amelyeket a helyszíni adatok elérésére fog használni. Ki kell választania az átjárót, és meg kell adnia a hitelesítő adatokat a kiválasztott átjáróhoz. A legördülő listában csak azok az átjárók jelennek meg, amelyeknek a felhasználó a rendszergazdája.

![Kapcsolati adatok megadása](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Az átjáró figyelése

A vállalati átjáróban az adatfolyamot ugyanúgy figyelheti, ahogyan az adatkészlet-átjárókat figyeli.

A Power BI adatfolyam beállítási képernyőjén figyelheti az adatfolyam átjárójának állapotát, és adatfolyamokat rendelhet hozzá az átjáróhoz az alábbi ábrának megfelelően.

![Az átjáró figyelése](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Az átjáró módosítása

Az adott adatfolyamhoz használt vállalati átjárót kétféleképpen módosíthatja:

1. **A szerkesztőeszközből** – Az összes lekérdezéshez hozzárendelt átjárót az adatfolyam-szerkesztő eszközzel módosíthatja.

    > [!NOTE]
    > Az adatfolyam megpróbálja megtalálni vagy létrehozni a szükséges adatforrásokat az új átjáróval. Ha ezt nem tudja végrehajtani, addig nem lehet módosítani az átjárót, amíg minden adatfolyam elérhetővé nem válik a kiválasztott átjárón.

2. **A beállítások képernyőről** – A Power BI szolgáltatásban az adatfolyam beállítások képernyőjén lehet módosítani a hozzárendelt átjárót.

Vállalati átjárókkal kapcsolatos további információkért lásd a [Helyszíni adatátjárók](service-gateway-onprem.md) szakaszt.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Van néhány a vállalati átjárók és adatfolyamok használatával kapcsolatos ismert korlát:

* Minden egyes adatfolyam csak egy átjárót használhat. Ennek következtében az összes lekérdezést azonos átjáró használatával kell konfigurálni.
* Az átjáró módosítása hatással van a teljes adatfolyamra.
* Ha több átjáróra van szükség, az ajánlott eljárás több adatfolyam létrehozása (minden átjáróhoz egyet) és a számítási vagy entitásreferencia szolgáltatás használata az adatok egyesítésére.
* Az adatfolyamok csak vállalati átjárók használatával támogatottak. Személyes átjárók nem lesznek kiválaszthatók a legördülő listákban és a beállítások képernyőin.


## <a name="next-steps"></a>Következő lépések

Ennek a cikknek az elolvasásával helyszíni adatforrás adatfolyamokhoz való használatával kapcsolatos információkat ismerhetett meg, valamint azt, hogyan használhat és konfigurálhat átjárókat ezeknek az adatoknak az elérésére. A következő cikkek szintén hasznosak lehetnek

* [Önkiszolgáló adatelőkészítés adatfolyamokkal](service-dataflows-overview.md)
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban (előzetes verzió)](service-dataflows-computed-entities-premium.md)
* [Fejlesztői erőforrások a Power BI-adatfolyamokhoz (előzetes verzió)](service-dataflows-developer-resources.md)

A Power Queryvel és az ütemezett frissítésekkel kapcsolatos további információkért olvassa el ezeket a cikkeket:
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Ütemezett frissítés beállítása](refresh-scheduled-refresh.md)

A Common Data Modellel kapcsolatos további információkért olvassa el a áttekintését tartalmazó cikket:
* [Common Data Modell – áttekintés](https://docs.microsoft.com/powerapps/common-data-model/overview)

