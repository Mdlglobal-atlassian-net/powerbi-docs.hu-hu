---
title: Példák kifejezésekre a Power BI Jelentéskészítőben
description: A Power BI Report Builderrel készült lapszámozott jelentésekben gyakran használnak kifejezéseket a tartalom és a jelentés megjelenésének szabályozására.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921148"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Példák kifejezésekre a Power BI Jelentéskészítőben
A Power BI Report Builderrel készült lapszámozott jelentésekben gyakran használnak kifejezéseket a tartalom és a jelentés megjelenésének szabályozására. A kifejezések Microsoft Visual Basicben vannak írva, és beépített függvényeket, egyéni kódot, jelentés- és csoportváltozókat és felhasználó által definiált változókat is használhatnak. A kifejezések egyenlőségjellel (=) kezdődnek.   

Ez a témakör a jelentésekben gyakori feladatokra használható kifejezésekre mutat példákat.  
  
-   [Visual Basic-függvények](#VisualBasicFunctions) – Példák dátum, sztring, konverziós és feltételes Visual Basic-függvényekre.  
  
-   [Jelentésfüggvények](#ReportFunctions) – Példák összegzésekre és más beépített jelentésfüggvényekre.  
  
-   [A jelentésbeli adatok megjelenése](#AppearanceofReportData) – Példák egy jelentés megjelenésének módosítására.  
  
-   [Tulajdonságok](#Properties) – Példák a formátum vagy a láthatóság vezérlésére jelentéselemek tulajdonságainak beállításával.  
  
-   [Paraméterek](#Parameters) – Példák paraméterek kifejezésben való használatára.  
  
-   [Egyéni kód](#CustomCode) – Példák beágyazott egyéni kódra.  
  
Az egyszerű és összetett kifejezésekről, a kifejezések felhasználási lehetőségeiről és a kifejezésekbe beépíthető hivatkozástípusokról a [Kifejezések a Power BI Jelentéskészítőben](report-builder-expressions.md) című cikk témaköreiből tájékozódhat. 
  
## <a name="functions"></a>Függvények  
 Sok jelentésbeli kifejezés tartalmaz függvényeket. Ezekkel a függvényekkel adatokat formázhat, logikát valósíthat meg és a jelentés metaadataihoz is hozzáférhet. Írhat kifejezéseket, amelyek a Microsoft Visual Basic futtatókörnyezeti kódtárából és az `xref:System.Convert` és `xref:System.Math` névtérből származó függvényeket használnak. Az egyéni kódban elhelyezheti függvények hivatkozásait. A Microsoft .NET-keretrendszerből is használhat olyan osztályokat, mint az `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Visual Basic-függvények  
 Visual Basic-függvényekkel kezelheti az adatokat, amelyek megjelennek a szövegdobozokban, vagy paraméterekhez, tulajdonságokhoz vagy a jelentés más területeihez lesznek használva. Ez a szakasz néhány ilyen függvény bemutatására kínál példákat. További információt [A Visual Basic futtatókörnyezeti kódtár tagjai](https://go.microsoft.com/fwlink/?LinkId=198941) című cikkben talál az MSDN webhelyén.  
  
 A .NET-keretrendszer számos egyéni formátumbeállítást kínál például adott dátumformátumokhoz. További információt a [Típusok formázása](/dotnet/standard/base-types/formatting-types) című cikkben találhat.  
  
### <a name="math-functions"></a>Matematikai függvények  
  
-   A **Round** függvény számoknak a legközelebbi egész számra kerekítésére használható. Az alábbi kifejezés az 1,3 értéket kerekíti 1-re:  
  
    ```  
    = Round(1.3)  
    ```  
  
     Olyan kifejezést is írhat, amely egy Ön által megadott szám többszörösére kerekít egy értéket, az Excel **TÖBBSZ.KEREKÍT** függvényéhez hasonlóan. Szorozza meg az értéket egy egészt eredményező tényezővel, kerekítse a számot, majd ossza el ugyanezzel a tényezővel. Az 1,3 érték például az alábbi példa alapján kerekíthető az 0,2 legközelebbi többszörösére (1,4):  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Dátumfüggvények  
  
-   A **Today** függvény az aktuális dátumot adja meg. Ez a kifejezés felhasználható egy szövegdobozban a jelentés keltének megjelenítésére, vagy egy paraméterben az adatok aktuális dátum szerinti szűrésére.  
  
    ```  
    =Today()  
    ```  
  
-   A dátum egy adott része kinyerhető a **DateInterval** függvénnyel. A **DateInterval** paraméterei többek között a következők:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Ez a kifejezés például az aktuális dátumhoz tartozó hét sorszámát adja meg az aktuális évben:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   A **DateAdd** függvény használatával dátumtartomány adható meg egyetlen paraméter alapján. Az alábbi kifejezés a hat hónappal egy *StartDate* nevű paraméter utáni dátumot adja meg.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   A **Year** függvény egy adott dátum évét jeleníti meg. Használatával dátumokat csoportosíthat, vagy címkeként jelenítheti meg az évszámot egy dátumcsoporthoz. Ez a kifejezés értékesítési megrendelési dátumok egy adott csoportjához adja meg az évszámot. A **Month** és néhány további függvény is felhasználható dátumok kezelésére. További információt a Visual Basic dokumentációjában talál.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Egy kifejezésben függvények kombinálásával szabhatja testre a formátumot. Az alábbi kifejezés a hónap/nap/év formátumban megadott dátumot alakítja hónap, hét, hét száma formátumúra. Így 12/23/2009 például December Week 3 (december 3. hete) formában jelenik meg:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Ezt a kifejezést egy adathalmaz számított mezőjeként használva a havi értékek heti összesítését végezheti el egy diagramon.  
  
-   Az alábbi kifejezés HHH-ÉÉ formátumra hozz a SellStartDate értéket. A SellStartDate mező adattípusa dátum/idő.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   Az alábbi kifejezés nn/HH/éééé formátumra hozz a SellStartDate értéket. A SellStartDate mező adattípusa dátum/idő.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   A **CDate** függvény dátummá konvertálja az értéket. A **Now** függvény az aktuális rendszerdátumot és -időt tartalmazó dátumértéket ad vissza. A **DateDiff** Long típusú értékkel adja meg a két dátumérték közötti intervallumok számát.  
  
     Az alábbi példa az aktuális év első napját jeleníti meg.  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   A következő példa az előző hónap első napját jeleníti meg az aktuális hónap alapján.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   A következő kifejezés a SellStartDate és a LastReceiptDate közötti évek számát állítja elő. Ezek a mezők a DataSet1 és DataSet2 külön adathalmazban vannak.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   A **DatePart** függvény egész értéket ad vissza, amely egy adott dátumérték megadott összetevőjét tartalmazza. Az alábbi példa az év értéket adja meg a DataSet1 adathalmaz SellStartDate mezőjének első értékéből. Az adathalmaz-hatókör azért van megadva, mert a jelentéshez több adathalmaz is tartozik.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   A **DateSerial** függvény a megadott évnek, hónapnak és napnak megfelelő dátumértéket ad vissza éjfélre beállított időadatokkal. A következő példa az előző hónap utolsó napját jeleníti meg az aktuális hónap alapján.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   A következő példák különböző dátumokat jelenítenek meg a felhasználó által választott dátumparaméter alapján.  
  
|Példa leírása|Példa|  
|-------------------------|-------------|  
|Tegnap|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Két nappal ezelőtt|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Egy hónappal ezelőtt|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Két hónappal ezelőtt|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Egy évvel ezelőtt|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Két évvel ezelőtt|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Sztringfüggvények  
  
-   Több mezőt kombinálhat összefűző operátorok és Visual Basic-konstansok használatával. Az alábbi kifejezés két mezőt ad vissza egy szövegdoboz két külön sorában:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   A **Format** függvénnyel formázhatja a sztringben lévő dátumokat és számokat. Az alábbi kifejezés a *StartDate* és az *EndDate* paraméterek értékét jeleníti meg hosszú dátum formátumban:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Ha a szövegdoboz csak egy dátumot vagy számot tartalmaz, akkor azt a szövegdobozon belüli **Format** függvény helyett érdemesebb a szövegdoboz Formátum tulajdonságával formázni.  
  
-   A **Right**, **Len** és **InStr** függvények sztringrészletek visszaadására használhatók, így nyerhető ki például a felhasználónév a *TARTOMÁNY*\\*felhasználónév* sztringből. A következő kifejezés eredménye a sztringnek a fordított perjeltől (\\) jobbra lévő részét adja vissza egy *User* nevű paraméterből:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     A következő kifejezés eredménye ugyanaz, mint az előzőé, de Visual Basic-függvények helyett a .NET-keretrendszer `xref:System.String` osztályának tagjait használja:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Megjeleníthetők egy többértékű paraméter kiválasztott értékei. Az alábbi példa a **Join** függvénnyel egyetlen sztringgé fűzi össze a *MySelection* paraméter kijelölt értékeit, az pedig kifejezésként már beállítható egy jelentéselem szövegdobozának értékeként:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     A következő példa ugyanazt a műveletet hajtja végre, mint az előző, de egy szöveges sztringet is megjelenít a kijelölt értékek előtt.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   A .NET-keretrendszerbeli `xref:System.Text.RegularExpressions`**reguláriskifejezés**-függvényei (RegEx) használatával meglévő sztringek formátuma módosítható, például formázhat velük egy telefonszámot. Az**Replace** függvény használatával egy telefonszámot alakít át egy mezőben az "*nnn*-*nnn*-*nnnn*" formátumról az "(*nnn*) *nnn*-*nnnn*" formátumra:  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Ellenőrizni kell, hogy a Fields!Phone.Value értéke nem tartalmaz-e felesleges szóközöket, és `xref:System.String` típusú-e.  
  
### <a name="lookup"></a>Lookup  
  
-   Egy kulcsmező megadásával a **Lookup** függvény segítségével lekérhet egy egy-az-egyhez kapcsolathoz tartozó értéket, például egy kulcs-érték párt. A következő kifejezés egy termék nevét jeleníti meg egy adathalmazból („Product”) a megadott termékazonosító alapján:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Egy kulcsmező megadásával a **LookupSet** függvény segítségével lekérheti egy egy-a-többhöz kapcsolathoz tartozó értékek halmazát. Egy személynek például több telefonszáma is lehet. Az alábbi példa azt feltételezi, hogy az adathalmaz PhoneList elemének minden sora egy személyazonosítót és egy telefonszámot tartalmaz. A **LookupSet** értéktömböt ad vissza. Az alábbi kifejezés egyetlen sztringben kombinálja a visszaadott értékeket, és az egy személy megadott ContactID azonosítójához tartozó telefonszámok listáját jeleníti meg:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Konverziós függvények  
 Visual Basic-függvények használatával egy mezőt egy adattípusról egy másikra konvertálhat át. A konverziós függvények használatával egy mező alapértelmezett adattípusa átkonvertálható a számításokhoz vagy szöveg kombinálásához szükséges típusra.  
  
-   Az alábbi kifejezés a konstans 500 értéket konvertálja át tizedestört típusúra, hogy egy szűrőkifejezésben összehasonlítható legyen a Value mező Transact-SQL pénznem adattípusával.  
  
    ```  
    =CDec(500)  
    ```  
  
-   A következő kifejezés a *MySelection* többértékű paraméter kijelölt értékeinek számát jeleníti meg.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Döntési függvények  
  
-   Az **Iif** függvény két érték egyikét adja vissza attól függően, hogy a kifejezés igaz vagy sem. Az alábbi kifejezés az **Iif** függvény használatával a **True** logikai értéket adja vissza, ha a `LineTotal` érték 100-nál nagyobb. Ellenkező esetben a **False** értéket adja vissza:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Több **IIF** függvény („beágyazott IIF-ek”) használatával háromféle érték is visszaadható a `PctComplete` értéke alapján. A következő kifejezés egy szövegdoboz kitöltőszíneként megadva a szövegdobozban lévő érték alapján állítja be annak háttérszínét.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     A 10-nél nagyobb vagy egyenlő értékek zöld, az 1 és 9 közöttiek kék, az 1-nél alacsonyabbak piros hátteret eredményeznek.  
  
-   Ugyanez a működés a **Switch** függvénnyel is elérhető. A **Switch** függvény három vagy több feltétel ellenőrzése esetén hasznos. A **Switch** függvény az egy kifejezésekből álló sorozat első igaz értékű tagjához tartozó értéket jeleníti meg:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     A 10-nél nagyobb vagy egyenlő értékek zöld, az 1 és 9 közöttiek kék, az 1 sárga, a 0 és annál kisebbek pedig piros hátteret eredményeznek.  
  
-   Tesztelheti az `ImportantDate` mező értékét, és ha az egy hétnél régebbi, a „Red”, ellenkező esetben pedig a „Blue” értéket adhatja vissza. Ezt a kifejezést felhasználva szabályozhatja egy jelentéselem egy szövegdobozának Szín tulajdonságát:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Ellenőrizheti a `PhoneNumber` mező értékét, és a „No value” eredményt adhatja vissza, ha az **null** (Visual Basicben **Nothing**), ellenkező esetben pedig visszaadhatja a telefonszámot. Ezt a kifejezést felhasználva szabályozhatja egy jelentéselem egy szövegdobozában megjelenő értéket.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   A `Department` mező értékét ellenőrizve visszaadhatja egy segédjelentés nevét, vagy a **null** (Visual Basicben **Nothing**) értéket. Ez a kifejezés feltételes részletező segédjelentésekhez használható.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Ellenőrizheti, hogy egy mező null értékű-e. Ez a kifejezés egy kép jelentéselem **Rejtett** tulajdonságának szabályozására használható. Az alábbi példában a [LargePhoto] mező által megadott kép csak akkor jelenik meg, ha a mező értéke nem null.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   A **MonthName** függvény a megadott hónap nevét tartalmazó sztring értéket ad vissza. Az alábbi példa az NA szöveget jeleníti meg a Month mezőben, ha a mező a 0 értéket tartalmazza.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Jelentésfüggvények  
 Egy kifejezésben további jelentésfunkciókra is hivatkozhat, amelyek a jelentésbeli adatokat manipulálják. Ez a szakasz két ilyen függvényre mutat be példát. 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   A **Sum** függvénnyel egy csoport vagy adatterület értékei összegezhetők. Ez a függvény jól használható egy csoport fejlécében vagy láblécében. Az alábbi kifejezés az Order csoport vagy adatterület adatainak összegét jeleníti meg:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   A **Sum** függvényt feltételes összesítő számításokhoz is felhasználhatja. Ha egy adathalmaznak például van egy State (Állapot) nevű mezője, amelynek lehetséges értéke Not Started, Started és Finished (Nem kezdődött el, Elkezdődött és Befejeződött), akkor az alábbi kifejezés egy csoportfejlécben elhelyezve csak a Finished értékeket számolja össze:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   A **RowNumber** függvény egy adatterületen lévő szövegdobozban használva a sorok számát jeleníti meg annak a szövegdoboznak az összes példányához, amelyben a kifejezés megjelenik. Ez a függvény felhasználható egy táblázat sorainak számozására. Olyan összetettebb feladatok is megoldhatók vele, mint oldaltörések beszúrása a sorok száma alapján. További információt ennek a témakörnek az [Oldaltörések](#PageBreaks) című szakaszában talál.  
  
     A **RowNumber** függvényhez megadott hatókör szabályozza az újraszámozás kezdetét. A **Nothing** kulcsszó azt eredményezi, hogy a függvény a legkülső adatterület első soránál kezdi a számozást. A számozás az adatterület nevének használatával indítható egy beágyazott adatterületen. A számozás csoporton belüli indításához használja a csoport nevét.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> A jelentésadatok megjelenése  
 Kifejezésekkel befolyásolható az adatok jelentésbeli megjelenése. Megjelenítheti például az értékeket egy szövegdobozon belül két mezőben, megjeleníthet a jelentésről szóló információkat, vagy befolyásolhatja, hogyan legyenek beszúrva az oldaltörések a jelentésbe.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> Oldalfejlécek és -láblécek  
 Jelentés tervezésekor érdemes lehet a jelentés nevét és az oldal számát feltüntetni a jelentés láblécében. Erre használhatja a következő kifejezéseket:  
  
-   Az alábbi kifejezés a jelentés nevét és futtatásának időpontját adja meg. Elhelyezhető egy szövegdobozban a jelentés láblécében vagy a jelentés törzsében. Az idő a .NET-keretrendszer rövid dátumhoz való formátumsztringjével van formázva:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   A következő kifejezés a jelentés láblécében lévő szövegdobozban elhelyezve az oldalszámot és a jelentés oldalainak számát adja meg:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 A következő példák bemutatják, hogyan jeleníthető meg egy oldal első és utolsó értéke az oldal fejlécében, ahogyan például egy szótárban látható. A példa feltételezi egy `LastName` nevű szövegdobozt tartalmazó adatterület meglétét.  
  
-   Az alábbi kifejezés az oldalfejléc bal oldalán elhelyezve a `LastName` szövegdoboznak az oldalon szereplő első értékét adja meg:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   Az alábbi kifejezés az oldalfejléc jobb oldalán elhelyezve a `LastName` szövegdoboznak az oldalon szereplő utolsó értékét adja meg:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 A következő példa az oldal összegzésének megjelenítését mutatja be. A példa feltételezi egy `Cost` nevű szövegdobozt tartalmazó adatterület meglétét.  
  
-   Az alábbi kifejezés az oldal fejlécében vagy láblécében elhelyezve megadja a `Cost` szövegdoboz értékeinek az oldalra vonatkozó összegét:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Oldalfejlécben vagy -láblécben kifejezésenként csak egy jelentéselemre hivatkozhat. Az oldalfejlécekben és -láblécekben lévő kifejezésekben hivatkozhat a szövegdoboz nevére is, de nem magára a szövegdobozban lévő adatkifejezésre.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Oldaltörések  
 Egyes jelentésekben érdemes lehet adott számú sor után oldaltörést elhelyezni a csoportok vagy jelentéselemek utániak helyett vagy azok mellett. Ehhez hozzon létre egy csoportot, amely a kívánt csoportokat vagy részletes rekordokat tartalmazza, adjon hozzá oldaltörést a csoporthoz, majd adjon hozzá csoportkifejezést, amely adott számú sort csoportosít.  
  
-   Az alábbi kifejezés egy csoportkifejezésben elhelyezve minden 25 sorból álló szakaszhoz sorszámot rendel. Ha a csoporthoz oldaltörés van megadva, a kifejezés 25 soronkénti oldaltörést eredményez.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Ha azt szeretné, hogy a felhasználó megadhassa az oldalanként megjelenő sorok számát, hozzon létre egy `RowsPerPage` nevű paramétert, és alapozza a csoportkifejezést erre a paraméterre, ahogyan az alábbi kifejezésben látható:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Tulajdonságok  
 Kifejezések nem csak adatok szövegdobozokban való megjelenítéséhez használhatók. Az is módosítható velük, ahogyan a tulajdonságok érvényesülnek a jelentéselemeken. Megváltoztathatók egy jelentéselem stílusinformációi, és megváltoztatható a láthatósága is.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Formázás  
  
-   Az alábbi kifejezés egy szövegdoboz Szín tulajdonságában használva a `Profit` változó értékétől függően módosítja a szöveg színét:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     A `Me` Visual Basic-objektumváltozót is használhatja. Ez a változó egy újabb mód egy szövegdoboz értékére való hivatkozásra.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   Az alábbi kifejezés egy adatterületen lévő jelentéselem Háttérszín tulajdonságában használva váltakozva halványzöldre és fehérre állítja be a sorok háttérszínét:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Ha egy kifejezést egy meghatározott hatókörhöz használ, esetleg meg kell adnia az adathalmazt az összesítő függvénynek:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Az elérhető színek a .NET-keretrendszer KnownColor színlistájából származnak.  
  
### <a name="chart-colors"></a>Diagramszínek  
 Alakzatdiagram színeinek megadásához egyéni kóddal szabályozhatja, hogy a színek milyen sorrendben legyenek leképezve az adatpontok értékeire. Így egyszerűbb egységes színeket megadni az ugyanazokra a kategóriacsoportokra épülő diagramokhoz. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Láthatóság  
 Egy jelentés elemei megjeleníthetők és elrejthetők a jelentéselem láthatósági tulajdonságaival. Egy adatterületen, például táblázatban kezdetben egy kifejezés értéke alapján elrejtheti a részletezősorokat.  
  
-   Az alábbi kifejezés egy csoport részletezősorainak kezdeti láthatóságához használva minden olyan értékesítés részletezősorát megmutatja, amely meghaladja a `PctQuota` mező értékének 90%-át:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   Az alábbi kifejezés egy táblázat Rejtett tulajdonságában beállítva csak akkor fedi fel a táblázatot, ha az több mint 12 sorból áll:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   A következő kifejezés egy oszlop **Rejtett** tulajdonságában beállítva csak akkor fedi fel az oszlopot, ha a mező létezik a jelentés adathalmazában az adatok adatforrásból való lekérése után:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL-címek  
 URL-címeket szabhat testre a jelentésbeli adatok használatával, és feltételesen szabályozhatja URL-címek műveletként való felvételét egy szövegdobozba.  
  
-   Az alábbi kifejezés szövegdobozbeli műveletként használva testreszabott URL-címet generál, amely az adathalmaz `EmployeeID` mezőjét adja meg az URL-paraméterként.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   A következő kifejezés feltételesen szabályozza az URL-cím szövegdobozba való felvételét. A kifejezés egy `IncludeURLs` nevű paramétertől függ, amelynek használatával a felhasználó eldöntheti, hogy legyenek-e aktív URL-címek egy jelentésben. Ez a kifejezés műveletként van beállítva egy szövegdobozban. Ha a paramétert False értékre állítja, majd megtekinti a jelentést, hivatkozások nélkül exportálhatja azt a Microsoft Excelbe.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> Jelentésadatok  
 A kifejezések a jelentésben használt adatok manipulálására is használhatók. Hivatkozhat paraméterekre és más jelentésbeli információkra. Akár a jelentés adatainak lekérésre használt lekérdezést is módosíthatja.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Paraméterek  
 Kifejezéseket egy paraméterben is használhat, hogy megváltoztassa a paraméter alapértelmezett értékét. Használhat egy paramétert például arra, hogy az adatokat egy meghatározott felhasználóra szűrje a jelentés futtatásához használt felhasználói azonosító alapján.  
  
-   Az alábbi kifejezés egy paraméter alapértelmezett értékeként használva begyűjti a jelentést futtató személy felhasználói azonosítóját:  
  
    ```  
    =User!UserID  
    ```  
  
-   Egy paraméterre a **Parameters** globális gyűjtemény használatával hivatkozhat lekérdezési paraméterekben, szűrőkifejezésekben, szövegdobozokban vagy a jelentés más területein. Ez a példa feltételezi, hogy a paraméter neve *Department*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Egy jelentésben létrehozhatók, de aztán rejtetté tehetők a paraméterek. Amikor a jelentés a jelentéskészítő kiszolgálón fut, a paraméter nem jelenik meg az eszköztáron, és a jelentés olvasója nem módosíthatja annak alapértelmezett értékét. Egy alapértelmezett értékre beállított rejtett paraméter egyéni konstansként is használható. Ezt az értéket bármilyen kifejezésben, akár mezőkifejezésekben is használhatja. A következő kifejezés *ParameterField* nevű paraméter alapértelmezett paraméterértéke által meghatározott mezőt adja meg:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Egyéni kód  
 Egyéni kód jelentésekbe ágyazva is használható. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Csoportváltozók használata egyéni összesítéshez  
 Beállíthatja egy adott csoporthatókörön belüli csoportváltozó kezdeti értékét, és kifejezésekben hivatkozhat erre a változóra. A csoportváltozók egyéni kóddal való felhasználásnak egyik módja az egyéni összesítések megvalósítása. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Null vagy nulla értékek kizárása futtatáskor  
 Egy kifejezésben néhány érték kiértékelési eredménye null vagy meghatározatlan lehet a jelentés feldolgozásakor. Ez futásidejű hibákhoz vezethet, amelyek következtében a kiértékelt kifejezés helyett a **#Error** szöveg jelenik meg a szövegdobozban. Az **IIF** függvény különösen érzékeny erre a viselkedésre, mert az If-Then-Else utasítástól eltérően az **IIF** utasítás minden része ki lesz értékelve (a függvényhívásokkal együtt), mielőtt tovább lenne adva az **igaz** vagy **hamis** értéket ellenőrző rutinnak. Az `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` utasítás a **#Error** eredményt hozza a megjelenített jelentésben, ha `Fields!Sales.Value` értéke NOTHING.  
  
 Ennek elkerülésére az alábbi stratégiák egyikét használhatja:  
  
-   Állítsa 0-ra a számlálót és 1-re a nevezőt, ha a B mező értéke 0 vagy nem meghatározott; egyébként állítsa be a számlálót az A mező értékére, a nevezőt pedig a B mező értékére.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Használjon egyéni kódot a kifejezés értékének visszaadására. Az alábbi példa a jelenlegi és az előző érték százalékos eltérését adja vissza. Bármely két egymást követő érték eltérésének kiszámítására használható, kezeli a szélső helyzetű első összehasonlítást (amikor nincs előző érték), és azokat az eseteket is, amikor az előző vagy az aktuális érték **null** (Visual Basicben **Nothing**).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     A következő kifejezés azt mutatja be, hogy hogyan hívható meg ez az egyéni kód egy szövegdobozból a „ColumnGroupByYear” tárolóra (csoport vagy adatterület).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Ezzel elkerülhetők a futásidejű kivételek. Most már használhat olyan kifejezéseket, mint `=IIF(Me.Value < 0, "red", "black")` a szövegdoboz **Szín** tulajdonságában, hogy feltételesen jelenítse meg a szöveget a 0-nál nagyobb és annál kisebb értékek alapján.  
  
## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
  
