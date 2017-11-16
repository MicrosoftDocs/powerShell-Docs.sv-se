---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a>Ny TemporaryFile
Ibland måste du skapa en temporär fil i ett skript. Du kan göra detta med den **ny TemporaryFile** cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\användare\\slee\\AppData\\lokala\\Temp\\tmp375.tmp

