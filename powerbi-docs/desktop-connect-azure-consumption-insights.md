---
title: Kapcsolódás Azure Consumption Insights-adatokhoz a Power BI Desktopban
description: Könnyedén kapcsolódhat az Azure-hoz és használati elemzésekhez juthat hozzá a Power BI Desktop segítségével
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c6987c5849fd2f971c1d7bdc7fe6130dcd09ce59
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761726"
---
# <a name="connect-to-azure-consumption-insights-data-in-power-bi-desktop"></a>Kapcsolódás Azure Consumption Insights-adatokhoz a Power BI Desktopban

A Power BI Desktop használatával csatlakozhat az Azure-hoz és részletes adatokat kaphat a Azure-szolgáltatások vállalata általi használatáról. Ezeknek az adatoknak a birtokában egyéni jelentéseket és mértékeket hozhat létre, amelyekkel jobban megértheti és elemezheti az Azure-beli kiadásait.

> [!NOTE]
> A Microsoft Azure Consumption Insightshoz (bétaverzió) korlátozott támogatás érhető el. További funkciókhoz használja az [Azure Cost Management-összekötőt a Power BI-ban](desktop-connect-azure-cost-management.md).

## <a name="connect-with-azure-consumption-insights"></a>Kapcsolódás az Azure Consumption Insights segítségével

Azure Consumption Insights lehetővé teszi, Azure Nagyvállalati Szerződéses számlázási fiókokhoz csatlakozzon.

Ebből a szakaszból megtudhatja, hogyan juthat hozzá a migráláshoz szükséges adatokhoz az Azure Enterprise-összekötő használatával. Az **ACI** (Azure Consumption Insights) API-ban a *felhasználási részleteket tartalmazó oszlopok* leképezését is megtalálhatja.

Az **Azure Consumption Insights**-összekötő sikeres használatához hozzáféréssel kell rendelkeznie az Azure Portal nagyvállalati funkcióhoz.

Az **Azure Consumption Insights**-összekötőt a következőképpen használhatja a **Power BI Desktopban**: 

1. A **Kezdőlap** menüszalagon válassza az **Adatok lekérése** lehetőséget.

1. A bal oldali kategóriák közül válassza az **Online szolgáltatások** lehetőséget.  

1. Válassza a **Microsoft Azure Consumption Insights (bétaverzió)** elemet. 

1. Kattintson a **Csatlakozás** gombra.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

   A megjelenő párbeszédablakban adja meg **Azure-beli regisztrációs számát**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

   * A beléptetési számot az [Azure Enterprise Portalról](https://ea.azure.com) kérheti le, a következő képen látható helyről:

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)

   Az összekötő ezen verziója csak a https://ea.azure.com címről érkező vállalati belépéseket támogatja. A Kínából történő belépések jelenleg nem támogatottak.

   Következő lépésként adja meg a *Hozzáférési kulcsát* a csatlakozáshoz.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

   * A beléptetéshez használatos hozzáférési kulcsát az [Azure Enterprise Portalon](https://ea.azure.com) kérheti le.

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Miután megadta *hozzáférési kulcsát*, és kiválasztotta a **Csatlakozás** lehetőséget, megjelenik a **Kezelő** ablak, rajta az elérhető kilenc táblával:

| Táblázat        | Leírás |
|------------- | -------------------------------------------------------------|
| **Budgets** | Költségvetési részletek a tényleges költségek megtekintéséhez vagy a használat és a költségkeret összehasonlításához. |
| **MarketPlace** | Használatalapú Azure Marketplace-díjak. |
| **PriceSheets** | Egy regisztráció mérőnként érvényesíthető díjai. |
| **RICharges** | A fenntartott példányaival kapcsolatos utolsó 24 havi díjak. |
| **RIRecommendations_Single** | Fenntartott példányok vásárlására vonatkozó javaslatok az egy előfizetésen belül 7, 30 vagy 60 napon át tapasztalt használati trendek alapján. |
| **RIRecommendations_Shared** | Fenntartott példányok vásárlására vonatkozó javaslatok az összes előfizetésen belül 7, 30 vagy 60 napon át tapasztalt használati trendek alapján. |
| **RIUsage** | Az utolsó hónapra vonatkozó fogyasztási részletek a meglévő fenntartott példányairól. |
| **Summaries** | Havi összegzés az egyenlegekről, új vásárlásokról, az Azure Marketplace-szolgáltatások díjairól, módosításokról és kerettúllépési díjakról. |
| **UsageDetails** | A felhasznált mennyiségek részletes lebontása és a becsült regisztrációs díjak. |

Ha valamelyik tábla jelölőnégyzetét bejelöli, megjelenik egy előnézet. Több táblát is kiválaszthat a nevek melletti jelölőnégyzetekkel, majd kattintson a **Betöltés** gombra.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> A *Summary* és *PriceSheet* táblák csak a beléptetési szintű API-kulcsokkal elérhetők. A táblák alapértelmezés szerint az aktuális havi *használat* és *árlista* adatait tartalmazzák. A *Summary* és a *Marketplace* táblák nem korlátozódnak az aktuális hónapra.
>
>

Ha a **Betöltés** gombra kattint, a rendszer betölti az adatokat a **Power BI Desktopba**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

A kiválasztott adatok betöltése után a kiválasztott táblák és mezők láthatók lesznek a **Mezők** panelen.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Az Azure Consumption Insights használata
Az **Azure Consumption Insights**-összekötő használatához hozzá kell férnie az Azure Portal nagyvállalati funkcióhoz.

Miután sikeresen betöltötte az adatokat az **Azure Consumption Insights** összekötő használatával, létrehozhatja a saját egyéni mértékeit és oszlopait a **Lekérdezésszerkesztő** segítségével. Vizualizációkat, jelentéseket és irányítópultokat is létrehozhat, amelyeket megoszthat a **Power BI szolgáltatásban**.

Üres lekérdezéssel egyéni Azure-lekérdezésminták gyűjteményét kérheti le. Ezt a lekérést két módon hajthatja végre: 

A **Power BI Desktopban**: 

1. Válassza a **Kezdőlap** menüszalagot 
2. Válassza az **Adatok lekérése** > **Üres lekérdezés** lehetőséget 

A **Lekérdezésszerkesztőben**: 

1. Kattintson jobb gombbal a bal oldali **Lekérdezések** panelre 
2. Válassza a megjelenő menü **Új lekérdezés > Üres lekérdezés** elemét

A **Képletsávba** gépelje be következőt:

    = MicrosoftAzureConsumptionInsights.Contents

Az alábbi képen egy ilyenkor megjelenő mintagyűjtemény látható.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Jelentések használatakor és lekérdezések létrehozásakor megteheti a következőket:

* A jelenlegi dátumtól számított hónapok számának meghatározásához használja a *numberOfMonth* paramétert
  * Használjon 1 és 36 közötti értéket. Ez adja meg az importálni kívánt hónapok számát az aktuális dátumtól számítva. Ajánlott legfeljebb 12 hónapnyi adatot lekérni. Ezzel a korlátozással elkerülheti a Power BI-lekérdezés importálási korlátozásinak vagy az adatmennyiség küszöbértékeinek túllépését.
* Egy több hónapos múltbéli időszak meghatározásához használja a *startBillingDataWindow* és *endBillingDataWindow* paramétereket
* A *numberOfMonth* paramétert ne használja a *startBillingDataWindow* vagy az *endBillingDataWindow* paraméterrel együtt

## <a name="migrate-from-the-azure-enterprise-connector"></a>Migrálás az Azure vállalati csatolóból

Néhány ügyfél az *Azure vállalati csatoló (bétaverzió)* használatával hozott létre vizualizációkat. Ezek helyt végül az **Azure Consumption Insights**-összekötő veszi majd át. Az új összekötő többek között az alábbi funkciókkal és fejlesztésekkel rendelkezik:

* További elérhető adatforrások az *Egyenleg összesítése* és a *Marketplace vásárlások* esetében
* Új és speciális paraméterek, pl. *startBillingDataWindow* és *endBillingDataWindow*
* Jobb teljesítmény és válaszképesség

A következő lépések az **Azure Consumption Insights**-összekötőre való áttérést mutatják be. Ezek a lépések megőrzik az egyéni irányítópultok vagy jelentések létrehozásával már elvégzett munkáját.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>1\. lépés: Csatlakozás az Azure-hoz az új összekötővel
Az első lépés a cikk korábbi részében már részletesen bemutatott **Azure Consumption Insights**-összekötő használata. Ebben a lépésben a **Power BI Desktop** **Kezdőlap** szalagján válassza a **Lekérdezés > Üres lekérdezés** lehetőséget.

### <a name="step-2-create-a-query-in-advanced-editor"></a>2\. lépés: Lekérdezés létrehozása a Speciális szerkesztőben
A **Lekérdezésszerkesztőben** válassza a **Speciális szerkesztőt** a **Kezdőlap** menüszalag **Lekérdezés** szakaszában. A megjelenő **Speciális szerkesztő** ablakban adja meg az alábbi lekérdezést:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Az *enrollmentNumber* érték helyére a saját regisztrációs számát kell beírnia. A számát az [Azure Enterprise portálon](https://ea.azure.com) tudhatja meg. A *numberOfMonth* paraméter adja meg, hány hónapot szeretne visszamenni az aktuális dátumtól számítva. A nulla (0) érték az aktuális hónapot jelöli.

Miután rákattintott a **Kész** gombra a **Speciális szerkesztőben**, az előnézet frissül és a táblában megjelennek a megadott hónaptartományra vonatkozó adatok. Kattintson a **Bezárás és alkalmazás** gombra a visszalépéshez.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>3\. lépés: Mértékek és egyéni oszlopok áthelyezése az új jelentésbe
Ezután át kell helyezni minden létrehozott egyéni oszlopot és mértéket a részleteket tartalmazó új táblába. A lépések a következők.

1. Nyissa meg a Jegyzettömböt (vagy egy másik szövegszerkesztőt).
2. Válassza ki az áthelyezni kívánt mértéket, másolja ki a *Képlet* mező szövegét, és illessze be a Jegyzettömbben.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Nevezze át a *Lekérdezés1* táblát a részleteket tartalmazó tábla eredeti nevére.
4. Új táblamértékek és egyéni oszlopok létrehozásához kattintson a jobb gombbal a táblára, majd válassza az **Új mérték** lehetőséget. Ez után vágja ki és illessze be a tárolt mértékeket és oszlopokat, amíg mindegyik el nem készül.

### <a name="step-4-relink-tables-that-had-relationships"></a>4\. lépés: A kapcsolatokkal rendelkezett táblák újrakapcsolása
Számos irányítópult rendelkezik kereséshez vagy szűréshez használt táblákkal, dátumtáblákkal és egyéni projektekhez használt táblákkal. Ezen kapcsolatok ismételt megadása megoldja a fennmaradó problémák nagy részét. Ennek menete a következő.

- A **Power BI Desktop** **Modellezés** lapján kattintson a **Kapcsolatok kezelése** lehetőségre. Ekkor megnyílik egy ablak, amelyben a modellen belüli kapcsolatok kezelhetők. Kapcsolja újra a táblákat szükség szerint.

    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>5\. lépés: Vizualizációk ellenőrzése, mezők formázásának igazítása
Ezen a ponton az eredeti vizualizációk, táblák és részletezések többségének már megfelelő módon működnie kell. A megjelenés pontos formázása azonban igényelhet még néhány kisebb igazítást. Szánjon egy kis időt az egyes irányítópultok és vizualizációk áttekintésére.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Az Azure Consumption Insights (ACI) API használata a használati adatok lekéréséhez
Az Azure biztosítja az [**Azure Consumption Insights (ACI) API**](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/)-t is. Létrehozhatja a saját egyéni megoldásait az Azure-használati adatok gyűjtéséhez, a jelentéskészítéshez és a vizualizáláshoz az ACI API használatával.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Nevek és használati adatok társítása a portál, az összekötő és az API között
Az Azure Portalbeli oszlopok és részletek nevei hasonlóak az API-ban és az összekötőében használtakhoz, de nem mindig azonosak. Az egyértelműség érdekében az alábbi táblázat ismerteti a leképezést. A táblázat azt is jelzi, ha egy oszlop elavult. Ezen kifejezések definícióit és a további információkat az [Azure-számlázási adatok szótárában](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail) találja meg.

| ACI összekötő/tartalomcsomag oszlopneve | ACI API oszlopneve | EA oszlopneve | Elavult/visszamenőleges kompatibilitási célból érhető el |
| --- | --- | --- | --- |
| AccountName |accountName |Account Name |Nem |
| AccountId |accountId | |Igen |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |Nem |
| AdditionalInfo |additionalInfo |AdditionalInfo |Nem |
| AdditionalInfold | | |Igen |
| Consumed Quantity |consumedQuantity |Consumed Quantity |Nem |
| Consumed Service |consumedService |Consumed Service |Nem |
| ConsumedServiceId |consumedServiceId | |Igen |
| Cost |cost |ExtendedCost |Nem |
| Cost Center |costCenter |Cost Center |Nem |
| Dátum |date |Dátum |Nem |
| Nap | |Nap |Nem |
| DepartmentName |departmentName |Department Name |Nem |
| DepartmentID |departmentId | |Igen |
| Instance ID | | |Igen |
| InstanceId |instanceId |Instance ID |Nem |
| Hely | | |Igen |
| Meter Category |meterCategory |Meter Category |Nem |
| Meter ID | | |Igen |
| Mérő neve |meterName |Meter Name |Nem |
| Meter Region |meterRegion |Meter Region |Nem |
| Meter Sub-Category |meterSubCategory |Meter Sub-Category |Nem |
| MeterId |meterId |Meter ID |Nem |
| Hónap | |Hónap |Nem |
| Termék |product |Termék |Nem |
| ProductId |productId | |Igen |
| Erőforráscsoport |resourceGroup |Resource Group |Nem |
| Resource Location |resourceLocation |Resource Location |Nem |
| ResourceGroupId | | |Igen |
| ResourceLocationId |resourceLocationId | |Igen |
| ResourceRate |resourceRate |ResourceRate |Nem |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |Nem |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |Nem |
| ServiceInfo1Id | | |Igen |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |Nem |
| ServiceInfo2Id | | |Igen |
| Store Service Identifier |storeServiceIdentifier |Store Service Identifier |Nem |
| StoreServiceIdentifierId | | |Igen |
| Előfizetés neve |subscriptionName |Subscription Name |Nem |
| Címkék |tags |Tags |Nem |
| TagsId | | |Igen |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |Nem |
| Év | |Év |Nem |
| SubscriptionId |subscriptionId |SubscriptionId |Igen |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Nem |


## <a name="next-steps"></a>Következő lépések

A Power BI Desktop használatával számos különböző adatforráshoz csatlakozhat. További információért tekintse át a következő cikkeket:

* [Kapcsolódás Azure Cost Management-adatokhoz a Power BI Desktopban](desktop-connect-azure-cost-management.md)
* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   
