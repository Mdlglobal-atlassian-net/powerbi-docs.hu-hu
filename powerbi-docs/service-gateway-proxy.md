---
title: Helyszíni adatátjáró proxybeállításainak konfigurálása
description: Információk a helyszíni adatátjáró proxybeállításainak konfigurálásáról.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2122ce9bd6eb850a51a06188ca1c10faf78f4bb1
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964663"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Helyszíni adatátjáró proxybeállításainak konfigurálása
Munkakörnyezete megkövetelheti, hogy proxyn keresztül érje el az Internetet. Ez megakadályozhatja, hogy a helyszíni adatátjáró a szolgáltatáshoz kapcsolódjon.

## <a name="does-your-network-use-a-proxy"></a>Használ proxyt az Ön hálózata?
A superuser.com alábbi bejegyzése arról szól, hogy hogyan állapítható meg, használ-e proxyt az Ön hálózata.

[Honnan tudhatom, hogy milyen proxykiszolgálót használok? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>A konfigurációs fájl helye és az alapértelmezett konfiguráció
A proxyadatok egy .NET-es konfigurációs fájlban vannak beállítva. A fájl helye és neve a használt átjárótól függően változó.

### <a name="on-premises-data-gateway"></a>Helyszíni adatátjáró
A helyszíni adatátjáró konfigurációjában két fő fájl játszik szerepet.

**Konfiguráció**

Az első az átjáró konfigurálására használt konfigurációs képernyőhöz való. Ha az átjáró konfigurálásával van problémája, akkor ezt a fájlt kell megvizsgálnia.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Windows-szolgáltatás**

A második a Power BI szolgáltatással kommunikáló és a kérelmeket kezelő Windows-szolgáltatásé.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Proxybeállítások konfigurálása
Az alapértelmezett proxykonfiguráció a következő.

```
<system.net>
    <defaultProxy useDefaultCredentials="true" />
</system.net>
```


Az alapértelmezett konfiguráció Windows-hitelesítéssel működik. Ha az Ön proxyja másféle hitelesítési formát használ, akkor módosítania kell a beállításokat. Ha nem biztos a dolgában, forduljon a hálózati rendszergazdához. Az alapszintű proxyhitelesítés nem ajánlott, ha alapszintű proxyhitelesítést próbál használni, az proxyhitelesítési hibákat okozhat, aminek eredményeképpen az átjáró nem lesz megfelelően konfigurálva. A feloldáshoz használjon erősebb proxyhitelesítési módot.

Az alapértelmezett hitelesítő adatok használatán kívül hozzáadhat <proxy> elemet is, így részletesebben definiálhatja a proxykiszolgáló beállításait. Meghatározhatja például, hogy a helyszíni adatárjáró még a helyi erőforrásokhoz is mindig használja a proxyt, ha a bypassonlocal paramétert false (hamis) értékre állítja. Ez segíthet a hibakeresésben, ha a proxy naplófájljában nyomon szeretne követni minden olyan http-kérelmet, amely egy helyszíni adatátjáróról érkezik. Az alábbi konfigurációs példa meghatározza, hogy minden kérelemnek egy meghatározott, 192.168.1.10 IP-című proxyn keresztül kell áthaladnia.

```
<system.net>
    <defaultProxy useDefaultCredentials="true">
        <proxy  
            autoDetect="false"  
            proxyaddress="http://192.168.1.10:3128"  
            bypassonlocal="false"  
            usesystemdefault="true"
        />  
    </defaultProxy>
</system.net>
```

Ezen kívül ahhoz, hogy az átjáró csatlakozni tudjon a felhőbeli adatforrásokhoz proxyn keresztül, frissítse a következő fájlt: *C:\Program Files\On-premises data gateway\Microsoft.Mashup.Container.NetFX45.exe*. A fájlban bontsa ki a `<configurations>` szakaszt az alábbi tartalomhoz, majd frissítse a `proxyaddress` attribútumot a saját proxyadataival. Az alábbi példa az összes felhőbeli kérelmet egy meghatározott, 192.168.1.10 IP-című proxyn keresztül irányítja.

```
<configuration>
<system.net>
    <defaultProxy useDefaultCredentials="true" enabled="true">
    <proxy proxyaddress=""http://192.168.1.10:3128" bypassonlocal="true" />
    </defaultProxy>
</system.net>
</configuration>
```

A .NET-konfigurációs fájlok proxy elemeinek konfigurációjáról a [defaultProxy elem (hálózati beállítások)](https://msdn.microsoft.com/library/kd3cf2ex.aspx) című cikkből tájékozódhat.

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Az átjárószolgáltatás fiókjának módosítása egy tartományi felhasználóra
Ha a proxybeállításokat a fent ismertetett módon az alapértelmezett hitelesítő adatok használatára konfigurálja, akkor hitelesítési hibák merülhetnek fel. Ennek az az oka, hogy az alapértelmezett szolgáltatásfiók a szolgáltatás biztonsági azonosítója, nem pedig egy hitelesített tartományi felhasználó. A proxyn való megfelelő hitelesítés érdekében megváltoztathatja az átjáró szolgáltatásfiókját.

> [!NOTE]
> A kötelező jelszómódosítás elkerülése érdekében javasolt felügyelt szolgáltatásfiókot használni. Ismertető [felügyelt szolgáltatásfiók](https://technet.microsoft.com/library/dd548356.aspx) létrehozásáról az Active Directoryban.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Helyszíni adatátjáró szolgáltatásfiókjának módosítása
1. Cserélje ki a Windows-szolgáltatásfiókot a **helyszíni adatátjáró szolgáltatáséra**.

    Ennek a szolgáltatásnak az alapértelmezett fiókja az *NT SERVICE\PBIEgwService*. Ezt érdemes felváltani egy olyan tartományi felhasználófiókkal, amely az Ön Active Directory-tartományában található. A kötelező jelszómódosítás elkerülése érdekében esetleg érdemes lehet felügyelt szolgáltatásfiókot használni.

    A fiók cseréjét a Windows-szolgáltatás tulajdonságai között, a **Bejelentkezés** oldalon hajthatja végre.
2. Indítsa újra a **helyszíni adatátjáró-szolgáltatást**.

    Rendszergazdai parancssorból adja ki a következő parancsokat.

        net stop PBIEgwService

        net start PBIEgwService
3. Indítsa el a **helyszíni adatátjáró konfiguráló programját**. Kattintson a Start gombra, és keressen rá a *helyszíni adatátjáró* kifejezésre.
4. Jelentkezzen be a Power BI szolgáltatásba.
5. Állítsa helyre az átjárót a helyreállítási kulcs használatával.

    Ezzel teszi lehetővé, hogy az új szolgáltatásfiók visszafejtse az adatforrások eléréséhez szükséges tárolt hitelesítő adatokat.

> [!NOTE]
> Ha a szolgáltatásfiókot közvetlenül a Szolgáltatások vezérlőpulton módosítja, akkor az nem frissíti automatikusan a hozzáférés-vezérlési listákat. Gondoskodnia kell róla, hogy az új szolgáltatás fiók rendelkezzen hozzáféréssel a telepítési fájlokhoz és mappához. Az átjáró telepítési mappáját a C:\Program Files\On-premises data gateway elérési úton találja. 
> 

## <a name="next-steps"></a>Következő lépések
[Helyszíni adatátjáró (személyes mód)](service-gateway-personal-mode.md)
[Tűzfal-információk](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

