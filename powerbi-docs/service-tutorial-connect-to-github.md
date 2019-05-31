---
title: 'Oktatóanyag: Csatlakozás egy GitHub-adattárat a Power bi-JAL'
description: Ebben az oktatóanyagban valódi, GitHub szolgáltatásbeli adatokhoz csatlakozhat a Power BI segítségével, és automatikusan hozhat létre Power BI-irányítópultokat és -jelentéseket.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578631"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Oktatóanyag: Csatlakozás egy GitHub-adattárat a Power bi-JAL
Ebben az oktatóanyagban valódi, GitHub szolgáltatásbeli adatokhoz csatlakozhat a Power BI segítségével, és automatikusan hozhat létre Power BI-irányítópultokat és -jelentéseket. Csatlakozás a Power BI tartalom nyilvános adattár (más néven egy *tárház*), és tekintse meg hasonló kérdések: Hány közreműködő dolgozik a nyilvános Power BI-tartalmon? kik a fő közreműködők, a hét mely napján történik a legtöbb közreműködés, És további kérdések. 

![GitHub-jelentés a Power BI szolgáltatásban](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

A jelen oktatóanyagban az alábbi lépéseket fogja végrehajtani:

> [!div class="checklist"]
> * GitHub-fiók létrehozása, ha még nincs fiókja 
> * Bejelentkezés a Power BI-fiókjába, vagy regisztrálás, ha még nincs fiókja
> * A Power BI szolgáltatás megnyitása
> * A GitHub alkalmazás megkeresése
> * Adatok megadása a Power BI nyilvános GitHub-adattárának eléréséhez
> * A GitHub-adatokból készült irányítópult és jelentés megtekintése
> * Erőforrások felszabadítása az alkalmazás törlésével

Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="prerequisites"></a>Előfeltételek

Az oktatóanyag követéséhez létre kell hoznia egy GitHub-fiókot, ha nincs még fiókja. 

- Regisztráljon egy [GitHub-fiók](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Csatlakozás
1. Jelentkezzen be a Power BI szolgáltatásba (https://app.powerbi.com). 
2. A bal oldali navigációs panelen válassza az **Alkalmazások** ikont, majd az **Alkalmazások letöltése** lehetőséget.
   
   ![Power BI – Alkalmazások letöltése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Válassza ki **alkalmazások**, típus **GitHub** kifejezést a keresőmezőbe > **Letöltés most**.
   
   ![Power BI – a GitHub alkalmazás letöltése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. A **a Power BI-alkalmazás telepítése?** kiválasztása **telepítése**.
5. A **készen áll az új alkalmazás**válassza **Ugrás az appra**.
6. A **az új alkalmazás használatának első lépései**válassza **adatok**.

    ![Első lépések az új alkalmazással](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. Adja meg az adattár nevét és tulajdonosát. Az adattár URL-címe https://github.com/MicrosoftDocs/powerbi-docs, az **Adattár tulajdonosa** a **MicrosoftDocs**, az **Adattár** neve pedig **powerbi-docs**. 
   
    ![Power BI – GitHub adattár neve](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Adja meg a GitHub-fiókja hitelesítő adatait. Előfordulhat, hogy a Power BI kihagyja ezt a lépést, ha korábban már bejelentkezett a GitHubba a böngészőjében. 

6. A **hitelesítési módszer**, tartsa **oAuth2** kiválasztott \> **bejelentkezés**.

7. Kövesse a GitHub-hitelesítés lépéseit. Engedélyezze a Power BI-nak a GitHub-adatok elérését.
   
   A Power BI ezután már képes elérni a GitHub szolgáltatást az adatok beolvasásához.  Az adatok naponta egyszer frissülnek.

8. Miután a Power BI importálta az adatokat, láthatja a tartalmát az új GitHub-munkaterületet. 
9. A bal oldali navigációs sávon válassza ki a munkaterület neve melletti nyílra. Megjelenik a munkaterület tartalmaz egy irányítópultot és jelentést. 

    ![A bal oldali navigációs ablaktáblán található alkalmazás](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Válassza ki az irányítópult neve melletti három pontra (...) > **átnevezése** > típus **GitHub-irányítópult**.
 
    ![Power BI – GitHub csempe](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Válassza a globális navigációs ikont a bal oldali navigációs panel kis méretűre állításához, hogy több szabad hely legyen a képernyőn.

    ![Globális navigációs ikon](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Válassza ki a GitHub-irányítópult.
    
    A GitHub-irányítópult élő adatokat tartalmaz, így láthatja a értékei eltérhetnek.

    ![GitHub-irányítópult a Power BI-ban](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Kérdés feltevése

1. Helyezze a kurzort **tegyen fel kérdést az adataival kapcsolatban**. Power bi-ban **kérdések az első lépéseket**. 

1. Válassza ki **hány felhasználó vannak-e**.
 
    ![Hány felhasználó vannak-e](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. A kettő között **hány** és **felhasználók vannak-e**, típus **lekéréses kérelmek /** . 

     A Power BI létrehoz egy főre jutó pull-kérelmek számát megjelenítő oszlopdiagram.

    ![Felhasználónként hány lekéréses kérelmek vannak-e](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Válassza ki a PIN-kódot, majd rögzítheti az irányítópulton **Kilépés a Q & A**.

## <a name="view-the-github-report"></a>GitHub-jelentés megtekintése 

1. A GitHub-irányítópulton, válassza ki az oszlopdiagram **lekéréses kérelmek hónap szerint** nyissa meg a kapcsolódó jelentést.

    ![Lekéréses kérelmek hónap oszlopdiagram szerint](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Válassza ki a felhasználót a a **lekéréses kérelmek összesen felhasználó** diagram. Ebben a példában látható a órában a legtöbb februárban volt.

    ![Power BI – Kiemelés a GitHub-jelentésben](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Válassza a **Punch Card** (Pontgyűjtés) fület a jelentés következő lapjának megtekintéséhez. 
 
    ![Power BI – GitHub-jelentés Punch Card lapja](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Kártevőnek "frissítő kedd" du. 3:, a legtöbb közös idő és a hét napját *véglegesítések*, ha a személyek ellenőrizze a munkájukat.

## <a name="clean-up-resources"></a>Erőforrások felszabadítása

Most, hogy befejezte ezt az oktatóanyagot, törölheti a GitHub alkalmazást. 

1. A bal oldali navigációs sávon válassza az **Alkalmazások** lehetőséget.
2. Vigye a mutatót a GitHub csempe fölé, és válassza a **Törlés** lehetőséget.

    ![A GitHub alkalmazás törlése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Következő lépések

Ebben az oktatóanyagban csatlakozott egy nyilvános GitHub-adattárhoz, és beolvasta az adatokat, melyeket a Power BI irányítópultként és jelentésként formázott. Ezután megválaszolt néhány kérdést az adatokkal kapcsolatban az irányítópult és a jelentés felfedezésével. Folytatásként megismerheti, hogy hogyan csatlakozhat más szolgáltatásokhoz, mint például a Salesforce, a Microsoft Dynamics és a Google Analytics. 
 
> [!div class="nextstepaction"]
> [Kapcsolódás online szolgáltatásokhoz](service-connect-to-services.md)


