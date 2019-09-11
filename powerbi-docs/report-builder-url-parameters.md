---
title: URL-paraméterek lapszámozott jelentésekben – Power BI jelentéskészítő
description: Ez a témakör sok más mellett a Power BI Lapszámozott jelentéskészítő jelentésparamétereinek gyakori használati módjait és a beállítható tulajdonságokat ismerteti.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: bda35bfb4690d8109f7bd611e3d319278d235f33
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302674"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>URL-paraméterek lapszámozott jelentésekben a Power BI-ban

A Power BI-ban a lapszámozott jelentésekhez parancsokat is küldhet, ha hozzáad egy paramétert egy URL-címhez. Előfordulhat például, hogy a jelentést a jelentésparaméter megadott értékeinek egy adott csoportja alapján tekintette meg. Ezeket az információkat az URL-címben előre definiált URL-hozzáférési paraméterek használatával ágyazhatja be. Paraméterek beágyazásával azt is testre szabhatja, hogy a Power BI hogyan dolgozza fel a jelentést, illetve hogyan jelenjen meg és hogyan működjön a jelentés eszköztára. Ezt az URL-címet közvetlenül egy e-mailbe vagy weblapra is beillesztheti, így másoknak is ugyanúgy jelenik meg a jelentés, ahogy a böngészőben. 

Az URL-hozzáférési paraméterek használatával az alábbi műveletek hajthatók végre: 

- Jelentés paramétereinek küldése jelentésbe. 
- A jelentéstartalom exportálásának kezdeményezése támogatott fájlformátumban. 
- A Paraméterek panel elrejtése vagy megjelenítése. 
- DeviceInfo-beállítás megadása. 

Az URL-hozzáférésen keresztül elérhető parancsok és beállítások teljes listáját a jelen cikk  [URL-cím hozzáférési paramétereinek referenciája](#url-access-parameter-reference) szakaszában találja meg. 

## <a name="url-access-concepts"></a>URL-hozzáférési fogalmak 

A Power BI-ba irányuló URL-kérelmek olyan paramétereket tartalmaznak, melyeket a szolgáltatás feldolgoz. Az, hogy a szolgáltatás hogyan dolgozza fel az URL-kérelmeket, attól függ, hogy az URL-cím milyen paramétereket, paraméter-előtagokat és milyen típusú elemeket tartalmaz. A lapszámozott jelentés URL-funkciója kompatibilis a legtöbb böngészővel és az olyan alkalmazásokkal, amelyek támogatják a szabványos URL-címzés használatát. 

## <a name="url-access-syntax"></a>Az URL-hozzáférés szintaxisa 

Az URL-kérelmek több paramétert is tartalmazhatnak, amelyeket tetszőleges sorrendben lehet felsorolni. A paramétereket „és” jellel (&) választjuk el egymástól. A név-érték párokat egyenlőségjellel (=) választjuk el egymástól. Például:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>szintaxis leírása 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

A Power BI-bérlő webszolgáltatási URL-címe. Például: 

Az **&** az URL-hozzáférési paraméterekben a név-érték párokat választja el egymástól.

**prefix** Az URL-paraméter előtagja (például rp: vagy rdl:), amely a műveletet határozza meg a Power BI szolgáltatásban. 

> [!NOTE]
> A jelentésparamétereknél meg kell adni egy paraméter-előtagot, amelyben megkülönböztetjük a kis- és nagybetűket. 

**parameter** A paraméter neve. 

### <a name="value"></a>value 

A használt paraméter értékének megfelelő URL-szöveg. 

A jelentés paramétereinek az URL-címnek való átadásával kapcsolatos példákért lásd:  [Jelentésparaméter átadása URL-címben.](report-builder-url-pass-parameters.md)

## <a name="url-access-parameter-reference"></a>URL-cím hozzáférési paramétereinek referenciája

Az URL-cím részeként a következő paramétereket használhatja a lapszámozott jelentések megjelenésének és működésének konfigurálásához Power BI-ban. A leggyakoribb paraméterek ebben a részben találhatók. A paraméterek nem különböztetik meg a kis- és nagybetűket, és az  `rdl:`  paraméter-előtaggal kezdődnek, ha a kimeneti formátumhoz kapcsolódnak.  

### <a name="report-commands-rdl"></a>Jelentésparancsok (`rdl:`) 

Az **exportálási formátum** azt határozza meg, hogy milyen formátumban jelenjen meg és legyen exportálva a jelentés. Lehetséges értékek: 
- PPTX (PowerPoint)
- MHTML 
- KÉP 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>Következő lépések

- [Jelentésparaméter átadása URL-címben lapszámozott jelentéshez a Power BI-ban](report-builder-url-pass-parameters.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
