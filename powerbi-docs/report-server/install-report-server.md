---
title: "A Power BI jelentéskészítő kiszolgáló telepítése"
description: "Ismerje meg, hogyan telepítheti a Power BI jelentéskészítő kiszolgálót. "
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/29/2018
ms.author: maghan
ms.openlocfilehash: 340e4a79e4ab0950143ea1af4f1c9a1f9c54b64c
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/30/2018
---
# <a name="install-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgáló telepítése

Ismerje meg, hogyan telepítheti a Power BI jelentéskészítő kiszolgálót.

 **Letöltés** ![letöltés](media/install-report-server/download.png "letöltés")

A Power BI jelentéskészítő kiszolgáló letöltéséhez látogasson el a [Power BI jelentéskészítő kiszolgálóval végzett helyszíni jelentéskészítéssel](https://powerbi.microsoft.com/report-server/) foglalkozó oldalra. 

A Microsoft letöltőközpontjában töltse le a [Microsoft Power BI Desktopot](https://go.microsoft.com/fwlink/?linkid=861076) [a Power BI jelentéskészítő kiszolgálóra (2017. október) optimalizálva].

![tipp](media/install-report-server/fyi-tip.png "tipp") A legfrissebb információkért tekintse meg a [Power BI jelentéskészítő kiszolgáló kibocsátási megjegyzéseit](release-notes.md).

<iframe width="640" height="360" src="https://www.youtube.com/embed/zacaEb9A4F0?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Előkészületek
A Power BI jelentéskészítő kiszolgáló telepítése előtt javasoljuk, hogy tekintse át a [Power BI jelentéskészítő kiszolgáló telepítésének hardver- és szoftverkövetelményeit](system-requirements.md).

### <a name="power-bi-report-server-product-key"></a>Power BI jelentéskészítő kiszolgáló termékkulcsa
#### <a name="power-bi-premium"></a>Power BI Premium
Ha a Power BI Premiumot vásárolta meg, a Power BI Felügyeleti portál **Premium beállítások** lapján érheti el a Power BI jelentéskészítő kiszolgáló termékkulcsát. Ez csak a globális rendszergazdák és a Power BI szolgáltatás azon felhasználói számára érhető el, akikhez rendszergazdai szerepkört rendeltek.

![](../media/service-admin-premium-manage/pbirs-product-key.png "A Power BI jelentéskészítő kiszolgáló kulcsa a Premium-beállításokon belül")

Ha rákattint a **Power BI jelentéskészítő kiszolgáló termékkulcsa** elemre, a termékkulcs megjelenik egy párbeszédpanelben. Innen lemásolhatja és felhasználhatja a telepítéshez.

![](../media/service-admin-premium-manage/pbirs-product-key-dialog.png "A Power BI jelentéskészítő kiszolgáló termékkulcsa")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Enterprise Frissítési Garancia (SA)
Ha SQL Server Enterprise Frissítési Garancia szerződése van, a termékkulcsot a [Mennyiségi licencszolgáltatási központban](https://www.microsoft.com/Licensing/servicecenter/) érheti el.

## <a name="install-your-report-server"></a>A jelentéskészítő kiszolgáló telepítése
A Power BI jelentéskészítő kiszolgáló telepítése nagyon egyszerű. Csupán néhány lépést kell megtennie a fájlok telepítéséhez.

> [!NOTE]
> A telepítés során nincs szükség elérhető SQL Server adatbázismotor-kiszolgálóra. Csak telepítés után, a Reporting Services konfigurálásához kell majd használnia.
> 
> 

1. Keresse meg a PowerBIReportServer.exe fájlt, és indítsa el a telepítőt.
2. Kattintson a **Power BI jelentéskészítő kiszolgáló telepítése** elemre.
   
    ![A Power BI jelentéskészítő kiszolgáló telepítése](media/install-report-server/pbireportserver-install.png)
3. Válassza ki a telepítendő kiadást, majd kattintson a **Tovább** elemre.
   
    ![Kiadás választása](media/install-report-server/pbireportserver-choose-edition.png)
   
    A legördülő menüből az Evaluation Editiont (próbaverzió) vagy a Developer Editiont (fejlesztői verzió) választhatja.
   
    ![](media/install-report-server/pbireportserver-choose-edition2.png)
   
    A másik lehetőség, hogy a kiszolgálóhoz megadja azt a termékkulcsot, amelyet a Power BI szolgáltatástól vagy a Mennyiségi licencszolgáltatási központtól kapott. A termékkulcs beszerzéséhez az [Előkészületek](#before-you-begin) című részben talál további információkat.
4. Olvassa el és fogadja el a licencfeltételeket, majd kattintson a **Tovább** elemre.
   
    ![Licencfeltételek](media/install-report-server/pbireportserver-eula.png)
5. A jelentéskészítő kiszolgáló adatbázisának tárolásához elérhető adatbázismotorra van szüksége. Ha csak a jelentéskészítő kiszolgálót kívánja telepíteni, kattintson a **Tovább** elemre.
   
    ![Csak fájltelepítés](media/install-report-server/pbireportserver-install-files-only.png)
6. Adja meg a jelentéskészítő kiszolgáló telepítési helyét. A folytatáshoz kattintson a **Telepítés** elemre.
   
    ![Telepítési útvonal megadása](media/install-report-server/pbireportserver-install-file-path.png)
   
   > [!NOTE]
   > Az alapértelmezett útvonal: C:\Program Files\Microsoft Power BI Report Server.
   > 
   > 
7. Sikeres telepítés után kattintson a **Jelentéskészítő kiszolgáló konfigurálása** lehetőségre a Reporting Services konfigurációkezelő indításához.
   
    ![A jelentéskészítő kiszolgáló konfigurálása](media/install-report-server/pbireportserver-configure.png)

## <a name="configuration-your-report-server"></a>A jelentéskészítő kiszolgáló konfigurálása
Ha a telepítőben rákattint a **Jelentéskészítő kiszolgáló konfigurálása** elemre, megjelenik a Reporting Services konfigurációkezelő. További információkért tekintse meg a [Reporting Services konfigurációkezelő](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode) oldalt.

A Reporting Services kezdeti konfigurációjának befejezéséhez [hozzon létre egy adatbázist a jelentéskészítő kiszolgáló számára](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database). A lépés végrehajtásához SQL Server adatbázis-kiszolgáló szükséges.

### <a name="creating-a-database-on-a-different-server"></a>Adatbázis létrehozása más kiszolgálón
Ha a jelentéskészítő kiszolgáló adatbázisát egy másik gépen futó adatbázis-kiszolgálón hozza létre, akkor a jelentéskészítő kiszolgáló szolgáltatásfiókját olyan hitelesítő adatokkal kell módosítania, amelyeket az adatbázis-kiszolgáló felismer. 

A jelentéskészítő kiszolgáló alapértelmezés szerint a virtuális szolgáltatásfiókot használja. Ha másik kiszolgálón kísérli meg az adatbázis létrehozását, a Kapcsolódási jogok alkalmazása lépés során a következő hibaüzenetet kaphatja:

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

A hiba megoldása érdekében a szolgáltatásfiókot Hálózati szolgáltatásfiókra vagy tartományi fiókra módosíthatja. A szolgáltatásfiók Hálózati szolgáltatásfiókra történő módosítása a jelentéskészítő kiszolgálóhoz tartozó számítógépfiók környezetében alkalmazza a jogokat.

![A jelentéskészítő kiszolgáló szolgáltatásfiókjának konfigurálása](media/install-report-server/pbireportserver-configure-account.png)

További információkért lásd: [A jelentéskészítő kiszolgáló szolgáltatásfiókjának konfigurálása](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager).

## <a name="windows-service"></a>Windows-szolgáltatás
A telepítés során létrejön egy Windows-szolgáltatás, amely **Power BI jelentéskészítő kiszolgáló** néven jelenik meg. A szolgáltatás neve **PowerBIReportServer**.

![Jelentéskészítő kiszolgáló Windows-szolgáltatás](media/install-report-server/pbireportserver-windows-service.png)

![A Jelentéskészítő kiszolgáló Windows-szolgáltatás tulajdonságai](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>Alapértelmezett URL-foglalások
Az URL-foglalások előtagból, állomásnévből, portból és virtuális könyvtárból állnak:

| Rész | Leírás |
| --- | --- |
| Előtag |Az alapértelmezett előtag a HTTP. Ha korábban már telepített Secure Sockets Layer (SSL) tanúsítványt, a Telepítő megkísérel HTTPS-előtagot használó URL-foglalásokat létrehozni. |
| Állomásnév |Az alapértelmezett állomásnév egy erős helyettesítő (+). Azt határozza meg, hogy a jelentéskészítő kiszolgáló a kijelölt porton bármilyen HTTP-kérelmet elfogad a számítógéphez rendelt bármely állomásnévhez, beleértve a következőket: `http://<computername>/reportserver`, `http://localhost/reportserver` vagy `http://<IPAddress>/reportserver.` |
| Port |Az alapértelmezett port a 80-as. Ha a 80-astól eltérő portot használ, explicit módon kell azt hozzáadnia az URL-hez, amikor a böngészőablakban megnyitja a webes portált. |
| Virtuális könyvtár |Alapértelmezés szerint a virtuális könyvtárak mind a Jelentéskészítő kiszolgáló webszolgáltatáshoz, mind a webes portálhoz készült jelentésekhez a ReportServer formátumában jönnek létre. A Jelentéskészítő kiszolgáló webszolgáltatás alapértelmezett virtuális könyvtára a **reportserver**. A webes portál alapértelmezett virtuális könyvtára a **reports**. |

A teljes URL-sztring például a következő lehet:

* `http://+:80/reportserver`, hozzáférést biztosít a jelentéskészítő kiszolgálóhoz.
* `http://+:80/reports`, hozzáférést biztosít a webes portálhoz.

## <a name="firewall"></a>Tűzfal
Ha távoli gépről éri el a jelentéskészítő kiszolgálót, érdemes ellenőriznie, hogy tűzfal jelenléte esetén beállította-e a tűzfalszabályzatokat.

Nyissa meg a webszolgáltatás és a webes portál URL-címére konfigurált TCP-portot. Alapértelmezés szerint ezek az URL-címek a 80-as TCP-portra vannak konfigurálva.

## <a name="additional-configuration"></a>További konfigurálás
* Ahhoz, hogy a jelentéseket rögzíthesse a Power BI-irányítópulton, konfigurálnia kell a Power BI szolgáltatással történő integrációt az [Integráció a Power BI szolgáltatással](https://docs.microsoft.com/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager) című témakörben leírtak szerint.
* Az előfizetés-feldolgozási levelezés konfigurálásához lásd a [Levelezési beállítások](https://docs.microsoft.com/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager) és az [E-mailek kézbesítése a jelentéskészítő kiszolgálón](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services) témaköröket.
* Ha úgy szeretné konfigurálni a webes portált, hogy egy jelentéskészítő számítógépről hozzáférve jelentéseket tekinthessen meg és kezelhessen rajta, tekintse meg a [Tűzfal beállítása a jelentéskészítő kiszolgáló eléréséhez](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access) és a [Jelentéskészítő kiszolgáló beállítása távoli felügyelethez](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration) című témaköröket.

## <a name="next-steps"></a>További lépések
[Rendszergazdai kézikönyv](admin-handbook-overview.md)  
[A jelentéskészítő kiszolgáló termékkulcsának megkeresése](find-product-key.md)  
[A Power BI jelentéskészítő kiszolgálóra optimalizált Power BI Desktop telepítése](install-powerbi-desktop.md)  
[A Reporting Services telepítésének ellenőrzése](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[A jelentéskészítő kiszolgáló szolgáltatásfiókjának konfigurálása](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[A jelentéskészítő kiszolgáló URL-címeinek konfigurálása](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[A jelentéskészítő kiszolgáló adatbázis-kapcsolatának konfigurálása](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[Jelentéskészítő kiszolgáló inicializálása](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[SSL-kapcsolatok konfigurálása a jelentéskészítő kiszolgálón](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Windows-szolgáltatásfiókok és -engedélyek konfigurálása](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[A Power BI jelentéskészítő kiszolgáló böngészőtámogatása](browser-support.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

