---
title: Ütemezett frissítés beállítása
description: Ez a cikk az átjáró kiválasztásának és az ütemezett frissítés beállításának lépéseit tartalmazza.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/06/2019
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: cc0527d093118fdb585800d0038f824223098119
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81675699"
---
# <a name="configure-scheduled-refresh"></a>Ütemezett frissítés beállítása

>[!NOTE]
>Két havi inaktivitás után az adatkészlet ütemezett frissítése szünetel. További információt a cikk egy későbbi részében, az [*Ütemezett frissítés*](#scheduled-refresh) című szakaszban talál.

Ez a cikk ismerteti mind a [(privát) helyszíni adatátjáró](service-gateway-personal-mode.md), mind a [helyszíni adatátjáró](service-gateway-onprem.md) esetében az ütemezett frissítéshez rendelkezésre álló beállításokat. A frissítési opciókat a Power BI szolgáltatás következő területein határozhatja meg: **Átjárókapcsolat**, az **Adatforrás hitelesítő adatai** és a **Frissítés ütemezése**. Sorban mindegyiket meg fogjuk vizsgálni. Az adatfrissítésre, többek között a frissítések ütemezésére vonatkozó további információért olvassa le az [Adatfrissítés](refresh-data.md#data-refresh) szakaszt.

Az **Ütemezett frissítés** képernyőre való váltáshoz tegye a következőt:

1. Válassza a navigációs ablaktáblán az **Adatkészletek** szakaszban listázott adathalmaz melletti **További beállítások** (...) lehetőséget.
2. Válassza a **Frissítés ütemezése** lehetőséget.

    ![Frissítés ütemezése](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Átjárókapcsolat

Itt eltérő beállításokkal találkozhat, attól függően, hogy az interneten személyes vagy vállalati átjáró érhető-e el.

Ha nem érhető el átjáró, akkor az **Átjárókapcsolat** le van tiltva. A személyes átjáró telepítésének módját ismertető üzenet is látható.

![Az átjáró nincs konfigurálva](media/refresh-scheduled-refresh/gateway-not-configured.png)

Ha rendelkezik konfigurált személyes átjáróval, és az online állapotú, akkor kiválasztható. Ha nem áll rendelkezésre, akkor offline állapotúként jelenik meg.

![Átjárókapcsolat](media/refresh-scheduled-refresh/gateway-connection.png)

A nagyvállalati átjárót is kiválaszthatja, ha az a rendelkezésére áll. Csak akkor fog rendelkezésre álló nagyvállalati átjárót látni, ha a fiókja szerepel az adott átjáróhoz konfigurált adatforrás **Felhasználók** lapján.

## <a name="data-source-credentials"></a>Adatforráshoz tartozó hitelesítő adatok

### <a name="power-bi-gateway---personal"></a>Személyes Power BI-átjáró

Ha a személyes átjárót használja az adatok frissítésére, meg kell adnia a háttéradatforráshoz való kapcsolódásra használt hitelesítő adatokat. Ha online szolgáltatásból kapcsolódott egy tartalomcsomaghoz, a kapcsolódáshoz megadott hitelesítő adatokat a rendszer az ütemezett frissítéshez is felhasználja.

![Adatforráshoz tartozó hitelesítő adatok](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

Az adatforrásokba csak az első alkalommal kell bejelentkeznie, amikor a frissítési funkciót használja az adatkészleten. Miután megadta a hitelesítő adatokat, azok megőrződnek az adatkészlettel.

> [!NOTE]
> Bizonyos hitelesítési módszereknél, ha az adatforrásba való bejelentkezésre használt jelszó lejár vagy megváltozik, akkor azt az adatforrásnál is meg kel változtatnia az **Adatforrás hitelesítő adataiban**.

Ha nem jó mennek a dolgok, a problémát általában az okozza, hogy az átjáró offline állapotú, mert nem tud bejelentkezni a Windowsba és nem tudja elindítani a szolgáltatást, vagy a Power BI nem tud bejelentkezni az adatforrásokba a frissített adatok lekérdezéséhez. Ha nem sikerül a frissítés, ellenőrizze az adatkészlet beállításait. Ha az átjárószolgáltatás offline állapotú, a hibát az **Állapot** területen tekintheti meg. Ha a Power BI nem tud bejelentkezni az adatforrásokba, akkor hiba jelenik meg az Adatforrás azonosító adatai területen.

### <a name="on-premises-data-gateway"></a>Helyszíni adatátjáró

Ha a Helyszíni adatátjárót használja az adatok frissítésére, akkor nem kell hitelesítő adatokat megadnia, mert azokat az átjáró rendszergazdája határozta meg az adatforráshoz.

![Frissítés ütemezése parancs](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> Ha helyszíni SharePointhoz csatlakozik adatfrissítéshez, a Power BI csak az *Anonim*, az *Alapvető* és a *Windows (NTLM/Kerberos)* hitelesítési módszereket támogatja. A Power BI nem támogatja sem az *ADFS*, sem az *űrlapalapú hitelesítési* módszereket a helyszíni SharePoint-adatforrások adatainak frissítéséhez.

## <a name="scheduled-refresh"></a>Ütemezett frissítés

Az **Ütemezett frissítés** szakaszban határozhatja meg az adatkészlet frissítésének gyakoriságát és időszakait. Egyes adatforrásokhoz nem szükséges frissítéshez konfigurálható átjáró, másokhoz azonban kötelező.

A beállítások megadásához a **Tartsa adatait naprakészen** csúszkát a **bekapcsolt** értékre kell beállítani.

> [!NOTE]
> A cél az, hogy a frissítés az ütemezett időponttól legfeljebb 15 perc eltéréssel elinduljon, de akár egyórás késés is előfordulhat, ha a szolgáltatás nem tudja korábban lefoglalni a szükséges erőforrásokat.

![Ütemezett frissítés párbeszédpanel](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Két havi inaktivitás után az adatkészlet ütemezett frissítése szünetel. Az adatkészlet akkor számít inaktívnak, ha egyetlen felhasználó sem látogatott meg az adatkészleten alapuló egyetlen irányítópultot és jelentést sem. Ekkor az adatkészlet tulajdonosa egy e-mailt kap az ütemezett frissítés szüneteltetéséről. Ekkor az adatkészlet ütemezett frissítése **letiltott** állapotúként jelenik meg. Az ütemezett frissítés folytatásához egyszerűen látogasson el bármelyik, az adatkészleten alapuló irányítópultra vagy jelentéshez.

## <a name="whats-supported"></a>Mik támogatottak?


> [!NOTE]
> Az ütemezett frissítés négy egymást követő hiba után is automatikusan le lesz tiltva.

Bizonyos adatkészletek ütemezett frissítése eltérő átjárók esetében támogatott. Az alábbi referencia alapján megértheti, milyen lehetőségek vannak.

### <a name="power-bi-gateway---personal"></a>Személyes Power BI-átjáró

**Power BI Desktop**

* A Power BI Desktop **Adatok lekérése** és Lekérdezésszerkesztő területein látható összes online adatforrás.
* A Power BI Desktop **Adatok lekérése** és Lekérdezésszerkesztő területein látható összes helyszíni adatforrás a Hadoop-fájl (HDFS) és a Microsoft Exchange kivételével.

**Excel**

* Minden online adatforrás megjelenik az Excelhez készült Microsoft Power Queryben.
* Minden helyszíni adatforrás megjelenik a Power Queryben a Hadoop-fájlokat (HDFS) és a Microsoft Exchange-t kivéve.
* Minden online adatforrás megjelenik a Power Pivotban.
* Minden helyszíni adatforrás megjelenik a Power Pivotban a Hadoop-fájlokat (HDFS) és a Microsoft Exchange-t kivéve.

> [!NOTE]
> Az Excel 2016-os vagy újabb verziójában a Power Query a menüszalag **Adatok** lapfülén található az **Adatok beolvasása és átalakítása** szakaszban.

### <a name="power-bi-gateway"></a>Power BI-átjáró

A támogatott adatforrásokra vonatkozó információért tekintse meg a [Power BI-adatforrások](power-bi-data-sources.md) szakaszt.

## <a name="troubleshooting"></a>Hibaelhárítás
Néha az adatok frissítése nem a várt módon történik. Ezt általában egy átjáróval kapcsolatos hiba okozza. Az átjáró-hibaelhárítással kapcsolatos cikkekben találja az eszközöket és az ismert hibákat.

- [A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)
- [A személyes Power BI Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Következő lépések

- [Adatfrissítés a Power BI-ban](refresh-data.md)  
- [Power BI Gateway – Personal](service-gateway-personal-mode.md)  
- [Helyszíni adatátjáró (személyes mód)](service-gateway-onprem.md)  
- [A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
- [A személyes Power BI Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)