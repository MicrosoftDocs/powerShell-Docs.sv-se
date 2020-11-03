---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 96282d28249f28744cf7dff436fa2e6c601c10ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267123"
---
# Debug-Runspace

## SAMMANFATTNING
Startar en interaktiv felsökningssession med en körnings utrymme.

## SYNTAX

### RunspaceParameterSet (standard)

```
Debug-Runspace [-Runspace] <Runspace> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Debug-Runspace [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdParameterSet

```
Debug-Runspace [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Debug-Runspace [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Debug-Runspace`Cmdleten startar en interaktiv felsökningssession med en lokal eller fjärran sluten Active-körnings utrymme. Du kan hitta en körnings utrymme som du vill felsöka genom att först köra `Get-Process` för att hitta processer som är associerade med PowerShell, sedan `Enter-PSHostProcess` med process-ID: t som anges i **ID-** parametern för att ansluta till processen och sedan `Get-Runspace` Visa körnings utrymmen i PowerShell-värd processen.

När du har valt en körnings utrymme för fel sökning, om körnings utrymme för närvarande kör ett kommando eller skript, eller om skriptet har stoppats vid en Bryt punkt, öppnar PowerShell en fjärrfelsökning för körnings utrymme. Du kan felsöka körnings utrymme-skriptet på samma sätt som skripten för fjärrsessioner felsöks.

Du kan bara ansluta till en PowerShell-värd process om du är administratör på datorn som kör processen eller om du kör skriptet som du vill felsöka. Du kan inte heller ange värd processen som kör den aktuella PowerShell-sessionen. Du kan bara ange en värd process som kör en annan PowerShell-session.

## EXEMPEL

### Exempel 1: Felsöka en fjärran sluten körnings utrymme

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

I det här exemplet ska du Felsöka en körnings utrymme som är öppen på en fjärrdator, WS10TestServer. På den första raden i kommandot kan du köra `Get-Process` på fjärrdatorn och filtrera för Windows PowerShell-värd processer. I det här exemplet ska du felsöka process-ID 1152, Windows PowerShell ISE värd processen.

I det andra kommandot kör du `Enter-PSSession` för att öppna en fjärrsession på WS10TestServer. I det tredje kommandot ansluter du till Windows PowerShell ISE värd process som körs på fjärrservern genom att köra `Enter-PSHostProcess` och anger ID: t för den värd process som du fick i det första kommandot 1152.

I det fjärde kommandot visar en lista över tillgängliga körnings utrymmen för process-ID 1152 genom att köra `Get-Runspace` .
Du noterar ID-numret för den upptagna körnings utrymme; Det kör ett skript som du vill felsöka.

I det sista kommandot börjar du Felsöka en öppen körnings utrymme som kör ett skript, TestWFVar1.ps1, genom `Debug-Runspace` att köra och identifiera körnings utrymme med ID, 2, genom att lägga till **ID-** parametern. Eftersom det finns en Bryt punkt i skriptet öppnas fel söknings programmet.

## PARAMETRAR

### -ID

Anger ID-numret för en körnings utrymme. Du kan köra `Get-Runspace` för att Visa körnings utrymme-ID: n.

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Anger en körnings utrymme med dess instans-ID, en GUID som du kan visa genom att köra `Get-Runspace` .

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger en körnings utrymme med hjälp av namnet. Du kan köra `Get-Runspace` för att visa namnen på körnings utrymmen.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Körnings utrymme

Anger ett körnings utrymme-objekt. Det enklaste sättet att ange ett värde för den här parametern är att ange en variabel som innehåller resultatet av ett filtrerat `Get-Runspace` kommando.

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. körnings utrymmen. körnings utrymme

Du kan skicka vidare resultatet av ett `Get-Runspace` kommando för att **Felsöka-körnings utrymme.**

## UTDATA

## ANTECKNINGAR

`Debug-Runspace` fungerar på körnings utrymmen som är i öppet tillstånd. Om ett körnings utrymme tillstånd ändras från öppnat till ett annat tillstånd, tas körnings utrymme bort automatiskt från listan som körs. En körnings utrymme läggs bara till i den aktiva listan om den uppfyller följande kriterier.

- Om det kommer från Invoke-Command; Det har ett `Invoke-Command` GUID-ID.
- Om det kommer från `Debug-Runspace` , det har ett `Debug-Runspace` GUID-ID.
- Om det kommer från ett PowerShell-arbetsflöde och dess jobb-ID för arbets flöde är detsamma som det aktuella aktiva fel söknings jobbets ID för arbets flöde.

## RELATERADE LÄNKAR

[about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[Fel sökning – jobb](../Microsoft.PowerShell.Core/Debug-Job.md)

[Get-körnings utrymme](Get-Runspace.md)

[Hämta process](../Microsoft.PowerShell.Management/Get-Process.md)

[Retur-PSHostProcess](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[Retur-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)
