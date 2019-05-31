---
title: Paraméterbeállítások módosítása a Power BI szolgáltatásban
description: A lekérdezési paraméterek a Power BI Desktopban jönnek létre, azonban a Power BI szolgáltatásban tekinthetők át és frissíthetők
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 8db6f106ecc2285cb66ff980bc72fa666456f81a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61226026"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Paraméterbeállítások módosítása a Power BI szolgáltatásban
A lekérdezési paramétereket a jelentéskészítők adják hozzá a Power BI Desktopban. A paraméterekkel a jelentések részeit *paraméterértékektől* függővé tehetik. Egy jelentéskészítő például létrehozhat egy olyan paramétert, amely egyetlen országra vagy régióra korlátozza az adatokat, vagy a mezők elfogadható formátumait határozza meg (például dátumok, idő és szöveg).

![Kezdőlap a Desktop Paraméterek kezelése lehetőségével](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Paraméterek áttekintése és szerkesztése a Power BI szolgáltatásban

Jelentéskészítőként Ön definiálja a paramétereket a Desktopban. Amikor a [jelentést közzéteszi a Power BI szolgáltatásban](desktop-upload-desktop-files.md), a paraméter beállításai és kijelölései a paraméterrel együtt haladnak. Egyes paraméterbeállítások áttekinthetők és szerkeszthetők a Power BI szolgáltatásban – nem azok, amelyek az elérhető adatokat korlátozzák, hanem azok, amelyek az elfogadható értékeket definiálják és határozzák meg.

1. A Power BI szolgáltatásban kattintson a fogaskerék ikonra ![fogaskerék ikon](media/service-parameters/power-bi-cog.png) a **beállítások** megnyitásához.

2. Válassza az **Adatkészletek** lapot, majd jelöljön ki egy adatkészletet a listában. 
    
    ![Beállítások ablak a kijelölt Adatkészletek lappal](media/service-parameters/power-bi-select-dataset2.png)

3. Bontsa ki a **Paraméterek** elemet.  Ha a kijelölt adatkészlethez nem tartozik paraméter, megjelenik egy üzenet, amely a lekérdezésparaméterek ismertetőjére hivatkozik. Azonban ha az adatkészlethez tartoznak paraméterek, azok megjelennek a **Paraméterek** fejléc kibontásakor. 

    ![A Beállítások ablak a kibontott Paraméterek elemmel](media/service-parameters/power-bi-settings.png)

    Tekintse át a paraméter-beállításokat, és szükség esetén végezzen módosításokat. A kiszürkített mezők nem szerkeszthetők. 


## <a name="next-steps"></a>Következő lépések
Ha ad hoc módon szeretne egyszerű paramétereket hozzáadni, [módosíthatja az URL-címet](service-url-filters.md).