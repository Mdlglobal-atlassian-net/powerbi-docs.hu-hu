---
title: A Power BI bemutatása
description: A Power BI és a különféle komponensek áttekintése – Power BI Desktop, Power BI szolgáltatás, Power BI Mobile, Jelentéskészítő kiszolgáló, Power BI Embedded.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: b1efe45d52b5a7a18a86407b41e8af287d3c8260
ms.sourcegitcommit: b717118c44499c8fd8f57534a275f2f78aacc0f1
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/09/2019
ms.locfileid: "55971648"
---
# <a name="what-is-power-bi"></a>A Power BI bemutatása
A **Power BI** olyan szoftverszolgáltatások, alkalmazások és összekötők gyűjteménye, amellyel az egymástól független adatforrásokat egymással együttműködő, vizuálisan megragadó, interaktív elemzésekké alakítja. Az adatok lehetnek akár egy Excel-táblában, vagy felhőalapú és helyszíni hibrid adattárházak gyűjteményében is. A **Power BI-jal** egyszerűen csatlakozhat az adatforrásokhoz, vizuálisan megjelenítheti és feltárhatja a fontos részeket, és ezt bárkivel meg is oszthatja.

![a Power BI bemeneti forrásait bemutató diagram](media/power-bi-overview/power-bi-input-new.png)

A **Power BI** használható egyszerű és gyors módon – készíthet például gyors elemzéseket Excel-táblák vagy helyi adatbázis alapján. De a **Power BI** emellett egy robusztus, nagyvállalati szintű megoldás is, mely kiterjedt lehetőségeket kínál modellezéshez, valós idejű elemzésekhez, illetve egyéni fejlesztésekhez. Ezért ez az Ön személyes jelentéskészítő és vizualizációs eszközének is tekinthető. Emellett elemzési és döntéshozatali alapként is szolgálhat a csoportprojektek, a részlegek és a teljes vállalat számára is.

## <a name="the-parts-of-power-bi"></a>A Power BI részei
A Power BI a következő részekből áll: a **Power BI Desktop** nevű asztali Windows-alkalmazásból, a **Power BI szolgáltatás** nevű szolgáltatott szoftverből (úgynevezett *SaaS* szolgáltatásból), valamint iOS- és Android-eszközökön elérhető Power BI **mobilalkalmazásokból**.

![Power BI Desktop, szolgáltatás, mobil](media/power-bi-overview/power-bi-blocks.png)

Ez a három elem – a **Power BI Desktop**, a **szolgáltatás** és a **mobilalkalmazás** – úgy lett tervezve, hogy a szerepkörük szerinti leghatékonyabb módon segítse a felhasználókat az üzleti elemzések létrehozásában, megosztásában és felhasználásában.

A **Power BI jelentéskészítő kiszolgáló** a negyedik elem. Ezzel a Power BI Desktopban létrehozott Power BI-jelentéseket lehet közzétenni helyszíni jelentéskészítő kiszolgálón. További információ: [Power BI jelentéskészítő kiszolgáló](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>A Power BI illeszkedése az Ön szerepköréhez
A Power BI szolgáltatás használata függhet attól, hogy Ön milyen szerepkört tölt be egy projektben vagy egy csapatban. A Power BI-t mindenki saját szerepkörének megfelelően használja.

Előfordulhat például, hogy Ön elsősorban a **Power BI szolgáltatást** használja. A számításokat végző és üzleti jelentéseket létrehozó munkatársa azonban nagy mértékben támaszkodik a **Power BI Desktop** alkalmazásra, és a jelentéseket közzéteszi a Power BI szolgáltatásban, ahol Ön aztán megtekintheti őket. Mindeközben elképzelhető, hogy egy másik, értékesítési osztályon dolgozó munkatárs a Power BI mobilalkalmazást használja az értékesítési kvótái előrehaladásának figyeléséhez, illetve az új értékesítések részleteinek vizsgálatához.

Fejlesztőként használhatja a Power BI API-jait arra, hogy az adatokat adatkészletekbe töltse be, vagy hogy irányítópultokat és jelentéseket ágyazzon be egyéni alkalmazásaiba. Javaslata van új vizualizációra? Hozza létre, és ossza meg másokkal is.  

A **Power BI** egyes elemeit használhatja emellett felváltva is attól függően, hogy épp milyen céljai vannak, illetve milyen szerepkörben dolgozik egy adott projektben vagy feladaton.

Használhatja például a **Power BI Desktopot** arra, hogy jelentéseket hozzon létre saját csapata számára az ügyfélelérési statisztikákról. Az is lehet, hogy egy valós idejű irányítópulton követi a leltár állapotát és a gyártási folyamatot a szolgáltatásban. A Power BI használatát az határozza meg, hogy e Power BI melyik funkciója vagy szolgáltatása a legmegfelelőbb az adott helyzetben. A Power BI minden elemét elérheti, ami nagy mértékű rugalmasságot jelent.

A szerepköréhez kapcsolódó dokumentumok elemzése:
- Power BI [***tervezők***](desktop-what-is-desktop.md) számára
- Power BI [***felhasználók***](consumer/end-user-consumer.md) számára
- Power BI [***fejlesztők***](developer/what-can-you-do.md) számára
- Power BI [***rendszergazdák***](service-admin-administering-power-bi-in-your-organization.md) számára

## <a name="the-flow-of-work-in-power-bi"></a>A Power BI-ban való munka folyamata
A Power BI-ban a leggyakoribb munkafolyamat első lépése az adatforrásokhoz való csatlakozás, majd pedig jelentések létrehozása a **Power BI Desktopban**. A jelentést ezt követően közzéteheti a **Power BI Desktopból** a **Power BI szolgáltatásba** és megoszthatja azt, így a végfelhasználók megtekinthetik azt a **szolgáltatásban** és a **mobileszközökön** is.
Ez egy nagyon gyakori munkafolyamat, és jól látszik benne, hogy hogyan egészíti ki egymást a Power BI három összetevője.

Az alábbiakban [a Power BI Desktop és a Power BI szolgáltatás részletes összehasonlítását](service-service-vs-desktop.md) találja.

De mi történik, ha Ön nem áll még készen arra, hogy a felhőbe települjön át, és jelentéseit egy vállalati tűzfal mögött szeretné tartani?  Olvasson tovább.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Helyszíni jelentéskészítés a Power BI jelentéskészítő kiszolgálóval
A Power BI mobil és többoldalas jelentések létrehozása, telepítése és felügyelete a helyszínen a Power BI jelentéskészítő kiszolgáló által biztosított, használatra kész eszközökkel.

![a helyszíni diagramja](media/power-bi-overview/power-bi-report-server2.png)

A Power BI jelentéskészítő kiszolgáló megoldást tűzfal mögött lehet üzembe helyezni, és ezt követően különféle módokon lehet a jelentéseket a megfelelő felhasználókhoz eljuttatni, akik megnézhetik azokat egy webböngészőben, mobileszközön vagy e-mailben is. Mivel a Power BI jelentéskészítő kiszolgálója kompatibilis a felhőalapú Power BI-jal, bármikor dönthet úgy, hogy áttelepül a felhőbe, ha készen áll rá. 

További információ: [Power BI jelentéskészítő kiszolgáló](report-server/get-started.md).

## <a name="next-steps"></a>Következő lépések
[Jelentkezzen be, olvasson be adatokat, és ismerkedjen meg a Power BI szolgáltatás használatának alapjaival](service-the-new-power-bi-experience.md)   
[Oktatóanyag: Első lépések a Power BI szolgáltatással](service-get-started.md)
[Rövid útmutató: Csatlakozás adatokhoz a Power BI Desktopban](desktop-quickstart-connect-to-data.md)