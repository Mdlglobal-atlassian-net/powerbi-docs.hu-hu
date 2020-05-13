---
title: Az SAP HANA használata a Power BI Desktopban
description: Az SAP HANA használata a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83289120"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Kapcsolódás SAP HANA-adatbázisokhoz aPower BI Desktopban

A Power BI Desktoppal mostantól hozzáférhet az *SAP HANA*-adatbázisokhoz. Az SAP HANA-adatbázisok használatához telepíteni kell az SAP HANA ODBC-illesztőprogramot a helyi ügyfélszámítógépen, hogy a Power BI Desktop SAP HANA-adatkapcsolat megfelelően működjön. Az SAP HANA-ügyféleszközöket az [SAP fejlesztési eszközök](https://tools.hana.ondemand.com/#hanatools) területről töltheti le, ahol megtalálható a szükséges ODBC-illesztő. Másik lehetőségként az [SAP Software Download Centerből](https://support.sap.com/en/my-support/software-downloads.html) is letöltheti. A Software portálon keresse meg a Windows rendszerű számítógépekhez készült *SAP HANA CLIENT* ügyfelet. Mivel az SAP Software Download Center szerkezete gyakran változik, a helyet nem tudjuk pontosabban meghatározni.

SAP HANA-adatbázishoz való kapcsolódáshoz válassza az **Adatok beolvasása** lehetőséget, az **Adatbázis** > **SAP HANA-adatbázis** elemet, majd a **Csatlakozás** lehetőséget:

![SAP HANA-adatbázis, Adatok beolvasása párbeszédpanel, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

SAP HANA-adatbázishoz való kapcsolódáskor adja meg a kiszolgáló nevét. Ez után adja meg a portot a legördülő listában és a beviteli mezőben.

Abban a kiadásban a [DirectQuery](desktop-directquery-sap-hana.md) módú SAP HANA támogatott a Power BI Desktopban és a Power BI szolgáltatásban. Olyan jelentéseket is közzétehet és feltölthet a Power BI szolgáltatásba, amelyek DirectQuery módban használják az SAP HANA-t. A Power BI szolgáltatásban akkor is közzétehet és feltölthet jelentéseket, ha nem SAP HANA-adatbázist használ DirectQuery módban.

## <a name="supported-features-for-sap-hana"></a>Az SAP HANA támogatott funkciói

Ebben a kiadásban számos képesség érhető el az SAP HANA-hoz, például a következők:

* Az SAP HANA-hoz készült Power BI-összekötő az SAP ODBC-illesztőprogramját használja a legjobb felhasználói élményt érdekében.

* Az SAP HANA a DirectQuery és az importálás módot is támogatja.

* A Power BI támogatja a HANA-információmodelleket, például az elemzési és számítási nézeteket, és optimalizált navigációval rendelkezik.

* Az SAP HANA használatával a közvetlen SQL funkciót is használhatja a sor- és oszloptáblázatokhoz való csatlakozáshoz.

* A Power BI-ban optimalizált navigáció érhető el a HANA-modellekhez.

* A Power BI támogatja az SAP HANA változóit és bemeneti paramétereit.

* A Power BI támogatja a HDI-tárolóalapú számítási nézeteket.

  * A Power BI Desktop 2019. augusztusi kiadása nyilvános előzetes verzióban támogatja a HDI-tárolóalapú számítási nézeteket. A HDI-tárolóalapú számítási nézetek eléréséhez győződjön meg róla, hogy a Power BI-jal használt HANA-adatbázis-felhasználók hozzáféréssel rendelkeznek az elérni kívánt nézeteket tároló HDI-futtatókörnyezet tárolójához. A hozzáférés megadásához hozzon létre olyan szerepkört, amely engedélyezi a HDI-tároló elérését. Ezt a szerepkört aztán rendelje hozzá a HANA-adatbázis Power BI-ban használni kívánt felhasználójához. (Ennek a felhasználónak a megszokott módon a \_SYS\_BI séma rendszertáblaira vonatkozó olvasási engedéllyel is rendelkeznie kell.) Az adatbázis-szerepkörök létrehozásának és hozzárendelésének módját a hivatalos SAP-dokumentációban tekintheti meg. [Ez az SAP-blogbejegyzés](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) jó kiindulópontként szolgálhat.

  * A HDI-alapú számítási nézetekhez tartozó HANA-változókra jelenleg érvényben van néhány korlátozás. A korlátozásokat a HANA oldalán fennálló hibák indokolják.
  
    Először is nem alkalmazható HANA-változó egy HDI-tárolóalapú számítási nézet megosztott oszlopain. A korlátozás feloldásához frissítsen a HANA 2 37.02-es vagy újabb, vagy a HANA 2 42-es vagy újabb verziójára. Emellett jelenleg nem jelennek meg a Power BI felhasználói felületén a változók és paraméterek alapértelmezett értékei. Ezt a korlátozás az SAP HANA egy hibája indokolja, de az SAP egyelőre nem jelentett be javítást.

## <a name="limitations-of-sap-hana"></a>Az SAP HANA korlátozásai

Az SAP HANA használatára a következő néhány korlátozás vonatkozik:

* Az NVARCHAR sztringeket a rendszer legfeljebb 4000 Unicode karakter hosszúságúra csonkolja.
* A SMALLDECIMAL nem támogatott.
* A VARBINARY nem támogatott.
* Az érvényes dátumok 1899/12/30 és 9999/12/31 közöttiek.

## <a name="next-steps"></a>Következő lépések

Az SAP HANA-val és a DirectQueryvel kapcsolatos további információkat talál az alábbi forrásanyagokban:

* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [Adatforrások a Power BI-hoz](power-bi-data-sources.md)
* [Az SAP HANA titkosításának engedélyezése](desktop-sap-hana-encryption.md)
