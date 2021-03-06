---
ms.date: 06/12/2017
title: Konsolförbättringar i WMF 5.1
description: WMF 5,1 lägger till nya funktioner i konsol miljön för Windows PowerShell 5,1.
ms.openlocfilehash: 9a86a2ed4787554e7255bedf1c2ae6e798fefa45
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660758"
---
# <a name="console-improvements-in-wmf-51"></a>Konsolförbättringar i WMF 5.1

## <a name="powershell-console-improvements"></a>Förbättringar i PowerShell-konsolen

Följande ändringar har gjorts i powershell.exe WMF 5,1 för att förbättra konsol upplevelsen:

### <a name="vt100-support"></a>VT100-support

Windows 10 har lagt till stöd för [VT100 escape-sekvenser](/windows/console/console-virtual-terminal-sequences).
PowerShell kommer att ignorera vissa VT100-formateringar när du beräknar tabell bredder.

PowerShell har även lagt till ett nytt API som kan användas i formateringsregler för att avgöra om VT100 stöds. Exempel:

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

Här är ett komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchningar från `Select-String` . Spara exemplet i en fil med namnet `MatchInfo.format.ps1xml` , och Använd den sedan i din profil eller någon annan stans, kör `Update-FormatData -Prepend MatchInfo.format.ps1xml` .

Observera att VT100 escape-sekvenser endast stöds från och med Windows 10 minnes dag uppdatering.
De stöds inte i tidigare system.

### <a name="vi-mode-support-in-psreadline"></a>Läges stöd i PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) lägger till stöd för läget vi. Kör om du vill använda läget för vi `Set-PSReadlineOption -EditMode Vi` .

### <a name="redirected-stdin-with-interactive-input"></a>Omdirigerat STDIN med interaktiva ingångar

I tidigare versioner krävdes PowerShell with `powershell -File -` när STDIN omdirigerades och du ville ange kommandon interaktivt.

Med WMF 5,1 behövs inte längre det här alternativet för att upptäcka. Du kan starta PowerShell utan några alternativ.

Observera att PSReadline inte stöder omdirigeradt STDIN och den inbyggda kommando rads redigerings upplevelsen med Omdirigerad STDIN är mycket begränsad, till exempel fungerar inte piltangenterna. En framtida version av PSReadline bör åtgärda problemet.
