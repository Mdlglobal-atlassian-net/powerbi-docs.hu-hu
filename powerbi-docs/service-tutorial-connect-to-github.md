---
title: 'Oktatóanyag: Csatlakozás GitHub-adattárhoz a Power BI segítségével'
description: Ebben az oktatóanyagban valódi, GitHub szolgáltatásbeli adatokhoz csatlakozhat a Power BI segítségével, és automatikusan hozhat létre Power BI-irányítópultokat és -jelentéseket.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 08/07/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 7f7fde7fcabc29238d9558739eff02519ef9cca3
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73020012"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Oktatóanyag: Csatlakozás GitHub-adattárhoz a Power BI segítségével
Ebben az oktatóanyagban valódi, GitHub szolgáltatásbeli adatokhoz csatlakozhat a Power BI segítségével, és automatikusan hozhat létre Power BI-irányítópultokat és -jelentéseket. A Power BI nyilvános adattárához (más néven *tárházához*) fog csatlakozni, hogy választ kapjon olyan kérdésekre, mint: Hány közreműködő dolgozik a nyilvános Power BI-tartalmon? kik a fő közreműködők, a hét mely napján történik a legtöbb közreműködés, és sok más kérdés. 

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

- Hozzon létre egy [GitHub-fiókot](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Csatlakozás
1. Jelentkezzen be a Power BI szolgáltatásba (https://app.powerbi.com). 
2. A bal oldali navigációs panelen válassza az **Alkalmazások** ikont, majd az **Alkalmazások letöltése** lehetőséget.
   
   ![Power BI – Alkalmazások letöltése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Válassza az **Alkalmazások** lehetőséget, írja be a **GitHub** szöveget a keresőmezőbe, majd válassza a **Letöltés most** gombot.
   
   ![Power BI – a GitHub alkalmazás letöltése](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. A **Telepíti ezt a Power BI-alkalmazást?** területen válassza a **Telepítés** lehetőséget.
5. **Az új alkalmazása elkészült** területen válassza az **Ugrás az alkalmazáshoz** lehetőséget.
6. **Az új alkalmazás használatának első lépései** résznél válassza az **Csatlakozás** lehetőséget.

    ![Első lépések az új alkalmazással](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. Adja meg az adattár nevét és tulajdonosát. Az adattár URL-címe https://github.com/MicrosoftDocs/powerbi-docs, az **Adattár tulajdonosa** a **MicrosoftDocs**, az **Adattár** neve pedig **powerbi-docs**. 
   
    ![Power BI – GitHub adattár neve](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Adja meg a GitHub-fiókja hitelesítő adatait. Előfordulhat, hogy a Power BI kihagyja ezt a lépést, ha korábban már bejelentkezett a GitHubba a böngészőjében. 

6. A **Hitelesítési módszernél** hagyja kijelölve az **oAuth2** bejelentkezési lehetőséget \> **jelentkezzen be**.

7. Kövesse a GitHub-hitelesítés lépéseit. Engedélyezze a Power BI-nak a GitHub-adatok elérését.
   
   A Power BI ezután már képes elérni a GitHub szolgáltatást az adatok beolvasásához.  Az adatok naponta egyszer frissülnek.

8. Miután a Power BI importálta az adatokat, megjelenik az új GitHub-munkaterület tartalma. 
9. Kattintson a munkaterület neve melletti nyílra a bal oldali navigációs sávon. Láthatja, hogy a munkaterület egy irányítópultot és egy jelentést tartalmaz. 

    ![Az alkalmazás a bal oldali navigációs panelen](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Válassza az irányítópult neve melletti **További lehetőségek** (...) elemet, majd az **Átnevezés** menüpontot, és gépelje be a **GitHub-irányítópult** nevet.
 
    ![Power BI – GitHub csempe](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Válassza a globális navigációs ikont a bal oldali navigációs panel kis méretűre állításához, hogy több szabad hely legyen a képernyőn.

    ![Globális navigációs ikon](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Válassza ki a GitHub-irányítópultot.
    
    A GitHub-irányítópult élő adatokat tartalmaz, ezért az Ön által látott értékek eltérhetnek az itt szemléltetettől.

    ![GitHub-irányítópult a Power BI-ban](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Kérdés feltevése

1. Vigye a kurzort a **Tegyen fel kérdést az adataival kapcsolatban** területre. A Power BI felkínál néhány **kérdést a kezdéshez**. 

1. Válassza a **how many users are there** (Hány felhasználó van?) kérdést.
 
    ![Hány felhasználó van?](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. A **how many** és a **users are there** közé gépelje be a **pull requests per** szöveget. 

     A Power BI ekkor létrehoz egy sávdiagramot, melyen a lekéréses kérelmek személyenkénti száma (pull requests per user) látható.

    ![Hány lekéréses kérelem van felhasználónként?](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Rögzítse az irányítópulton a rajzszög választásával, majd **lépjen ki a Q&A-ból**.

## <a name="view-the-github-report"></a>GitHub-jelentés megtekintése 

1. Válassza a GitHub-irányítópulton a **Pull Requests by Month** (Lekéréses kérelmek hónapok szerint) oszlopdiagramot a vonatkozó jelentés megnyitásához.

    ![Lekéréses kérelmek hónapok szerint oszlopdiagram](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Jelöljön ki egy felhasználónevet a **Total pull requests by user** (Összes lekéréses kérelem felhasználó szerint) diagramon. Ezen a példán az látható, hogy a többség februárra esik.

    ![Power BI – Kiemelés a GitHub-jelentésben](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

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


