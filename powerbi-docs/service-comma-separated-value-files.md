---
title: Adatok lekérdezése vesszővel tagolt (.CSV) fájlokból
description: Ismerje meg, hogy miképpen kérdezhet le adatokat .CSV-fájlokból a Power BI-ban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1a150c2cb4eb819b78b2b08a492087eb98bf6363
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513340"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Adatok lekérdezése vesszővel tagolt (.CSV) fájlokból
![](media/service-comma-separated-value-files/csv_icon.png)

A gyakran .CSV néven emlegetett, vesszővel tagolt értékfájlok adatsorokból álló egyszerű szövegfájlok, amelyekben az egyes értékeket vesszők választják el egymástól. Az ilyen típusú fájlok viszonylag kis fájlméretben nagy mennyiségű adatot tárolhatnak, ezért ideális adatforrást jelentenek a Power BI számára. [Innen](http://go.microsoft.com/fwlink/?LinkID=619356) letölthet egy .CSV-mintafájlt.

Ha már rendelkezik .CSV-fájllal, itt az ideje, hogy adatkészletként csatlakoztassa a Power BI-webhelyhez, ahol elemezheti az adatokat, irányítópultokat hozhat létre, és másokkal is megoszthatja az elemzéseket.

>[!TIP]
>Számos cég naponta friss adatokat tartalmazó .CSV-fájlokat bocsát ki. Annak érdekében, hogy a Power BI-beli adatkészlet a frissített fájllal is szinkronizálva legyen, gondoskodjon róla, hogy a fájl ugyanazon a néven legyen mentve a OneDrive-on.

## <a name="where-your-file-is-saved-makes-a-difference"></a>Nem mindegy, hogy hol menti a fájlokat
**Helyi meghajtó** – Ha a .CSV-fájlt a saját számítógépén vagy a cég egy másik helyszíni gépén mentette, a Power BI-ból *importálhatja* a fájlt a Power BI-ba. Mivel a fájl ténylegesen a helyi meghajtón marad, a teljes fájl valójában nem kerül a Power BI-ba. Ehelyett az történik, hogy a Power BI-ban új adatkészlet jön létre, és ebbe töltődnek a .CSV-fájlból származó adatok.

**OneDrive – Vállalati verzió** – A leghatékonyabb megoldás a .CSV-fájl, az adatbázis, a jelentések és az irányítópultok szinkronban tartásához, ha rendelkezik OneDrive Vállalati verzióval, és oda a Power BI-hoz használt fiókkal jelentkezik be. Mivel a Power BI és a OneDrive egyaránt a felhőben található, a Power BI nagyjából óránként *kapcsolódik* a OneDrive-on található fájlhoz. Ha a rendszer bármilyen változást érzékel, az adatbázis, a jelentések és az irányítópultok automatikusan frissülnek a Power BI-ban.

**OneDrive – személyes** – Ha a saját OneDrive-fiókjába menti a fájlokat, számos olyan előnyre tehet szert, mint a OneDrive Vállalati verziójának használatakor. A legnagyobb különbség az, hogy amikor a fájlt először csatlakoztatja (Get Data > Files > OneDrive – Personal) akkor a Microsoft-fiókjával kell a OneDrive-ba jelentkeznie, és ez általában nem ugyanaz, mint amit a Power BI-ba való belépéshez használ. Ha a Microsoft-fiókkal jelentkezik be a OneDrive-ba, mindenképpen válassza a Maradjak bejelentkezve lehetőséget. Így a Power BI képes lesz nagyjából óránként kapcsolódni a fájlhoz, és ellenőrizni, hogy szinkronban van-e a Power BI-ban lévő adatkészlettel.

**SharePoint – csoportwebhelyek** – A Power BI Desktop-fájlok SharePoint – csoportwebhelyekre való mentése sokban hasonlít a OneDrive Vállalati verziójába való mentéshez. A legnagyobb különbség a fájlhoz a Power BI-ból való csatlakozás módja. Ehhez megadhat egy URL-címet, vagy csatlakozhat a gyökérmappához.

## <a name="import-or-connect-to-a-csv-file"></a>.CSV-fájl importálása vagy csatlakoztatása
>[!IMPORTANT]
>A Power BI-ba maximálisan 1 GB méretű fájl importálható.

1. A Power BI navigációs ablaktábláján kattintson az **Adatok lekérdezése** elemre.
   
   ![](media/service-comma-separated-value-files/csv_get_data_button.png)
2. A **Fájlok** lapon kattintson a **Beolvasás** elemre.
   
   ![](media/service-comma-separated-value-files/csv_files_get.png)
3. Keresse meg a fájlt.
   
   ![](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>További lépések
**Adatok elemzése** – Ha a fájl adatai már bekerültek a Power BI rendszerébe, ideje megvizsgálni őket. A jobb gombbal kattintson az új adatkészletre, majd kattintson az **Explore** (Vizsgálat) elemre.

**Ütemezett frissítés** – Ha a fájlt helyi meghajtón mentette, az ütemezett frissítés beállításával biztosíthatja, hogy a Power BI-ban tárolt adatkészlet és a jelentések naprakészek maradjanak. További tudnivalókért lásd: [Adatfrissítés a Power BI-ban](refresh-data.md). Ha a fájlt a OneDrive-on mentette, a Power BI nagyjából óránként automatikusan szinkronizál vele.

