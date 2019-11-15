---
title: Kapcsolódás az Office365Mon tartalomcsomaghoz a Power BI-jal
description: A Power BI-hoz készült Office365Mon tartalomcsomag
author: teddybercovitz
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 8/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: 64e8365a6d4e0c01911de9e69998af4d58d59202
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73854719"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Kapcsolódás az Office365Mon tartalomcsomaghoz a Power BI-jal
Az Office 365 leállásainak és az állapot teljesítményadatainak elemzése egyszerű a Power BI-jal és az Office365Mon sablonalkalmazással. A Power BI lekéri az adatokat, többek között a leállásokat és az állapotmintákat, majd ezeken az adatokon alapuló, használatra kész irányítópultot és jelentéseket hoz létre.

Csatlakozzon a Power BI-hoz készült [Office365Mon sablonalkalmazáshoz](https://app.powerbi.com/groups/me/getdata/services/office365mon).

>[!NOTE]
>A Power BI-sablonalkalmazás betöltéséhez Office365Mon rendszergazdai fiók szükséges.

## <a name="how-to-connect"></a>Csatlakozás
1. Kattintson az **Adatok lekérése** elemre a navigációs panel alján.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Kattintson az **Office365Mon** \> **Get** (Beolvasás) gombra.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Az Authentication Method (Hitelesítési módszer) beállításnál válassza az **oAuth2** \> beállítást, majd a **Sign In** (Bejelentkezés) elemet.
   
   Amikor a rendszer kéri, adja meg az Office365Mon rendszergazdai hitelesítő adatait, majd haladjon végig a hitelesítési folyamaton.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Miután a Power BI importálta az adatokat, megjelenik egy új irányítópult, jelentés és adathalmaz a navigációs panelen. Az új elemeket egy sárga csillag jelöli \*, válassza ki az Office365Mon bejegyzést.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="troubleshooting"></a>Hibaelhárítás
Ha **„Sikertelen bejelentkezés”** hibaüzenetet kap az Office365Mont hitelesítő adatai megadása után, akkor a használt fióknak nincs jogosultsága az Office365Mon-adatokat lekérni az Ön fiókjából. Ellenőrizze, hogy rendszergazdai fiókot használ-e, és próbálkozzon újra.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](fundamentals/power-bi-overview.md)

[Power BI – Adatok lekérése](service-get-data.md)

