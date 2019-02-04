---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687344"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="7a297-103">Förbättringar i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="7a297-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="7a297-104">Förbättringar i PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a297-104">PowerShell console improvements</span></span>

<span data-ttu-id="7a297-105">Följande ändringar har gjorts till powershell.exe i WMF 5.1 kan förbättra upplevelsen för konsolen:</span><span class="sxs-lookup"><span data-stu-id="7a297-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="7a297-106">VT100 support</span><span class="sxs-lookup"><span data-stu-id="7a297-106">VT100 support</span></span>

<span data-ttu-id="7a297-107">Windows 10 har lagt till stöd för [VT100 escape-sekvenser](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="7a297-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="7a297-108">PowerShell ignorerar vissa VT100 formatering escape-sekvenser vid beräkning av tabellens bredd.</span><span class="sxs-lookup"><span data-stu-id="7a297-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="7a297-109">PowerShell även lagt till ett nytt API som kan användas i formatering kod för att avgöra om VT100 stöds.</span><span class="sxs-lookup"><span data-stu-id="7a297-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="7a297-110">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="7a297-110">For example:</span></span>

```powershell
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

<span data-ttu-id="7a297-111">Här är ett komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchningar från `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="7a297-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="7a297-112">Spara exemplet i en fil med namnet `MatchInfo.format.ps1xml`, kör sedan följande för att använda den i din profil eller någon annanstans, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="7a297-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="7a297-113">Observera att VT100 escape-sekvenser stöds endast från och med Windows 10 Anniversary-uppdateringen. de stöds inte på tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="7a297-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="7a297-114">Stöd för vi i PSReadline</span><span class="sxs-lookup"><span data-stu-id="7a297-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="7a297-115">[PSReadline](https://github.com/lzybkr/PSReadLine) lägger till stöd för vi läge.</span><span class="sxs-lookup"><span data-stu-id="7a297-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="7a297-116">Om du vill använda vi läge kör `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="7a297-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="7a297-117">Omdirigerad stdin med interaktiva indata</span><span class="sxs-lookup"><span data-stu-id="7a297-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="7a297-118">I tidigare versioner, starta PowerShell med `powershell -File -` krävdes när stdin omdirigerades och du vill ange kommandon interaktivt.</span><span class="sxs-lookup"><span data-stu-id="7a297-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="7a297-119">Med WMF 5.1, så svårt att upptäcka alternativet inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="7a297-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="7a297-120">Du kan starta PowerShell utan några alternativ, t.ex. `powershell`.</span><span class="sxs-lookup"><span data-stu-id="7a297-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="7a297-121">Observera att PSReadline inte stöder för närvarande omdirigeras stdin, och den inbyggda kommandoradsverktyget med omdirigerade stdin är ytterst begränsat, till exempel piltangenterna fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="7a297-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="7a297-122">En framtida utgåva av PSReadline bör lösa problemet.</span><span class="sxs-lookup"><span data-stu-id="7a297-122">A future release of PSReadline should address this issue.</span></span>