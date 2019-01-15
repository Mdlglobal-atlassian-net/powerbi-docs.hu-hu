---
title: Sorszintű biztonság (RLS) a Power BI Desktoppal – összefoglaló
description: Az importált adatkészletek és a DirectQuery sorszintű biztonságának konfigurálása a Power BI Desktopban.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/03/2018
LocalizationGroup: Create reports
ms.openlocfilehash: 7cdbb86bafa2d5a532a4ceeeef9f28f5ba22e204
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280148"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Sorszintű biztonság (RLS) a Power BI Desktoppal

A Power BI Desktoppal használható sorszintű biztonsági (RLS) funkció adott felhasználók adatokhoz való hozzáférésének korlátozására szolgál. A szűrők sorszinten korlátozzák az adatokat. A szűrőket a szerepkörökön belül adhatja meg.

Most már konfigurálhat RLS-t a Power BI Desktoppal a Power BI-be importált adatmodellekhez. Ezen kívül a DirectQueryt használó adatkészletekhez is konfigurálhat RLS-t, például az SQL Serverhez. Korábban csak a Power BI szolgáltatáson kívül, a helyszíni Analysis Services-modellekben lehetett RLS-t beállítani. Az Analysis Services élő kapcsolataihoz a helyszíni modellen konfigurálhatja a sorszintű biztonságot. Az élő kapcsolatok adatkészleteinél nem fog megjelenni a biztonsági beállítás.

> [!IMPORTANT]
> Ha szerepköröket és szabályokat adott meg a Power BI szolgáltatásban, újból létre kell hoznia ezeket a szerepköröket a Power BI Desktopon belül, és közzé kell tennie a jelentést a szolgáltatásban.

További információk az [RLS beállításairól a Power BI szolgáltatásban](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>További lépések

[Sorszintű biztonság (RLS) a Power BI szolgáltatással](service-admin-rls.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)