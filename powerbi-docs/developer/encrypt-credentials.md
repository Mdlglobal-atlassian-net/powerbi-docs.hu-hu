---
title: Hitelesítő adatok titkosítása
description: Lépésenkénti útmutató – Helyszíni átjáró adatforrásaihoz tartozó hitelesítő adatok titkosítása
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836610"
---
# <a name="encrypt-credentials"></a>Hitelesítő adatok titkosítása

Ha egy **vállalati helyszíni átjárón[ a [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) használatával az ](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource)Adatforrás létrehozása[ vagy az ](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)Adatforrás frissítése** utasítást hívja, a hitelesítő adatokat az átjáró nyilvános kulcsával kell titkosítani.

Tekintse meg az alábbi kódpéldát a hitelesítő adatok .NET-ben történő titkosításához.

Az alábbi EncodeCredentials metódushoz megadott hitelesítő adatok formátumának a hitelesítő adatok típusától függően az alábbiak egyikének kell lennie:

**Alapszintű / windowsos hitelesítő adatok**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Kulcshitelesítő adatok**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2 hitelesítő adatok**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Névtelen hitelesítő adatok**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Titkosított hitelesítő adatok**

Titkosítsa a hitelesítő adatok értékét az átjáró nyilvános kulcsával. A különböző átjáróverziók különböző nyilvánoskulcs-mérettel rendelkezhetnek.

Tekintse át az SDK-kód példáját, amely a PowerBI-CSharp GitHub-adattárban érhető el: [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)