---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Konsolförbättringar i WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145056"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="fa4be-103">Konsolförbättringar i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="fa4be-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="fa4be-104">Förbättringar i PowerShell-konsolen</span><span class="sxs-lookup"><span data-stu-id="fa4be-104">PowerShell console improvements</span></span>

<span data-ttu-id="fa4be-105">Följande ändringar har gjorts i PowerShell. exe i WMF 5,1 för att förbättra konsol upplevelsen:</span><span class="sxs-lookup"><span data-stu-id="fa4be-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="fa4be-106">VT100-support</span><span class="sxs-lookup"><span data-stu-id="fa4be-106">VT100 support</span></span>

<span data-ttu-id="fa4be-107">Windows 10 har lagt till stöd för [VT100 escape-sekvenser](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="fa4be-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="fa4be-108">PowerShell kommer att ignorera vissa VT100-formateringar när du beräknar tabell bredder.</span><span class="sxs-lookup"><span data-stu-id="fa4be-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="fa4be-109">PowerShell har även lagt till ett nytt API som kan användas i formateringsregler för att avgöra om VT100 stöds.</span><span class="sxs-lookup"><span data-stu-id="fa4be-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="fa4be-110">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="fa4be-110">For example:</span></span>

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

<span data-ttu-id="fa4be-111">Här är ett komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchningar `Select-String`från.</span><span class="sxs-lookup"><span data-stu-id="fa4be-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="fa4be-112">Spara exemplet i en fil med namnet `MatchInfo.format.ps1xml`, och Använd den sedan i din profil eller någon annan stans, `Update-FormatData -Prepend MatchInfo.format.ps1xml`kör.</span><span class="sxs-lookup"><span data-stu-id="fa4be-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="fa4be-113">Observera att VT100 escape-sekvenser endast stöds från och med Windows 10 minnes dag uppdatering.</span><span class="sxs-lookup"><span data-stu-id="fa4be-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="fa4be-114">De stöds inte i tidigare system.</span><span class="sxs-lookup"><span data-stu-id="fa4be-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="fa4be-115">Läges stöd i PSReadline</span><span class="sxs-lookup"><span data-stu-id="fa4be-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="fa4be-116">[PSReadline](https://github.com/PowerShell/PSReadLine) lägger till stöd för läget vi.</span><span class="sxs-lookup"><span data-stu-id="fa4be-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="fa4be-117">Kör `Set-PSReadlineOption -EditMode Vi`om du vill använda läget för vi.</span><span class="sxs-lookup"><span data-stu-id="fa4be-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="fa4be-118">Omdirigerat STDIN med interaktiva ingångar</span><span class="sxs-lookup"><span data-stu-id="fa4be-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="fa4be-119">I tidigare versioner krävdes PowerShell with `powershell -File -` när STDIN omdirigerades och du ville ange kommandon interaktivt.</span><span class="sxs-lookup"><span data-stu-id="fa4be-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="fa4be-120">Med WMF 5,1 behövs inte längre det här alternativet för att upptäcka.</span><span class="sxs-lookup"><span data-stu-id="fa4be-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="fa4be-121">Du kan starta PowerShell utan några alternativ.</span><span class="sxs-lookup"><span data-stu-id="fa4be-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="fa4be-122">Observera att PSReadline inte stöder omdirigeradt STDIN och den inbyggda kommando rads redigerings upplevelsen med Omdirigerad STDIN är mycket begränsad, till exempel fungerar inte piltangenterna.</span><span class="sxs-lookup"><span data-stu-id="fa4be-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="fa4be-123">En framtida version av PSReadline bör åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="fa4be-123">A future release of PSReadline should address this issue.</span></span>