---
title: Dinamikus kötés
description: Megtudhatja, hogyan ágyazhat be egy jelentést dinamikus kötéssel.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776237"
---
# <a name="dynamic-binding"></a>Dinamikus kötés

Dinamikus kötéssel dinamikusan kiválaszthat egy adathalmazt egy jelentés beágyazásakor. A jelentésnek és az adathalmaznak nem kell ugyanazon a munkaterületen lennie. A végfelhasználók számára a kiválasztott adathalmaztól függően különböző eredmények jelennek meg.

Mindkét munkaterületet (a jelentést tartalmazót és az adathalmazt tartalmazót) hozzá kell rendelni egy kapacitáshoz.

Egy jelentés dinamikus kötéssel való beágyazásának két szakasza van:
1. Jogkivonat generálása
2. Konfigurációs objektum beállítása

## <a name="generating-a-token"></a>Jogkivonat generálása
Egy jogkivonat generálásához használja a [több elem beágyazási tokenjének generálására szolgáló API-t](embed-sample-for-customers.md#multiEmbedToken).

A dinamikus kötés mindkét beágyazási forgatókönyv – *Beágyazás a szervezet számára* és *Beágyazás ügyfelek számára* – esetében támogatott.

| Megoldás                   | Jogkivonat                               | Követelmények                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Beágyazás a szervezet számára* | Hozzáférési jogkivonat Power BI-felhasználók számára     | A felhasználónak, akinek az Azure AD-jogkivonatát használják, az összes összetevőre vonatkozóan rendelkeznie kell a megfelelő engedélyekkel.                                                                    |
| *Beágyazás ügyfelek számára*    | Hozzáférési jogkivonat nem Power BI-felhasználók számára | A jelentésre és a dinamikusan kötött adathalmazra vonatkozó engedélyeket is tartalmaznia kell. Az új API-val hozhat létre több összetevőt támogató beágyazási jogkivonatot. |

## <a name="adjusting-the-config-object"></a>Konfigurációs objektum beállítása
Adja hozzá a `datasetBinding` elemet a konfigurációs objektumhoz. Az oldal alján található példát használhatja hivatkozásként.

Ha még most kezd beágyazást használni a Power BI-ban, a következő oktatóanyagok áttekintésével megtudhatja, hogyan ágyazhat be Power BI-tartalmakat:
* [Power BI tartalom beágyazása egy alkalmazásba az ügyfelek számára](embed-sample-for-customers.md)
* [Oktatóanyag: Power BI tartalom beágyazása egy alkalmazásba a vállalat számára](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Példa
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```