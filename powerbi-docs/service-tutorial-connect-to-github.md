---
title: 'Oktatóanyag: Csatlakozás GitHub-mintához a Power BI segítségével'
description: Ebben az oktatóanyagban valódi, GitHub szolgáltatásbeli adatokhoz csatlakozhat a Power BI segítségével, és automatikusan hozhat létre Power BI-irányítópultokat és -jelentéseket.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.component: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 05/17/2018
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 88be0aa477b5e4b2df4f53c42dfb6fde3dda0184
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900497"
---
# <a name="tutorial-connect-to-a-github-sample-with-power-bi"></a>Oktatóanyag: Csatlakozás GitHub-mintához a Power BI segítségével
Ebben az oktatóanyagban valódi, GitHub szolgáltatásbeli adatokhoz csatlakozhat a Power BI segítségével, és automatikusan hozhat létre Power BI-irányítópultokat és -jelentéseket. A Power BI nyilvános adattárához (más néven *tárházához*) fog csatlakozni, hogy megállapíthassa, hány közreműködő dolgozik a nyilvános Power BI-tartalmakon, kik a fő közreműködők, a hét mely napján történik a legtöbb közreműködés, és így tovább. 

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

- Hozzon létre egy [GitHub-fiókot](https://docs.microsoft.com/contribute/get-started-setup-github)


## <a name="how-to-connect"></a>Csatlakozás
1. Jelentkezzen be a Power BI szolgáltatásba (http://powerbi.com). 
2. A bal oldali navigációs panelen válassza az **Alkalmazások** ikont, majd az **Alkalmazások letöltése** lehetőséget.
   
   ![Power BI – Alkalmazások letöltése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Válassza az **Alkalmazások** lehetőséget, írja be a **github** szöveget a keresőmezőbe, majd válassza a **Letöltés most** gombot.
   
   ![Power BI – a GitHub alkalmazás letöltése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-get-it-now.png) 

4. Adja meg az adattár nevét és tulajdonosát. Az adattár URL-címe https://github.com/MicrosoftDocs/powerbi-docs, az **Adattár tulajdonosa** a **MicrosoftDocs**, az **Adattár** neve pedig **powerbi-docs**. 
   
    ![Power BI – GitHub adattár neve](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-repo-name.png)

5. Adja meg a GitHub-fiókja hitelesítő adatait. Előfordulhat, hogy a Power BI kihagyja ezt a lépést, ha korábban már bejelentkezett a GitHubba a böngészőjében. 

6. A **Hitelesítési módszer** beállításánál válassza az **oAuth2** \> **Bejelentkezés** lehetőséget.

7. Kövesse a GitHub-hitelesítés lépéseit. Engedélyezze a Power BI-nak a GitHub-adatok elérését.
   
   A Power BI ezután már képes elérni a GitHub szolgáltatást az adatok beolvasásához.  Az adatok naponta egyszer frissülnek.

8. Miután a Power BI importálta az adatokat, megjelenik az új GitHub csempe. 
 
   ![Power BI – GitHub csempe](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tile.png) 

8. Válassza a globális navigációs ikont a bal oldali navigációs panel kis méretűre állításához, hogy több szabad hely legyen a képernyőn.

    ![Globális navigációs ikon](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Válassza a 8. lépésben létrehozott GitHub csempét. 
    
    Ekkor megnyílik a GitHub-irányítópult. Ezek élő adatok, ezért az Ön által látott értékek eltérhetnek az itt szemléltetettől.

    ![GitHub-irányítópult a Power BI-ban](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-dashboard.png)

    

## <a name="ask-a-question"></a>Kérdés feltevése

11. Vigye a kurzort a **Tegyen fel kérdést az adataival kapcsolatban** területre, majd válassza a **pull requests** (lekéréses kérelmek) lehetőséget. 

    ![Power BI – Tegyen fel kérdést az adataival kapcsolatban](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-ask-question.png)

12. Írja be a **by month** (hónap szerint) szöveget.
 
    ![Lekéréses kérelmek hónap szerint](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-ask-question-by-month.png)

     A Power BI ekkor létrehoz egy sávdiagramot, melyen látható a lekéréses kérelmek száma hónap szerint.

13. Válassza a **Kilépés a Q&A részből** lehetőséget.

## <a name="view-the-github-report"></a>GitHub-jelentés megtekintése 

1. Válassza a GitHub-irányítópulton a kombinált **Pull Requests by Month** (Lekéréses kérelmek hónapok szerint) oszlop- és sávdiagramot a vonatkozó jelentés megnyitásához.

    ![Lekéréses kérelmek hónapok szerint kombinált diagram](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-pull-requests-combo-chart.png)

2. Válasszon egy felhasználónevet a **Total pull requests by user** (Lekéréses kérelmek összesen felhasználónként) diagramban, és láthatja, az alábbi képen szemléltetett módon, hogy az adott felhasználóhoz márciusban az átlagosnál több óra tartozik.

    ![Power BI – Kiemelés a GitHub-jelentésben](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-report-highlight.png)

3. Válassza a **Punch Card** (Pontgyűjtés) fület a jelentés következő lapjának megtekintéséhez. 
 
    ![Power BI – GitHub-jelentés Punch Card lapja](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Úgy tűnik, hogy kedd 15 óra az a leggyakoribb nap és időpont, amikor a felhasználók *véglegesítik* a munkájukat, azaz beadják az általuk végzett módosításokat.

## <a name="clean-up-resources"></a>Erőforrások felszabadítása

Most, hogy befejezte ezt az oktatóanyagot, törölheti a GitHub alkalmazást. 

1. A bal oldali navigációs sávon válassza az **Alkalmazások** lehetőséget.
2. Vigye a mutatót a GitHub csempe fölé, és válassza a **Törlés** lehetőséget.

    ![A GitHub alkalmazás törlése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Következő lépések

Ebben az oktatóanyagban csatlakozott egy nyilvános GitHub-adattárhoz, és beolvasta az adatokat, melyeket a Power BI irányítópultként és jelentésként formázott. Ezután megválaszolt néhány kérdést az adatokkal kapcsolatban az irányítópult és a jelentés felfedezésével. Folytatásként megismerheti, hogy hogyan csatlakozhat más szolgáltatásokhoz, mint például a Salesforce, a Microsoft Dynamics és a Google Analytics. 
 
> [!div class="nextstepaction"]
> [Kapcsolódás online szolgáltatásokhoz](service-connect-to-services.md)


