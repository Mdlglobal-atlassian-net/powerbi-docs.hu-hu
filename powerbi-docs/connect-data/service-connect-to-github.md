---
title: Csatlakozás a GitHubhoz a Power BI használatával
description: A Power BI-hoz készült GitHub
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 2d5a2f319753323dd391cf6f5dceb970de1720b5
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83693325"
---
# <a name="connect-to-github-with-power-bi"></a>Csatlakozás a GitHubhoz a Power BI használatával
Ez a cikk bemutatja, hogyan kérhet le adatokat a GitHub-fiókjáról egy Power BI-sablonalkalmazással. A sablonalkalmazás egy irányítópulttal, több jelentéssel, és egy adathalmazzal rendelkező munkaterületet, amely segítségével elemezheti és megismerheti a GitHub-adatokat. A Power BI-hoz készült GitHub alkalmazással betekintést nyerhet GitHub-adattárakba, amelyek hozzájárulásokra, problémákra, lekéréses kérelmekre és aktív felhasználókra vonatkozó adatokat tartalmaznak.

![GitHub-sablonalkalmazás](media/service-connect-to-github/service-github-app-report.png)

A sablonalkalmazás telepítése után módosíthatja az irányítópultot és a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

Csatlakozzon a [GitHub-sablonalkalmazáshoz](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github), vagy olvasson még arról, hogy miképpen jön létre [a GitHub integrációja](https://powerbi.microsoft.com/integrations/github) a Power BI szolgáltatással.

Kipróbálhatja a [GitHub-oktatóanyagot](service-tutorial-connect-to-github.md)is. Ez valós, a Power BI-dokumentáció nyilvános adattárairól szóló GitHub-adatokat telepít.

>[!NOTE]
>A sablonalkalmazás használatához a GitHub-fióknak hozzá kell férnie az adattárhoz. A követelményekről alább talál további információkat.
>
>Ez a sablonalkalmazás nem támogatja a GitHub Enterprise-t.

## <a name="install-the-app"></a>Az alkalmazás telepítse

1. Az alkalmazás beszerzéséhez kattintson a következő hivatkozásra: [GitHub-sablonalkalmazás](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)

1. Az alkalmazás AppSource-oldalán válassza az [**AZONNALI BESZERZÉS**](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github) lehetőséget.

    [![GitHub-sablonalkalmazás az AppSource-on](media/service-connect-to-github/service-github-template-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)

1. Válassza az **Install** (Telepítés) lehetőséget. 

    ![A GitHub-sablonalkalmazás telepítése](media/service-connect-to-github/service-regional-emergency-response-select-install.png)

    A telepítést követően megtekintheti az alkalmazást az Alkalmazások oldalon.

   ![GitHub-alkalmazás az alkalmazások oldalon](media/service-connect-to-github/service-github-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Kapcsolódás adatforrásokhoz

1. Az alkalmazás megnyitásához kattintson az Alkalmazás oldalon lévő ikonra.

1. A kezdőképernyőn válassza az **Alkalmazás felfedezése** lehetőséget.

   ![Sablonalkalmazás üdvözlőképernyője](media/service-connect-to-github/service-github-app-splash-screen.png)

   Ekkor az alkalmazás megnyílik és mintaadatokat jelenít meg.

1. Kattintson az **Adatok csatlakoztatása** hivatkozásra az oldal tetején látható szalagcímen.

   ![GitHub-alkalmazás – csatlakozás az adatkapcsolathoz](media/service-connect-to-github/service-github-app-connect-data.png)

1. A megjelenő párbeszédpanelen adja meg az adattár nevét és tulajdonosát. A [paraméterek fellelhetőségével](#FindingParams) kapcsolatos információt lásd alább. Ha befejezte, kattintson a **Tovább** elemre.

   ![Power BI – GitHub adattár neve](media/service-connect-to-github/power-bi-github-app-tutorial-connect.png)

1. Az ekkor megjelenő párbeszédpanelen állítsa be az **OAuth2** hitelesítési módszert. Az adatvédelmi szint beállításával nem kell foglalkoznia. Amikor elkészült, kattintson az **Bejelentkezés** gombra.

   ![A Power BI GitHubos hitelesítési módszere](media/service-connect-to-github/power-bi-github-authentication.png)

1. Adja meg a GitHub-hitelesítő adatait, és kövesse a GitHub hitelesítési folyamatát. (Ha már bejelentkezett a böngészőjében, akkor lehet, hogy ez a lépés kimarad).

   ![A Power BI GitHubos hitelesítési módszere](media/service-connect-to-github/power-bi-github-authenticate-process.png)


Miután bejelentkezett, a jelentés csatlakozik az adatforrásokhoz, és naprakész adatokkal töltődik fel. Eközben forog a tevékenységfigyelő.

![A Power BI GitHub-alkalmazás frissítése folyamatban van](media/service-connect-to-github/service-github-app-refresh-monitor.png)

A jelentés adatai naponta egyszer automatikusan frissülnek, kivéve, ha letiltotta ezt a bejelentkezési folyamat során. Lehetőség van [a frissítési ütemezés beállítására](./refresh-scheduled-refresh.md) is, hogy szükség szerint frissen tartsa a jelentésadatokat.

## <a name="customize-and-share"></a>Testreszabás és megosztás

Az alkalmazás testre szabásához és megosztásához kattintson a lap jobb felső sarkában található ceruza ikonra.

![Alkalmazás szerkesztése](media/service-template-apps-install-distribute/power-bi-template-app-edit-app.png)


További információk a munkaterületen lévő elemek szerkesztéséről:
* [A Power BI jelentésszerkesztőjének bemutatása](../create-reports/service-the-report-editor-take-a-tour.md)
* [A Power BI szolgáltatás alapfogalmai tervezők számára](../fundamentals/service-basic-concepts.md)

Ha végzett a munkaterületi elemeken végrehajtani kívánt módosításokkal, már készen áll az alkalmazás közzétételére és megosztására. Ennek módjáról az [Alkalmazás közzététele](../collaborate-share/service-create-distribute-apps.md#publish-your-app) szakaszban tájékozódhat.

## <a name="whats-included-in-the-app"></a>Az alkalmazás tartalma
A GitHubból az alábbi adatok érhetők el a Power BI szolgáltatásban:     

| Table name (Táblázat neve) | Description (Leírás) |
| --- | --- |
| Közreműködések |A hozzájárulások táblázata a hozzájárulóktól származó összes kiegészítést, törlést és véglegesítést tartalmazza heti összesítésben. A táblázatban az első 100 hozzájáruló szerepel. |
| Issues (Problémák) |Listázza a kijelölt adattárban szereplő összes problémát, továbbá olyan adatokat, mint a problémák megoldására fordított összes és átlagos idő, az összes nyitott probléma és az összes megoldott probléma. A táblázat üres, ha nincsenek problémák az adattárban. |
| Pull requests (Lekéréses kérelmek) |Ebben a táblázatban szerepel az adattár összes lekéréses kérelme és a kérelmezők neve. Számított adatokat is tartalmaz, mint például a nyitott és a lezárt lekéréses kérelmek száma, az összes lekéréses kérelem, az egyes kérelmek lekéréséhez szükséges idő és az átlagos kérelemlekérési idő. A táblázat üres, ha nincsenek problémák az adattárban. |
| Felhasználók |Ez a táblázat azokat a GitHub-felhasználókat és -közreműködőket tartalmazza, akik közreműködtek, vagy lekéréses kérelmeket iktattak vagy oldottak meg a kiválasztott adattárban. |
| Milestones (Mérföldkövek) |A kiválasztott adattár összes mérföldkövét tartalmazza. |
| DateTable (Dátumtáblázat) |Ez a táblázat a mai dátumtól kezdve akár több évre is visszamenőleg tartalmazza a dátumokat, amelyek segítségével dátum szerint elemezheti GitHub-adatait. |
| ContributionPunchCard (Közreműködői pontgyűjtés) |Ez a táblázat közreműködők pontgyűjtésének vezetésére használatható a kijelölt adattárban. A hozzájárulásokat nap és időpont szerint jeleníti meg. Ez a tábla nem kapcsolódik a modell többi táblájához. |
| RepoDetails (Adattár adatai) |Ez a táblázat a kiválasztott adattár adatait tartalmazza. |

## <a name="system-requirements"></a>System requirements (Rendszerkövetelmények)
* A GitHub-fiók, amely hozzáfér az adattárhoz.  
* Engedély megadása a GitHubhoz készült Power BI alkalmazásnak az első bejelentkezéskor. Az engedély visszavonásának módját alább találja.  
* Elegendő API-hívás az adatok lekéréséhez és frissítéséhez.
>[!NOTE]
>Ez a sablonalkalmazás nem támogatja a GitHub Enterprise-t.

### <a name="de-authorize-power-bi"></a>A Power BI engedélyének visszavonása
Ha vissza szeretné vonni a Power BI-nak a GitHub-adattár elérésére kiadott engedélyt, ezt a GitHubban teheti meg. További információt ebben a [GitHub súgótémakörben](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) talál.

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Paraméterek helye
A tulajdonos és az adattár közvetlenül az adattárból állapítható meg a GitHubban:

![Az adattár neve és tulajdonosa](media/service-connect-to-github/github_ownerrepo.png)

Az első rész, az „Azure” a tulajdonos, a második rész, az „azure-sdk-for-php” pedig maga az adattár.  Ugyanez a két elem megtalálható az adattár URL-jében is:

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Hibaelhárítás
Ha szükséges, ellenőrizheti a GitHub-hitelesítő adatait.  

1. Egy másik böngészőablakban navigáljon a GitHub weboldalára, és jelentkezzen be. Ha bejelentkezett, azt a GitHub oldalának jobb felső sarkában láthatja.    
2. A GitHub webhelyen navigáljon annak az adattárnak az URL-címére, amelyet el kíván érni a Power BI-ból. Például: https://github.com/dotnet/corefx.  
3. A Power BI-ba visszatérve próbáljon csatlakozni a GitHubhoz. A GitHub beállítása párbeszédpanelen adja meg a szóban forgó adattár nevét és tulajdonosát.  

## <a name="next-steps"></a>További lépések

* [Oktatóanyag: Csatlakozás GitHub-adattárhoz a Power BI segítségével](service-tutorial-connect-to-github.md)
* [Új munkaterületek létrehozása a Power BI-ban](../collaborate-share/service-create-the-new-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](../consumer/end-user-apps.md)
* [Csatlakozás külső szolgáltatások Power BI-alkalmazásaihoz](service-connect-to-services.md)
* Kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
