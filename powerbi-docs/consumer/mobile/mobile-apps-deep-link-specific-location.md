---
title: Egy meghatározott helyre mutató hivatkozás létrehozása a Power BI-mobilalkalmazásokban
description: Megtudhatja, hogyan hozhat létre a Power BI-mobilalkalmazásban meghatározott irányítópultra, csempére vagy jelentésre mutató mélyhivatkozást URI használatával.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906538"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>A Power BI-mobilalkalmazásokon belül egy meghatározott helyre mutató hivatkozás létrehozása
Hivatkozások segítségével közvetlenül a Power BI-ban meghatározott elemek eléréséhez: Jelentés, az irányítópult és a csempe.

A hivatkozások használata a Power BI Mobile nagyrészt két forgatókönyv közül választhat: 

* Nyissa meg a Power bi-ban való **az alkalmazáson kívül**, valamint az adott tartalmon (jelentés vagy irányítópult vagy alkalmazás). Ez általában a-integrációs forgatókönyv, ha meg szeretné nyitni a Power BI Mobile más alkalmazásból. 
* A **lépjen** belüli Power bi-ban. Ez akkor általában akkor, ha szeretne létrehozni egy egyéni navigáció a Power bi-ban.


## <a name="use-links-from-outside-of-power-bi"></a>Hivatkozásokat a Power BI szolgáltatáson kívül
Egy hivatkozást a Power BI alkalmazáson kívül használatakor szeretne-e győződjön meg arról, hogy azt nyitja meg az alkalmazást, és ha az alkalmazás nincs telepítve az eszközön, majd telepítheti a felhasználónak. A speciális hivatkozás formátuma hoztunk létre, amely pontosan támogatása érdekében. Ezt a hivatkozási formátumot, győződjön meg arról, hogy az eszköz a hivatkozás megnyitásához használja az alkalmazást, és ha az alkalmazás nincs telepítve az eszközön, akkor a felhasználót, hogy a Store áruházból való letöltés felajánlja lesz.

A hivatkozás a következő webalkalmazásokba  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> Ha a tartalom üzemel, a speciális adatközpont, például a kormány Esettanulmányának, Kína, stb. A hivatkozás el kell indulnia a megfelelő Power BI-címmel, például `app.powerbigov.us` vagy `app.powerbi.cn`.   
>


A **lekérdezési paraméterei** vannak:
* **action** (mandatory) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **identifikátor appId** =, ha meg szeretné nyitni egy jelentést vagy irányítópultot egy alkalmazás részét képező 
* **groupObjectId** =, ha meg szeretné nyitni egy jelentést vagy irányítópultot munkaterület (de nem a saját munkaterület) részét képező
* **dashboardObjectId** = irányítópult objektum azonosítója (Ha a művelet OpenDashboard vagy OpenTile)
* **reportObjectId** = jelentésobjektum Azonosítójának (Ha a művelet JelentésMegnyitása)
* **tileObjectId** = csempe objektum azonosítója (Ha a művelet OpenTile)
* **reportPage** =, ha meg szeretné nyitni a meghatározott jelentésre hivatkozó szakaszt (Ha a művelet JelentésMegnyitása)
* **ctId** = elem a szervezet azonosítója (B2B a forgatókönyvhöz kapcsolódó. Ez elhagyható, ha a cikk a felhasználó szervezete tartozik).

**Példák:**

* Nyissa meg az alkalmazásra mutató hivatkozás 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* Egy alkalmazás részét képező irányítópult megnyitása 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* Nyissa meg a jelentést, amely része egy munkaterületet
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>A megfelelő hivatkozás formátuma beszerzése

#### <a name="links-of-apps-and-items-in-app"></a>Az alkalmazások és az alkalmazás elemeinek hivatkozások

A **alkalmazások és a jelentések és irányítópult-alkalmazás részét képező**, szerezzen be a hivatkozást a legegyszerűbb módja az, hogy nyissa meg az alkalmazás-munkaterületet, és válassza az "App frissítése". Ekkor megnyílik a "közzététel" alkalmazásélményről, és a hozzáférési lapon található egy **hivatkozások** szakaszban. Bővülő, hogy szakaszban fog megjelenni az alkalmazások listájában, és minden tartalom hivatkozik, amely segítségével közvetlenül érheti el őket.

![A Power BI alkalmazás hivatkozások közzététele ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>Hivatkozások elemek nincs alkalmazás 

A jelentéseket és irányítópultokat, amelyek nem részei egy alkalmazást az azonosítók kinyerni az elem URL-címet kell.

Például keresse meg a 36 karakterből álló **irányítópult** objektumazonosító, lépjen az adott irányítópultra a Power BI szolgáltatásban 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

A 36 karakterből álló található **jelentés** objektumazonosító, keresse meg az adott jelentéshez a Power BI szolgáltatásban.
Ez a jelentés egy példa a "Saját munkaterület"

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
A fenti URL-cím is tartalmazza, adott jelentésoldal **"ReportSection3"** .

Itt látható egy példa a jelentés egy munkaterületről (nem a saját munkaterület)

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Power bi-ban lévő hivatkozások

Hivatkozások belüli Power bi-ban a mobilalkalmazások pontosan hasonlóan a Power BI szolgáltatás működik.

Ha szeretné hozzáadhat a jelentéshez, egy másik Power BI-cikk mutató hivatkozás, csak másolhat adott elem URL-CÍMÉT a böngésző címsorában. Tudjon meg többet [hivatkozás hozzáadása szövegmezőhöz egy jelentésben szövegmező hogyan](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="use-report-url-with-filter"></a>Használati jelentés URL-cím szűrővel
Ugyanaz, mint a Power BI szolgáltatásban, a Power BI Mobile-alkalmazások is támogatja a jelentés URL-címe, amely egy szűrő lekérdezés param tartalmazza. Nyisson meg egy jelentést a Power BI Mobile app és a meghatározott állapotba szűrheti azokat. Például az URL-címet az értékesítési jelentés megnyitása és szűrés a területén

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

További tudnivalók a [hozhat létre a lekérdezés param szűrése jelentések](https://docs.microsoft.com/power-bi/service-url-filters).

## <a name="next-steps"></a>Következő lépések
A visszajelzése segít eldönteni, hogy milyen fejlesztésekre koncentráljunk a jövőben, ezért kérjük, ne mulasszon el szavazni más szolgáltatásokra, amelyeket szívesen látna a Power BI-mobilalkalmazásokban. 

* [Power BI-alkalmazások mobileszközökre](mobile-apps-for-mobile-devices.md)
* @MSPowerBI követése Twitteren
* Vegyen részt [a Power BI-közösség](http://community.powerbi.com/) beszélgetéseiben
* [Mi az a Power BI?](../../power-bi-overview.md)

