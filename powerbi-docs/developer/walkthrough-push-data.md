---
title: Adatok elküldése adatkészletbe
description: Adatok elküldése Power BI-adatkészletbe
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222156"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Adatok elküldése Power BI-adatkészletbe

A Power BI API lehetővé teszi adatok leküldése a Power BI-adatkészletbe. Ebben a cikkben bemutatjuk, hogyan küldhet be egy meglévő adatkészlet egy termék táblát tartalmazó értékesítési Marketing adatkészletet.

Az első lépések előtt kell egy Azure Active Directory (Azure AD) és a egy [Power BI-fiókja](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Adatok adatkészletbe történő elküldésének lépései

* 1. lépés: [Alkalmazás regisztrálása az Azure AD-ben](walkthrough-push-data-register-app-with-azure-ad.md)
* 2. lépés: [Hitelesítési hozzáférési token beszerzése](walkthrough-push-data-get-token.md)
* 3. lépés: [Adatkészlet létrehozása a Power BI-ban](walkthrough-push-data-create-dataset.md)
* 4. lépés: [Adatkészlet lekérése, és sorok hozzáadása egy Power BI-táblához](walkthrough-push-data-get-datasets.md)
* 5. lépés: [Sorok hozzáadása egy Power BI-táblához](walkthrough-push-data-add-rows.md)

A következő szakasz egy általános ismertetés az adatok küldésére használható Power BI API-műveletekről.

## <a name="power-bi-api-operations-to-push-data"></a>Adatok küldésére használt Power BI API-műveletek

A Power BI REST API-val adatforrásokat küldhet a Power BI-ba. Amikor egy alkalmazás sorokat ad hozzá egy adatkészlethez, irányítópult-csempék frissítés automatikusan az új adatokkal. Az adatok leküldéséhez használja a [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) és [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows) műveleteket. Egy adatkészlet kereséséhez használja a [adatkészletek lekérése](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) műveletet. Megadhat egy csoportot a fenti műveletek bármelyike dolgozni egy csoport azonosítója. Egy azonosító listájának lekéréséhez használja a [csoportok lekérése](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) műveletet.

Az adatok adatkészletbe történő elküldéséhez használható műveletek az alábbiak:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Adatkészletek lekérése](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Csoportok lekérése](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Adatkészletet úgy hozhat létre a Power BI-ban, hogy átad egy JavaScript Object Notation- (JSON-) sztringet a Power BI szolgáltatásnak. További információt a JSON-karakterláncokról [a JSON ismertetésében](http://json.org/) talál.

Az adatkészletek JSON-sztringjének formátuma a következő:

**Power BI-adatkészlet JSON-objektuma**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Értékesítési Marketing adatkészletet példa ahogy az alábbi JSON-karakterláncot kellene átadnia. Ebben a példában **SalesMarketing** az adatkészlet neve, és **termék** a tábla neve. A tábla meghatározása, után határozza meg a következő tábla sémáját. A **SalesMarketing** adatkészlet esetében a táblaséma az alábbi oszlopokat tartalmazza: ProductID (Termékazonosító), Manufacturer (Gyártó), Category (Kategória), Segment (Szegmens), Product (Termék) és IsComplete (Kész állapot).

**Példa adatkészlet-objektum JSON-ra**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Power BI-táblaséma esetén az alábbi adattípusok használhatók.

## <a name="power-bi-table-data-types"></a>Power BI-tábla adattípusai

| **Adattípus** | **Korlátozások** |
| --- | --- |
| Int64 |Az Int64.MaxValue és Int64.MinValue érték nem engedélyezett. |
| Double |A Double.MaxValue és Double.MinValue érték nem engedélyezett. Nem támogatott NaN. + Infinity és - Infinity értékek nem támogatottak egyes függvényekben (például, Min, Max). |
| Logikai érték |Nincsenek |
| Datetime |Adatok betöltése során kvantáljuk az értékeket a 1/300 másodperc (3,33 ezredmásodperc) egész többszöröseiként. |
| Sztring |Jelenleg lehetővé teszi, hogy legfeljebb 128 ezer karakter hosszú lehet. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>További információk az adatoknak a Power BI-ba leküldésével kapcsolatban

Az adatok adatkészletekbe történő küldésének első lépéseihez tekintse meg a bal oldali navigációs ablaktábla [1. lépés: Alkalmazás regisztrálása az Azure AD-ben](walkthrough-push-data-register-app-with-azure-ad.md) című szakaszát.

[Következő lépés >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Következő lépések

[Regisztráció a Power BI-ra](create-an-azure-active-directory-tenant.md)  
[A JSON ismertetése](http://json.org/)  
[A Power BI REST API áttekintése](overview-of-power-bi-rest-api.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)