---
title: 'Kiskereskedelmi elemzési minta a Power BI-hoz: bemutató'
description: 'Kiskereskedelmi elemzési minta a Power BI-hoz: bemutató'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: c07c33cb6ae859c9cf202ae67119dbfb8dd45e26
ms.sourcegitcommit: 1e4fee6d1f4b7803ea285eb879c8d5a4f7ea8b85
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51717677"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Kiskereskedelmi elemzési minta a Power BI-hoz: bemutató

Ez az iparági minta-irányítópult és a mögöttes jelentés a több üzletben és körzetben értékesített cikkek kiskereskedelmi értékesítési adatait elemzi. A mérőszámok a folyó év teljesítményét vetik össze a tavalyival a következő területeken: értékesítés, egységek, bruttó nyereség, eltérés, új üzletek elemzett adatai. Az adatok az obviEnce-től ([www.obvience.com](http://www.obvience.com)) származó valós, de anonimizált adatok.

![](media/sample-retail-analysis/retail1.png)

## <a name="prerequisites"></a>Előfeltételek

 Használat előtt a mintát [tartalomcsomagként](https://docs.microsoft.com/power-bi/sample-datasets#get-and-open-a-sample-content-pack-in-power-bi-service), [.pbix-fájlként](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) vagy [Excel-munkafüzetként](http://go.microsoft.com/fwlink/?LinkId=529778) le kell töltenie.


### <a name="get-the-content-pack-for-this-sample"></a>Tartalomcsomag letöltése ehhez a mintához

1. Nyissa meg a Power BI szolgáltatást (app.powerbi.com), és jelentkezzen be.
2. A bal alsó sarokban válassza az **Adatok lekérése** lehetőséget.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Ekkor megjelenik az Adatok lekérése lap. Itt kattintson a **Minták** ikonra.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Válassza a **Kiskereskedelmi elemzési minta** elemet, majd a **Kapcsolódás** lehetőséget.  
  
   ![Kiskereskedelmi elemzési minta](media/sample-retail-analysis/retail16.png)
   
5. A Power BI importálja a tartalomcsomagot, és egy új irányítópultot, jelentést és adatkészletet ad hozzá az aktuális munkaterülethez. Az új tartalmakat sárga csillag jelöli. 
   
   ![Kiskereskedelmi elemzési minta](media/sample-retail-analysis/retail17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>.pbix-fájl letöltése ehhez a mintához

Lehetőség van a mintát .pbix-fájlként is letölteni, amelyet a Power BI Desktoppal való használatra terveztek. 

 * [Kiskereskedelmi elemzési minta](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Excel-munkafüzet letöltése ehhez a mintához
Letöltheti [kizárólag a minta adatkészletét (Excel-munkafüzetét) is](http://go.microsoft.com/fwlink/?LinkId=529778). A munkafüzet megtekinthető és módosítható Power View-lapokat tartalmaz. A nyers adatokat a **Power Pivot > Kezelés** lehetőségre kattintva nézheti meg.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Az irányítópult elindítása és a jelentés megnyitása
1. Az irányítópulton kattintson az „Összes üzlet” csempére:

   ![](media/sample-retail-analysis/retail-analysis-7.png)  

   Ekkor megnyílik a jelentés „Üzleti értékesítések áttekintése” oldala. Amint látható, összesen 104 üzlet van, amiből 10 új. Két üzletlánc működik, a Fashions Direct és a Lindseys. A Fashions Direct üzleteinek nagyobb az átlagos mérete.
2. A kördiagramon kattintson a **Fashions Direct** elemre.

   ![](media/sample-retail-analysis/retail3.png)  

   Tekintse meg az eredményt a buborékdiagramon:

   ![](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   Az egy négyzetlábra eső átlagos értékesítési arány az FD-01-es körzetben a legnagyobb, az értékesítések eltérése a tavalyihoz képest az FD-02-es körzetben a legalacsonyabb, az FD-03-as és az FD-04-es körzetek teljesítménye általában a legrosszabb.
3. Kattintson az egyes buborékokra vagy diagramokra annak megtekintéséhez, hogy ennek hatására milyen keresztkijelölések jönnek létre.
4. Az irányítópulthoz úgy térhet vissza, hogy a felső navigációs sávon (webhely-navigációs eszközön) az irányítópult nevére kattint.

   ![](media/sample-retail-analysis/power-bi-breadcrumbs.png)
5. Az irányítópulton kattintson a „Folyó évi értékesítések” csempére.

   ![](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Ez egyenértékű azzal, mintha a kérdés mezőbe beírná a „This year sales” (Folyó évi értékesítések) szöveget.

   Ekkor az alábbi képernyő jelenik meg:

   ![](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>A Power BI Q&A funkcióban létrehozott csempe áttekintése
Tárja fel a részleteket.

1. Egészítse ki a kérdést a „this year sales **by district**” (folyó évi értékesítés körzetek szerint) szövegre. Tekintse meg az eredményt: A rendszer automatikusan sávdiagramba rendezte a választ, és más kifejezéseket is felkínál:

   ![](media/sample-retail-analysis/retail8.png)
2. Most egészítse ki a kérdést a „this year sales **by zip and chain**” (folyó évi értékesítés irányítószám és üzletlánc szerint) szövegre.

   Figyelje meg, hogy a rendszer miképpen válaszol a megfelelő diagramokkal az éppen beírt kérdésre.
3. Játsszon egy kicsit: tegyen fel többféle kérdést, és tekintse meg a válaszul kapott eredményeket.
4. Amikor elkészült, térjen vissza az irányítópulthoz.

## <a name="dive-deeper-into-the-data"></a>Mélyebb adatelemzés
Most tárjon fel egy részletesebb szintet, ahol megvizsgálhatja az egyes körzetek teljesítményét.

1. Az irányítópulton kattintson a folyó és a tavalyi év értékesítési adatait összevető csempére.

   ![](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   Figyelje meg, milyen nagymértékben ingadozott az Eltérés % értéke a tavalyi évhez képest, és hogy a január, az április és a július hónapok különösen rosszul teljesítettek.

   ![](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Próbálja meg szűkítéssel kideríteni a probléma okát.
2. Kattintson a buborékdiagramra, majd jelölje ki a **020-Mens** (Férfiak) elemet.

   ![](media/sample-retail-analysis/retail11.png)  

   Figyelje meg, hogy a Férfiak kategóriát áprilisban nem érintette olyan rosszul a változás, mint a vállalkozás egészét, de a január és a július itt is problémát jelent.
3. Most kattintson a **010-Womens’ buborékra** (Nők).

   ![](media/sample-retail-analysis/retail12.png)

   Figyelje meg, hogy a Nők kategória minden hónapban rosszabbul teljesített, mint a vállalkozás egésze, és szinte minden hónapban sokkal rosszabbul teljesített a tavalyinál.
4. Kattintson ismét a buborékra a szűrő törléséhez.

## <a name="try-out-the-slicer"></a>A szeletelő kipróbálása
Tekintse meg az egyes körzetek eredményeit.

1. Válassza ki Allan Guinot nevét a bal oldalon, felül található szeletelőben.

   ![](media/sample-retail-analysis/retail13.png)

   Figyelje meg, hogy Allan körzete márciusban és júniusban jobban teljesített, mint tavaly.
2. Hagyja kijelölve Allant, és kattintson a Nők buborékra.

   ![](media/sample-retail-analysis/power-bi-allan.png)

   Figyelje meg, hogy a Nők kategóriában Allan körzete egyszer sem érte el a tavalyi eredményt.
3. Vizsgálja meg a többi körzeti vezetőt és a kategóriákat – Milyen egyéb következtetések vonhatók le?
4. Amikor elkészült, térjen vissza az irányítópulthoz.

## <a name="what-is-our-data-telling-us-about-sales-growth-this-year"></a>Mit árulnak el az adatok az értékesítés folyó évi alakulásáról?
Végezetül vessen egy pillantást a vállalkozás növekedésére – az idén új üzletek nyíltak.

1. Kattintson az „Folyóévben megnyílt üzletek” csempére.

   ![](media/sample-retail-analysis/retail15.png)

   A csempe világosan mutatja, hogy idén több Fashions Direct üzlet nyílt, mint Lindseys.
2. Vizsgálja meg az „Egy négyzetlábra eső értékesítés üzletnév szerint” diagramot:

   ![](media/sample-retail-analysis/retail14.png)

    Az új üzletek egy négyzetlábra eső átlagos értékesítési adataiban jelentős eltérések mutatkoznak.
3. Kattintson a Fashions Direct feliratra a jobb felső diagramon. Figyelje meg, hogy még ugyanazon a láncon belül is jelentősen meghaladja a legjobban teljesítő üzlet (a Winchester Fashions Direct) 21,22 dolláros eredménye a leggyengébb üzlet (Cincinnati 2 Fashions Direct) 12,86 dolláros eredményét.

   ![](media/sample-retail-analysis/power-bi-lindseys.png)
4. Kattintson a szeletelőben a Winchester Fashions Direct elemre, és vizsgálja meg a vonaldiagramot. Az első értékesítési eredményeket februárban jelentették.
5. Kattintson a szeletelőben a Cincinnati 2 Fashions Direct elemre: a megjelenő vonaldiagramból kiderül, hogy az üzlet júniusban nyílt meg, és valószínűleg ez a legrosszabbul teljesítő üzlet.
6. Ahogy korábban, most is kattinthat a diagramokon lévő egyéb sávokra, vonalakra és buborékokra a további összefüggések elemzéséhez.

Ebben a környezetben bármit nyugodtan kipróbálhat. Mindig hozhat olyan döntést, hogy nem menti a módosításokat. De ha mégis mentené őket, bármikor lekérheti a minta új másolatát az Adatok lekérése lehetőséggel.

## <a name="connect-to-your-data"></a>Csatlakozás az adatokhoz
Reméljük, hogy ez a bemutató segített megérteni a Power BI irányítópultok, Q&A és jelentések segítségével történő kiskereskedelmi adatelemzést. Most Önön a sor – csatlakozzon a saját adataihoz. A Power BI használatával számos különböző adatforráshoz kapcsolódhat. További információkért lásd: [Első lépések a Power BI használatával](service-get-started.md).

## <a name="next-steps"></a>További lépések
* [A Kiskereskedelmi elemzési minta tartalomcsomag letöltése](sample-tutorial-connect-to-the-samples.md)
* [Az összes mintafájl letöltése zip-fájlban](http://go.microsoft.com/fwlink/?LinkId=535020)    
* [A fenti Power BI-mintához tartozó Excel-munkafüzet letöltése](http://go.microsoft.com/fwlink/?LinkId=529778)    
* [Adatbeolvasás (a Power BI-ban)](service-get-data.md)    
* [Power BI – Alapfogalmak](consumer/end-user-basic-concepts.md)    
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
