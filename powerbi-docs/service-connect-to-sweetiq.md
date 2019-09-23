---
title: Kapcsolódás a SweetIQ-hoz a Power BI-jal
description: SweetIQ a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 535a5b0d24abcd76d7c7b9becedad152e17829ed
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61159347"
---
# <a name="connect-to-sweetiq-with-power-bi"></a>Kapcsolódás a SweetIQ-hoz a Power BI-jal
A Power BI-tartalomcsomag a SweetIQ-fiókban található adatait használja, és előre elkészített tartalmakat generál, hogy egyszerűen feltárhassa az adatokat. A SweetIQ-tartalomcsomagot a helyeire, listáira, minősítéseire és értékeléseire vonatkozó adatok elemzésére használhatja. Az alapértelmezett beállítások szerint az adatok naponta frissülnek, hogy Ön mindig naprakész adatokat ellenőrizhessen.

Kapcsolódjon a Power BI-hoz készült [SweetIQ-tartalomcsomaghoz](https://app.powerbi.com/groups/me/getdata/services/sweetiq).

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs sávon kattintson az **Adatok lekérése** gombra.
   
    ![](media/service-connect-to-sweetiq/getdata.png)
2. Válassza a **SweetIQ** lehetőséget, és kattintson a **Beolvasás** gombra.
   
    ![](media/service-connect-to-sweetiq/sweetiq.png)
3. Adja meg a SweetIQ-beli ügyfél-azonosítóját. Ez általában egy alfanumerikus érték. Az érték megkeresésére vonatkozó további részleteket lásd alább.
   
    ![](media/service-connect-to-sweetiq/parameter.png)
4. Válassza a **Kulcs** hitelesítési típust, és adja meg a SweetIQ API-kulcsát. Ez általában egy alfanumerikus érték. Az érték megkeresésére vonatkozó további részleteket lásd alább.
   
    ![](media/service-connect-to-sweetiq/credentials.png)
5. A Power BI elkezdi betölteni az adatokat, ami eltarthat egy ideig a fiókban található adatok méretétől függően. Miután befejeződött a betöltés, a bal oldali navigációs ablaktáblán megjelenik egy új irányítópult, jelentés és adatkészlet.
   
    ![](media/service-connect-to-sweetiq/dashboard.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="finding-parameters"></a>Paraméterek helye
Ennek a tartalomcsomagnak az ügyfél-azonosítója és API-kulcsa nem azonos a SweetIQ-beli felhasználónevével és jelszavával.

Válassza az egyik olyan ügyfél azonosítóját, amelyhez a fiókja rendelkezik hozzáféréssel. Az ügyfelek listáját a SweetIQ-fiókja „Client Management” (Ügyfélkezelés) területén találja.

Az adott ügyfél adainak eléréséhez szükséges API-kulcs beszerzéséért beszéljen a rendszergazdával.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[Power BI – Adatok lekérése](service-get-data.md)

