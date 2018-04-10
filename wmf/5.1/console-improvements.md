---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: Förbättringar i administrationskonsolen i WMF 5.1
ms.openlocfilehash: 2abc02010c6c1d9f7fc617e9831b2d1243e0a3ee
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="console-improvements-in-wmf-51"></a>Förbättringar i administrationskonsolen i WMF 5.1#

## <a name="powershell-console-improvements"></a>Förbättringar av PowerShell-konsolen

Följande ändringar har gjorts till powershell.exe i WMF 5.1 att förbättra upplevelsen för konsolen:

###<a name="vt100-support"></a>VT100 stöd

Windows 10 tillagt stöd för [VT100 escape-sekvenser](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignoreras vissa VT100 formatering escape-sekvenser vid beräkning av tabellens bredd.

PowerShell även lagt till ett nytt API som kan användas i koden för att avgöra om VT100 stöds formatering.
Till exempel:

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
Här är en komplett [exempel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) som kan användas för att markera matchar från Välj-sträng.
Spara i exempel i en fil med namnet `MatchInfo.format.ps1xml`, om du vill använda den i din profil eller någon annanstans, kör `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Observera att VT100 escape-sekvenser stöds endast från och med Windows 10 årsdagar uppdateringen. de stöds inte i tidigare versioner.

### <a name="vi-mode-support-in-psreadline"></a>Stöd för vi i PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) lägger till stöd för vi läge. Om du vill använda vi läge kör `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Omdirigerade stdin med interaktiva indata

I tidigare versioner, starta PowerShell med `powershell -File -` krävdes när stdin omdirigerades och du vill ange kommandon interaktivt.

Med WMF 5.1, så svårt att upptäcka alternativet inte längre behövs.
Du kan starta PowerShell utan alternativ, t.ex. `powershell`.

Observera att PSReadline inte stöder för närvarande omdirigeras stdin, och inbyggda kommandoradsverktyget redigera erfarenhet av omdirigerade stdin är mycket begränsad, till exempel piltangenterna fungerar inte.
En framtida utgåvan av PSReadline bör det här problemet.