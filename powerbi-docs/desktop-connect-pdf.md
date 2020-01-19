---
title: Csatlakozás PDF-fájlhoz a Power BI Desktopban
description: Egyszerű csatlakozás PDF-fájlokhoz, és az azokban tárolt adatok használata a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3d3afa28119a0924356491226bf0baf6e7bb228b
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761611"
---
# <a name="connect-to-pdf-files-in-power-bi-desktop"></a>Csatlakozás PDF-fájlokhoz a Power BI Desktopban
A Power BI Desktopban csatlakozhat egy **PDF-fájlhoz**, és úgy használhatja a fájlban lévő adatokat, mint a Power BI Desktop bármely más adatforrását.

![Csatlakozás PDF-fájlban lévő adatokhoz](media/desktop-connect-pdf/connect-pdf-04.png)

A következő bekezdések a **PDF-fájlhoz** való csatlakozást, az adatok kijelölését és az adatoknak a **Power BI Desktopba** való beolvasását ismertetik.

Javasoljuk, hogy mindig frissítsen a **Power BI Desktop** legújabb verziójára, amelyet a [Power BI Desktop beszerzése](desktop-get-the-desktop.md) hivatkozással érhet el. 

## <a name="connect-to-a-pdf-file"></a>Csatlakozás PDF-fájlhoz
Ha csatlakozni kíván egy **PDF-fájlhoz**, válassza az **Adatok lekérése** lehetőséget a Power BI Desktop **Kezdőlap** menüszalagján. A bal oldali kategóriák közül válassza az **Fájl** lehetőséget, ekkor megjelenik a **PDF**.

![PDF kiválasztása az Adatok lekérésénél](media/desktop-connect-pdf/connect-pdf-01.png)

A rendszer megkéri, hogy adja meg a használni kívánt PDF-fájl helyét. Ha megadta a fájl helyét, és a PDF-fájl be lett töltve, megjelenik a **Kezelő** ablaka, és megjeleníti a fájlban elérhető adatokat. Ezek közül kiválaszthat egy vagy több importálni kívánt elemet, és használhatja őket a **Power BI Desktopban**.

![Csatlakozás PDF-fájlban lévő adatokhoz](media/desktop-connect-pdf/connect-pdf-04.png)

A PDF-fájlban felderített elemek melletti jelölőnégyzet bejelölésével azok megjelennek a jobb oldali panelen. Ha kész az importálásra, válassza a **Betöltés** gombot az adatoknak a **Power BI Desktopba** töltéséhez.

A **Power BI Desktop** 2018. novemberi kiadásától kezdve a PDF-kapcsolat választható paramétereként megadható a **Start page** (kezdőoldal) és az **End page** (utolsó oldal). Ezek a paraméterek az M képletnyelven is megadhatók az alábbi formátumban:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`


## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   

