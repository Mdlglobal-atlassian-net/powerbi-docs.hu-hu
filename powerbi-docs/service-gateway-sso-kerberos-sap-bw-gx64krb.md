---
title: Kerberos használata az SAP BW-n történő egyszeri bejelentkezéshez (SSO) a gx64krb5-tel
description: Az SAP BW-kiszolgáló konfigurálása a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez a gx64krb5 használatával
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5dd31dc4333dc03100370100e16eadab6012c1f0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106331"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Kerberos használata az SAP BW-n történő egyszeri bejelentkezéshez (SSO) a gx64krb5-tel

Ez a cikk azt ismerteti, hogy hogyan konfigurálhatja az SAP BW-kiszolgálót a Power BI szolgáltatás egyszeri bejelentkezési funkciójának engedélyezéséhez a gx64krb5 használatával.

> [!NOTE]
> Ha elvégzi ezen cikk és a [Kerberos SSO konfigurálását ismertető cikk](service-gateway-sso-kerberos.md) lépéseit, engedélyezheti a frissítést az SAP BW-alkalmazáskiszolgálóra alapuló jelentések számára, amelyek a Kerberos SSO-t alkalmazzák a Power BI szolgáltatásban. A Microsoft azonban a CommonCryptoLib használatát javasolja, mint SNC-könyvtár. Az SAP már nem támogatja a gx64krb5-öt, ennek az átjáró használatára történő konfigurációjához szükséges lépései pedig jelentősen összetettebbek, mint a CommonCryptoLib eljárása. Az SSO a CommonCryptoLibbel történő konfigurálásához tekintse meg [Az SAP BW konfigurálása egyszeri bejelentkezéshez a CommonCryptoLib használatával](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) című cikket. A konfigurációt a CommonCryptoLib _vagy_ a gx64krb5 számára kell elvégeznie. Ne konfiguráljon mindkét könyvtárhoz.

### <a name="set-up-gx64krb5gsskrb5-on-gateway-machine-and-the-sap-bw-server"></a>A gx64krb5/gsskrb5 beállítása az átjárógépen és az SAP BW-kiszolgálón

> [!NOTE]
> A `gx64krb5` és a `gsskrb5` kódtárat már nem támogatja az SAP. További információt az [SAP 352295 megjegyzés](https://launchpad.support.sap.com/#/notes/352295) című cikkben talál. Vegye figyelembe azt is, hogy a `gx64krb5` nem teszi lehetővé az adatátjáróból az SAP BW üzenetkiszolgálóba irányuló SSO-kapcsolatokat. Csak az SAP BW-alkalmazáskiszolgálóba irányuló kapcsolatok lehetségesek. Ez az alkalmazáskiszolgálóra vonatkozó korlátozás nem létezik, ha a [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) az SNC-könyvtára. A BW SSO-val egyéb SNC-könyvtárak is működhetnek, azonban ezeket nem támogatja hivatalosan a Microsoft.

A `gx64krb5` \ `gsskrb5`-öt az ügyfélnek és a kiszolgálónak is használnia kell az SSO-kapcsolat átjárón keresztüli létrehozásához, azaz az ügyfélnek és a kiszolgálónak is ugyanazt az SNC-könyvtárat kell használnia.

1. Töltse le a `gx64krb5` könyvtárat az [SAP Note 2115486](https://launchpad.support.sap.com/) oldaláról (ehhez szükséges egy SAP S-felhasználó). Legalább az 1.0.11.x verzióval kell rendelkeznie. Emellett töltse le a `gsskrb5` elemet (a könyvtár 32 bites verzióját), ha az SSO-kapcsolatot az SAP GUI-ban is tesztelni szeretné az átjárón keresztüli SSO-kapcsolat létrehozása előtt (ajánlott). A 32 bites verzió azért szükséges az SAP GUI-teszthez, mert az SAP GUI csak 32 bites verzióban érhető el.

1. Helyezze a `gx64krb5` könyvtárat egy olyan helyre az átjárót tartalmazó számítógépen, amely hozzáférhető átjáró szolgáltatásfelhasználója számára (és az SAP GUI számára is, ha szeretné tesztelni az egyszeri bejelentkezési kapcsolatot az SAP Logon használatával). Mind az átjáró szolgáltatásfelhasználójának, mind pedig a szolgáltatásfelhasználó által megszemélyesített Active Directory- (AD-) felhasználónak rendelkeznie kell olvasási és végrehajtási engedélyekkel a .dll fájlhoz. Javasoljuk, hogy a .dll kiterjesztésű fájlokra vonatkozó engedélyeket adja meg a Hitelesített felhasználók csoport számára. Tesztelési célból ezeket az engedélyeket explicit módon megadhatja az átjáró Szolgáltatás felhasználója és a tesztelési Active Directory-felhasználó számára is.

1. Ha a BW-kiszolgálót még nem konfigurálta az SSO-hoz a gx64krb5/gsskrb5 könyvtárral, helyezzen egy másik másolatot au SAP BW-kiszolgálógépre egy, az SAP BW-kiszolgáló által hozzáférhető helyre. 

1. Az ügyfél és a kiszolgáló gépein állítsa be az `SNC_LIB` vagy az `SNC_LIB_64` környezeti változót. Ha a gsskrb5-öt használja, állítsa az `SNC_LIB` változót a gsskrb5.dll fájl abszolút elérési útjára. Ha a gx64krb5-öt használja, állítsa az `SNC_LIB_64` változót a gx64krb5.dll fájl abszolút elérési útjára.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication"></a>Az SAP BW-szolgáltatásfelhasználó konfigurálása és SNC-kommunikáció engedélyezése

Akkor térjen erre a szakaszra, ha még nem konfigurálta az SAP BW-kiszolgálót az SNC-kommunikációhoz (például SSO-hoz) a gx64krb5/gsskrb5 használatával.

> [!NOTE]
> Ez a szakasz feltételezi, hogy már létrehozott egy szolgáltatásfelhasználót a BW-hez, amelyhez egy megfelelő SPN-t kötött (például egy `SAP/` kezdetűt).

1. Biztosítson hozzáférést a szolgáltatásfelhasználónak az SAP BW-alkalmazáskiszolgálóhoz:

    1. Az SAP BW kiszolgálógépén adja hozzá a szolgáltatásfelhasználót a Helyi rendszergazdák csoportjához. Nyissa meg a Számítógép-felügyelet programot, és kattintson duplán a kiszolgálójához tartozó Helyi rendszergazdák csoport elemre.

        ![Képernyőkép a Számítógép-felügyelet programról](media/service-gateway-sso-kerberos/computer-management.png)

    1. Kattintson duplán a Helyi rendszergazdák csoportra, majd válassza a **Hozzáadás** lehetőséget a szolgáltatásfelhasználó a csoporthoz történő hozzáadásához. A **Névellenőrzés** lehetőség használatával ellenőrizze, hogy helyesen írta-e be a nevet. Kattintson az **OK** gombra.

1. Állítsa be az SAP BW-kiszolgáló szolgáltatásfelhasználóját azon felhasználóként, amely elindítja az SAP BW-kiszolgálószolgáltatást az SAP BW-kiszolgálógépen.

    1. Nyissa meg a **Futtatás** lehetőséget, és írja be a „Services.msc” kifejezést. Keresse meg az SAP BW-alkalmazáskiszolgáló példányának megfelelő szolgáltatást. Kattintson rá a jobb gombbal, és válassza a **Tulajdonságok** elemet.

        ![Képernyőkép a Szolgáltatások területről, kiemelt Tulajdonságok elemmel](media/service-gateway-sso-kerberos/server-properties.png)

    1. Váltson a **Bejelentkezés** lapra, és módosítsa a felhasználót az SAP BW-szolgáltatásfelhasználójára. Adja meg a felhasználó jelszavát, és válassza az **OK** lehetőséget.

1. Jelentkezzen be a kiszolgálóba az SAP Logon programban, és állítsa be az alábbi profilparamétereket az RZ10 tranzakció használatával:

    1. Állítsa az snc/identity/as profilparamétert a p:\<a létrehozott SAP BW-szolgáltatásfelhasználóra\>, például: p:BWServiceUser@MYDOMAIN.COM. Figyelje meg a szolgáltatásfelhasználó egyszerű felhasználóneve előtt szereplő p: elemet. Ez nem p:CN=, mintha a közös titkosítási kódtárat használná SNC-kódtárként.

    1. Állítsa az snc/gssapi\_lib profilparamétert \<a BW-kiszolgálógépen található gsskrb5.dll/gx64krb5.dll elérési útjára (a használandó kódtár az operációs rendszer bitszámától függ)\>. Ne feledje a kódtárat egy olyan helyre helyezni, amelyhez az SAP BW-alkalmazáskiszolgáló hozzá tud férni.

    1. Emellett módosítsa az alábbi profilparaméterek értékeit az igényeinek megfelelően. Az utolsó öt lehetőség lehetővé teszi, hogy az ügyfelek SNC konfigurálása nélkül csatlakozzanak az SAP BW-kiszolgálóhoz az SAP Logon használatával.

        | **Beállítás** | **Érték** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Állítsa az snc/enable tulajdonság értékét 1-re.

1. A profilparaméterek beállítása után nyissa meg az SAP Felügyeleti konzolt a kiszolgálógépen, és indítsa újra az SAP BW-példányt. Ha a kiszolgáló nem indul el, ellenőrizze, hogy a profilparamétereket megfelelően állította-e be. A profilparaméterek beállításáról további információt az [SAP dokumentációjában](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm) talál. Ha problémába ütközik, tekintse át a szakasz később részletezett, hibaelhárítással kapcsolatos információit.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>SAP BW-felhasználó leképezése egy Active Directory-felhasználóra

Ha még nem tette meg, képezzen le egy Active Directory-felhasználót egy SAP BW-alkalmazáskiszolgáló-felhasználóra, és tesztelje az egyszeri bejelentkezési kapcsolatot az SAP Logon programban.

1. Jelentkezzen be az SAP BW-kiszolgálóba az SAP Logon használatával. Futtassa az SU01 tranzakciót.

1. A **Felhasználó** mezőben adja meg az SAP BW-felhasználót, amely számára engedélyezni szeretné az egyszeri bejelentkezési kapcsolatot (az előző képernyőképen a BIUSER nevű felhasználó számára állítunk be engedélyeket). Válassza a **Szerkesztés** ikont (amely egy tollat ábrázol) az SAP Logon-ablak bal felső részében.

    ![Képernyőkép az SAP BW Felhasználó-karbantartás képernyőjéről](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Válassza az **SNC** lapot. Az SNC-név beviteli mezőjében adja meg a p:\<Active Directory-felhasználó\>@\<tartománynév\> sztringet. Vegye figyelembe, hogy a kötelező p: elemnek meg kell előznie az Active Directory-felhasználó egyszerű felhasználónevét. A megadott Active Directory-felhasználónak ahhoz a személyhez vagy szervezethez kell tartoznia, amely számára engedélyezni szeretné az egyszeri bejelentkezési hozzáférést az SAP BW-alkalmazáskiszolgálójához. Ha például a testuser\@TESTDOMAIN.COM felhasználó számára szeretné engedélyezni az egyszeri bejelentkezési hozzáférést, adja meg a p:testuser@TESTDOMAIN.COM sztringet.

    ![Képernyőkép az SAP BW Felhasználók karbantartása képernyőjéről](media/service-gateway-sso-kerberos/maintain-users.png)

1. Válassza a **Mentés** ikont (amely egy hajlékonylemezt ábrázol) a képernyő bal felső sarkában.

### <a name="test-sign-in-by-using-sso"></a>Egyszeri bejelentkezés (SSO) használatával való bejelentkezés tesztelése

Ellenőrizze, hogy be tud-e jelentkezni a kiszolgálóba az SAP Logon használatával egyszeri bejelentkezéssel azon Active Directory-felhasználóként, amely számára az előbb engedélyezte az egyszeri bejelentkezési hozzáférést.

1. Azon Active Directory-felhasználóként, amely számára az előbb engedélyezte az egyszeri bejelentkezési hozzáférést, jelentkezzen be egy gépre, amelyen telepítve van az SAP Logon. Indítsa el az SAP Logont, és hozzon létre egy új kapcsolatot.

1. Az **Új rendszerbejegyzés létrehozása** képernyőn válassza a **Felhasználó által meghatározott rendszer** > **Tovább** lehetőséget.

    ![Képernyőkép az Új rendszerbejegyzés létrehozása képernyőről](media/service-gateway-sso-kerberos/new-system-entry.png)

1. A következő képernyőn adja meg a megfelelő részleteket az alkalmazáskiszolgálóval, a példányszámmal és a rendszer-azonosítóval együtt. Ezután válassza a **Befejezés** gombot.

1. Kattintson a jobb gombbal az új kapcsolatra, majd válassza a **Tulajdonságok** elemet. Válassza a **Hálózat** lapot. Az **SNC-név** ablakban adja meg a p:\<az SAP BW-szolgáltatásfelhasználó egyszerű felhasználóneve\> sztringet, például: p:BWServiceUser@MYDOMAIN.COM. Ezután válassza az **OK** gombot.

    ![Képernyőkép a Rendszerbejegyzés-tulajdonságok képernyőről](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Kattintson duplán az előbb létrehozott kapcsolatra, hogy megkísérelje az egyszeri bejelentkezést az SAP BW-kiszolgálóra. Ha ez a kapcsolat sikeres, folytassa a következő lépéssel. Ellenkező esetben tekintse át a dokumentum korábbi lépéseit, hogy meggyőződjön arról, hogy azok megfelelően lettek elvégezve, vagy tekintse át az alábbi, hibaelhárítással kapcsolatos szakaszt. Ha ebben a környezetben nem tud csatlakozni az SAP BW-kiszolgálóhoz egyszeri bejelentkezéssel, akkor az átjárói környezetben sem fog tudni csatlakozni az SAP BW-kiszolgálóhoz egyszeri bejelentkezéssel.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Beállításjegyzékbeli bejegyzések hozzáadása az átjárót tartalmazó számítógépen

Adja hozzá a szükséges beállításjegyzék-bejegyzéseket annak a gépnek beállításjegyzékéhez, amelyre az átjáró telepítve van, valamint azokhoz a gépekhez, amelyekhez csatlakozni szeretne a Power BI Desktopról. A futtatandó parancsok:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Új SAP BW-alkalmazáskiszolgáló-adatforrás hozzáadása a Power BI szolgáltatáshoz, vagy meglévő szerkesztése

1. Az adatforrás konfigurációs ablakában adja meg az Alkalmazáskiszolgáló **Gazdagépnév**, **Rendszer száma** és **Ügyfél-azonosító** adatait, ahogy azt a Power BI Desktopból az SAP BW-kiszolgálóba való bejelentkezés során tenné.

1. Az **SNC-partner neve** mezőben adja meg a p: \<az SAP BW-szolgáltatás felhasználójára leképezett egyszerű szolgáltatásnév\> értéket. Ha például az SPN SAP/BWServiceUser@MYDOMAIN.COM, adja meg a p:SAP/BWServiceUser@MYDOMAIN.COM értéket az **SNC-partner neve** mezőben.

1. Az SNC-kódtárnál válassza az **SNC_LIB** vagy az **SNC_LIB_64** lehetőséget. Győződjön meg arról, hogy az átjárógép SNC_LIB_64 eleme a gx64krb5.dll fájlra mutat. Alternatívaként az „Egyéni” lehetőséggel megadhatja a gx64krb5.dll abszolút elérési útját (az átjárógépen).

1. Jelölje be az **Egyszeri bejelentkezés használata a Kerberoson keresztül DirectQuery-lekérdezésekhez** jelölőnégyzetet, majd válassza az **Alkalmaz** lehetőséget. Ha a tesztkapcsolat nem volt sikeres, ellenőrizze, hogy az előző telepítési és konfigurációs lépések megfelelően lettek elvégezve.

1. [Power BI-jelentés futtatása](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="troubleshoot-gx64krb5gsskrb5-configuration"></a>A gx64krb5/gsskrb5 konfigurációjának hibaelhárítása

Ha bármilyen problémát tapasztal, kövesse az alábbi lépéseket a gx64krb5-/gsskrb5-telepítés és az egyszeri bejelentkezési kapcsolatok SAP Logon programból történő hibaelhárításához.

* A kiszolgálónaplók (…work\dev\_w0 a kiszolgálógépen) megtekintése hasznos lehet a gx64krb5/gsskrb5 telepítésének lépései során tapasztalt hibák elhárításában. Ez különösen igaz akkor, ha az SAP BW-kiszolgáló nem indul el a profilparaméterek módosítása után.

* Ha nem tudja elindítani az SAP BW szolgáltatást egy bejelentkezési hiba miatt, előfordulhat, hogy rossz jelszót adott meg az SAP BW indítási felhasználójának beállításakor. Ellenőrizze a jelszót úgy, hogy bejelentkezik egy Active Directory-környezetben található gépre az SAP BW-szolgáltatásfelhasználóként.

* Ha az SQL hitelesítő adatok meggátolják, hogy a kiszolgáló elinduljon, és ezért hibába ütközik, ellenőrizze, hogy biztosított-e hozzáférést a szolgáltatásfelhasználónak az SAP BW-adatbázishoz.

* Ekkor a következő üzenet jelenhet meg: „(GSS-API) specified target is unknown or unreachable.”(„(GSS-API) a megadott cél ismeretlen vagy elérhetetlen”). Ez általában azt jelenti, hogy rossz SNC-nevet adott meg. Ügyeljen arra, hogy az ügyfélalkalmazásban csak a „p:” elemet használja, ne a „p:CN=”-t vagy bármi mást, amely a szolgáltatásfelhasználó egyszerű felhasználónevétől eltér.

* Ekkor a következő üzenet jelenhet meg: „(GSS-API) An invalid name was supplied.” („(GSS-API) érvénytelen név lett megadva”). Győződjön meg arról, hogy a „p:” szerepel a kiszolgáló SNC-azonosítójának profilparaméter-értékében.

* Ekkor a következő üzenet jelenhet meg: „(SNC error) the specified module could not be found.” („(SNC-hiba) a megadott modul nem található”). Ezt általában az okozza, hogy a `gsskrb5.dll/gx64krb5.dll` olyan helyen található, amelynek hozzáféréséhez megemelt jogosultsági szint (rendszergazdai jogosultság) szükséges.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Átjáróhoz való csatlakozás hibaelhárítása

1. Tekintse meg az átjárónaplókat. Nyissa meg az átjárókonfigurációs alkalmazást, és válassza a **Diagnosztika** > **Naplók exportálása** lehetőséget. A legutóbbi hibák a vizsgált naplófájlok alján jelennek meg.

    ![Képernyőkép a helyszíni adatátjáró alkalmazásról, kiemelt Diagnosztika elemmel](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Kapcsolja be az SAP BW-nyomkövetést, és tekintse át a létrehozott naplófájlokat. Számos különböző típusú SAP BW-nyomkövetés érhető el. Erről további információt az SAP dokumentációjában talál.

## <a name="next-steps"></a>Következő lépések

A **helyszíni adatátjáróval** és a **DirectQueryvel** kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a helyszíni adatátjáró?](/data-integration/gateway/service-gateway-getting-started)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
