---
title: A „vállalati SSL-tanúsítványa nem megbízható” hiba elhárítása
description: 'A Power BI Androidos alkalmazásba való bejelentkezéskor a következő üzenet jelenhet meg: „A hitelesítés nem sikerült, mert a vállalati SSL-tanúsítványt nem megbízhatóként kezeli ez az eszköz”'
.": ''
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: mshenhav
ms.openlocfilehash: de103412e21e0d26d20058e2d4e1fb9a8a5449bf
ms.sourcegitcommit: a054782370dec56d49bb205ee10b7e2018f22693
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662319"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>A „vállalati SSL-tanúsítványa nem megbízható” hiba elhárítása – Power BI
A Microsoft Power BI Android-mobilalkalmazásba való bejelentkezéskor a következő üzenet jelenhet meg: „A hitelesítés nem sikerült, mert a vállalati SSL-tanúsítványt nem megbízhatóként kezeli ez az eszköz. Kérjük, lépjen kapcsolatba a vállalata rendszergazdájával.” 

Az ilyenkor szükséges lépések általában az Android-eszköz operációs rendszerétől függenek, azonban a hibát néhány egyéb dolog is okozhatja.

## <a name="on-android-7-or-later"></a>Az Android 7-es vagy újabb verzióján
Keressen rá a **Chrome** nevű alkalmazás frissítésére, és telepítse azt.

## <a name="on-android-6-and-earlier"></a>Az Android 6-os vagy újabb verzióján
Szükség lehet a System Webview frissített verziójára az eszközön. Ha ez telepítve van az eszközön, elég csak a **Frissítés** gombra kattintania.

Ha a System Webview nincs telepítve az eszközön:

1. Zárja be a Power BI alkalmazást az Android-eszközön.
2. Nyissa meg a Google Play Áruházat, és keressen rá a Google Inc. által készített **System Webview** alkalmazásra.
3. Telepítse.
4. Indítsa el újra a Power BI alkalmazást, és jelentkezzen be.

## <a name="time-zone-settings"></a>Időzóna-beállítások
Elképzelhető, hogy az eszköz időzóna-beállításai nem megfelelőek. 

A **Beállítások** > **Rendszer** > **Dátum és idő** helyen tudja ellenőrizni ezeket.

## <a name="custom-authentication-server"></a>Egyéni hitelesítési kiszolgáló
Ha egyéni hitelesítési kiszolgálót használ, előfordulhat, hogy a vállalati hitelesítési kiszolgáló SSL-tanúsítványa nem érvényes. A vállalat informatikusaival együttműködve tesztelje a vállalat hitelesítési kiszolgálójának konfigurációját [ennek a cikknek](https://support.microsoft.com/en-us/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce) az útmutatása alapján.

## <a name="next-steps"></a>Következő lépések
* [Töltse le az Android-alkalmazást](http://go.microsoft.com/fwlink/?LinkID=544867) az Androidos alkalmazás-áruházból.
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/) 

