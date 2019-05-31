---
title: Saját maga és mások feliratkozás jelentésekre és irányítópultokra – Power bi-ban
description: Ismerje meg, hogyan lehet előfizetni saját maga és mások Power BI-jelentésoldal, irányítópult vagy többoldalas jelentés pillanatképet.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: a344e3cdd93fbd237387b61fb4735b41f22625e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65991131"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>Feliratkozás és mások feliratkoztatása jelentésekre és irányítópultokra a Power BI szolgáltatásban

Előfizethet a saját maga és a munkatársai a jelentésoldalak, irányítópultok és többoldalas jelentéseket, amelyek az Önnek leginkább fontos. A Power BI e-mailek egy pillanatképet a Beérkezett üzenetek mappájába. Megadhatja a Power BI-nak, hogy milyen gyakran szeretne ilyen e-mailt kapni: naponta, hetente vagy naponta egyszer, az adatok első frissítése után.  Ha úgy dönt, napi vagy heti, kiválaszthatja az idő szeretné futtatni-előfizetéssel rendelkezik.  Egy napra legfeljebb 24 különböző feliratkozást állíthat be az összes jelentésoldalhoz és irányítópulthoz.

![az irányítópult e-mailes pillanatképe](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

Feliratkozásokat csak a Power BI szolgáltatásban hozhat létre. E-mailt kap a jelentésoldal vagy irányítópult pillanatképével és a jelentést vagy irányítópultot megnyitó hivatkozással. Olyan mobileszközökön, melyeken telepítve van a Power BI alkalmazás, a hivatkozás választásakor a Power BI alkalmazás indul el a jelentésnek vagy az irányítópultnak a Power BI webhelyén való megnyitása helyett.

## <a name="requirements"></a>Követelmények

- Az előfizetések **létrehozása** a Power BI Pro egyik funkciója.
- A tartalomra (irányítópultra vagy jelentésre) nem kell szerkesztési jogosultsággal rendelkeznie ahhoz, hogy önmagának hozzon létre feliratkozást, másnak viszont csak akkor tud létrehozni egyet, ha szerkesztési jogosultsággal rendelkezik. 
- 2019 januárjától már nem szükséges adathalmaz-frissítést beállítani egy feliratkozás futtatásához.  Az a beállított ütemezett frissítésektől függetlenül fut.  

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>Feliratkozás egy irányítópult, jelentés lap vagy többoldalas jelentés

Hogy van egy irányítópult, jelentés, vagy a többoldalas jelentés, a folyamat előfizetés hasonlít. Ugyanazzal a gombbal iratkozhat fel a Power BI szolgáltatás irányítópultjaira és jelentéseire.

Többoldalas jelentések előfizetés eltérő. Lásd: [többoldalas jelentésekhez a Power BI szolgáltatásban a saját maga és mások előfizetés](paginated-reports-subscriptions.md) részleteiről.
 
![Előfizetés ikon kiválasztása](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Nyissa meg az irányítópultot vagy a jelentést.
2. A felső menüsávon válassza a **Feliratkozás** lehetőséget vagy a boríték ikont ![Feliratkozás ikon](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Feliratkozás ikon](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. A feliratkozást a sárga csúszkával kapcsolhatja be és ki.  A csúszkával történő **kikapcsolás** nem törli a feliratkozást. A feliratkozás törléséhez válassza a kuka ikont.

4. E-mail-címe már szerepel a **Feliratkozás** mezőben. A feliratkozáshoz is megadhat egy további e-mail-címet, de csak azonos tartományban. Ha a jelentést és az irányítópultot [prémium szintű kapacitásban](service-premium-what-is.md) üzemelteti, akkor más egyéni e-mail-címeket és csoportos aliasokat is felírathat. Ha a jelentést és az irányítópultot nem prémium szintű kapacitásban üzemelteti, akkor is feliratkoztathat másokat, de nekik is Power BI Pro-licenccel kell rendelkezniük. További részleteket az alábbi, [Megfontolandó szempontok és hibaelhárítás](#considerations-and-troubleshooting) című részben olvashat. 

5. Töltse ki az e-mail **Tárgy7** és **Üzenet** adatait. 

5. Válasszon **Gyakoriságot** feliratkozásához: **Napi**, **Heti**, vagy **Adatfrissítések utáni (Napi)** .  Ha az e-mailt, amelyre feliratkozott, csak bizonyos napokon szeretné megkapni, válassza a **Heti** értéket, majd jelölje ki a napokat.  Ha például az e-mailt csak hétköznapokon szeretné megkapni, válassza a **Heti** gyakoriságot, majd távolítsa el a jelölést a **szombat** és a **vasárnap** jelölőnégyzetéből.  

6. Ha **Napi** vagy **Heti** gyakoriságot választ, akkor **Ütemezett időpontot** is megadhat a feliratkozáshoz.  Futtathatja egész órakor, vagy 15, 30, 45 perccel az után.  Választhat délelőtti (AM) vagy délutáni (PM) időpontot. Az időzónát is megadhatja.

7. A feliratkozás kezdő dátuma alapértelmezés szerint az a nap, amelyen létrehozta. Lehetősége van a záró dátum beállítására. Ha nem állít be záró dátumot, az automatikusan az egy évvel a kezdő dátum utáni napra lesz beállítva. Ezt a feliratkozás lejárta előtt bármikor módosíthatja bármely jövőbeli dátumra (a 9999-es évig). Amikor egy feliratkozás záró dátuma elérkezik, a küldés leáll, amíg újra nem engedélyezi. Az ütemezett záró dátum előtt értesítés(eke)t kap, amelyek rákérdeznek a kiterjesztésére.    

    Figyelje meg az alábbi képernyőfelvételen, hogy amikor feliratkozik egy jelentésre, akkor valójában egy jelentés*oldalra* iratkozik fel.  Ha egy jelentésben több oldalra is fel szeretne iratkozni, válassza a **Másik előfizetés hozzáadása** lehetőséget, és válasszon ki egy másik oldalt. 
      
   ![Feliratkozás panel](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. Válassza a **Mentés és bezárás** lehetőséget. A feliratkozott személyek a választott gyakorisággal és időpontban e-mailt kapnak, és az irányítópult vagy jelentésoldal pillanatképét. Összesen legfeljebb 24 feliratkozást hozhat létre egy jelentéshez vagy irányítópulthoz, és mindegyikhez egyedi címzetteket, időpontokat és gyakoriságokat adhat meg.  Minden olyan, irányítópultra vagy jelentésre való feliratkozás, amelynek gyakorisága **Adatfrissítések utáni**, csak az első ütemezett frissítés után küld e-mailt.   
      
   > [!TIP]
   > Szeretné azonnal elküldeni az előfizetésből az e-mailt, vagy igény szerint küldeni azt bármely időpontban? Válassza ki a **Futtatás most** lehetőséget az előfizetésekhez a küldeni kívánt irányítópulthoz vagy jelentéshez. Megjelenik egy értesítés arról, hogy az e-mail úton van mindenkihez az adott előfizetésben.  Előfordulhat, hogy ehhez olyan gyakran tetszés szerint. Ez nem számít bele az jelentésenkénti vagy irányítópultonkénti napi 24 ütemezett előfizetés-futtatási korlátba. Ne indítsa el az alapul szolgáló adatkészlet adatok frissítését. 
   > 
   > 
   
## <a name="email-languages"></a>E-mail-nyelvek

Az e-mail és a pillanatkép a Power BI beállításaiban szereplő nyelvet használja (lásd [A Power BI által támogatott nyelvek és országok/régiók](supported-languages-countries-regions.md) témakört). Ha nincs megadva nyelv, a Power BI a böngésző területi beállításait használja. A nyelvi beállításokat megtekintheti vagy módosíthatja a fogaskerék ikon ![fogaskerék ikon](media/service-report-subscribe/power-bi-settings-icon.png) > **Beállítások > Általános > Nyelv** lehetőség választásával. 

![Nyelv legördülő lista](media/service-report-subscribe/power-bi-language.png)

## <a name="manage-your-subscriptions"></a>Feliratkozások kezelése
Csak az a személy kezelheti a feliratkozást, aki létrehozta.  A feliratkozások kezelésére szolgáló képernyő két úton érhető el.  Az első **Az összes előfizetés kezelése** lehetőség választása a **Feliratkozás e-mailekre** párbeszédpanelen (lásd a fenti 4. lépés alatti képernyőképet). A második a Power BI a felső menüsávon lévő fogaskerék ikonjának ![fogaskerék ikon](media/service-report-subscribe/power-bi-settings-icon.png), majd a **Beállítások** lehetőség választása.

![Beállítások kiválasztása](media/service-report-subscribe/power-bi-subscribe-settings.png)

Hogy mely feliratkozások jelennek meg, az attól függ, hogy éppen melyik munkaterület aktív.  Ha az összes munkaterülethez tartozó feliratkozásokat szeretné megjeleníteni, győződjön meg arról, hogy a **Saját munkaterület** aktív. A munkaterületek működéséről a [Munkaterületek a Power BI-ban](service-create-workspaces.md) című cikkben olvashat bővebben.

![összes előfizetés megtekintése a Saját munkaterületen](media/service-report-subscribe/power-bi-subscriptions.png)

A feliratkozás megszűnik, ha lejár a Pro-licence, ha az irányítópultot vagy jelentést törli a tulajdonosa, vagy ha törlik a feliratkozás létrehozásához használt felhasználói fiókot.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

* Előfordulhat, hogy a felhasználóknak küldött előfizetési e-mailekben a több mint 25 kitűzött csempével vagy négy kitűzött élő jelentésoldallal rendelkező irányítópultok nem jelennek meg teljes egészében.  Az irányítópultokon keresztül ezek rögzíthető csempék számának előfizetések nincsenek letiltva. Azonban azokat a rendszer nem támogatott, ha problémák merülnek fel. Vegye figyelembe, hogy ennek megfelelően módosítja a támogatott tartományon belüli.
* Az e-mail-előfizetések beállításakor vegye figyelembe nincs késleltetés, ha az előfizetés feladat elindul, és az e-mail küldése a pontos idő.  A kettő közötti késleltetés minimalizálása érdekében állítsa be egy másik időpontot, amikor az e-mail előfizetés való futásra van ütemezve, mint az ütemezett Adatfrissítés.
* Az irányítópult e-mailes feliratkozások minden csempénél van a sorszintű biztonság (RLS) a alkalmazni, ha ezek a csempék ne jelenjen meg.  
* A jelentés-előfizetések e-mailt Ha az adatkészlet használja az rls-t, létrehozhat egy előfizetés maga. Másokat nem iratkoztathat fel egy jelentéshez a alkalmazni a sorszintű biztonság (RLS).
* A jelentésoldalakra való feliratkozás a jelentésoldal nevéhez kapcsolódik. Ha feliratkozik egy jelentésoldalra, majd átnevezi azt, akkor újra létre kell hoznia a feliratkozást.
* Előfordulhat, hogy a szervezet konfigurált néhány beállítást az Azure Active Directory-ban, amelyek korlátozhatják a Power BI-ban az e-mail-előfizetések használatát.  A korlátozások körébe a teljesség igénye nélkül beletartoznak az erőforrások elérésekor a többtényezős hitelesítés és az IP-címtartomány korlátozásai.
* Jelenleg más felhasználók regisztrálásánál a jelentések/irányítópultok e-mailes megosztása nincs támogatva az élő kapcsolattal rendelkező adatkészleteket használatával.
* Az e-mailekre való feliratkozások az [egyéni vizualizációk](power-bi-custom-visuals.md) többségét nem támogatják.  Az egyetlen kivétel a [minősített](power-bi-custom-visuals-certified.md) egyéni vizualizációk esete.  
* Az e-mailekre való feliratkozások jelenleg nem támogatják az R-alapú egyéni vizualizációkat.  
* Az e-mail-értesítések a jelentés szűrőinek és szeletelőinek alapértelmezett állapotait alkalmazva lesznek elküldve. Az alapértelmezéseknek a feliratkozás után végzett módosításai nem jelennek meg az e-mailben.    
* Kifejezetten az irányítópultokra való feliratkozások esetében bizonyos csempetípusok még nem támogatottak.  Ilyenek többek között a streamelési csempék, a videócsempék és az egyéni webes tartalomcsempék.     
* Ha a bérlőn kívüli munkatársával oszt meg egy irányítópultot, akkor ezen munkatársa számára nem tud feliratkozást is létrehozni. Ha tehát Ön aaron@xyz.com, akkor megoszthat irányítópultot a(z) anyone@ABC.com címmel, de nem hozhat létre feliratkozást anyone@ABC.com részére, és ő sem iratkozhat fel megosztott tartalomra.      
* A Power BI automatikusan felfüggeszti a több mint két hónapja nem látogatott irányítópultokhoz vagy jelentésekhez társított adathalmazok frissítését.  Ha azonban feliratkozik egy irányítópultra vagy jelentésre, az nem szünetel akkor sem, ha nem látogatják.    
* Ha nem kapja meg az e-mail-értesítéseket, akkor ellenőrizze, hogy tud-e e-maileket fogadni az egyszerű felhasználónevével (UPN). [A Power BI csapata dolgozik ennek a követelménynek az enyhítésén](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163); figyelje az értesítéseket. 
* Ha az irányítópultja vagy jelentése prémium szintű kapacitásban van, akkor használhat csoportos e-mail-aliasokat a feliratkozásokhoz, és nem kell a munkatársai számára e-mail-címenként elvégezni azt. Az aliasok a jelenlegi Active Directoryn alapulnak. 

## <a name="next-steps"></a>Következő lépések

- [Feliratkozás saját maga és mások többoldalas jelentést a Power BI szolgáltatásban](paginated-reports-subscriptions.md)
- További kérdései vannak? [Kérdezze a Power BI-közösséget](http://community.powerbi.com/)    
- [Olvassa el a blogbejegyzést](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
