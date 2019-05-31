---
ms.openlocfilehash: ea958349988cade1045e80b073254ab1f29bbe9e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61263841"
---
Az előző témakörökben áttekintettük, hogyan használható a Power BI adatforrásokhoz történő csatlakozásra, és hogyan frissíthetők a Power BI szolgáltatásba feltöltött adatkészletek manuálisan. Ugyanakkor, ha nem szeretne minden adatváltozás alkalmával mindent frissíteni, a Power BI segítségével beállíthat ütemezett frissítést is, amely kapcsolódik az adatforrásokhoz, és automatikusan közzéteszi a változásokat a Power BI szolgáltatásban. Bármilyen helyi adatforrást, többek között Excel-fájlokat, Access-adatbázisokat, SQL-adatbázisokat és sok minden mást is csatlakoztathat így a szolgáltatáshoz.

A helyszíni adatforrások Power BI szolgáltatáshoz történő csatlakoztatását lehetővé tevő rendszer neve **adatátjáró**. Az adatátjáró egy, a felhasználó számítógépén futó kis alkalmazás. Előre összeállított ütemezés alapján kapcsolódik az adatokhoz, összegyűjti a frissítéseket, és elküldi azokat a Power BI szolgáltatásba. A **személyes átjáró** az **adatátjáró** olyan verziója, amelyet nem szükséges a rendszergazdának konfigurálnia.

>[!NOTE]
>A **személyes átjáró** megfelelő működéséhez *arra van szükség*, hogy a Power BI személyes átjárót futtató számítógép be legyen kapcsolva, és csatlakozzon az internethez.
> 

A **személyes átjáró** beállításához először jelentkezzen be a Power BI szolgáltatásba. Válassza ki a **Letöltés** ikont a képernyő jobb felső sarkából, majd válassza az **Data Gateway** menüelemet.

![](media/4-6-install-configure-personal-gateway/4-6_1b.png)

Ekkor a rendszer egy olyan weboldalra lépteti, ahonnan kiválaszthatja a **Power BI Gateway – Personal** lehetőséget, ahogy az alább látható.

![](media/4-6-install-configure-personal-gateway/4-6_2b.png)

A letöltés befejeződésekor indítsa el az alkalmazást, és hajtsa végre a telepítő varázslóban megjelenő lépéseket.

![](media/4-6-install-configure-personal-gateway/4-6_3a.png)

Ezután a rendszer kérni fogja, hogy az átjáró beállításához indítsa el a beállítás varázslót.

![](media/4-6-install-configure-personal-gateway/4-6_3b.png)

Először be kell majd jelentkeznie saját Power BI-fiókjába, majd számítógépe Windows-fiókjába, mivel az átjáró szolgáltatás az Ön fiókja alatt fog futni.

![](media/4-6-install-configure-personal-gateway/4-6_3c.png)

Térjen vissza a Power BI szolgáltatásba. Kattintson a három pont menüelemre a frissíteni kívánt adatkészlet mellett, majd kattintson a **Frissítés ütemezése** lehetőségre. Ekkor megnyílik a **Beállítások frissítése** lap. A Power BI észleli, hogy telepített egy **személyes átjárót**, és jelzi annak állapotát.

Válassza ki a **Hitelesítő adatok szerkesztése** lehetőséget a megfelelő adatforrások mellett, és állítsa be a hitelesítést.

![](media/4-6-install-configure-personal-gateway/4-6_6.png)

Végül az automatikus frissítések aktiválásához adja meg a beállításokat a **Frissítés ütemezése** alatt, és állítsa be, hogy azokra mikor és milyen gyakorisággal kerüljön sor.

![](media/4-6-install-configure-personal-gateway/4-6_7.png)

Ezzel készen is van. Az ütemezett időpontokban a Power BI a megadott hitelesítési adatokat használva kapcsolódik a **személyes átjárót** futtató számítógéphez, és az ütemezésnek megfelelően frissíti a jelentéseket és az adatkészleteket. Amikor legközelebb a Power BI felületére lép, az iránytópultok, jelentések és adatkészletek a legutóbbi ütemezett frissítésnek megfelelő adatokat fogják tükrözni.

## <a name="next-steps"></a>Következő lépések
**Gratulálunk!** Ön teljesítette a Power BI **Interaktív tanulás** oktatóanyagának **Adatok feltárása** című fejezetét. A Power BI szolgáltatás számtalan izgalmas módszert kínál az adatok feltárására, az összefüggések megosztására és a vizualizációs elemek alakítására. A módszerek mindegyike elérhető böngészőből, egy olyan szolgáltatásból amely bárhonnan elérhető.

A Power BI egyik hatékony és jól ismert partnere az **Excel**. A Power BI-t és az Excel-t úgy tervezték, hogy jól működjenek együtt. A munkafüzetek egyszerűen beemelhetők és gond nélkül használhatók a Power BI-ban.

![](media/4-6-install-configure-personal-gateway/5-1_1.png)

Mennyire egyszerűen? **A Power BI és az Excel** című következő szakasz pontosan erről szól.

Találkozunk a következő szakaszban!

