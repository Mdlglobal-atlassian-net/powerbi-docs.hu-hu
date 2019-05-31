---
title: Az Önnel megosztott ArcGIS-térképek használata
description: ArcGIS-térképek használata olvasási nézetben Power BI-jelentésfelhasználóként
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/10/2019
ms.author: mihart
ms.openlocfilehash: 49eb11698d05ee8877f78b6b3d4cbbc6ef403e75
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61137088"
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>ArcGIS-térképek használata a Power BI-ban
Ez a témakör az ArcGIS-térképet a Power BI szolgáltatás, a Desktop alkalmazás vagy a mobilalkalmazás felületén *használó* felhasználó szemszögéből van megírva. Ha egy ArcGIS-térképet a létrehozója megoszt Önnel, számos különféle módon használhatja azt.  Az ArcGIS-térképek létrehozásával kapcsolatos információkért lásd: [Az esri ArcGIS-térképeinek oktatóanyaga](../visuals/power-bi-visualization-arcgis.md).

Az ArcGIS-térképek és a Power BI együttes használata új lehetőségeket kínál a térképkezelésben, amelyek messze túlmutatnak a pontok térképeken való elhelyezésén. Az alaptérképekhez, helytípusokhoz, témákhoz, szimbólumstílusokhoz és referenciarétegekhez elérhető beállítások segítségével lenyűgöző és informatív térképi megjelenítések hozhatók létre. A térképen megjelenített mérvadó adatrétegek (például népszámlálási adatok) és a térbeli elemzés egyesítésével jobban megértheti a képi megjelenítésben szereplő adatokat.

> [!TIP]
> A GIS az angol Geographic Information System (térinformatikai rendszer) kifejezés rövidítése.
> 

Az itt használt példa a tavalyi értékesítési adatokat jeleníti meg városok szerint, és egy utcaszintű alaptérképet, a méretet jelölő buborékszimbólumokat és a háztartásonkénti átlagjövedelmet megjelenítő referenciaréteget tartalmaz. A térképen 3 jelölőt és egy, az utazási időt jelző körívet (lila) tartalmaz.

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> Példákat és beszámolókat az [esri Power BI-oldalán](https://www.esri.com/powerbi) talál. Ezután tekintse meg az esri [ArcGIS Maps for Power BI termékének Első lépések oldalát](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) is.
> 
> 

<br/>

## <a name="user-consent"></a>Felhasználói beleegyezés
Az első alkalommal, amikor egy kollégája megoszt Önnel egy ArcGIS-térképet, a Power BI megjelenít egy figyelmeztetést. Az ArcGIS Maps for Power BI terméket az Esri (www.esri.com) fejleszti, így a térképek használatára az Esri használati feltételei és adatvédelmi szabályzata vonatkozik. Ha a Power BI-felhasználó alkalmazni szeretné az ArcGIS Maps for Power BI vizualizációit, el kell fogadnia a feltételeket.

## <a name="selection-tools"></a>Kijelölési eszközök
Az ArcGIS Maps for Power BI három kijelölési módot tesz lehetővé. Egyszerre legfeljebb 250 adatpont jelölhető ki.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) Egyéni adatpontok kijelölése.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) A térképre rajzolt négyszögbe foglalt összes adatpont kijelölése. A CTRL billentyű lenyomásával több négyszögletes terület is kijelölhető.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) A referenciarétegeken lévő határvonalak és sokszögek által közrefogott összes adatpont kijelölése.

<br/>

## <a name="interacting-with-an-arcgis-map"></a>Az ArcGIS-térképek használata
Az elérhető funkciók attól függően változnak, hogy Ön a térkép *létrehozója* (aki a térképet készítette) vagy *felhasználója* (valaki megosztotta Önnel az ArcGIS-térképet). Ha felhasználóként használja valamely ArcGIS-térképet (lásd [Olvasás nézet](../consumer/end-user-reading-view.md)), az alábbi műveleteket hajthatja végre.

* Ha Ön *megtekintési* engedélyekkel rendelkező Prémium-felhasználó, akkor többek között [megtekintheti a vizualizáció létrehozásához használt adatokat](../consumer/end-user-show-data.md), [feliratkozhat](../consumer/end-user-subscribe.md), megtekintheti a térképet [Fókusz módban és teljes képernyős módban](../consumer/end-user-focus.md), [megtekintheti a kapcsolódó tartalmakat](../consumer/end-user-related.md), [használhatja azokat a szűrőket](../consumer/end-user-report-filter.md), amelyeket a *jelentés létrehozója* adott meg és [megoszthatja a jelentést](../service-share-reports.md).

* Akárcsak más vizualizációtípusok esetében, a Power BI **Pro**-felhasználóknak minden olyan joguk megvan, amivel a Premium-felhasználók rendelkeznek, ezenfelül többek között [exportálhatják az alapul szolgáló adatokat](../visuals/power-bi-visualization-export-data.md), [lekérhetik a használati metrikákat](../service-usage-metrics.md) és menthetnek egy másolatot és [közzétehetik a weben](../service-publish-to-web.md).

    
* A **Szűrők** panel kibontásával szűrők használatával derítheti fel a térképet.   
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* Ha a térkép tartalmaz referenciaréteget, a helyek kijelölésekor a részletek elemleírásokban jelennek meg. Az Adams megye van kijelölve, így a létrehozó által hozzáadott háztartásonkénti átlagjövedelem referenciafólia adatai láthatók.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    Ebben az esetben egy diagram is látható. A diagram sávjainak kijelölésével részletesebb adatok jelennek meg. Láthatjuk, hogy Adams megyében 79 háztartás bevétele éri el az évi 200 000 dollárt.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    A nyíl ikon használatával további diagramokat jeleníthet meg.
* A kurzort az alaptérkép helyszimbólumai fölé mozgatva elemleírásokban jelenítheti meg a részleteket.     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > Lehet, hogy bizonyos helyek kijelöléséhez nagyítás szükséges.  Ellenkező esetben előfordulhat, hogy a Power BI egyszerre jeleníti meg az egymást fedő helyek elemleírásait. Az elemleírások közt a nyilak használatával léptethet.
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* Ha a létrehozó Infografika réteget is hozzáadott az ArcGIS-térképhez, további adatok jelennek meg a térkép jobb felső sarkában.  Jelen esetben például a „14 év alatti gyermekek” réteg lett hozzáadva.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
Az ArcGIS Maps for Power BI az alábbi szolgáltatásokban és alkalmazásokban érhető el:

<table>
<tr><th>Szolgáltatás/alkalmazás</th><th>Elérhetőség</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Igen</td>
</tr>
<tr>
<td>Power BI service (app.powerbi.com)</td>
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

**Hogyan működik az ArcGIS Maps for Power BI?**
Az ArcGIS Maps for Power BI szolgáltatója az Esri (www.esri.com). Az ArcGIS Maps for Power BI használatára az Esri [szerződési feltételei](https://go.microsoft.com/fwlink/?LinkID=8263222) és [adatvédelmi szabályzata](https://go.microsoft.com/fwlink/?LinkID=826323) vonatkoznak. Ha a Power BI-felhasználó használni kívánja az ArcGIS Maps for Power BI vizualizációit, el kell fogadnia a feltételeket (részletekért tekintse meg a felhasználói beleegyezésről szóló szakaszt).  Az Esri ArcGIS Maps for Power BI az Esri használati feltételeinek és adatvédelmi szabályzatának hatálya alá tartozik, amelyek elérhetők a beleegyező párbeszédpanelről. Az ArcGIS Maps for Power BI első használata előtt minden felhasználónak el kell fogadnia a feltételeket. Miután a felhasználók elfogadták a feltételeket, a program elküldi a vizualizációhoz tartozó adatokat az Esrinek geokódolásra, amelyne során a helyadatok térképen megjeleníthető szélességi és hosszúsági adatokká lesznek átalakítva. Érdemes annak tudatában használni a szolgáltatást, hogy az Esri minden, adatvizualizációhoz tartozó adatot megkaphat. Az Esri olyan szolgáltatásokat nyújt, mint az alaptérképek, térelemzés, geokódolás és hasonlók. Az ArcGIS Maps for Power BI vizualizáció ezekkel a szolgáltatásokkal egy SSL-kapcsolaton keresztül kommunikál, amelyet egy Esri által nyújtott és fenntartott tanúsítvány véd. További információt az ArcGIS Maps for Power BI szolgáltatásról az Esri [ArcGIS Maps for Power BI termékoldalán](https://www.esri.com/powerbi) találhat.

**Power BI Plus**    
![A Plus ikont választva regisztrálhat vagy bejelentkezhet](media/power-bi-visualizations-arcgis/power-bi-plus.png)

Amikor egy felhasználó az ArcGIS Maps for Power BI egy, az Esri által ajánlott Plus-előfizetésére regisztrál, közvetlen kapcsolatba kerül az Esrivel. A Power BI nem küld személyes felhasználói adatokat az Esrinek. A felhasználó a bejelentkezés után megadja a saját AAD-identitását egy Esri által nyújtott AAD-alkalmazásnak. Ezzel személyes adatokat oszt meg közvetlenül az Esrivel. Ha egy felhasználó Plus-tartalmakat ad meg egy ArcGIS Maps for Power BI-vizualizációhoz, a többi felhasználónak szintén Plus-előfizetésre lesz szüksége az adott tartalom megtekintéséhez vagy szerkesztéséhez. 

Az Esri ArcGIS Maps for Power BI működésével kapcsolatos részletes technikai kérdésekkel az Esri támogatási oldalához fordulhat.

**Az ArcGIS-térkép nem jelenik meg**    
Azokban a szolgáltatásokban és alkalmazásokban, ahol az ArcGIS Maps for Power BI nem elérhető, a képi megjelenítésben üres vizualizáció jelenik meg a Power BI emblémával.

**Nem jelenik meg az összes információ a térképen**    
A térkép szélességi/hosszúsági adatainak geokódolásakor legfeljebb 30 000 adatpont jelenik meg. Az olyan adatpontok geokódolása során, mint az irányítószámok és utcacímek, csak az első 15 000 adatpont lesz geokódolva. A helynevek és országok geokódolására az 1500 címes korlát nem vonatkozik.

**Van valamilyen díja az ArcGIS Maps for Power BI használatának?**

Az ArcGIS Maps for Power BI minden Power BI-felhasználó számára elérhető külön költségvonzatok nélkül. Ezt az összetevőt az **Esri** biztosítja, ezért használata az **Esri** használati feltételeinek és adatvédelmi szabályzatának elfogadásához kötött, ahogy az a cikkben korábban olvasható. Ha feliratkozik az ArcGIS **Plus** szolgáltatásra, az díjfizetési kötelezettséggel jár.

**Hibaüzenetet kapok arról, hogy megtelt a gyorsítótár**

Ez egy programhiba, amelynek a javítása folyamatban van.  Addig is a hibaüzenetben lévő hivatkozásra kattintva megtudhatja, hogyan ürítheti a Power BI gyorsítótárát.

**Kapcsolat nélkül is megtekinthetem az ArcGIS-térképeimet?**

Nem, a térképek megjelenítéséhez a Power BI-nak kapcsolódnia kell a hálózathoz.

## <a name="next-steps"></a>Következő lépések
Ahonnan segítséget kaphat: Az **Esri** [átfogó dokumentációt](https://go.microsoft.com/fwlink/?LinkID=828772) biztosít az **ArcGIS Maps for Power BI** szolgáltatáskészletére vonatkozóan.

A Power BI [**ArcGIS Maps for Power BI** termékkel kapcsolatos közösségi csatornáján](https://go.microsoft.com/fwlink/?LinkID=828771) felteheti kérdéseit, megtalálhatja a legfrissebb információkat, jelentheti a hibákat és válaszokat kaphat.


[Az ArcGIS Maps for Power BI termékoldala](https://www.esri.com/powerbi)
