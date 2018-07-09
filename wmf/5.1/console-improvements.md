---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892934"
---
# <a name="console-improvements-in-wmf-51"></a>Förbättringar i WMF 5.1

## <a name="powershell-console-improvements"></a>Förbättringar i PowerShell

Följande ändringar har gjorts till powershell.exe i WMF 5.1 kan förbättra upplevelsen för konsolen:

### <a name="vt100-support"></a>VT100 support

Windows 10 har lagt till stöd för [VT100 escape-sekvenser](/windows/console/console-virtual-terminal-sequences).
PowerShell ignorerar vissa VT100 formatering escape-sekvenser vid beräkning av tabellens bredd.

PowerShell även lagt till ett nytt API som kan användas i formatering kod för att avgöra om VT100 stöds.
Till exempel:

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

Här är ett komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchningar från `Select-String`.
Spara exemplet i en fil med namnet `MatchInfo.format.ps1xml`, kör sedan följande för att använda den i din profil eller någon annanstans, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Observera att VT100 escape-sekvenser stöds endast från och med Windows 10 Anniversary-uppdateringen. de stöds inte på tidigare versioner.

### <a name="vi-mode-support-in-psreadline"></a>Stöd för vi i PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) lägger till stöd för vi läge. Om du vill använda vi läge kör `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Omdirigerad stdin med interaktiva indata

I tidigare versioner, starta PowerShell med `powershell -File -` krävdes när stdin omdirigerades och du vill ange kommandon interaktivt.

Med WMF 5.1, så svårt att upptäcka alternativet inte längre behövs.
Du kan starta PowerShell utan några alternativ, t.ex. `powershell`.

Observera att PSReadline inte stöder för närvarande omdirigeras stdin, och den inbyggda kommandoradsverktyget med omdirigerade stdin är ytterst begränsat, till exempel piltangenterna fungerar inte.
En framtida utgåva av PSReadline bör lösa problemet.