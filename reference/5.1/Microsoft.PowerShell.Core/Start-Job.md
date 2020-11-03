---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264141"
---
# Start-Job

## SAMMANFATTNING
Startar ett PowerShell-bakgrunds jobb.

## SYNTAX

### ComputerName (standard)

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### DefinitionName

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### FilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### LiteralFilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## BESKRIVNING

`Start-Job`Cmdleten startar ett PowerShell-bakgrunds jobb på den lokala datorn.

Ett PowerShell-bakgrunds jobb kör ett kommando utan att interagera med den aktuella sessionen. När du startar ett bakgrunds jobb returnerar ett Job-objekt omedelbart, även om jobbet tar lång tid att slutföra. Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.

Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.
När jobbet har slutförts använder du `Receive-Job` cmdleten för att hämta resultatet av jobbet. Mer information om bakgrunds jobb finns [about_Jobs](./About/about_Jobs.md).

Om du vill köra ett bakgrunds jobb på en fjärrdator använder du parametern **AsJob** som är tillgänglig på många cmdletar eller använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på fjärrdatorn. Mer information finns i [about_Remote_Jobs](./About/about_Remote_Jobs.md).

Från och med PowerShell 3,0 `Start-Job` kan instanser av anpassade jobb typer startas, till exempel schemalagda jobb. Information om hur du använder `Start-Job` för att starta jobb med anpassade typer finns i hjälp dokumenten för funktionen jobb typ.

Standard arbets katalogen för jobb är hårdkodad. Windows standard är `$HOME\Documents` och på Linux eller MacOS som standard är `$HOME` . Skript koden som körs i bakgrunds jobbet måste hantera arbets katalogen efter behov.

## EXEMPEL

### Exempel 1: starta ett bakgrunds jobb

I det här exemplet startas ett bakgrunds jobb som körs på den lokala datorn.

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

`Start-Job` använder parametern **script block** för att köras `Get-Process` som ett bakgrunds jobb. Parametern **Name** anger för att hitta PowerShell-processer `powershell` . Jobb informationen visas och PowerShell återgår till en prompt medan jobbet körs i bakgrunden.

Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten. Till exempel `Receive-Job -Id 1`.

### Exempel 2: starta ett jobb med Invoke-Command

I det här exemplet körs ett jobb på flera datorer. Jobbet lagras i en variabel och körs med hjälp av variabel namnet på PowerShell-kommandoraden.

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

Ett jobb som använder `Invoke-Command` skapas och lagras i `$jobWRM` variabeln. `Invoke-Command` använder parametern **computername** för att ange de datorer där jobbet körs. `Get-Content` hämtar Server namnen från `C:\Servers.txt` filen.

Parametern **script block** anger ett kommando som `Get-Service` hämtar **WinRM** -tjänsten. Parametern **JobName** anger ett eget namn för jobbet, **WinRM**. Parametern **ThrottleLimit** begränsar antalet samtidiga kommandon till 16. Parametern **AsJob** startar ett bakgrunds jobb som kör kommandot på servrarna.

### Exempel 3: Hämta jobb information

I det här exemplet får du information om ett jobb och visar resultatet av ett slutfört jobb som kördes på den lokala datorn.

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` använder parametern **script block** för att köra ett kommando som anger `Get-WinEvent` för att hämta **system** loggen. Parametern **Credential** anger ett domän användar konto med behörighet att köra jobbet på datorn. Jobbobjektet lagras i `$j` variabeln.

Objektet i `$j` variabeln skickas nedåt i pipeline till `Select-Object` . **Egenskaps** parametern anger en asterisk ( `*` ) för att visa alla jobb objekt egenskaper.

### Exempel 4: kör ett skript som ett bakgrunds jobb

I det här exemplet körs ett skript på den lokala datorn som ett bakgrunds jobb.

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

`Start-Job` använder parametern **sökväg** för att ange en skript fil som är lagrad på den lokala datorn.

### Exempel 5: få en process med ett bakgrunds jobb

I det här exemplet används ett bakgrunds jobb för att hämta en angiven process efter namn.

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

`Start-Job` använder **namn** parametern för att ange ett eget jobbnamn, **PShellJob**. Parametern **script block** anger `Get-Process` för att hämta processer med namnet **PowerShell**.

### Exempel 6: samla in och spara data med hjälp av ett bakgrunds jobb

I det här exemplet startas ett jobb som samlar in en stor mängd kartdata och sparar den sedan i en `.tif` fil.

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

`Start-Job` använder **namn** parametern för att ange ett eget jobbnamn, **GetMappingFiles**. Parametern **InitializationScript** kör ett skript block som importerar **MapFunctions** -modulen. Parametern **script block** körs `Get-Map` och `Set-Content` sparar data på den plats som anges i parametern **Path** . Parametern **RunAs32** kör processen som 32-bit, även på ett 64-bitars operativ system.

### Exempel 7: skicka in ininformation till ett bakgrunds jobb

I det här exemplet används den `$input` automatiska variabeln för att bearbeta ett indatamängds objekt. Används `Receive-Job` för att Visa jobbets utdata.

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

`Start-Job` använder parametern **script block** för att köra `Get-Content` med den `$input` automatiska variabeln. `$input`Variabeln hämtar objekt från **InputObject** -parametern. `Receive-Job` använder parametern **Name** för att ange jobbet och ger resultatet utdata. Parametern **Keep** sparar jobbets utdata så att den kan visas igen under PowerShell-sessionen.

### Exempel 8: Använd parametern argument list för att ange en matris

I det här exemplet används parametern **argument List** för att ange en matris med argument. Matrisen är en kommaavgränsad lista med process namn.

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

`Start-Job`Cmdleten använder parametern **script block** för att köra ett kommando. `Get-Process` använder parametern **Name** för att ange den automatiska variabeln `$args` . Parametern **argument List** skickar matrisen med process namn till `$args` . Process namnen PowerShell, pwsh och Notepad är processer som körs på den lokala datorn.

Om du vill visa jobbets utdata använder du `Receive-Job` cmdleten. Till exempel `Receive-Job -Id 1`.

## PARAMETRAR

### – Argument List

Anger en matris med argument, eller parameter värden, för det skript som anges av parametern för **Sök väg** eller ett kommando som anges med parametern **script block** .

Argument måste skickas till **argument List** som ett mat ris argument med en dimension. Till exempel en kommaavgränsad lista. Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.

De acceptabla värdena för den här parametern är följande:

- Default
- Basic
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Standardvärdet är default.

CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Om parametern **Credential** inte anges använder kommandot den aktuella användarens autentiseringsuppgifter.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionName

Anger definitions namnet för det jobb som denna cmdlet startar. Använd den här parametern för att starta anpassade jobb typer som har ett definitions namn, till exempel schemalagda jobb.

När du använder `Start-Job` för att starta en instans av ett schemalagt jobb startar jobbet omedelbart, oavsett jobb utlösare eller jobb alternativ. Den resulterande jobb instansen är ett schemalagt jobb, men det sparas inte på disken som utlösta schemalagda jobb. Du kan inte använda parametern **argument List** för `Start-Job` för att ange värden för parametrar för skript som körs i ett schemalagt jobb. Mer information finns i [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionPath

Anger sökvägen till definitionen för jobbet som denna cmdlet startar. Ange definitions Sök vägen. Sammanfogningen av värdena för parametrarna **DefinitionPath** och **DefinitionName** är den fullständigt kvalificerade sökvägen för jobb definitionen. Använd den här parametern för att starta anpassade jobb typer som har en definitions Sök väg, till exempel schemalagda jobb.

För schemalagda jobb är värdet för parametern **DefinitionPath** `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger ett lokalt skript som `Start-Job` körs som ett bakgrunds jobb. Ange sökvägen och fil namnet för skriptet eller Använd pipelinen för att skicka en skript Sök väg till `Start-Job` . Skriptet måste finnas på den lokala datorn eller i en mapp som den lokala datorn kan komma åt.

När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block och kör skript blocket som ett bakgrunds jobb.

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Anger kommandon som körs innan jobbet startas. Om du vill skapa ett skript block, omger du kommandona med klammerparenteser ( `{}` ).

Använd den här parametern för att förbereda sessionen där jobbet körs. Du kan till exempel använda den för att lägga till funktioner, snapin-moduler och moduler i sessionen.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ininformation till kommandot. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som genererar objekten.

I värdet för parametern **script block** använder du den `$input` automatiska variabeln för att representera objekten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger ett lokalt skript som denna cmdlet kör som ett bakgrunds jobb. Ange sökvägen till ett skript på den lokala datorn.

`Start-Job` använder värdet för parametern **LiteralPath** exakt som den skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger ett eget namn för det nya jobbet. Du kan använda namnet för att identifiera jobbet till andra jobb-cmdlet: ar, till exempel `Stop-Job` cmdleten.

Det egna standard namnet är `Job#` , där `#` är ett ordnings tal som ökar för varje jobb.

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PSVersion

Anger en version. `Start-Job` Kör jobbet med PowerShell-versionen. De acceptabla värdena för den här parametern är: `2.0` och `3.0` .

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

Anger att `Start-Job` jobbet körs i en 32-bitars process. **RunAs32** tvingar jobbet att köras i en 32-bitars process, även på ett 64-bitars operativ system.

I 64-bitars versioner av Windows 7 och Windows Server 2008 R2 kan `Start-Job` du inte använda parametern **Credential** för att ange autentiseringsuppgifterna för en annan användare när kommandot innehåller parametern **RunAs32** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block

Anger vilka kommandon som ska köras i bakgrunds jobbet. Om du vill skapa ett skript block, omger du kommandona med klammerparenteser ( `{}` ). Använd den `$input` automatiska variabeln för att få åtkomst till värdet för parametern **InputObject** . Den här parametern är obligatorisk.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Typ

Anger den anpassade typen för jobb som startas av `Start-Job` . Ange ett namn på en anpassad Jobbtyp, till exempel PSScheduledJob för schemalagda jobb eller PSWorkflowJob för arbets flödes jobb. Den här parametern är inte giltig för standard bakgrunds jobb.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan använda pipelinen för att skicka ett objekt med egenskapen **Name** till parametern **Name** . Du kan till exempel pipelina ett **fileinfo** -objekt från `Get-ChildItem` till `Start-Job` .

## UTDATA

### System. Management. Automation. PSRemotingJob

`Start-Job` Returnerar ett **PSRemotingJob** -objekt som representerar det jobb som startades.

## ANTECKNINGAR

För att köra i bakgrunden `Start-Job` körs i en egen session i den aktuella sessionen. När du använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i en session på en fjärrdator `Start-Job` körs i en session i fjärrsessionen.

## RELATERADE LÄNKAR

[about_Arrays](./about/about_arrays.md)

[about_Automatic_Variables](./about/about_automatic_variables.md)

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Hämta jobb](Get-Job.md)

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Återuppta – jobb](Resume-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Pausa – jobb](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
