---
title: Kapacitás és SKU a Power BI Embedded Analyticsben
description: A Power BI Embedded Analytics kapacitásának és SKU-inak bemutatása.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: f8c3bdf3e3f92d570205551a97389def2921fe98
ms.sourcegitcommit: 17aad73762579d6822383b27b96b1b63f87f2d6f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/14/2020
ms.locfileid: "77260457"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Kapacitás és SKU a Power BI Embedded Analyticsben

Az éles környezetre való áttéréskor Power BI Embedded Analytics dedikált kapacitást igényel (*A*, *EM* vagy *P* SKU-k) a beágyazott Power BI-tartalmak közzétételéhez.

Kapacitásnak az olyan dedikált erőforráskészleteket nevezzük, amelyek kizárólagos használatra vannak fenntartva. Használatával irányítópultokat, jelentéseket és adathalmazokat tehet közzé anélkül, hogy felhasználónkénti licenceket kellene vásárolnia. A dedikált kapacitás emellett megbízható, egyenletes teljesítményt biztosít a tartalmakhoz.

>[!NOTE]
>A közzétételhez egy Power BI Pro-fiókra lesz szüksége.

## <a name="what-is-embedded-analytics"></a>Mit jelent a beágyazott analitika?

A Power BI beágyazott analitikája két megoldást tartalmaz:
* *Power BI Embedded* – egy Azure-ajánlat
* A Power BI beágyazása a *Power BI Premium* részeként – egy Office-ajánlat

### <a name="power-bi-embedded"></a>Power BI Embedded

A Power BI Embedded olyan független szoftvergyártók és fejlesztők számára készült, akik vizualizációkat ágyaznak be alkalmazásaikba.

A Power BI Embeddedet használó alkalmazások lehetővé teszik a felhasználók számára a Power BI Embedded-kapacitásban tárolt tartalmak felhasználását.

### <a name="power-bi-premium"></a>Power BI Premium

A [Power BI Premium](../service-premium-what-is.md) azokat a nagyvállalatokat célozza meg, akik egy teljes körű Power BI-megoldást szeretnének, amellyel egyetlen helyről áttekinthetik vállalatukat, partnereiket, ügyfeleiket és szállítóikat.

A Power BI Premium egy szolgáltatottszoftver-termék, amely mobilalkalmazásokon, belsőleg fejlesztett alkalmazásokon, vagy a Power BI portálon (Power BI szolgáltatás) keresztül a felhasználók számára is lehetővé teszi a tartalmak használatát. Ez lehetővé teszi, hogy a Power BI Premium a belső és külső ügyfelek felé irányuló alkalmazásokhoz is biztosítson megoldást.

## <a name="capacity-and-skus"></a>Kapacitás és SKU-k

Minden egyes kapacitás több SKU-t kínál, és minden SKU különböző erőforrásszinteket biztosít a memória és a számítási teljesítmény terén. Az, hogy milyen típusú SKU-ra van szükség attól függ, hogy milyen típusú megoldást szeretne üzembe helyezni.

Mielőtt eldöntené, milyen SKU-t vásárol, olvassa el az ebben a szakaszban található információkat.
* Arról, hogy mely számítási feladatok támogatottak az egyes szinteken, a [Számítási feladatok konfigurálása a prémium szintű kapacitásban](../service-admin-premium-workloads.md) című cikkben talál információt.
* A [kapacitás megtervezéséhez és teszteléséhez](../service-premium-capacity-optimize.md#testing-approaches) használja ezt a hivatkozást

### <a name="power-bi-embedded-skus"></a>A Power BI Embedded SKU-i

A Power BI Embedded alapkiépítésben *A* SKU-t tartalmaz.
* [Ismerje meg, hogy mit képes kezelni a Power BI Embedded](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan)
* [Az *A* SKU megvásárlása](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>A Power BI Premium termékváltozatai

A Power BI Premium két SKU-t kínál: *P* és *EM*.
* [A *P* és az *EM* SKU közötti különbségek megismerése](../service-premium-what-is.md#subscriptions-and-licensing)
* [Prémium szintű SKU megvásárlása](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Melyik SKU-t használjam?

Ez a táblázat összefoglalja a funkciókat, a hozzájuk szükséges kapacitást és az egyes felhasználók számára szükséges SKU-kat. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Funkció</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>Mi van felhasználva?</em><p></td>
<td><p><em>Mi végzi a felhasználást?</em><p></td>
<td style="text-align: center"><p><em>A SKU-k</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM SKU-k</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P SKU-k</br>(Office)</em></p></td>
</tr>
<tr>
<td>Összetevők beágyazása Power BI-munkaterületről</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI-jelentések</td>
<td>Egy beágyazott alkalmazás a szervezet számára</br>(a felhasználó tulajdonában lévő adatok)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Egy beágyazott alkalmazás az ügyfelei számára</br>(az alkalmazás tulajdonában lévő adatok)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI-tartalom<br>(ingyenes Power BI licenccel)</td>
<td>Power BI szolgáltatásban</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI mobile</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office-alkalmazások</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>Kapacitással kapcsolatos szempontok

Az alábbi táblázat a kapacitásokhoz a fizetési és használati szempontokat sorolja fel.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Ajánlat</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>Termékváltozat</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Számlázás</strong></td>
<td style="text-align: center;">Óránként</td>
<td style="text-align: center;">Havonta</td>
<td style="text-align: center;">Havonta</td>
</tr>
<tr>
<td><p><strong>Kötelezettségvállalás</strong></td>
<td style="text-align: center;">Nincs</td>
<td style="text-align: center;">Havi vagy éves</td>
<td style="text-align: center;">Havi vagy éves</td>
</tr>
<tr>
<td valign="top"><p><strong>Használat</strong></td>
<td style="text-align: center;">Az Azure-erőforrások lehetnek:</br>- <a href="azure-pbie-scale-capacity.md">Vertikálisan fel -vagy leskálázva</a></br>- <a href="azure-pbie-pause-start.md">Szüneteltetve és folytatva</a>
</td>
<td style="text-align: center;">Beágyazás az alkalmazásokban és</br> Microsoft-alkalmazásokban</td>
<td style="text-align: center;">Beágyazás az alkalmazásokban és</br> a Power BI szolgáltatásban</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU memória és számítási teljesítmény

Az alábbi táblázat az egyes termékváltozatok erőforrásait és korlátait ismerteti.

| Kapacitás-csomópontok | Összes virtuális mag | Háttérrendszeri virtuális magok | Memória (GB) | Előtérrendszeri virtuális magok | DirectQuery-/élő kapcsolatok (másodpercenként) | Párhuzamosan végrehajtható modellfrissítések |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
>[Beágyazás az ügyfelek számára](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Beágyazás a cég számára](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Beágyazás alkalmazásokból](embed-from-apps.md)