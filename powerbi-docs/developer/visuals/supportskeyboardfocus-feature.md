---
title: A supportsKeyboardFocus funkció
description: Ez a cikk a supportsKeyboardFocus funkció Power BI-vizualizációkban való használatát és annak feltételeit ismerteti.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: c8cf0f4e896b8a44764d1c363c597182f55d30b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276513"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>A supportsKeyboardFocus funkció használata

Ez a cikk a `supportsKeyboardFocus` funkció Power BI-vizualizációkban való használatát ismerteti.
A `supportsKeyboardFocus` funkció lehetővé teszi a vizualizáció adatpontjaiban való navigációt kizárólag a billentyűzet használatával.

A billentyűzetnavigáció vizualizációkkal való használatával kapcsolatos további információért lásd: [Billentyűzetnavigáció](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Példa

Nyisson meg egy vizualizációt, amely a `supportsKeyboardFocus` funkciót használja. Válasszon ki a vizualizáción belül egy tetszőleges adatpontot, majd nyomja le a Tab billentyűt. A fókusz a Tab lenyomásakor mindig a következő adatpontra kerül. Nyomja le az Enter billentyűt a kiemelt adatpont kiválasztásához.

![SupportsKeyboardFocus-példa](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Követelmények

Ehhez a funkcióhoz 2.1.0-s vagy újabb verziójú API szükséges.

Ez a funkció a képek kivételével minden vizualizációra alkalmazható.

## <a name="usage"></a>Használat

A `supportsKeyboardFocus` funkció használatához adja hozzá az alábbi kódot a vizualizáció *capabilities.json* fájljához.
Ez a képesség lehetővé teszi a vizualizáció számára, hogy a billentyűzetnavigációval fókuszba kerüljön.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Következő lépések

További információ a kisegítő lehetőségekről: [Power BI-jelentések kisegítő lehetőségeinek megtervezése](../../create-reports/desktop-accessibility-creating-reports.md).

A Power BI-fejlesztés kipróbálásához tekintse meg a [Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md) című ismertetőt.
