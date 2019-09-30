---
title: Power BI-adatkészlet tulajdonságai
description: A Power BI-adatkészlet API-k tulajdonságainak megismerése
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 508f304e2f5033c301db683e3b7557856fb3731b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61386293"
---
# <a name="dataset-properties"></a>Adatkészlet tulajdonságai

Az adatkészletek API-jának jelenlegi v1 verziójában az adatkészlet létrehozása csak névvel és táblák gyűjteményével engedélyezett. Minden egyes tábla rendelkezhet névvel és oszlopok gyűjteményével. Minden oszlop rendelkezik egy névvel és adattípussal. Jelenleg bővítjük ezeket a tulajdonságokat, melyek közül a legfigyelemreméltóbb a mértékek és a táblák közötti kapcsolatok támogatása. Ebben a kiadásban támogatott tulajdonságok teljes listája a következő:

> [!IMPORTANT]
> Ez a [Datasets Operation Groups](https://docs.microsoft.com/rest/api/power-bi/datasets) (Adatkészletek, műveletcsoportok) oldalon érhető el.

## <a name="dataset"></a>Adathalmaz

Név  |Típus  |Leírás  |Csak olvasható  |Kötelező
---------|---------|---------|---------|---------
azonosító     |  Guid       | Az adatkészlet egész rendszerre kiterjedő, egyedi azonosítója.        | Igaz        | Hamis        
név     | Sztring        | Az adatkészlet felhasználó által meghatározott neve.        | Hamis        | Igaz        
táblák     | Table[]        | Táblagyűjtemény.        |  Hamis       | Hamis        
kapcsolatok     | Relationship[]        | Táblák közti kapcsolatok gyűjteménye.        | Hamis        |  Hamis  
defaultMode     | Sztring        | A „Push” és „Streaming” értékekkel meghatározza, hogy az adatkészlet továbbítása leküldéssel, streameléssel vagy mindkettővel történjen-e.         | Hamis        |  Hamis

## <a name="table"></a>Táblázat

Név  |Típus  |Leírás  |Csak olvasható  |Kötelező
---------|---------|---------|---------|---------
név     | Sztring        |  A tábla felhasználó által meghatározott neve. A tábla azonosítójaként is szolgál.       | Hamis        |  Igaz       
oszlopok     |  column[]       |  Oszlopgyűjtemény.       | Hamis        |  Igaz       
mértékek     | measure[]        |  Mértékgyűjtemény.       | Hamis        |  Hamis       
isHidden     | Logikai érték        | Ha az értéke igaz, a tábla rejtett lesz az ügyféleszközök elől.        | Hamis        | Hamis        

## <a name="column"></a>Oszlop

Név  |Típus  |Leírás  |Csak olvasható  |Kötelező
---------|---------|---------|---------|---------
név     |  Sztring        | Az oszlop felhasználó által meghatározott neve.        |  Hamis       | Igaz       
dataType     |  Sztring       |  Támogatott [EDM-adattípusok](https://msdn.microsoft.com/library/ee382832.aspx) és korlátozások. Lásd: [Adattípus-korlátozások](#DataTypeRestrictions).      |  Hamis       | Igaz        
formatString     | Sztring        | Egy sztring, amely leírja, hogyan kell formázni az értéket a megjelenésekor. A sztringek formázásáról további információért olvassa el a [FORMAT_STRING tartalmakat](https://msdn.microsoft.com/library/ms146084.aspx).      | Hamis        | Hamis        
sortByColumn    | Sztring        |   Ugyanazon tábla oszlopának a sztringneve, amelyet a jelenlegi oszlop elrendezésére használ.     | Hamis        | Hamis       
dataCategory     | Sztring        |  Az ebben az oszlopban lévő adatokat leíró adatkategóriához használható sztringérték. Néhány gyakori érték például: Address, City, Continent, Country, Image, ImageUrl, Latitude, Longitude, Organization, Place, PostalCode, StateOrProvince, WebUrl       |  Hamis       | Hamis        
isHidden    |  Logikai érték       |  Tulajdonság, amely azt jelzi, hogy az oszlop rejtett-e a nézetben. Az alapértelmezett értéke a hamis.       | Hamis        | Hamis        
summarizeBy     | Sztring        |  Alapértelmezett aggregációs módszer az oszlophoz. Értékek többek között: default, none, sum, min, max, count, average, distinctCount     |  Hamis       | Hamis

## <a name="measure"></a>Mérték

Név  |Típus  |Leírás  |Csak olvasható  |Kötelező
---------|---------|---------|---------|---------
név     | Sztring        |  A mérték felhasználó által meghatározott neve.       |  Hamis       | Igaz        
kifejezés     | Sztring        | Egy érvényes DAX-kifejezés.        | Hamis        |  Igaz       
formatString     | Sztring        |  Egy sztring, amely leírja, hogyan kell formázni az értéket a megjelenésekor. A sztringek formázásáról további információért olvassa el a [FORMAT_STRING tartalmakat](https://msdn.microsoft.com/library/ms146084.aspx).       | Hamis        | Hamis        
isHidden     | Sztring        |  Ha az értéke igaz, a tábla rejtett lesz az ügyféleszközök elől.       |  Hamis       | Hamis       

## <a name="relationship"></a>Kapcsolat

Név  |Típus  |Leírás  |Csak olvasható  |Kötelező 
---------|---------|---------|---------|---------
név     | Sztring        | A kapcsolat felhasználó által meghatározott neve. A kapcsolat azonosítójaként is szolgál.        | Hamis       | Igaz        
crossFilteringBehavior     | Sztring        |    A kapcsolat szűrőiránya: OneDirection (egyirányú) (alapértelmezett), BothDirections (kétirányú), Automatic (automatikus)       | Hamis        | Hamis        
fromTable     | Sztring        | A külső kulcs tábla neve.        | Hamis        | Igaz         
fromColumn    | Sztring        | A külső kulcs oszlop neve.        | Hamis        | Igaz         
toTable    | Sztring        | Az elsődleges kulcs tábla neve.        | Hamis        | Igaz         
toColumn     | Sztring        | Az elsődleges kulcs oszlop neve.        | Hamis        | Igaz        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Adattípus-korlátozások (a dataType tulajdonságra vonatkozik)

Adattípus  |Korlátozások  
---------|---------
Int64     |   Az Int64.MaxValue és Int64.MinValue érték nem engedélyezett.      
Double     |  A Double.MaxValue és Double.MinValue érték nem engedélyezett. A számtól eltérő értékek (NaN) nem támogatottak. +Infinity és -Infinity értékek nem támogatottak egyes függvényekben (pl.: Min, Max).       
Logikai érték     |   Igaz vagy hamis.
Datetime    |   Az adatok betöltése során kvantáljuk az értékeket a napok törtrészével az 1/300 másodperc (3,33 ms) egész többszörösévé.      
Sztring     |  Jelenleg akár 4000 karaktert is lehetővé tesz sztringértékenként.
Tizedes tört|precision=28, scale=4

## <a name="example"></a>Példa
A következő mintakód tartalmaz néhányat ezek közül a tulajdonságok közül:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```