---
title: A „vállalati SSL-tanúsítványa nem megbízható” hiba elhárítása
description: 'A Power BI Androidos alkalmazásba való bejelentkezéskor a következő üzenet jelenhet meg: „A hitelesítés nem sikerült, mert a vállalati SSL-tanúsítványt nem megbízhatóként kezeli ez az eszköz”'
.": ''
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 494e148a62675aab1a6e799c4e4b61f022483d9f
ms.sourcegitcommit: aa8045e42b979206c600bce4a8d17de1f0620462
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/22/2018
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
Ha egyéni hitelesítési kiszolgálót használ, előfordulhat, hogy a vállalati hitelesítési kiszolgáló SSL-tanúsítványa nem érvényes. Segítségért forduljon a szervezet rendszergazdájához.

## <a name="next-steps"></a>További lépések
* [Töltse le az Android-alkalmazást](http://go.microsoft.com/fwlink/?LinkID=544867) az Androidos alkalmazás-áruházból.
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

