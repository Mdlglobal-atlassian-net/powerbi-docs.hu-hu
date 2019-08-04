---
title: Saját titkosítási kulcsok használata a Power BI-hoz (előzetes verzió)
description: Útmutató saját titkosítási kulcsok Power BI Premiumban való használatához.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2019
LocalizationGroup: Premium
ms.openlocfilehash: d1a057f56237a0609f3330d4728c7dfcded84a71
ms.sourcegitcommit: 012f05efc4e97aeb6178fb2fc820b73bcc1ce920
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68391137"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Saját titkosítási kulcsok használata a Power BI-hoz (előzetes verzió)

A Power BI az _inaktív_ és _feldolgozás alatt álló_ adatokat titkosítja. A Power BI alapértelmezés szerint a Microsoft által felügyelt kulcsokkal titkosítja az adatokat. A Power BI Premiumban saját kulcsait is használhatja az adathalmazba importált inaktív adatokhoz (További információ: [Adatforrásokkal kapcsolatos és tárolási szempontok](#data-source-and-storage-considerations)). Ezt nevezik _Bring Your Own Key_ (BYOK) megközelítésnek.

## <a name="why-use-byok"></a>Miért érdemes BYOK-t használni?

BYOK használatával egyszerűbben eleget tehet a kulcsokkal kapcsolatban a felhőszolgáltatóval (ebben az esetben a Microsofttal) kötött megállapodás követelményeinek. BYOK használatával Ön adhatja meg és szabályozhatja alkalmazásszinten a Power BI-beli inaktív adatok titkosítási kulcsait. Ennek eredményeként ön szabályozza, és vissza is vonhatja vállalati kulcsait, ha a szolgáltatás elhagyása mellett dönt. A kulcsok visszavonása után az adatok a szolgáltatás számára olvashatatlanná válnak.

## <a name="data-source-and-storage-considerations"></a>Adatforrásokkal kapcsolatos és tárolási szempontok

BYOK használatához adatokat kell feltöltenie a Power BI szolgáltatásba egy Power BI Desktop- (PBIX-) fájlból. Nem használhat BYOK-t a következő helyzetekben:

- Élő Analysis Services-kapcsolat
- Excel-munkafüzetek (ha az adatok nincsenek a Power BI Desktopba importálva)
- Leküldéses adathalmazok

A BYOK csak a PBIX-fájlhoz társított adatkészletre vonatkozik, a csempék és vizualizációk lekérdezési eredményeinek gyorsítótáraira nem.

## <a name="configure-azure-key-vault"></a>Az Azure Key Vault konfigurálása

Ebben a szakaszban megtudhatja, hogyan konfigurálhatja az Azure Key Vaultot, amely egy titkos kódok, köztük titkosítási kulcsok biztonságos tárolására és elérésére szolgáló eszköz. Titkosítási kulcsok tárolásához használhat meglévő kulcstartót, vagy újat is létrehozhat, amelyet csak a Power BI-hoz használ.

Az ebben a szakaszban leírtak feltételezik az Azure Key Vault alapszintű ismeretét. További információ: [Mi az Azure Key Vault?](/azure/key-vault/key-vault-whatis). Kulcstartóját az alábbi módon konfigurálhatja:

1. Vegye fel a Power BI szolgáltatást szolgáltatásnévként a kulcstartóhoz, Wrap és Unwrap engedélyekkel.

1. Hozzon létre 4096 bites RSA-kulcsot (vagy használjon ilyen típusú meglévő kulcsot) Wrap és Unwrap engedélyekkel.

    > [!IMPORTANT]
    > A Power BI BYOK csak 4096 bites RSA-kulcsokat támogat.

1. Ajánlott: Ellenőrizze, hogy a kulcstárolóhoz engedélyezve van-e a _Helyreállítható törlés_ beállítás.

### <a name="add-the-service-principal"></a>A szolgáltatásnév hozzáadása

1. Az Azure Portalon a kulcstartóban a **Hozzáférési szabályzatok** alatt válassza az **Új hozzáadása** lehetőséget.

1. A **Rendszerbiztonsági tag kijelölése** alatt keresse meg és válassza ki a Microsoft.Azure.AnalysisServices elemet.

    > [!NOTE]
    > Ha nem találja a „Microsoft.Azure.AnalysisServices” elemet, az valószínűleg azért van, mert az Azure Key Vaulthoz társított Azure-előfizetéséhez nem rendeltek Power BI-erőforrást. Próbáljon meg a következő sztringre keresni: 00000009-0000-0000-c000-000000000000.

1. A **Kulcsengedélyek** területen jelölje ki a **Kulcs kicsomagolása** és a **Kulcs kicsomagolása** engedélyt.

    ![PBIX-fájl összetevői](media/service-encryption-byok/service-principal.png)

1. Válassza az **OK**, majd a **Mentés** lehetőséget.

### <a name="create-an-rsa-key"></a>RSA-kulcs létrehozása

1. Kulcstartójában a **Kulcsok** alatt válassza a **Generálás/Importálás** lehetőséget.

1. Válassza az RSA **Kulcstípust** és a 4096 **RSA-kulcsméretet**.

    ![PBIX-fájl összetevői](media/service-encryption-byok/create-rsa-key.png)

1. Kattintson a **Létrehozás** gombra.

1. A **Kulcsok** alatt jelölje ki a létrehozott kulcsot.

1. Válassza a kulcs **Aktuális verziójának** GUID-azonosítóját.

1. Ellenőrizze, hogy a **Kulcs becsomagolása** és a **Kulcs kicsomagolása** is ki van-e jelölve. Másolja ki a BYOK Power BI-beli engedélyezéséhez szükséges **Kulcsazonosítót**.

    ![PBIX-fájl összetevői](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>Helyreállítható törlés beállítás

A kulcstartóhoz a kulcs – vagy a kulcstartó – véletlen törléséből eredő adatvesztés elkerülése érdekében ajánlott engedélyezni a [Helyreállítható törlés](/azure/key-vault/key-vault-ovw-soft-delete) beállítást. A kulcstartóhoz [a PowerShell használatával kell engedélyeznie a „Helyreállítható törlés” tulajdonságot](/azure/key-vault/key-vault-soft-delete-powershell), mert ez a beállítás egyelőre nem érhető el az Azure Portalon.

Az Azure Key Vault megfelelő konfigurálása után már engedélyezheti bérlőjében a BYOK-t.

## <a name="enable-byok-on-your-tenant"></a>BYOK engedélyezése a bérlőben

BYOK úgy engedélyezhető a bérlői szinten a [PowerShell](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Admin) használatával, hogy először bevezeti Power BI-bérlőjében a létrehozott és az Azure Key Vaultban tárolt titkosítási kulcsait. Ez után prémium szintű kapacitásonként kioszthatja ezeket a titkosítási kulcsokat a kapacitásbeli tartalom titkosításához.

### <a name="important-considerations"></a>Fontos szempontok

BYOK engedélyezése előtt vegye figyelembe a következőket:

- Jelenleg nem tilthatja le a BYOK-ot, miután engedélyezte azt. Az `Add-PowerBIEncryptionKey` parancshoz megadott paraméterektől függően szabályozni tudja, hogy hogyan legyen használva a BYOK egy vagy több kapacitáshoz. A kulcsok bérlőbeli bevezetését azonban nem vonhatja vissza. További információ: [BYOK engedélyezése](#enable-byok).

- Egy BYOK-t használó munkaterületet nem helyezhet át _közvetlenül_ megosztott kapacitásba egy Power BI Premiumbeli dedikált kapacitásból. A munkaterületet először olyan dedikált kapacitásba kell áthelyeznie, amelyen nincs engedélyezve BYOK.

### <a name="enable-byok"></a>BYOK engedélyezése

BYOK engedélyezéséhez bérlői rendszergazdának kell lennie a Power BI szolgáltatásban, a `Connect-PowerBIServiceAccount` parancsmag használatával bejelentkezve. Ez után az [`Add-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/Add-PowerBIEncryptionKey) paranccsal engedélyezheti a BYOK-ot, az alábbi példán bemutatott módon:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Több kulcs hozzáadásához futtassa az `Add-PowerBIEncryptionKey` parancsmagot különböző értékeket megadva a -`-Name` és a `-KeyVaultKeyUri` számára. 

A parancsmag két kapcsolóparamétert fogad el, amelyek a jelenlegi és jövőbeli kapacitások titkosítását befolyásolják. Alapértelmezés szerint a kapcsolók egyike sincs beállítva:

- `-Activate`: Azt jelzi, hogy a rendszer ezt a kulcsot fogja használni a bérlőben meglévő minden olyan kapacitáshoz, amely még nem lett titkosítva.

- `-Default`: Azt jelzi, hogy ez a kulcs mostantól az egész bérlőben alapértelmezett. Új kapacitás létrehozásakor a kapacitás örökli ezt a kulcsot.

> [!IMPORTANT]
> A `-Default` kapcsoló megadása esetén a bérlőben ettől kezdve létrehozott összes kapacitás a megadott kulccsal (vagy egy frissített alapértelmezett kulccsal) lesz titkosítva. Az alapértelmezett művelet nem vonható vissza, így többé nem tud olyan prémium szintű kapacitást létrehozni a bérlőben, amely nem használ BYOK-t.

Miután engedélyezte a BYOK-t a bérlőben, a [`Set-PowerBICapacityEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/set-powerbicapacityencryptionkey) használatával állíthatja be a titkosítási kulcsot egy vagy több Power BI-kapacitáshoz:

```powershell
Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
```

Azt szabályozni tudja, hogy hogyan használja a BYOK-ot a bérlőben. Egyetlen kapacitás titkosításához például hívja meg az `Add-PowerBIEncryptionKey` parancsot az `-Activate` vagy a `-Default` kapcsoló nélkül. Ez után hívja meg a `Set-PowerBICapacityEncryptionKey` parancsot arra a kapacitásra, amelyen engedélyezni kívánja a BYOK-ot.

## <a name="manage-byok"></a>BYOK felügyelete

A Power BI további parancsmagokat kínál a BYOK egyszerű bérlőbeli felügyeletéhez:

- A [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) használatával lekérheti a kapacitás által jelenleg használt kulcsot:

    ```powershell
    Get-PowerBICapacity -Scope Organization -ShowEncryptionKey
    ```

- A [`Get-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiencryptionkey) használatával lekérheti a bérlő által jelenleg használt kulcsot:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- A [`Get-PowerBIWorkspaceEncryptionStatus`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiworkspaceencryptionstatus) használatával megállapíthatja, hogy a munkaterületen lévő adathalmazok titkosítva vannak-e, és hogy titkosítási állapotuk szinkronban van-e a munkaterülettel:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Lényeges, hogy a titkosítás a kapacitás szintjén van engedélyezve, de a titkosítás állapotát az adathalmaz szintjén kapja meg a megadott munkaterülethez.

- A titkosításhoz használt kulcs verziója a [`Switch-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/switch-powerbiencryptionkey) paranccsal váltható (vagy _forgatható_). A parancsmag csak a `-Name` kulcs `-KeyVaultKeyUri` értékét módosítja:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```
