---
title: A Power BI integrációja a Power Automate-tel
description: Elsajátíthatja, hogy miként hozhat létre Power BI-adatokkal kapcsolatos riasztások által kiváltott Power Automate-folyamatokat.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: aafba825c5bd4ece3c8b97256d5943f91b456cd7
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609697"
---
# <a name="power-automate-and-power-bi"></a>A Power Automate és a Power BI

A [Power Automate](https://docs.microsoft.com/power-automate/getting-started) egy olyan SaaS-ajánlat, amely a munkafolyamatok automatizálásához használható egyre több olyan alkalmazásban és SaaS-szolgáltatásban, amelyre a vállalati felhasználók támaszkodnak. A Power Automate használatával kedvenc alkalmazásait és szolgáltatásait (többek között a Power BI-t) integrálva feladatokat automatizálhat értesítések kéréséhez, fájlok szinkronizálásához, adatgyűjtéshez és még sok egyébhez. A munkafolyamatok automatizálásával egyszerűbben végezhetők el az ismétlődő feladatok.

[A Power Automate használatbavétele](https://docs.microsoft.com/power-automate/getting-started)

Megnézheti, hogy miként hoz létre Sirui egy olyan Power Automate-folyamatot, amely részletes e-mailt küld a munkatársaknak, amikor valami riasztást vált ki a Power BI-ban. Ezután a videó alatt látható részletes utasításokat követve próbálkozzon meg a feladat elvégzésével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Power BI-adatriasztás által indított folyamat létrehozása

### <a name="prerequisites"></a>Előfeltételek
Ez az oktatóanyag bemutatja, hogyan hozzon létre két különböző folyamatot; az egyiket sablonból, a másikat teljesen az alapoktól. Ennek követéséhez [hozzon létre egy adatriasztást a Power BI-ban](service-set-data-alerts.md), hozzon létre egy ingyenes Slack-fiókot, majd [regisztráljon a Power Automate-re](https://flow.microsoft.com/#home-signup) (ingyenes!).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Power BI-t használó folyamat létrehozása sablonból
Ebben a feladatban sablonnal létrehozunk egy egyszerű folyamatot, amelyet egy Power BI-adatokkal kapcsolatos riasztás (értesítés) vált ki.

1. Jelentkezzen be a Power Automate-be (flow.microsoft.com).
2. Kattintson a **Saját folyamatok** lehetőségre.
   
   ![A Power Automate menüsora](media/service-flow-integration/power-bi-my-flows.png)
3. Kattintson a **Létrehozás sablonból** lehetőségre.
   
    ![A saját folyamatok menüsora](media/service-flow-integration/power-bi-template.png)
4. A keresőmezőt használva keressen Power BI-sablonokat, majd válassza ki az **Adatvezérelt Power BI-riasztás esetén e-mail értesítés küldése bárkinek > Folytatás** lehetőséget.
   
    ![keresési eredmények](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>A folyamat létrehozása
Ez a sablon egy triggerből (Power BI-adatriasztás újabb ír olimpiai érem megszerzésekor) és egy műveletből (e-mail küldése) áll. Amikor kiválaszt egy mezőt, a Power Automate megjelenít némi dinamikus tartalmat, amelyet belefoglalhat az üzenetbe.  Ebben a példában a csempe értékét és URL-címét foglaljuk bele az üzenettörzsbe.

![folyamatsablon](media/service-flow-integration/power-bi-template1.png)

1. A triggerek legördülő menüjéből válassza ki a Power BI-adatriasztás lehetőséget. Válassza az **Új érem Írországnak** (New medal for Ireland) lehetőséget. A riasztások létrehozásával kapcsolatban tekintse meg a [Power BI-beli adatriasztásokról](service-set-data-alerts.md) szóló cikket.
   
   ![riasztás legördülő listája](media/service-flow-integration/power-bi-trigger-flow.png)
2. Adjon meg egy vagy több érvényes e-mail-címet, majd válassza a **Szerkesztés** lehetőséget (lásd alább) vagy a **Dinamikus tartalom hozzáadása** lehetőséget. 
   
   ![E-mail küldése képernyő](media/service-flow-integration/power-bi-flow-email.png)

3. A Power Automate létrehoz egy címet és egy üzenetet, amelyet megtarthat vagy módosíthat. Minden olyan érték elérhető és használható, amelyet a riasztás létrehozásakor állított be a Power BI-ban. Használatukhoz mindössze a kiemelt szürke terület fölé kell vinnie a kurzort. 

   ![E-mail küldése képernyő](media/service-flow-integration/power-bi-flow-email-default.png)

1.  Ha például a riasztás címekét beállította a **Újabb érmet nyertünk** szöveget, a **Riasztás címe** lehetőség kiválasztásával felhasználhatja ezt a szöveget az e-mail tárgyának szövegeként.

    ![e-mail létrehozása szöveg](media/service-flow-integration/power-bi-flow-message.png)

    Az e-mail törzseként elfogadhatja az alapbeállítás szerinti szöveget, de létrehozhat saját szöveget is. A fenti példában az alapértelmezett üzenetben néhány változtatás látható.

1. Ha elkészült, válassza a **Folyamat létrehozása** vagy a **Folyamat mentése** lehetőséget.  A rendszer létrehozza és ellenőrzi a folyamatot.  A Power Automate értesíteni fogja, ha hibát észlel.
2. Hibák esetén a **Folyamat szerkesztése** lehetőségre kattintva hárítsa el azokat. Ha nincsenek hibák, a **Kész** gombra kattintva futtathatja az új folyamatot.
   
   ![sikert jelző üzenet](media/service-flow-integration/power-bi-flow-running.png)
5. Ha az adatriasztás megtörténik, a rendszer a megadott e-mail-címekre üzenetet küld.  
   
   ![riasztási e-mail](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-power-automate-that-uses-power-bi---from-scratch-blank"></a>Power BI-t használó, előzmények nélküli üres Power Automate-folyamat létrehozása
Ebben a feladatban egy előzmények nélküli egyszerű folyamatot hozunk létre, amelyet egy Power BI-adatokkal kapcsolatos riasztás (értesítés) vált majd ki.

1. Jelentkezzen be a Power Automate-be.
2. Kattintson a **Saját folyamatok** > **Üres folyamat létrehozása** lehetőségre.
   
   ![A Power Automate felső menüsora](media/service-flow-integration/power-bi-my-flows.png)
3. A keresőmezőt használva keressen rá a Power BI-triggerekre, majd válassza a **Power BI – adatriasztás esetén** lehetőséget.

### <a name="build-your-flow"></a>A folyamat létrehozása
1. A legördülő listából válassza ki a riasztás nevét.  A riasztások létrehozásával kapcsolatban tekintse meg a [Power BI-beli adatriasztásokról](service-set-data-alerts.md) szóló cikket.
   
    ![a riasztás nevének kiválasztása](media/service-flow-integration/power-bi-totalstores2.png)
2. Kattintson az **Új lépés** > **Művelet hozzáadása** lehetőségre.
   
   ![új lépés felvétele](media/service-flow-integration/power-bi-new-step.png)
3. Keressen rá az **Outlook** kifejezésre, majd kattintson a **Create event** (Esemény létrehozása) lehetőséget tartalmazó találatra.
   
   ![a folyamat létrehozása](media/service-flow-integration/power-bi-create-event.png)
4. Töltse ki az eseményhez kapcsolódó mezőket. Amikor kiválaszt egy mezőt, a Power Automate megjelenít némi dinamikus tartalmat, amelyet belefoglalhat az üzenetbe.
   
   ![a folyamat létrehozásának folytatása](media/service-flow-integration/power-bi-flow-event.png)
5. Ha elkészült, kattintson a **Folyamat létrehozása** lehetőségre.  A Power Automate menti és kiértékeli a folyamatot. Ha nincsenek hibák, a **Kész** gombra kattintva tudja futtatni a folyamatot.  Az új folyamatot a rendszer felveszi a **Saját folyamatok** lapra.
   
   ![Folyamat befejezése](media/service-flow-integration/power-bi-flow-running.png)
6. Amikor egy Power BI-adatriasztás elindítja a folyamatot, az alábbihoz hasonló Outlook-eseményértesítést fog kapni.
   
    ![A Power Automate aktivál egy outlookos értesítést](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Következő lépések
* [Első lépések a Power Automate-ben](https://docs.microsoft.com/power-automate/getting-started/)
* [Adatriasztások beállítása a Power BI szolgáltatásban](service-set-data-alerts.md)
* [Adatriasztások beállítása az iPhone-on](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* [Adatriasztások beállítása a Windows 10-hez készült Power BI-mobilalkalmazásban](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

