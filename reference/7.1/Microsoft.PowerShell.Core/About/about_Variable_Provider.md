---
description: Variabel
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variabel leverantör
ms.openlocfilehash: 126ba39db4d7f49e1ec405a73ba4da19c7e877ee
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270141"
---
# <a name="variable-provider"></a>Variabel leverantör

## <a name="provider-name"></a>Providernamn
Variabel

## <a name="drives"></a>Enheter

`Variable:`

## <a name="capabilities"></a>Funktioner

**ShouldProcess**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till PowerShell-variablerna och deras värden.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell- **variabeln** Provider kan du hämta, lägga till, ändra, rensa och ta bort PowerShell-variabler i den aktuella konsolen.

PowerShell- **variabeln** provider stöder variabler som PowerShell skapar, inklusive automatiska variabler, inställningar för variabler och variabler som du skapar.

**Variabeln** Drive är en planad namnrymd som bara innehåller de variabla objekten. Variablerna har inga underordnade objekt.

**Variabeln** provider stöder följande cmdlets, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell innehåller också en uppsättning cmdlets som utformats särskilt för att visa och ändra variabler. När du använder **variabel** -cmdletar behöver du inte ange `Variable:` enheten i namnet. Den här artikeln beskriver inte hur du arbetar med **variabel** -cmdletar.

- [Get-Variable](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [Ny variabel](xref:Microsoft.PowerShell.Utility.New-Variable)
- [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [Ta bort variabel](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> Du kan också använda PowerShell Expression parser för att skapa, Visa och ändra värdena för variabler utan att använda cmdletarna. När du arbetar med variabler direkt använder du ett dollar tecken ( `$` ) för att identifiera namnet som en variabel och tilldelnings operatorn ( `=` ) för att upprätta och ändra värdet. Till exempel `$p = Get-Process` skapar `p` variabeln och lagrar resultatet av ett `Get-Process` kommando i den.

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Variabler kan vara en av flera olika typer. De flesta variabler är instanser av `PSVariable` klassen. Andra variabler och deras typer visas nedan.

- `?`Variabeln är en instans av `QuestionMarkVariable` klassen.
- `null`Variabeln är en instans av `NullVariable` klassen.
- Variablerna för maximalt antal är instanser av `SessionStateCapacityVariable` klassen.
- `LocalVariable` instanser innehåller information om aktuell körning, till exempel:
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a>Navigera mellan variabla enheter

**Variabeln** Provider visar data lagret i `Variable:` enheten. Om du vill arbeta med variabler kan du ändra din plats till `Variable:` enheten ( `Set-Location Variable:` ) eller så kan du arbeta från en annan PowerShell-enhet. Om du vill referera till en variabel från en annan plats använder du enhets namnet ( `Variable:` ) i sökvägen.

```powershell
Set-Location Variable:
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel:

```powershell
Set-Location C:
```

Du kan också arbeta med den **variabla** providern från andra PowerShell-enheter. Om du vill referera till en variabel från en annan plats använder du enhets namnet `Variable:` i sökvägen.

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location). och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="displaying-the-value-of-variables"></a>Visar värdet för variabler

### <a name="get-all-variables-in-the-current-session"></a>Hämta alla variabler i den aktuella sessionen

Det här kommandot hämtar listan över alla variabler och deras värden i den aktuella sessionen. Du kan använda det här kommandot från valfri PowerShell-enhet.

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a>Hämta en variabel med dess Provider-sökväg

Det här kommandot hämtar ett variabel värde med hjälp av dess Provider-sökväg som föregås av dollar tecknet ( `$` ). Detta har samma resultat som när du reparerar variabelns namn med dollar tecknet ( `$` ).

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a>Hämta variabler med jokertecken

Det här kommandot hämtar variablerna med namn som börjar med "Max". Du kan använda det här kommandot från valfri PowerShell-enhet.

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a>Hämta värdet för? variabel

Det här kommandot använder `-LiteralPath` parametern för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) för att hämta värdet för `?` variabeln i `Variable:` enheten. `?`Är ett jokertecken i sökvägar, men `Get-ChildItem` försöker inte matcha jokertecken i värdena för `-LiteralPath` parametern.

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a>Hämta ReadOnly och konstanta variabler

Det här kommandot hämtar de variabler som har värdet `ReadOnly` eller `Constant` för egenskapen **Options** .

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a>Skapa variabler

### <a name="create-a-new-variable"></a>Skapa en ny variabel

Det här kommandot skapar `services` variabeln och lagrar resultatet av ett `Get-Service` kommando i det. Eftersom den aktuella platsen finns i `Variable:` enheten är värdet för `-Path` parametern en punkt ( `.` ) som representerar den aktuella platsen.

Parenteserna runt `Get-Service` kommandot ser till att kommandot utförs innan variabeln skapas. Utan parenteser är värdet för den nya variabeln en "Get-service"-sträng.

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a>Skapa en variabel med en absolut sökväg

Det här kommandot skapar en `services` variabel och lagrar resultatet av ett `Get-Service` kommando i det.

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 Om du vill skapa en variabel utan värde utelämnar du tilldelnings operatorn.

## <a name="changing-variables"></a>Ändra variabler

### <a name="rename-a-variable"></a>Byta namn på en variabel

Det här kommandot använder `Rename-Item` cmdleten för att ändra namnet på `a` variabeln till `processes` .

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a>Ändra värdet för en variabel

Det här kommandot använder `Set-Item` cmdleten för att ändra värdet för `ErrorActionPreference` variabeln till "stoppa".

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a>Kopiera en variabel

Det här kommandot använder `Copy-Item` cmdleten för att kopiera `processes` variabeln till `old_processes` . Detta skapar en ny variabel med namnet `old_processes` som har samma värde som `processes` variabeln.

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a>Ta bort en variabel

Det här kommandot tar bort `serv` variabeln från den aktuella sessionen. Du kan använda det här kommandot i valfri PowerShell-enhet.

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a>Ta bort variabler med parametern-Force

Det här kommandot tar bort alla variabler från den aktuella sessionen, förutom variabler vars **alternativ** -egenskap har värdet `Constant` . Utan `-Force` parametern tar kommandot inte bort variabler vars **alternativ** egenskap har värdet `ReadOnly` .

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a>Ange värdet för en variabel till NULL

Det här kommandot använder `Clear-Item` cmdleten för att ändra värdet för `processes` variabeln till null.

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a>Använda pipelinen

Provider-cmdletar accepterar pipeline-ininformation. Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.
Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.

## <a name="getting-help"></a>Få hjälp

Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.

Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a>Se även

[about_Variables](../About/about_Variables.md)

[about_Automatic_Variables](../About/about_Automatic_Variables.md)

[about_Providers](../About/about_Providers.md)

