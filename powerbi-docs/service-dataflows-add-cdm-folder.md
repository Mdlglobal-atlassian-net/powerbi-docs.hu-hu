---
title: CDM-mappa hozzáadása a Power BI-hoz adatfolyamként
description: Alkalmazás-munkaterület konfigurálása adatfolyam-definíciók és adatfájlok Azure Data Lake Storage Gen2-beli tárolására
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ce2f993e2745cb0e5b359bfbc492e6e7aea25493
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53181562"
---
# <a name="add-a-cdm-folder-to-power-bi-as-a-dataflow-preview"></a>CDM-mappa hozzáadása a Power BI-hoz adatfolyamként (előzetes verzió)

A Power BI-ban a vállalati Azure Data Lake Storage Gen2-ben tárolt Common Data Model-mappák (CDM-mappák) felvehetők adatfolyamokként. Miután létrehoz egy adatfolyamot egy CDM-mappából, a **Power BI Desktop** és a **Power BI szolgáltatás** használatával a CDM-mappákban elhelyezett adatokon alapuló adathalmazokat, jelentéseket és alkalmazásokat hozhat létre.

![Adatfolyam CDM-mappából](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

Adatfolyamok CDM-mappákból való létrehozására az alábbi felsorolásban ismertetett korlátozások érvényesek:

* Adatfolyamok CDM-mappákból való létrehozása *csak* az [új munkaterületi felületen](service-create-the-new-workspaces.md) érhető el. 
* CDM-mappa Power BI-hoz adásához a mappát az eljáró felhasználónak [a CDM-mappára és annak fájljaira vonatkozó jogosultsággal](https://go.microsoft.com/fwlink/?linkid=2029121) kell rendelkeznie.
* Ahhoz, hogy a Power BI-hoz adhassa őket, olvasási és végrehajtási jogosultsággal kell rendelkeznie a CDM-mappában lévő minden fájlra és mappára.

A következő bekezdések adatfolyamok CDM-mappából való létrehozását ismertetik.

> [!NOTE]
> Az adatfolyamok előzetes verzióban állnak rendelkezésre, és az általánosan elérhetővé válás előtt módosulhatnak és frissülhetnek.

## <a name="create-a-dataflow-from-a-cdm-folder"></a>Adatfolyam létrehozása CDM-mappából

Egy adatfolyam CDM-mappából való létrehozásának első lépéseként indítsa el a **Power BI szolgáltatást**, és válasszon **alkalmazás-munkaterületet** a bal oldali navigációs panelen. Új munkaterületet is létrehozhat, amelyben aztán létrehozhatja új adatfolyamát.

![Adatfolyam létrehozása a Power BI szolgáltatásban](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_02.jpg)

A megjelenő képernyőn válassza a **Létrehozás és csatolás** lehetőséget, ahogyan az alábbi képen látható.

![Új adatfolyam létrehozása és csatolása](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_03.jpg)

Az ezután megjelenő képernyőn nevet adhat adatfolyamának, megadhat hozzá egy leírást és a CDM-mappa elérési útját a vállalat Azure Data Lake Gen2-fiókjában. Olvassa el a cikk [A CDM-mappa elérési útjának megállapítása](service-dataflows-configure-workspace-storage-settings.md#get-the-uri-of-stored-dataflow-files) című szakaszát. 

![Adatfolyam CDM-mappából](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

Az információk megadása után hozza létre az adatfolyamot a **Létrehozás és csatolás** lehetőséget választva.

A CDM-mappákból létrehozott adatfolyamok a *külső* ikonnal megjelölve jelennek meg a Power BI-ban. A következő szakasz a hagyományos és a CDM-mappákból létrehozott adatfolyamok közötti különbségeket ismerteti.

Az engedélyeknek a cikk korábbi részében leírtak szerinti, megfelelő beállítása után már csatlakozhat adatfolyamához a **Power BI Desktopban**.


## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

A CDM-mappákból létrehozott adatfolyamokra vonatkozó engedélyek hasonló eljárással kezelhetők, mint a külső adatforrások a Power BI-ban. Az engedélyek kezelése nem a Power BI-on belül, hanem az adatforrásban történik. Ahhoz, hogy megfelelően működjenek a Power BI-jal, az engedélyeket magában az adatforrásban, például a CDM-mappából létrehozott adatfolyamban kell helyesen beállítani.

Az alábbi lista segít tisztázni, hogyan működnek a CDM-mappából létrehozott adatfolyamok a Power BI-jal.

Power BI Pro-, Premium- és Embedded-munkaterületek:
* A CDM-mappákból létrehozott adatfolyamok nem szerkeszthetők
* A CDM-mappából létrehozott adatfolyam olvasására vonatkozó engedélyeket nem a Power BI, hanem a CDM-mappa tulajdonosa kezeli

Power BI Desktop:
* Az adatfolyam adataihoz csak azok a felhasználók férnek hozzá a Power BI Dataflows összekötőből, akik hozzáféréssel rendelkeznek a munkaterülethez, amelyben az adatfolyam létre lett hozva, és a CDM-mappához


Az alábbiakban felsorolt szempontokat is érdemes figyelembe venni:

* Adatfolyamok CDM-mappákból való létrehozása *csak* az [új munkaterületi felületen](service-create-the-new-workspaces.md) lehetséges
* Csatolt entitások CDM-mappából létrehozott adatfolyamokhoz nem érhetők el


**Power BI Desktop**-ügyfél csak akkor fér hozzá az Azure Data Lake Storage Gen2-tárfiókokban tárolt adatfolyamhoz, ha az adatfolyam tulajdonosa, vagy ha külön megadott jogosultsággal rendelkezik az adatfolyam CDM-mappájához. Figyelje meg a következő példát:

1.  Anna új alkalmazás-munkaterületet hoz létre, amelyet CDM-mappából létrehozott adatfolyamok tárolására konfigurál.
2.  Dávid, aki szintén tagja az Anna által létrehozott munkaterületnek, a Power BI Desktop és az adatfolyam-összekötő használatával szeretne adatokhoz jutni az Anna által létrehozott adatfolyamból.
3.  Dávid hibajelenséget tapasztal, ugyanis nem adták hozzá jogosult felhasználóként az adatfolyam data lake-beli CDM-mappájához.

    ![Hiba adatfolyam használatára tett kísérlet esetén](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

A probléma megoldásához Dávidnak olvasási jogot kell adni a CDM-mappára és annak fájljaira. A CDM-mappákhoz való hozzáférés megadásáról [ez a cikk](https://go.microsoft.com/fwlink/?linkid=2029121) tartalmaz további információt.


## <a name="next-steps"></a>Következő lépések

Ez a cikk munkaterület-tárolók adatfolyamokhoz való konfigurálásához nyújtott útmutatást. További információt a következő cikkekben találhat:

Az adatfolyamokról, a CDM-ről és az Azure Data Lake Storage Gen2-ről az alábbi cikkekből tájékozódhat:

* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)
* [Munkaterület adatfolyam-beállításainak konfigurálása (előzetes verzió)](service-dataflows-configure-workspace-storage-settings.md)
* [Azure Data Lake Storage Gen2 csatlakoztatása adatfolyam-tároláshoz (előzetes verzió)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Az adatfolyamokról általánosságban a következő cikkek szólnak:

* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban (előzetes verzió)](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal (előzetes verzió)](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások a Power BI-adatfolyamokhoz (előzetes verzió)](service-dataflows-developer-resources.md)

Az Azure Storage szolgáltatással kapcsolatban az alábbi cikkeket érdemes elolvasni:
* [Azure Storage – biztonsági útmutató](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Ütemezett frissítés beállítása](refresh-scheduled-refresh.md)
* [Első lépések az Azure Data Servicesből származó github-mintákkal](https://aka.ms/cdmadstutorial)

A Common Data Modellel kapcsolatos további információt a témát áttekintő cikkben talál:
* [Common Data Model – áttekintés](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappák](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfájl definiálása](https://go.microsoft.com/fwlink/?linkid=2045521)

[Kérdéseit mindig felteheti a Power BI-közösségben](http://community.powerbi.com/) is.
