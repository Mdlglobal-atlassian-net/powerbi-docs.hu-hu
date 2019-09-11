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
ms.openlocfilehash: 13926603d7a5bfee987439180151d64ef5c456c2
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237253"
---
# <a name="create-an-ssl-certificate"></a>SSL-tanúsítvány létrehozása

Ez a cikk az SSL-tanúsítványok létrehozását ismerteti.

A tanúsítvány Windows 8 vagy újabb rendszeren a PowerShell `New-SelfSignedCertificate` parancsmagjával generálható az alábbi parancsot futtatásával:

```cmd
pbiviz --create-cert
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
pbiviz --create-cert
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
pbiviz --create-cert
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
