---
title: Ne legyenek üres lapok a többoldalas jelentések nyomtatásakor
description: Útmutató többoldalas jelentések tervezéséhez annak érdekében, hogy elkerüljük az üres oldalakat nyomtatáskor.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 349459b95a815a52665e50687554f81f90a9c81b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920841"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Ne legyenek üres lapok a többoldalas jelentések nyomtatásakor

Ez a cikk a [többoldalas](../paginated-reports/paginated-reports-report-builder-power-bi.md) Power BI-jelentéseket megtervező jelentéskészítők számára készült. Javaslatokkal segíti azt, hogy elkerülhesse az üres oldalakat, amikor a jelentést rögzített formátumba, például PDF- vagy Microsoft Word-fájlba exportálja vagy kinyomtatja.

## <a name="page-setup"></a>Oldalbeállítás

A jelentés oldalméret tulajdonsága határozza meg az oldal tájolását, a dimenziókat és a margókat. Ezeket a jelentéstulajdonságokat az alábbi módon érheti el:

- A jelentés **Tulajdonságok oldalának** használatával: Kattintson a jobb gombbal a jelentésvásznon kívüli sötétszürke területre, majd válassza a _Jelentés tulajdonságai_lehetőséget.
- A [**Tulajdonságok** panel](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane) használatával: Kattintson a jelentésvásznon kívüli sötétszürke területre, majd válassza ki a jelentés objektumot. Ügyeljen rá, hogy a **Tulajdonságok** panel meg legyen nyitva.

A **Tulajdonságok oldal** **Oldalbeállítás** oldala egy könnyen használható felületet biztosít, amelyen megtekinthetők és módosíthatók az oldalbeállítás tulajdonságai.

![A képen a Jelentés tulajdonságai ablak látható, melyen ki van emelve az Oldalbeállítás oldal.](media/report-paginated-blank-page/report-page-setup-properties.png)

Ügyeljen rá, hogy az oldalméret minden tulajdonsága megfelelően legyen beállítva:

|Tulajdonság|Javaslat|
|---------|---------|
|Oldalegységek|Válassza ki a megfelelő mértékegységeket – hüvelyk vagy centiméter.|
|Tájolás|Válassza a megfelelő lehetőséget – álló vagy fekvő.|
|Papírméret|Válassza ki a papírméretet, vagy adjon meg egyéni szélességi és magassági értékeket.|
|Margók|Állítsa be a megfelelő értékeket a bal, a jobb, a felső és az alsó margóhoz.|
|||

## <a name="report-body-width"></a>A jelentés törzsének szélessége

Az oldalméret tulajdonságai határozzák meg a jelentés objektumai számára elérhető szabad területet. A jelentésobjektumok lehetnek adatterületek, adatvizualizációk vagy egyéb jelentéselemek.

Az üres lapok gyakran azért jelennek meg, mert a jelentés törzsének szélessége _meghaladja a rendelkezésre álló oldalterületet_.

A jelentés törzsének szélessége csak a **Tulajdonságok** panel használatával tekinthető meg és állítható be. Először kattintson bárhová a jelentés törzsének üres területén.

![A képen a Tulajdonságok panel látható, amelyen ki van emelve a jelentéstörzs szélessége tulajdonság.](media/report-paginated-blank-page/report-body-properties-width.png)

Ügyeljen rá, hogy a szélességi érték ne haladja meg az oldal szélességét. Kövesse az alábbi képletet:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Nem lehet csökkenteni a jelentés törzsének szélességét, ha már szerepelnek jelentésobjektumok az eltávolítani kívánt helyen. Mielőtt csökkentené a szélességet, először át kell helyeznie vagy át kell méreteznie őket.
>
> A jelentés törzsének szélessége automatikusan növekedhet új objektumok hozzáadásakor, illetve a meglévő objektumok átméretezésénél vagy áthelyezésénél. A jelentéskészítő mindig szélesebbre állítja a törzset, hogy az megfeleljen a benne foglalt objektumok pozíciójának és méretének.

## <a name="report-body-height"></a>A jelentés törzsének magassága

Egy másik ok, amiért üres lap jelenhet meg az, hogy a jelentés törzsében az utolsó objektum után még további terület van.

Javasoljuk, hogy mindig csökkentse a törzs magasságát, hogy eltávolítsa a nem használt helyet.

![A képen a jelentéstervezés látható. A táblix adatterülete alatti tér ki van emelve, és szükségtelenként van megjelölve.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Oldaltörési beállítások

Minden adatterület és adatvizualizáció rendelkezik oldaltörési beállításokkal is. Ezek a beállítások a tulajdonságok oldalon vagy a **Tulajdonságok** panelen érhetőek el.

Ügyeljen rá, hogy az **Oldaltörés hozzáadása utána** tulajdonság ne legyen feleslegesen bekapcsolva.

![A képen egy táblix Tulajdonságok ablaka látható. Az „Oldaltörés hozzáadása utána” tulajdonság engedélyezve van.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Tároló üres helyének felhasználása

Ha továbbra is üres oldalak jelennek meg, próbálja meg letiltani a **ConsumeContainerWhitespace** tulajdonságot. Ez csak a **Tulajdonságok** panelen végezhető el.

![A képen a Tulajdonságok ablaktábla látható, amelyen ki van emelve a ConsumeContainerWhitespace tulajdonság.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Alapértelmezés szerint engedélyezve van. Ezzel a beállítással megadható, hogy a tárolókban (például a jelentés törzsében vagy egy téglalapban) lévő minimális üres helyeket kell-e használni. Ez csak a tartalom alatt és az attól jobbra lévő üres helyet érinti.

## <a name="printer-paper-size"></a>Nyomtatópapír mérete

Végül pedig ha a jelentést papírra nyomtatja, ellenőrizze, hogy a nyomtatóba a megfelelő papírt töltötte-e be. A papír fizikai méretének meg kell felelnie a [jelentés papírméretének](#page-setup).

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Mik a lapszámozott jelentések a Power BI Premiumban?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Tördelési mód többoldalas Power BI-jelentésekben](../paginated-reports/paginated-reports-pagination.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com)
