---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217999"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Ibland måste du skapa en temporär fil i ett skript. Du kan göra detta med den **ny TemporaryFile** cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\användare\\slee\\AppData\\lokala\\Temp\\tmp375.tmp
