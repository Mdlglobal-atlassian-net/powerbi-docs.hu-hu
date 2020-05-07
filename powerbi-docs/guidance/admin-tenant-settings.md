---
title: Útmutató a bérlő rendszergazdai beállításokhoz
description: Útmutató a Power BI-bérlő beállításaihoz.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: v-pemyer
ms.openlocfilehash: fdd7504823f088ed0e88657a6fcccaeb9a5a36d0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79487809"
---
# <a name="tenant-admin-settings-guidance"></a>Útmutató a bérlő rendszergazdai beállításokhoz

Ez a cikk a Power BI-adminisztrátoroknak szól, akiknek az a feladata, hogy a szervezetüknél beállítsák a Power BI-környezetet.

Útmutatást nyújtunk az olyan bérlői beállításokhoz, amelyek javítják a Power BI használati élményét, vagy amelyek kockázatot jelenthetnek a szervezet számára. Javasoljuk, hogy a bérlőt mindig úgy konfigurálja, hogy az megfeleljen a szervezet szabályzatainak és folyamatainak.

A [bérlői beállításokat](../service-admin-portal.md#tenant-settings) a [Felügyeleti portálon](https://app.powerbi.com/admin-portal/tenantSettings) lehet elvégezni, a konfigurálást pedig a [Power BI-szolgáltatásgazda](../service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi) végezheti el. Számos bérlői beállítás azt eredményezheti, hogy a képességek és a funkciók csak adott felhasználók számára lesznek elérhetőek. Ezért javasoljuk, hogy először ismerkedjen meg a beállításokkal, mielőtt megtervezné a szükséges biztonsági csoportokat. Előfordulhat, hogy ugyanazt a biztonsági csoportot több beállításra is alkalmazhatja.

## <a name="improve-power-bi-experience"></a>A Power BI-élmény javítása

### <a name="publish-get-help-information"></a>Súgóinformációk közzététele

Javasoljuk, hogy hozzon létre a szervezeten belül a Power BI-hoz kapcsolódó webhelyeket a [Microsoft Teams](/microsoftteams) vagy más együttműködési platform használatával. Ezeken a helyeken tárolhatók a képzési dokumentációk, használhatók vitákra és megbeszélésekre, licencek kérésére vagy segítségre kínált válaszokra is.

Ha így tesz, javasoljuk, hogy engedélyezze a **Súgóinformációk közzététele** beállítást _a teljes szervezet számára_. Ez a **Súgó- és támogatási beállítások** csoportban található. URL-címeket állíthat be az alábbiakhoz:

- Képzési dokumentáció
- Fórum
- Licencelési kérelmek
- Ügyfélszolgálat

Ezek az URL-címek a Power BI Súgó menüjében hivatkozásként lesznek elérhetők.

> [!NOTE]
> A **Licencelési kérelmek** URL-cím megadásával megakadályozható, hogy a felhasználók regisztrálni tudjanak a Power BI Pro ingyenes, 60 napos próbaverziójára. Ehelyett a belső webhelyre irányítjuk őket, ha a licencek beszerzésével kapcsolatos információkat szeretnének – mind az ingyenes, mind a Pro verzió esetén.

![Megjelenik a Súgóinformációk közzététele beállítás.](media/admin-tenant-settings/publish-get-help-information.png)

## <a name="manage-risk"></a>A kockázatok kezelése

### <a name="receive-email-notification-service-outages-or-incidents"></a>E-mail-értesítések fogadása szolgáltatásbeli kimaradásokról vagy incidensekről

E-mailben kaphat értesítést, ha a bérlőt szolgáltatáskimaradás vagy valamilyen incidens érinti. Így proaktív módon reagálhat az incidensekre.

Javasoljuk, hogy kapcsolja be az **E-mail-értesítések fogadása szolgáltatásbeli kimaradásokról vagy incidensekről** beállítást. Ez a **Súgó- és támogatási beállítások** csoportban található. Rendeljen hozzá egy vagy több _levelezési_ biztonsági csoportot.

![Megjelenik az „E-mail-értesítések fogadása szolgáltatásbeli kimaradásokról vagy incidensekről” beállítás.](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>Information Protection

Az Information protection kötelezővé teszi a védelmi beállítások – például a titkosítás vagy a vízjelek – érvényesítését, amikor adatokat exportálnak a Power BI szolgáltatásból.

Az információvédelemmel kapcsolatban két bérlői beállítás van. Alapértelmezés szerint mindkét beállítás le van tiltva a teljes szervezet számára.

Javasoljuk, hogy engedélyezze ezeket a beállításokat, ha bizalmas adatokat kell kezelnie és védelemmel ellátni. További információt az [Adatvédelem a Power BI-ban](../admin/service-security-data-protection-overview.md) című cikkben talál.

### <a name="create-workspaces"></a>Munkaterületek létrehozása

Korlátozhatja, hogy a felhasználók létrehozhatnak-e munkaterületeket. Így szabályozhatja, hogy a szervezeten belül mi hozható létre.

> [!NOTE]
> Jelenleg átmeneti időszak van érvényben a régi és az új munkaterület között. Ez a bérlői beállítás csak az új felületre vonatkozik.

A **Munkaterületek létrehozása** beállítás alapértelmezés szerint engedélyezve van a teljes szervezet számára. Ezt a **Munkaterület beállításai** csoportban találja.

Javasoljuk, hogy rendeljen hozzá egy vagy több biztonsági csoportot. Ezeknek a csoportoknak engedélyezheti _vagy letilthatja_ a munkaterületek létrehozásának lehetőségét.

Ügyeljen arra, hogy a dokumentációban utasítások is szerepeljenek, amelyek alapján a felhasználók (akik nem rendelkeznek munkaterület-létrehozási jogokkal) megtudhatják, hogyan kérhetnek új munkaterületet.

![Megjelenik a „Munkaterületek létrehozása” beállítás.](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>Tartalom megosztása külső felhasználókkal

A felhasználók a szervezeten kívüli személyekkel is megoszthatják a jelentéseket és az irányítópultokat.

A **Tartalom megosztása külső felhasználókkal** beállítás alapértelmezés szerint engedélyezve van a teljes szervezet számára. Ezt az **Exportálási és megosztási beállítások** csoportban találja meg.

Javasoljuk, hogy rendeljen hozzá egy vagy több biztonsági csoportot. Ezeknek a csoportoknak engedélyezheti _vagy letilthatja_ a tartalom külső felhasználókkal való megosztását.

![Megjelenik a „Tartalom megosztása külső felhasználókkal” beállítás.](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>Webes közzététel

A [Webes közzététel](../service-publish-to-web.md) funkció lehetővé teszi a nyilvános jelentések weben történő közzétételét. Ha nem megfelelően használják, fennáll a veszélye, hogy a bizalmas információk elérhetővé válnak az interneten.

A **Webes közzététel** beállítás alapértelmezés szerint engedélyezve van a teljes szervezet számára, de a nem rendszergazda felhasználók nem hozhatnak létre beágyazási kódokat. Ezt az **Exportálási és megosztási beállítások** csoportban találja meg.

Ha engedélyezve van, javasoljuk, hogy rendeljen hozzá egy vagy több biztonsági csoportot. Ezeknek a csoportoknak engedélyezheti _vagy letilthatja_ a jelentések közzétételének lehetőségét.

Továbbá lehetőség van a beágyazási kódok működésének kiválasztására is. Alapértelmezés szerint a **Csak meglévő kódok engedélyezése** van beállítva. Ez azt jelenti, hogy a felhasználóknak fel kell venniük a kapcsolatot egy Power BI-rendszergazdával új beágyazási kód létrehozásához.

![Megjelenik a „Webes közzététel” beállítás.](media/admin-tenant-settings/publish-to-web.png)

Javasoljuk továbbá, hogy rendszeresen tekintse át a [webes közzététel beágyazási kódjait](https://app.powerbi.com/admin-portal/embedCodes) is. Távolítsa el azokat a kódokat, amelyek személyes vagy bizalmas adatok közzétételét eredményeznék.

### <a name="export-data"></a>Adatok exportálása

Korlátozhatja a felhasználókat abban, hogy adatokat exportáljanak az irányítópult csempéiből vagy a jelentések vizualizációiból.

Az **Adatok exportálása** beállítás alapértelmezés szerint engedélyezve van a teljes szervezet számára. Ezt az **Exportálási és megosztási beállítások** csoportban találja meg.

Javasoljuk, hogy rendeljen hozzá egy vagy több biztonsági csoportot. Ezeknek a csoportoknak engedélyezheti _vagy letilthatja_ a jelentések közzétételének lehetőségét.

> [!IMPORTANT]
> Ha letiltja ezt a beállítást, akkor korlátozza az [Elemzés az Excelben](../service-analyze-in-excel.md) és a Power BI szolgáltatás [élő kapcsolatok](../desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management) funkcióit is.

![Megjelenik az „Adatok exportálása” beállítás.](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> Ha a felhasználók engedélyezik felhasználóknak az adatexportálást, hozzáadhat egy védelmi réteget az [adatvédelem](../admin/service-security-data-protection-overview.md) kényszerítésével. Ha konfigurálva van, a jogosulatlan felhasználók számára le lesz tiltva a bizalmas címkékkel rendelkező tartalmak exportálása.

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat

Lehetőség van arra, hogy a külső vendégfelhasználók szerkeszthessék és kezeljék a Power BI-tartalmakat. További információt a [Power BI tartalmak terjesztése Azure AD B2B külső vendégfelhasználóknak](../service-admin-azure-ad-b2b.md) című témakörben talál.

Az **Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat** beállítás alapértelmezés szerint le van tiltva a teljes szervezet számára. Ezt az **Exportálási és megosztási beállítások** csoportban találja meg.

Ha a külső felhasználók számára engedélyezni szeretné a tartalmak szerkesztését és kezelését, javasoljuk, hogy rendeljen hozzá egy vagy több biztonsági csoportot. Ezeknek a csoportoknak engedélyezheti _vagy letilthatja_ a jelentések közzétételének lehetőségét.

![Megjelenik az „Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat” beállítás.](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>Fejlesztői beállítások

A [Power BI-tartalom beágyazásával](../developer/embedded/embedding.md) kapcsolatban két bérlői beállítás érhető el. Ezek a következők:

- Tartalom beágyazása alkalmazásokban (alapértelmezés szerint engedélyezve van)
- A Power BI API-k használatának engedélyezése szolgáltatásneveknek (alapértelmezés szerint le van tiltva)

Ha nem tervezi használni a fejlesztői API-kat a tartalmak beágyazásához, javasoljuk, hogy tiltsa le őket. Vagy legalább állítson be olyan biztonsági csoportokat, amelyek ezt elvégzik.

![Megjelennek a fejlesztői beállítások.](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>További lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Mit jelent a Power BI-felügyelet?](../service-admin-administering-power-bi-in-your-organization.md)
- [A Power BI felügyelete a felügyeleti portálon](../service-admin-portal.md)
- Kérdései vannak? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com)
