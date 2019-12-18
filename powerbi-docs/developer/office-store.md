---
title: Power BI-vizualizációk közzététele a Partnerközpontban
description: Ismerje meg, hogy miképpen teheti közzé a Partnerközpontban a saját egyéni vizualizációit, amelyeket ezután mások is megismerhetnek és használhatnak
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: ec1bd8666a9d76b4ccfa7793415488f85a24dfdb
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999902"
---
# <a name="publish-power-bi-visuals-to-partner-center"></a>Power BI-vizualizációk közzététele a Partnerközpontban

Miután létrehozta a saját Power BI-vizualizációját, közzéteheti az AppSource-ban, hogy mások is megismerhessék és használhassák. A Power BI-vizualizációk létrehozásával kapcsolatos további információkhoz lásd a [Power BI vizualizáció fejlesztése](visuals/custom-visual-develop-tutorial.md) című cikket.

## <a name="what-is-appsource"></a>Mi az az AppSource?

Az [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) az a hely, ahol SaaS-alkalmazásokat és -bővítményeket találhat Microsoft-termékeihez és -szolgáltatásaihoz.

![Office Áruház](media/office-store/appsource-01.png)

## <a name="preparing-to-submit-your-power-bi-visual"></a>A Power BI-vizualizáció beküldésének előkészítése

Mielőtt beküldené a Power BI-vizualizációt az AppSource-ba, olvassa el a [Power BI-vizualizációk útmutatóját](guidelines-powerbi-visuals.md), és [tesztelje az egyéni vizualizációt](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/SubmissionTesting.md).

Ha készen áll a Power BI-vizualizáció beküldésére, ellenőrizze, hogy a vizualizáció megfelel-e az alábbi követelményeknek.

| Item | Kötelező | Leírás |
| --- | --- | --- |
| Pbiviz-csomag |Igen |Csomagolja a Power BI-vizualizációt egy Pbiviz-csomagba, amely az összes szükséges metaadatot tartalmazza.<br>Vizualizáció neve<br>Megjelenített név<br>GUID<br>Verzió<br>Leírás<br>Szerző neve és e-mail-címe |
| Minta .pbix jelentésfájl |Igen |A vizualizáció megfelelő bemutatásához érdemes megismertetnie a felhasználókkal a részleteket. Hangsúlyozza ki a vizualizáció felhasználó számára nyújtott értékeit, illusztrálja példákkal a használatot és a formázási lehetőségeket. Végül hozzáadhat egy tippeket, trükköket és elkerülendő lépéseket tartalmazó *„tippek”* oldalt is.<br>A minta .pbix jelentésfájlnak működnie kell offline állapotban, bármilyen külső kapcsolat nélkül. |
| Ikon |Igen |Meg kell adnia az egyéni vizualizáció áruházban megjelenő emblémáját. Ennek formátuma .png, .jpg, .jpeg vagy .gif lehet, Pontosan 300 képpont (szélesség) × 300 képpont (magasság) méretűnek kell lennie.<BR>**Fontos!** Az ikon beküldése előtt tekintse át figyelmesen az [AppSource képtárolási útmutatóját](https://docs.microsoft.com/office/dev/store/craft-effective-appsource-store-images). |
| Képernyőképek |Igen |Adjon meg legalább egy képernyőképet. Ennek formátuma .png, .jpg, .jpeg vagy .gif lehet, A mérete csak 1366 px (szélesség) és 768 px (hosszúság) lehet. A fájl nem lehet nagyobb 1024 kb-nál.<br>A hatékonyabb használat érdekében adjon hozzá szövegbuborékokat az egyes képernyőképeken látható fő jellemzők által képviselt érték kihangsúlyozásához. |
| Támogatás letöltési hivatkozása |Igen |Adjon meg egy támogatási URL-címet az ügyfeleknek. Ez a hivatkozás a SellerDashboard-lista részeként lesz megadva, és látható lesz a vizualizációt az AppSource-beli listában elérő felhasználók számára. Az URL-címnek tartalmaznia kell a https:// vagy a http:// előtagot. |
| Adatvédelmi dokumentum hivatkozása |Igen |Adjon meg egy hivatkozást a vizualizáció adatvédelmi szabályzatához. Ez a hivatkozás a SellerDashboard-lista részeként lesz megadva, és látható lesz a vizualizációt az AppSource-beli listában elérő felhasználók számára. A hivatkozásnak tartalmaznia kell a https:// vagy a http:// előtagot. |
| Végfelhasználói licencszerződés (EULA) |Igen |Fel kell töltenie egy EULA fájlt. Ez lehet saját EULA is, de az Office Áruház Power BI-vizualizációkra vonatkozó alapértelmezett EULA fájlját is használhatja. Az alapértelmezett EULA használatához illessze be a következő URL-címet az eladó irányítópultjának „Végfelhasználói licencszerződés” fájlfeltöltési párbeszédpaneljére. [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf). |
| Videó hivatkozása |Nem |Tovább növelheti a felhasználók érdeklődését az egyéni vizualizáció iránt, ha videóhivatkozást ad meg a vizualizáció témájában. Az URL-címnek tartalmaznia kell a https:// vagy a http:// előtagot. |
| GitHub-adattár |Nem |Osszon meg nyilvános hivatkozást egy [GitHub](https://www.github.com)-adattárban a Power BI-vizualizáció és az adatminták forrásaival. Ez lehetővé teszi más fejlesztők számára a visszajelzést és a javaslattételt a kód javítására. |

## <a name="getting-an-app-package-xml"></a>Az alkalmazáscsomag XML-fájljának beszerzése

A Power BI-vizualizáció beküldéséhez be kell szereznie az alkalmazáscsomag XML-fájlját a Power BI csapatától. Az alkalmazáscsomag XML-fájljának beszerzéséhez küldjön e-mailt a Power BI-vizualizációk beküldését intéző csapatnak ([pbivizsubmit@microsoft.com](mailto:pbivizsubmit@microsoft.com)).

A **pbiviz** csomag létrehozása előtt ki kell töltenie a következő mezőket a **pbiviz.json** fájlban:
* leírás
* supportUrl
* szerző
* név
* e-mail

Mellékelje a **pbiviz fájlt** és a **mintajelentés pbix fájlját** az e-mailhez. A Power BI-csapattól egy választ fog kapni, amely tartalmazza a feltöltésre vonatkozó utasításokat és a feltöltendő alkalmazáscsomag XML-fájlját. Erre az XML-alkalmazáscsomagra szükség van ahhoz, hogy be tudja küldeni a vizualizációt az Office fejlesztői központján keresztül.

> [!NOTE]
> A minőség javítása és annak biztosítása érdekében, hogy a meglévő jelentések ne sérüljenek, az áruházban való jóváhagyás után további 2 hétbe telik, amíg a meglévő vizualizációk frissítései életbe lépnek az éles környezetben.

## <a name="submitting-to-appsource"></a>Beküldés az AppSource-ba

A Power BI-vizualizáció AppSource-ba küldéséhez be kell szereznie egy alkalmazáscsomagot a Power BI csapatától, majd be kell küldenie a Partnerközpontba. 

### <a name="getting-the-app-package"></a>Az alkalmazáscsomag beszerzése

Mielőtt beküldené a vizualizációt az AppSource-ba, el kell küldenie egy e-mailt a **pbiviz-** és a **pbix-** fájllal a Power BI csapatának. A Power BI csapata így feltöltheti a fájlokat a nyilvános megosztási kiszolgálóra. Ha ezt nem teszi meg, az AppSource nem tudja lekérni a fájlokat. 

A Power BI csapatának ellenőriznie kell az új Power BI-vizualizációk beküldésére vonatkozó fájlokat, a meglévő Power BI-vizualizációk frissítéseit, és a visszautasított beküldések javításait.

### <a name="submitting-to-partner-center"></a>Beküldés a Partnerközpontba

Ahhoz, hogy a Power BI-vizualizációt beküldhesse a Partnerközpontba, regisztrálnia kell a Partnerközpontban. Ha még nem regisztrált, [nyisson meg egy fejlesztői számlát a Partnerközpontban](https://docs.microsoft.com/office/dev/store/open-a-developer-account).

Kövesse az alábbi lépéseket a Power BI-vizualizáció Partnerközpontba való beküldéséhez. A beküldési folyamattal kapcsolatos további információkért lásd: [Fejlesztői számla nyitása a Partnerközpontban](https://docs.microsoft.com/office/dev/store/use-partner-center-to-submit-to-appsource).

>[!NOTE]
> Ha már megkezdte egy Power BI-vizualizáció beküldését, és a [Seller Dashboardot](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (a régi kezelőeszközt) kell használnia, akkor tekintse át a [Power BI-vizualizáció beküldése az AppSource-ba a Seller Dashboard használatával](seller-dashboard.md) című útmutatót.

1. Jelentkezzen be a **Partnerközpontba**.

2. A baloldali ablaktáblán válassza az **OFFICE ÁRUHÁZ** lehetőséget.

3. Válassza az **Áttekintés** lehetőséget.

4. Válassza az **Új létrehozása** elemet, majd a legördülő menüből válassza a **Power BI-vizualizáció** lehetőséget.

    ![Office Áruház](media/office-store/power-bi-visual.png)

5. Az **Új Power BI-vizualizáció létrehozása** ablakban adjon nevet a Power BI-vizualizációnak, és válassza a **Létrehozás** lehetőséget.

6. Kattintson a **Csomagok** elemre, és töltse fel a Power BI-vizualizáció alkalmazáscsomag XML-fájlját.

7. Kattintson a **Tulajdonságok** elemre, és adja meg a kért információkat.

8. Ha a termékhez további vásárlásra van szükség, válassza a **Termék beállítása** lehetőséget, és jelölje be a **Társított szolgáltatás vásárlása** jelölőnégyzetet.

9. (Választható) Ha [tanúsítványt](power-bi-custom-visuals-certified.md) kíván beszerezni a vizualizációhoz, válassza a **Termék beállítása** lehetőséget, és jelölje be a **Power BI-tanúsítvány** jelölőnégyzetet.
    >[!TIP]
    >A Power BI hitelesítési folyamata időt vehet igénybe. Új Power BI-vizualizáció létrehozása esetén a Power BI-tanúsítvány igénylése előtt javasoljuk a Power BI-vizualizáció Partnerközponton keresztüli közzétételét. Így gondoskodhat a vizualizáció késedelem nélküli közzétételéről.

10. Válassza a **Termék beállítása** lehetőséget, és kattintson az **Áttekintés és közzététel** lehetőségre.

## <a name="tracking-submission-status-and-usage"></a>A beküldési állapot és a használat nyomon követése

Áttekintheti az [érvényesítési szabályzatokat](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

A beküldés után az [alkalmazás irányítópultján](https://sellerdashboard.microsoft.com/Application/Summary/) tekintheti meg a beküldés állapotát.

## <a name="certify-your-visual"></a>A vizualizáció tanúsítása

Létrehozás után igény szerint [tanúsítványt](../developer/power-bi-custom-visuals-certified.md) szerezhet be a vizualizációhoz.

## <a name="next-steps"></a>Következő lépések

[Egyéni Power BI-vizualizáció fejlesztése](visuals/custom-visual-develop-tutorial.md)  
[Vizualizációk a Power BI-ban](../visuals/power-bi-report-visualizations.md)  
[Egyéni vizualizációk a Power BI-ban](../developer/power-bi-custom-visuals.md)  
[Tanúsítvány beszerzése Power BI-vizualizációhoz](../developer/power-bi-custom-visuals-certified.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
