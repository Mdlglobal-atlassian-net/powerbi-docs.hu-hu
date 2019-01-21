---
title: A Power BI bemutatása
description: A Power BI és a különféle komponensek áttekintése – Power BI Desktop, Power BI szolgáltatás, Power BI Mobile, Jelentéskészítő kiszolgáló, Power BI Embedded.
author: davidiseminger
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: bc712b892cd35259bc036f41b6e3e16a5388ffad
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54293069"
---
# <a name="what-is-power-bi"></a>A Power BI bemutatása
A **Power BI** olyan szoftverszolgáltatások, alkalmazások és összekötők gyűjteménye, amellyel az egymástól független adatforrásokat egymással együttműködő, vizuálisan megragadó, interaktív elemzésekké alakítja. Akár egyszerű Excel-táblákból, akár felhőalapú és helyszíni hibrid adatraktárak gyűjteményéből állnak az adatai, a **Power BI** segítségével könnyedén összekötheti az adatforrásokat, vizualizálhatja (vagy feltárhatja) a fontos részleteket, és megoszthatja az így kapott információt bárkivel, akivel csak szeretné.

![a Power BI bemeneti forrásait bemutató diagram](media/power-bi-overview/power-bi-input-new.png)

A **Power BI** használható egyszerű és gyors módon – készíthet például gyors elemzéseket Excel-táblák vagy helyi adatbázis alapján. De a **Power BI** emellett egy robusztus, nagyvállalati szintű megoldás is, mely kiterjedt lehetőségeket kínál modellezéshez, valós idejű elemzésekhez, illetve egyéni fejlesztésekhez. Így tehát szolgálhat mind az Ön személyes jelentéskészítő és vizualizációs eszközeként, mind pedig projektek, részlegek vagy teljes nagyvállalatok analitikai és döntéshozatali motorjaként.

## <a name="the-parts-of-power-bi"></a>A Power BI részei
A Power BI a következő részekből áll: a **Power BI Desktop** nevű asztali Windows-alkalmazásból, a **Power BI szolgáltatás** nevű szolgáltatott szoftverből (úgynevezett *SaaS* szolgáltatásból), illetve a Windows-telefonokon és táblagépeken, valamint iOS- és Android-eszközökön elérhető Power BI **alkalmazásokból**.

![Power BI Desktop, szolgáltatás, mobil](media/power-bi-overview/power-bi-blocks.png)

Ez a három elem – az **asztali alkalmazás**, a **szolgáltatás** és a **mobilalkalmazás** – úgy lett tervezve, hogy a szerepkörük szerinti leghatékonyabb módon segítse a felhasználókat az üzleti elemzések létrehozásában, megosztásában és felhasználásában.

## <a name="how-power-bi-matches-your-role"></a>A Power BI illeszkedése az Ön szerepköréhez
A Power BI szolgáltatás használata függhet attól, hogy Ön milyen szerepkört tölt be egy projektben vagy egy csapatban. A Power BI-t mindenki saját szerepkörének megfelelően használja.

Előfordulhat például, hogy Ön elsősorban a **Power BI szolgáltatást** használja, míg a számításokat végző és üzleti jelentéseket létrehozó munkatársa nagy mértékben támaszkodik a **Power BI Desktop** alkalmazásra (és a Desktop alkalmazásban készített jelentéseket közzéteszi a Power BI szolgáltatásban, ahol Ön aztán megtekintheti őket). Mindeközben elképzelhető, hogy egy másik, értékesítési osztályon dolgozó munkatárs a Power BI mobilalkalmazást használja az értékesítési kvótái előrehaladásának figyeléséhez, illetve az új értékesítések részleteinek vizsgálatához.

Fejlesztőként használhatja a Power BI API-jait arra, hogy az adatokat adatkészletekbe töltse be, vagy hogy irányítópultokat és jelentéseket ágyazzon be egyéni alkalmazásaiba. Javaslata van új vizualizációra? Hozza létre, és ossza meg másokkal is.  

A **Power BI** egyes elemeit használhatja emellett felváltva is attól függően, hogy épp milyen céljai vannak, illetve milyen szerepkörben dolgozik egy adott projektben vagy feladaton.

Megtekintheti például a leltárat és a gyártási folyamat állapotát a szolgáltatás egy valós idejű irányítópultján, a **Power BI Desktop** alkalmazással pedig jelentéseket hozhat létre a saját csapatának az ügyfélkapcsolati statisztikákról. A Power BI használatának módját befolyásolhatja, hogy a Power BI mely funkciója vagy szolgáltatása a legjobb eszköz az adott helyzetben – de a Power BI összes részéhez hozzáférhet, és ez teszi ezt a megoldást oly rugalmassá és hatékonnyá.

A szerepköréhez kapcsolódó dokumentumok elemzése:
- Power BI [***tervezők***](desktop-what-is-desktop.md) számára
- Power BI [***felhasználók***](consumer/end-user-consumer.md) számára
- Power BI [***fejlesztők***](developer/what-can-you-do.md) számára
- Power BI [***rendszergazdák***](service-admin-administering-power-bi-in-your-organization.md) számára

## <a name="the-flow-of-work-in-power-bi"></a>A Power BI-ban való munka folyamata
A Power BI-ban a leggyakoribb munkafolyamat első lépése az adatforrásokhoz való csatlakozás, majd pedig jelentések létrehozása a **Power BI Desktopban**. A létrehozott jelentést ezt követően a **Desktopból** közzé lehet tenni a **Power BI szolgáltatásban**, és meg lehet osztani más felhasználókkal, akik azt a **szolgáltatásban** és **mobileszközökön** is *használhatják*.
Előfordulhat, hogy egyes kollégáknak az Önéhez hasonló (azaz *létrehozói*) jogosultságokat szeretne adni, ami lehetővé teszi, hogy a **szolgáltatásban** ők is szerkeszthessék a jelentéseket, irányítópultokat hozzanak létre és megoszthassák a munkájukat.

Noha nem mindig ez az eljárás használatos, ez a leggyakoribb forgatókönyv, és ez megmutatja, hogyan egészíti ki egymást a Power BI három fő összetevője.

De mi történik, ha Ön nem áll még készen arra, hogy a felhőbe települjön át, és jelentéseit egy vállalati tűzfal mögött szeretné tartani?  Olvasson tovább.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Helyszíni jelentéskészítés a Power BI jelentéskészítő kiszolgálóval
A Power BI mobil és többoldalas jelentések létrehozása, telepítése és felügyelete a helyszínen a Power BI jelentéskészítő kiszolgáló által biztosított, használatra kész eszközökkel.

![a helyszíni diagramja](media/power-bi-overview/power-bi-report-server2.png)

A Power BI jelentéskészítő kiszolgáló megoldást tűzfal mögött lehet üzembe helyezni, és ezt követően különféle módokon lehet a jelentéseket a megfelelő felhasználókhoz eljuttatni, akik megnézhetik azokat egy webböngészőben, mobileszközön vagy e-mailben is. Mivel a Power BI jelentéskészítő kiszolgálója kompatibilis a felhőalapú Power BI-jal, bármikor dönthet úgy, hogy áttelepül a felhőbe, ha készen áll rá.

## <a name="next-steps"></a>Következő lépések
[Jelentkezzen be, olvasson be adatokat, és ismerkedjen meg a Power BI szolgáltatás használatának alapjaival](service-the-new-power-bi-experience.md)   
[Oktatóanyag: A Power BI szolgáltatás használatának első lépései](service-get-started.md)
