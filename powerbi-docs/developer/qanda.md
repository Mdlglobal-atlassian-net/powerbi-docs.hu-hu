---
title: Kérdések és válaszok a Power BI Embeddedben
description: A Power BI Embedded segítségével a Kérdések és válaszok szolgáltatást beépítheti egy alkalmazásba, és engedélyezheti a felhasználók számára, hogy kérdéseket tegyenek fel a természetes nyelvet használva.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/20/2017
ms.author: maghan
ms.openlocfilehash: d1fd42f059f8050662adc80018748d11c1e73e2b
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/26/2018
ms.locfileid: "34813756"
---
# <a name="qa-in-power-bi-embedded"></a>Kérdések és válaszok a Power BI Embeddedben
A Power BI Embedded segítségével a Kérdések és válaszok szolgáltatást beépítheti egy alkalmazásba, és engedélyezheti a felhasználók számára, hogy kérdéseket tegyenek fel a természetes nyelvet használva, és ezekre azonnal választ is kapjanak vizualizációk, például diagramok és ábrák formájában.

![Kérdések és válaszok – Interaktív kérdés egy beágyazott keretben](media/qanda/embedded-qanda.gif)

Két mód létezik a Kérdések és válaszok szolgáltatás beillesztésére az alkalmazásokba: **interaktív** és **csak eredmény**. Az **interaktív** mód lehetővé teszi, hogy kérdéseket írjon be, és azok megjelenjenek a vizualizációban. Ha mentett egy kérdést, vagy beállított egy megjelenítendő kérdést, használhatja a **csak eredmény** módot úgy, hogy feltölti a kérdést a beágyazott konfigurációban.

A JavaScript-kód ehhez hasonlóan fog kinézni.

```
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnAMode.Interactive | models.QnAMode.ResultOnly,
    question:    optional parameter for Explore mode (QnAMode.Interactive) and mandatory for Render Result mode (QnAMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Kérdés beállítása
Ha az **eredmény módot** egy beállított kérdéssel használta, további kérdéseket szúrhat be a keretbe, és azonnal megválaszolhatja őket, lecserélve az előző eredményt. Az új kérdésnek megfelelő új vizualizáció jelenik meg.

Példa erre a használatra a gyakori kérdések listája. A felhasználó áttekintheti ezeket a kérdéseket, és választ kaphat rájuk ugyanabban a beágyazott részben.

**Kódrészlet a JS SDK-használatához:**  

```        
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>Vizuálisan megjelenített esemény
Az **interaktív** módnál az alkalmazás egy adatmódosítási eseménnyel értesíthető minden alkalommal, amikor a megjelenített vizuális módosítások a frissített bemeneti lekérdezést érintik a beírás közben.

A *visualRendered* esemény figyelése lehetővé teszi a kérdések későbbi használatra történő mentését. 

**Kódrészlet a JS SDK-használatához:**  

```
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Beágyazási token
Hozzon létre egy beágyazási tokent egy adatkészletből a Kérdések és válaszok rész megkezdéséhez. További információkért lásd: [Token létrehozása](https://docs.microsoft.com/rest/api/power-bi/embedtoken).

## <a name="next-steps"></a>Következő lépések
A Kérdések és válaszok szolgáltatás beágyazásának kipróbáláshoz tekintse meg a [JavaScript beágyazási mintát](https://microsoft.github.io/PowerBI-JavaScript/demo/).

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

