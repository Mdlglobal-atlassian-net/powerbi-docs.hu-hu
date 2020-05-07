---
title: Adathalmazok több munkaterületen való használatának szabályozása (előzetes verzió) – Power BI
description: Útmutató a Power BI-bérlőn belüli információáramlás szabályozásához.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d1ad29bebc148d9f30e8d22240dd149787251a0a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872584"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>Adathalmazok több munkaterületen való használatának szabályozása (előzetes verzió)

Az adathalmazok több munkaterületen való felhasználása hatékony mód a vállalaton belüli adatkultúra és a közös adathasználat fejlesztésére. A Power BI-rendszergazdák számára olykor mégis ajánlott korlátozni a Power BI-bérlőn belüli információáramlást. Az **Adathalmazok használata több munkaterületen** bérlői beállítással teljesen, vagy biztonsági csoportonként részlegesen korlátozni tudja az adathalmazok újbóli felhasználását.

![Power BI-rendszergazdai munkaterület-beállítások](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Ha ezt a beállítást kikapcsolja, a jelentéskészítők a következőket tapasztalják:

- A jelentések munkaterületek közötti másolására szolgáló gomb nem érhető el. 
- A megosztott adathalmazon alapuló jelentésekben nem érhető el a **Jelentés szerkesztése** gomb.
- A Power BI szolgáltatásban a felfedezési felületen csak az aktuális munkaterületen lévő adathalmazok jelennek meg.
- A Power BI Desktopban a felfedezési felületen csak olyan munkaterületekről származó adathalmazok jelennek meg, ahol Ön tag.
- Ha a felhasználók megnyitnak egy .pbix-fájlt a Power BI Desktopban, az pedig élő kapcsolattal rendelkezik egy adathalmazzal, amely kívül van minden munkaterületen, amelynek a tagjai, hibaüzenet szólítja fel őket, hogy csatlakozzanak másik adathalmazhoz.

## <a name="provide-a-link-for-the-certification-process"></a>Hivatkozás megadása a minősítési folyamathoz

Bérlői rendszergazdaként megadhat egy URL-címet a **Támogatás** beállítási lapján található **További információ** hivatkozáshoz.  Ez a hivatkozás a minősítési eljárás dokumentációjára mutathat. Ha nem adja meg a **További információ** hivatkozás célját, akkor az alapértelmezés szerint erre az [Adathalmaz minősítése](service-datasets-certify.md) című cikkre mutat.

![További információk az adathalmazok minősítéséről](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>További lépések

- [Adathalmazok használata több munkaterületen (előzetes verzió)](service-datasets-across-workspaces.md)
- Kérdései vannak? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)
