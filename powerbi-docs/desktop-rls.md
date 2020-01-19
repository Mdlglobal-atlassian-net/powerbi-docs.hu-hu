---
title: Sorszintű biztonság (RLS) a Power BI Desktoppal – összefoglaló
description: Az importált adatkészletek és a DirectQuery sorszintű biztonságának konfigurálása a Power BI Desktopban.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 12/05/2019
LocalizationGroup: Create reports
ms.openlocfilehash: dc2c1e312592048c90643526a898ebe654907a68
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760658"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Az adathozzáférés korlátozása sorszintű biztonsággal (RLS) a Power BI Desktopban

A sorszintű biztonság (RLS) a Power BI Desktoppal adott felhasználók adatokhoz való hozzáférésének korlátozására használható. A szűrők sorszinten korlátozzák az adatokat. A szűrőket a szerepkörökön belül adhatja meg.

Most már konfigurálhat RLS-t a Power BI Desktoppal a Power BI-be importált adatmodellekhez. Ezen kívül konfigurálhat RLS-t a [DirectQueryt](desktop-use-directquery.md) használó adatkészletekhez, például az SQL Serverhez is. Korábban csak a Power BI szolgáltatáson kívül, a helyszíni Analysis Services-modellekben lehetett RLS-t beállítani. Az Analysis Services élő kapcsolataihoz a helyszíni modellen konfigurálhatja a sorszintű biztonságot. Az élő kapcsolatok adatkészleteinél nem fog megjelenni a biztonsági beállítás.

> [!IMPORTANT]
> Ha szerepköröket és szabályokat adott meg a Power BI szolgáltatásban, újból létre kell hoznia ezeket a szerepköröket a Power BI Desktopon belül, és közzé kell tennie a jelentést a szolgáltatásban.

További információk az [RLS beállításairól a Power BI szolgáltatásban](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Következő lépések

[Sorszintű biztonság (RLS) a Power BI szolgáltatással](service-admin-rls.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)