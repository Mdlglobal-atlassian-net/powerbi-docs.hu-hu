---
title: A Power BI Desktop bejelentkezési űrlapjának rendszergazdák általi kezelése
description: Tudja meg, hogyan kezelheti a Power BI Desktop első megnyitásakor megjelenő bejelentkezési űrlapot.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: b1ab5188ba8f5ccf54589d359f6f8ced1ada3060
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878865"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>A Power BI Desktop bejelentkezési űrlapjának rendszergazdák általi kezelése
A Power BI Desktop első indításakor megjelenik egy bejelentkezési űrlap. A folytatáshoz ezt ki kell tölteni, vagy be kell jelentkezni a Power BI szolgáltatásba. A rendszergazdák egy beállításkulccsal kezelik ezt az űrlapot. 

![A Power BI Desktop első indításakor megjelenő bejelentkezési űrlap](media/desktop-admin-sign-in-form/sign-in-form.png)

A rendszergazdák az alábbi beállításkulccsal tilthatják le a bejelentkezési űrlapot. Ez globális szabályzatok használatával az egész vállalatra kiterjeszthető.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Emellett kipróbálhatja a következő kulcsot is, amely a konfigurációk alapján sikeresen bevált néhány ügyfélnél a konfigurációk alapján:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

A 0 érték kikapcsolja a párbeszédpanelt.




További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

