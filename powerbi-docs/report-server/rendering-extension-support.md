---
title: PDF-megjelenítési bővítmény megfelelősége az ISO 14289-1 szabványnak – Power BI jelentéskészítő kiszolgáló és SSRS
description: Ez a dokumentum a Power BI jelentéskészítő kiszolgáló és az SQL Server Reporting Services PDF-megjelenítési bővítményének ISO 14289-1 (PDF/UA) szabványnak való megfelelőségét ismerteti.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: bfefcef18b8cd92a5c3b15c2dcbd4653a6c7c9cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76819514"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>PDF-megjelenítési bővítmény megfelelősége az ISO 14289-1 szabványnak – Power BI jelentéskészítő kiszolgáló és SSRS

A következőkre vonatkozik: Power BI jelentéskészítő kiszolgáló és SQL Server Reporting Services (SSRS)

Ez a dokumentum a Power BI jelentéskészítő kiszolgáló és az SQL Server Reporting Services PDF-megjelenítési bővítményének [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/) szabványnak való megfelelőségét ismerteti.

> [!NOTE]
> A dokumentumot a böngésző **Nyomtatás**, **Mentés PDF-ként** lehetőségével elmentheti és ki is nyomtathatja.

## <a name="1--scope"></a>1.  Hatókör

Nem értelmezhető

## <a name="2--normative-references"></a>2.  Hivatkozások normatívákra

Nem értelmezhető

## <a name="3--terms-and-definitions"></a>3.  Feltételek és definíciók

Nem értelmezhető

## <a name="4--notation"></a>4.  Jelölés

Nem értelmezhető

## <a name="5-version-identification"></a>5. Verzió azonosítása

A PDF-megjelenítési bővítmény a PDF/UA szabványhoz biztosít támogatást, a jelen dokumentumban leírtak szerint. Egyes esetekben – az alább leírtaknak megfelelően – a felhasználó feladata, hogy elvégezze a szükséges lépéseket, és gondoskodjon róla, hogy a PDF-fájl teljes mértékben megfeleljen a PDF/UA szabványnak.  A felhasználó dolga hozzáadni a megfelelő PDF/UA-verziót és megfelelőségi azonosítókat a folyamat utolsó lépéseként, amelyek azt jelzik, hogy megtörténtek a szükséges lépések annak érdekében, hogy a PDF teljes mértékben PDF/UA-kompatibilis legyen.

A jelen dokumentumban felsoroltak a PDF-dokumentum olyan megjelenítésén alapulnak, amelynél az AccessiblePdf eszközinformációs beállítás `true` értékre van állítva. Bizonyos esetekben megfelelőségi korlátozások vannak érvényben a Report Definition Language (jelentésdefiníciós nyelv, RDL) korlátai miatt.

## <a name="6--conformance-requirements"></a>6.  Megfelelőségi követelmények

|     Feltételek     |     Támogatás     |     Megjegyzések      |
|----|--------|--------|
|    6.1 Általános    |                 Támogatott    |    A PDF-megjelenítő bővítmény 1.7-es PDF-verziót hoz létre.    |
|    6.2 Megfelelő fájlok    |                 Támogatva, kivételekkel    |    Lásd a megjegyzéseket a fájlformátum-követelményekre vonatkozó 7. szakaszban.    |
|    6.3 Megfelelő olvasó    |     Nem alkalmazható     |         |
|    6.4 Megfelelő kisegítő technológia    |     Nem alkalmazható     |         |

## <a name="7--file-format-requirements"></a>7.  Fájlformátum-követelmények

|     Feltételek     |     Támogatás     |     Megjegyzések      |
|-----|-------|------------------------|
|    7.1 Általános    |                 Támogatva, kivételekkel    |    Az összes valós tartalmat az ISO 32000-1:2008 14.8-as szakasza által meghatározott módon kell megjelölni. Az összetevők (ISO 32000-1:2008, 14.8.2.2.2) nem címkézhetőek a szerkezetfában. <li> A PDF-megjelenítő bővítmény nem teszi lehetővé, hogy explicit módon megjelölje az egyes elemeket összetevőkként, így mindent összetevőként kezel, ami leképezhető az ISO 32000-1:2008 14.8.2.2.2-es szakaszának feltételeire.<br>A tartalmat a szerkezetfában kell megjelölni logikus olvasási sorrendben, szemantikailag megfelelő címkékkel. <br> **Megjegyzés** A 4 WCAG 2.0 1.4-es iránymutatása a kisegítő lehetőségekhez kapcsolódó formázásokkal, például kontraszt- és színbeállításokkal kapcsolatos problémákat ismerteti. <br><li> A felhasználónak meg kell győződnie arról, hogy a dokumentumban nincsenek ilyen jellegű problémák. <br>Az ISO 32000-1:2008 14.8.4-es szakaszában definiált szabványos címkék nem képezhetőek le újra. <li> A PDF-megjelenítő bővítmény nem képezi le újra a szabványos címkéket. A dokumentumok a dokumentum gyökérelemével kezdődnek. <br>Azon fájlokban, amelyek meg kívánnak felelni a nemzetközi szabványnak, a Suspects (gyanús elemek) értékének „hamisnak” kell lennie (ISO 32000-1:2008, 321. táblázat). <li> A PDF-megjelenítési bővítménynek nincsen gyanús elemekre vonatkozó bejegyzése. Ez a tulajdonság nem kötelező.    |
|    7.2 Szöveg    |                 Támogatva, kivételekkel    |    A tartalmat logikus olvasási sorrendben kell megcímkézni. A dokumentum tartalmának minden logikai eleméhez a szemantikailag leginkább megfelelő címkét kell használni. <br><li> A PDF-megjelenítési bővítmény a tartalmakat logikai olvasási sorrendben címkézi meg, amennyire ez lehetséges.<br>A karakterkódokat Unicode-ra kell leképezni, az ISO 32000-1:2008 14.8.2.4.2-es szakaszában leírtak szerint. Az Unicode-specifikációban nem szereplő karakterek használhatják az Unicode felhasználói karakterek területét, vagy deklarálhatnak egy másik típusú karakterkódolást. <br>A természetes nyelvet az ISO 32000-1:2008 14.9.2-es és/vagy az ISO 32000-1:2008 7.9.2-es szakaszában leírtak alapján kell deklarálni. A természetes nyelv módosításait is deklarálni kell. A természetes nyelv szöveges sztringeken (például a helyettesítő leírásokon) belüli módosításait az ISO 32000-1:2008 14.9.2.2-es szakaszában leírtak alapján, nyelvazonosító használatával kell deklarálni. <br><li> A PDF-megjelenítő bővítmény csak a dokumentum szintjén deklarálja a természetes nyelvet.    |
|    7.3 Grafikák    |                 Támogatva, kivételekkel    |    A grafikus objektumokat – amelyek nem szöveges objektumok – az ISO 32000-1:2008 14.8.4.5-ös szakaszának 340. táblázata szerint Ábra címkével kell megjelölni. Ha a következő kivételek bármelyike igaz, a grafikát összetevőként kell megcímkézni: <br><li> a grafikának nincs értelmezhető tartalma, vagy <li>  háttérként jelenik meg egy hivatkozásjegyzetben. Ebben az esetben a hivatkozás helyettesítő szövegében a grafikát és a hivatkozást is le kell írni. <li> A PDF-megjelenítő bővítmény a grafikus objektumokat az Ábra címkével jelöli meg. <br>Az ábrához tartozó feliratot Felirat címkével kell megjelölni. <li> A PDF-megjelenítő bővítmény jelenleg nem címkézi a feliratokat a Felirat címkével rendelkező ábráknál. <br>Az Ábra címkéknek tartalmaznia kell egy alternatív ábrázolást vagy helyettesítő szöveget, amely az Ábra címkével megjelölt tartalmat mutatja be, az ISO 32000-1:2008 14.7.2-es szakaszának 323. táblázatában leírtaknak megfelelően. <br>**1. megjegyzés** Lásd még: WCAG 2.0, 1.1-es útmutató. <br>Ha egy grafikában szereplő szöveg nem természetes nyelven írott és emberi olvasóknak szánt szöveg, akkor meg kell adni a grafika természetét vagy célját leíró helyettesítő szöveget. <br>**2. megjegyezés** Ilyen nem természetes nyelven írt szövegnek számítanak a típusminták vagy egy nyelv írásrendszerére például szolgáló szövegrészek.   A PDF-megjelenítési bővítmény támogatja az ábrákhoz tartozó helyettesítő szöveget, de azt a felhasználónak kell megadnia. <br>További megjegyzés a BBox attribútummal kapcsolatban: <br><li> A PDF-megjelenítő bővítmény jelenleg nem ír BBox attribútumot. <li> Megkerülő megoldásként manuálisan újra lehet címkézni az illusztrációkat új ábraként vagy összetevőként.    |
|    7.4 Fejlécek    |                 Nem alkalmazható    |    Az RDL semmilyen módon nem támogatja a fejlécek jelölését. A felhasználónak kell a megfelelő módon megcímkéznie őket.    |
|    7.5 Táblázatok    |                 Támogatva, kivételekkel    |    A táblázatoknak táblázatfejléceket kell tartalmazniuk. A táblázat fejléceit az ISO 32000-1:2008 szabvány 337. és 349. táblázatának megfelelően kell címkézni. <br>**1. megjegyezés** A táblázatok tartalmazhatnak oszlopfejléceket, sorfejléceket, vagy mindkettőt. <br>**2. megjegyezés** A táblák struktúrájával kapcsolatos lehető legtöbb információt elérhetővé kell tenni a kisegítő technológia lehető legnagyobb mértékű támogatása érdekében. A fejlécek kulcsfontosságú szerepet játszanak a strukturális információk biztosításában. <br><li> A felhasználónak kell belevennie a fejléceket a táblázatokba. Az RDL és a PDF-megjelenítési bővítmény támogatja a sorfejléceket. <br>  A TH típusú szerkezeti elemeknek Scope (hatókör) attribútummal kell rendelkezni.   <li> A PDF-megjelenítési bővítmény tartalmazza a TH-elemek Scope attribútumát oszlop- és sortagokhoz, de sarokcellákhoz nem.<br>A táblázat címkézési struktúráit csak a logikus sor- és/vagy oszlopkapcsolatokon belül megjelenített tartalmak címkézésére lehet használni.   <li> Ez attól függ, hogy a felhasználó a táblázatok milyen jellegű használata mellett döntött az RDL-ben.    |
|    7.6 Listák    |                 Nem alkalmazható    |    Az RDL nem támogatja a listák megjelölését. Az RDL-ben ezek szerkezetileg egy egyetlen cellás táblázatként jelennek meg. <br>A felhasználónak kell a megfelelő módon átcímkéznie őket.    |
|    7.7 Matematikai kifejezések    |                 Támogatva, kivételekkel    |    Az összes matematikai kifejezést egy Képlet címkén belül kell megadni, az ISO 32000-1:2008 14.8.4.5-ös szakasza alapján, és rendelkezniük kell egy Alt (helyettesítő) attribútummal. <br><li> A PDF-megjelenítési bővítmény jelenleg nem foglalja magában a Képlet címkében szereplő matematikai kifejezéseket. <br>A karakterek Unicode-ra való leképezésével kapcsolatos követelmények az ISO 32000-1:2008 9.10.2-es és a 14.8.2.4-es szakaszában meghatározottak szerint vonatkoznak a matematikai kifejezésekre. <br><li> Ezt támogatja a PDF-megjelenítési bővítmény.    |
|    7.8 Oldalfejlécek és -láblécek    |                 Támogatott    |    A futó fejléceket és élőlábakat oldalszámozási összetevőkként kell azonosítani és Fejléc vagy Lábléc altípusként minősítve, az ISO 32000-1:2008 14.8.2.2.2-es szakaszának 330. táblázata szerint. <br><li> A fejléceket és az élőlábakat a rendszer összetevőkként kezeli és címkézi meg.    |
|    7.9 Megjegyzések és hivatkozások    |                 Nem alkalmazható    |    A PDF-megjelenítési bővítmény nem támogatja a megjegyzések és hivatkozások megjelölését. <br>A felhasználónak kell a megfelelő módon megcímkéznie őket.    |
|    7.10 Opcionális tartalom    |                 Nem alkalmazható    |         |
|    7.11 Beágyazott fájlok    |                 Nem alkalmazható    |         |
|    7.12 Cikkszálak    |                 Nem alkalmazható    |         |
|    7.13 Digitális aláírások    |                 Nem alkalmazható    |         |
|    7.14 Nem interaktív űrlapok    |                 Nem alkalmazható    |         |
|    7.15 XFA    |                 Nem alkalmazható    |         |
|    7.16 Biztonság    |                 Nem alkalmazható    |         |
|    7.17 Navigáció    |                 Támogatott    |    A dokumentumnak tartalmaznia kell egy dokumentumvázlatot, amely megfelel a navigációs célok olvasási sorrendjének és szintjének (ISO 32000-1:2008, 12.3.3). <br><li> Az RDL támogatja a jelentéselemek könyvjelzőit, de a felhasználónak kell kiválasztania ezt a lehetőséget. Ezeket a könyvjelzőket a PDF-megjelenítő bővítmény dokumentumvázlatként rendereli. <br>Ha vannak, akkor a hármas számú PageLabels (ISO 32000-1:2008, 7.7.2, 28. táblázat) bejegyzéseinek szemantikailag megfelelőnek kell lenniük. <br><li> A PDF-megjelenítő bővítmény nem tartalmaz hármas számú PageLabelst.    |
|    7.18 Jegyzetek    |                 Nem alkalmazható    |    Az RDL nem támogatja a jegyzeteket.    |
|    7.21 Betűkészletek    |                 Támogatott    |         |
|    7.21.1 Általános    |                 Támogatott    |         |
|    7.21.2 Betűkészletek típusai    |                 Támogatott    |         |
|    7.21.3 Összetett betűkészletek    |                 Támogatott    |         |
|    7.21.3.1 Általános    |                 Támogatott    |         |
|    7.21 3.2 CIDFonts    |                 Támogatott    |         |
|    7.21.3.3 CMaps    |                 Támogatott    |         |
|    7.21.4 Beágyazás    |                 Támogatott    |         |
|    7.21.4.1 Általános    |                 Támogatott    |         |
|    7.21.4.2 Részhalmaz beágyazása    |                 Támogatott    |         |
|    7.21.5 Betűkészlet-metrikák    |                 Támogatott    |         |
|    7.21.6 Karakterkódolások    |                 Támogatott    |         |
|    7.21.7 Unicode-karaktertérképek    |                 Támogatott    |         |
|    7.21.8 A .notdef betűkép használata    |                 Támogatott    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Megfelelő olvasói követelmények

Nem értelmezhető

## <a name="9--at-requirements"></a>9.  AT-követelmények

Nem értelmezhető

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Következő lépések
[Rendszergazdai áttekintés](admin-handbook-overview.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

