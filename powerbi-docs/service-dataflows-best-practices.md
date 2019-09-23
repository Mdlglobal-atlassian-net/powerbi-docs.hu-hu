---
title: Power BI-adatfolyamokhoz ajánlott eljárások
description: Power BI-adatfolyamokhoz ajánlott eljárások
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c5aeb74277379b46398dc709f5deda1d10dc0926
ms.sourcegitcommit: 7eb74b060de080152c190ac7eb6b64767f8d6626
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70919483"
---
# <a name="dataflows-best-practice"></a>Ajánlott eljárások adatfolyamokhoz

Ez a cikk az adatfolyamok tervezésének a Power BI szolgáltatásban bevált gyakorlatait mutatja be. Ennek az útmutatónak a használatával megtanulhat adatfolyamokat létrehozni, és ezeket a gyakorlatokat a saját adatfolyamaihoz felhasználni.

> [!NOTE]
> A cikkben ismertetett javaslatok irányelvek. Ésszerű indokok szólhatnak emellett, hogy eltérjen az itt ismertetett ajánlott eljárásoktól. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>A betöltés és az átalakítás szétválasztása a fejlettebb számítási motor használatához

Adatfolyamok létrehozásakor jó ötletnek tűnhet egyetlen adatfolyamot létrehozni az összes entitással, átalakítással, összekapcsolással és fejlesztéssel. Kisebb adathalmazok esetében egyetlen adatfolyam hatékony lehet. Nagyobb adatmennyiség esetén azonban az összekapcsolásokat vagy átalakításokat torlódások vagy memóriakorlátozások hátráltathatják. Ezeknek a problémáknak a kezelésére egy továbbfejlesztett motort bocsátottuk ki a Power BI Premium-felhasználók számára, amely sokkal nagyobb adattömegekre skálázható. A továbbfejlesztett számítási motor csak összekapcsolt vagy számított entitásokon működik, ezért a kihasználásához érdemes külön adatfolyamot létrehozni a betöltéshez, és egy kapcsolt adatfolyamot az összetett egyesítési és átalakítási műveletekhez.

Az adatfolyamok szétválasztása a frissítési problémák diagnosztizálásában és elhárításában is segít, főleg olyan források használata esetén, amelyekre átviteli korlátozások vonatkoznak.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>A továbbfejlesztett számítási motor kihasználására képes műveletek végrehajtása

A továbbfejlesztett számítási motor kihasználása érdekében először egy számított entitásban végezze el az összekapcsolásokat és szűrési átalakításokat, mielőtt más átalakításokat végez.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Adatfolyamok szétválasztása a SharePointhoz kapcsolódva

Ha a SharePointtal dolgozik, és több fájlhoz is kapcsolódik, szórványos hibákat tapasztalhat. A SharePoint a kérések korlátozásával biztosítja a megbízhatóságát és válaszképességét. Emiatt jó ötletnek tűnhet, hogy amikor Excel-fájlokhoz csatlakozik a SharePointból, az összes fájlt egyetlen adatfolyamban töltse le. Ha sok, 20-nál több fájlt tölt le, hozzon létre kettő vagy több adatfolyamot a frissítéssel járó terhelés felosztására, így megkerülheti a SharePoint korlátozásait.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Ütemezés elkerülése az egy munkaterületen belül összekapcsolt entitások frissítéséhez

Ha a rendszer gyakran kizárja az összekapcsolt entitásokat tartalmazó adatfolyamokból, ennek oka az egy munkaterületen belül összetartozó, egymástól függő adatfolyamok frissítés alatti zárolása lehet. Ez a zárolás biztosítja a tranzakciók pontosságát, és biztosítja mindkét adatfolyam sikeres frissítését, de megakadályozhatja a szerkesztést. 

Ha külön ütemezést állít be a kapcsolt adatfolyamhoz, akkor az adatfolyamok esetleg szükségtelen frissítése megakadályozhatja az adatfolyam szerkesztését. Ennek a problémának az elkerülésére két javaslatunk van: 

* Kerülje a forrásadatfolyammal egy munkaterületen lévő kapcsolt adatfolyamok frissítésének ütemezését
* Ha külön frissítési ütemezést szeretne beállítani, de el szeretné kerülni a zárolással járó viselkedést, különítse el az adatfolyamot egy külön munkaterületen.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Külön munkaterület létrehozása a betöltéshez és az átalakításhoz

Ha sok felhasználónak szeretne hozzáférést adni a mögöttes adatfolyamhoz anélkül, hogy a mögöttes forrásrendszer feldolgozatlan adataihoz is hozzáférnének, hozzon létre külön munkaterületet, amelyen megvan az összes megosztani kívánt adat, és erre adjon engedélyeket. Az egyéni adatfolyam-engedélyek jelenleg nem támogatottak.

### <a name="ensure-capacity-is-in-the-same-region"></a>A kapacitás legyen ugyanabban a régióban

Az adatfolyamok jelenleg nem támogatják több földrajzi régió használatát. A Prémium szintű kapacitásnak a Power BI-bérlővel egy régióban kell lennie.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>A helyszíni és a felhőbeli források elkülönítése

A korábban említett ajánlott eljárások mellett külön adatfolyamot hozhat létre az egyes forrástípusokhoz, így többek között a helyszíni, felhőbeli, SQL Server-, Spark- és Dynamics-forrásokhoz is. Az adatfolyamot erősen ajánlott az adatforrás típusa szerint szétválasztani. A forrástípus szerinti elkülönítés gyors hibaelhárítást tesz lehetővé, és megkerüli a belső korlátozásokat az adatfolyamok frissítésekor.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Adatfolyamok elkülönítése külön kapacitásban

Átviteli korlátozások esetén, vagy ha rendszeresen tapasztal hibákat a kapacitás memóriára vonatkozó korlátozása miatt, érdemes lehet elkülöníteni az adatfolyamokat, vagy több memóriával felskálázni a Prémium szintű kapacitást.

## <a name="next-steps"></a>Következő lépések

Ez a cikk az adatfolyamokhoz ajánlott eljárásokról nyújtott információkat. Az adatfolyamokra vonatkozó további információt a következő cikkekben olvashat:

* [Önkiszolgáló adatelőkészítés adatfolyamokkal](service-dataflows-overview.md)
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal](service-dataflows-on-premises-gateways.md)

CDM-fejlesztői forrásokkal és oktatóanyagokkal kapcsolatos információt az alábbi helyeken talál:
* [Common Data Model – áttekintés](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappák](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfájl definiálása](https://go.microsoft.com/fwlink/?linkid=2045521)


A Power Queryvel és az ütemezett frissítésekkel kapcsolatos további információt a következő cikkekben talál:
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Ütemezett frissítés beállítása](refresh-scheduled-refresh.md)
