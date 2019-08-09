---
title: Az adatforrás kezelése – Oracle
description: A helyszíni adatátjáró és az átjáróhoz tartozó adatforrások kezelésének módja.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 3e3e51bf13a904e46552529d9131dbbb4665cb7d
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730238"
---
# <a name="manage-your-data-source---oracle"></a>A vállalati adatforrások kezelése – Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Amint [telepítette a helyszíni adatátjárót](/data-integration/gateway/service-gateway-install), [fel kell vennie az átjáróval használható adatforrásokat](service-gateway-data-sources.md#add-a-data-source). Ez a cikk bemutatja, hogyan lehet használni az átjárókat és az Oracle-adatforrásokat akár ütemezett frissítéshez, akár a DirectQueryhez.

## <a name="installing-the-oracle-client"></a>Az Oracle ügyfél telepítése

Ahhoz, hogy az átjáró csatlakozni tudjon az Oracle-kiszolgálóhoz, telepíteni és konfigurálni kell a .NET rendszer Oracle-adatszolgáltatóját (ODP.NET). Ez az Oracle Data Access Components (ODAC) része.

A Power BI Desktop **32 bites** verzióihoz a következő hivatkozással töltse le és telepítse a **32 bites** Oracle ügyfelet:

* [32 bites Oracle Data Access Components (ODAC) az Oracle Developer Tools for Visual Studio (12.1.0.2.4) verzióval](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

A Power BI Desktop **64 bites** verzióihoz vagy a helyszíni adatátjáróhoz a következő hivatkozással töltse le és telepítse a **64 bites** Oracle ügyfelet:

* [64 bites ODAC 12.2c 1-es kiadás (12.2.0.1.0) Windows x64 rendszerhez](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

A telepítés után a megfelelő információkkal konfigurálnia kell a tnsnames.ora fájlt az adatbázishoz megfelelő adatokkal. A Power BI Desktop és az átjáró nem a tnsnames.ora fájlban meghatározott net_service_name névvel rendelkezik. Ha ez nincs konfigurálva, nem fog tudni csatlakozni. A tnsnames.ora fájl alapértelmezett elérési útja a következő: `[Oracle Home Directory]\Network\Admin\tnsnames.ora`. A tnsnames.ora fájlok konfigurálásáról további információ: [Oracle: Helyi elnevezési paraméterek (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm).

### <a name="example-tnsnamesora-file-entry"></a>Példa tnsnames.ora fájlbejegyzés

A tnsname.ora fájlban lévő bejegyzések alapvető formátuma a következő.

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Íme egy példa a kitöltött kiszolgáló- és portinformációkra.

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>Adatforrások felvétele

Az [Adatforrás hozzáadása](service-gateway-data-sources.md#add-a-data-source) című témakörben további információt talál adatforrások hozzáadásáról. Az **Adatforrás típusaként** válassza az Oracle-t.

![Oracle-adatforrás hozzáadása](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Miután kiválasztotta az Oracle-t adatforrásként, ki kell töltenie az adatforrás adatait, többek között meg kell adnia a **Kiszolgálót** és az **Adatbázist**.  

**Hitelesítési módszert** is választania kell.  Ez **Windows** vagy **Alapszintű** lehet.  Akkor érdemes az **Alapszintűt** választani, ha Windows-hitelesítés helyett egy, az Oracle-ben létrehozott fiókot fog használni. Ezután írja be az adatforráshoz használni kívánt hitelesítő adatokat.

> [!NOTE]
> Az adatforrás felé irányuló összes lekérdezés ezen hitelesítő adatok segítségével fut. A [Titkosított hitelesítő adatok tárolása a felhőben](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud) című témakörben további információt talál a hitelesítő adatok tárolásáról.

![Adatforrás-beállítások kitöltése](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Miután minden információt megadott, válassza a **Hozzáadás** lehetőséget. Mostantól használhatja ezt az adatforrást az ütemezett frissítéshez vagy a DirectQueryhez egy helyszíni Oracle-kiszolgálóval. Ha sikerrel járt, megjelenik a *Sikeres csatlakozás* üzenet.

![A kapcsolat állapotának megjelenítése](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Speciális beállítások

Ha szeretné, konfigurálhatja az adatforrás adatvédelmi szintjét is. Ez vezérli, hogy hogyan lesznek egyesítve az adatok. Ez csak ütemezett frissítéshez használható. Mindez nem érvényes a DirectQueryre. Az adatforrás adatvédelmi szintjeiről az [Adatvédelmi szintek (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) című témakörben olvashat részletesebben.

![Az adatvédelem szintjének beállítása](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Az adatforrás használata

Miután létrehozta az adatforrást, használhatja DirectQuery-kapcsolatokkal vagy ütemezett frissítéssel is.

> [!WARNING]
> A kiszolgáló és az adatbázis nevének egyeznie kell a Power BI Desktopban és az adatforrásban a helyszíni adatátjárón belül.

Az adatkészlet és az adatforrás közötti kapcsolat az átjárón belül a kiszolgáló nevén és az adatbázis nevén alapul. Ezeknek egyezniük kell. Ha például egy IP-címet ad meg a kiszolgáló nevének, a Power BI Desktopban azt az IP-címet kell használnia az adatforráshoz az átjáró konfigurációján belül. Ennek a névnek egyeznie kell a tnsnames.ora fájlban meghatározott aliassal is. A tnsnames.ora fájlról további információ: [Az Oracle-ügyfél telepítése](#installing-the-oracle-client).

Ez a DirectQuery és az ütemezett frissítések esetén is igaz.

### <a name="using-the-data-source-with-directquery-connections"></a>Az adatforrás használata DirectQuery-kapcsolatokkal

Fontos, hogy a kiszolgáló és az adatbázis neve megegyezzen a Power BI Desktop és az átjáró számára konfigurált adatforrás között. Arra is ügyelnie kell, hogy a felhasználó szerepeljen az adatforrás **Felhasználók** lapján, ha DirectQuery-adatkészleteket szeretne közzétenni. A DirectQuery esetén a kiválasztásra az első adatimportáláskor kerül sor a Power BI Desktopon belül. A DirectQueryről további információt talál [A DirectQuery használata a Power BI-ban](desktop-use-directquery.md) című cikkben.

Miután elvégezte a közzétételt a Power BI Desktopból vagy az **Adatok lekérése** területről, el kell kezdeni működniük a jelentéseknek. Az átjárón belüli adatforrás létrehozása után több percbe telhet, amíg a kapcsolat használhatóvá válik.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Az adatforrás használata ütemezett frissítéssel

Ha szerepel az átjárón belül konfigurált adatforrás **Felhasználók** lapján, és a kiszolgáló és az adatbázis neve egyezik, az átjáró megjelenik lehetőségként az ütemezett frissítésnél.

![A felhasználók megjelenítése](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Hibaelhárítás

Több hibaüzenetet kaphat az Oracle-től, ha az elnevezési szintaxis helytelen vagy nincs megfelelően konfigurálva.

* ORA-12154: TNS: nem oldható fel a megadott csatlakozásazonosító  
* ORA-12514: A TNS figyelő jelenleg nem ismeri a csatlakozásleíróban kért szolgáltatást  
* ORA-12541: TNS: nincs figyelő  
* ORA-12170: TNS: kapcsolat-időtúllépés történt  
* ORA-12504: A TNS figyelő nem kapta meg a SERVICE_NAME nevet a CONNECT_DATA adatokban  

Ezek a hibák akkor fordulhatnak elő, ha az Oracle-ügyfél nincs telepítve, vagy ha nincs megfelelően konfigurálva. Ha telepítve van, ellenőrizze, hogy a tnsnames.ora fájl helyesen van-e konfigurálva, és hogy a megfelelő net_service_name nevet használja-e. Arra is ügyelnie kell, hogy a net_service_name egyezzen a Power BI Desktopot használó gép és az átjárót futtató gép között. További információ: [Az Oracle-ügyfél telepítése](#installing-the-oracle-client).

> [!NOTE]
> Az Oracle-kiszolgáló verziója és az Oracle-ügyfél verziója közötti kompatibilitás miatt is kaphat hibaüzenetet. Ezeknek általában egyezniük kell.

Az átjáróval kapcsolatos további hibaelhárítási információkért lásd: [A helyszíni adatátjáró hibaelhárítása](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Következő lépések

* [Átjárók hibaelhárítása – Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

