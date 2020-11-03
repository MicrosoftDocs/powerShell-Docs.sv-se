---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: d4712a945e82a0ba1f2899c679dc0972885de050
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263456"
---
# Set-PSBreakpoint

## SAMMANFATTNING
Anger en Bryt punkt för en linje, ett kommando eller en variabel.

## SYNTAX

### Rad (standard)

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### Kommando

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### Variabel

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## BESKRIVNING

`Set-PSBreakpoint`Cmdleten anger en Bryt punkt i ett skript eller i alla kommando körningar i den aktuella sessionen. Du kan använda `Set-PSBreakpoint` för att ange en Bryt punkt innan du kör ett skript eller kör ett kommando, eller under fel sökning när det stoppas vid en annan Bryt punkt.

`Set-PSBreakpoint` Det går inte att ange en Bryt punkt på en fjärrdator. Om du vill felsöka ett skript på en fjärrdator, kopiera skriptet till den lokala datorn och Felsök det lokalt.

Varje `Set-PSBreakpoint` kommando skapar någon av följande tre typer av Bryt punkter:

- Rad Bryt punkt – anger Bryt punkter vid särskilda rader och kolumn koordinater.
- Kommando Bryt punkt – anger Bryt punkter för kommandon och funktioner.
- Variabel Bryt punkt – anger Bryt punkter för variabler.

Du kan ange en Bryt punkt för flera rader, kommandon eller variabler i ett enda `Set-PSBreakpoint` kommando, men varje `Set-PSBreakpoint` kommando anger bara en typ av Bryt punkt.

Vid en Bryt punkt slutar PowerShell tillfälligt att köra och ger kontroll till fel söknings programmet. Kommando tolken ändras till `DBG\>` och en uppsättning fel söknings kommandon blir tillgängliga för användning. Du kan dock använda **Åtgärds** parametern för att ange ett alternativt svar, till exempel villkor för Bryt punkten eller instruktionerna för att utföra ytterligare åtgärder, till exempel loggning eller diagnostik.

`Set-PSBreakpoint`Cmdleten är en av flera cmdletar utformade för fel sökning av PowerShell-skript.
Mer information om PowerShell-felsökaren finns i [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).

## EXEMPEL

### Exempel 1: Ange en Bryt punkt på en linje

I det här exemplet anges en Bryt punkt på rad 5 i Sample.ps1-skriptet. När skriptet körs stoppar körningen omedelbart innan rad 5 körs.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

När du anger en ny Bryt punkt per rad nummer `Set-PSBreakpoint` genererar cmdleten ett rad Bryt punkts objekt ( **system. Management. Automation. LineBreakpoint** ) som innehåller Bryt punkts-ID och antal träffar.

### Exempel 2: Ange en Bryt punkt för en funktion

I det här exemplet skapas en kommando Bryt punkt för `Increment` funktionen i Sample.ps1 cmdlet. Skriptet slutar att köra omedelbart före varje anrop till den angivna funktionen.

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Resultatet är ett kommando Bryt punkts objekt. Innan skriptet körs är värdet för egenskapen **HitCount** 0.

### Exempel 3: Ange en Bryt punkt för en variabel

I det här exemplet anges en Bryt punkt för **Server** variabeln i Sample.ps1-skriptet. Den använder parametern **mode** med värdet **readwrite** för att stoppa körningen när värdet för variabeln läses och precis innan värdet ändras.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### Exempel 4: Ange en Bryt punkt för varje kommando som börjar med angiven text

I det här exemplet anges en Bryt punkt för varje kommando i Sample.ps1-skriptet som börjar med "Write", till exempel `Write-Host` .

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### Exempel 5: Ange en Bryt punkt beroende på värdet för en variabel

I det här exemplet stoppas körningen i `DiskTest` funktionen i Test.ps1-skriptet endast när värdet för `$Disk` variabeln är större än 2.

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

Värdet för **åtgärden** är ett skript block som testar värdet för `$Disk` variabeln i funktionen.

Åtgärden använder `break` nyckelordet för att stoppa körningen om villkoret är uppfyllt. Alternativet (och standard) är **fortfarande**.

### Exempel 6: Ange en Bryt punkt för en funktion

I det här exemplet anges en Bryt punkt för `CheckLog` funktionen. Eftersom kommandot inte anger något skript, anges Bryt punkten för allt som körs i den aktuella sessionen. Fel söknings verktyget bryts när funktionen anropas, inte när den har deklarerats.

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### Exempel 7: Ange Bryt punkter på flera rader

I det här exemplet anges tre rad Bryt punkter i Sample.ps1-skriptet. Den anger en Bryt punkt i kolumn 2 på var och en av de rader som anges i skriptet. Den åtgärd som anges i parametern **åtgärd** gäller för alla Bryt punkter.

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## PARAMETRAR

### -Åtgärd

Anger kommandon som körs vid varje Bryt punkt i stället för att brytas. Ange ett skript block som innehåller kommandona. Du kan använda den här parametern för att ange villkorliga Bryt punkter eller utföra andra uppgifter, till exempel testning eller loggning.

Om den här parametern utelämnas eller om ingen åtgärd anges, stoppas körningen vid Bryt punkten och fel söknings programmet startar.

När **Åtgärds** parametern används körs åtgärds skript blocket vid varje Bryt punkt. Körningen stoppas inte om inte skript blocket innehåller nyckelordet Break. Om du använder nyckelordet Continue i-skript blocket återupptas körningen tills nästa Bryt punkt.

Mer information finns i [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)och [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kolumn

Anger kolumn numret för kolumnen i skript filen där körningen stoppas. Ange endast ett kolumn nummer. Standardvärdet är kolumn 1.

Kolumnvärdet används med värdet för **rad** parametern för att ange Bryt punkten. Om **rad** parametern anger flera rader, anger **kolumn** parametern en Bryt punkt i den angivna kolumnen på var och en av de angivna raderna. PowerShell slutar att köra före instruktionen eller uttrycket som innehåller tecknen vid den angivna rad-och kolumn positionen.

Kolumner räknas från den övre vänstra marginalen med början på kolumn nummer 1 (inte 0). Om du anger en kolumn som inte finns i skriptet, deklareras inte ett fel, men Bryt punkten körs aldrig.

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kommando

Anger en kommando Bryt punkt. Ange namn på cmdlets, till exempel `Get-Process` eller funktions namn. Jokertecken är tillåtna.

Körningen stoppas precis innan varje instans av varje kommando körs. Om kommandot är en funktion stoppas körningen varje gång funktionen anropas och vid varje BEGIN-, PROCESS-och END-avsnitt.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Rad

Anger en rad Bryt punkt i ett skript. Ange ett eller flera rad nummer, avgränsade med kommatecken. PowerShell stoppas omedelbart innan instruktionen som börjar på var och en av de angivna raderna körs.

Rader räknas från den övre vänstra marginalen för skript filen som börjar med rad nummer 1 (inte 0).
Om du anger en tom rad stoppas körningen före nästa icke-tomma rad. Om raden är utanför intervallet når Bryt punkten aldrig.

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Läge

Anger det åtkomst läge som utlöser variabla Bryt punkter. Standardvärdet är **Write**.

Den här parametern är endast giltig när **variabel** parametern används i kommandot. Läget gäller för alla Bryt punkter som anges i kommandot. De acceptabla värdena för den här parametern är:

- **Write** -stoppar körningen omedelbart innan ett nytt värde skrivs till variabeln.
- **Read** -stoppa körning när variabeln läses, det vill säga när dess värde har använts, antingen för att tilldelas, visas eller användas. I läsläge stoppas inte körningen när värdet på variabeln ändras.
- **Readwrite** – stoppar körningen när variabeln läses eller skrivs.

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Skript

Anger en matris med skriptfiler som denna cmdlet anger en Bryt punkt i. Ange sökvägar och fil namn för en eller flera skriptfiler. Om filerna finns i den aktuella katalogen kan du utelämna sökvägen.
Jokertecken är tillåtna.

Som standard anges variabla Bryt punkter och kommando Bryt punkter för alla kommandon som körs i den aktuella sessionen. Den här parametern krävs endast när du anger en rad Bryt punkt.

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Variabel

Anger en matris med variabler som denna cmdlet anger Bryt punkter för. Ange en kommaavgränsad lista med variabler utan dollar tecken ( `$` ).

Använd parametern **mode** för att fastställa åtkomst läget som utlöser Bryt punkterna. Standard läget, Write, stoppar körningen precis innan ett nytt värde skrivs till variabeln.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka pipe-ininformation till `Set-PSBreakpoint` .

## UTDATA

### Bryt punkts objekt (system. Management. Automation. LineBreakpoint, system. Management. Automation. VariableBreakpoint, system. Management. Automation. CommandBreakpoint)

`Set-PSBreakpoint` Returnerar ett objekt som representerar varje Bryt punkt som den anger.

## ANTECKNINGAR

- `Set-PSBreakpoint` Det går inte att ange en Bryt punkt på en fjärrdator. Om du vill felsöka ett skript på en fjärrdator, kopiera skriptet till den lokala datorn och Felsök det lokalt.
- När du ställer in en Bryt punkt på fler än en rad, ett kommando eller `Set-PSBreakpoint` en variabel, genererar ett Bryt punkts objekt för varje post.
- När du anger en Bryt punkt för en funktion eller variabel i kommando tolken kan du ange Bryt punkten före eller efter att du har skapat funktionen eller variabeln.

## RELATERADE LÄNKAR

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Aktivera – PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

