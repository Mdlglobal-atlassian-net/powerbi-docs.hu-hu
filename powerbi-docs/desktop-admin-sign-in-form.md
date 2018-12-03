---
title: A Power BI Desktop bejelentkezési űrlapjának rendszergazdák általi kezelése
description: Tudja meg, hogyan kezelheti a Power BI Desktop első megnyitásakor megjelenő bejelentkezési űrlapot.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
ms.openlocfilehash: 3c92063c82c370bd59ecd7bfa2798ae60a3b425d
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578244"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>A Power BI Desktop bejelentkezési űrlapjának rendszergazdák általi kezelése
A Power BI Desktop első indításakor megjelenik egy bejelentkezési űrlap. A folytatáshoz ezt ki kell tölteni, vagy be kell jelentkezni a Power BI szolgáltatásba. A rendszergazdák egy beállításkulccsal kezelik ezt az űrlapot. 

![A Power BI Desktop első indításakor megjelenő bejelentkezési űrlap](media/desktop-admin-sign-in-form/sign-in-form.png)

A rendszergazdák az alábbi beállításkulccsal tilthatják le a bejelentkezési űrlapot. Ez globális szabályzatok használatával az egész vállalatra kiterjeszthető.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

A 0 érték kikapcsolja a párbeszédpanelt.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

