---
title: Szolgáltatásnév – áttekintés
description: Szolgáltatásnév – áttekintés
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615985"
---
A szolgáltatásnév olyan hitelesítési módszer, amellyel egy Azure AD-alkalmazás hozzáférhet a Power BI szolgáltatásbeli tartalmakhoz és API-khoz.

Azure Active Directory- (Azure AD-) alkalmazás létrehozásakor egy [szolgáltatásnév objektum](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) is létre lesz hozva. A szolgáltatásnév objektum, röviden *szolgáltatásnév* teszi lehetővé az Azure AS számára az alkalmazás hitelesítését. A hitelesítést követően az alkalmazás hozzáférhet az Azure AD-bérlő erőforrásaihoz.

A hitelesítéshez a szolgáltatásnév az Azure AD-alkalmazás *alkalmazásazonosítóját*, és a következők egyikét használja:
* Alkalmazás titkos kódja
* Tanúsítvány