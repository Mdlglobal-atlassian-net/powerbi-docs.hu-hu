---
title: Jelentések és irányítópultok beágyazása alkalmazásokból
description: Megtudhatja, hogyan integrálhat vagy ágyazhat be egy jelentést vagy irányítópultot egy Power BI-alkalmazásból, és nem a munkaterületről.
author: rkarlin
ms.author: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
manager: kfile
ms.date: 11/27/2018
ms.openlocfilehash: 1883d82b47c32f3c7f03e55a177429d09ce337a2
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73430854"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Jelentések és irányítópultok beágyazása alkalmazásokból

A Power BI-ban létrehozhat az irányítópultokat és jelentéseket egy helyen összefűző alkalmazásokat. Ezután közzéteheti azokat a vállalat nagy csoportjai számára. Ezen alkalmazások használata akkor válik fontossá, ha minden felhasználója Power BI-felhasználó. Ekkor a Power BI-alkalmazásokon keresztül oszthat meg velük tartalmakat. A cikk bemutatja, hogyan kell beágyazni egy közzétett Power BI-alkalmazásból származó tartalmat egy külső alkalmazásba.

## <a name="grab-a-report-embedurl-for-embedding"></a>Jelentési embedURL beszerzése beágyazáshoz

1. Példányosítsa az alkalmazást a **Saját munkaterület** nevű felhasználói munkaterületen. Ezt ossza meg saját magával, vagy irányítson hozzá egy másik felhasználót.

2. Nyissa meg a kívánt jelentést a Power BI szolgáltatásban.

3. Válassza a **Fájl** > **Beágyazás a SharePoint Online-ba** lehetőséget, és megtalálhatja a jelentés beágyazási URL-címét (embedURL). Az alábbi képernyőképen láthat egy minta beágyazási URL-címet. Alternatív megoldásként meghívhatja a GetReports/GetReport REST API-t, és a válaszból kinyerheti a megfelelő jelentés embedURL mezőjét. A REST-hívás URL-címe elvileg nem tartalmaz munkaterület-azonosítót, mivel az alkalmazás a felhasználó munkaterületén lett példányosítva.

    ![Beágyazás alkalmazásokból](media/embed-from-apps/embed-from-app.png)

4. Használja a 3. lépésben lekért embedURL-t a JavaScript SDK-val.

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Irányítópult embedURL-jének beszerzése beágyazáshoz

1. Példányosítsa az alkalmazást a **Saját munkaterület** nevű felhasználói munkaterületen. Ezt ossza meg saját magával, vagy irányítson hozzá egy másik felhasználót.

2. Alternatív megoldásként meghívhatja a GetDashboards REST API-t, és kinyerheti a válaszból a megfelelő irányítópult-embedURL-mezőt. A REST-hívás URL-címe elvileg nem tartalmaz munkaterület-azonosítót, mivel az alkalmazás a felhasználó munkaterületén lett példányosítva.

3. Használja a 2. lépésben lekért embedURL-t a JavaScript SDK-val.

## <a name="next-steps"></a>Következő lépések

Tekintse át, hogyan ágyazhat be tartalmakat a munkaterületről külső ügyfelekhez és a szervezetbe:

> [!div class="nextstepaction"]
>[Beágyazás külső ügyfelek számára](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Beágyazás a cég számára](embed-sample-for-your-organization.md)
