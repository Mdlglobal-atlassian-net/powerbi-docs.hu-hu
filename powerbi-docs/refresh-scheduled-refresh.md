---
title: Ütemezett frissítés beállítása
description: Ez a cikk az átjáró kiválasztásának és az ütemezett frissítés beállításának lépéseit tartalmazza.
author: mgblythe
manager: kfile
ms.reviewer: kayu''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/06/2019
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 46f61d2fcce21e3f8e6dae83c32457414928faee
ms.sourcegitcommit: 206806d8ddb6bdfc322c1a46fb34a1b0678acba2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816581"
---
# <a name="configure-scheduled-refresh"></a>Ütemezett frissítés konfigurálása

>[!NOTE]
>Két havi inaktivitás után az adatkészlet ütemezett frissítése szünetel. További információt a cikk egy későbbi részében, az [*Ütemezett frissítés*](#scheduled-refresh) című szakaszban talál.
>
>

Ha az adatkészlet támogatja a **Frissítés most** és a **Frissítés ütemezése** használatával történő ütemezett frissítést, van néhány követelmény és beállítás, amelyek fontosak a sikeres frissítéshez. Ezek az **Átjárókapcsolat**, az **Adatforrás hitelesítő adatai** és a **Frissítés ütemezése**. Most vizsgáljuk meg közelebbről mindegyiket.

Ez a cikk ismerteti mind a [(privát) helyszíni adatátjáró](service-gateway-personal-mode.md), mind a [helyszíni adatátjáró](service-gateway-onprem.md) esetében rendelkezésre álló beállításokat.

A **Ütemezett frissítés** képernyőre való váltáshoz tegye a következőt:

1. Kattintson az **Adatkészletek** alatt található egyik adatkészlet melletti **három pontra (...)** .
2. Válassza a **Frissítés ütemezése** lehetőséget.

    ![Frissítés ütemezése](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Átjárókapcsolat
Itt eltérő beállításokkal találkozhat, attól függően, hogy az interneten személyes vagy vállalati átjáró érhető-e el.

Ha nem érhető el átjáró, akkor az **Átjárókapcsolat** le van tiltva. A személyes átjáró telepítésének módját ismertető üzenet is látható.

![Az átjáró nincs konfigurálva](media/refresh-scheduled-refresh/gateway-not-configured.png)

Ha rendelkezik beállított személyes átjáróval, és az online állapotú, akkor kiválasztható. Ha nem áll rendelkezésre, akkor offline állapotúként jelenik meg.

![Átjárókapcsolat](media/refresh-scheduled-refresh/gateway-connection.png)

A nagyvállalati átjárót is kiválaszthatja, ha az a rendelkezésére áll. Csak akkor fog rendelkezésre álló nagyvállalati átjárót látni, ha a fiókja szerepel az adott átjáróhoz konfigurált adatforrás **Felhasználók** lapján.

## <a name="data-source-credentials"></a>Adatforráshoz tartozó hitelesítő adatok
### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personal
Ha a személyes átjárót használja az adatok frissítésére, meg kell adnia a háttéradatforráshoz való kapcsolódásra használt hitelesítő adatokat. Ha online szolgáltatásból kapcsolódott egy tartalomcsomaghoz, a kapcsolódáshoz megadott hitelesítő adatokat a rendszer az ütemezett frissítéshez is felhasználja.

![Adatforráshoz tartozó hitelesítő adatok](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

Az adatforrásokba csak az első alkalommal kell bejelentkeznie, amikor a frissítési funkciót használja az adatkészleten. Miután megadta a hitelesítő adatokat, azok megőrződnek az adatkészlettel.

> [!NOTE]
> Bizonyos hitelesítési módszereknél, ha az adatforrásba való bejelentkezésre használt jelszó lejár vagy megváltozik, akkor azt az adatforrásnál is meg kel változtatnia az **Adatforrás hitelesítő adataiban**.
>
>

Ha nem jó mennek a dolgok, a problémát általában az okozza, hogy az átjáró offline állapotú, mert nem tud bejelentkezni a Windowsba és nem tudja elindítani a szolgáltatást, vagy a Power BI nem tud bejelentkezni az adatforrásokba a frissített adatok lekérdezéséhez. Ha nem sikerül a frissítés, ellenőrizze az adatkészlet beállításait. Ha az átjárószolgáltatás offline állapotú, a hibát az **Állapot** területen tekintheti meg. Ha a Power BI nem tud bejelentkezni az adatforrásokba, akkor hiba jelenik meg az Adatforrás azonosító adatai területen.

### <a name="on-premises-data-gateway"></a>Helyszíni adatátjáró
Ha a Helyszíni adatátjárót használja az adatok frissítésére, akkor nem kell hitelesítő adatokat megadnia, mert azokat az átjáró rendszergazdája határozta meg az adatforráshoz.

![Frissítés ütemezése parancs](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> Ha helyszíni SharePointhoz csatlakozik adatfrissítéshez, a Power BI csak az *Anonim*, az *Alapvető* és a *Windows (NTLM/Kerberos)* hitelesítési módszereket támogatja. A Power BI nem támogatja sem az *ADFS*, sem az *űrlapalapú hitelesítési* módszereket a helyszíni SharePoint-adatforrások adatainak frissítéséhez.
>
>

## <a name="scheduled-refresh"></a>Ütemezett frissítés
Az **Ütemezett frissítés** szakaszban határozhatja meg az adatkészlet frissítésének gyakoriságát és időszakait. Egyes adatforrásokhoz nem szükséges frissítéshez konfigurálható átjáró, másokhoz azonban kötelező.

A beállítások megadásához a **Tartsa adatait naprakészen** csúszkát a **bekapcsolt** értékre kell beállítani.

> [!NOTE]
> A Power BI szolgáltatás az ütemezett frissítési időponthoz képest **15 percen** belül kezdeményezi a frissítést.
>
>

![Ütemezett frissítés párbeszédpanel](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Két havi inaktivitás után az adatkészlet ütemezett frissítése szünetel. Az adatkészlet akkor számít inaktívnak, ha egyetlen felhasználó sem látogatott meg az adatkészleten alapuló egyetlen irányítópultot és jelentést sem. Ekkor az adatkészlet tulajdonosa egy e-mailt kap az ütemezett frissítés szüneteltetéséről, és az adatkészlet frissítési ütemezése **letiltott** állapotúként jelenik meg. Az ütemezett frissítés folytatásához egyszerűen látogasson el bármelyik, az adatkészleten alapuló irányítópultra vagy jelentéshez.
>
>

## <a name="whats-supported"></a>Mi támogatott?
Bizonyos adatkészletek ütemezett frissítése eltérő átjárók esetében támogatott. Az alábbi referencia alapján megértheti, milyen lehetőségek vannak.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personal
**Power BI Desktop**

* A Power BI Desktop **Adatok lekérése** és Lekérdezésszerkesztő területein látható összes online adatforrás.
* A Power BI Desktop **Adatok lekérése** és Lekérdezésszerkesztő területein látható összes helyszíni adatforrás a Hadoop-fájl (HDFS) és a Microsoft Exchange kivételével.

**Excel**

> [!NOTE]
> Az Excel 2016-os vagy újabb verziójában a Power Query a menüszalag **Adatok** lapfülén található az **Adatok beolvasása és átalakítása** szakaszban.
>
>

* Minden online adatforrás megjelenik az Excelhez készült Microsoft Power Queryben.
* Minden helyszíni adatforrás megjelenik a Power Queryben a Hadoop-fájlokat (HDFS) és a Microsoft Exchange-t kivéve.
* Minden online adatforrás megjelenik a Power Pivotban.
* Minden helyszíni adatforrás megjelenik a Power Pivotban a Hadoop-fájlokat (HDFS) és a Microsoft Exchange-t kivéve.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

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

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

