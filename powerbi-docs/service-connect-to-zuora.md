---
title: Csatlakozás a Zuorához a Power BI-ból
description: Zuora a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b183738c062af1d834a742639369ca90f2cb1bad
ms.sourcegitcommit: 42475ac398358d2725f98228247b78aedb8cbc4f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003225"
---
# <a name="connect-to-zuora-with-power-bi"></a>Csatlakozás a Zuorához a Power BI-ból
A Power BI-hoz készült Zuora segítségével ábrázolhatja a bevételekkel, a számlázással és az előfizetésekkel kapcsolatos fontos adatait. Az alapértelmezett irányítópulttal és jelentésekkel elemezheti a használati trendeket, követheti a számlázási és fizetési adatokat, illetve figyelheti az ismétlődő bevételeket. Az irányítópultot és a jelentéseket testre is szabhatja az egyéni igényei kielégítéséhez.

Csatlakozzon a Power BI-hoz készült [Zuora](https://app.powerbi.com/getdata/services/Zuora) szolgáltatáshoz.

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.

   ![](media/service-connect-to-zuora/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.

   ![](media/service-connect-to-zuora/services.png)
3. Válassza a **Zuora** \> **Beolvasás** lehetőséget.

   ![](media/service-connect-to-zuora/zuora.png)
4. Adja meg a Zuora URL-címét. Az URL-cím általában „<https://www.zuora.com>”. A [paraméterek megkereséséről](#FindingParams) alább olvashat részletesebben.

   ![](media/service-connect-to-zuora/params.png)
5. **Hitelesítési módszerként** válassza az **Alapszintű** lehetőséget, adja meg a felhasználónevét és a jelszavát (figyeljen a kis- és nagybetűkre), majd kattintson a **Bejelentkezés** elemre.

    ![](media/service-connect-to-zuora/creds.png)
6. A jóváhagyás után automatikusan megkezdődik az importálási folyamat. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.

     ![](media/service-connect-to-zuora/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
Ez a tartalomcsomag a Zuora AQUA API segítségével olvas be adatokat az alábbi táblákból:

| Táblák |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Usage |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

Emellett az alábbi számított mértékeket is tartalmazza:

| Mérték | Leírás | Számítás |
| --- | --- | --- |
| Account: Payments |Befizetések teljes összege egy időszakban, a befizetések hatályba lépési dátuma szerint. |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Account: Refunds |Visszatérítések teljes összege egy időszakban, a visszatérítések hatályba lépési dátuma szerint. Ez a mennyiség negatív számként jelenik meg. |-1*SUM(Refund.Amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| Account: Net Payments |Fiókhoz tartozó befizetések plusz fiókhoz tartozó visszatérítések egy adott időszakban. |Account.Payments + Account.Refunds |
| Account: Active Accounts |Az adott időszakban aktív fiókok száma. Az időszak kezdő dátuma előtt (vagy azzal egy időben) induló előfizetéseket tartalmazza. |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) –evergreen subscription |
| Account: Average Recurring Revenue |Bruttó havi ismétlődő bevétel (MRR) az adott időszakban aktív fiókokként. |Gross MRR / Account.ActiveAccounts |
| Account: Cancelled Subscriptions |Az adott időszakban előfizetést lemondó fiókok száma. |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Cancelled"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| Account: Payment Errors |A befizetési hibák összesített értéke. |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Error" |
| Revenue Schedule Item: Recognized Revenue |Az adott számviteli időszakban érvényes összbevétel. |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Subscription: New Subscriptions |Az új előfizetések száma egy adott időszakban. |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| Invoice: Invoice Items |Számlatételek díjának összértéke egy adott időszakban. |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Taxation Items |Adózási tételek összértéke egy adott időszakban. |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Invoice Item Adjustments |Számlatételek korrekciójának összértéke egy adott időszakban. |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Invoice: Invoice Adjustments |Számlák korrekciójának összértéke egy adott időszakban. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Invoice: Net Billings |A számlatételeknek, az adózási tételeknek, a számlatételek korrekcióinak és a számlák korrekcióinak összértéke egy adott időszakban. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Invoice: Invoice Aging Balance |Elküldött számlaegyenlegek összege. |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Posted" |
| Invoice: Gross Billings |Számlatételek díjának összege az elküldött számlákra vonatkozóan egy adott időszakban. |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Total Adjustments |Az elküldött számlákhoz tartozó feldolgozott számlakorrekciók és számlatétel-korrekciók összege. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Rate Plan Charge: Gross MRR |Előfizetésekből származó havi ismétlődő bevétel összege egy adott időszakban. |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR    RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Rendszerkövetelmények
Hozzáféréssel kell rendelkeznie a Zuora API-hoz.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek keresése
Adja meg azt az URL-címet, amellyel be szokott jelentkezni a Zuora-adatai eléréshez. Az érvényes lehetőségek a következők:  

* https://www.zuora.com  
* A használt szolgáltatáspéldány által meghatározott URL-cím  

## <a name="troubleshooting"></a>Hibaelhárítás
A Zuora-tartalomcsomag a Zuora-fiókjához tartozó adatok széles körét beolvassa. Ha nem használ bizonyos funkciókat, akkor előfordulhat, hogy a vonatkozó csempék vagy jelentések üresek lesznek. Ha problémát tapasztal a betöltés során, lépjen kapcsolatba a Power BI támogatási szolgálatával.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)
