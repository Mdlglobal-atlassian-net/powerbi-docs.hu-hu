---
title: Mik azok a helyszíni adatátjárók?
description: Alapvető ismeretek a Power BI-adatátjárókról.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: overview
ms.date: 04/18/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: f1ae47dcb7c9281db018952d619691607d331003
ms.sourcegitcommit: 87e81ba92f3d1d65c26f9fc007bf106f96f37bfd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57461649"
---
# <a name="what-are-on-premises-data-gateways"></a>Mik azok a helyszíni adatátjárók?

A Power BI-átjáró egy olyan szoftver, amelyet a helyszíni hálózaton belül telepíthet, és amely lehetővé teszi a hálózaton belüli adatok elérését. Kapuőrként figyeli a kapcsolódási kérelmeket, és csak akkor engedélyezi azokat, ha a felhasználói kérelem eleget tesz bizonyos feltételeknek. Ez lehetővé teszi, hogy a cégek az adatbázisaikat és más adatforrásaikat a helyszíni hálózaton belül tartsák, de ezzel együtt biztonságosan használhassák ezeket a helyszíni adatokat a Power BI-jelentésekhez és az irányítópultokhoz.

Egy átjáró használható egyetlen adatforráshoz vagy több adatforráshoz. Az alábbi ábrán egy áttekintő nézet látható, ahol az átjáró a felhőből három helyszíni számítógéphez érkező kérelmet kezel. A cikk későbbi részében erre még részletsebben is kitérünk majd.

![Az átjáró áttekintése](media/service-gateway-getting-started/gateway-overview.png)

## <a name="types-of-gateways"></a>Átjárótípusok

A Power BI két átjárót biztosít, mindegyiket külön helyzethez:

* **Helyszíni adatátjáró (személyes mód)** – egyetlen felhasználónak teszi lehetővé, hogy kapcsolódjon a forrásokhoz, és nem osztható meg másokkal. Csak a Power BI-jal használható. Ez az átjáró kiválóan alkalmazható olyan helyzetekhez, ahol egyedül Ön készít jelentéseket, és nem szükséges megosztania az adatforrásokat másokkal.

* **Helyszíni adatátjáró** – Több felhasználó számára teszi lehetővé, hogy több helyszíni adatforráshoz csatlakozzanak. Használhatja a Power BI, a PowerApps, a Flow, az Azure Analysis Services és az Azure Logic Apps szolgáltatásokkal, és mindegyikhez csupán egyetlen átjárótelepítés szükséges. Ez az átjáró összetettebb helyzetekhez optimális, ahol többen is hozzá akarnak férni több adatforráshoz. 

## <a name="using-a-gateway"></a>Átjáró használata

Átjáró használatához négy fő lépés szükséges:

1. **Az átjáró telepítése** egy helyi számítógépen a megfelelő mód használatával
2. **Felhasználók hozzáadása az átjáróhoz**, hogy hozzáférhessenek a helyszíni adatforrásokhoz
3. **Csatlakozás adatforrásokhoz**, hogy azok használhatóak legyenek jelentésekben és irányítópultokon
4. **A helyszíni adatok frissítése**, hogy a Power BI-jelentések mindig aktuálisak legyenek

Telepíthető önálló átjáró, vagy egy *fürthöz* is hozzáadható egy átjáró – ez utóbbi a javasolt eljárás a magas rendelkezésre állás érdekében.

## <a name="how-gateways-work"></a>Az átjárók működése

A telepített átjáró **helyszíni adatátjáró** Windows-szolgáltatásként fut. Ez a helyi szolgáltatás az Azure Service Buson keresztül van regisztrálva a Gateway felhőszolgáltatásban. Az alábbi ábra a helyszíni adatok és az átjárót használó felhőszolgáltatások közötti folyamatot mutatja be.

![Ábra az átjáró adatfolyamával](media/service-gateway-getting-started/gateway-how-it-works.png)

Lekérdezések és adatfolyam:

1. A felhőszolgáltatás létrehoz egy lekérdezést a helyszíni adatforráshoz tartozó titkosított hitelesítő adatokkal. Ezt a rendszer elküldi az átjáró várólistájára feldolgozásra.
2. Az átjáró felhőszolgáltatása elemzi a lekérdezést, majd leküldi a kérelmet az Azure Service Busnak. A Power BI kezeli a Service Bust az Ön számára, tehát nincsenek további költségek, sem konfigurációs lépések, amelyeket végre kellene hajtani.
3. A helyszíni adatátjáró lekérdezi a függőben lévő kéréseket az Azure Service Busról.
4. Az átjáróhoz beérkezik a lekérdezés, az elvégzi a hitelesítő adatok visszafejtését, majd kapcsolódik az adatforrásokhoz ezekkel a hitelesítő adatokkal.
5. A futtatáshoz az átjáró a lekérdezést elküldi az adatforrásnak.
6. A futtatás eredményeit az adatforrás visszaküldi az átjárónak, majd a felhőszolgáltatásnak és az Ön kiszolgálójának.

## <a name="next-steps"></a>Következő lépések
[A helyszíni adatátjáró telepítése](service-gateway-install.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

