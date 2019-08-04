---
title: SSL-tanúsítvány létrehozása
description: Megoldási útmutató a tanúsítványok manuális létrehozásához a fejlesztői kiszolgáló számára
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425436"
---
# <a name="creating-ssl-certificate"></a>SSL-tanúsítvány létrehozása

Futtassa a következő parancsot a tanúsítvány létrehozásához a PowerShell New-SelfSignedCertificate parancsmag használatával Windows 8 vagy újabb rendszeren.

Az eszközhöz szükséges az OpenSSL telepítése **Windows** **7** rendszerhez. Az `openssll` eszköznek elérhetőnek kell lennie a parancssorból.

Az OpenSSL telepítéséhez látogasson el a következő webhelyre: [https://www.openssl.org](https://www.openssl.org) vagy [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Tanúsítvány létrehozása (Mac OS X)

Linux vagy Mac OS X operációs rendszereken általában elérhetőek az OpenSSL-segédeszközök.

Egyéb esetben a következő címről telepítheti:

*Brew* csomagkezelő

```cmd
brew install openssl
brew link openssl --force
```

vagy a *MacPorts* használatával

```cmd
sudo port install openssl
```

Miután telepítette az OpenSSL-t az új tanúsítványkérelem létrehozásához:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Tanúsítvány létrehozása (Linux)

Ha az OpenSSL-segédeszközök nem érhetők el a linuxos operációs rendszeren, a következő parancsokkal telepítheti.

Az *APT* csomagkezelővel:

```cmd
sudo apt-get install openssl
```

A *Yellowdog Updater* használatával:

```cmd
yum install openssl
```

A *Redhat-csomagkezelővel*:

```cmd
rpm install openssl
```

Ha az OpenSSl már elérhető az operációs rendszeren

```cmd
pbiviz --create-cert
```

új tanúsítvány létrehozásához.

Vagy beszerezheti azt a [https://www.openssl.org](https://www.openssl.org) vagy a [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) webhelyekről

## <a name="generate-certificate-manually"></a>Tanúsítvány manuális létrehozása

Bármely eszköz által létrehozott tanúsítványait megadhatja.

Ha telepítve van az OpenSSL a rendszeren, a következő parancs futtatásával új tanúsítványt hozhat létre

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

A PowerBI-vizualizációs eszközök webkiszolgáló-tanúsítványai általában a következő helyen találhatók:

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

az eszközök globális példányához

vagy

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

az eszközök helyi példányához.

A tanúsítványfájlt `PowerBICustomVisualTest_public.cer` néven, a privát kulcsot pedig `PowerBICustomVisualTest_public.key` néven kell menteni, ha PEM-formátumot használ.
Ha PFX-formátumot használ, akkor a tanúsítványfájlt `PowerBICustomVisualTest_public.pfx` néven mentse.

Ha a PFX-tanúsítványhoz hozzáférési kód szükséges, adja meg itt

```cmd
\PowerBI-visuals-tools\config.json
```

a „server” szakaszban:

```cmd
"server":{
    "root":"webRoot",
    "assetsRoute":"/assets",
    "privateKey":"certs/PowerBICustomVisualTest_private.key",
    "certificate":"certs/PowerBICustomVisualTest_public.crt",
    "pfx":"certs/PowerBICustomVisualTest_public.pfx",
    "port":"8080",
    "passphrase":"YOUR PASSPHRASE"
}
```
