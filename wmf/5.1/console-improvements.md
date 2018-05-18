---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i administrationskonsolen i WMF 5.1
ms.openlocfilehash: fb689002caf42203d760f11acc64e52cfa681069
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="909f0-103">Förbättringar i administrationskonsolen i WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="909f0-103">Console Improvements in WMF 5.1#</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="909f0-104">Förbättringar av PowerShell-konsolen</span><span class="sxs-lookup"><span data-stu-id="909f0-104">PowerShell console improvements</span></span>

<span data-ttu-id="909f0-105">Följande ändringar har gjorts till powershell.exe i WMF 5.1 att förbättra upplevelsen för konsolen:</span><span class="sxs-lookup"><span data-stu-id="909f0-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="909f0-106">VT100 stöd</span><span class="sxs-lookup"><span data-stu-id="909f0-106">VT100 support</span></span>

<span data-ttu-id="909f0-107">Windows 10 tillagt stöd för [VT100 escape-sekvenser](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="909f0-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="909f0-108">PowerShell ignoreras vissa VT100 formatering escape-sekvenser vid beräkning av tabellens bredd.</span><span class="sxs-lookup"><span data-stu-id="909f0-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="909f0-109">PowerShell även lagt till ett nytt API som kan användas i koden för att avgöra om VT100 stöds formatering.</span><span class="sxs-lookup"><span data-stu-id="909f0-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="909f0-110">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="909f0-110">For example:</span></span>

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
<span data-ttu-id="909f0-111">Här är en komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchar från Välj-sträng.</span><span class="sxs-lookup"><span data-stu-id="909f0-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="909f0-112">Spara i exempel i en fil med namnet `MatchInfo.format.ps1xml`, om du vill använda den i din profil eller någon annanstans, kör `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="909f0-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="909f0-113">Observera att VT100 escape-sekvenser stöds endast från och med Windows 10 årsdagar uppdateringen. de stöds inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="909f0-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="909f0-114">Stöd för vi i PSReadline</span><span class="sxs-lookup"><span data-stu-id="909f0-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="909f0-115">[PSReadline](https://github.com/lzybkr/PSReadLine) lägger till stöd för vi läge.</span><span class="sxs-lookup"><span data-stu-id="909f0-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="909f0-116">Om du vill använda vi läge kör `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="909f0-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="909f0-117">Omdirigerade stdin med interaktiva indata</span><span class="sxs-lookup"><span data-stu-id="909f0-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="909f0-118">I tidigare versioner, starta PowerShell med `powershell -File -` krävdes när stdin omdirigerades och du vill ange kommandon interaktivt.</span><span class="sxs-lookup"><span data-stu-id="909f0-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="909f0-119">Med WMF 5.1, så svårt att upptäcka alternativet inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="909f0-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="909f0-120">Du kan starta PowerShell utan alternativ, t.ex. `powershell`.</span><span class="sxs-lookup"><span data-stu-id="909f0-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="909f0-121">Observera att PSReadline inte stöder för närvarande omdirigeras stdin, och inbyggda kommandoradsverktyget redigera erfarenhet av omdirigerade stdin är mycket begränsad, till exempel piltangenterna fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="909f0-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="909f0-122">En framtida utgåvan av PSReadline bör det här problemet.</span><span class="sxs-lookup"><span data-stu-id="909f0-122">A future release of PSReadline should address this issue.</span></span>
