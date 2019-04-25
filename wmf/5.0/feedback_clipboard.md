---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057306"
---
# <a name="clipboard-cmdlets"></a>Urklipps-cmdletar
**Get-Urklipp** och **Set-Urklipp** gör det enklare att överföra innehåll till och från en Windows PowerShell-session. Exempel: Om du använder Windows Explorer för att kopiera tre filer till Urklipp (genom att markera dem och trycka på `ctrl-c`, till exempel), du kan sedan enkelt komma åt innehållet i Urklipp som en lista över filer:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Urklipps-cmdletar har stöd för bilder, ljudfiler, fillistor och text.
