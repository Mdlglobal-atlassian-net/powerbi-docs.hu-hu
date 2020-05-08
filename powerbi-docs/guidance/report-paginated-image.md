---
title: Útmutató képek többoldalas jelentésekben való használatához
description: Útmutató képek többoldalas Power BI-jelentésekben való használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d2f3f36911c72df1b95ceb5bd90043870559cc62
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920709"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Útmutató képek többoldalas jelentésekben való használatához

Ez a cikk a [többoldalas](../paginated-reports/paginated-reports-report-builder-power-bi.md) Power BI-jelentéseket megtervező jelentéskészítők számára készült. Képekkel való munkavégzéskor javaslatokat jelenít meg. Általában a jelentéselrendezésekben szereplő képek grafikákat, például vállalati emblémákat vagy képeket jeleníthetnek meg.

A képek három különféle helyen tárolhatók:

- A jelentésben (beágyazott)
- Egy webkiszolgálón
- Egy adatbázisban, amely egy adathalmaz által lekérdezhető

Ezek azután többféle forgatókönyv szerint is használhatók a jelentéselrendezésekben:

- Önálló embléma vagy kép
- Adatsorokhoz rendelt kép
- Bizonyos jelentéselemek háttere:
  - A jelentés törzse
  - Szövegmező
  - Téglalap
  - Rácsos adatrégió (tábla, mátrix vagy lista)

## <a name="suggestions"></a>Javaslatok

Vegye fontolóra a következő javaslatokat, ha professzionális jelentéselrendezéseket, könnyű karbantarthatóságot és optimalizált jelentésteljesítményét szeretne elérni:

- **Használja a lehető legkisebb méretet**: Javasoljuk, hogy olyan képeket készítsen, amelyek kisméretűek, de mégis élesnek látszanak. Mindez a minőség és a méret közötti egyensúlyon múlik. Fontolja meg egy grafikus szerkesztőprogram (például az MS Paint) használatát a kép méretének csökkentésére.
- **Kerülje a beágyazott képek használatát**: Először is a beágyazott képek megnövelhetik a jelentés fájlméretét, amely hozzájárulhat a jelentések lassúbb megjelenítéséhez. Másodszor, a beágyazott képek gyorsan karbantartási rémálommá válhatnak, ha sok képet kell frissítenie a jelentésben (amire szükség lehet a vállalati embléma megváltozásakor).
- **Webkiszolgálón való tárolás használata**: A képek webkiszolgálón való tárolása jó választási lehetőség, különösen a vállalati embléma esetében, amelyet betölthet a vállalat webhelyéről. Azonban vegye figyelembe, hogy a jelentés felhasználói a hálózaton kívülről is hozzáférhetnek-e a jelentésekhez. Ebben az esetben gondoskodjon róla, hogy a képek elérhetők legyenek az interneten.

    Ha a képek az adatokra (például az értékesítési munkatársak képei) vonatkoznak, úgy nevezze el a képfájlokat, hogy a jelentéskifejezés dinamikusan elkészíthesse a kép URL-címét. Elnevezheti például az értékesítési munkatársak képeit az egyes munkatársak alkalmazotti azonosítóit felhasználva. Feltéve, hogy a jelentés adathalmaza lekéri az alkalmazotti azonosítót, írhat egy olyan kifejezést, amely elkészíti a kép teljes URL-címét.
- **Adatbázistár használata**: Ha a relációs adatbázis képadatokat tárol, észszerű a képi adatokat közvetlenül az adatbázistáblákból betölteni – különösen, ha a képek nem túl nagyok.
- **Megfelelő háttérképek**: Ha úgy dönt, hogy háttérképeket használ, ügyeljen rá, hogy ezek ne vonják el a jelentés felhasználóinak figyelmét a jelentés adatairól. 

    Használjon _vízjel stílusú képeket_. A vízjel stílusú képek általában transzparens háttérrel rendelkeznek (vagy a jelentés által használt háttérszínnel). Halvány színeket is használnak. A vízjel stílusú képekre gyakori példa a vállalati embléma vagy az adatok bizalmasságára utaló címkék, például „Vázlat” vagy „Bizalmas”.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Mik a lapszámozott jelentések a Power BI Premiumban?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
