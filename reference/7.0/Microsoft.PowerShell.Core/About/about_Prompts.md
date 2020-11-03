---
description: Beskriver `Prompt` funktionen och visar hur du skapar en anpassad `Prompt` funktion.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3e1496c84fa528b4673a770b5b2777fc3d31dc34
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270021"
---
# <a name="about-prompts"></a>Om prompter

## <a name="short-description"></a>Kort beskrivning
Beskriver `Prompt` funktionen och visar hur du skapar en anpassad `Prompt` funktion.

## <a name="long-description"></a>Lång beskrivning

PowerShell-Kommandotolken visar att PowerShell är redo att köra ett kommando:

```
PS C:\>
```

PowerShell-prompten bestäms av den inbyggda `Prompt` funktionen. Du kan anpassa prompten genom att skapa en egen `Prompt` funktion och spara den i din PowerShell-profil.

## <a name="about-the-prompt-function"></a>Om funktionen prompt

`Prompt`Funktionen bestämmer utseendet på PowerShell-prompten.
PowerShell innehåller en inbyggd `Prompt` funktion, men du kan åsidosätta den genom att definiera en egen `Prompt` funktion.

`Prompt`Funktionen har följande syntax:

```powershell
function Prompt { <function-body> }
```

`Prompt`Funktionen måste returnera ett objekt. Vi rekommenderar att du returnerar en sträng eller ett objekt som är formaterat som en sträng. Den högsta rekommenderade längden är 80 tecken.

Följande funktion returnerar till exempel `Prompt` en "Hello, World"-sträng följt av en höger vinkel paren tes ( `>` ).

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a>Hämtar prompt-funktionen

Hämta `Prompt` funktionen genom att använda `Get-Command` cmdleten eller använda `Get-Item` cmdleten i funktions enheten.

Ett exempel:

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

Om du vill hämta skriptet som anger värdet för prompten använder du punkt metoden för att hämta egenskapen **script block** för `Prompt` funktionen.

Ett exempel:

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

Precis som alla funktioner `Prompt` lagras funktionen i `Function:` enheten.
Om du vill visa skriptet som skapar den aktuella `Prompt` funktionen skriver du:

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a>Standard frågan

Standard frågan visas bara när `Prompt` funktionen genererar ett fel eller inte returnerar något objekt.

Standard frågan om PowerShell är:

```
PS>
```

Följande kommando anger till exempel `Prompt` funktionen till `$null` , som är ogiltig. Därför visas standard meddelandet.

```powershell
PS C:\> function prompt {$null}
PS>
```

Eftersom PowerShell innehåller en inbyggd prompt visas normalt inte standard meddelandet.

### <a name="built-in-prompt"></a>Inbyggd prompt

PowerShell innehåller en inbyggd `Prompt` funktion.

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

Funktionen använder `Test-Path` cmdleten för att avgöra om den `$PSDebugContext` automatiska variabeln är ifylld. Om `$PSDebugContext` är ifylld är du i fel söknings läge och `[DBG]:` läggs till i prompten enligt följande:

```Output
[DBG]: PS C:\ps-test>
```

Om `$PSDebugContext` inte har fyllts i, läggs funktionen `PS` till i prompten.
Och funktionen använder `Get-Location` cmdleten för att hämta aktuell katalog plats för fil systemet. Sedan lägger den till en höger vinkel paren tes ( `>` ).

Ett exempel:

```Output
PS C:\ps-test>
```

Om du är i en kapslad prompt lägger funktionen till två vinkelparenteser ( `>>` ) i prompten. (Du är i en kapslad prompt om värdet för den `$NestedPromptLevel` automatiska variabeln är större än 1.)

Om du till exempel felsöker i en kapslad prompt liknar prompten följande fråga:

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a>Ändringar i prompten

`Enter-PSSession`Cmdleten prepends namnet på fjärrdatorn till den aktuella `Prompt` funktionen. När du använder `Enter-PSSession` cmdleten för att starta en session med en fjärrdator, ändras kommando tolken så att den innehåller namnet på fjärrdatorn. Ett exempel:

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

Andra PowerShell-värdprogram och alternativa gränssnitt kan ha sina egna anpassade kommando tolkar.

Mer information om de `$PSDebugContext` `$NestedPromptLevel` automatiska variablerna och finns i [about_Automatic_Variables](about_Automatic_Variables.md).

### <a name="how-to-customize-the-prompt"></a>Anpassa prompten

Om du vill anpassa prompten skriver du en ny `Prompt` funktion. Funktionen är inte skyddad, så du kan skriva över den.

Skriv följande om du vill skriva en `Prompt` funktion:

```powershell
function prompt { }
```

Ange sedan de kommandon eller den sträng som skapar din prompt mellan klammerparenteserna.

Följande prompt innehåller till exempel ditt dator namn:

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

På Server01-datorn liknar prompten följande prompt:

```Output
PS [Server01] >
```

Följande `Prompt` funktion innehåller aktuellt datum och tid:

```powershell
function prompt {"$(Get-Date)> "}
```

Prompten liknar följande prompt:

```Output
03/15/2012 17:49:47>
```

Du kan också ändra standard `Prompt` funktionen:

Till exempel läggs följande ändrade `Prompt` funktion till i `[ADMIN]:` den inbyggda PowerShell-prompten när PowerShell öppnas med alternativet **Kör som administratör** :

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

När du startar PowerShell med alternativet **Kör som administratör** visas ett meddelande som liknar följande meddelande:

```Output
[ADMIN]: PS C:\ps-test>
```

Följande `Prompt` funktion visar historik-ID för nästa kommando. Om du vill visa kommando historiken använder du `Get-History` cmdleten.

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

Följande prompt använder `Write-Host` `Get-Random` cmdletarna och för att skapa en prompt som ändrar färg slumpmässigt. Eftersom `Write-Host` skrivningar till det aktuella värd programmet, men inte returnerar ett objekt, innehåller den här funktionen en `Return` instruktion. Utan den, använder PowerShell standard frågan `PS>` .

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a>Spara prompt-funktionen

Precis som vilken funktion som helst `Prompt` finns funktionen bara i den aktuella sessionen. Om du vill spara `Prompt` funktionen i framtida sessioner lägger du till den i dina PowerShell-profiler. Mer information om profiler finns [about_Profiles](about_Profiles.md).

## <a name="see-also"></a>Se även

[Get-location](xref:Microsoft.PowerShell.Management.Get-Location)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Hämta historik](xref:Microsoft.PowerShell.Core.Get-History)

[Hämta slumpmässiga](xref:Microsoft.PowerShell.Utility.Get-Random)

[Skriv värd](xref:Microsoft.PowerShell.Utility.Write-Host)

[about_Profiles](about_Profiles.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Debuggers](about_Debuggers.md)

[about_Automatic_Variables](about_Automatic_Variables.md)
