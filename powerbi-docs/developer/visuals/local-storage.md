---
title: A helyi tárolási API használata Power BI-vizualizációkban
description: A cikk azt ismerteti, hogyan használható a Power BI-vizualizációs API a böngésző helyi tárterületének eléréséhez
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879889"
---
# <a name="local-storage-api"></a>Helyi tárolási API

A helyi tárolási API egy olyan API, amellyel az egyéni vizualizációk azt kérhetik a gazdagéptől, hogy adatokat mentsen az eszköz tárterületére, vagy adatokat töltsön be arról. Elszigetelt, abban az értelemben, hogy a különböző vizualizációtípusok tárolóhoz való hozzáférése külön van választva.

## <a name="sample"></a>Minta

Ha az egyéni vizualizációnak a frissítési metódus minden meghívásakor növelnie kell egy számláló értékét, de a számláló értékét meg is kell őrizni, és azt nem szabad a vizualizáció minden indításkor visszaállítani:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Ismert korlátozások és problémák

A helyi tárolási API alapértelmezés szerint nincs aktiválva az egyéni vizualizációkhoz. Ha szeretné aktiválni az egyéni vizualizációhoz, küldjön kérelmet a Power BI egyéni vizualizációkkal foglalkozó ügyfélszolgálatának `pbicvsupport@microsoft.com`
