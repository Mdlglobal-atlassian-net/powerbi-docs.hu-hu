---
title: Tartalom kezelése a Power BI jelentéskészítő kiszolgáló webportálján
description: Ebben a cikkben a Power BI jelentéskészítő kiszolgáló webportálján végzett tartalomkezelésről olvashat.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/24/2018
ms.author: maggies
ms.openlocfilehash: e7a9b4da760f02672f51aa7ace0f3bb19c501834
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770135"
---
# <a name="manage-content-in-the-web-portal"></a>Tartalom kezelése a webes portálon 
A Power BI jelentéskészítő kiszolgáló webportálja egy helyszíni platform, amely Power BI-, mobil- és többoldalas jelentések és főbb teljesítménymutatók (KPI-k) megtekintésére, tárolására és kezelésére szolgál.

![A jelentéskészítő kiszolgáló webportálja](media/getting-around/report-server-web-portal.png)

A webportál bármelyik korszerű böngészőben megnyitható. A jelentéseket és a főbb teljesítménymutatókat a webportál mappákba rendezi, amelyeket megjelölhet kedvencként. A mappákban Excel-munkafüzeteket is tárolhat. A webportálról elindíthatja a jelentéskészítéshez szükséges eszközöket:

* Power BI Desktoppal létrehozott **Power BI-jelentések**: Megtekintheti őket a webportálon és a Power BI-mobilalkalmazásokban.
* A Jelentéskészítővel létrehozott **lapszámozott jelentések**: Korszerű megjelenésű, rögzített elrendezésű, nyomtatásra optimalizált dokumentumok.
* **Főbb teljesítménymutatók**, amelyek közvetlenül a webportálon készülnek.

A webportálon tallózhat a jelentéskészítő kiszolgáló mappáiban, és adott jelentéseket is megkereshet. Megtekintheti a jelentéseket, az általános jelentéstulajdonságaikat és a jelentéselőzmények közt tárolt korábbi példányaikat. Ha engedélyei lehetővé teszik, feliratkozhat jelentésekre, és kérheti az e-mailben vagy a fájlrendszer egy megosztott mappájába való elküldésüket.

## <a name="web-portal-roles-and-permissions"></a>Webportálszerepkörök és -engedélyek
A webportál alkalmazás böngészőben fut. Attól függ, hogy milyen lapok, hivatkozások és lehetőségek jelennek meg a webportál megnyitásakor, hogy Önnek milyen jogosultságai vannak a jelentéskészítő kiszolgálón. Ha teljes körű jogosultságokkal rendelkező szerepköre van, minden alkalmazásmenühöz és laphoz hozzáfér, amely a jelentéskészítő kiszolgáló kezeléséhez szükséges. Ha a szerepköre jelentések megtekintését és futtatását teszi lehetővé, akkor csak az ehhez szükséges menüket és lapokat éri el. Szerepkörei az egyes jelentéskészítő kiszolgálókon – sőt, akár egy kiszolgálón belül az egyes jelentésekben és mappákban – eltérőek lehetnek.

## <a name="start-the-web-portal"></a>A webportál megnyitása
1. Nyissa meg a webböngészőt.
   
    A [támogatott webböngészők és verziók](browser-support.md) listáját itt találja.
2. A címsorba írja be a webportál URL-jét.
   
    Ez alapértelmezés szerint a <em>http://[A számítógép neve]/reports</em>.
   
    Előfordulhat, hogy a jelentéskészítő kiszolgáló egy adott port használatára van beállítva. Például: <em>http://[A számítógép neve]:80/reports</em> vagy <em>http://[A számítógép neve]:8080/reports</em>
   
    Amint láthatja, a webportál kategóriákba rendezi az elemeket:
   
   * KPI-k
   * Mobiljelentések
   * Többoldalas jelentések
   * Power BI Desktop-jelentések
   * Excel-munkafüzetek
   * Adatkészletek
   * Adatforrások
   * Erőforrások

## <a name="manage-items-in-the-web-portal"></a>Elemek kezelése a webportálon
A Power BI jelentéskészítő kiszolgálón Önnek teljes körű jogosultsága van a webportálon tárolt elemek kezelésére. Beállíthat például feliratkozásokat, gyorsítótárazást, pillanatképeket és az egyes többoldalas jelentésekre vonatkozó védelmet.

1. Kattintson a három pontra (...) egy elem jobb felső sarkában, majd a **Kezelés** lehetőségre.
   
    ![Kattintás a Kezelés elemre](media/getting-around/report-server-web-portal-manage-ellipsis.png)
2. Válasszon egy tulajdonságot vagy más beállítást.
   
    ![Tulajdonság kiválasztása](media/getting-around/report-server-web-portal-manage-properties.png)
3. Kattintson az **Alkalmazás** lehetőségre.

További információ [a feliratkozásoknak a webportálon történő kezeléséről](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal).

## <a name="next-steps"></a>Következő lépések
[Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

