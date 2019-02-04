---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685118"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Ibland måste du skapa en temporär fil i ett skript. Du kan göra detta med den **New TemporaryFile** cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\användare\\slee\\AppData\\lokala\\Temp\\tmp375.tmp
