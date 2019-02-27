---
title: A Power BI Desktop bejelentkezési űrlapjának rendszergazdák általi kezelése
description: Tudja meg, hogyan kezelheti a Power BI Desktop első megnyitásakor megjelenő bejelentkezési űrlapot.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/21/2019
ms.author: davidi
ms.openlocfilehash: 9e35bbffec40aa57d3097e122bd038659405dfed
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892298"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>A Power BI Desktop bejelentkezési űrlapjának rendszergazdák általi kezelése
A Power BI Desktop első indításakor megjelenik egy bejelentkezési űrlap. A folytatáshoz ezt ki kell tölteni, vagy be kell jelentkezni a Power BI szolgáltatásba. A rendszergazdák egy beállításkulccsal kezelik ezt az űrlapot. 

![A Power BI Desktop első indításakor megjelenő bejelentkezési űrlap](media/desktop-admin-sign-in-form/sign-in-form.png)

A rendszergazdák az alábbi beállításkulccsal tilthatják le a bejelentkezési űrlapot. Ez globális szabályzatok használatával az egész vállalatra kiterjeszthető.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

A 0 érték kikapcsolja a párbeszédpanelt.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

