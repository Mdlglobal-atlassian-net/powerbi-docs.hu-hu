---
title: Tippek és trükkök Q&A-kérdések feltevéséhez
description: Tippek és trükkök Q&A-kérdések feltevéséhez a Power BI-ban
author: mihart
ms.reviewer: Mohammad
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: d97ff72c385edd4c59c6eb72ce1eb873656923c9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79376822"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Tippek kérdések feltevéséhez a Power BI Q&A-ben

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Szavak és kifejezések, amelyeket a Q&A felismer
Az oldalon található kulcsszavak listája nem teljes.  A legjobban úgy ellenőrizheti, hogy a Power BI felismer-e egy adott kulcsszót, hogy megpróbálja azt beírni a kérdésmezőbe.  Ha a szó vagy kifejezés szürkén jelenik meg, az azt jelenti, hogy a Power BI nem ismeri fel.

Az alábbi lista jelen idejű kifejezéseket tartalmaz, de a rendszer a legtöbb esetben az összes igealakot felismeri. Például az angol nyelvű „is” ige magában foglalja a következő igealakokat is: **are**, **was**, **were**, **will be**, **have**, **has**, **had**, **will have**, **has got**, **do**, **does**, **did**.  A „sort” ige pedig magában foglalja a **sorted** és a **sorting** alakokat is.  A Power BI felismeri és magában foglalja a szavak többes és egyes számú verzióit is. 

> [!NOTE]
> A Q&A szolgáltatás a [Microsoft Power BI iOS-hez készült alkalmazásában iPadeken, iPhone-okon, és iPod Touch eszközökön](mobile/mobile-apps-ios-qna.md) is rendelkezésre áll.
>  


|Kategória  |Kulcsszavak  |3\. oszlop  |
|---------|---------|---------|
|**Összesítések**     | total, sum, amount, number, quantity, count, average, most, least, fewest, largest, smallest, highest, biggest, maximum, max, greatest, lowest, littlest, minimum, min          |
|     |         |         
**Névelők**     |  a, an, the              |
|     |         |         
|**Üres és logikai értékek**     |   blank, empty, null, „non” vagy „non-” előtaggal, empty string, empty text, true, t, false, f          |
|     |         |         |
|**Összehasonlítások**     |   vs, versus, compared to, compared with            |
|     |         |         |
|**Kötőszavak**     |  and, or, each of, with, versus, &, and, but, nor, along with, in addition to       |         
|          |         |
|**Összevonásokat**     |  A Q&A szinte minden összevonást felismer, próbálja csak ki.  Íme néhány angol nyelvű példa: didn’t, haven’t, he’d, he’s, isn’t, it’s, she’ll, they’d, weren’t, who’s, won’t, wouldn’t          |
|        |         |
|**Dátumok**     |       A Power BI felismeri a legtöbb dátummal kapcsolatos angol nyelvű kifejezést (day, week, month, year, quarter, decade stb.), valamint a különböző formátumokban írt dátumokat is (lásd alább). A Power BI felismeri a következő kulcsszavakat: MonthName, Days 1-31, decade. Angol nyelvű Példák: January 3rd of 1995, January 3rd 1995, jan 03 1995, 3 Jan 1995, the 3rd of January, January 1995, 1995 January, 1995-01, 01/1995, hónapok nevei         |
|        |         |
|**Angol nyelvű relatív dátumok**     |   today, right now, current time, yesterday, tomorrow, the current, next, the coming, last, previous, ago, before now, sooner than, after, later than, from, at, on, from now, after now, in the future, past, last, previous, within, in, over, N days ago, N days from now, next, once, twice.|
|    |  Angol nyelvű példa: count of orders in the past 6 days.  |            |
|        |         |
|**Egyenlőség (tartomány)**     |   in, equal to, =, after, is more than, in, between, before  |
|  |Angol nyelvű Példák: Order year is before 2012? Price equals between 10 and 20? Is the age of John greater than 40? Total sales in 200-300?              |
|        |         |
|**Egyenlőség (érték)**     |   is, equal, equal to, in, of, for, within, is in, is on |
|   | Angol nyelvű Példák: Which products are green (Mely termékek zöldek)? Order date equals 2012. Is the age of John 40? Total sales that is not equal to 200? Order date of 1/1/2016. 10 in price? Green for color? 10 in price?              |
|        |         |
|**Nevek**     |       Ha az adatkészlet egy oszlopa tartalmazza a „name” kifejezést (például EmployeeName formában), a Q&A észlelni fogja, hogy az oszlop értékei neveket tartalmaznak. Feltehet ilyen kérdést is például: „which employees are named robert.”          |
|        |         |
**Névmások**  | he, him, himself, his, she, herself, her, hers, it, itself, its, they, their, them, themselves, theirs, this, these, that, those
|**Lekérdezési parancsok**     |    sorted, sort by, direction, group, group by, by, show, list, display, give me, name, just, only, arrange, rank, compare, to, with, against, alphabetically, ascending, descending, order             |
|        |         |
|**Tartomány**     |      greater, more, larger, above, over, >, less, smaller, fewer, below, under, <,  at least, no less than, >=, at most, no more than, <=, in, between, in the range of, from, later, earlier, sooner, after, on, at, later than, after, since, starting with, starting from, ending with           |
|        |         |
**Időszakok**  |am, pm, o'clock, noon, midnight, hour, minute, second, hh:mm:ss  |
|  |  Angol nyelvű Példák: 10 pm, 10:35 pm, 10:35:15 pm, 10 oclock, noon, midnight, hour, minute, second.  |
|  |  |
|**Felső N**     |     (rendezés, rangsorolás): top, bottom, highest, lowest, first, last, next, earliest, newest, oldest, latest, most recent, next            |
|        |         |
|**Vizualizációtípusok**     |  A Power BI minden vizualizációs típust natívan támogat.  Ha a Megjelenítések ablaktábla egyik beállításáról van szó, szerepelhet a kérdésben.  A kivételt ez alól a szabály alól a [Power BI-vizualizációk](../developer/visuals/power-bi-custom-visuals.md) képezik, amelyeket manuálisan vett fel a Megjelenítések ablaktáblán.  |
|  |  Angol nyelvű példa: show districts by month and sales total as bar chart               |
|        |         |
|**Kérdőszavak (kapcsolat, minősített)**  | when, where, which, who, whom, how many, how much, how many times, how often, how frequently, amount, number, quantity, how long, what                |

## <a name="qa-helps-you-phrase-the-question"></a>A Q&A segít megfogalmazni a kérdést
A Q&A mindent elkövet, hogy a feltett kérdéseket megértse és válaszolni tudjon rá. A megértést többféleképpen megkísérli. Az összes ilyen kifejezés esetében a műveletet teljes mértékben, részletesen vagy egyáltalán nem lehet elfogadni. A kérdés beírásakor a Q&A az alábbiakat teszi:

* automatikusan kiegészíti a szavakat és a kérdéseket. Különböző stratégiákat használ, beleértve a felismert szavak, a tárolt kérdések és a korábban használt és érvényes válaszokat eredményező kérdések automatikus kiegészítését. Egynél több automatikus kiegészítés esetén a rendszer a lehetőségeket egy legördülő listában jeleníti meg.
* kijavítja a helyesírási hibákat.
* vizualizáció formájában jeleníti meg a válasz előnézetét. A vizualizáció a kérdés beírása és szerkesztése közben frissül (a rendszer nem várja meg, amíg a felhasználó lenyomja az Enter billentyűt).
* helyettesítő kifejezéseket javasol a mögöttes adatkészlet(ek)ből, ha a felhasználó a kurzort a kérdésmezőbe helyezi.
* újrafogalmazza a kérdést a mögöttes adatkészlet(ek) adatai alapján. A Q&A a használt szavakat a mögöttes adatkészlet(ek)ben található szinonimákra cseréli le. A kifejezés elolvasásával ellenőrizheti, hogy a Q&A megértette-e a kérdést. 
* dupla aláhúzással jelöli a szavakat, amelyeket nem tud értelmezni.
* egyszeres aláhúzással jelöli a szavakat, amelyeket értelmezni tud.
* lehetővé teszi, hogy felvegye a kapcsolatot a jelentés vagy az irányítópult tulajdonosával, ha a kifejezés nem található vagy a kérdésre nem érkeznek eredmények.

## <a name="dont-stop-now"></a>Nincs megállás
Miután a Q&A megjeleníti az eredményeket, folytathatja a beszélgetést! A vizualizáció és a Q&A interaktív funkcióinak használatával további betekintést kaphat az adatokba.

## <a name="next-steps"></a>Következő lépések
Vissza a [Q&A a Power BI-ban](end-user-q-and-a.md) című témakörhöz  

[Power BI – Alapfogalmak](end-user-basic-concepts.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

