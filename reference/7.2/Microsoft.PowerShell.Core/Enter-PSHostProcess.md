---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 85cbc9d012781873dddaf2a7d220a0e478dcbda2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709594"
---
# Enter-PSHostProcess

## SAMMANFATTNING
Ansluter till och går in i en interaktiv session med en lokal process.

## SYNTAX

### ProcessIdParameterSet (standard)

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessParameterSet

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### PSHostProcessInfoParameterSet

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### PipeNameParameterSet

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## BESKRIVNING

`Enter-PSHostProcess`Cmdleten ansluter till och går in i en interaktiv session med en lokal process. Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.

I stället för att skapa en ny process som är värd för PowerShell och köra en fjärrsession, körs den interaktiva sessionen i en befintlig process som redan kör PowerShell. När du interagerar med en fjärrsession i en angiven process kan du räkna upp körnings körnings utrymmen och sedan välja en körnings utrymme för att felsöka genom att köra antingen `Debug-Runspace` eller `Enable-RunspaceDebug` .

Den process som du vill ange måste vara värd för PowerShell (System.Management.Automation.dll).
Du måste antingen vara medlem i gruppen Administratörer på den dator där processen finns, eller så måste du vara den användare som kör skriptet som startade processen.

När du har valt en körnings utrymme för fel sökning öppnas en fjärrfelsökning för körnings utrymme om den antingen kör ett kommando eller stoppas i fel söknings programmet. Du kan sedan felsöka körnings utrymme-skriptet på samma sätt som du felsöker andra skript för fjärrsessioner.

Koppla från en felsökningssession och sedan den interaktiva sessionen med processen, genom att avsluta två gånger, eller stoppa skript körningen genom att köra det befintliga fel söknings kommandot avsluta.

Om du anger en process med hjälp av **namn** parametern, och det bara finns en process med det angivna namnet, anges processen. Om mer än en process med det angivna namnet hittas returnerar PowerShell ett fel och visar en lista över alla processer med det angivna namnet.

För att stödja anslutning till processer på fjärrdatorer `Enter-PSHostProcess` är cmdleten aktive rad på en angiven fjärrdator, så att du kan ansluta till en lokal process inom en fjärran sluten PowerShell-session.

## EXEMPEL

### Exempel 1: starta fel sökning av en körnings utrymme i PowerShell ISE-processen

I det här exemplet ska du köra `Enter-PSHostProcess` från PowerShell-konsolen för att ange POWERSHELL ISE-processen. I den resulterande interaktiva sessionen kan du hitta en körnings utrymme som du vill felsöka genom att köra `Get-Runspace` och sedan felsöka körnings utrymme.

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## PARAMETRAR

### -AppDomainName

Anger ett program domän namn som ska anslutas till om det utelämnas används **DefaultAppDomain**. Används `Get-PSHostProcessInfo` för att Visa programmets domän namn.

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostProcessInfo

Anger ett **PSHostProcessInfo** -objekt som kan anslutas till med PowerShell. Används `Get-PSHostProcessInfo` för att hämta objektet.

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ID

Anger en process med process-ID. Kör cmdleten för att hämta ett process-ID `Get-Process` .

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger en process efter process namnet. Kör cmdleten för att få ett process namn `Get-Process` . Du kan också hämta process namn från dialog rutan Egenskaper för en process i aktivitets hanteraren.

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Process

Anger en process av objektet process. Det enklaste sättet att använda den här parametern är att spara resultatet av ett `Get-Process` kommando som returnerar en process som du vill ange i en variabel och sedan ange variabeln som värde för den här parametern.

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CustomPipeName

Hämtar eller anger namnet på den anpassade namngivna pipe som ska anslutas till. Detta används vanligt vis tillsammans med `pwsh -CustomPipeName` .

Den här parametern introducerades i PowerShell 6,2.

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Diagnostics. process

## UTDATA

## ANTECKNINGAR

`Enter-PSHostProcess` Det går inte att ange processen för PowerShell-sessionen där du kör kommandot. Du kan dock ange processen för en annan PowerShell-session eller en PowerShell ISE-session som körs samtidigt som den session där du kör `Enter-PSHostProcess` .

`Enter-PSHostProcess` kan bara ange de processer som är värdar för PowerShell. Det vill säga att de har läst in PowerShell-motorn.

Om du vill avsluta en process inifrån processen skriver du **exit** och trycker på <kbd>RETUR</kbd>.

Före PowerShell 7,1 har fjärr kommunikation via SSH inte stöd för andra hopp-fjärrsessioner. Den här funktionen var begränsad till sessioner som använder WinRM. PowerShell 7,1 tillåter `Enter-PSSession` och `Enter-PSHostProcess` fungerar inifrån en interaktiv fjärrsession.

## RELATERADE LÄNKAR

[Avsluta-PSHostProcess](Exit-PSHostProcess.md)

[Get-PSHostProcessInfo](Get-PSHostProcessInfo.md)

