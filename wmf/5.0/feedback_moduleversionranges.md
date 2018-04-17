---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="e783f-102">Moduler som har stöd för deklarerar versioner som stöds (1.\* osv)</span><span class="sxs-lookup"><span data-stu-id="e783f-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="e783f-103">I kombination med **- MinimumVersion**, **- MaximumVersion** nu kan användare get/import-module inom ett visst intervall.</span><span class="sxs-lookup"><span data-stu-id="e783f-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="e783f-104">Parametern stöder också **.** \*.</span><span class="sxs-lookup"><span data-stu-id="e783f-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="e783f-105">I följande exempel visas hur det fungerar:</span><span class="sxs-lookup"><span data-stu-id="e783f-105">The following example shows how it works:</span></span>

<span data-ttu-id="e783f-106">Nu kan du kombinera **- MinimumVersion** och **- MaximumVersion** importera modul i särskilda intervall:</span><span class="sxs-lookup"><span data-stu-id="e783f-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
