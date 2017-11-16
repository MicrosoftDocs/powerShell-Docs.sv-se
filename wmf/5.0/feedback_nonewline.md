---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 4d32ced8e75042f494477408424b97be8958854e
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="nonewline-parameter"></a><span data-ttu-id="269db-102">NoNewLine parameter</span><span class="sxs-lookup"><span data-stu-id="269db-102">NoNewLine parameter</span></span>
<span data-ttu-id="269db-103">**Out-File**, **Lägg till innehåll**, och **Set-innehåll** har nu en ny **– NoNewline** växeln som bara tar bort en ny rad efter utdatan.</span><span class="sxs-lookup"><span data-stu-id="269db-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="269db-104">Utan **– NoNewline** anges varje fragment skulle vara på en separat rad:</span><span class="sxs-lookup"><span data-stu-id="269db-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

