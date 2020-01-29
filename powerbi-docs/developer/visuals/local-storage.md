---
title: A helyi tárolási API használata Power BI-vizualizációkban
description: A cikk azt ismerteti, hogyan használható a Power BI-vizualizációs API a böngésző helyi tárterületének eléréséhez
author: uve
ms.author: v-grniki
ms.reviewer: KesemSharabi
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 85517fcd7ec773f947135614c94c0c4e4638ea48
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539325"
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

A helyi tárolási API alapértelmezés szerint nincs aktiválva az egyéni vizualizációkhoz. Ha szeretné aktiválni az egyéni vizualizációhoz, küldjön kérelmet a Power BI egyéni vizualizációkkal foglalkozó ügyfélszolgálatának `pbicvsupport@microsoft.com`.  
**Lényeges, hogy a vizualizációnak az [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals)-ban elérhetőnek és [minősítettnek](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/) kell lennie.**
