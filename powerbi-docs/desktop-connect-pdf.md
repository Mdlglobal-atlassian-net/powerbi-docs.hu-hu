---
title: Csatlakozás PDF-fájlhoz a Power BI Desktopban (előzetes verzió)
description: Egyszerű csatlakozás PDF-fájlokhoz, és az azokban tárolt adatok használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: fe13e5776648342aa4f7e86dce657e6ffcca11b9
ms.sourcegitcommit: c51461690e8faa121a1325957ca79b7a3975e8b8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/12/2018
ms.locfileid: "44512925"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop-preview"></a>Csatlakozás PDF-fájlhoz a Power BI Desktopban (előzetes verzió)
A Power BI Desktopban csatlakozhat egy **PDF-fájlhoz**, és úgy használhatja a fájlban lévő adatokat, mint a Power BI Desktop bármely más adatforrását.

![Csatlakozás PDF-fájlban lévő adatokhoz](media/desktop-connect-pdf/connect-pdf_04.png)

A következő bekezdések a **PDF-fájlhoz** való csatlakozást, az adatok kijelölését és az adatoknak a **Power BI Desktopba** való beolvasását ismertetik.

## <a name="enable-the-pdf-connector"></a>A PDF-összekötő engedélyezése
A PDF-összekötő előzetes verzióban érhető el a **Power BI Desktophoz**, ezért engedélyezni kell. A PDF-összekötő engedélyezéséhez válassza a **Fájl > Lehetőségek és beállítások > Lehetőségek > Előzetes funkciók** menüpontot, majd jelölje be az **Adatok beolvasása PDF-fájlokból** elem melletti jelölőnégyzetet. 

![A PDF-összekötő engedélyezése a Beállítások > Előzetes funkciók lehetőséggel](media/desktop-connect-pdf/connect-pdf_01.png)

Miután ezt beállította, újra kell indítania a **Power BI Desktopot**.

A **PDF- (bétaverzió)** összekötő első használatakor figyelmeztetést kap arról, hogy a PDF-összekötő fejlesztés alatt áll, és a jövőben módosulhat. Az összekötő használatához válassza a **Tovább** lehetőséget.

Javasoljuk, hogy mindig frissítsen a **Power BI Desktop** legújabb verziójára, amelyet a [Power BI Desktop beszerzése](desktop-get-the-desktop.md) hivatkozással érhet el. 

## <a name="connect-to-a-pdf-file"></a>Csatlakozás PDF-fájlhoz
Ha csatlakozni kíván egy **PDF-fájlhoz**, válassza az **Adatok lekérése** lehetőséget a Power BI Desktop **Kezdőlap** menüszalagján. A bal oldali kategóriák közül válassza az **Fájl** lehetőséget, ekkor megjelenik a **PDF (bétaverzió)**.

![PDF kiválasztása az Adatok lekérésénél](media/desktop-connect-pdf/connect-pdf_01.png)

A rendszer megkéri, hogy adja meg a használni kívánt PDF-fájl helyét. Ha megadta a fájl helyét, és a PDF-fájl be lett töltve, megjelenik a **Kezelő** ablaka, és megjeleníti a fájlban elérhető adatokat. Ezek közül kiválaszthat egy vagy több importálni kívánt elemet, és használhatja őket a **Power BI Desktopban**.

![Csatlakozás PDF-fájlban lévő adatokhoz](media/desktop-connect-pdf/connect-pdf_04.png)

A PDF-fájlban felderített elemek melletti jelölőnégyzet bejelölésével azok megjelennek a jobb oldali panelen. Ha kész az importálásra, válassza a **Betöltés** gombot az adatoknak a **Power BI Desktopba** töltéséhez.


## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   

