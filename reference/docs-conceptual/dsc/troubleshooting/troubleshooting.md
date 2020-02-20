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
# <a name="troubleshooting-dsc"></a><span data-ttu-id="4a15c-103">Felsöka DSC</span><span class="sxs-lookup"><span data-stu-id="4a15c-103">Troubleshooting DSC</span></span>

<span data-ttu-id="4a15c-104">_Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0_</span><span class="sxs-lookup"><span data-stu-id="4a15c-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="4a15c-105">I det här avsnittet beskrivs olika sätt att felsöka DSC när det uppstår problem.</span><span class="sxs-lookup"><span data-stu-id="4a15c-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="4a15c-106">WinRM-beroende</span><span class="sxs-lookup"><span data-stu-id="4a15c-106">WinRM Dependency</span></span>

<span data-ttu-id="4a15c-107">Windows PowerShell Desired State Configuration (DSC) är beroende av WinRM.</span><span class="sxs-lookup"><span data-stu-id="4a15c-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="4a15c-108">WinRM är inte aktiverat som standard på Windows Server 2008 R2 och Windows 7.</span><span class="sxs-lookup"><span data-stu-id="4a15c-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="4a15c-109">Kör `Set-WSManQuickConfig`i en upphöjd Windows PowerShell-session för att aktivera WinRM.</span><span class="sxs-lookup"><span data-stu-id="4a15c-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="4a15c-110">Använda Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="4a15c-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="4a15c-111">[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) -cmdlet: en hämtar information om konfigurations status från en målnod.</span><span class="sxs-lookup"><span data-stu-id="4a15c-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="4a15c-112">Ett omfattande objekt returneras som innehåller information på hög nivå om huruvida konfigurations körningen lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="4a15c-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="4a15c-113">Du kan göra en inblick i objektet för att identifiera information om konfigurations körningen, till exempel:</span><span class="sxs-lookup"><span data-stu-id="4a15c-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="4a15c-114">Alla resurser som misslyckats</span><span class="sxs-lookup"><span data-stu-id="4a15c-114">All of the resources that failed</span></span>
- <span data-ttu-id="4a15c-115">Alla resurser som begärde en omstart</span><span class="sxs-lookup"><span data-stu-id="4a15c-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="4a15c-116">Inställningar för meta-konfiguration vid körning av konfigurations körning</span><span class="sxs-lookup"><span data-stu-id="4a15c-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="4a15c-117">O.s.v.</span><span class="sxs-lookup"><span data-stu-id="4a15c-117">Etc.</span></span>

<span data-ttu-id="4a15c-118">Följande parameter uppsättning returnerar statusinformation för den senaste konfigurations körningen:</span><span class="sxs-lookup"><span data-stu-id="4a15c-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="4a15c-119">Följande parameter uppsättning returnerar statusinformation för all föregående konfigurations körningar:</span><span class="sxs-lookup"><span data-stu-id="4a15c-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="4a15c-120">Exempel</span><span class="sxs-lookup"><span data-stu-id="4a15c-120">Example</span></span>

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="4a15c-121">Skriptet körs inte: använda DSC-loggar för att diagnostisera skript fel</span><span class="sxs-lookup"><span data-stu-id="4a15c-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="4a15c-122">Precis som all Windows-programvara registrerar DSC fel och händelser i [loggar](/windows/desktop/EventLog/about-event-logging) som kan visas från [Loggboken](https://support.microsoft.com/hub/4338813/windows-help).</span><span class="sxs-lookup"><span data-stu-id="4a15c-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="4a15c-123">Genom att undersöka dessa loggar kan du hjälpa dig att förstå varför en viss åtgärd misslyckades och hur du kan förhindra fel i framtiden.</span><span class="sxs-lookup"><span data-stu-id="4a15c-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="4a15c-124">Det kan vara svårt att skriva konfigurations skript, så att det blir enklare att spåra fel när du redigerar, använda DSC-logg resurs för att följa förloppet för din konfiguration i händelse loggen för DSC-analys.</span><span class="sxs-lookup"><span data-stu-id="4a15c-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="4a15c-125">Var finns DSC-händelseloggar?</span><span class="sxs-lookup"><span data-stu-id="4a15c-125">Where are DSC event logs?</span></span>

<span data-ttu-id="4a15c-126">I Loggboken är DSC-händelser i: **program-och tjänst loggar/Microsoft/Windows/önskad tillstånds konfiguration**</span><span class="sxs-lookup"><span data-stu-id="4a15c-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="4a15c-127">Motsvarande PowerShell-cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), kan också köras för att visa händelse loggarna:</span><span class="sxs-lookup"><span data-stu-id="4a15c-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="4a15c-128">Som visas ovan är DSC: s primära logg namn **Microsoft-> Windows-> DSC** (andra logg namn under Windows visas inte här för det kortfattat).</span><span class="sxs-lookup"><span data-stu-id="4a15c-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="4a15c-129">Det primära namnet läggs till i kanal namnet för att skapa det fullständiga logg namnet.</span><span class="sxs-lookup"><span data-stu-id="4a15c-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="4a15c-130">DSC-motorn skriver huvudsakligen i tre typer av loggar: [operativa, analytiska och fel söknings loggar](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="4a15c-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="4a15c-131">Eftersom de analytiska och fel söknings loggarna är inaktiverade som standard bör du aktivera dem i Loggboken.</span><span class="sxs-lookup"><span data-stu-id="4a15c-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="4a15c-132">Det gör du genom att öppna Loggboken genom att skriva show-EventLog i Windows PowerShell; Du kan också klicka på knappen **Starta** , klicka på **kontroll panelen**, klicka på **administrations verktyg**och sedan klicka på **Loggboken**.</span><span class="sxs-lookup"><span data-stu-id="4a15c-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="4a15c-133">I menyn **Visa** i logg boken klickar du på **Visa analytiska loggar och fel söknings loggar**.</span><span class="sxs-lookup"><span data-stu-id="4a15c-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="4a15c-134">Logg namnet för den analytiska kanalen är **Microsoft-Windows-DSC/analytisk**och fel söknings kanalen är **Microsoft-Windows-DSC/debug**.</span><span class="sxs-lookup"><span data-stu-id="4a15c-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="4a15c-135">Du kan också använda verktyget [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) för att aktivera loggarna, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="4a15c-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="4a15c-136">Vad innehåller DSC-loggar?</span><span class="sxs-lookup"><span data-stu-id="4a15c-136">What do DSC logs contain?</span></span>

<span data-ttu-id="4a15c-137">DSC-loggar delas av de tre logg kanalerna baserat på meddelandets prioritet.</span><span class="sxs-lookup"><span data-stu-id="4a15c-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="4a15c-138">Den operativa loggen i DSC innehåller alla fel meddelanden och kan användas för att identifiera ett problem.</span><span class="sxs-lookup"><span data-stu-id="4a15c-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="4a15c-139">Analys loggen har en större mängd händelser och kan identifiera var fel uppstod.</span><span class="sxs-lookup"><span data-stu-id="4a15c-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="4a15c-140">Den här kanalen innehåller också utförliga meddelanden (om det finns några).</span><span class="sxs-lookup"><span data-stu-id="4a15c-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="4a15c-141">Fel söknings loggen innehåller loggar som kan hjälpa dig att förstå hur fel uppstår.</span><span class="sxs-lookup"><span data-stu-id="4a15c-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="4a15c-142">DSC Event-meddelanden är strukturerade så att varje händelse meddelande börjar med ett jobb-ID som unikt representerar en DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="4a15c-143">Exemplet nedan försöker hämta meddelandet från den första händelsen som loggats till den operativa DSC-loggen.</span><span class="sxs-lookup"><span data-stu-id="4a15c-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="4a15c-144">DSC-händelser loggas i en viss struktur som gör att användaren kan aggregera händelser från ett DSC-jobb.</span><span class="sxs-lookup"><span data-stu-id="4a15c-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="4a15c-145">Strukturen är följande:</span><span class="sxs-lookup"><span data-stu-id="4a15c-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="4a15c-146">Samla in händelser från en enskild DSC-åtgärd</span><span class="sxs-lookup"><span data-stu-id="4a15c-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="4a15c-147">DSC-händelseloggar innehåller händelser som genererats av olika DSC-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="4a15c-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="4a15c-148">Men du kommer vanligt vis att behöva detaljerna om bara en viss åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="4a15c-149">Alla DSC-loggar kan grupperas efter den jobb-ID-egenskap som är unik för varje DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="4a15c-150">Jobb-ID visas som det första egenskap svärdet i alla DSC-händelser.</span><span class="sxs-lookup"><span data-stu-id="4a15c-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="4a15c-151">Följande steg beskriver hur du samlar in alla händelser i en grupperad mat ris struktur.</span><span class="sxs-lookup"><span data-stu-id="4a15c-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

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

<span data-ttu-id="4a15c-152">Här kan variabeln `$SeparateDscOperations` innehålla loggar grupperade efter jobb-ID: n.</span><span class="sxs-lookup"><span data-stu-id="4a15c-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="4a15c-153">Varje mat ris element i den här variabeln representerar en grupp händelser som loggats av en annan DSC-åtgärd, vilket ger åtkomst till mer information om loggarna.</span><span class="sxs-lookup"><span data-stu-id="4a15c-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="4a15c-154">Du kan extrahera data i variabeln `$SeparateDscOperations` med [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="4a15c-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="4a15c-155">Följande är fem scenarier där du kanske vill extrahera data för att felsöka DSC:</span><span class="sxs-lookup"><span data-stu-id="4a15c-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="4a15c-156">1: åtgärder som misslyckats</span><span class="sxs-lookup"><span data-stu-id="4a15c-156">1: Operations failures</span></span>

<span data-ttu-id="4a15c-157">Alla händelser har [allvarlighets GRADS nivåer](/windows/desktop/WES/defining-severity-levels).</span><span class="sxs-lookup"><span data-stu-id="4a15c-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="4a15c-158">Den här informationen kan användas för att identifiera fel händelser:</span><span class="sxs-lookup"><span data-stu-id="4a15c-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="4a15c-159">2: information om åtgärder som körs under den senaste halvtimmen</span><span class="sxs-lookup"><span data-stu-id="4a15c-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="4a15c-160">`TimeCreated`, en egenskap för varje Windows-händelse, anger den tidpunkt då händelsen skapades.</span><span class="sxs-lookup"><span data-stu-id="4a15c-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="4a15c-161">Att jämföra den här egenskapen med ett visst datum-/tids objekt kan användas för att filtrera alla händelser:</span><span class="sxs-lookup"><span data-stu-id="4a15c-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="4a15c-162">3: meddelanden från den senaste åtgärden</span><span class="sxs-lookup"><span data-stu-id="4a15c-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="4a15c-163">Den senaste åtgärden lagras i det första indexet i mat ris gruppen `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="4a15c-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="4a15c-164">Fråga om gruppens meddelanden för index 0 returnerar alla meddelanden för den senaste åtgärden:</span><span class="sxs-lookup"><span data-stu-id="4a15c-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="4a15c-165">4: fel meddelanden loggade för senaste misslyckade åtgärder</span><span class="sxs-lookup"><span data-stu-id="4a15c-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="4a15c-166">`$SeparateDscOperations[0].Group` innehåller en uppsättning händelser för den senaste åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4a15c-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="4a15c-167">Kör cmdleten `Where-Object` för att filtrera händelserna baserat på deras nivå visnings namn.</span><span class="sxs-lookup"><span data-stu-id="4a15c-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="4a15c-168">Resultaten lagras i `$myFailedEvent`-variabeln, som kan visas ytterligare för att hämta händelse meddelandet:</span><span class="sxs-lookup"><span data-stu-id="4a15c-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="4a15c-169">5: alla händelser som genereras för ett visst jobb-ID.</span><span class="sxs-lookup"><span data-stu-id="4a15c-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="4a15c-170">`$SeparateDscOperations` är en uppsättning grupper som har samma namn som det unika jobb-ID: t.</span><span class="sxs-lookup"><span data-stu-id="4a15c-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="4a15c-171">Genom att köra `Where-Object`-cmdlet kan du extrahera dessa grupper med händelser som har ett visst jobb-ID:</span><span class="sxs-lookup"><span data-stu-id="4a15c-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="4a15c-172">Använda xDscDiagnostics för att analysera DSC-loggar</span><span class="sxs-lookup"><span data-stu-id="4a15c-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="4a15c-173">**xDscDiagnostics** är en PowerShell-modul som består av flera funktioner som kan hjälpa till att analysera DSC-fel på din dator.</span><span class="sxs-lookup"><span data-stu-id="4a15c-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="4a15c-174">Dessa funktioner kan hjälpa dig att identifiera alla lokala händelser från tidigare DSC-åtgärder, eller DSC-händelser på fjärrdatorer (med giltiga autentiseringsuppgifter).</span><span class="sxs-lookup"><span data-stu-id="4a15c-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="4a15c-175">Här används termen DSC-åtgärd för att definiera en enskild unik DSC-körning från början till slutet.</span><span class="sxs-lookup"><span data-stu-id="4a15c-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="4a15c-176">`Test-DscConfiguration` skulle till exempel vara en separat DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="4a15c-177">På samma sätt kan alla andra cmdlets i DSC (till exempel `Get-DscConfiguration`, `Start-DscConfiguration`osv.) identifieras som separata DSC-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="4a15c-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="4a15c-178">Funktionerna förklaras på [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="4a15c-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="4a15c-179">Hjälp finns tillgängligt genom att köra `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="4a15c-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="4a15c-180">Hämta information om DSC-åtgärder</span><span class="sxs-lookup"><span data-stu-id="4a15c-180">Getting details of DSC operations</span></span>

<span data-ttu-id="4a15c-181">Med funktionen `Get-xDscOperation` kan du hitta resultaten av de DSC-åtgärder som körs på en eller flera datorer och returnerar ett objekt som innehåller den samling av händelser som har skapats av varje DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="4a15c-182">I följande utdata kördes till exempel tre kommandon.</span><span class="sxs-lookup"><span data-stu-id="4a15c-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="4a15c-183">Den första som skickades och de andra två misslyckades.</span><span class="sxs-lookup"><span data-stu-id="4a15c-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="4a15c-184">Resultaten sammanfattas i resultatet av `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="4a15c-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="4a15c-185">Du kan också ange att du bara vill ha resultat för de senaste åtgärderna med hjälp av parametern `Newest`:</span><span class="sxs-lookup"><span data-stu-id="4a15c-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

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

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="4a15c-186">Hämta information om DSC-händelser</span><span class="sxs-lookup"><span data-stu-id="4a15c-186">Getting details of DSC events</span></span>

<span data-ttu-id="4a15c-187">Cmdleten `Trace-xDscOperation` returnerar ett objekt som innehåller en samling händelser, händelse typer och meddelandets utdata som genererats från en viss DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="4a15c-188">När du upptäcker ett problem i någon av de åtgärder som använder `Get-xDscOperation`skulle du normalt kunna spåra den åtgärden för att ta reda på vilka av händelserna som orsakade ett haveri.</span><span class="sxs-lookup"><span data-stu-id="4a15c-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="4a15c-189">Använd parametern `SequenceID` för att hämta händelser för en speciell åtgärd för en speciell dator.</span><span class="sxs-lookup"><span data-stu-id="4a15c-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="4a15c-190">Om du till exempel anger en `SequenceID` på 9 kan `Trace-xDscOperaion` Hämta spårningen för den DSC-åtgärd som har varit nionde från den senaste åtgärden:</span><span class="sxs-lookup"><span data-stu-id="4a15c-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

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

<span data-ttu-id="4a15c-191">Skicka det **GUID** som tilldelats till en speciell DSC-åtgärd (som returneras av `Get-xDscOperation` cmdlet) för att hämta händelse information för den DSC-åtgärden:</span><span class="sxs-lookup"><span data-stu-id="4a15c-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

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

<span data-ttu-id="4a15c-192">Observera att eftersom `Trace-xDscOperation` aggregerar händelser från analys-, fel söknings-och drift loggar, uppmanas du att aktivera dessa loggar enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="4a15c-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="4a15c-193">Alternativt kan du samla in information om händelserna genom att spara resultatet av `Trace-xDscOperation` i en variabel.</span><span class="sxs-lookup"><span data-stu-id="4a15c-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="4a15c-194">Du kan använda följande kommandon för att visa alla händelser för en viss DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="4a15c-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="4a15c-195">Detta visar samma resultat som `Get-WinEvent` cmdlet, till exempel i följande utdata:</span><span class="sxs-lookup"><span data-stu-id="4a15c-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

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

<span data-ttu-id="4a15c-196">Vi rekommenderar att du först använder `Get-xDscOperation` för att visa en lista över de senaste DSC-konfigurationerna som körs på datorerna.</span><span class="sxs-lookup"><span data-stu-id="4a15c-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="4a15c-197">På så sätt kan du undersöka en enskild åtgärd (med hjälp av dess SequenceID eller JobID) med `Trace-xDscOperation` för att identifiera vad den gjorde i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="4a15c-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="4a15c-198">Hämta händelser för en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="4a15c-198">Getting events for a remote computer</span></span>

<span data-ttu-id="4a15c-199">Använd `ComputerName`-parametern för cmdleten `Trace-xDscOperation` för att hämta händelse information på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="4a15c-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="4a15c-200">Innan du kan göra detta måste du skapa en brand Väggs regel för att tillåta fjärr administration på fjärrdatorn:</span><span class="sxs-lookup"><span data-stu-id="4a15c-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="4a15c-201">Nu kan du ange att datorn i ditt anrop till `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="4a15c-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="4a15c-202">Mina resurser uppdateras inte: återställa cachen</span><span class="sxs-lookup"><span data-stu-id="4a15c-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="4a15c-203">DSC-motorn cachelagrar resurser som implementerats som en PowerShell-modul i effektivitets syfte.</span><span class="sxs-lookup"><span data-stu-id="4a15c-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="4a15c-204">Detta kan dock orsaka problem när du skapar en resurs och testar den samtidigt eftersom DSC kommer att läsa in den cachelagrade versionen tills processen startas om.</span><span class="sxs-lookup"><span data-stu-id="4a15c-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="4a15c-205">Det enda sättet att göra DSC-inläsning av den nyare versionen är att uttryckligen avsluta processen som är värd för DSC-motorn.</span><span class="sxs-lookup"><span data-stu-id="4a15c-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="4a15c-206">När du kör `Start-DscConfiguration`, när du har lagt till och ändrat en anpassad resurs, kanske ändringen inte körs om inte, eller förrän, datorn startas om.</span><span class="sxs-lookup"><span data-stu-id="4a15c-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="4a15c-207">Detta beror på att DSC körs i WMI-providerns värd process (WmiPrvSE) och att det vanligt vis finns många instanser av WmiPrvSE som körs samtidigt.</span><span class="sxs-lookup"><span data-stu-id="4a15c-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="4a15c-208">När du startar om startas värd processen om och cachen rensas.</span><span class="sxs-lookup"><span data-stu-id="4a15c-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="4a15c-209">För att kunna återvinna konfigurationen och rensa cacheminnet utan att starta om, måste du stoppa och sedan starta om värd processen.</span><span class="sxs-lookup"><span data-stu-id="4a15c-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="4a15c-210">Detta kan göras per instans, där du kan identifiera processen, stoppa den och starta om den.</span><span class="sxs-lookup"><span data-stu-id="4a15c-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="4a15c-211">Du kan också använda `DebugMode`, enligt nedan, för att läsa in PowerShell DSC-resursen igen.</span><span class="sxs-lookup"><span data-stu-id="4a15c-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="4a15c-212">För att identifiera vilken process som är värd för DSC-motorn och stoppa den per instans, kan du Visa process-ID: t för den WmiPrvSE som är värd för DSC-motorn.</span><span class="sxs-lookup"><span data-stu-id="4a15c-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="4a15c-213">Om du sedan vill uppdatera providern stoppar du WmiPrvSE-processen med hjälp av kommandona nedan och kör sedan **Start-DscConfiguration** igen.</span><span class="sxs-lookup"><span data-stu-id="4a15c-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="4a15c-214">Använda DebugMode</span><span class="sxs-lookup"><span data-stu-id="4a15c-214">Using DebugMode</span></span>

<span data-ttu-id="4a15c-215">Du kan konfigurera den lokala DSC-Configuration Manager (LCM) att använda `DebugMode` för att alltid rensa cacheminnet när värd processen startas om.</span><span class="sxs-lookup"><span data-stu-id="4a15c-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="4a15c-216">När värdet är **True**, gör det att motorn alltid laddar om PowerShell DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="4a15c-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="4a15c-217">När du har skrivit din resurs kan du ange den till **false** så att motorn återgår till att cachelagra modulerna.</span><span class="sxs-lookup"><span data-stu-id="4a15c-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="4a15c-218">Följande är en demonstration som visar hur `DebugMode` kan uppdatera cacheminnet automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4a15c-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="4a15c-219">Först ska vi titta på standard konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="4a15c-219">First, let's look at the default configuration:</span></span>

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

<span data-ttu-id="4a15c-220">Du kan se att `DebugMode` har angetts till **"ingen"** .</span><span class="sxs-lookup"><span data-stu-id="4a15c-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="4a15c-221">Om du vill konfigurera `DebugMode` demonstrationen använder du följande PowerShell-resurs:</span><span class="sxs-lookup"><span data-stu-id="4a15c-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="4a15c-222">Nu kan du skapa en konfiguration med hjälp av ovanstående resurs som heter `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="4a15c-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="4a15c-223">Du kommer att se att innehållet i filen: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` är **1**.</span><span class="sxs-lookup"><span data-stu-id="4a15c-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="4a15c-224">Uppdatera nu leverantörs koden med följande skript:</span><span class="sxs-lookup"><span data-stu-id="4a15c-224">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="4a15c-225">Det här skriptet genererar ett slumpmässigt nummer och uppdaterar leverantörs koden på motsvarande sätt.</span><span class="sxs-lookup"><span data-stu-id="4a15c-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="4a15c-226">Om `DebugMode` har angetts till false ändras inte innehållet i filen " **$env: SystemDrive\OutputFromTestProviderDebugMode.txt**".</span><span class="sxs-lookup"><span data-stu-id="4a15c-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="4a15c-227">Ange `DebugMode` till **"ForceModuleImport"** i konfigurations skriptet:</span><span class="sxs-lookup"><span data-stu-id="4a15c-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="4a15c-228">När du kör skriptet ovan igen kommer du att se att innehållet i filen är olika varje gång.</span><span class="sxs-lookup"><span data-stu-id="4a15c-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="4a15c-229">(Du kan köra `Get-DscConfiguration` för att kontrol lera den).</span><span class="sxs-lookup"><span data-stu-id="4a15c-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="4a15c-230">Nedan visas resultatet av två ytterligare körningar (dina resultat kan vara olika när du kör skriptet):</span><span class="sxs-lookup"><span data-stu-id="4a15c-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a><span data-ttu-id="4a15c-231">DSC returnerar "oväntad svarskod InternalServerError" vid registrering med Windows pull server</span><span class="sxs-lookup"><span data-stu-id="4a15c-231">DSC returns "unexpected response code InternalServerError" when registering with Windows Pull Server</span></span>

<span data-ttu-id="4a15c-232">När du använder en metaconfiguration på en server för att registrera den med en instans av Windows pull server kan du stöta på följande fel.</span><span class="sxs-lookup"><span data-stu-id="4a15c-232">When applying a metaconfiguration to a server to register it with an instance of Windows Pull Server, you might encounter the following error.</span></span>

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

<span data-ttu-id="4a15c-233">Detta kan inträffa när certifikatet som används på servern för att kryptera trafik har ett eget namn (CN) som skiljer sig från det DNS-namn som används av noden för att matcha URL: en.</span><span class="sxs-lookup"><span data-stu-id="4a15c-233">This can occur when the certificate used on the server to encrypt traffic has a common name (CN) that is different than the DNS name used by the node to resolve the URL.</span></span>
<span data-ttu-id="4a15c-234">Uppdatera Windows pull Server-instansen för att använda ett certifikat med ett korrigerat namn.</span><span class="sxs-lookup"><span data-stu-id="4a15c-234">Update the Windows Pull Server instance to use a certificate with a corrected name.</span></span>

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a><span data-ttu-id="4a15c-235">Fel vid körning av Sysprep efter användning av en DSC-konfiguration</span><span class="sxs-lookup"><span data-stu-id="4a15c-235">Error when running Sysprep after applying a DSC Configuration</span></span>

<span data-ttu-id="4a15c-236">När du försöker köra Sysprep för att generalisera en Windows Server efter att ha tillämpat en DSC-konfiguration kan du stöta på följande fel.</span><span class="sxs-lookup"><span data-stu-id="4a15c-236">When attempting to run Sysprep to generalize a Windows Server after applying a DSC configuration, you might encounter the following error.</span></span>

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

<span data-ttu-id="4a15c-237">Att generalisera en server när den har kon figurer ATS med hjälp av Windows PowerShell Desired State Configuration är inte ett scenario som stöds.</span><span class="sxs-lookup"><span data-stu-id="4a15c-237">Generalizing a server after it has been configured using Windows PowerShell Desired State Configuration is not a supported scenario.</span></span>  <span data-ttu-id="4a15c-238">Använd i stället konfigurationer för Windows när specialize-fasen i Installationsprogrammet för Windows har slutförts.</span><span class="sxs-lookup"><span data-stu-id="4a15c-238">Instead, apply configurations to Windows after the Specialize phase of Windows Setup has completed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a15c-239">Se även</span><span class="sxs-lookup"><span data-stu-id="4a15c-239">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="4a15c-240">Koncept</span><span class="sxs-lookup"><span data-stu-id="4a15c-240">Concepts</span></span>

- [<span data-ttu-id="4a15c-241">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a15c-241">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="4a15c-242">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="4a15c-242">Other Resources</span></span>

- [<span data-ttu-id="4a15c-243">Windows PowerShell Desired State Configuration-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4a15c-243">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)
