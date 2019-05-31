---
title: Csatlakozás a Power BI Premium-adatkészletek (előzetes verzió) eszközök és az ügyfélalkalmazások számára
description: Csatlakozás adathalmazokhoz a Power BI Premium ügyfélalkalmazások és az eszközök módját ismerteti.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941499"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Csatlakozás adathalmazokhoz az ügyfél-alkalmazások és eszközök (előzetes verzió)

A Power BI Premium-munkaterületek és adatkészletek támogatási *csak olvasható* kapcsolatok a Microsoft és külső ügyfél-alkalmazások és eszközök. 

> [!NOTE]
> Ez a cikk csak be a Power BI prémium szintű munkaterületeken és az adatkészletek csak olvasható kapcsolat célja. Ez *nem* programozhatóság, eszközöket és alkalmazásokat, architektúra és felügyeleti munkaterületet, és az adatkészlet kapcsolatos részletes információk megadására szolgál. Az itt ismertetett témák Analysis Services táblázatos modellű adatbázis-architektúra és felügyeleti alapos ismerete szükséges.

## <a name="protocol"></a>Protokoll

A Power BI Premium használja a [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) (XMLA) protokoll ügyfél-alkalmazások és a motor, amely a-munkaterületek és adatkészletek közötti kommunikációhoz. Ezek a kommunikációk rendszer milyen gyakran nevezik XMLA végpontok. Az XMLA ugyanazt a kommunikációs protokollt használják a Microsoft Analysis Services motort, amely technikai részletek, futtatja a Power BI szemantikai modellezés, cégirányítási, életciklusát és data management. 

Ügyfél-alkalmazások és eszközök túlnyomó többsége nem explicit módon kommunikálnak a motor az XMLA-végpont használatával. Például az MSOLAP ADOMD és AMO klienskódtárak ehelyett az ügyfélalkalmazás és a motor, amely kizárólag az XMLA használatával kommunikál közötti közvetítőként használnak.


## <a name="supported-tools"></a>Támogatott eszközök

Ezek az eszközök támogatják a Power BI prémium szintű munkaterületeken és az adatkészletek a csak olvasható hozzáférést:

**Az SQL Server Management Studio (SSMS)** – támogatja a DAX, MDX, XMLA és TraceEvent lekérdezéseket. 18.0 verzióját igényli. Töltse le [Itt](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**Az SQL Server Profiler** – SSMS 18.0 (előzetes verzió) részét képező, az eszköz biztosít nyomkövetéséhez és a kiszolgáló eseményeit. Rögzítése, és mentse kapcsolatos minden egyes esemény egy fájlhoz vagy tábla később elemzéséhez. Az SQL Server hivatalosan elavult, bár a Profiler továbbra is szerepelnie az ssms-ben, és továbbra is a támogatott Analysis Services és a most már a Power BI Premium. További tudnivalókért lásd: [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**A DAX-Studio** – nyílt forráskódú, közösségi eszköz végrehajtása és elemzése a DAX lekérdezés Analysis Services. Szükséges 2.8.2-es verzió vagy újabb verziója. További tudnivalókért lásd: [daxstudio.org](https://daxstudio.org/).

**Excel-kimutatások** - vagy újabb 16.0.11326.10000 az Office Kattintásra kattintson verzióra szükség.

**Harmadik féltől származó** - ügyfélalkalmazások adatokat Vizualizációk és kapcsolódhatnak az eszközök, lekérdezés, és adatkészleteket a Power BI Premium a felhasználni. A legtöbb az eszközök csak a legújabb verziókat MSOLAP-klienskódtár, de néhány ADOMD használhatja.

## <a name="client-libraries"></a>Ügyfélkódtárak

Ügyféloldali függvénytárak is ügyfélalkalmazások és az eszközök csatlakozni a Power BI Premium-munkaterület szükséges. Az Analysis Serviceshez való csatlakozáshoz használt azonos ügyfélkódtárak is támogatottak a Power BI Premium. Microsoft ügyfélalkalmazások, mint az Excel, az SQL Server Management Studio (SSMS) és az SQL Server Data Tools (SSDT) telepítése mindhárom ügyfélkódtárat, és frissítse azokat rendszeres alkalmazásfrissítéseknél együtt. Különösen a harmadik féltől származó alkalmazások és eszközök, bizonyos esetekben szükség lehet a klienskódtárak újabb verzióját telepítse. Ügyfélkódtárak havonta frissülnek. További tudnivalókért lásd: [klienskódtárak csatlakozik az Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Csatlakozás egy prémium munkaterület

Dedikált prémium szintű kapacitások rendelt munkaterületek csatlakozhat. Egy dedikált kapacitáshoz rendelve munkaterületekre egy kapcsolati karakterláncot az URL-formátum. 

A munkaterület-kapcsolati karakterlánc lekérése a Power BI-ban a **munkaterület beállításainak**, a a **prémium szintű** lap **munkaterület kapcsolat**, kattintson a **másolása**.

![Munkaterület kapcsolati karakterlánc](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

Munkaterület kapcsolatok formátuma a következő URL-cím használatával oldja meg a munkaterület, mintha egy Analysis Services-kiszolgáló neve:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Ha például `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` a kis-és nagybetűket, és szóközöket is tartalmazhatnak. 

### <a name="to-connect-in-ssms"></a>Csatlakozás az ssms-ben

A **kapcsolódás a kiszolgálóhoz** > **kiszolgálótípus**válassza **Analysis Services**. A **kiszolgálónév**, adja meg az URL-címet. A **hitelesítési**válassza **Active Directory - Universal MFA-támogatással rendelkező**, majd **felhasználónév**, adja meg a szervezeti felhasználói azonosítóját. 

Ha csatlakoztatva van, a munkaterület jelenik meg, mint egy Analysis Services-kiszolgálón, és a munkaterület adatkészletek adatbázisok jelennek meg.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Kezdeti katalógus

Bizonyos eszközök, például az SQL Server Profiler, előfordulhat, hogy kell adnia egy *Initial Catalog*. Adja meg a munkaterület egy adatkészletet (adatbázis). A **kapcsolódás a kiszolgálóhoz**, kattintson a **beállítások**. Az a **kapcsolódás a kiszolgálóhoz** párbeszédpanelen, a a **kapcsolat tulajdonságai** lap **csatlakozhat az adatbázishoz**, adja meg az adatkészlet nevét.

### <a name="duplicate-workspace-name"></a>Ismétlődő munkaterület neve

A munkaterület neve megegyezik egy másik munkaterülethez való csatlakozáskor a következő hiba jelenhet meg: **Nem lehet csatlakozni a powerbi://api.powerbi.com/v1.0/ [bérlő neve] / [munkaterületnév].**

Ez a hiba, a munkaterület neve mellett eléréséhez adja meg, amely a munkaterület objectID az URL-cím átmásolható a Objektumazonosítóguid. Az objectID hozzáfűzése a kapcsolati URL-cím. For example, `powerbi://api.powerbi.com/v1.0/myorg/Contoso Sales - 9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>Ismétlődő adatkészlet neve

Egy adatkészlet neve megegyezik egy másik adatkészlet ugyanazon a munkaterületen való csatlakozáskor hozzáfűzése a adatkészlet globálisan egyedi azonosítót az adatkészlet nevét. Megjelenik a két adatkészlet neve *és* guid, a munkaterület az ssms-ben való csatlakozáskor. 

### <a name="delay-in-datasets-shown"></a>Az adatkészletek látható késleltetés

Ha kapcsolódik egy munkaterületet, az új, törölt és átnevezett adatkészletekből származó módosítások jelennek meg, akár 5 percet is igénybe vehet. 

### <a name="unsupported-datasets"></a>Nem támogatott adatkészlet

Az alábbi adatkészletekben az XMLA-végpontok nem érhetők el. Ezek az adatkészletek *nem lesz* az ssms-ben vagy más eszközök munkaterületen jelennek meg: 

- Egy Analysis Services-modellekhez történő élő kapcsolattal rendelkező adatkészletek. 
- Adatok leküldése a REST API-val rendelkező adatkészletek.
- Excel-munkafüzet adatkészletek. 

A következő adatkészlet nem támogatottak a Power BI szolgáltatásban:   

- A Power BI-adatkészlethez élő kapcsolattal rendelkező adatkészletek.

## <a name="audit-logs"></a>Auditnaplók 

Ha ügyfél-alkalmazások és eszközök csatlakoznak egy munkaterületet, XMLA kapcsolódó végpontok hozzáférésének be van jelentkezve a Power BI-naplók alatt a **GetWorkspaces** műveletet. További tudnivalókért lásd: [Power BI-naplózás](service-admin-auditing.md).

## <a name="see-also"></a>Lásd még:

[Analysis Services-hivatkozások](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services táblázatos protokoll](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Dinamikus felügyeleti nézetekkel (DMV-kkel)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
