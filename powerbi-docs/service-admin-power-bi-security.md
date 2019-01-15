---
title: A Power BI és a biztonság
description: A Power BI és a biztonság. A Power BI kapcsolata az Azure Active Directoryval és más Azure-szolgáltatásokkal. Ez a témakör egy részletesebb tanulmányra mutató hivatkozást is tartalmaz.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/15/2018
ms.author: davidi
LocalizationGroup: Administration
ms.openlocfilehash: 83273d42ed27523c618cf229c0c3a0bec7b82cb6
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292841"
---
# <a name="power-bi-security"></a>A Power BI és a biztonság
A Power BI biztonságáról részletes leírásért [töltse le a Power BI-jal és a biztonsággal kapcsolatos tanulmányt](http://go.microsoft.com/fwlink/?LinkId=829185):

[![](media/service-admin-power-bi-security/pbi_security_01.png)](http://go.microsoft.com/fwlink/?LinkId=829185)

A Power BI szolgáltatás az **Azure**-ra épül, amely a Microsoft felhőalapú számítástechnikai infrastruktúrája és platformja. A Power BI szolgáltatás architektúrája két fürtön alapul – a webes előtérrendszer (**WFE-**) fürtön és a **háttérbeli** fürtön. A WFE-fürt kezeli a kezdeti kapcsolódást és a Power BI szolgáltatás hitelesítését, a hitelesítés után a háttérbeli fürt kezeli az összes további felhasználói interakciót. A Power BI az Azure Active Directory (AAD) használatával tárolja és kezeli a felhasználói identitásokat, valamint kezeli az adatoknak és metaadatoknak az Azure BLOB és az Azure SQL Database használatával történő tárolását.

## <a name="power-bi-architecture"></a>A Power BI-architektúra
Minden üzemelő Power BI-példány két fürtből áll – egy webes előtérrendszer (**WFE-**) fürtből és egy **háttérbeli** fürtből.

A **WFE**-fürt kezeli a kezdeti kapcsolódást és a Power BI hitelesítési folyamatát az AAD-val hitelesítve a felhasználókat, és hozzáférési jogkivonatokat ad ki a Power BI szolgáltatással való további felhasználói kapcsolatokhoz. A Power BI az **Azure Traffic Managert** (ATM) is használja arra, hogy a felhasználói forgalmat – a kapcsolódást megkísérlő ügyfél DNS-rekordja alapján – a legközelebbi adatközponthoz irányítsa a hitelesítési elvégzéséhez és statikus tartalom és fájlok letöltéséhez. A Power BI a szükséges statikus tartalmat és fájlokat az **Azure Content Delivery Network** (CDN) használatával osztja el hatékonyan a felhasználók között a földrajzi helyzet alapján.

![](media/service-admin-power-bi-security/pbi_security_v2_wfe.png)

A hitelesített ügyfelek a **háttérbeli** fürtön kommunikálnak a Power BI szolgáltatással. A **háttérbeli** fürt kezeli a vizualizációkat, a felhasználói irányítópultokat, az adathalmazokat, a jelentéseket, az adattárolást, az adatkapcsolatokat, az adatfrissítést és a Power BI szolgáltatással való kommunikáció egyéb módjait. Az **átjárói szerepkör** átjáróként szolgál a felhasználói kérelmek és a Power BI szolgáltatás között. A felhasználók nem kerülnek közvetlen kapcsolatba más szerepkörrel, csak az **átjárói szerepkörrel**. Az **átjárói szerepkört** végső soron az **Azure API Management** kezeli.

![](media/service-admin-power-bi-security/pbi_security_v2_backend_updated.png)

> [!IMPORTANT]
> Fontos tisztában lenni azzal, hogy a nyilvános interneten keresztül csak az **Azure API Management** (APIM) és az **Átjáró** (GW) szerepkörök érhetők el. Ezek biztosítják a hitelesítést, az engedélyezést, a DDoS-védelmet, a szabályozást, a terheléselosztást, az útválasztást és más funkciókat.
> 
> 

## <a name="data-storage-security"></a>Adattárolók biztonsága
A Power BI két elsődleges adattárat használ adatok tárolására és kezelésére: A felhasználóktól feltöltött adatokat általában **Azure BLOB**-tárolóra küldi, a metaadatokat és magának a rendszernek az összetevőit **Azure SQL Database**-ben tárolja.

A fenti ábrán a **háttérbeli** fürt képén lévő szaggatott vonal a felhasználók által egyedül elérhető két összetevő (a szaggatott vonaltól balra) és a csak a rendszer által elérhető szerepkörök közötti határvonalat jelzi. Amikor egy hitelesített felhasználó a Power BI szolgáltatáshoz kapcsolódik, akkor a kapcsolatot és az ügyfél minden kérelmét az **átjárói szerepkör** fogadja és kezeli (és végül az **Azure API Management** kezeli), amely aztán a felhasználó nevében használja a Power BI szolgáltatás többi elemét. Amikor egy ügyfél például egy irányítópultot próbál megtekinteni, az **átjárói szerepkör** fogadja a kérelmet, majd külön kérelmet küld a **bemutatási szerepkörnek**, hogy lekérje az adatokat, amelyekre a böngészőnek az irányítópult megjelenítéséhez szüksége van.

## <a name="user-authentication"></a>Felhasználók hitelesítése
A Power BI az Azure Active Directory ([AAD](http://azure.microsoft.com/services/active-directory/)) használatával hitelesíti a Power BI szolgáltatásra bejelentkező felhasználókat, és azután a Power BI bejelentkezési hitelesítő adatait használja, amikor egy felhasználó hitelesítést igénylő erőforrásokat próbál meg elérni. A felhasználók a Power BI-fiók létrehozásához használt e-mail-címmel jelentkeznek be a Power BI szolgáltatásba. A Power BI ezt a bejelentkezési e-mail-címet használja az *érvényes felhasználónévként*, amelyet az erőforrásoknak ad át, amikor a felhasználó adatokhoz próbál csatlakozni. Az *érvényes felhasználónév* hozzárendelődik az *egyszerű felhasználónévhez* ([UPN](https://msdn.microsoft.com/library/windows/desktop/aa380525\(v=vs.85\).aspx)), és a hozzá társított Windows-tartományi fiókká oldódik fel, amelyen megtörténik a hitelesítés.

Az olyan szervezeteknél, ahol vállalati e-mail-címeket használnak a Power BI-bejelentkezéshez (például <em>david@contoso.com</em>) az *érvényes felhasználónév* magától értetődően rendelődik hozzá az egyszerű névhez. Az olyan szervezeteknél, ahol nem vállalati e-mail-címeket használnak a Power BI-bejelentkezéshez (például <em>david@contoso.onmicrosoft.com</em>), az AAD és a helyszíni hitelesítő adatok egymáshoz rendelésének helyes működése [címtár-szinkronizálást](https://technet.microsoft.com/library/jj573653.aspx) kíván.

A Power BI platform-szintű biztonsága magában foglalja a több-bérlős környezet biztonságát, a hálózati biztonságot és további AAD-alapú biztonsági elemek hozzáadásának lehetőségét.

## <a name="data-and-service-security"></a>Az adatok és a szolgáltatás biztonsága
Ha további tájékoztatást szeretne, keresse fel a [Microsoft Adatvédelmi központot](https://www.microsoft.com/trustcenter).

Ebben a cikkben már volt szó arról, hogy a helyszíni Active Directory-kiszolgálók felhasználják a felhasználó Power BI-bejelentkezési információit az egyszerű felhasználónév és a hitelesítő adatok egymáshoz rendeléséhez. **Fontos** ugyanakkor, hogy a megosztott adatokért a felhasználók felelnek: ha egy felhasználó a saját hitelesítő adataival kapcsolódik adatforrásokhoz, majd megoszt egy, ezekre az adatokra épülő jelentést (vagy irányítópultot vagy adatkészletet), akkor azok, akikkel az irányítópultot megosztotta, hozzáférnek a jelentéshez, bár nincs jogosultságuk az eredeti adatforráshoz.

Ezalól az **SQL Server Analysis Services** szolgáltatások **helyszíni adatátjárón** keresztüli elérése jelent kivételt; az irányítópultok gyorsítótárazva vannak a Power BI-ban, de a mögöttes jelentések vagy adathalmazok hozzáférése hitelesítést kezdeményez a jelentést (vagy adathalmazt) elérni próbáló felhasználóhoz, és csak akkor biztosít hozzáférést, ha a felhasználó elegendő hitelesítő adattal rendelkezik az adatok eléréséhez. További információ: [Helyszíni adatátjáró részletesen](service-gateway-onprem-indepth.md).

## <a name="enforcing-tls-version-usage"></a>A TLS-verzió használatának kényszerítése

A hálózati és informatikai rendszergazdák a hálózatukon lévő bármely biztonságos kommunikációhoz kényszeríthetik az aktuális TLS (Transport Layer Security) használatát. A Windows a Microsoft Schannel-szolgáltatón keresztül biztosítja a TLS-verziók támogatását, ahogyan arról [a TLS Schannel SSP-t ismertető cikkben](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-) olvashat.

Ez a kényszerítés a beállításkulcsok felügyeleti beállításával érhető el. A kényszerítés leírását az [SSL-protokollok AD FS-ben való kezelésével kapcsolatos cikk](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/manage-ssl-protocols-in-ad-fs) tartalmazza. 

A **Power BI Desktop** figyelembe veszi az ezekben a cikkekben leírt beállításkulcs-beállításokat, és csak az engedélyezett TLS-verzióval hoz létre kapcsolatokat ezekkel a beállításjegyzék-beállításokkal, amikor jelen vannak.

Ezen beállításkulcsok beállításáról további információt a [TLS-beállításjegyzék beállításaival](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings) kapcsolatos cikkben talál.

