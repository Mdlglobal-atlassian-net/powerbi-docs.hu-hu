---
title: Csatlakozás a UserVoice-hoz a Power BI-ban
description: UserVoice a Power BI-ban
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a12f2821108c5becaf054680e4395295f0979f0b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61171593"
---
# <a name="connect-to-uservoice-with-power-bi"></a>Csatlakozás a UserVoice-hoz a Power BI-ban
A UserVoice-adatok egyszerűen nyomon követhetők és megvizsgálhatók aPower BI és a UserVoice-tartalomcsomag használatával. A Power BI beolvassa az adatokat, köztük a jegyeket, javaslatokat és elégedettségi mutatókat, majd az adatok alapján használatra kész irányítópultot és jelentéseket hoz létre.

Kapcsolódás a [UsreVoice-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/uservoice) a Power BI-ban.

>[!NOTE]
>A Power BI-tartalomcsomaghoz való kapcsolódáshoz rendszergazdai fiók szükséges. A tartalomcsomag a UserVoice API-t is felhasználja és a UserVoice használati keretéhez adódik. A részleteket alább találja.

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-uservoice/pbi_getdata.png)
2. A **Szolgáltatások** keretben kattintson a **Beolvasás** elemre.
   
   ![](media/service-connect-to-uservoice/pbi_getservices.png) 
3. Válassza a **UserVoice**, majd a **Beolvasás** lehetőséget.
   
   ![](media/service-connect-to-uservoice/uservoice.png)
4. Amikor a rendszer kéri, adja meg UserVoice URL-címét. Az URL-címnek pontosan meg kell felelnie a következő mintának: `https://fabrikam.uservoice.com` (a „fabrikam” helyén a saját terméke vagy szolgáltatása nevével).
   
   >[!NOTE]
   >A cím végén nincs lezáró perjel, és a kapcsolati séma http**s**.
   
   ![](media/service-connect-to-uservoice/capture.png)
5. Amikor a rendszer kéri, adja meg saját UserVoice-beli hitelesítő adatait, majd haladjon végig a UserVoice hitelesítési folyamatán. Ha már bejelentkezett a UserVoice-ba a böngészőjében, akkor a rendszer nem feltétlenül kéri a hitelesítő adatait. A "Hozzáférés engedélyezése" gombra kattintva adjon a Power BI-alkalmazásnak hozzáférést az adataihoz.
   
   >[!NOTE]
   >A UserVoice-fiókja használatához rendszergazdai hitelesítő adatok szükségesek.
   
   ![](media/service-connect-to-uservoice/capture3.png)
6. A Power BI betölti a UserVoice-adatokat, és használatra kész irányítópultot és jelentést hoz létre. A Power BI a következő adatokat tölti be: minden javaslatot, minden nyitott jegyet, az utolsó 30 nap folyamán létrehozott összes jegyet a lezártakkal együtt, és az összes ügyfél-elégedettségi mutatót.
   
   ![](media/service-connect-to-uservoice/capture4.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="troubleshooting"></a>Hibaelhárítás
**"Parameter validation failed, please make sure all parameters are valid"** (A paraméterek érvényesítése sikertelen, ellenőrizze az összes paraméter érvényességét)

Ha ezt a hibaüzenetet kapja a UserVoice URL-címe begépelése után, akkor győződjön meg a következő követelmények teljesüléséről:

* Az URL-cím pontosan megfelel a következő mintának: `https://fabrikam.uservoice.com` (a „fabrikam” helyén a saját helyes UserVoice-os URL-előtagjával).
* Minden betű kisbetű.
* Az URL-cím sémája 'http**s**'.
* Az URL-cím vége nincs perjellel lezárva.

**"Login failed"** (Sikertelen bejelentkezés)

Ha "Sikertelen bejelentkezés" hibaüzenetet kap a UserVoice hitelesítő adatai megadása után, akkor a használt fióknak nincs jogosultsága UserVoice-adatokat lekérni az Ön fiókjából. Ellenőrizze, hogy rendszergazdai fiókot használ-e, és próbálkozzon újra.

"**Oops something went wrong**" (Hoppá! Hiba történt.)

Ha ez a hibaüzenet jelenik meg az adatok betöltésekor, akkor ellenőrizze, hogy a UserVoice-fiókja nem lépte-e túl a havi API-használati keretét. Ha mindent rendben talál, akkor próbáljon meg újra kapcsolódni. Ha a probléma továbbra is fennáll, keresse fel a Power BI támogatási oldalát: [https://community.powerbi.com](https://community.powerbi.com/).

**Egyéb**  

A Power BI UserVoice-tartalomcsomag a UserVoice API-jait használja az adatok betöltéséhez. Kísérje figyelemmel az API-használatot, hogy túl ne lépje a keretét. Ha sok adat van a UserVoice-fiókja alatt, akkor az API-használat minimalizálása érdekében ajánlott a jelenleg alapértelmezett naponta egyszeri frissítést átállítani úgy, hogy csak munkanapokon vagy csak kétnaponta történjen meg, ahogyan Önnek megfelel. Egy másik javaslat, hogy csak egy rendszergazda hozza létre a tartalomcsomagot és ossza meg a csapat többi tagjával. Ha a cég összes rendszergazdája saját tartalomcsomagot hoz létre, akkor szükségtelenül terhelik az API-kat.

## <a name="next-steps"></a>További lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

