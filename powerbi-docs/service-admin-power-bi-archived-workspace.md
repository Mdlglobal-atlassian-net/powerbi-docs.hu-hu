---
title: A Power BI archivált munkaterülete
description: A Power BI archivált munkaterülete az Office 365-bérlő kezelése után
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 66bf203cad577df0c985fbd73bcab3c6d79f6a95
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873570"
---
# <a name="power-bi-archived-workspace"></a>A Power BI archivált munkaterülete

> [!IMPORTANT]
> A Power BI már nem támogatja az archivált munkaterület funkciót, amelyet 2019. végén eltávolítunk. Ha archivált munkaterületet használ, azonnal újra létre kell hoznia a megőrizni kívánt tartalmakat az aktuális bérlő egy új munkaterületén. Az archivált munkaterülethez való hozzáférése nem megbízható. A Power BI már nem támogatja az ehhez kapcsolódó funkciót, az [Azure AD-bérlők külső átvételét](service-admin-faq.md#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users).

A Power BI-ra bárki perceken belül regisztrálhat, és megkezdheti a szolgáltatás használatát.  Később a szervezet IT-részlege dönthet úgy, hogy átveszi a Power BI a szervezet felhasználói számára történő kezelését.  Ha ez az átvétel megtörténik a szervezetben, élvezheti a felhasználók és engedélyek központi kezelésének előnyeit. Esetleg kihasználhatja a leegyszerűsített bejelentkezés lehetőségét is, mellyel ugyanazzal a felhasználónévvel és jelszóval jelentkezhet be, mint a szervezet más szolgáltatásaiba.

Azok a tartalmak, amelyeket még azelőtt hozott létre, hogy az informatikai részleg megkezdte volna a Power BI kezelését, a Power BI archivált munkaterületére kerülnek, amely a [Power BI](https://app.powerbi.com) navigációs paneljéről érhető el. Az új Power BI-tartalom létrehozását a Saját munkaterületen kezdheti meg, melyet a vállalat IT-részlege biztosít és kezel.  Az archivált munkaterület továbbra is megmarad, de az abban tárolt tartalmon végezhető műveletek korlátozottak lesznek.  A korlátozások eltávolításához migrálnia kell a tartalmat az archivált munkaterületről az IT-részleg által kezelt Saját munkaterületre.

## <a name="restrictions-in-your-archived-workspace"></a>Az archivált munkaterület korlátozásai

A Power BI nem töröl tartalmat az archivált munkaterületről. Továbbra is letölthet adatokat, létrehozhat jelentéseket és irányítópultokat, és frissítheti az adatkészleteket. Azok a meglévő felhasználók, akikkel már megosztott tartalmat, továbbra is megtekinthetik azt a saját archivált munkaterületükön. Azonban az archivált munkaterületen található tartalomra néhány korlátozás is vonatkozik:

* **OneDrive Vállalati verzió**: Az archivált munkaterületen található adathalmazok esetében többé nem fog tudni adatokat letölteni vagy frissíteni a OneDrive Vállalati verzióból.  Ha ehhez a forráshoz próbál csatlakozni, figyelmeztetés fog kapni.

* **Irányítópultok megosztása**: Az archivált munkaterületről nem oszthat meg irányítópultokat más felhasználókkal.  Azok a felhasználók, akik már rendelkeznek hozzáféréssel, továbbra is megtekinthetik a megosztott irányítópultokat az archivált munkaterületük elérésével.

* **Csoportok létrehozása**: Az archivált munkaterületen nem hozhat létre csoportokat.

* **Hozzáférés a Power BI-mobilalkalmazásokban**: Bár továbbra is megtekintheti a webes tartalmat az archivált munkaterületen, ez a tartalom többé nem fog megjelenni a Power BI-mobilalkalmazásokban.

## <a name="migrating-content-in-your-archived-workspace"></a>Tartalom migrálása az archivált munkaterületen

A Power BI használatának folytatásához hozzon létre új tartalmat a Saját munkaterületen. Meg kell terveznie az archivált munkaterületen lévő tartalom Saját munkaterületre való migrálását is.  A tartalom migrálásának módja a tartalom típusától függ:

* **Excel- vagy Power BI Desktop-adatkészletek**: Ezeknek az adatkészleteknek a migrálásához váltson az archivált munkaterületről a Saját munkaterületre, és töltse fel újra az Excel- vagy Power BI Desktop-fájlt a **My Data** (Adataim) gombbal.  Ha állított be ütemezett frissítést, ezt a beállítást újra meg kell adnia a Saját munkaterületen található új adathalmazhoz.

* **Egyéb adatkészletek**: Váltson a Saját munkaterületre, és kattintson az **Adatok lekérése** gombra az archivált munkaterületen létrehozott egyéb adatkészletekhez való újrakapcsolódáshoz.  Lehet, hogy újra meg kell adnia a biztonsági vagy kapcsolódási adatokat.

* **Jelentések**: Az Excel- vagy Power BI Desktop-fájlokban tárolt jelentéseket a rendszer automatikusan újra létrehozza, amint újra feltölti a hozzájuk tartozó Excel- vagy Power BI Desktop-fájlokat. A tartalomcsomag részeként telepített jelentéseket a rendszer szintén újra létrehozza, amint újból csatlakoztatja a tartalomcsomagot. Ha a Power BI szolgáltatásban hozta létre a jelentéseit, akkor ezeket újra létre kell hoznia a Saját munkaterületen.

* **Irányítópultok**: A tartalomcsomagok részeként telepített irányítópultok automatikusan újra létrejönnek, amikor újrakapcsolódik a tartalomcsomaghoz a Saját munkaterületen. Ha a Power BI szolgáltatásban hozta létre az irányítópultjait, akkor ezeket újra létre kell hoznia a Saját munkaterületen.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

