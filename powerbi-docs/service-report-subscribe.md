---
title: Feliratkozás jelentésekre és irányítópultokra a Power BI szolgáltatásban
description: Útmutató mások feliratkoztatásához Power BI-jelentések és -irányítópultok pillanatképére.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/04/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 73e89b0228a1adf78bf1676749f910c6d1866a81
ms.sourcegitcommit: 658b0de4f5a544d0906665b40925552804a61880
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/19/2019
ms.locfileid: "54406638"
---
# <a name="subscribe-to-a-report-or-dashboard-in-power-bi-service"></a>Feliratkozás egy jelentésre vagy irányítópultra a Power BI szolgáltatásban
Minden eddiginél egyszerűbb naprakésznek lenni a legfontosabb irányítópultokkal és jelentésekkel kapcsolatban. Ön és munkatársai feliratkozhatnak az Önöknek legfontosabb jelentésoldalakra és irányítópultokra, a Power BI pedig pillanatképeket küld e-mailben a postafiókjaikba. Megadhatja a Power BI-nak, hogy milyen gyakran szeretne ilyen e-mailt kapni: naponta egyszer, vagy csak hetente. 

Az e-mail és a pillanatkép a Power BI beállításaiban szereplő nyelvet fogja használni (lásd [A Power BI által támogatott nyelvek és országok/régiók](supported-languages-countries-regions.md) témakört). Ha nincs megadva nyelv, a Power BI a böngésző területi beállításait használja. A nyelvi beállításokat megtekintheti vagy módosíthatja a fogaskerék ikon ![fogaskerék ikon](media/service-report-subscribe/power-bi-settings-icon.png) > **Beállítások > Általános > Nyelv** lehetőség választásával. 

![Nyelv legördülő lista](media/service-report-subscribe/power-bi-language.png)

Feliratkozások csak a Power BI szolgáltatásban hozhatók létre. Amikor e-mail érkezik, abban szerepelni fog egy „ugrás a jelentésre vagy irányítópultra” hivatkozás. Olyan mobileszközökön, melyeken telepítve van a Power BI alkalmazás, a hivatkozás választásakor az alkalmazás indul el (szemben az alapértelmezett művelettel, a jelentés vagy az irányítópult a Power BI webhelyén való megnyitásával).


## <a name="requirements"></a>Követelmények
- A feliratkozás **létrehozása** Power BI Pro-funkció, amelyhez rendelkeznie kell a tartalom (irányítópult vagy jelentés) szerkesztéséhez szükséges engedélyekkel. 
- Mivel az előfizetési e-mailek csak egy mögöttes adathalmaz frissítésekor lesznek elküldve, az előfizetések nem működnek a nem frissített adathalmazokon.

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>Feliratkozás irányítópultra vagy jelentésoldalra
Függetlenül attól, hogy irányítópultra vagy jelentésre iratkozik fel, a folyamat nagyon hasonló. Ugyanazzal a gombbal iratkozhat fel (vagy írathat fel másokat) a Power BI szolgáltatás irányítópultjaira és jelentéseire.
 
![Előfizetés ikon kiválasztása](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Nyissa meg az irányítópultot vagy a jelentést.
2. A felső menüsávon válassza a **Feliratkozás** lehetőséget vagy a boríték ikont ![Feliratkozás ikon](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Feliratkozás ikon](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. A feliratkozást a sárga csúszkával kapcsolhatja be és ki.  A csúszkával történő kikapcsolás nem törli a feliratkozást. A feliratkozás törléséhez válassza a kuka ikont.

4. Töltse ki az e-mail részleteit. Az e-mailt a szolgáltatás előre kitölti, de másokat is hozzáadhat a feliratkozáshoz. Csak ugyanahhoz a tartományhoz tartozó e-mail-címeket lehet hozzáadni (további részletekért lásd az alábbi **Megfontolások és hibaelhárítás** szakaszt). Ha a jelentést és az irányítópultot [prémium szintű kapacitásban](service-premium.md) üzemelteti, akkor egyéni e-mail-címeket és csoportos aliasokat használó más személyeket is felírathat. Ha a jelentést vagy irányítópultot nem prémium szintű kapacitásban üzemelteti, akkor is felírathat másokat az egyéni e-mail-címeikkel, de ebben az esetben nekik is rendelkezniük kell Power BI Pro-licencekkel.

    Az alábbi képernyőfelvételeken figyelje meg, hogy amikor feliratkozik egy jelentésre, akkor valójában egy jelentés*oldalra* iratkozik fel.  Ha egy jelentésben több oldalra is fel szeretne iratkozni, válassza a **Másik előfizetés hozzáadása** lehetőséget, és válasszon ki egy másik oldalt. 
      
   ![Feliratkozás ablak](media/service-report-subscribe/power-bi-emails-new.png)  

5. A feliratkozás mentéséhez válassza a **Mentés és bezárás** lehetőséget. Azok, akik feliratkoztak, minden alkalommal e-mailt és pillanatképet kapnak az irányítópultról vagy a jelentésoldalról, amikor bármelyik, annak alapjául szolgáló adathalmaz módosul. Ha az irányítópult vagy a jelentés egy nap alatt egynél többször frissül, akkor az e-mailt csak az első frissítés után kapja meg.  
   
   ![az irányítópult e-mailes pillanatképe](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 
   
   > [!TIP]
   > Szeretné most azonnal látni az e-mailt? Váltson ki e-mail küldést az irányítópulthoz társított vagy a jelentéshez társított adathalmazok egyikének frissítésével. (Ha nincs az adathalmazra vonatkozó szerkesztési engedélye, akkor meg kell kérnie valakit, aki rendelkezik ilyen engedéllyel, hogy tegye meg Ön helyett.) A használt adathalmazok megismeréséhez válassza a **Kapcsolódók megtekintése** ikont ![Kapcsolódók megtekintése ikon](media/service-report-subscribe/power-bi-view-related.png), amely megnyitja a **Kapcsolódó tartalom** panelt, majd válassza a frissítés ikont ![frissítés ikon](media/service-report-subscribe/power-bi-refresh.png). 
   > 
   > 
   
   ![Kapcsolódó adatkészletek](media/service-report-subscribe/power-bi-view-related-screen.png)

## <a name="how-the-email-schedule-is-determined"></a>Az e-mailek ütemezésének meghatározása
Az alábbi táblázat azt ismerteti, hogy milyen gyakran kap e-mail-értesítést. Ez függ az irányítópult vagy jelentés alapjául szolgáló adathalmaz kapcsolódási módjától (DirectQuery, élő kapcsolat, Power BI-ba importált fájl, vagy Excel-fájl a OneDrive-on vagy a SharePoint Online-ban), valamint az elérhető és kijelölt feliratkozási lehetőségektől (naponta, hetente vagy nincs).

|  | **DirectQuery** | **Élő kapcsolat** | **Ütemezett frissítés (importálás)** | **Excel-fájl a OneDrive-on vagy a SharePoint Online-ban** |
| --- | --- | --- | --- | --- |
| **Milyen gyakran frissül a jelentés vagy az irányítópult?** |15 percenként |A Power BI 15 percenként ellenőrzi, hogy módosult-e az adathalmaz, és ha igen, akkor frissíti a jelentést. |A felhasználó a nincs, a naponta és a hetente lehetőség közül választhat. Naponta legfeljebb 8 alkalom lehet. A heti ütemezést a felhasználó hozza létre és állítja be legalább hetente egyszeri, vagy akár napi frissítésre. |Óránként egyszer |
| **Milyen mértékben befolyásolhatja a felhasználó az feliratkozásokhoz tartozó e-mailek ütemezését?** |Napi vagy heti ütemezés választható |Nem módosítható: a felhasználó a jelentés frissülésekor e-mailt kap, de naponta legfeljebb egyszer. |Ha a frissítés napi ütemezésű, akkor napi vagy heti ütemezés választható.  Ha a frissítés heti ütemezésű, akkor csak heti ütemezés válaszható. |Nem módosítható: a felhasználó az adathalmaz frissítésekor kap e-mailt, de naponta legfeljebb egyszer. |

## <a name="manage-your-subscriptions"></a>Feliratkozások kezelése
Csak az a személy kezelheti a feliratkozást, aki létrehozta.  A feliratkozások kezelésére szolgáló képernyő két úton érhető el.  Az első **Az összes előfizetés kezelése** lehetőség választása a **Feliratkozás e-mailekre** párbeszédpanelen (lásd a fenti 4. lépés alatti képernyőképet). A második a Power BI a felső menüsávon lévő fogaskerék ikonjának ![fogaskerék ikon](media/service-report-subscribe/power-bi-settings-icon.png), majd a **Beállítások** lehetőség választása.

![Beállítások kiválasztása](media/service-report-subscribe/power-bi-subscribe-settings.png)

Hogy mely feliratkozások jelennek meg, az attól függ, hogy éppen melyik munkaterület aktív.  Ha az összes munkaterülethez tartozó feliratkozásokat szeretné megjeleníteni, győződjön meg arról, hogy a **Saját munkaterület** aktív. A munkaterületek működéséről a [Munkaterületek a Power BI-ban](service-create-distribute-apps.md) című cikkben olvashat bővebben.

![összes előfizetés megtekintése a Saját munkaterületen](media/service-report-subscribe/power-bi-subscriptions.png)

A feliratkozás megszűnik, ha lejár a Pro-licence, ha az irányítópultot vagy jelentést törli a tulajdonosa, vagy ha törlik a feliratkozás létrehozásához használt felhasználói fiókot.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
* Az irányítópultok e-mail-feliratkozásai esetén, ha bármely csempe sorszintű biztonsággal (RLS) rendelkezik, ezek a csempék nem jelennek meg.  A jelentésekhez kapcsolódó e-mail-feliratkozások esetén, ha az adatkészlet sorszintű biztonságot használ, nem hozható létre feliratkozás.
* A jelentésoldalakra való feliratkozás a jelentésoldal nevéhez kapcsolódik. Ha feliratkozik egy jelentésoldalra, majd átnevezi azt, akkor újra létre kell hoznia a feliratkozást
* Előfordulhat, hogy a szervezet konfigurált néhány beállítást az Azure Active Directory-ban, amelyek korlátozhatják a Power BI-ban az e-mail-előfizetések használatát.  Ebbe a teljesség igénye nélkül beletartoznak az erőforrások elérésekor a többtényezős hitelesítés és az IP-címtartomány korlátozásai.
* Jelenleg más felhasználók regisztrálásánál a jelentések/irányítópultok e-mailes megosztása nincs támogatva az élő kapcsolattal rendelkező adatkészleteket használatával.
* Az élő kapcsolattal rendelkező adathalmazokra vonatkozó e-mailekre való feliratkozáskor csak az adatok változása esetén kap értesítést. Tehát ha frissítés történik, de az adatok nem változnak, akkor a Power BI nem küld e-mailt.
* Az e-mailekre való feliratkozások az [egyéni vizualizációk](power-bi-custom-visuals.md) többségét nem támogatják.  Az egyetlen kivétel a [minősített](power-bi-custom-visuals-certified.md) egyéni vizualizációk esete.  
* Az e-mailekre való feliratkozások jelenleg nem támogatják az R-alapú egyéni vizualizációkat.  
* Ha bármely irányítópult-csempe sorszintű biztonsággal (RLS) rendelkezik, ezek a csempék nem jelennek meg.
* Nem írathat fel más felhasználókat olyan jelentésekre, amelyek sorszintű biztonsággal rendelkeznek.
* Az e-mail-értesítések a jelentés szűrőinek és szeletelőinek alapértelmezett állapotait alkalmazva lesznek elküldve. Az alapértelmezéseknek a feliratkozás után végzett módosításai nem jelennek meg az e-mailben.    
* A feliratkozást egyelőre nem támogatják a Power BI Desktop élő szolgáltatáskapcsolati funkciójával létrehozott jelentésoldalak.    
* Kifejezetten az irányítópultokra való feliratkozások esetében bizonyos csempetípusok még nem támogatottak.  Ilyenek többek között a streamelési csempék, a videócsempék és az egyéni webes tartalomcsempék.     
* Ha a bérlőn kívüli munkatársával oszt meg egy irányítópultot, akkor ezen munkatársa számára nem fog tudni feliratkozást is létrehozni. Ha tehát Ön aaron@xyz.com, akkor megoszthat irányítópultot a(z) anyone@ABC.com címmel, de nem hozhat létre feliratkozást anyone@ABC.com részére, és ő sem iratkozhat fel megosztott tartalomra.      
* A különösen nagy méretű képeket tartalmazó irányítópultokra vagy jelentésekre való feliratkozás meghiúsulhat az e-mailek méretkorlátozásai miatt.    
* A Power BI automatikusan felfüggeszti a több mint 2 hónapja nem látogatott irányítópultokhoz vagy jelentésekhez társított adathalmazok frissítését.  Ha azonban feliratkozik egy irányítópultra vagy jelentésre, az nem lesz felfüggesztve akkor sem, ha nem látogatják.    
* Ha nem kapja meg az e-mail-értesítéseket, akkor ellenőrizze, hogy tud-e e-maileket fogadni az egyszerű felhasználónevével (UPN). [A Power BI csapata dolgozik ennek a követelménynek az enyhítésén](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163); figyelje az értesítéseket. 
* Ha az irányítópultja vagy jelentése prémium szintű kapacitásban van, akkor használhat csoportos e-mail-aliasokat a feliratkozásokhoz, és nem kell a munkatársai számára e-mail-címenként elvégezni azt. Az aliasok a jelenlegi Active Directoryn alapulnak. 

## <a name="next-steps"></a>Következő lépések
* További kérdései vannak? [Kérdezze a Power BI-közösséget](http://community.powerbi.com/)    
* [Olvassa el a blogbejegyzést](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

