---
title: Egyéni vizualizációk közzététele az AppSource-ban
description: Megtudhatja, hogyan teheti közzé egyéni vizualizációit az AppSource-ban, amelyeket aztán mások is felfedezhetnek és használhatnak.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/30/2018
ms.openlocfilehash: 850d4c01248a16029b3874548b61c2f9170560bb
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281505"
---
# <a name="publish-custom-visuals-to-appsource"></a>Egyéni vizualizációk közzététele az AppSource-ban

Megtudhatja, hogyan teheti közzé egyéni vizualizációit az AppSource-ban, amelyeket aztán mások is felfedezhetnek és használhatnak.

Miután létrehozta egyéni vizualizációját, közzéteheti az AppSource-ban, hogy mások felfedezhessék és használhassák. Ehhez először el kell végezni néhány előkészítő lépést. Az egyéni vizualizációk létrehozásáról az [egyéni Power BI-vizualizáció fejlesztését](custom-visual-develop-tutorial.md) ismertető cikkben talál további információkat.

   ![Office Áruház](media/office-store/AppSource_01.jpg)

## <a name="what-is-appsource"></a>Mi az az AppSource?

Az **AppSource** az a hely, ahol SaaS-alkalmazásokat és -bővítményeket találhat Microsoft-termékeihez és -szolgáltatásaihoz. Az [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) az Office 365, a Dynamics 365, a Cortana Intelligence és egyéb szolgáltatások több millió felhasználójának tesz elérhetővé olyan megoldásokat, amelyekkel minden eddiginél hatékonyabban, részletgazdagabban vagy látványosabban dolgozhatnak.

## <a name="preparing-to-submit-your-custom-visual"></a>Az egyéni vizualizáció elküldésének előkészítése

Miután végzett az egyéni vizualizáció kódolásával és tesztelésével, és becsomagolta egy pbiviz fájlba, a következőkkel is rendelkeznie kell az elküldéshez.

| Item | Kötelező | Leírás |
| --- | --- | --- |
| Pbiviz csomag, amely az összes kötelező metaadatot tartalmazza |Igen |Vizualizáció neve<br>Megjelenített név<br>GUID<br>Verzió<br>Leírás<br>Szerző neve és e-mail-címe |
| Minta .pbix jelentésfájl |Igen |Ahhoz, hogy kellően be tudja mutatni a vizualizációt, segítenie kell a felhasználókat a részletei megismerésében. Érdemes kihangsúlyozni, hogy milyen értéket nyújt a vizualizáció a felhasználó számára, és érdemes felhozni a használatra, formázási lehetőségekre stb. vonatkozó példákat. Egy *„tippek”* oldalt is hozzáadhat a végén, amely tippeket, trükköket, elkerülendő lépéseket és hasonló információkat tartalmaz.<br>A minta .pbix jelentésfájlnak offline állapotban kell működnie, bármilyen külső kapcsolat nélkül |
| Ikon |Igen |Meg kell adnia az egyéni vizualizáció áruházban megjelenő emblémáját. Ennek formátuma .png, .jpg, .jpeg vagy .gif lehet, Pontosan 300 képpont (szélesség) × 300 képpont (magasság) méretűnek kell lennie. **Fontos!** Az ikon beküldése előtt gondosan tekintse át a [rövid útmutatót](https://docs.microsoft.com/office/dev/store/craft-effective-appsource-store-images). |
| Képernyőképek |Igen |Meg kell adnia legalább egy képernyőképet. Ennek formátuma .png, .jpg, .jpeg vagy .gif lehet, Pontosan 1366 képpont (szélesség) × 768 képpont (magasság) méretűnek kell lennie. A fájl mérete nem lehet nagyobb 1024 kB-nál. *A hatékonyabb használat érdekében adjon hozzá szövegbuborékokat az egyes képernyőképeken látható fő jellemzők által képviselt érték kihangsúlyozásához.* |
| Támogatás letöltési hivatkozása |Igen |Adjon meg egy URL-címet, amelyet felkereshetnek a felhasználók, akiknek gondjuk van a vizualizációval. Ez a hivatkozás a SellerDashboard-lista részeként lett megadva, és látható a vizualizációját az AppSource-on lévő listában elérő felhasználók számára. Az URL formátumának tartalmaznia kell a https:// vagy a http:// előtagot. |
| Adatvédelmi dokumentum hivatkozása |Igen |Adja meg a vizualizációt használó ügyfelekre vonatkozó adatvédelmi szabályzat hivatkozását. Ez a hivatkozás a SellerDashboard-lista részeként lett megadva, és látható a vizualizációját az AppSource-on lévő listában elérő felhasználók számára. A hivatkozás formátumának tartalmaznia kell a https:// vagy a http:// előtagot. |
| Végfelhasználói licencszerződés (EULA) |Igen |Fel kell töltenie egy EULA fájlt. Ez lehet saját EULA is, de az Office Áruház Power BI-vizualizációkra vonatkozó alapértelmezett EULA fájlját is használhatja. Az alapértelmezett EULA használatához illessze be a következő URL-címet az eladó irányítópultjának „Végfelhasználói licencszerződés” fájlfeltöltési párbeszédpaneljére: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf). |
| Videó hivatkozása |Nem |Ahhoz, hogy felkelthesse a felhasználók érdeklődését az egyéni vizualizáció iránt, ajánlott megadni egy, a vizualizációval foglalkozó videó hivatkozását. Az URL formátumának tartalmaznia kell a https:// vagy a http:// előtagot. |
| GitHub-adattár |Nem |Ajánlott megadni egy érvényes és nyilvános hivatkozást a vizualizáció forrásait és a mintaadatokat tartalmazó [GitHub](https://www.github.com)-adattárra, hogy más fejlesztők visszajelzést adhassanak, hozzájárulhassanak a kód fejlesztéséhez. |

## <a name="submitting-to-power-bi"></a>Elküldés a Power BI-nak

Az elküldés során először egy e-mailt küld az egyéni Power BI-vizualizációk elküldéséért felelős csapatának. Az e-mailt a következő címre küldheti el: [pbivizsubmit@microsoft.com](mailto:pbivizsubmit@microsoft.com).

> [!IMPORTANT]
> A .pbiviz-csomag létrehozása előtt ki kell töltenie a következő mezőket a pbiviz.json fájlban: „description”, „supportUrl”, „author”, „name” és „email”.

Mellékelje a **.pbiviz fájlt** és a **mintajelentés .pbix fájlját** az e-mailhez. A Power BI-csapattól egy választ fog kapni, amely tartalmazza a feltöltésre vonatkozó utasításokat és a feltöltendő alkalmazáscsomag XML-fájlját. Erre az XML-alkalmazáscsomagra szükség van ahhoz, hogy be tudja küldeni a vizualizációt az Office fejlesztői központján keresztül.

> [!NOTE]
> A minőség javítása és annak biztosítása érdekében, hogy a meglévő jelentések ne sérüljenek, az áruházban való jóváhagyás után további 2 hétbe telik, amíg a meglévő vizualizációk frissítései életbe lépnek az éles környezetben.

## <a name="submitting-to-appsource"></a>Beküldés az AppSource-ba

Miután megkapta az alkalmazáscsomag XML-fájlját a Power BI-csapattól, lépjen a [fejlesztői központba](https://sellerdashboard.microsoft.com/Application/Summary), hogy beküldhesse a vizualizációt az AppSource-ba.

> [!NOTE]
> Érvényes Office fejlesztői fiókkal kell rendelkeznie, hogy bejelentkezhessen az [Office fejlesztői központjába](https://dev.office.com/). Az Office fejlesztői fiókoknak (Live ID azonosítóval rendelkező) Microsoft-fiókoknak kell lenniük (például hotmail.com vagy outlook.com).

> [!IMPORTANT]
> El kell küldenie egy e-mailt a .pbiviz- és a .pbix-fájllal a Power BI csapatának, mielőtt beküldené a vizualizációt az AppSource-ba. A Power BI csapata így feltöltheti a fájlokat a nyilvános megosztási kiszolgálóra. Ha ezt nem teszi meg, az AppSource nem tudja lekérni a fájlokat. Minden új vizualizáció beküldésekor, a meglévő vizualizációk frissítésekor és az elutasított beküldések javításakor is el kell küldenie a fájlokat.

### <a name="process-to-submit-visual"></a>A vizualizáció beküldése

A beküldéshez kövesse az alábbi lépéseket.

1. Válassza az **Új alkalmazás hozzáadása** lehetőséget.

    ![Alkalmazás felvétele](media/office-store/powerbi-custom-visual-add-an-app.png)

2. Válassza a **Power BI egyéni vizualizáció**, majd a **Tovább** lehetőséget.

3. Válassza az **Alkalmazáscsomag** területen lévő **+** lehetőséget, és válassza ki a Power BI-csapattól kapott alkalmazáscsomag XML-fájlját a fájlmegnyitási párbeszédpanelen.

    ![Alkalmazáscsomag](media/office-store/powerbi-custom-visual-apppackage.png)

4. A rendszer megerősítést küld, ha a Power BI-alkalmazáscsomagot érvényesnek találja.

    ![Jegyzék jóváhagyva](media/office-store/powerbi-custom-visual-manifest-approved.png)

5. Töltse ki az **Általános információk** adatait.

   * *Beküldés címe:* A beküldés neve a fejlesztői központban
   * *Verzió:* A verziószámot a rendszer automatikusan kitölti a bővítmény alkalmazáscsomagja alapján.
   * *Kiadás dátuma (UTC):* Válassza ki, hogy mikor szeretné közzétenni az alkalmazást az áruházban. Ha egy jövőbeli dátumot választ, az alkalmazás az előtt nem lesz elérhető.
   * *Kategória:* Az első kategória automatikusan „Adatmegjelenítés + BI” lesz. Minden egyéni Power BI-vizualizáció ezzel a címkével rendelkezik. Legfeljebb 2 további kategóriát adhat meg, hogy a felhasználók könnyen kikereshessék a vizualizációt
   * *Tesztelést segítő jegyzetek és megjegyzések:* Megadhatja, ha utasításokkal szeretné ellátni a Microsoft tesztelőit.
   * *Alkalmazásom kriptográfiát vagy titkosítást használ, tartalmaz, támogat vagy hív meg:* Ne jelölje be.
   * *A bővítmény elérhetővé tétele az Office bővítmények katalógusában az iPaden:* Ne jelölje be.
6. Töltse fel a vizualizáció emblémáját az **Alkalmazásembléma** területen lévő **+** kiválasztásával. Ezután válassza ki az ikon fájlját a fájlmegnyitási párbeszédpanelen. A fájlnak .png, .jpg, .jpeg vagy .gif formátummal kell rendelkeznie. Pontosan 300 képpont (szélesség) × 300 képpont (magasság) méretűnek kell lennie, és nem lehet nagyobb 512 kB-nál.

    ![Alkalmazás emblémája](media/office-store/powerbi-custom-visual-app-logo.png)

7. Töltse ki a **Támogatási dokumentumok** adatait.

   * Támogatási dokumentum hivatkozása
   * Adatvédelmi dokumentum hivatkozása
   * Videó hivatkozása
   * Végfelhasználói licencszerződés (EULA)

       Fel kell töltenie egy EULA fájlt. Ez lehet saját EULA is, de az Office Áruház Power BI-vizualizációkra vonatkozó alapértelmezett EULA fájlját is használhatja. Az alapértelmezett EULA használatához illessze be a következő URL-címet az eladó irányítópultjának „Végfelhasználói licencszerződés” fájlfeltöltési párbeszédpaneljére: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

8. Válassza a **Tovább** lehetőséget, hogy a **Részletek** lapra lépjen.

9. Válassza a **Nyelv** lehetőséget, és válasszon egy nyelvet a listából.

    ![Nyelv](media/office-store/powerbi-custom-visual-language.png)

10. Töltse ki a „Leírás” részleteit.

    * *Alkalmazás neve (ehhez a nyelvhez):* Írja be az alkalmazás címét, ahogyan az áruház oldalán kell megjelennie.
    * *Rövid leírás:* Adja meg az alkalmazás rövid leírását legfeljebb 100 karakterben, ahogyan az áruház oldalán meg fog jelenni. Ez a leírás az emblémával együtt jelenik meg a felső szintű oldalakon. A pbiviz csomagban szereplő leírást is használhatja.
    * *Hosszú leírás:* Adja meg az alkalmazás részletesebb leírását, amelyet az ügyfelek az alkalmazást részletező oldalon látnak. Ha azt szeretné, hogy a közösség hozzájárulhasson a vizualizáció továbbfejlesztéséhez, és ezért nyílt forráskódúvá szeretné tenni, itt adja meg a nyilvános adattár, például a GitHub hivatkozását.

11. Töltsön fel legalább egy képernyőképet. Ennek formátuma .png, .jpg, .jpeg vagy .gif lehet, Pontosan 1366 képpont (szélesség) × 768 képpont (magasság) méretűnek kell lennie. A fájl mérete nem lehet nagyobb 1024 kB-nál. *A hatékonyabb használat érdekében adjon hozzá szövegbuborékokat az egyes képernyőképeken látható fő jellemzők által képviselt érték kihangsúlyozásához.*

12. Ha több nyelvet szeretne hozzáadni, válassza a **Nyelv hozzáadása** lehetőséget, és ismételje meg a 10. és a 11. lépéseket. Ha több nyelvet ad meg, a felhasználók a saját nyelvükön tekinthetik meg az egyéni vizualizáció részleteit. A listában nem szereplő nyelvek esetében a vizualizáció információi alapértelmezés szerint az első kiválasztott nyelven jelennek meg.

13. Amikor végzett a nyelvek hozzáadásával, válassza a **Tovább** lehetőséget, hogy a **Hozzáférés letiltása** oldalra lépjen.

14. Ha nem szeretné, hogy bizonyos országokban vagy régiókban tartózkodó vásárlók használhassák vagy megvásárolhassák az alkalmazást, jelölje be a jelölőnégyzetet, és válasszon a listából.

15. Az **Árak** lapra való továbblépéshez válassza a **Tovább** lehetőséget.

16. Jelenleg csak az *ingyenes* vizualizációk támogatottak, és a vizualizáción belüli további vásárlások (alkalmazáson belüli vásárlások) nem engedélyezettek. Jelölje be az **Ez az alkalmazás ingyenes** jelölőnégyzetet.

    > [!NOTE]
    > Ha nem az ingyenes lehetőséget választja, vagy ha alkalmazáson belül megvásárolható tartalom van a beküldött vizualizációban, a rendszer elutasítja a beküldést.

17. Bejelölheti a **Mentés vázlatként** lehetőséget és elküldheti a vizualizációt később, vagy bejelölheti a **Küldés jóváhagyásra** jelölőnégyzetet, hogy elküldje az egyéni vizualizációt az Office Áruházba.

## <a name="tracking-submission-status-and-usage"></a>A beküldési állapot és a használat nyomon követése

Áttekintheti az [érvényesítési szabályzatokat](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

A beküldés után az [alkalmazás irányítópultján](https://sellerdashboard.microsoft.com/Application/Summary/) tekintheti meg a beküldés állapotát.

## <a name="certify-your-visual"></a>A vizualizáció tanúsítása

A vizualizáció létrehozása azt is megteheti, hogy tanúsíttatja a vizualizációt. Ez azt jelenti, hogy futtathatja azt a Power BI szolgáltatáson belül, és a szolgáltatás más funkcióival együtt is használhatja, például exportálhatja a PowerPointba. További információért lásd az [egyéni látványelem *tanúsíttatásával*](../power-bi-custom-visuals-certified.md) foglalkozó témakört.

## <a name="next-steps"></a>Következő lépések

[Egyéni Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md)  
[Vizualizációk a Power BI-ban](../visuals/power-bi-report-visualizations.md)  
[Egyéni vizualizáció a Power BI-ban](../power-bi-custom-visuals.md)  
[Egyéni vizualizáció *tanúsíttatása*](../power-bi-custom-visuals-certified.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
