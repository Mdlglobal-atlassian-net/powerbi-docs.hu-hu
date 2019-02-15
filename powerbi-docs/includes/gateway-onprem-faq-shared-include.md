## <a name="general"></a>Általános
**Kérdés:** Mi a neve a konkrét Windows-szolgáltatásnak?  
**Válasz:** A Szolgáltatások eszközben az átjáró helyszíni adatátjáró szolgáltatásként jelenik meg

**Kérdés:** Milyen követelmények vonatkoznak az átjáróra?  
**Válasz:** Tekintse meg az [átjárókkal foglalkozó cikk](../service-gateway-onprem.md) követelményeket ismertető szakaszát.

**Kérdés:** Milyen adatforrásokat támogat az átjáró?  
**Válasz:** Tekintse meg az [átjárókkal foglalkozó cikk](../service-gateway-onprem.md) adatforrásokat tartalmazó táblázatát.

**Kérdés:** Szükséges átjáró a felhőben található adatforrásokhoz, például az Azure SQL Database-hez?  
**Válasz:** Nem. A szolgáltatás átjáró nélkül is tud csatlakozni az adatforráshoz.

**Kérdés:** Léteznek a felhőből az átjáró felé irányuló bemenő kapcsolatok?  
**Válasz:** Nem. Az átjáró kimenő kapcsolatokat használ az Azure Service Bushoz.

**Kérdés:** Mi történik, ha letiltom a kimenő kapcsolatokat? Mit kell megnyitnom?  
**Válasz:** Tekintse át az átjáró által használt gazdagépek és [portok listáját](../service-gateway-onprem.md#ports).

**Kérdés:** Az átjárót ugyanarra a gépre kell telepíteni, mint az adatforrást?  
**Válasz:** Nem. Az átjáró a megadott kapcsolatadatokkal kapcsolódik az adatforráshoz. Ebben az értelemben az átjáró egyfajta ügyfélalkalmazásnak tekinthető. Csupán a megadott kiszolgáló nevéhez kell sikeresen kapcsolódnia.

**Kérdés:** Mennyi a lekérdezések futtatásának késése az adatforrás és az átjáró között? Mi a legjobb architektúra?  
**Válasz:** A hálózati késés csökkentése érdekében ajánlott az adatforráshoz minél közelebb telepíteni az átjárót. Ha az átjárót a tényleges adatforrásra is tudja telepíteni, az minimálisra csökkenti a késést. Vegye figyelembe az adatközpontokat is. Például ha a szolgáltatás az USA nyugati régiójának adatközpontját használja, és rendelkezik egy Azure-beli virtuális gépen üzemeltetett SQL Serverrel, akkor javasolt az USA nyugati régiójára állítani az Azure VM-et is. Ez a minimálisra csökkenti a késést, és elkerülheti az Azure-beli virtuális gépen a kimenő adatforgalom díját.

**Kérdés:** Vannak a hálózati sávszélességgel kapcsolatos követelmények?  
**Válasz:** Nagy átviteli sebességű hálózati kapcsolat használatát ajánljuk. Minden környezet más, és az eredmény az elküldött adatok mennyiségétől is függ. Az ExpressRoute használata segíti a teljesítmény szintjének garantálását a helyszíni és az Azure-beli adatközpontok között.

A teljesítmény kiszámításához használhatja a harmadik féltől származó [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) alkalmazást.

**Kérdés:** Futtatható az átjáró Windows-szolgáltatás Azure Active Directory-fiókkal?  
**Válasz:** Nem. A Windows-szolgáltatáshoz szükség van egy érvényes Windows-fiókra. Alapértelmezés szerint a szolgáltatás biztonsági azonosítójával fut: *NT SERVICE\PBIEgwService*.

**Kérdés:** Hogyan kerülnek vissza az eredmények a felhőbe?  
**Válasz:** Ez az Azure Service Bus használatával történik. A további tudnivalókat lásd: [hogyan működik](../service-gateway-onprem.md#how-the-gateway-works).

**Kérdés:** Hol vannak tárolva a hitelesítő adataim?  
**Válasz:** Az adatforráshoz megadott hitelesítő adatait az átjáró felhőszolgáltatása tárolja titkosított formában. A hitelesítő adatok visszafejtése a helyszínen az átjárón történik.

**Kérdés:** Elhelyezhetek-e átjárót szegélyhálózaton (vagy más néven DMZ vagy demilitarizált zónában)?  
**Válasz:** Az átjárónak csatlakoznia kell az adatforráshoz. Ha az adatforrás nem érhető el a szegélyhálózaton, akkor előfordulhat, hogy az átjáró nem tud hozzá csatlakozni. Lehetséges például, hogy az SQL-kiszolgáló nem a szegélyhálózaton van. És a szegélyhálózatról nem tud csatlakozni az SQL-kiszolgálóhoz. A szegélyhálózaton elhelyezett átjáró nem tudná elérni az SQL-kiszolgálót.

**Kérdés:** Elő lehet írni az átjárónak, hogy ne TCP, hanem HTTPS protokollal kommunikáljon az Azure Service Busszal?  
**Válasz:** Igen. Ez azonban nagymértékben csökkenti a teljesítményt. Ebben az esetben módosítania kell a *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* fájlt. Az `AutoDetect` értéket módosítania kell `Https` értékre. A fájl alapértelmezett helye: *C:\Program Files\On-premises data gateway*.

**Kérdés:** Engedélyeznem kell az Azure Datacenter IP-címlistáját? Hol találom ezt a listát?  
**Válasz:** Ha blokkolja a kimenő IP-forgalmat, lehetséges, hogy engedélyeznie kell az Azure Datacenter IP-címlistáját. Jelenleg az átjáró az IP-cím és a teljes tartománynév használatával kommunikál az Azure Service Busszal. Az Azure Datacenter IP-címlistája hetente frissül. [A Microsoft Azure Datacenter IP-címlistáját innen töltheti le](https://www.microsoft.com/download/details.aspx?id=41653).

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Magas rendelkezésre állás/vészhelyreállítás
**Kérdés:** Tervezik a magas rendelkezésre állás elérésének lehetővé tételét az átjárók esetében?  
**Válasz:** Igen, a Power BI csapata aktívan dolgozik ennek a területnek a fejlesztésén. A szolgáltatással kapcsolatos hírekért kövessen bennünket a [Power BI-blogon](https://powerbi.microsoft.com/blog/).

**Kérdés:** Milyen vészhelyreállítási lehetőségek érhetők el?  
**Válasz:** A helyreállítási kulcs használatával elvégezheti egy átjáró visszaállítását vagy áthelyezését. Az átjáró telepítésekor adja meg a helyreállítási kulcsot.

**Kérdés:** Milyen előnyökkel jár a helyreállítási kulcs használata?  
**Válasz:** Lehetővé teszi az átjáró beállításainak migrálását és helyreállítását. Ez vészhelyreállítás esetén is használható.

## <a name="troubleshooting"></a>Hibaelhárítás
**Kérdés:** Hol tárolja a rendszer az átjáró naplóit?  
**Válasz:** További részleteket a [hibaelhárításról szóló cikk](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting) eszközöket tárgyaló szakaszában talál.

**Kérdés:** Hogyan tekinthetem meg a helyszíni adatforrásra éppen elküldött lekérdezéseket?  
**Válasz:** Engedélyezheti a lekérdezések nyomon követését.  Ez magában foglalja az éppen elküldött lekérdezéseket is. A hibaelhárítás végrehajtása után ne felejtse el visszaállítani az eredeti értékre. Ha továbbra is engedélyezi a lekérdezések nyomon követését, a naplók mérete megnő.

Megtekintheti az adatforrások számára rendelkezésre álló, lekérdezések nyomon követésére használt eszközöket is. Például az SQL Serverhez és az Analysis Serviceshez használhatja az Extended Eventset vagy az SQL Profilert.

