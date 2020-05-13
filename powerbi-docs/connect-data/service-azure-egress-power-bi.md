---
title: A Power BI és az Azure kimenő forgalma
description: Ismerje meg az Azure kimenő forgalma után fizetendő díjakat és a Power BI-t, a bérlő helye és a Power BI Premium függvényében.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: b39812eb155d1d1c32ddba984986e5260f4b1ad1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302230"
---
# <a name="power-bi-and-azure-egress"></a>A Power BI és az Azure kimenő forgalma

Amikor a Power BI-t Azure-beli adatforrásokkal használja, elkerülheti az Azure kimenő forgalma után fizetendő díjakat, ha gondoskodik róla, hogy az Ön Power BI-bérlője az Azure-beli adatforrásokkal azonos régióban található.

Amennyiben az Ön Power BI-bérlője ugyanazon Azure-régióban van üzembe helyezve, mint az adatforrásai, nem kell kimenő forgalom után fizetendő díjakkal számolnia üzemezett frissítés és DirectQuery-interakciók esetén. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>A Power BI-bérlő helyének meghatározása

A Power BI-bérlő helyének meghatározásához lásd a [Power BI-bérlő helyének megállapítását](../admin/service-admin-where-is-my-tenant-located.md) ismertető cikket.

Power BI Premium Multi-Geo-ügyfelek esetén, ha a Power BI-bérlő nem az Azure-alapú adatforrásoknak megfelelő optimális helyszínen található, akkor a kívánt Azure-régióban üzembe helyezheti a Power BI Premium Multi-Geót, és ettől kezdve élvezheti az azonos Azure-régióban található Power BI-bérlő és Azure-beli adatforrások előnyeit.

## <a name="next-steps"></a>További lépések

Ha további információt szeretne kapni a Power BI Premiumról és a Multi-Geóról, tekintse meg a következő segédleteket:

* [Mi az a Microsoft Power BI Premium?](../admin/service-premium-what-is.md)
* [A Power BI Premium megvásárlása](../admin/service-admin-premium-purchase.md)
* [Multi-Geo-támogatás a Power BI Premiumhoz (előzetes verzió)](../admin/service-admin-premium-multi-geo.md)
* [Hol található a Power BI-bérlőm?](../admin/service-admin-where-is-my-tenant-located.md)
* [Power BI Premium – gyakori kérdések](../admin/service-premium-faq.md)
