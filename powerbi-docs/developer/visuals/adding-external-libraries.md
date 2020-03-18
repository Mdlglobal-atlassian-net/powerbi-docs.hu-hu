---
title: Külső kódtárak hozzáadása a Power BI-vizualizációkhoz
description: Ez a cikk a külső kódtárak Power BI-vizualizációkban való használatát ismerteti.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/24/2020
ms.openlocfilehash: 13d5f2ed62ddefb8ac99fe2c91c72fc599a15936
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922505"
---
# <a name="adding-external-libraries"></a>Külső kódtárak hozzáadása

Ez a cikk a külső kódtárak Power BI-vizualizációkban való használatát ismerteti. Információkat tartalmaz a külső kódtárak telepítéséről, importálásáról és a Power BI-vizualizáció kódjából való meghívásáról.

## <a name="javascript-libraries"></a>JavaScript-kódtárak

1. Telepítsen egy külső JavaScript-kódtárat egy tetszőleges csomagkezelő, például az *npm* vagy a *yarn* használatával.
2. Importálja a szükséges modulokat a forrásfájlokba a külső kódtárral.

>[!NOTE]
>Ha tipizálásokat szeretne hozzáadni a JavaScript-kódtárhoz, valamint intellisense és fordítási idejű biztonságot szeretne, ügyeljen rá, hogy a megfelelő csomagot telepítse.

### <a name="installing-the-d3-library"></a>A d3 kódtár telepítése

Íme egy példa a [d3 kódtár](https://www.npmjs.com/package/d3) és a [@types/d3](https://www.npmjs.com/package/@types/d3) csomag [npm](https://www.npmjs.com/) használatával való telepítésére.

A teljes példáért lásd a [Power BI-vizualizációk](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29) kódot.

1. Telepítse a *d3* és a *d3 típusok* csomagot.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importálja a *d3* kódtárat az azt használó fájlokba, például: `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS-keretrendszer

1. Telepítsen egy külső CSS-keretrendszert egy tetszőleges csomagkezelő, például az *npm* vagy a *yarn* használatával.
2. Foglalja bele az `import` utasítást a vizualizáció `.less` fájljába.

### <a name="installing-bootstrap"></a>Bootstrap telepítése

Íme egy példa a [bootstrap](https://www.npmjs.com/package/bootstrap) telepítésére az [npm](https://www.npmjs.com/) használatával.

A teljes példáért lásd a [Power BI-vizualizációk](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32) kódot.

1. Telepítse a *bootstrap* csomagot.

    ```powershell
    npm install bootstrap --save
    ```

2. Foglalja bele az `import` utasítást a következőbe: `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
