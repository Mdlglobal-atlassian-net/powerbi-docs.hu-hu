---
title: Power BI-munkaterületcsoport tartalmainak migrálása a Power BI-ba
description: A cikk azt mutatja be, hogyan migrálhatja az adatokat a Power BI-munkaterületcsoportokból a Power BI Embeddedbe, és hogyan aknázhatja ki az alkalmazásokba való beágyazás nyújtotta fejlett lehetőségeket.
author: markingmyname
ms.author: maghan
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/30/2018
ms.openlocfilehash: 9901d5a60c0fe3127dada9523e659d48fbe7bf8b
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762191"
---
# <a name="how-to-migrate-power-bi-workspace-collection-content-to-power-bi-embedded"></a>Power BI-munkaterületcsoport tartalmainak migrálása a Power BI Embeddedbe

A cikk azt mutatja be, hogyan migrálhatja az adatokat a Power BI-munkaterületcsoportokból a Power BI Embeddedbe, és hogyan aknázhatja ki az alkalmazásokba való beágyazás nyújtotta fejlett lehetőségeket.

A Microsoft nemrégiben [bejelentette az új, kapacitásalapú Power BI Embedded licencelési modellt](https://powerbi.microsoft.com/blog/power-bi-embedded-capacity-based-skus-coming-to-azure/), amelynek segítségével a felhasználók rugalmasabban érhetik el, oszthatják meg és terjeszthetik a tartalmakat. Az ajánlat emellett növeli a méretezhetőséget és a teljesítményt.

A Power BI Embeddeddel a tartalmak (például irányítópultok, átjárók és alkalmazás-munkaterületek) beágyazásához egyetlen egységes API-felület, konzisztens funkciókészlet és a Power BI legújabb szolgáltatásai használhatók. A továbbiakban lehetősége van a Power BI Desktopban elkezdeni a munkát, az üzembe helyezést pedig elvégezheti a Power BI Embedded használatával.

A jelenlegi Power BI-munkaterületcsoport már csak korlátozott ideig lesz elérhető. Nagyvállalati Szerződéssel rendelkező ügyfelek szerződésük lejáratáig kapnak hozzáférést hozzá, míg azok, akik a Direkt vagy CSP-csatornákon keresztül szerezték be a Power BI-munkaterületcsoportokat, a Power BI Embedded általános megjelenésétől számított egy évig férhetnek hozzá a munkaterület-csoportokhoz.  A cikk útmutatást ad a Power BI-munkaterületcsoportok migrálásához az új Power BI Embeddedbe, valamint tájékoztatást nyújt az alkalmazás várható változásairól.

> [!IMPORTANT]
> Bár a migrálás függőséget jelent a Power BI Embeddedtől, az alkalmazást használó ügyfelekre **beágyazási token** használata esetén nem vonatkozik Power BI-függőség. Nem kell bejelentkezniük a Power BI szolgáltatásba a beágyazott tartalmak megtekintéséhez az alkalmazásban. Ezzel a beágyazási megközelítéssel kiszolgálhatja az Embedded nem Power BI-felhasználóit.

![Beágyazási folyamat](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

Mielőtt megkezdené az új Power BI Embedded szolgáltatásba való migrálást, gyorsan áttekintheti a részletes útmutatót, amely segítségével beállíthatja az új Power BI Embedded-környezetet a [beágyazáshoz szükséges telepítési eszközzel](https://aka.ms/embedsetup).

Válassza ki az Ön számára megfelelő megoldást:
* **Beágyazás az ügyfelek számára** – ha olyan megoldásra van szüksége, melyben [az adatok tulajdonosa az alkalmazás (app owns data)](https://aka.ms/embedsetup/AppOwnsData). Amennyiben az [ügyfelei számára végez beágyazást](embedding.md#embedding-for-your-customers), irányítópultokat és jelentéseket ágyazhat be olyan felhasználók számára, akik nem rendelkeznek Power BI-fiókkal. 

* **Beágyazás a cég számára** – ha olyan megoldásra van szüksége, melyben [az adatok tulajdonosa a felhasználó (user owns data)](https://aka.ms/embedsetup/UserOwnsData). Amennyiben [a cég számára végzi a beágyazást](embedding.md#embedding-for-your-organization), kibővítheti a Power BI szolgáltatást.

## <a name="prepare-for-the-migration"></a>Előkészületek a migráláshoz

A Power BI-munkaterület-csoport Power BI Embeddedbe való migrálásának előkészítéséhez néhány dolgot végre kell hajtania. Szükség lesz egy elérhető bérlőre, valamint egy Power BI Pro licenccel rendelkező felhasználóra.

1. Bizonyosodjon meg róla, hogy rendelkezésre áll egy Azure Active Directory (Azure AD) bérlő.

    Meg kell határoznia, hogy milyen bérlőbeállítást használ.

   * A meglévő vállalati Power BI-bérlőt használja?
   * Külön bérlőt használ az alkalmazáshoz?
   * Külön bérlőt használ mindegyik ügyfélhez?

     Ha új bérlőt hozna létre az alkalmazáshoz vagy egyenként az ügyfelekhez, tekintse meg az [Azure Active Directory-bérlő létrehozásával](create-an-azure-active-directory-tenant.md) vagy [Azure AD-bérlő beszerzésével](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant) kapcsolatos cikket.
2. Hozzon létre egy felhasználót ezen az új bérlőn, amely a alkalmazás „fő” fiókjaként fog szolgálni. A fióknak fel kell iratkoznia a Power BI-ra, és rendelkeznie kell egy Power BI Pro licenccel.

## <a name="accounts-within-azure-ad"></a>Az Azure AD-ben lévő fiókok

A következő fiókoknak létezniük kell a bérlőn.

> [!NOTE]
> Ezeknek a fiókoknak Power BI Pro licenccel kell rendelkezniük, hogy használhassák az alkalmazás-munkaterületet.

1. Egy bérlői rendszergazda felhasználó.

    Javasoljuk, hogy ez a felhasználó a beágyazás céljával létrehozott összes alkalmazás-munkaterület tagja legyen.

2. A tartalmat létrehozó elemzők fiókjai.

    Ezeket a felhasználókat igény szerint hozzá kell rendelni az alkalmazás-munkaterületekhez.

3. Az alkalmazás *fő* felhasználói vagy Embedded-fiókja.

    A fiók hitelesítő adatait az alkalmazások háttérrendszere tárolja majd és használja az Azure AD-token beszerzéséhez a Power BI API-k használatához. A rendszer ennek a fióknak a használatával hozza létre a beágyazási tokent az alkalmazáshoz. A fióknak a beágyazáshoz létrehozott alkalmazás-munkaterületeken is rendszergazdai jogosultsággal kell rendelkeznie.

> [!NOTE]
> Ez csak a szervezet egy normál felhasználói fiókja, amely beágyazási célokra lesz használva.

## <a name="app-registration-and-permissions"></a>Alkalmazásregisztráció és -engedélyek

Az alkalmazásokat regisztrálni kell az Azure AD-ben, és bizonyos engedélyeket kell biztosítani a számukra.

### <a name="register-an-application"></a>Egy alkalmazás regisztrálása

A REST API-hívások indításához az alkalmazásokat regisztrálni kell az Azure AD-ben. Ehhez be kell jelentkeznie az Azure Portalra, és további konfigurációs beállításokat kell tennie a Power BI alkalmazásregisztrációs oldalán megadottak mellett. További információkért lásd: [Azure AD alkalmazás regisztrálása Power BI-tartalmak beágyazásához](register-app.md).

Az alkalmazást annak **fő** fiókjával kell regisztrálni.

## <a name="create-app-workspaces-required"></a>Alkalmazás-munkaterületek létrehozása (kötelező)

Az alkalmazás-munkaterületek használatával nagyobb fokú elszigetelés érhető el, ha az alkalmazás több ügyfelet is kiszolgál. Az irányítópultok és a jelentések így ügyfelenként elkülöníthetőek. Ekkor alkalmazás-munkaterületenként külön Power BI-fiók használatával még jobban elszigetelheti az alkalmazásfelületeket az ügyfelek közt.

> [!IMPORTANT]
> Személyes munkaterületek használatával nem aknázhatja ki a nem Power BI-felhasználók számára való beágyazás kínálta előnyöket.

A Power BI alkalmazás-munkaterületek létrehozásához szükség van egy Pro licenccel rendelkező felhasználóra. Az alkalmazás-munkaterületet létrehozó Power BI-felhasználó alapértelmezés szerint az adott munkaterület rendszergazdájává válik.

> [!NOTE]
> Az alkalmazás *fő* fiókjának rendszergazdai jogosultsággal kell rendelkeznie a munkaterületen.

## <a name="content-migration"></a>Tartalommigrálás

A tartalmak migrálása a munkaterület-csoportokból a Power BI Embeddedbe az aktuális megoldással párhuzamosan végezhető, így nem okoz állásidőt.

A **migrálási eszköz** szabadon használható a Power BImunkaterületcsoportok tartalmának a Power BI Embeddedbe másolásához. Ez különösen akkor hasznos, ha sok tartalommal rendelkezik. További információ: [Power BI Embedded migrálási eszköz](migrate-tool.md).

A tartalommigrálás leginkább két API-n keresztül történik.

1. Download PBIX: ez az API a Power BI-ba 2016 októbere után feltöltött PBIX-fájlok letöltéséhez használható.
2. Import PBIX: ez az API bármilyen PBIX-fájl a Power BI-ba való feltöltéséhez használható.

Néhány kapcsolódó kódrészletért lásd: [Tartalmak a Power BI-munkaterületcsoportokból való migrálásához használható kódrészletek](migrate-code-snippets.md).

### <a name="report-types"></a>Jelentéstípusok

A jelentéseknek több típusa létezik, és mindegyikhez valamelyest eltérő migrálási folyamat szükséges.

#### <a name="cached-dataset--report"></a>Gyorsítótárazott adatkészlet és jelentés

Gyorsítótárazott adatkészletek alatt olyan PBIX-fájlokat értünk, amelyek élő vagy DirectQuery-kapcsolatok helyett importált adatokat tartalmaznak.

**Folyamat**

1. Hívja meg az Import PBIX API-t a PaaS-munkaterületről.
2. Mentse a PBIX-fájlt.
3. Hívja meg az Import PBIX API-t a SaaS-munkaterületre.

#### <a name="directquery-dataset--report"></a>DirectQuery-adatkészlet és -jelentés

**Folyamat**

1. Végezzen egy GET https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources hívást, és mentse az így kapott kapcsolati sztringet.
2. Hívja meg az Import PBIX API-t a PaaS-munkaterületről.
3. Mentse a PBIX-fájlt.
4. Hívja meg az Import PBIX API-t a SaaS-munkaterületre.
5. Kapcsolati sztring frissítése ezzel a hívással: POST https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections
6. GW-azonosító és adatforrás-azonosító lekérdezése ezzel a hívással: GET https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources
7. A felhasználó hitelesítő adatainak frissítése: PATCH https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}

#### <a name="old-dataset--reports"></a>Régi adatkészlet és jelentések

Ezek a 2016 októbere előtt létrehozott adatkészletek/jelentések. A PBIX-letöltés API nem támogatja a 2016 októbere előtt feltöltött PBIX-fájlokat

**Folyamat**

1. Töltse le a PBIX-fájlokat a fejlesztői környezetből (a belső forráskezelő környezetből).
2. Hívja meg az Import PBIX API-t a SaaS-munkaterületre.

#### <a name="push-dataset--report"></a>Leküldéses adatkészlet és jelentés

A PBIX-letöltés nem támogatja a *Push API* adatkészleteit. A Push API adatkészleteinek adatai nem portolhatóak PaaS-munkaterületekről SaaS-munkaterületekre.

**Folyamat**

1. Hívja meg a „Create dataset” (Adatkészlet létrehozása) API-t az adatkészlet JSON-fájljával az adatkészlet létrehozásához a SaaS-munkaterületen.
2. Állítsa újra össze a jelentést a létrehozott adatkészlethez*.

Bizonyos kerülő megoldásokkal lehetséges migrálni a Push API-val készített jelentéseket a PaaS- és a SaaS-munkaterületek közt. Ehhez próbálkozzon a következőkkel.

1. Töltsön fel néhány helyőrző PBIX-fájlt a PaaS-munkaterületre.
2. Klónozza a Push API-val készített jelentést, és kösse az 1. lépésben feltöltött helyőrző PBIX-fájlhoz.
3. Töltse le a Push API-val készített jelentést a helyőrző PBIX-fájllal.
4. Töltse fel a helyőrző PBIX-fájlt a SaaS-munkaterületre.
5. Hozza létre a leküldéses adatkészletet a SaaS-munkaterületen.
6. Kösse újra a jelentést a Push API-val készített adatkészlethez.

## <a name="create-and-upload-new-reports"></a>Új jelentések létrehozása és feltöltése

A Power BI-munkaterületcsoportokból migrált tartalmak mellett a Power BI Desktop használatával is létrehozhatja a jelentéseket és adatkészleteket, majd közzéteheti ezeket a jelentéseket egy alkalmazás-munkaterületen. A jelentéseket közzétevő végfelhasználónak Power BI Pro-licencre van szüksége az alkalmazás-munkaterületen történő közzétételhez.

## <a name="rebuild-your-application"></a>Az alkalmazás újrabuildelése

1. Power BI REST API-k használatához és a powerbi.com szolgáltatáson belüli jelentéshely megadásához módosítania kell az alkalmazást.
2. Buildelje újra az AuthN/AuthZ hitelesítést az alkalmazás *fő* fiókjának használatával. [Beágyazási token](https://docs.microsoft.com/rest/api/power-bi/embedtoken) használatával kiaknázhatja azt a lehetőséget, hogy ez a felhasználó a többi felhasználó nevében cselekedhet.
3. Ágyazza be a jelentéseket a powerbi.com helyről az alkalmazásba.

## <a name="map-your-users-to-a-power-bi-user"></a>A felhasználók leképezése Power BI-felhasználókra

Az alkalmazásban az abban kezelt felhasználókat leképezi egy, az alkalmazáshoz használható *fő* Power BI fiókra. A Power BI *fő* fiók hitelesítő adatait az alkalmazás tárolja, és beágyazási tokenek létrehozásához használja.

## <a name="what-to-do-when-you-are-ready-for-production"></a>Mi a teendő, ha készen áll az éles üzemeltetésre

Amikor kész átállni éles üzemre, a következőket kell tennie.

* Ha külön bérlőt használ a fejlesztéshez, gondoskodnia kell róla, hogy az alkalmazás-munkaterületek, valamint az irányítópultok és a jelentések elérhetők az éles környezetben. Arra is figyelnie kell, hogy az alkalmazást az Azure AD-ben az éles környezeti bérlőhöz hozza létre, és hozzárendelje a megfelelő alkalmazásjogosultságokat, amint azt az 1. lépés tárgyalja.
* Vásároljon az igényeinek megfelelő kapacitást. A [Power BI Embedded elemzési kapacitásának tervezésével kapcsolatos tanulmány](https://aka.ms/pbiewhitepaper) további információt tartalmaz a szükséges kapacitás mennyiségéről és típusairól. Kapacitást az Azure-ban [vásárolhat](https://portal.azure.com/#create/Microsoft.PowerBIDedicated).
* Az alkalmazás-munkaterületet a Speciális felületen módosíthatja és rendelheti hozzá a Premium kapacitásokhoz.

    ![Prémium-kapacitás](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity02.png)

* Helyezze üzembe a frissített alkalmazást az éles környezetben, és kezdje beágyazni a jelentéseket a Power BI Embeddedből.

## <a name="after-migration"></a>A migrálás után

Takarítson az Azure-ban.

* Távolítsa el a telepített megoldás összes már nem használt munkaterületét a Power BI-munkaterületcsoport Azure-szolgáltatásában.
* Törölje az Azure-ból az összes munkaterület-csoportot.

## <a name="next-steps"></a>További lépések

[Beágyazás a Power BI szolgáltatással](embedding.md)  
[Migrálási eszköz a Power BI-munkaterületcsoporthoz](migrate-tool.md)  
[Kódrészletek a tartalmak Power BI-munaterületcsoportból való migrálásához](migrate-code-snippets.md)  
[Power BI-irányítópultok, -jelentések és -csempék beágyazása](embedding-content.md)  
[Power BI Premium – pontosan mi is ez?](../service-premium.md)  
[JavaScript API Git-adattár](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git-adattár](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript beágyazási minta](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Munkaterület-csoportok elemzési kapacitásának tervezésével kapcsolatos tanulmány](https://aka.ms/pbiewhitepaper)  
[Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
