---
title: Jelentés adathalmazhoz csatlakoztatása dinamikus kötés használatával
description: Útmutató jelentés dinamikus kötéssel történő beágyazásához.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: ecc7ec21117c9e2cd974058c63bcf02d72d1f4b1
ms.sourcegitcommit: 50c4bebd3432ef9c09eacb1ac30f028ee4e66d61
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925764"
---
# <a name="connecting-a-report-to-a-dataset-using-dynamic-binding"></a>Jelentés adathalmazhoz csatlakoztatása dinamikus kötés használatával 

A dinamikus kötés használata csak egy jelentés adathalmazhoz csatlakoztatásában játszik szerepet. A jelentés és az adathalmaz közötti kapcsolatot nevezzük *kötésnek*. A nem előre, hanem a beágyazási ponton meghatározott kötést neve [dinamikus kötés](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FLate_binding&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C5d5b0d2d62cf4818f0c108d7635b151e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637087115150775585&sdata=AbEtdJvgy4ivi4v4ziuui%2Bw2ibTQQXBQNYRKbXn5scA%3D&reserved=0).
 
Power BI-jelentés *dinamikus kötéssel* való beágyazásakor ugyanazt a jelentést a felhasználó hitelesítő adatai alapján különböző adathalmazokhoz is csatlakoztathatja.
 
Ez azt jelenti, hogy ugyanabban a jelentésben más információkat jeleníthet meg attól az adathalmaztól függően, amelyhez csatlakozik. Egy értékesítési eredményeiket bemutató jelentés például különböző kereskedői adathalmazokhoz csatlakozhat, és más eredményeket állíthat elő attól függően, hogy melyik kereskedő adathalmazához csatlakozik.
 
A jelentésnek és az adathalmaznak nem kell ugyanazon a munkaterületen lennie. Mindkét munkaterületet (a jelentést tartalmazót és az adathalmazt tartalmazót) hozzá kell rendelni egy [kapacitáshoz](azure-pbie-create-capacity.md).

A beágyazási folyamat részeként mindenképpen *generáljon egy megfelelő engedélyekkel rendelkező jogkivonatot* és *állítsa be a konfigurációs objektumot*.


## <a name="generating-a-token-with-sufficient-permissions"></a>Megfelelő engedélyekkel rendelkező jogkivonat generálása

A dinamikus kötés *a vállalat számára végzett beágyazáshoz* és az *ügyfelek számára végzett beágyazáshoz* is támogatott. Az alábbi táblázat ennek a két esetnek a szempontjait foglalja össze.


|Eset  |Az adatok tulajdonjoga  |Jogkivonat  |Követelmények  |
|---------|---------|---------|---------|
|*Beágyazás a szervezet számára*    |Felhasználó tulajdonában lévő adatok         |Hozzáférési jogkivonat Power BI-felhasználók számára         |A felhasználónak, akinek az Azure AD-jogkivonatát használják, az összes összetevőre vonatkozóan rendelkeznie kell a megfelelő engedélyekkel.         |
|*Beágyazás ügyfelek számára*     |Alkalmazás tulajdonában lévő adatok         |Hozzáférési jogkivonat nem Power BI-felhasználók számára         |A jelentésre és a dinamikusan kötött adathalmazra vonatkozó engedélyeket is tartalmaznia kell. Használja a [Több elem beágyazási jogkivonatának generálására szolgáló API-t](embed-sample-for-customers.md#multiEmbedToken) egy több összetevőt támogató beágyazási jogkivonat generálásához.         |

## <a name="adjusting-the-config-object"></a>Konfigurációs objektum beállítása
Adja hozzá a `datasetBinding` elemet a konfigurációs objektumhoz. Referenciaként használhatja az alábbi példát.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Következő lépések

Ha még most kezd beágyazást használni a Power BI-ban, a következő oktatóanyagok áttekintésével megtudhatja, hogyan ágyazhat be Power BI-tartalmakat:
* [Oktatóanyag: Power BI tartalom beágyazása egy alkalmazásba az ügyfelek számára](embed-sample-for-customers.md)
* [Oktatóanyag: Power BI tartalom beágyazása egy alkalmazásba a vállalat számára](embed-sample-for-your-organization.md)