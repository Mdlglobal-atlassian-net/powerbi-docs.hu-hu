---
title: Útmutató az Azure Data Lake Storage Gen2 és a Power BI csatlakoztatásához adatfolyam-tároláshoz
description: Saját adatok importálása adatfolyamokba az Azure Data Lake Storage Gen2 használatával
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e24888d4be0a527bd7af6a28fd28795b516b2020
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309268"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Azure Data Lake Storage Gen2 csatlakoztatása adatfolyam-tároláshoz

A Power BI-munkaterületeket konfigurálhatja úgy, hogy az adatfolyamokat a szervezeti Azure Data Lake Storage Gen2-fiókban tárolják. Ez a cikk az ehhez szükséges általános lépéseket útmutatással és az ajánlott eljárásokkal együtt ismerteti. A munkaterületek Data Lake-beli adatfolyam-definíciók és adatfájlok tárolására való konfigurálása egyebek mellett az alábbi előnyökkel jár:

* Az Azure Data Lake Storage Gen2 kitűnően méretezhető tárolási lehetőséget kínál az adatokhoz
* Az adatfolyam-adatokat és a definíciós fájlokat az informatikai fejlesztők is felhasználhatják az Azure Data és a mesterséges intelligencia (AI) kiaknázására az [Azure Data Servicesből származó GitHub-mintákat](https://aka.ms/cdmadstutorial) ismertető cikkben leírtak szerint
* A vállalati fejlesztők a belső alkalmazásokba és üzletági megoldásokba integrálhatják az adatfolyamok adatait, az adatfolyamokhoz és az Azure-hoz készült fejlesztői források használatával

Az Azure Data Lake Storage Gen2 adatfolyamokhoz való felhasználásához az alábbiak szükségesek:

* **Power BI-bérlő** – Az Azure Active Directory-bérlő (AAD-bérlő) legalább egy fiókjának Power BI-regisztrációval kell rendelkeznie
* **Globális rendszergazdafiók** – ez a fiókra akkor van szükség, ha csatlakozni szeretne a Power BI-hoz, és úgy szeretné konfigurálni a Power BI-t, hogy az Azure Data Lake Storage Gen2-fiókjában tárolja az adatfolyam-definíciót és az -adatokat
* **Azure-előfizetés** – az Azure Data Lake Storage Gen2 használatához Azure-előfizetés szükséges
* **Erőforráscsoport** – használhat meglévő erőforráscsoportot, vagy létrehozhat egy újat
* **Egy Data Lake Storage Gen2-vel rendelkező Azure Storage-fiók** 

> [!TIP]
> Ha még nincs Azure-előfizetése, kezdés előtt hozzon létre egy [ingyenes fiókot](https://azure.microsoft.com/free/).

> [!WARNING]
> Az adatfolyam-tároló helye a konfigurálás után már nem módosítható. További fontos megfontolásokért tekintse meg a [Megfontolandó szempontok és korlátozások](#considerations-and-limitations) című szakaszt a cikk végén.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-bi"></a>Az Azure Data Lake Storage Gen2 előkészítése a Power BI-hoz

Mielőtt Azure Data Lake Storage Gen2-fiókkal konfigurálná a Power BI-t, először tárfiókot kell létrehoznia és konfigurálnia. A Power BI-ra vonatkozó követelmények az alábbiak:

1. Az ADLS-tárfiók tulajdonosának kell lennie. Ezt az erőforrás szintjén kell hozzárendelni, és nem az előfizetési szintről örökölve.
2. A tárfiókot ugyanabban az AAD-bérlőben kell létrehozni, mint a Power BI-bérlőt.
3. A tárfiókot ugyanabban a régióban kell létrehozni, mint a Power BI-bérlőt. A Power BI-bérlő helyének meghatározását a [Power BI-bérlő helyének megállapításáról](../admin/service-admin-where-is-my-tenant-located.md) szóló cikk ismerteti.
4. A tárfiókban engedélyeznie kell a *hierarchikus névtér* funkciót.

Az alábbi szakaszok az Azure Data Lake Storage Gen2-fiók konfigurálásához szükséges lépéseket írják le részletesen.

### <a name="create-the-storage-account"></a>A tárfiók létrehozása

Kövesse az [Azure Data Lake Storage Gen2-tárfiók létrehozása](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account) című cikkben leírt lépéseket.

1. Mindenképpen a Power BI-bérlőével azonos helyet válasszon, a tároló beállítása pedig legyen **StorageV2 (általános célú v2)**
2. Engedélyezze a hierarchikus névtér funkciót
3. A replikációs beállítást érdemes **georedundáns írásvédett társzolgáltatásra (RA-GRS)** beállítani

### <a name="grant-permissions-to-power-bi-services"></a>Engedélyek megadása Power BI-szolgáltatások számára

Ezután olvasó és adathozzáférési szerepkört kell adnia a Power BI szolgáltatásnak a létrehozott tárfiókban. Mindkettő beépített szerepkör, tehát a lépések maguktól értetődnek. 

Kövesse a [Beépített RBAC-szerepkör hozzárendelése](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac#assign-a-built-in-rbac-role) című témakör lépéseit.

A **Szerepkör-hozzárendelés megadása** ablakban jelölje ki az **Olvasó és az Adathozzáférési** szerepkört. Majd a keresőt használva keresse meg a **Power BI szolgáltatás** alkalmazást.
Ismételje meg ugyanezeket a lépéseket a **Storage blob adattulajdonosa** szerepkörhöz, és rendelje hozzá a szerepkört a **Power BI szolgáltatás** és a **Power BI Premium** alkalmazásokhoz.

> [!NOTE]
> Legalább 30 percig tart, amíg az engedély a Power BI-ból átkerül a Portalra. Várjon 30 percet minden alkalommal, amikor a Portalon módosítja az engedélyeket, hogy azok megjelenjenek a Power BI-ban. 

## <a name="connect-your-azure-data-lake-storage-gen2-to-power-bi"></a>Az Azure Data Lake Storage Gen2 csatlakoztatása a Power BI-hoz

Miután beállította Azure Data Lake Storage Gen2-fiókját az Azure Portalon, a **Power BI felügyeleti portálon** csatlakoztassa a Power BI-hoz. A Power BI-adatfolyamok tárolóját is kezelheti a Power BI felügyeleti portál **Adatfolyam-tároló** beállításainak szakaszában. Az indításról és az alapszintű használatról [A felügyeleti portál elérése](../admin/service-admin-portal.md) című cikk nyújt részletes útmutatást.

**Azure Data Lake Storage Gen2**-fiókjához az alábbi lépésekben kapcsolódhat:

1. Nyissa meg az **Adatfolyam-beállítások** lapot a **Power BI felügyeleti portálon**

    ![Power BI felügyeleti portál](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-08b.png) 

2. Válassza a **Csatlakozás az Azure Data Lake Storage Gen2-höz** gombot. Az alábbi ablak jelenik meg.

    ![Azure Data Lake Storage Gen2](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_09.jpg) 

3. Adja meg a tárfiók **előfizetés-azonosítóját**.
4. Adja meg annak az **erőforráscsoportnak a nevét**, amelyben a tárfiókot létrehozta.
5. Adja meg a **tárfiók nevét**.
6. Kattintson a **Csatlakozás** gombra.

Miután végrehajtotta ezeket a lépéseket, Azure Data Lake Storage Gen2-fiókja csatlakoztatva lesz a Power BI-hoz. 

> [!NOTE]
> Ahhoz, hogy kapcsolatot tudjon konfigurálni az Azure Data Lake Storage Gen2-höz a Power BI felügyeleti portálján, globális rendszergazdai jogosultságokkal kell rendelkeznie. A globális rendszergazdák azonban nem csatlakoztathatnak külső tárhelyeket a felügyeleti portálon.  

Ezután engedélyt kell adnia a vállalaton belüli személyeknek munkaterületeik konfigurálására, hogy használni tudják ezt a tárfiókot adatfolyamok definiálására és adattárolásra. Erre a következő szakaszban kerül sor. 


## <a name="allow-admins-to-assign-workspaces"></a>Munkaterületek hozzárendelésének engedélyezése rendszergazdák számára

Az adatfolyam-definíciók és az adatfájlok alapértelmezés szerint a Power BI által biztosított tárolóban helyezkednek el. A saját tárfiókban lévő adatfolyamfájlok eléréséhez a munkaterület rendszergazdáinak először konfigurálnia kell a munkaterület úgy, hogy lehetővé tegye adatfolyamok hozzárendelését és tárolását az új tárfiókban. Ahhoz, hogy konfigurálni tudja az adatfolyam tárolási beállításait, a munkaterület rendszergazdájának tároló-hozzárendelési jogosultságot kell adni a **Power BI felügyeleti portálján**.

Tároló-hozzárendelési jogosultság megadásához nyissa meg az **Adatfolyam-beállítások** lapot a **Power BI felügyeleti portálján**. Az *Annak engedélyezése, hogy a munkaterület-rendszergazdák munkaterületeket rendelhessenek hozzá ehhez a tárfiókhoz* választógombot az **engedélyezés** lehetőségre kell állítani. Az engedély megadása után válassza az **Alkalmaz** gombot a módosítások érvénybe léptetéséhez. 

![Munkaterületek hozzárendelésének engedélyezése rendszergazdák számára](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_10.jpg) 

Ennyi az egész. A Power BI-munkaterület rendszergazdái ezt követően munkaterületeket rendelhetnek az Ön által létrehozott fájlrendszerhez.


## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Ez a funkció előzetes verziójú, és a viselkedése a megjelenés időpontjához közeledve változhat. Az adatfolyam-tároló használatakor figyelembe kell vennie néhány tényezőt és korlátozást:

* Az adatfolyam-tároló helye a konfigurálás után már nem módosítható.
* Alapértelmezés szerint csak az Azure Data Lake Storage Gen2-ben tárolt adatfolyam tulajdonosa férhet hozzá az adatfolyam adataihoz. Az Azure-ban tárolt adatfolyamokhoz további személyeknek úgy adhat hozzáférést, hogy hozzáadja őket az adatfolyam CDM-mappájához 
* Hivatkozott entitásokkal csak akkor hozható létre adatfolyam, ha ugyanabban a tárfiókban vannak tárolva
* Megosztott Power BI-kapacitásokban lévő helyszíni adatforrások nem támogatottak a vállalati data lake-ben tárolt adatfolyamokban
* Az ADLS Gen 2 nem törli automatikusan a pillanatképeket. Ha tárhelyet szeretne felszabadítani, egy Azure-függvény létrehozásával rendszeresen törölheti a régi pillanatképeket.

Létezik néhány ismert probléma is. Ezeket az alábbi szakasz ismerteti.

Power BI Desktop-ügyfél csak akkor fér hozzá az **Azure Data Lake-tárfiókokban** tárolt adatfolyamokhoz, ha az adatfolyam tulajdonosa, vagy ha jogosultsággal rendelkezik a lake-beli CDM-mappához. A helyzet a következőnek felel meg:

1. Anna új munkaterületet hozott létre, amelyet úgy konfigurált, hogy a vállalati data lake-ben tárolja az adatfolyamokat. 
2. Dávid, aki szintén tagja az Anna által létrehozott munkaterületnek, a Power BI Desktop és az adatfolyam-összekötő használatával szeretne adatokhoz jutni az Anna által létrehozott adatfolyamból.
3. Dávid hasonló hibajelenséget tapasztal, ugyanis nem rendelkezik jogosultsággal az adatfolyam lake-beli CDM-mappájához.

Gyakori kérdések és válaszok többek között az alábbiak:

**Kérdés:** Mi a teendő, ha korábban adatfolyamokat hoztam létre egy munkaterületen, és szeretném módosítani a tárolási helyüket?

**Válasz:** Az adatfolyamok tárolási helye a létrehozásuk után már nem módosítható. 

**Kérdés:** Mikor módosíthatom egy munkaterület adatfolyam-tárolási helyét?

**Válasz:** Egy munkaterület adatfolyam-tárolási helyének módosítása csak akkor megengedett, ha a munkaterület nem tartalmaz adatfolyamokat.


## <a name="next-steps"></a>Következő lépések

Ez a cikk Azure Data Lake Gen2-adatfolyamok tárolása érdekében végzett csatlakoztatásához nyújtott útmutatást. További információt a következő cikkekben találhat:

Az adatfolyamokról, a CDM-ről és az Azure Data Lake Storage Gen2-ről az alábbi cikkekből tájékozódhat:

* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)
* [Munkaterület adatfolyam-beállításainak konfigurálása (előzetes verzió)](service-dataflows-configure-workspace-storage-settings.md)
* [CDM-mappa hozzáadása a Power BI-hoz adatfolyamként (előzetes verzió)](service-dataflows-add-cdm-folder.md)

Az adatfolyamokról általánosságban a következő cikkek szólnak:

* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások Power BI-adatfolyamokhoz](service-dataflows-developer-resources.md)

Az Azure Storage szolgáltatással kapcsolatban az alábbi cikkeket érdemes elolvasni:
* [Azure Storage – biztonsági útmutató](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

A Common Data Modellel kapcsolatos további információt a témát áttekintő cikkben talál:
* [Common Data Model – áttekintés](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappák](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfájl definiálása](https://go.microsoft.com/fwlink/?linkid=2045521)

[Kérdéseit mindig felteheti a Power BI-közösségben](https://community.powerbi.com/) is.
