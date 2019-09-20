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
# <a name="console-improvements-in-wmf-51"></a>Konsolförbättringar i WMF 5.1

## <a name="powershell-console-improvements"></a>Förbättringar i PowerShell-konsolen

Följande ändringar har gjorts i PowerShell. exe i WMF 5,1 för att förbättra konsol upplevelsen:

### <a name="vt100-support"></a>VT100-support

Windows 10 har lagt till stöd för [VT100 escape-sekvenser](/windows/console/console-virtual-terminal-sequences).
PowerShell kommer att ignorera vissa VT100-formateringar när du beräknar tabell bredder.

PowerShell har även lagt till ett nytt API som kan användas i formateringsregler för att avgöra om VT100 stöds. Till exempel:

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

Här är ett komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchningar `Select-String`från. Spara exemplet i en fil med namnet `MatchInfo.format.ps1xml`, och Använd den sedan i din profil eller någon annan stans, `Update-FormatData -Prepend MatchInfo.format.ps1xml`kör.

Observera att VT100 escape-sekvenser endast stöds från och med Windows 10 minnes dag uppdatering.
De stöds inte i tidigare system.

### <a name="vi-mode-support-in-psreadline"></a>Läges stöd i PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) lägger till stöd för läget vi. Kör `Set-PSReadlineOption -EditMode Vi`om du vill använda läget för vi.

### <a name="redirected-stdin-with-interactive-input"></a>Omdirigerat STDIN med interaktiva ingångar

I tidigare versioner krävdes PowerShell with `powershell -File -` när STDIN omdirigerades och du ville ange kommandon interaktivt.

Med WMF 5,1 behövs inte längre det här alternativet för att upptäcka. Du kan starta PowerShell utan några alternativ.

Observera att PSReadline inte stöder omdirigeradt STDIN och den inbyggda kommando rads redigerings upplevelsen med Omdirigerad STDIN är mycket begränsad, till exempel fungerar inte piltangenterna. En framtida version av PSReadline bör åtgärda problemet.