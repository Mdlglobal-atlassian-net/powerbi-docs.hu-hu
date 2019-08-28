---
title: Az SAP HANA használata a Power BI Desktopban
description: Az SAP HANA használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f40ed1b3950ace0b3cb362a22670e98c3ef83112
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985666"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Az SAP HANA használata a Power BI Desktopban
A Power BI Desktoppal mostantól hozzáférhet az **SAP HANA**-adatbázisokhoz. Az **SAP HANA**-adatbázisok használatához telepíteni kell az SAP HANA ODBC-illesztőprogramot a helyi ügyfélszámítógépen, hogy a Power BI Desktop **SAP HANA**-adatkapcsolat megfelelően működjön. Az SAP HANA ODBC-illesztőprogramot az [SAP Software Download Center központból](https://support.sap.com/swdc) töltheti le. Itt keresse meg a Windows rendszerű számítógépekhez készült SAP HANA-ügyfelet. Mivel az **SAP Software Download Center** szerkezete gyakran változik, a helyet nem tudjuk pontosabban meghatározni.

Ha **SAP HANA**-adatbázishoz szeretne csatlakozni, válassza az **Adatok lekérése > Adatbázis > SAP HANA-adatbázis** lehetőséget az alábbi ábrának megfelelően:

![](media/desktop-sap-hana/sap-hana-1.png)

Amikor SAP HANA-adatbázishoz csatlakozik, adja meg a kiszolgáló nevét és a portot *kiszolgáló:port* formátumban – a következő képen látható példában a kiszolgáló neve *ServerXYZ*, a port pedig a *30015-ös* port.

![](media/desktop-sap-hana/sap-hana-2.png)

Ebben a kiadásban az **SAP HANA** [DirectQuery](desktop-directquery-sap-hana.md) módban támogatott a Power BI Desktopban és a Power BI szolgáltatásban, és a **SAP HANA**-adatbázist DirectQuery módban használó jelentéseket tehet közzé és tölthet fel a Power BI szolgáltatásban. A Power BI szolgáltatásban akkor is közzétehet és feltölthet jelentéseket, ha nem **SAP HANA**-adatbázist használ DirectQuery módban.

## <a name="supported-features-for-sap-hana"></a>Az SAP HANA támogatott funkciói
Ebben a kiadásban számos képesség érhető el az **SAP HANA**-hoz, például a következők:

* Az **SAP HANA**-hoz készült Power BI-összekötő az SAP ODBC-illesztőprogramját használja a legjobb felhasználói élményt érdekében
* Az **SAP HANA** a DirectQuery és az importálási lehetőségeket is támogatja
* A Power BI támogatja a HANA-információmodelleket (például az elemzési és számítási nézeteket), és optimalizált navigációval rendelkezik
* Az **SAP HANA** használatával a közvetlen SQL funkciót is használhatja a sor- és oszloptáblázatokhoz való csatlakozáshoz
* Optimalizált navigáció érhető el a HANA-modellekhez
* A Power BI támogatja az **SAP HANA** változóit és bemeneti paramétereit
* HDI-tárolóalapú számítási nézetek
  * A Power BI Desktop 2019. augusztusi kiadása nyilvános előzetes verzióban támogatja a HDI-tárolóalapú számítási nézeteket. A HDI-tárolóalapú számítási nézetek eléréséhez győződjön meg róla, hogy a Power BI-jal használt HANA-adatbázis-felhasználók hozzáféréssel rendelkeznek az elérni kívánt nézeteket tároló HDI-futtatókörnyezet tárolójához. A hozzáférés megadásához létre kell hoznia egy olyan szerepkört, amely engedélyezi a HDI-tárolóhoz való hozzáférést, majd hozzárendelnie a Power BI-jal használt HANA-adatbázis-felhasználóhoz (a felhasználónak emellett engedéllyel kell rendelkeznie a \_SYS\_ BI-séma rendszertábláinak olvasásához is). Az adatbázis-szerepkörök létrehozásának és hozzárendelésének módját a hivatalos SAP-dokumentációban tekintheti meg. [Ez az SAP-blogbejegyzés](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0) jó kiindulópontként szolgálhat.
  * A HDI-alapú számítási nézetekhez tartozó HANA-változók jelenleg rendelkeznek némi korlátozásokkal. Ezek HANA-oldali korlátok, amelyeket az SAP HANA későbbi kiadásaiban orvosolunk. Először is nem alkalmazható HANA-változó egy HDI-tárolóalapú számítási nézet megosztott oszlopain. Ez a korlátozás feloldható, ha a HANA 2 37.02-es vagy újabb, vagy a HANA 2 42-es vagy újabb verziójára frissít. Emellett jelenleg nem jelennek meg a Power BI felhasználói felületén a változók és paraméterek alapértelmezett értékei. Ezt is az SAP HANA egy hibája okozza, azonban ehhez még nem várható javítás.

## <a name="limitations-of-sap-hana"></a>Az SAP HANA korlátozásai
Az **SAP HANA** használatára a következő néhány korlátozás vonatkozik:

* Az NVARCHAR sztringeket a rendszer legfeljebb 4000 Unicode karakter hosszúságúra csonkolja
* A SMALLDECIMAL nem támogatott
* A VARBINARY nem támogatott
* Az érvényes dátumok 1899/12/30 és 9999/12/31 közöttiek


## <a name="next-steps"></a>Következő lépések
Az SAP HANA-val és a DirectQueryvel kapcsolatos további információkért tekintse meg az alábbi forrásanyagokat:

* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [Az SAP HANA titkosításának engedélyezése](desktop-sap-hana-encryption.md)


