---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685916"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="58588-102">NoNewLine-parametern</span><span class="sxs-lookup"><span data-stu-id="58588-102">NoNewLine parameter</span></span>
<span data-ttu-id="58588-103">**Out-File**, **Lägg till innehåll**, och **Set-innehåll** har nu en ny **– NoNewline** växeln som utesluter helt enkelt en ny rad efter utdatan.</span><span class="sxs-lookup"><span data-stu-id="58588-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="58588-104">Utan **– NoNewline** anges varje fragment är på en separat rad:</span><span class="sxs-lookup"><span data-stu-id="58588-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
