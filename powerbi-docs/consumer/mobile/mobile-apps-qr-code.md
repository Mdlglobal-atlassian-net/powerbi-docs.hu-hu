---
title: Power BI QR-kód beolvasása mobileszközzel
description: A Power BI-ban lévő QR-kódok a való világból bármit közvetlenül összekapcsolhatnak az iPhone-okhoz vagy Android-eszközökhöz készült Power BI mobilalkalmazás kapcsolódó BI-információival.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: painbar
ms.openlocfilehash: 55b71508380a424ba48e4d24ac6c6fc70d9a570d
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802072"
---
# <a name="scan-a-power-bi-qr-code-from-your-mobile-device"></a>Power BI QR-kód beolvasása mobileszközzel
A következőkre vonatkozik:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPadek](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android rendszerű telefon](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android rendszerű táblagép](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone-ok |iPadek |Android rendszerű telefonok |Android rendszerű táblagépek |

A Power BI-ban lévő QR-kódok a való világból bármit közvetlenül összekapcsolhatnak a kapcsolódó BI-információkkal, és ehhez nincs szükség navigálásra vagy keresésre.

Tegyük fel, hogy egy kollégája [létrehozott egy QR-kódot a Power BI szolgáltatásban](../../service-create-qr-code-for-tile.md) egy jelentéshez vagy egy irányítópult valamely csempéjéhez, majd megosztotta Önnel az irányítópultot vagy a jelentést, a QR-kódot pedig elhelyezte a kívánt helyen, például egy e-mailben vagy valamilyen tárgyon. 

A Power BI alkalmazás beolvasó funkciójával vagy a telefonra telepített bármely egyéb olvasóval beolvashatja a QR-kódot, és ezáltal azonnal, közvetlenül a telefonjáról érheti el a vonatkozó csempét vagy jelentést. 

Ha kollégája nem osztotta meg Önnel az irányítópultot vagy jelentést, közvetlenül a mobilalkalmazásból kérhet hozzáférést. 

> [!NOTE]
> [A jelentés QR-kódját a Power BI vegyes valósághoz alkalmazással is beolvashatja](mobile-mixed-reality-app.md#scan-a-report-qr-code-in-holographic-view).

## <a name="scan-a-power-bi-qr-code-on-your-iphone-with-the-power-bi-scanner"></a>Power BI QR-kód beolvasása iPhone-on a Power BI-olvasóval

1. A navigációs sávon koppintson a **további beállítások** (...) lehetőségre, majd a **Vizsgálat** elemre.

    ![](media/mobile-apps-qr-code/power-bi-scanner.png)

2. Ha a kamera nincs engedélyezve, engedélyeznie kell, hogy a Power BI alkalmazás használhassa azt. Ezt csak egyszer kell megtennie. 
 
3. Irányítsa az olvasót a Power BI QR-kódra. 
   
    ![](media/mobile-apps-qr-code/power-bi-align-qr-code.png)
4. A csempe vagy jelentés háttér előtt lebegve jelenik meg a kiterjesztett valóságban.
   
    ![](media/mobile-apps-qr-code/power-bi-ios-qr-ar-scanner.png)

5. Koppintson a jelentésre vagy a csempére annak Fókusz módban való megnyitásához, vagy lépjen vissza az olvasóra.

### <a name="scan-a-qr-code-from-an-external-scanner-on-your-iphone"></a>QR-kód beolvasása az iPhone-on lévő külső olvasóval
1. A telefonra telepített bármely olvasó használatával a kamerát egy adott Power BI QR-kódra irányítva azonnal elérheti a vonatkozó csempét vagy jelentést. 
2. Ha a Power BI alkalmazás nincs telepítve, a rendszer átirányítja az [Apple App Store áruházba, ahonnan letöltheti azt](https://go.microsoft.com/fwlink/?LinkId=522062) iPhone készülékére.

## <a name="scan-a-power-bi-qr-code-on-your-android-device-with-the-power-bi-scanner"></a>Power BI QR-kód beolvasása Android-eszközön a Power BI-olvasóval

1. A navigációs sávon koppintson a **további beállítások** (...) lehetőségre, majd a **Vizsgálat** elemre.

    ![](media/mobile-apps-qr-code/power-bi-scanner.png)

2. Ha a kamera nincs engedélyezve, engedélyeznie kell, hogy a Power BI alkalmazás használhassa azt. Ezt csak egyszer kell megtennie. 

3. Irányítsa az olvasót a Power BI QR-kódra. 
   
    ![](media/mobile-apps-qr-code/pbi_iph_qrscan.png)
4. A csempe vagy jelentés automatikusan megnyílik a Power BI alkalmazásban.
   
    ![](media/mobile-apps-qr-code/power-bi-android-tile.png)

### <a name="scan-a-qr-code-from-an-external-scanner-on-your-android-device"></a>QR-kód beolvasása az Android-eszközön lévő külső olvasóval
1. Az Android-eszközön telepített bármely olvasó használatával a kamerát egy adott Power BI QR-kódra irányítva azonnal elérheti a vonatkozó csempét vagy jelentést. 
2. Ha a Power BI alkalmazás nincs telepítve, a rendszer átirányítja a [Google Play áruházba, ahonnan letöltheti azt](https://go.microsoft.com/fwlink/?LinkID=544867). 

## <a name="next-steps"></a>Következő lépések
* [Power BI-információk elérése a való világból](mobile-apps-data-in-real-world-context.md) a mobilalkalmazásokkal
* [QR-kód létrehozása a Power BI szolgáltatásban lévő csempékhez](../../service-create-qr-code-for-tile.md)
* [QR-kód létrehozása a Power BI szolgáltatásban lévő jelentésekhez](../../service-create-qr-code-for-report.md)
* [QR-kódot a Power BI vegyes valósághoz alkalmazással is beolvashat](mobile-mixed-reality-app.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

