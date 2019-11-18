---
title: SSL-tanúsítvány létrehozása
description: Megoldási útmutató a tanúsítványok manuális létrehozásához a fejlesztői kiszolgáló számára
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 224b6db8fa04a471a1ce7d1fff2b34a838d6fb9d
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060353"
---
# <a name="create-an-ssl-certificate"></a>SSL-tanúsítvány létrehozása

Ez a cikk az SSL-tanúsítványok létrehozását ismerteti.

A tanúsítvány Windows 8 vagy újabb rendszeren a PowerShell `New-SelfSignedCertificate` parancsmagjával generálható az alábbi parancsot futtatásával:

```cmd
pbiviz --install-cert
```

Windows 7 rendszerhez az eszköz az OpenSSL telepítését igényli. Az OpenSSL segédprogramnak elérhetőnek kell lennie a parancssorból.

Az OpenSSL telepítéséhez nyissa meg az [OpenSSL](https://www.openssl.org) vagy az [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) webhelyet.

## <a name="create-a-certificate-mac-os-x"></a>Tanúsítvány létrehozása (Mac OS X)

Az OpenSSL segédprogram általában elérhető a Linux vagy a Mac OS X operációs rendszerben.

A segédprogram az alábbi parancsok valamelyikével is telepíthető:

* A *Brew* csomagkezelőből:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* A *MacPorts* használatával:

    ```cmd
    sudo port install openssl
    ```

Miután telepítette az OpenSSL segédprogramot az új tanúsítvány generálásához, futtassa az alábbi parancsot:

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>Tanúsítvány létrehozása (Linux)

Ha az OpenSSL segédprogram nem érhető el a Linux operációs rendszeren, a következő parancsok valamelyikével telepítheti:

* Az *APT* csomagkezelővel:

    ```cmd
    sudo apt-get install openssl
    ```

* A *Yellowdog Updater* használatával:

    ```cmd
    yum install openssl
    ```

* A *Redhat-csomagkezelővel*:

    ```cmd
    rpm install openssl
    ```

Ha az OpenSSL segédprogram már elérhető az operációs rendszerben, a következő paranccsal generálhat új tanúsítványt:

```cmd
pbiviz --install-cert
```

Az OpenSSL segédprogram az [OpenSSL](https://www.openssl.org) vagy az [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) webhelyről is beszerezhető.

## <a name="generate-the-certificate-manually"></a>A tanúsítvány manuális generálása

A tanúsítványok generálására bármilyen eszközt megadhat.

Ha az OpenSSL segédprogram már telepítve van a rendszeren, az alábbi parancsok futtatásával generálhat új tanúsítványt:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

A PowerBI-visuals-tools webkiszolgáló tanúsítványait általában a következő futtatásával találhatja meg:

* Az eszközök globális példányaihoz:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Az eszközök helyi példányaihoz:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Ha a PEM formátumot használja, a tanúsítványfájlt *PowerBICustomVisualTest_public.crt* néven, a privát kulcsot (privateKey) pedig *PowerBICustomVisualTest_public.key* néven mentse.

Ha a PFX formátumot használja, a tanúsítványfájlt *PowerBICustomVisualTest_public.pfx* néven mentse.

Ha a PFX-tanúsítványfájlhoz jelszó szükséges, hajtsa végre a következő lépéseket:
1. A konfigurációs fájlban adja meg a következőt:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. A `server` szakaszban adja meg a jelszót a "*YOUR PASSPHRASE*" helyőrző felülírásával:

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