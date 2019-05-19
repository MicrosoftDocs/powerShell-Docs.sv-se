---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856219"
---
# <a name="console-improvements-in-wmf-51"></a>Förbättringar i WMF 5.1

## <a name="powershell-console-improvements"></a>Förbättringar i PowerShell

Följande ändringar har gjorts till powershell.exe i WMF 5.1 kan förbättra upplevelsen för konsolen:

### <a name="vt100-support"></a>VT100 support

Windows 10 har lagt till stöd för [VT100 escape-sekvenser](/windows/console/console-virtual-terminal-sequences).
PowerShell ignorerar vissa VT100 formatering escape-sekvenser vid beräkning av tabellens bredd.

PowerShell även lagt till ett nytt API som kan användas i formatering kod för att avgöra om VT100 stöds. Till exempel:

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

Här är ett komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchningar från `Select-String`. Spara exemplet i en fil med namnet `MatchInfo.format.ps1xml`, kör sedan följande för att använda den i din profil eller någon annanstans, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Observera att VT100 escape-sekvenser stöds endast från och med Windows 10 Anniversary-uppdateringen.
De stöds inte på tidigare versioner.

### <a name="vi-mode-support-in-psreadline"></a>Stöd för vi i PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) lägger till stöd för vi läge. Om du vill använda vi läge kör `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Omdirigerad stdin med interaktiva indata

I tidigare versioner, starta PowerShell med `powershell -File -` krävdes när stdin omdirigerades och du vill ange kommandon interaktivt.

Med WMF 5.1, så svårt att upptäcka alternativet inte längre behövs. Du kan starta PowerShell utan några alternativ.

Observera att PSReadline inte stöder omdirigeras stdin, och den inbyggda kommandoradsverktyget med omdirigerade stdin är ytterst begränsat, till exempel piltangenterna fungerar inte. En framtida utgåva av PSReadline bör lösa problemet.