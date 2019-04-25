---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085269"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="02d1e-102">Uppdateringar till FileInfo-objektet</span><span class="sxs-lookup"><span data-stu-id="02d1e-102">Updates to FileInfo object</span></span>
<span data-ttu-id="02d1e-103">Kan vilseledande filversionsinformation särskilt i fall där filen var korrigeras.</span><span class="sxs-lookup"><span data-stu-id="02d1e-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="02d1e-104">Den här versionen av WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper till FileInfo-objekt.</span><span class="sxs-lookup"><span data-stu-id="02d1e-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="02d1e-105">Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är ID för PowerShell-process):</span><span class="sxs-lookup"><span data-stu-id="02d1e-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
