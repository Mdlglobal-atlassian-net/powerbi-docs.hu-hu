---
title: ESRI ArcGIS-térképek létrehozása a Power BI-ban
description: 'ESRI ArcGIS-térképek létrehozása a Power BI-ban '
author: mihart
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: EKVvOZmxg9s
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 85bf9630a8c272b513f27f38b24a5d8a77075444
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37599620"
---
# <a name="arcgis-maps-in-power-bi-service-and-power-bi-desktop-by-esri"></a>Esri ArcGIS-térképek a Power BI szolgáltatásban és a Power BI Desktopban
Ez az oktatóanyag az ArcGIS-térképet létrehozó személy szemszögéből van megírva. Ha a készítő megosztja az ArcGIS-térképet egy kollégájával, az illető megtekintheti és használhatja a térképet, azonban nem mentheti a módosításokat. További információ az ArcGIS-térképek megtekintéséről: [Az ArcGIS-térképek használata](power-bi-visualizations-arcgis.md).

Az ArcGIS-térképek és a Power BI együttes használata új lehetőségeket kínál a térképkezelésben, amelyek messze túlmutatnak a pontok térképeken való elhelyezésén. Az alaptérképekhez, helytípusokhoz, témákhoz, szimbólumstílusokhoz és referenciarétegekhez elérhető beállításokkal lenyűgöző és informatív térképes vizualizációk hozhatók létre. A térképen megjelenített mérvadó adatrétegek és a térbeli elemzés egyesítésével jobban megértheti a vizualizációban szereplő adatokat.

 Az ArcGIS-térképek mobileszközökön nem hozhatók létre, de megtekinthetők és használhatók. Lásd: [ArcGIS-térképek használata a Power BI-ban](power-bi-visualizations-arcgis.md).

> [!TIP]
> A GIS az angol Geographic Information Science (térinformatika) kifejezés rövidítése.


Az alábbi példa sötétszürke vásznon ábrázolja hőtérképként a regionális értékesítéseket a rendelkezésre álló jövedelem 2016-os középértékét jelölő demográfiai rétegen. Amint azt a továbbiakban is látni fogja, az ArcGIS-térképek szinte korlátlan térképes megjelenítési lehetőségekkel, demográfiai adatmegjelenítésekkel és igen figyelemreméltó térképi vizualizációkkal rendelkeznek, amelyekkel a lehető legszemléletesebb módon mutathatja be az adatait.

![](media/power-bi-visualization-arcgis/power-bi-intro-arcgis.png)

> [!TIP]
> Példákat és beszámolókat az [ESRI Power BI-oldalán](https://www.esri.com/powerbi) talál. Ezután tekintse meg az esri [ArcGIS Maps for Power BI termékének Első lépések oldalát](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) is.

## <a name="user-consent"></a>Felhasználói beleegyezés
Az ArcGIS Maps for Power BI szolgáltatója az Esri (www.esri.com). Az ArcGIS Maps for Power BI használatára az Esri szerződési feltételei és adatvédelmi szabályzata vonatkoznak. Ha a Power BI-felhasználó használni kívánja az ArcGIS Maps for Power BI vizualizációit, el kell fogadnia a feltételeket.

**Forrásanyagok**

[Feltételek](https://go.microsoft.com/fwlink/?LinkID=826322)

[Adatvédelmi irányelvek](https://go.microsoft.com/fwlink/?LinkID=826323)

[Az ArcGIS Maps for Power BI termékoldala](https://www.esri.com/powerbi)

<br/>

## <a name="enable-arcgis-map"></a>ArcGIS-térkép engedélyezése
Az ArcGIS-térképek jelenleg a Power BI szolgáltatásban, a Power BI Desktopban és a Power BI mobilalkalmazásban érhetők el. Ez a cikk a szolgáltatás és az asztali alkalmazás használatához nyújt útmutatást.

### <a name="enable-the-arcgis-map-in-power-bi-service-apppowerbicom"></a>ArcGIS-térkép engedélyezése a ***Power BI szolgáltatásban (app.powerbi.com)***
Ez az oktatóanyag a [Kiskereskedelmi elemzési mintát](sample-retail-analysis.md) használja. Az **ArcGIS Maps for Power BI** engedélyezése:

1. A menüsor jobb felső részén kattintson a fogaskerék ikonra, és nyissa meg a **Beállításokat**
   
    ![](media/power-bi-visualization-arcgis/power-bi-settings.png)
2. Jelölje be az **ArcGIS Maps for Power BI** jelölőnégyzetet. A bejelölés után újra kell indítania a Power BI-t.
   
    ![](media/power-bi-visualization-arcgis/power-bi-use-arcgis-new.png)
3. Nyisson meg egy jelentést [Szerkesztési nézetben](service-reading-view-and-editing-view.md), és a Vizualizációk panelen kattintson az ArcGIS Maps for Power BI ikonra.
   
    ![](media/power-bi-visualization-arcgis/power-bi-viz-pane2.png)
4. A Power BI hozzáad egy üres ArcGIS-térképsablont a jelentésvászonhoz.
   
   ![](media/power-bi-visualization-arcgis/power-bi-esri-placeholder2new.png)

<br/>

## <a name="create-an-arcgis-map-visual"></a>ArcGIS-térképes vizualizáció létrehozása
Figyelje meg, hogyan hoz létre Will néhány ArcGIS-térképes vizualizációt, majd az alábbi lépések alapján próbálja ki Ön is, a [Kiskereskedelmi elemzési minta](sample-datasets.md) használatával.

<iframe width="560" height="315" src="https://www.youtube.com/embed/EKVvOZmxg9s" frameborder="0" allowfullscreen></iframe>

1. A **Mezők** panelen húzzon egy adatmezőt a **Hely** vagy a **Szélesség** és/vagy **Hosszúság** gyűjtőkbe. Ebben a példában az **Üzlet > Város** adatokat használjuk.
   
   > [!NOTE]
   > Az ArcGIS Maps for Power BI automatikusan érzékeli, hogy a kiválasztott mezők formaként vagy pontként jeleníthetők meg a legjobban a térképen. Az alapértelmezett beállítást a beállítások között módosíthatja (lásd alább).
   > 
   > 
   
    ![](media/power-bi-visualization-arcgis/power-bi-fields-pane3new.png)
2. Alakítsa át a vizualizációt ArcGIS-térképpé. Ehhez válassza ki a sablont a Vizualizációk panelen ![](media/power-bi-visualization-arcgis/power-bi-arcgis-template.png).
3. A **Mezők** panelen húzzon egy mértéket a **Méret** gyűjtőbe, így megadja az adatok megjelenítésének módját. Ebben a példában az **Értékesítés > Előző évi értékesítés** adatokat használjuk.
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-point-map-size2new.png)

## <a name="settings-and-formatting-for-arcgis-maps"></a>Az ArcGIS-térképek beállításai és formázása
Az **ArcGIS Maps for Power BI** formázási funkcióinak elérése:

1. Válassza a vizualizáció jobb felső sarkában található három pontot, majd a **Szerkesztés** lehetőség kiválasztásával nyissa meg a további funkciókat.
   
   ![](media/power-bi-visualization-arcgis/power-bi-edit2.png)
   
   Az elérhető funkciók a vizualizáció felső részén jelennek meg. Az egyes funkciók kiválasztásakor megnyílik egy részletes lehetőségeket tartalmazó feladatpanel.<br/>
   
   ![](media/power-bi-visualization-arcgis/power-bi-esri-features-new.png)
   
   > [!NOTE]
   > A beállításokra és funkciókra vonatkozó további információkért lásd az alábbi **Részletes dokumentációt**.
   > 
   > 
2. A jelentéshez való visszatéréshez válassza a jelentésvászon bal felső sarkában található **Vissza a jelentéshez** lehetőséget.

<br/>

## <a name="detailed-documentation"></a>Részletes dokumentáció
Az **Esri** [átfogó dokumentációt](https://go.microsoft.com/fwlink/?LinkID=828772) biztosít az **ArcGIS Maps for Power BI** szolgáltatáskészletére vonatkozóan.

## <a name="features-overview"></a>Funkciók áttekintése
### <a name="base-maps"></a>Alaptérképek
Négy alaptérkép áll rendelkezésre: sötétszürke vászon, világosszürke vászon, OpenStreetMap és utcák.  Az ArcGIS standard alaptérképe az utcák.

Ha alkalmazni kíván egy alaptérképet, válassza ki a feladatpanelen.

![](media/power-bi-visualization-arcgis/power-bi-esri-base-maps-new.png)

### <a name="location-type"></a>Hely típusa
Az ArcGIS Maps for Power BI automatikusan észleli az adott térkép megjelenítésének legjobb módját. A Points (Pontok) vagy a Boundaries (Határok) lehetőségek közül választ. A Location Type (Hely típusa) beállítással pontosíthatja ezt a választást.

![](media/power-bi-visualization-arcgis/power-bi-esri-location-types-new.png)

A **Boundaries** (Határok) megjelenítés csak akkor használható, ha az adatok standard földrajzi értékeket tartalmaznak. Az Esri automatikusan meghatározza a térképen megjelenítendő formát. A standard geometriai értékek közé tartoznak az országok, a tartományok, az irányítószámok stb. Azonban a GeoCodinghoz hasonlóan előfordulhat, hogy a Power BI nem észleli, hogy a határnak alapértelmezés szerint határnak kellene lennie, vagy hogy nem rendelkezik határértékkel az adatokhoz.  

### <a name="map-theme"></a>A térkép témája
Négy térképtéma áll rendelkezésre. A Location Only (Csak hely) és a Size (Méret) témákat a rendszer automatikusan kiválasztja a helyhez kapcsolt mezők alapján, majd hozzáadja a **Méret** gyűjtőhöz a Power BI Mezők paneljén. Jelenleg a **Size** (Méret) témát használja, ezért váltsunk a **Heat Map** (Hőtérkép) témára.  

![](media/power-bi-visualization-arcgis/power-bi-esri-map-theme-new.png)

<table>
<tr><th>Téma</th><th>Leírás</th>
<tr>
<td>Location Only (Csak hely)</td>
<td>Az adatpontokat vagy a kitöltött határokat a Location Type (Hely típusa) beállításai alapján jeleníti meg.</td>
</tr>
<tr>
<td>Heat Map (Hőtérkép)</td>
<td>Intenzitási adatmegjelenítést ábrázol a térképen.</td>
</tr>
<tr>
<td>Size (Méret)</td>
<td>A méretezett adatpontokat a mezők panel méret gyűjtőjében szereplő érték alapján rajzolja fel.</td>
</tr>
<tr>
<td>Clustering (Fürtözés)</td>
<td>A térkép régióiban szereplő adatpontok számát jeleníti meg. </td>
</tr>
</table>


### <a name="symbol-style"></a>Symbol Style (Szimbólumstílus)
A szimbólumstílusok használatával pontosítható az adatok térképen való megjelenése. A szimbólumstílusok a Hely típusa és a kiválasztott Térképtéma kontextusától függenek. Az alábbi példában a Location Type (Hely típusa) **Size** (Méret) értékre van beállítva, továbbá számos átlátszósági, valamint stílus- és méretbeállítás van megadva.

![](media/power-bi-visualization-arcgis/power-bi-esri-symbol-style-new.png)

### <a name="pins"></a>Gombostűk
A térkép egyes pontjaira gombostűk hozzáadásával hívhatja fel a figyelmet.  

1. Kattintson a **Pins** (Gombostűk) fülre.
2. Adja meg a kulcsszavakat (pl. címek, helyek és hasznos helyek) a keresőmezőben, és válasszon a legördülő menüből. Ekkor egy szimbólum jelenik meg a térképen, a térkép pedig automatikusan ráközelít az adott helyre. A rendszer helykártyákként menti a keresési találatokat a Gombostűk panelen. Legfeljebb 10 helykártya menthető.
   
   ![](media/power-bi-visualization-arcgis/power-bi-pin-arcgis-newer.png)
3. A Power BI egy gombostűt ad hozzá a helyhez, a gombostű színe pedig módosítható.
   
   ![](media/power-bi-visualization-arcgis/power-bi-pin-color-new.png)
4. Gombostűk hozzáadása és törlése.
   
   ![](media/power-bi-visualization-arcgis/power-bi-pin3.png)

### <a name="drive-time"></a>Drive Time (Utazási idő)
A Drive Time (Utazási idő) panelen kiválaszthat egy helyet, és meghatározhatja, hogy mely térképelemek találhatók még egy adott távolságon vagy utazási időn belül.  
    ![](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

1. Válassza a **Drive Time** (Utazási idő) fület, és válassza az egyszeres vagy többszörös kijelölés eszközt. Egyszeres kijelöléssel jelölje ki a Washington, D.C.-hez tartozó gombostűt
    ![](media/power-bi-visualization-arcgis/power-bi-esri-single-select.png)
   
   > [!TIP]
   > A hely kiválasztása egyszerűbb, ha ráközelít a térképen (a + ikon használatával).
   > 
   > 
2. Tegyük fel, hogy néhány napra Washington D.C.-be kell repülnie, és arra kíváncsi, hogy melyik üzletek érhetők el ésszerű utazási időn belül. Módosítsa a Search Area (Keresési terület) beállítást **Radius** (Sugár) értékre, a Distance (Távolság) értékét pedig **50** mérföldre, majd válassza az OK lehetőséget.    
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-drive-time-radius.png)
3. A sugár lila színnel jelenik meg. Kattintson bármely helyre a részletek megjelenítéséhez. A sugarat a szín és a körvonal módosításával formázhatja is.
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

### <a name="reference-layer"></a>Reference Layer (Referenciaréteg)
#### <a name="reference-layer---demographics"></a>Reference Layer – Demographics (Referenciaréteg – Demográfiai adatok)
Az ArcGIS Maps for Power BI számos demográfiai réteget tartalmaz, amelyekkel kontextusba helyezheti a Power BI-ban tárolt adatokat.

1. Válassza ki a **Reference layer** (Referenciaréteg) fület, és válassza a **Demographics** (Demográfiai adatok) lehetőséget.
2. Minden réteghez tartozik egy jelölőnégyzet. A réteg térképhez való hozzáadásához jelölje be a kívánt jelölőnégyzeteket.  Ebben a példában a háztartás átlagos bevételét adtuk hozzá.<br/>
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-reference-layer-demographic.png)
3. Minden réteg interaktív. A buborékok fölé mozgatott kurzorhoz hasonlóan a térkép árnyékolt területeire kattintva megtekintheti a részleteket.<br/>
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-reference-layer-details.png)

#### <a name="reference-layer---arcgis"></a>Reference Layer - ArcGIS (Referenciaréteg – ArcGIS)
Az ArcGIS Online szolgáltatás használatával a vállalatok nyilvános webes térképeket tehetnek közzé. Ezen felül az Esri válogatott webes térképeket kínál a Living Atlason keresztül. Az ArcGIS lapon az összes nyilvános webes térkép és Living Atlas-térkép között kereshet, és referenciarétegként hozzáadhatja őket a térképhez.

1. Kattintson a **Reference layer** (Referenciaréteg) fülre, és válassza az **ArcGIS** lehetőséget.
2. Írja be a keresési kifejezéseket, majd válasszon egy térképréteget. Ebben a példában az egyesült államokbeli kongresszusi körzeteket választottuk.
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-demographics-esri2-new.png)
3. Ha szeretné megtekinteni a részleteket, válasszon egy árnyékolt területet a *Select from reference layer* (Kiválasztás referenciarétegről) eszköz megnyitásához. A referenciaréteg-választó eszközzel határokat vagy objektumokat választhat ki a referenciarétegen.

<br/>

## <a name="selecting-data-points"></a>Adatpontok kiválasztása
Az ArcGIS Maps for Power BI három kijelölési módot tesz lehetővé.

Változtassa meg a kijelölési módot a kapcsolóval:

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-single2.png) Egyéni adatpontok kijelölése.

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-marquee2.png) A térképre rajzolt négyszögbe foglalt összes adatpont kijelölése.

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-layer2.png) A referenciafóliákon lévő határvonalak és sokszögek is használhatóak a bennfoglalt adatok kijelölésére.

> [!NOTE]
> Egyszerre legfeljebb 250 adatpont jelölhető ki.
> 
> 

<br/>

## <a name="getting-help"></a>A súgó használata
Az **Esri** [átfogó dokumentációt](https://go.microsoft.com/fwlink/?LinkID=828772) biztosít az **ArcGIS Maps for Power BI** szolgáltatáskészletére vonatkozóan.

A Power BI [**ArcGIS Maps for Power BI** termékkel kapcsolatos közösségi csatornáján](https://go.microsoft.com/fwlink/?LinkID=828771) felteheti kérdéseit, megtalálhatja a legfrissebb információkat, jelentheti a hibákat és válaszokat kaphat.

Amennyiben fejlesztési javaslatai vannak, azokat a [Power BI ötletlistájához](https://ideas.powerbi.com) adja hozzá.

<br/>

## <a name="managing-use-of-arcgis-maps-for-power-bi-within-your-organization"></a>Az ArcGIS Maps for Power BI cégen belüli használata
A Power BI használatával a felhasználók, a bérlői rendszergazdák és az informatikai rendszergazdák eldönthetik, hogy szeretnék-e használni az ArcGIS Maps for Power BI-t.

**Felhasználói beállítások** A Power BI Desktopban a felhasználók kikapcsolhatják az ArcGIS Maps for Power BI használatát, ha a **Beállítások** menü Biztonság lapján letiltják azt. Ha le van tiltva, az ArcGIS Maps alapértelmezés szerint nem töltődik be.

![](media/power-bi-visualization-arcgis/power-bi-desktop-security-dialog2.png)

A Power BI szolgáltatásban a felhasználók kikapcsolhatják az ArcGIS Maps for Power BI használatát, ha a felhasználói beállításokat tartalmazó menü ArcGIS Maps for Power BI lapján letiltják azt. Ha le van tiltva, az ArcGIS Maps alapértelmezés szerint nem töltődik be.

![](media/power-bi-visualization-arcgis/power-bi-use-arcgis-new.png)

**Bérlői rendszergazdai beállítások** A PowerBI.com webhelyen a bérlői rendszergazdák minden bérlői felhasználó számára letilthatják az ArcGIS Maps for Power BI használatát. Ebben az esetben a Power BI vizualizációk panelén nem fog megjelenni az ArcGIS Maps for Power BI ikon.

![](media/power-bi-visualization-arcgis/power-bi-arcgis-admin-portal2.png)

**Informatikai rendszergazdai beállítások** A Power BI Desktop támogatja a **Csoportházirendek** használatát az ArcGIS Maps for Power BI használatának letiltásához a cég összes üzembe helyezett számítógépén.

<table>
<tr><th>Attribútum</th><th>Érték</th>
</tr>
<tr>
<td>key</td>
<td>Software\Policies\Microsoft\Power BI Desktop&lt;/td&gt;
</tr>
<tr>
<td>valueName</td>
<td>EnableArcGISMaps</td>
</tr>
</table>

Az 1 (decimális) érték engedélyezi az ArcGIS Maps for Power BI használatát.

A 0 (decimális) érték letiltja az ArcGIS Maps for Power BI használatát.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
Az ArcGIS Maps for Power BI az alábbi szolgáltatásokban és alkalmazásokban érhető el:

<table>
<tr><th>Szolgáltatás/alkalmazás</th><th>Elérhetőség</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Igen</td>
</tr>
<tr>
<td>Power BI szolgáltatás (PowerBI.com)</td>
<td>Igen</td>
</tr>
<tr>
<td>Power BI mobilalkalmazások</td>
<td>Igen</td>
</tr>
<tr>
<td>Power BI webes közzététel</td>
<td>Nem</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>Nem</td>
</tr>
<tr>
<td>Power BI szolgáltatás beágyazása (PowerBI.com)</td>
<td>Nem</td>
</tr>
</table>

Azokban a szolgáltatásokban és alkalmazásokban, ahol az ArcGIS Maps for Power BI nem elérhető, a képi megjelenítésben üres vizualizáció jelenik meg a Power BI emblémával.

Az utcacímek geokódolása során csak az első 1500 cím lesz geokódolva. A helynevek és országok geokódolására az 1500 címes korlát nem vonatkozik.

<br/>

**Hogyan működik az ArcGIS Maps for Power BI?**
Az ArcGIS Maps for Power BI szolgáltatója az Esri (www.esri.com). Az ArcGIS Maps for Power BI használatára az Esri [szerződési feltételei](https://go.microsoft.com/fwlink/?LinkID=8263222) és [adatvédelmi szabályzata](https://go.microsoft.com/fwlink/?LinkID=826323) vonatkoznak. Ha a Power BI-felhasználó használni kívánja az ArcGIS Maps for Power BI vizualizációit, el kell fogadnia a feltételeket (részletekért tekintse meg a felhasználói beleegyezésről szóló szakaszt).  Az Esri ArcGIS Maps for Power BI az Esri használati feltételeinek és adatvédelmi szabályzatának hatálya alá tartozik, amelyek elérhetők a beleegyező párbeszédpanelről. Az ArcGIS Maps for Power BI első használata előtt minden felhasználónak el kell fogadnia a feltételeket. Miután a felhasználók elfogadták a feltételeket, a program elküldi a vizualizációhoz tartozó adatokat az Esrinek geokódolásra, amelyne során a helyadatok térképen megjeleníthető szélességi és hosszúsági adatokká lesznek átalakítva. Érdemes annak tudatában használni a szolgáltatást, hogy az Esri minden, adatvizualizációhoz tartozó adatot megkaphat. Az Esri olyan szolgáltatásokat nyújt, mint az alaptérképek, térelemzés, geokódolás és hasonlók. Az ArcGIS Maps for Power BI vizualizáció ezekkel a szolgáltatásokkal egy SSL-kapcsolaton keresztül kommunikál, amelyet egy Esri által nyújtott és fenntartott tanúsítvány véd. További információt az ArcGIS Maps for Power BI szolgáltatásról az Esri [ArcGIS Maps for Power BI termékoldalán](https://www.esri.com/powerbi) találhat.

Amikor egy felhasználó az ArcGIS Maps for Power BI egy, az Esri által ajánlott Plus-előfizetésére regisztrál, közvetlen kapcsolatba kerül az Esrivel. A Power BI nem küld személyes felhasználói adatokat az Esrinek. A felhasználó a bejelentkezés után megadja a saját AAD-identitását egy Esri által nyújtott AAD-alkalmazásnak. Ezzel személyes adatokat oszt meg közvetlenül az Esrivel. Ha egy felhasználó Plus-tartalmakat ad meg egy ArcGIS Maps for Power BI-vizualizációhoz, a többi felhasználónak szintén Plus-előfizetésre lesz szüksége az adott tartalom megtekintéséhez vagy szerkesztéséhez. 

Az Esri ArcGIS Maps for Power BI működésével kapcsolatos részletes technikai kérdésekkel az Esri támogatási oldalához fordulhat.


**Van valamilyen díja az ArcGIS Maps for Power BI használatának?**

Az ArcGIS Maps for Power BI minden Power BI-felhasználó számára elérhető külön költségvonzatok nélkül. Ezt az összetevőt az **Esri** biztosítja, ezért használata az **Esri** használati feltételeinek és adatvédelmi szabályzatának elfogadásához kötött, ahogy az a cikkben korábban olvasható.

**Hibaüzenetet kapok Power BI Desktopban arról, hogy megtelt a gyorsítótár**

Ez egy programhiba, amelynek a javítása folyamatban van.  Addig is a gyorsítótár ürítéséhez törölje a fájlokat a C:\Users\\AppData\Local\Microsoft\Power BI Desktop\CEF mappából, majd indítsa újra a Power BI-t.

**Támogatja az ArcGIS Maps for Power BI az Esri-alakzatfájlok használatát?**

Az ArcGIS Maps for Power BI automatikusan észleli a standard határokat, például az országok/régiók, államok/tartományok, illetve irányítószámok határait. Ha saját alakzatokat kell megadnia, megteheti a [Shape Maps for Power BI Desktop (előzetes verzió)](desktop-shape-map.md) használatával.

**Offline is megtekinthetem az ArcGIS-térképeimet?**

Nem, a térképek megjelenítéséhez a Power BI-nak kapcsolódnia kell a hálózathoz.

**Csatlakozhatok az ArcGIS Online-fiókomhoz a Power BI-ból?**

Jelenleg nem. [Szavazzon erre az ötletre](https://ideas.powerbi.com/forums/265200-power-bi-ideas/suggestions/9154765-arcgis-geodatabases), és e-mailben értesítjük, ha hozzákezdtünk a funkció fejlesztéséhez.  

## <a name="next-steps"></a>Következő lépések
[Az Önnel megosztott ArcGIS-térképek használata](power-bi-visualizations-arcgis.md)

[Az ArcGIS Maps for Power BI elérhetőségét bejelentő blogbejegyzés](https://powerbi.microsoft.com/blog/announcing-arcgis-maps-for-power-bi-by-esri-preview/)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

