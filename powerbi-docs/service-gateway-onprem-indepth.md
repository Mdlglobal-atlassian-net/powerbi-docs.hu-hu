---
title: Helyszíni adatátjáró – részletesen
description: Ez a cikk a helyszíni adatátjárót ismerteti részletesen. Kitér a szolgáltatás és az Azure Active Directory, valamint a helyszíni Active Directory közötti együttműködésre az Analysis Services használata során.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 18458820f98bcea32eb5288389d57808646d462c
ms.sourcegitcommit: 91ac6185f7026ddbaa925dc54057bb742b4fa411
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2019
ms.locfileid: "56325014"
---
# <a name="on-premises-data-gateway-in-depth"></a>Helyszíni adatátjáró – részletesen
Cége felhasználói hozzáférhetnek a helyszíni adatokhoz (amelyekhez már van hozzáférési jogosultságuk), de ahhoz, hogy ezek a felhasználók az Ön helyszíni adatforrásához kapcsolódjanak, helyszíni adatátjáró telepítésére és konfigurálására van szükség. Az átjáró gyors és biztonságos háttérbeli kommunikációt biztosít a felhőbeli felhasználótól az Ön helyszíni adatforrásáig és vissza a felhő felé.

Az átjárók telepítését és konfigurálását általában rendszergazdák végzik. Szükség lehet hozzá a helyszíni kiszolgálók alapos ismeretére és bizonyos esetekben kiszolgáló-rendszergazdai jogosultságokra is.

Ez a cikk nem vezeti végig lépésenként az átjáró telepítésén és konfigurálásán. Erről mindenképpen olvassa el a [Helyszíni adatátjáró](service-gateway-onprem.md) című cikket. Ez a cikk az átjáró működésének alapos megértését hivatott elősegíteni. Tárgyalja az Azure Active Directory és az Analysis Services felhasználónév-kezelését és biztonságát, valamint azt, hogy hogyan biztosítja a felhőszolgáltatás a helyszíni adatokhoz való kapcsolódás és a lekérdezések biztonságát a felhasználó által a bejelentkezéshez használt e-mail-cím, az átjáró és az Active Directory használatával.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Bejelentkezési fiók
A felhasználók munkahelyi vagy iskolai fiókjukkal jelentkeznek be. Ez az Ön céges fiókja. Ha feliratkozott egy Office 365-ajánlatra, és nem adta meg a tényleges munkahelyi e-mail-címét, lehetséges, hogy így fog kinézni a cím: nancy@contoso.onmicrosoft.com. A felhőszolgáltatásban lévő fiókját egy Azure Active Directory-bérlő tárolja. Az AAD-fiókjához tartozó egyszerű felhasználónév a legtöbb esetben megegyezik ezzel az e-mail-címmel.

## <a name="authentication-to-on-premises-data-sources"></a>Hitelesítés helyszíni adatforrásoknál
Az átjáróból a helyszíni adatforrásokhoz való kapcsolódás tárolt hitelesítő adatok használatával történik, kivéve az Analysis Services esetében. Az átjáró a felhasználó személyétől függetlenül a tárolt hitelesítő adatokat használja a csatlakozáshoz.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Hitelesítés élő Analysis Services-adatforrásnál
Valahányszor a felhasználó kapcsolatba lép az Analysis Servicesszel, az érvényes felhasználóneve adódik át az átjárónak, majd tovább a helyszíni Analysis Services-kiszolgálónak. Az egyszerű felhasználónév (UPN), általában a felhőbe való bejelentkezéshez használt e-mail-cím lesz átadva az Analysis Servicesnek érvényes felhasználónévként. Az egyszerű felhasználónév a csatlakozás EffectiveUserName tulajdonságában adódik át. Ennek az e-mail-címnek egyeznie kell egy, a helyszíni Active Directory-tartományban megadott egyszerű felhasználónévvel. Az egyszerű felhasználónév az Active Directory-fiókok egyik tulajdonsága. A kiszolgálóhoz való hozzáféréshez ennek a Windows-fióknak benne kell lennie egy Analysis Services-szerepkörben. A bejelentkezés sikertelen lesz, ha nincs egyező találat az Active Directoryban.

Az Analysis Services szűrést is képes végezni az adott fiók alapján. A szűrés történhet szerepköralapú vagy sorszintű biztonsággal.

## <a name="role-based-security"></a>Szerepköralapú biztonság
A modellek a felhasználói szerepkörök alapján gondoskodnak a biztonságról. Az egy adott modell-projekthez tartozó szerepkörök definiálása a szerzői szakaszban, az SQL Server Data Tools – Business Intelligence (SSDT-BI) használatával, vagy a modell telepítése után, az SQL Server Management Studio (SSMS) használatával történik. A szerepkörök a Windows-felhasználói név vagy Windows-csoport szerint tárolják tagjaikat. A szerepkörök határozzák meg egy felhasználó engedélyeit a modellen végzett lekérdezésekre vagy műveletekre. A felhasználók többsége olvasási engedéllyel rendelkező szerepkörhöz tartozik. A további, rendszergazdáknak szánt szerepkörök elemek feldolgozására és adatbázis-funkciók vagy más szerepkörök kezelésére is jogosultak.

## <a name="row-level-security"></a>Sorszintű biztonság
A sorszintű biztonság csak az Analysis Services sorszintű biztonságára vonatkozik. A modellek dinamikus, sorszintű biztonságot is nyújthatnak. A felhasználókat tartalmazó legalább egy szerepkörrel ellentétben a dinamikus biztonság nem követelmény a táblázatos modellek esetében. A magas szintű dinamikus biztonság egy adott táblázat adott sorának szintjéig meghatározza egy felhasználó adatolvasási jogosultságát. A szerepkörökhöz hasonlóan a dinamikus sorszintű biztonság is a felhasználó Windows-felhasználónevén múlik.

Azt, hogy egy felhasználó lekérdezheti és megtekintheti-e a modell adatait, elsősorban a szerepkör határozza meg, amelynek a Windows-felhasználói fiókja a tagja, másodszor pedig a dinamikus sorszintű biztonság, ha konfigurálva van.

A szerepkörök és a dinamikus sorszintű biztonság megvalósítása a modellekben meghaladja e cikk kereteit.  Erről további információt talál az MSDN [Szerepkörök (táblázatos SSAS)](https://msdn.microsoft.com/library/hh213165.aspx) és [Biztonsági szerepkörök (Analysis Services - többdimenziós adatok)](https://msdn.microsoft.com/library/ms174840.aspx) című cikkeiben. A táblázatos modellek biztonságának legrészletesebb tárgyalását a letölthető [A táblázatos BI szemantikus modell biztosítása](https://msdn.microsoft.com/library/jj127437.aspx) című tanulmányban olvashatja.

## <a name="what-about-azure-active-directory"></a>Mi az Azure Active Directory szerepe?
A Microsoft-felhőszolgáltatások az [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) használatával hitelesítik a felhasználókat. Az Azure Active Directory a felhasználóneveket és biztonsági csoportokat tartalmazó bérlő. A felhasználó által a bejelentkezéshez használt e-mail-cím általában megegyezik a fiók egyszerű felhasználónevével.

Mi az én helyszíni Active Directorym szerepe?

Az Analysis Services csak akkor tudja meghatározni, hogy egy kapcsolódó felhasználó olyan szerepkör tagja-e, amely jogosult az adatok olvasására, ha a kiszolgáló konvertálja az AAD-ból az átjárónak majd onnan az Analysis Services-kiszolgálónak átadott érvényes felhasználónevet. Az Analysis Services-kiszolgáló átadja az érvényes felhasználónevet egy Windows Active Directory-tartományvezérlőnek (DC). Az Active Directory-tartományvezérlő ellenőrzi, hogy az érvényes felhasználónév létezik-e egy helyi fiók egyszerű felhasználóneveként, majd visszaadja az adott felhasználó Windows-felhasználónevét az Analysis Services-kiszolgálónak.

Az EffectiveUserName tulajdonság nem használható nem tartományba léptetett Analysis Services-kiszolgálón. A bejelentkezési hibák elkerülése érdekében az Analysis Services-kiszolgálót be kell léptetni egy tartományba.

## <a name="how-do-i-tell-what-my-upn-is"></a>Hogyan állapíthatom meg az egyszerű felhasználónevemet?
Előfordulhat, hogy nem tudja az UPN-jét, és az is lehet, hogy Ön nem tartományi rendszergazda. Munkaállomásán a következő parancs kiadásával állapíthatja meg a fiókjához tartozó egyszerű felhasználónevet.

    whoami /upn

Az eredmény e-mail-címre hasonlíthat, de ez a helyszíni tartományi fiók egyszerű felhasználóneve. Ha Analysis Services-adatforrást használ élő kapcsolatokhoz, akkor ennek egyeznie kell azzal, amelyet az átjáró az EffectiveUserName tulajdonságban ad át.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Felhasználónevek és Analysis Services-adatforrások egymáshoz rendelése
A Power BI lehetővé teszi a felhasználónevek és az Analysis Services-adatforrások egymáshoz rendelését. Szabályokat konfigurálhat a Power BI-ba bejelentkezett felhasználónevek és az Analysis Services-kapcsolat EffectiveUserName tulajdonságaként átadott nevek egymáshoz rendeléséhez. A felhasználónevek egymáshoz rendelése kitűnő kerülő megoldás amikor a helyi Active Directoryban nincs az AAD-beli felhasználónevével megegyező egyszerű felhasználónév. Ha az e-mail-címe például nancy@contoso.onmicrsoft.com, akkor hozzárendelheti a nancy@contoso.com címet és ez lesz átadva az átjárónak. A [felhasználónevek egymáshoz rendeléséről](service-gateway-enterprise-manage-ssas.md#map-user-names) további információk is rendelkezésére állnak.

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Helyszíni Active Directory szinkronizálása az Azure Active Directoryval
Élő Analysis Services-kapcsolatok használatához előnyös, ha a helyi Active Directory-beli fiókok egyeznek az Azure Active Directory-beliekkel. Ugyanúgy, ahogyan az egyszerű felhasználóneveknek egyezniük kell a fiókokban.

A felhőszolgáltatások csak az Azure Active Directoryn belüli fiókokat érik el. Hiába ad hozzá fiókot a helyi Active Directoryhoz, ha az nem létezik az AAD-ben, akkor nem használható. A helyi Active Directory-fiókok és az Azure Active Directory egyeztetése több módon is megoldható.

1. Hozzáadhat fiókokat az Azure Active Directoryhoz manuálisan.
   
   Létrehozhat egy fiókot az Azure Portalon vagy az Office 365 felügyeleti portálon, amelynek a neve egyezik a helyi Active Directory-fiók egyszerű felhasználónevével.
2. Használhatja az [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) eszközt az Azure Active Directory-bérlő és a helyi fiókok szinkronizálására.
   
   Az Azure AD Connect eszköz beállításokat tesz elérhetővé a címtár-szinkronizáláshoz és a hitelesítés beállításához, többek között jelszókivonat-szinkronizálást, átmenő hitelesítést és összevonást. Ha Ön nem bérlői vagy helyi tartományi rendszergazda, akkor ennek konfigurálásához fel kell vennie a kapcsolatot a rendszergazdával.

Az Azure AD Connect használata biztosítja, hogy egyszerű felhasználónév egyezését az AAD és a helyszíni Active Directory között.

> [!NOTE]
> A fiókok Azure AD Connect használatával történő szinkronizálása új fiókokat hoz létre az AAD-bérlőjén belül.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>Itt jut szerephez az átjáró
Az átjáró hídként szolgál a felhő és a helyszíni kiszolgáló között. A felhő és az átjáró közötti adatátvitel biztonságát az [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) garantálja. A Service Bus az átjáró egy kimenő kapcsolatán keresztül biztonságos csatornát hoz létre a felhő és a helyszíni kiszolgáló között.  A helyszíni tűzfalon egy kimenő kapcsolatot sem kell megnyitnia. A Power BI kezeli a Service Bust az Ön számára, tehát nincsenek további költségek, sem konfigurációs lépések, amelyeket végre kellene hajtani.

Analysis Services-adatforrás használata esetén a az átjárót olyan számítógépre kell telepítenie, amely az Analysis Services-kiszolgálóval közös erdőbe/tartományba van beléptetve.

Minél közelebb van az átjáró a kiszolgálóhoz, annál gyorsabb a kapcsolat. Az átjáró és a kiszolgáló közötti hálózati késés kiküszöbölése érdekében a legjobb, ha az átjárót az adatforrással közös kiszolgálóra tudja telepíteni.

## <a name="what-to-do-next"></a>Hogyan tovább?
Az átjáró telepítése után az átjáróhoz tartozó adatforrások telepítése következik. Adatforrásokat az **Átjárók kezelése** képernyőn adhat hozzá. További információkat talál az adatforrások kezelésével foglalkozó cikkekben.

[Adatforrások kezelése – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Az adatforrás kezelése – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Adatforrások kezelése – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Adatforrások kezelése – Oracle](service-gateway-onprem-manage-oracle.md)  
[Adatforrások kezelése – Importálás és ütemezett frissítés](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Hibalehetőségek
Előfordul, hogy az átjáró telepítése sikertelen. Az is lehetséges, hogy az átjáró telepítése látszólag sikeres, de a szolgáltatás továbbra sem tudja használni. Ennek sok esetben egyszerű oka van, például az átjáró által az adatforrásba való bejelentkezéshez használt hitelesítő adatok hibás jelszava.

Más esetekben a felhasználók által a bejelentkezéshez használt e-mail-címek típusával van probléma, vagy az Analysis Services nem tudja feloldani az érvényes felhasználónevet. Olykor az is problémákat okozhat, ha több tartománya van, köztük megbízhatósági kapcsolatokkal, és az átjáró az egyikben, az Analysis Services pedig egy másikban van.

A hibaelhárítási kérdéseket nem itt tárgyaljuk, hanem egy külön cikkben írtuk össze a lépésenkénti hibaelhárítás menetét: [A helyszíni adatátjáró hibaelhárítása](service-gateway-onprem-tshoot.md). Bízunk benne, hogy Ön nem ütközik problémákba. Ha mégis, akkor a rendszer működésének ismerete és a hibaelhárításról szóló cikk segíthet.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Következő lépések

[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
[Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview/)  
[Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis/)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

