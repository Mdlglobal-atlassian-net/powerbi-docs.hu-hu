---
title: URL-paraméterek lapszámozott jelentésekben – Power BI jelentéskészítő
description: Ez a témakör sok más mellett a Power BI Report Builder jelentésparamétereinek gyakori használati módjait és a beállítható tulajdonságokat ismerteti.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: 83de843ba640bc165e9a56450bc5539e8e433e78
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82692851"
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

## <a name="syntax-description"></a>Szintaxisleírás 

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

Az **exportálási formátum** azt határozza meg, hogy milyen formátumban jelenjen meg és legyen exportálva a jelentés.

Például: rdl:format=PDF

Lehetséges értékek:
 
- PPTX (PowerPoint)
- MHTML 
- KÉP 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

**Paraméterpanel állapota** – Megadja, hogy a jelentés betöltésekor a paraméterpanel meg van nyitva, be van zárva, vagy teljesen rejtett.

-   rdl:parameterPanelState

    - „collapsed” (összecsukva): bezárt paraméterpanellel nyitja meg a jelentést. A paraméter gomb engedélyezve van, hogy a felhasználók a gombra kattintva kibonthassák;
    - „hidden” (rejtett): bezárt paraméterpanellel nyitja meg a jelentést, és a paraméter gomb le van tiltva;
    - „expanded” (kibontva, alapértelmezés): megnyitott paraméterpanellel nytja meg a jelentést és a paraméter gomb engedélyezve van;

**Eszközinformáció** – További kimeneti paramétereket adhat meg az alábbi exportálási formátumhoz. 

PDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:FileExtension=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:FileExtension=string
- rdl:Schema=true/false

## <a name="next-steps"></a>Következő lépések

- [Jelentésparaméter átadása URL-címben lapszámozott jelentéshez a Power BI-ban](report-builder-url-pass-parameters.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
