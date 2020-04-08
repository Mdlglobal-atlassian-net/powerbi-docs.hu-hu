---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621577"
---
A szolgáltatásnév olyan hitelesítési módszer, amellyel egy Azure AD-alkalmazás hozzáférhet a Power BI szolgáltatásbeli tartalmakhoz és API-khoz.

Azure Active Directory- (Azure AD-) alkalmazás létrehozásakor egy [szolgáltatásnév objektum](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) is létre lesz hozva. A szolgáltatásnév objektum, röviden *szolgáltatásnév* teszi lehetővé az Azure AS számára az alkalmazás hitelesítését. A hitelesítést követően az alkalmazás hozzáférhet az Azure AD-bérlő erőforrásaihoz.

A hitelesítéshez a szolgáltatásnév az Azure AD-alkalmazás *alkalmazásazonosítóját*, és a következők egyikét használja:
* Alkalmazás titkos kódja
* Tanúsítvány