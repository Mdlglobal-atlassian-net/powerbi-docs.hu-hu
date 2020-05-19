---
title: SSL-tanúsítványok létrehozása Power BI-vizualizációkhoz
description: A cikk azt ismerteti, hogyan hozhat létre SSL-tanúsítványokat a Power BI vizualizációs eszközeivel Windows, Mac és Linux rendszerű gépeken vagy manuálisan.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 37bd8f15dcf17cd0f967e819338a719edf2a3054
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276375"
---
# <a name="create-an-ssl-certificate"></a>SSL-tanúsítvány létrehozása

Ez a cikk azt ismerteti, hogyan hozhat létre és telepíthet SSL- (Secure Sockets Layer-) tanúsítványokat a Power BI-vizualizációkhoz.

Windows-, macOS X-és Linux-eljárások esetén telepítve kell lennie a Power BI vizualizációs eszközeit tartalmazó **pbiviz** csomagnak. További információ: [A fejlesztői környezet beállítása](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Tanúsítvány létrehozása Windows rendszeren

Ha Windows 8 vagy újabb rendszeren a `New-SelfSignedCertificate` PowerShell-parancsmaggal kíván létrehozni egy tanúsítványt, futtassa a következő parancsot:

```powershell
pbiviz --install-cert
```

Windows 7 esetén az `pbiviz` eszköz megköveteli, hogy az OpenSSL segédprogram elérhető legyen a parancssorból. Az OpenSSL telepítéséhez keresse fel az [OpenSSL](https://www.openssl.org) vagy az [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) webhelyet.

A tanúsítványok telepítésével kapcsolatos további információért és utasításokért lásd: [Tanúsítvány létrehozása és telepítése Windows rendszeren](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#windows).

## <a name="create-a-certificate-on-macos-x"></a>Tanúsítvány létrehozása macOS X rendszeren

Az OpenSSL segédprogram általában elérhető a macOS X operációs rendszerben.

Az OpenSSL segédprogram az alábbi parancsok valamelyikének futtatásával is telepíthető:

- A *Brew* csomagkezelőből:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- A *MacPorts* használatával:
  
  ```cmd
  sudo port install openssl
  ```

Miután telepítette az OpenSSL segédprogramot, futtassa az alábbi parancsot egy új tanúsítvány létrehozásához:

```cmd
pbiviz --install-cert
```

További információért és utasításokért lásd: [Tanúsítvány létrehozása és telepítése macOS X rendszeren](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#osx).

## <a name="create-a-certificate-on-linux"></a>Tanúsítvány létrehozása Linuxon

Az OpenSSL segédprogram általában elérhető a Linux operációs rendszerben.

Mielőtt elkezdené, az alábbi parancsok futtatásával győződjön meg arról, hogy az `openssl` és a `certutil` telepítve van:

```sh
which openssl
which certutil
```

Ha az `openssl` és a `certutil` nincs telepítve, telepítse az `openssl` és a `libnss3` segédprogramokat.

### <a name="create-the-ssl-configuration-file"></a>SSL-konfigurációs fájl létrehozása

Hozzon létre egy */tmp/openssl.cnf* nevű fájlt, amely az alábbi szöveget tartalmazza:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Legfelső szintű hitelesítésszolgáltató létrehozása

A helyi tanúsítványok aláírására szolgáló legfelső szintű hitelesítésszolgáltató (CA) létrehozásához futtassa az alábbi parancsokat:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Állítson elő egy tanúsítványt a helyi gazdagép részére 

Ha létre kíván hozni egy tanúsítványt a `localhost` számára a létrehozott CA és az *openssl.cnf* használatával, futtassa a következő parancsokat:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Főtanúsítványok hozzáadása

A főtanúsítványt az alábbi parancs futtatásával adhatja hozzá a Chrome böngésző adatbázisához:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

A főtanúsítványt az alábbi parancs futtatásával adhatja hozzá a Mozilla Firefox böngésző adatbázisához:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Rendszerszintű főtanúsítvány hozzáadásához futtassa a következőt:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Főtanúsítványok eltávolítása

A főtanúsítvány eltávolításához futtassa a következőt:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Tanúsítvány manuális létrehozása

Az SSL-tanúsítványt manuálisan is létrehozhatja az OpenSSL használatával. Bármilyen eszközt megadhat a tanúsítványok előállításához.

Ha az OpenSSL segédprogram már telepítve van, hozzon létre egy új tanúsítványt az alábbi parancs futtatásával:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

A `PowerBI-visuals-tools` webkiszolgáló-tanúsítványokat általában megtalálhatja az alábbi parancsok egyikének futtatásával:

- Az eszközök globális példányaihoz:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Az eszközök helyi példányaihoz:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM formátum

Ha a Privacy Enhanced Mail (PEM) tanúsítványformátumot használja, mentse a tanúsítványfájlt *PowerBIVisualTest_public.crt*, a titkos kulcsot pedig *PowerBIVisualTest_private.key* néven.

### <a name="pfx-format"></a>PFX-formátum

Ha a Personal Information Exchange (PFX) tanúsítványformátumot használja, mentse a tanúsítványfájlt *PowerBIVisualTest_public.pfx* néven.

Ha a PFX-tanúsítványfájlhoz jelszó szükséges:

1. A konfigurációs fájlban adja meg a következőt:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. A `server` szakaszban adja meg a jelszót a \<YOUR PASSPHRASE> helyőrző felülírásával:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Következő lépések
- [Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md)
- [Minta Power BI-vizualizációk](samples.md)
- [Power BI-vizualizáció közzététele az AppSource-ban](office-store.md)
