---
title: Az egyszeri bejelentkezés (SSO) áttekintése a Power BI-ban található átjárókhoz
description: Az átjáró konfigurálása a Power BI-ból a helyszíni adatforrásokba történő egyszeri bejelentkezés (SSO) engedélyezéséhez.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 43394e8f09327ebcb858ff5644b30daee1793444
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872374"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Az egyszeri bejelentkezés (SSO) áttekintése a Power BI-ban található átjárókhoz

A helyszíni adatátjáró konfigurálásával zökkenőmentes egyszeri bejelentkezési kapcsolatot hozhat létre, amely lehetővé teszi a Power BI-jelentések és -irányítópultok valós idejű frissítését a helyszíni adatokból. Lehetősége van az átjáró konfigurálására a [Kerberos](service-gateway-sso-kerberos.md) korlátozott delegálással vagy a Security Assertion Markup Language ([SAML](service-gateway-sso-saml.md)) használatával. A helyszíni adatátjáró a helyszíni adatforrásokhoz csatlakozó [DirectQuery](desktop-directquery-about.md) használatával támogatja az SSO-t.

A Power BI az alábbi adatforrásokat támogatja:

* SQL Server (Kerberos)
* SAP HANA (Kerberos és SAML)
* SAP BW Application Server (Kerberos)
* SAP BW Message Server (Kerberos) - nyilvános előzetes verzió
* Oracle (Kerberos) - nyilvános előzetes verzió
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

Az egyszeri bejelentkezés jelenleg nincs támogatva az [M-bővítményeknél](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Ha egy felhasználó DirectQuery-jelentést használ a Power BI szolgáltatásban, az összes keresztszűrő, szeletelő, rendezés és szerkesztési művelet olyan lekérdezéseket eredményezhet, amelyek az alapul szolgáló helyszíni adatforrásból dolgoznak. Ha az egyszeri bejelentkezés konfigurálva van az adatforráshoz, akkor a Power BI-t használó felhasználó identitása alatt futnak a lekérdezések (vagyis a webtartalmakon vagy a Power BI-mobilalkalmazásokon keresztül). Ezért minden felhasználó pontosan azokat az adatokat látja, amelyekhez engedélye van az alapul szolgáló adatforrásban. Ha az egyszeri bejelentkezés konfigurálva van, nincs megosztott adatgyorsítótárazás a különböző felhasználók számára.

## <a name="query-steps-when-running-sso"></a>A lekérdezés lépései SSO futtatása esetén

Az SSO-val futó lekérdezés három lépésből áll, az alábbi ábrán látható módon.

![Az SSO-lekérdezés lépései](media/service-gateway-sso-overview/sso-query-steps.png)

További információk az egyes lépésekről:

1. Az egyes lekérdezésekhez a Power BI szolgáltatás hozzárendeli az *egyszerű felhasználónevet (ez a UPN*, vagyis a Power BI szolgáltatásba bejelentkezett felhasználó felhasználói neve), amikor elküldi a lekérdezési kérést a konfigurált átjáróra.

2. Az átjárónak le kell képeznie az Azure Active Directory UPN-jét egy helyi Active Directory-identitásra:

   a. Ha az Azure AD DirSync (más néven *Azure AD Connect*) konfigurálva van, akkor a leképezés automatikusan működik az átjáróban.

   b.  Ellenkező esetben az átjáró kikeresheti és leképezheti az Azure AD UPN-jét egy helyi AD-felhasználóra a helyi Active Directory-tartományra irányuló keresés végrehajtásával.

3. Az átjárószolgáltatás folyamata megszemélyesíti a leképezett helyi felhasználót, megnyitja a kapcsolatot az alapul szolgáló adatbázishoz, és elküldi a lekérdezést. Az átjárót nem kell ugyanarra a gépre telepíteni, mint az adatforrást.

## <a name="next-steps"></a>Következő lépések

Most, hogy megismerte az SSO átjárón történő engedélyezésének alapjait, a Kerberos és az SAML használatával kapcsolatos részletesebb információkért olvassa el az alábbi cikkeket:

* [Egyszeri bejelentkezés (SSO) – Kerberos](service-gateway-sso-kerberos.md)
* [Egyszeri bejelentkezés (SSO) – SAML](service-gateway-sso-saml.md)
