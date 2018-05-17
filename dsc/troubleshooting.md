---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Felsöka DSC
ms.openlocfilehash: c08f91b514aae438578fa278228fe5ec879a4012
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="troubleshooting-dsc"></a>Felsöka DSC

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Det här avsnittet beskrivs hur du felsöker DSC när problem uppstår.

## <a name="winrm-dependency"></a>WinRM-beroende

Windows PowerShell önskad tillstånd Configuration (DSC) är beroende av WinRM. WinRM är inte aktiverad som standard i Windows Server 2008 R2 och Windows 7. Kör ```Set-WSManQuickConfig```, utökade sessionen att aktivera WinRM i en Windows PowerShell.

## <a name="using-get-dscconfigurationstatus"></a>Med hjälp av Get-DscConfigurationStatus

Den [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet hämtar information om status för konfiguration från målnoden.
En omfattande objekt returneras som innehåller översiktlig information om huruvida kör konfigurationen lyckades eller inte. Du kan prova objektet för att identifiera information om Kör som-konfiguration:

* Alla resurser som misslyckades
* Alla resurser som har begärt en omstart
* Kör meta-konfigurationsinställningar vid tiden för konfiguration
* osv.

Följande parameteruppsättningen returnerar statusinformation för den senaste konfigurationen som kör:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
Följande parameteruppsättningen returnerar statusinformation för alla tidigare configuration körs:

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a>Exempel

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :
InDesiredState          :   False
InitialState            :
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Min skriptet inte körs: använder DSC loggar för att diagnostisera skriptfel

Alla Windows-program, t.ex. DSC registrerar fel och händelser i [loggar](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) som kan visas från den [Loggboken](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Undersöka dessa loggar hjälper dig att förstå varför en viss åtgärd misslyckades, och förhindra fel i framtiden. Skriva konfigurationsskript kan vara svårt så för att underlätta spårning fel som du författare använder resursen DSC-loggen för att följa förloppet av konfigurationen i analytiska DSC-händelseloggen.

## <a name="where-are-dsc-event-logs"></a>Var finns DSC-händelseloggar?

I Loggboken DSC-händelser finns i: **program och tjänster loggar/Microsoft/Windows/önskade Tillståndskonfiguration**

Motsvarande PowerShell-cmdleten [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), kan också köra om du vill visa händelseloggar:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Visas ovanför DSC-primära loggnamn är **Microsoft -> Windows -> DSC** (andra loggen namn under Windows visas inte här planeringsaspekter). Det primära namnet läggs till Kanalnamn komplett logg namn. DSC-motorn skriver huvudsakligen till tre typer av loggar: [drift, analytiska, loggar och felsökningsloggar](https://technet.microsoft.com/library/cc722404.aspx). Eftersom de analytiska loggar och felsökningsloggar är inaktiverade som standard, bör du aktivera dem i Loggboken. Gör detta genom att öppna Loggboken genom att skriva visa händelseloggen i Windows PowerShell; eller klicka på den **starta** , klicka på **Kontrollpanelen**, klickar du på **Administrationsverktyg**, och klicka sedan på **Loggboken**. På den **visa** Klicka på menyn i Loggboken **visa analytiska loggar och felsökningsloggar**. Namnet på loggen för analytiska kanal är **Microsoft-Windows-Dsc/analytiska**, och debug-kanalen är **Microsoft-Windows-Dsc/Debug**. Du kan också använda den [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) verktyg för att aktivera loggarna, vilket visas i följande exempel.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Vad innehåller DSC loggar?

DSC-loggar delas över de tre loggkanaler baserat på vikten av meddelandet. Arbetsloggen i DSC innehåller alla felmeddelanden och kan användas för att identifiera problem. Analytiska loggen har ett ökat antal händelser och kan identifiera där fel uppstod. Den här kanalen innehåller också utförliga meddelanden (eventuella). Debug-loggen innehåller loggarna som kan hjälpa dig att förstå hur felen inträffade. Händelsemeddelanden för DSC är strukturerade så att varje händelsemeddelande börjar med ett jobb-ID som unikt representerar en DSC-åtgärd. Exemplet nedan försöker att hämta meddelandet från den första händelsen loggas i arbetsloggen i DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC-händelser loggas i en viss struktur som gör att användaren att aggregera händelser från ett DSC-jobb. Strukturen är följande:

**Jobb-ID: <Guid>**
**<Event Message>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Samla in händelser från en enda DSC-åtgärd

DSC-händelseloggarna innehålla händelser som genererats av olika DSC-åtgärder. Du kommer dock vanligtvis att berörda med detaljer om en viss åtgärd. Alla DSC-loggar kan grupperas efter egenskapen jobb-ID som är unik för varje DSC-åtgärd. Jobb-ID visas som det första egenskapsvärdet i alla DSC-händelser. Följande steg förklarar hur du lagra alla händelser i en grupperad matris-struktur.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

Här, variabeln `$SeparateDscOperations` innehåller loggar grupperade efter jobb-ID: N. Varje element i matrisen för den här variabeln representerar en grupp av händelser som loggats av en annan DSC-åtgärd, att tillåta åtkomst till mer information om loggarna.

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

Du kan extrahera data i variabeln `$SeparateDscOperations` med [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Följande är fem scenarier som du kanske vill hämta data för att felsöka DSC:

### <a name="1-operations-failures"></a>1: misslyckade

Alla händelser har [allvarlighetsgrader](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Den här informationen kan användas för att identifiera felhändelser:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: information om åtgärder som körs i senaste halvtimme

`TimeCreated`, en egenskap för varje Windows-händelse, anger den tid som händelsen skapades. Jämföra den här egenskapen med ett visst datum/tid-objekt kan användas för att filtrera alla händelser:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: meddelanden från den senaste åtgärden

Den senaste åtgärden lagras i det första indexet i gruppen matris `$SeparateDscOperations`. Frågar gruppens meddelanden för index 0 returnerar alla meddelanden för den senaste åtgärden:

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: felmeddelanden som loggats för senaste misslyckade åtgärder

`$SeparateDscOperations[0].Group` innehåller en uppsättning händelser för den senaste åtgärden. Kör den `Where-Object` cmdlet för att filtrera händelser utifrån deras nivå visningsnamn. Resultatet lagras i den `$myFailedEvent` variabel, vilket kan medföra ytterligare ut för att få meddelandet:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: alla händelser som genererats för ett specifikt jobb-ID.

`$SeparateDscOperations` är en matris med grupper som har namn som unikt jobb-ID. Genom att köra den `Where-Object` cmdlet, som du kan extrahera de grupperna av händelser som har ett specifikt jobb-ID:

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Med hjälp av xDscDiagnostics att analysera DSC loggar

**xDscDiagnostics** är en PowerShell-modul som består av flera funktioner som kan hjälpa dig att analysera DSC-fel på din dator. Dessa funktioner kan hjälpa dig att identifiera alla lokala händelser från den senaste DSC operations eller DSC-händelser på fjärrdatorer (med giltiga autentiseringsuppgifter). Här används termen DSC-åtgärden för att definiera en enda unika DSC körning från dess start till dess slut. Till exempel `Test-DscConfiguration` skulle vara en separat DSC-åtgärd. På liknande sätt kan alla andra cmdletar i DSC (t.ex `Get-DscConfiguration`, `Start-DscConfiguration`osv) kan varje identifieras som separata DSC-åtgärder. Funktionerna som beskrivs i [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).
Hjälp är tillgänglig genom att köra `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Hämta information om DSC-åtgärder

Den `Get-xDscOperation` funktionen kan du hitta resultaten av DSC-åtgärder som körs på en eller flera datorer och returnerar ett objekt som innehåller samlingen av händelser som genereras av varje DSC-åtgärd.
I följande utdata, till exempel körs tre kommandon. Den första som skickas och de andra två misslyckades. De här resultaten returneras sammanfattas i utdata för `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

Du kan också ange att du vill endast resultat för de senaste åtgärderna med hjälp av den `Newest` parameter:

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>Hämta information om DSC-händelser

Den `Trace-xDscOperation` cmdlet returnerar ett objekt som innehåller en uppsättning händelser, deras händelsetyper och meddelandet utdata genereras från en viss DSC-åtgärd. Vanligtvis när du hittar ett fel i någon av de åtgärder som använder `Get-xDscOperation`, skulle du spåra åtgärden att ta reda på vilka av händelserna som orsakade ett fel.

Använd den `SequenceID` parametern för att hämta händelser för en specifik åtgärd för en specifik dator. Till exempel om du anger en `SequenceID` 9, `Trace-xDscOperaion` hämta spårningen för DSC-åtgärden som var 9: e från den senaste åtgärden:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

Skicka den **GUID** tilldelas en specifik DSC-åtgärd (som returneras av den `Get-xDscOperation` cmldet) att hämta händelseinformation om för den DSC-åtgärden:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

Observera att eftersom `Trace-xDscOperation` aggregerar händelser från analys, felsökning och drift loggar, uppmanas du att aktivera dessa loggar som beskrivs ovan.

Alternativt kan du kan samla in information om händelser genom att spara resultatet av `Trace-xDscOperation` i en variabel. Du kan använda följande kommandon för att visa alla händelser för en viss DSC-åtgärd.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Samma resultat som visas i `Get-WinEvent` cmdlet, exempelvis utdata nedan:

```powershell
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

Helst bör du först använder `Get-xDscOperation` för att lista ut senast några DSC-konfiguration körs på dina datorer. Detta kan du undersöka en enda åtgärd (med dess SequenceID eller JobID) med `Trace-xDscOperation` att identifiera det gjorde i bakgrunden.

### <a name="getting-events-for-a-remote-computer"></a>Hämta händelser för en fjärransluten dator

Använd den `ComputerName` parameter för den `Trace-xDscOperation` för att hämta händelseinformationen på en fjärrdator. Du måste skapa en brandväggsregel för att tillåta fjärradministration på fjärrdatorn innan du kan göra detta:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Nu kan du ange den datorn i anrop till `Trace-xDscOperation`:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Mina resurser inte uppdatera: hur du återställer cachen

DSC-motorn cachelagrar resurser som implementeras som en PowerShell-modul för effektivitet. Detta kan emellertid orsaka problem när du redigerar en resurs och testar samtidigt eftersom DSC kommer att läsa in den cachelagrade versionen tills processen startas. Det enda sättet att läsa in den senare versionen DSC är att uttryckligen avsluta processen som är värd för DSC-motorn.

På liknande sätt, när du kör `Start-DscConfiguration`, efter att lägga till och ändra en anpassad resurs ändringen kanske inte kan köras om eller tills, datorn startas. Detta beror på att DSC körs i värdprocessen för WMI-Provider (WmiPrvSE) och vanligtvis det finns många instanser av WmiPrvSE som körs på samma gång. När du startar om värdprocessen startas och cachen rensats.

Om du vill att återvinna konfigurationen och rensa cachen utan att starta om, måste du stoppa och starta sedan om värdprocessen. Detta kan göras på grundval per instans där du identifiera processen, stoppa och starta om den. Du kan också använda `DebugMode`, som visas nedan, för att läsa in PowerShell DSC-resursen.

För att identifiera vilken process är värd för DSC-motorn och stoppa på grundval av per instans, kan du visa process-ID för WmiPrvSE som är värd för DSC-motorn. Stoppa sedan WmiPrvSE processen med nedanstående kommandon och kör sedan för att uppdatera providern **Start DscConfiguration** igen.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a>Med hjälp av DebugMode

Du kan konfigurera den DSC lokala Configuration Manager (MGM) att använda `DebugMode` att rensa cacheminnet alltid när värdprocessen startas. Om värdet är **SANT**, medför motorn alltid ladda PowerShell DSC-resursen. När du är klar skrivs din resurs, kan du ändra det till **FALSKT** och motorn återgår till sitt beteende av cachelagring moduler.

Följande är en demonstration att visa hur `DebugMode` kan automatiskt uppdatera cachen. Först ska vi titta på standardkonfigurationen:

```
PS C:\> Get-DscLocalConfigurationManager


AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : False
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

Du kan se det `DebugMode` är inställd på **FALSKT**.

Att ställa in den `DebugMode` demonstration, Använd följande PowerShell-resurs:

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

Nu kan skapa en konfiguration med hjälp av ovanstående resursen anropas `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Du kan nu se att innehållet i filen ”:**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” är **1**.

Uppdatera nu providern koden med följande skript:

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Det här skriptet genererar ett slumptal och uppdateras provider-koden. Med `DebugMode` inställt på false, innehållet i filen ”**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” aldrig ändras.

Nu ska du ange `DebugMode` till **SANT** i skriptet konfiguration:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

När du kör skriptet ovan, ser du att innehållet i filen är olika varje gång. (Du kan köra `Get-DscConfiguration` kontrollerar du detta). Nedan visas resultatet av två ytterligare körs (resultaten kan vara annorlunda när du kör skriptet):

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a>Se även

### <a name="reference"></a>Referens
* [DSC-loggen resurs](logResource.md)

### <a name="concepts"></a>Begrepp
* [Skapa anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md)

### <a name="other-resources"></a>Andra resurser
* [Windows PowerShell Desired State Configuration-Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)