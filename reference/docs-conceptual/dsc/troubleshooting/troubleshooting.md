---
ms.date: 10/30/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Felsöka DSC
ms.openlocfilehash: 5cbe6496a6e0b9940f4b69e13d1e19e43b3915f0
ms.sourcegitcommit: 5f199cd2a1b31dbcebaab44f2fe496f289831a30
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77478793"
---
# <a name="troubleshooting-dsc"></a>Felsöka DSC

_Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0_

I det här avsnittet beskrivs olika sätt att felsöka DSC när det uppstår problem.

## <a name="winrm-dependency"></a>WinRM-beroende

Windows PowerShell Desired State Configuration (DSC) är beroende av WinRM. WinRM är inte aktiverat som standard på Windows Server 2008 R2 och Windows 7. Kör `Set-WSManQuickConfig`i en upphöjd Windows PowerShell-session för att aktivera WinRM.

## <a name="using-get-dscconfigurationstatus"></a>Använda Get-DscConfigurationStatus

[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) -cmdlet: en hämtar information om konfigurations status från en målnod. Ett omfattande objekt returneras som innehåller information på hög nivå om huruvida konfigurations körningen lyckades eller inte. Du kan göra en inblick i objektet för att identifiera information om konfigurations körningen, till exempel:

- Alla resurser som misslyckats
- Alla resurser som begärde en omstart
- Inställningar för meta-konfiguration vid körning av konfigurations körning
- O.s.v.

Följande parameter uppsättning returnerar statusinformation för den senaste konfigurations körningen:

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
Följande parameter uppsättning returnerar statusinformation för all föregående konfigurations körningar:

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a>Exempel

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Skriptet körs inte: använda DSC-loggar för att diagnostisera skript fel

Precis som all Windows-programvara registrerar DSC fel och händelser i [loggar](/windows/desktop/EventLog/about-event-logging) som kan visas från [Loggboken](https://support.microsoft.com/hub/4338813/windows-help).
Genom att undersöka dessa loggar kan du hjälpa dig att förstå varför en viss åtgärd misslyckades och hur du kan förhindra fel i framtiden. Det kan vara svårt att skriva konfigurations skript, så att det blir enklare att spåra fel när du redigerar, använda DSC-logg resurs för att följa förloppet för din konfiguration i händelse loggen för DSC-analys.

## <a name="where-are-dsc-event-logs"></a>Var finns DSC-händelseloggar?

I Loggboken är DSC-händelser i: **program-och tjänst loggar/Microsoft/Windows/önskad tillstånds konfiguration**

Motsvarande PowerShell-cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), kan också köras för att visa händelse loggarna:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Som visas ovan är DSC: s primära logg namn **Microsoft-> Windows-> DSC** (andra logg namn under Windows visas inte här för det kortfattat). Det primära namnet läggs till i kanal namnet för att skapa det fullständiga logg namnet. DSC-motorn skriver huvudsakligen i tre typer av loggar: [operativa, analytiska och fel söknings loggar](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)). Eftersom de analytiska och fel söknings loggarna är inaktiverade som standard bör du aktivera dem i Loggboken. Det gör du genom att öppna Loggboken genom att skriva show-EventLog i Windows PowerShell; Du kan också klicka på knappen **Starta** , klicka på **kontroll panelen**, klicka på **administrations verktyg**och sedan klicka på **Loggboken**.
I menyn **Visa** i logg boken klickar du på **Visa analytiska loggar och fel söknings loggar**. Logg namnet för den analytiska kanalen är **Microsoft-Windows-DSC/analytisk**och fel söknings kanalen är **Microsoft-Windows-DSC/debug**. Du kan också använda verktyget [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) för att aktivera loggarna, som du ser i följande exempel.

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Vad innehåller DSC-loggar?

DSC-loggar delas av de tre logg kanalerna baserat på meddelandets prioritet. Den operativa loggen i DSC innehåller alla fel meddelanden och kan användas för att identifiera ett problem. Analys loggen har en större mängd händelser och kan identifiera var fel uppstod. Den här kanalen innehåller också utförliga meddelanden (om det finns några). Fel söknings loggen innehåller loggar som kan hjälpa dig att förstå hur fel uppstår. DSC Event-meddelanden är strukturerade så att varje händelse meddelande börjar med ett jobb-ID som unikt representerar en DSC-åtgärd. Exemplet nedan försöker hämta meddelandet från den första händelsen som loggats till den operativa DSC-loggen.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC-händelser loggas i en viss struktur som gör att användaren kan aggregera händelser från ett DSC-jobb. Strukturen är följande:

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a>Samla in händelser från en enskild DSC-åtgärd

DSC-händelseloggar innehåller händelser som genererats av olika DSC-åtgärder. Men du kommer vanligt vis att behöva detaljerna om bara en viss åtgärd. Alla DSC-loggar kan grupperas efter den jobb-ID-egenskap som är unik för varje DSC-åtgärd. Jobb-ID visas som det första egenskap svärdet i alla DSC-händelser. Följande steg beskriver hur du samlar in alla händelser i en grupperad mat ris struktur.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

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

Här kan variabeln `$SeparateDscOperations` innehålla loggar grupperade efter jobb-ID: n. Varje mat ris element i den här variabeln representerar en grupp händelser som loggats av en annan DSC-åtgärd, vilket ger åtkomst till mer information om loggarna.

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

Du kan extrahera data i variabeln `$SeparateDscOperations` med [Where-Object](/powershell/module/microsoft.powershell.core/where-object). Följande är fem scenarier där du kanske vill extrahera data för att felsöka DSC:

### <a name="1-operations-failures"></a>1: åtgärder som misslyckats

Alla händelser har [allvarlighets GRADS nivåer](/windows/desktop/WES/defining-severity-levels). Den här informationen kan användas för att identifiera fel händelser:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: information om åtgärder som körs under den senaste halvtimmen

`TimeCreated`, en egenskap för varje Windows-händelse, anger den tidpunkt då händelsen skapades. Att jämföra den här egenskapen med ett visst datum-/tids objekt kan användas för att filtrera alla händelser:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: meddelanden från den senaste åtgärden

Den senaste åtgärden lagras i det första indexet i mat ris gruppen `$SeparateDscOperations`.
Fråga om gruppens meddelanden för index 0 returnerar alla meddelanden för den senaste åtgärden:

```powershell
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: fel meddelanden loggade för senaste misslyckade åtgärder

`$SeparateDscOperations[0].Group` innehåller en uppsättning händelser för den senaste åtgärden. Kör cmdleten `Where-Object` för att filtrera händelserna baserat på deras nivå visnings namn. Resultaten lagras i `$myFailedEvent`-variabeln, som kan visas ytterligare för att hämta händelse meddelandet:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: alla händelser som genereras för ett visst jobb-ID.

`$SeparateDscOperations` är en uppsättning grupper som har samma namn som det unika jobb-ID: t. Genom att köra `Where-Object`-cmdlet kan du extrahera dessa grupper med händelser som har ett visst jobb-ID:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Använda xDscDiagnostics för att analysera DSC-loggar

**xDscDiagnostics** är en PowerShell-modul som består av flera funktioner som kan hjälpa till att analysera DSC-fel på din dator. Dessa funktioner kan hjälpa dig att identifiera alla lokala händelser från tidigare DSC-åtgärder, eller DSC-händelser på fjärrdatorer (med giltiga autentiseringsuppgifter). Här används termen DSC-åtgärd för att definiera en enskild unik DSC-körning från början till slutet. `Test-DscConfiguration` skulle till exempel vara en separat DSC-åtgärd. På samma sätt kan alla andra cmdlets i DSC (till exempel `Get-DscConfiguration`, `Start-DscConfiguration`osv.) identifieras som separata DSC-åtgärder. Funktionerna förklaras på [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). Hjälp finns tillgängligt genom att köra `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Hämta information om DSC-åtgärder

Med funktionen `Get-xDscOperation` kan du hitta resultaten av de DSC-åtgärder som körs på en eller flera datorer och returnerar ett objekt som innehåller den samling av händelser som har skapats av varje DSC-åtgärd. I följande utdata kördes till exempel tre kommandon. Den första som skickades och de andra två misslyckades. Resultaten sammanfattas i resultatet av `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

Du kan också ange att du bara vill ha resultat för de senaste åtgärderna med hjälp av parametern `Newest`:

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

Cmdleten `Trace-xDscOperation` returnerar ett objekt som innehåller en samling händelser, händelse typer och meddelandets utdata som genererats från en viss DSC-åtgärd. När du upptäcker ett problem i någon av de åtgärder som använder `Get-xDscOperation`skulle du normalt kunna spåra den åtgärden för att ta reda på vilka av händelserna som orsakade ett haveri.

Använd parametern `SequenceID` för att hämta händelser för en speciell åtgärd för en speciell dator.
Om du till exempel anger en `SequenceID` på 9 kan `Trace-xDscOperaion` Hämta spårningen för den DSC-åtgärd som har varit nionde från den senaste åtgärden:

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

Skicka det **GUID** som tilldelats till en speciell DSC-åtgärd (som returneras av `Get-xDscOperation` cmdlet) för att hämta händelse information för den DSC-åtgärden:

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

Observera att eftersom `Trace-xDscOperation` aggregerar händelser från analys-, fel söknings-och drift loggar, uppmanas du att aktivera dessa loggar enligt beskrivningen ovan.

Alternativt kan du samla in information om händelserna genom att spara resultatet av `Trace-xDscOperation` i en variabel. Du kan använda följande kommandon för att visa alla händelser för en viss DSC-åtgärd.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Detta visar samma resultat som `Get-WinEvent` cmdlet, till exempel i följande utdata:

```output
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

Vi rekommenderar att du först använder `Get-xDscOperation` för att visa en lista över de senaste DSC-konfigurationerna som körs på datorerna. På så sätt kan du undersöka en enskild åtgärd (med hjälp av dess SequenceID eller JobID) med `Trace-xDscOperation` för att identifiera vad den gjorde i bakgrunden.

### <a name="getting-events-for-a-remote-computer"></a>Hämta händelser för en fjärrdator

Använd `ComputerName`-parametern för cmdleten `Trace-xDscOperation` för att hämta händelse information på en fjärrdator. Innan du kan göra detta måste du skapa en brand Väggs regel för att tillåta fjärr administration på fjärrdatorn:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

Nu kan du ange att datorn i ditt anrop till `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Mina resurser uppdateras inte: återställa cachen

DSC-motorn cachelagrar resurser som implementerats som en PowerShell-modul i effektivitets syfte.
Detta kan dock orsaka problem när du skapar en resurs och testar den samtidigt eftersom DSC kommer att läsa in den cachelagrade versionen tills processen startas om. Det enda sättet att göra DSC-inläsning av den nyare versionen är att uttryckligen avsluta processen som är värd för DSC-motorn.

När du kör `Start-DscConfiguration`, när du har lagt till och ändrat en anpassad resurs, kanske ändringen inte körs om inte, eller förrän, datorn startas om. Detta beror på att DSC körs i WMI-providerns värd process (WmiPrvSE) och att det vanligt vis finns många instanser av WmiPrvSE som körs samtidigt. När du startar om startas värd processen om och cachen rensas.

För att kunna återvinna konfigurationen och rensa cacheminnet utan att starta om, måste du stoppa och sedan starta om värd processen. Detta kan göras per instans, där du kan identifiera processen, stoppa den och starta om den. Du kan också använda `DebugMode`, enligt nedan, för att läsa in PowerShell DSC-resursen igen.

För att identifiera vilken process som är värd för DSC-motorn och stoppa den per instans, kan du Visa process-ID: t för den WmiPrvSE som är värd för DSC-motorn. Om du sedan vill uppdatera providern stoppar du WmiPrvSE-processen med hjälp av kommandona nedan och kör sedan **Start-DscConfiguration** igen.

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

## <a name="using-debugmode"></a>Använda DebugMode

Du kan konfigurera den lokala DSC-Configuration Manager (LCM) att använda `DebugMode` för att alltid rensa cacheminnet när värd processen startas om. När värdet är **True**, gör det att motorn alltid laddar om PowerShell DSC-resursen. När du har skrivit din resurs kan du ange den till **false** så att motorn återgår till att cachelagra modulerna.

Följande är en demonstration som visar hur `DebugMode` kan uppdatera cacheminnet automatiskt. Först ska vi titta på standard konfigurationen:

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

Du kan se att `DebugMode` har angetts till **"ingen"** .

Om du vill konfigurera `DebugMode` demonstrationen använder du följande PowerShell-resurs:

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

Nu kan du skapa en konfiguration med hjälp av ovanstående resurs som heter `TestProviderDebugMode`:

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

Du kommer att se att innehållet i filen: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` är **1**.

Uppdatera nu leverantörs koden med följande skript:

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

Det här skriptet genererar ett slumpmässigt nummer och uppdaterar leverantörs koden på motsvarande sätt. Om `DebugMode` har angetts till false ändras inte innehållet i filen " **$env: SystemDrive\OutputFromTestProviderDebugMode.txt**".

Ange `DebugMode` till **"ForceModuleImport"** i konfigurations skriptet:

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

När du kör skriptet ovan igen kommer du att se att innehållet i filen är olika varje gång. (Du kan köra `Get-DscConfiguration` för att kontrol lera den). Nedan visas resultatet av två ytterligare körningar (dina resultat kan vara olika när du kör skriptet):

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

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a>DSC returnerar "oväntad svarskod InternalServerError" vid registrering med Windows pull server

När du använder en metaconfiguration på en server för att registrera den med en instans av Windows pull server kan du stöta på följande fel.

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

Detta kan inträffa när certifikatet som används på servern för att kryptera trafik har ett eget namn (CN) som skiljer sig från det DNS-namn som används av noden för att matcha URL: en.
Uppdatera Windows pull Server-instansen för att använda ett certifikat med ett korrigerat namn.

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a>Fel vid körning av Sysprep efter användning av en DSC-konfiguration

När du försöker köra Sysprep för att generalisera en Windows Server efter att ha tillämpat en DSC-konfiguration kan du stöta på följande fel.

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

Att generalisera en server när den har kon figurer ATS med hjälp av Windows PowerShell Desired State Configuration är inte ett scenario som stöds.  Använd i stället konfigurationer för Windows när specialize-fasen i Installationsprogrammet för Windows har slutförts.

## <a name="see-also"></a>Se även

### <a name="concepts"></a>Koncept

- [Bygg anpassade resurser för Desired Configuration för Windows PowerShell](../resources/authoringResource.md)

### <a name="other-resources"></a>Andra resurser

- [Windows PowerShell Desired State Configuration-cmdletar](/powershell/module/psdesiredstateconfiguration/)
