---
title: Licenctípusok Power BI-ügyfelek számára
description: Megismerheti a különböző licenctípusokat, és azt, hogyan állapíthatja meg, hogy melyikkel rendelkezik.
author: mihart
ms.reviewer: lukasz
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/27/2020
ms.author: mihart
LocalizationGroup: consumers
ms.openlocfilehash: 4615bae84ddeb3d3e0b3c471a6b9d6bcf7eda406
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267296"
---
# <a name="types-of-power-bi-licenses"></a>Power BI-licencek típusai

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

*Ügyfélként* a Power BI szolgáltatást használhatja a jelentések és irányítópultok megismeréséhez és ezek alapján az üzleti döntések meghozatalához. Ha már egy ideje használja a Power BI-t, vagy beszélgetett *tervező* munkatársaival, valószínűleg észrevette, hogy van néhány funkció, amely csak akkor működik, ha rendelkezik bizonyos típusú licenccel vagy előfizetéssel. 

Az a cikk a felhasználói licencek és a vállalati előfizetések (ingyenes, Pro, Prémium és Prémium szintű kapacitás) közötti különbségeket, valamint azok együttműködését ismerteti. Azt is megtudja, hogyan derítheti ki, hogy Ön a licencek és előfizetések melyik kombinációt használja.  

![a licencek kapcsolatát bemutató ábra](media/end-user-license/power-bi-venn.png)

Először nézzük meg a két licenckategóriát: a felhasználónkénti és vállalati előfizetéseket. Induljunk ki a mindkettőhöz elérhető alapértelmezett képességekből. Ez után megvizsgáljuk, hogy a Power BI rendszergazdája és a tartalomtulajdonosok hogyan használhatják a szerepköröket és engedélyeket az alapértelmezett licencelési és előfizetési lehetőségek módosításához. 

Még ha a licence lehetővé is teszi, a rendszergazda korlátozhatja például az adatexportálást, a Q&A természetes nyelvi lekérdezések használatát, illetve a webes közzétételt is. Ha pedig egy *jelentéstervező* tartalmat rendel egy [munkaterülethez](end-user-workspaces.md), akkor hozzárendelheti Önt egy munkaterület-szerepkörhöz. A szerepkörök határozzák meg, hogy az adott munkaterületen belül mit tehet és mit nem. A *jelentéstervező* tovább módosíthatja a licenc korlátait az engedélyek beállításaival. Más szóval... bonyolult. Remélhetőleg ez a cikk segít nagyrészt – vagy akár teljes egészében – átlátni a zűrzavart.

## <a name="per-user-licenses"></a>Felhasználónkénti licencek
Az első licenctípus a **felhasználónkénti** licenc. A Power BI-felhasználók ingyenes licenccel vagy Pro-licenccel rendelkeznek. Bizonyos szolgáltatások a Pro-licenccel rendelkező felhasználók számára vannak fenntartva.  

- **A Power BI Pro-licenc (prémium szintű előfizetés nélkül)** lehetővé teszi a felhasználóknak, hogy együttműködjenek más Pro-felhasználókkal a tartalom létrehozásában vagy megosztásában. Csak a Pro-licenccel rendelkező felhasználók tehetnek közzé jelentéseket, fizethetnek elő irányítópultokra és jelentésekre, és működhetnek együtt a munkatársakkal a munkaterületeken. 

    ![pro-felhasználók képe](media/end-user-license/power-bi-pro.jpg)

    A Power BI Pro egy egyéni felhasználói licenc, amellyel a felhasználók beolvashatják és kezelhetik azokat a jelentéseket és irányítópultokat, amelyeket mások közzétettek a Power BI szolgáltatásban. Az ezzel a licenctípussal rendelkező felhasználók megoszthatnak tartalmakat, és együttműködhetnek más Power BI Pro-felhasználókkal. Csak Power BI Pro felhasználók tehetnek közzé és oszthatnak meg tartalmakat más felhasználókkal, vagy használhatják fel a mások által létrehozott tartalmakat. Ez alól kivétel a [Power BI Premium-kapacitásban](#understanding-premium-and-premium-capacity) tárolt tartalom. (Lásd alább: [A Power BI Prémium szintű kapacitás](#understanding-premium-and-premium-capacity).) A Pro-licenceket jellemzően a jelentések *tervezői* és a fejlesztők használják. 


- **Az önálló ingyenes Power BI-licenc (prémium szintű előfizetés nélkül)** – bár sok mindenre használható – azon felhasználóknak való, akik most ismerkednek a Power BI-jal, vagy akik saját maguk számára készítenek tartalmat. Lásd: [Egyéni regisztráció a Power BI szolgáltatásra](../service-self-service-signup-for-power-bi.md).   

    Az ingyenes önálló felhasználói licenc tökéletes megoldás azoknak, akik a Microsoft-mintákat használják a Power BI megismerésére. Az ingyenes önálló licenccel rendelkező felhasználók nem tekinthetik meg a mások által megosztott tartalmakat, és nem oszthatják meg a sajátjaikat más Power BI-felhasználókkal. 

    ![önálló felhasználók képe](media/end-user-license/power-bi-free-license.jpg)

    Az ingyenes önálló licenccel rendelkező összes ügyfél továbbléphet egy [ingyenes Power BI Pro-licenc próbaverzióra](../service-self-service-signup-for-power-bi.md). A próbaverzió a Power BI Pro-felhasználók összes képességét és funkcióját biztosítja.

    ![megvívás Pro próbaverzióra](media/end-user-license/power-bi-pro-trial.png)

- **Ingyenes Power BI-licence prémium szintű előfizetéssel** Ha egy vállalat prémium szintű előfizetéssel rendelkezik, a rendszergazdák és a Pro-felhasználók munkaterületeket rendelhetnek egy *Prémium szintű kapacitáshoz* és engedélyezhetik az ingyenes felhasználóknak az ehhez a munkaterülethez való hozzáférést. A Premium-kapacitású munkaterületek olyan területek, ahol a Pro-felhasználók megoszthatnak tartalmakat és együttműködhetnek az ingyenes felhasználókkal anélkül, hogy az ingyenes felhasználóknak Pro-fiókra lenne szükségük. Az ilyen munkaterületeken az ingyenes felhasználók magasabb szintű engedélyekkel rendelkeznek: sok más mellett közreműködhetnek az adatfeldolgozásban, megoszthatják és exportálhatják azokat, feliratkozhatnak és szűrőket kezelhetnek. 

Eddig világos?  Oké. Vizsgáljuk meg alaposabban a **Prémium szintű kapacitást**.

## <a name="understanding-premium-and-premium-capacity"></a>A Premium és a Premium-kapacitás megismerése
A Premium egy **vállalati** szintű előfizetés. Gondoljon rá úgy, mintha a szervezet funkciók egy további rétegét venné fel a Power BI **felhasználónkénti** licencei mellé. 

Ha egy szervezet Premium-licencet vásárol, a rendszergazda általában azokhoz az alkalmazottakhoz rendel Pro-licenceket, akik tartalmakat fognak létrehozni és megosztani. A rendszergazda pedig ingyenes licenceket rendel hozzá mindenkihez, aki ezt a tartalmat használja. A Pro-felhasználók [alkalmazás-munkaterületeket](end-user-workspaces.md) hozhatnak létre, és tartalmat (irányítópultokat, jelentéseket, alkalmazásokat) adhatnak hozzájuk. Annak érdekében hogy ezeken a munkaterületeken az ingyenes felhasználók is közreműködhessenek, a rendszergazda vagy Pro-felhasználó egy *Prémium szintű kapacitásba* menti a munkaterületeket. 

Ha egy szervezet Premium-licenceket vásárol, kifejezetten a számára fenntartott kapacitást kap a Power BI szolgáltatásban. Más vállalatokkal ez nincs megosztva. Ezeket teljes egészében a Microsoft által felügyelt, dedikált hardverek szolgálják ki. A szervezetek dönthetnek úgy, hogy a dedikált kapacitást széles körben szétterítik, vagy egyes munkaállomásokra koncentrálják. Egy vállalat összes munkaterülete, vagy csak azok egy része is lehet kapacitásban. A Prémium szintű kapacitásban lévő munkaterületeket a gyémánt ikonról ismerheti fel ![gyémánt ikon](media/end-user-license/power-bi-diamond.png).  A Premium-kapacitású munkaterületek olyan területek, ahol a Pro-felhasználók megoszthatnak tartalmakat és együttműködhetnek az ingyenes felhasználókkal anélkül, hogy az ingyenes felhasználóknak Pro-fiókra lenne szükségük. 

A Premium-kapacitásban továbbra is Pro-licencre van szükség a tartalomtervezők számára. A tervezők alkalmazás-munkaterületeket hozhatnak létre, adatforrásokhoz csatlakozhatnak, adatokat modellezhetnek, valamint jelentéseket és irányítópultokat készíthetnek, amelyek közvetlenül vagy csomagolva, alkalmazásként vannak megosztva. A Pro-licenccel nem rendelkező felhasználók továbbra is hozzáférhetnek a Power BI Premiumban található alkalmazás-munkaterülethez, feltéve, hogy a munkaterület Prémium szintű *kapacitásban* van, és a munkaterület tulajdonosa engedélyt ad nekik.

Az alábbi ábrán a bal oldalon azok a Pro-felhasználók jelennek meg, akik tartalmat hoznak létre és osztanak meg alkalmazás-munkaterületeken. 

- Az **A munkaterületet** olyan szervezetben hozták létre, amely nem rendelkezik Prémium előfizetéssel. 

- A **B munkaterületet** olyan szervezetben hozták létre, amely Prémium előfizetéssel rendelkezik, bár ezt az adott munkaterületet nem a Premium-kapacitásba mentették. A munkaterület nem rendelkezik gyémánt ikonnal.

- A **C munkaterületet** egy Prémium előfizetéssel rendelkező szereveztnél hozták létre, és Prémium szintű kapacitásba mentették. A munkaterület rendelkezik gyémánt ikonnal.  

![pro-felhasználók képe](media/end-user-license/power-bi-sharing-scenarios.jpg)

A Power BI Pro-*tervező* a három munkaterületet bármelyikén együttműködhet és tartalmakat oszthat meg más Pro-felhasználókkal. mindaddig, amíg a tervező megosztja a munkaterületet a teljes szervezettel, vagy munkaterületi szerepköröket rendel a Pro-felhasználókhoz. 

A Power BI Pro-felhasználó csak a C munkaterület használatával oszthat meg tartalmakat és dolgozhat együtt ingyenes felhasználókkal. A munkaterületet a Premium-kapacitáshoz kell rendelni ahhoz, hogy az ingyenes felhasználók hozzáférhessenek. A munkaterületen belül a tervező adhat szerepköröket az együttműködésben részt vevő felhasználóknak: *Rendszergazda*, *Tag*, *Közreműködő* vagy *Megtekintő*. A munkaterületen elvégezhető műveleteket a szerepköre határozza meg. A Power BI-*felhasználók* általában *Megtekintő* szerepkört kapnak. További információ: [Munkaterületek Power BI-felhasználóknak](end-user-workspaces.md).

## <a name="find-out-which-license-and-subscription-you-have"></a>A saját licenc és előfizetés megállapítása
A Power BI-licencekre és -előfizetésekre vonatkozó információkat többféleképpen is meg lehet keresni. 

Először határozza meg, hogy milyen **felhasználói** licenccel rendelkezik.

- A Microsoft Office bizonyos verziói Power BI Pro-licencet foglalnak magukban.  Ha szeretné megtudni, hogy az Office Ön által használt verziója tartalmazza-e a Power BI-t, látogasson el [a hivatalos Office-portálra](https://portal.office.com/account), és válassza az **Előfizetések** lehetőséget.

    Az első felhasználó, Pradtanna Office 365 E5 előfizetéssel rendelkezik, amely tartalmazza a Power BI Pro-licencet.

    ![Az Office-portál előfizetések lapja](media/end-user-license/power-bi-license-office.png)

    A második felhasználónak, Zalánnak ingyenes Power BI-licence van. 

    ![Az Office-portál előfizetések lapja](media/end-user-license/power-bi-license-free.png)

Következőként ellenőrizze, hogy fiókja egy Prémium előfizetés része. A fenti felhasználók bármelyike – függetlenül attól, hogy Pro- vagy ingyenes licence van – tartozhat olyan szervezethez, amely Premium-licenccel rendelkezik.  Nézzük meg a második felhasználónkat, Zalánt.  

- A Power BI szolgáltatásban válassza a **Saját munkaterület** lehetőséget, majd a jobb felső sarokban a fogaskerék ikont. Válassza a **Személyes tárhely kezelése** lehetőséget.

    ![A fogaskerék-beállítások menü megjelenítése](media/end-user-license/power-bi-license-personal.png)

    A Pro vagy az ingyenes **felhasználónkénti** licencek 10 GB-os tárhelyet biztosítanak a felhőben, amely Power BI-jelentések vagy Excel-munkafüzetek tárolására használható. Ha többet lát, mint 10 GB, akkor Ön egy Premium-licenccel rendelkező szervezeti fiók tagja.

    ![100 GB-os kapacitást mutató tár kezelése](media/end-user-license/power-bi-free-capacity.png)

    Ne feledje, hogy az Office-portál lapon Zalán felhasználói licence Power BI (ingyenes) típusú volt. Mivel azonban a szervezete Prémium előfizetést vásárolt, Zalán nem korlátozódik 10 GB tárterületre a Power BI szolgáltatásban; 100 GB-ot ér el. A Premium-licenccel rendelkező szervezetekben – amíg a *tervező* a munkaterületet a Premium-kapacitásban helyezi el – Zalán *felhasználóként* képes megtekinteni a megosztott tartalmakat, együttműködni a munkatársakkal, használni az alkalmazásokat, stb. Az engedélyeinek hatályát a Power BI-rendszergazda és a tartalomtervező állítja be. Figyelje meg, hogy egy Pro-felhasználó már megosztott egy munkaterületet Zalánnal. A gyémánt ikon azt jelzi, hogy a munkaterület a Premium-kapacitásban van tárolva. 

   
## <a name="understanding-workspace-roles"></a>A munkaterület szerepköreinek megismerése
Eddig áttekintettük a felhasználónkénti licenceket, a Prémium előfizetéseket, az alkalmazás-munkaterületeket és a Prémium szintű kapacitást. Most vessünk egy pillantást a munkaterület *szerepköreire*.

Mivel ez a cikk a Power BI-*felhasználóknak* szól, vegyük a következő forgatókönyvet:

-  Ön egy *ingyenes* felhasználó egy Power BI Premium-előfizetéssel rendelkező szervezetben. 
- Egy Power BI Pro-felhasználó irányítópultok és jelentések csoportját hozta létre, és *alkalmazásként* közzétette a gyűjteményt a teljes szervezet számára.  
- A *munkaterületeken* belül alkalmazások vannak, a munkaterületet pedig a Premium-kapacitásban tárolják.    
- Az alkalmazás-munkaterületnek egy irányítópultja és két jelentése van.
- A Pro-felhasználó **Megtekintő** szerepkört rendelt a felhasználónkhoz.

### <a name="the-viewer-role"></a>A Megtekintő szerepkör
A Power BI-*tervezők* a szerepkörökkel kezelhetik, hogy mely felhasználók milyen műveleteket végezhetnek a munkaterületeken, így elősegíthetik a csapatok együttműködését. Az egyik ilyen szerepkör a **Megtekintő**. 

Ha a munkaterület Power BI Premium-kapacitásban van, a Megtekintő szerepkörrel rendelkező felhasználók akkor is hozzáférnek a munkaterülethez, ha nem rendelkeznek Power BI Pro-licenccel. Mivel pedig a Megtekintő szerepkör nem fér hozzá a mögöttes adatokhoz, és nem is exportálhatja őket, ez az irányítópultokkal, jelentésekkel és alkalmazásokkal való kommunikáció biztonságos módja.

> [!TIP]
> A további szerepkörök (Rendszergazda, Tag, Közreműködő) megismeréséhez tekintse meg az [új munkaterület létrehozásával](../service-new-workspaces.md) foglalkozó részt.

## <a name="next-steps"></a>Következő lépések
[A Power BI *felhasználójának* számítok?](end-user-consumer.md)    
[További tudnivalók a munkaterületekről](end-user-workspaces.md)    
<!--[View Power BI features by license type](end-user-features.md) -->

