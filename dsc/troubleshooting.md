---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Felsöka DSC
ms.openlocfilehash: c08f91b514aae438578fa278228fe5ec879a4012
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190017"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="5ea6a-103">Felsöka DSC</span><span class="sxs-lookup"><span data-stu-id="5ea6a-103">Troubleshooting DSC</span></span>

><span data-ttu-id="5ea6a-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5ea6a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5ea6a-105">Det här avsnittet beskrivs hur du felsöker DSC när problem uppstår.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="5ea6a-106">WinRM-beroende</span><span class="sxs-lookup"><span data-stu-id="5ea6a-106">WinRM Dependency</span></span>

<span data-ttu-id="5ea6a-107">Windows PowerShell önskad tillstånd Configuration (DSC) är beroende av WinRM.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="5ea6a-108">WinRM är inte aktiverad som standard i Windows Server 2008 R2 och Windows 7.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="5ea6a-109">Kör ```Set-WSManQuickConfig```, utökade sessionen att aktivera WinRM i en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-109">Run ```Set-WSManQuickConfig```, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="5ea6a-110">Med hjälp av Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5ea6a-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="5ea6a-111">Den [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet hämtar information om status för konfiguration från målnoden.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span>
<span data-ttu-id="5ea6a-112">En omfattande objekt returneras som innehåller översiktlig information om huruvida kör konfigurationen lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="5ea6a-113">Du kan prova objektet för att identifiera information om Kör som-konfiguration:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-113">You can dig into the object to discover details about the configuration run such as:</span></span>

* <span data-ttu-id="5ea6a-114">Alla resurser som misslyckades</span><span class="sxs-lookup"><span data-stu-id="5ea6a-114">All of the resources that failed</span></span>
* <span data-ttu-id="5ea6a-115">Alla resurser som har begärt en omstart</span><span class="sxs-lookup"><span data-stu-id="5ea6a-115">Any resource that requested a reboot</span></span>
* <span data-ttu-id="5ea6a-116">Kör meta-konfigurationsinställningar vid tiden för konfiguration</span><span class="sxs-lookup"><span data-stu-id="5ea6a-116">Meta-Configuration settings at time of configuration run</span></span>
* <span data-ttu-id="5ea6a-117">osv.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-117">Etc.</span></span>

<span data-ttu-id="5ea6a-118">Följande parameteruppsättningen returnerar statusinformation för den senaste konfigurationen som kör:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-118">The following parameter set returns the status information for the last configuration run:</span></span>

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
<span data-ttu-id="5ea6a-119">Följande parameteruppsättningen returnerar statusinformation för alla tidigare configuration körs:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="5ea6a-120">Exempel</span><span class="sxs-lookup"><span data-stu-id="5ea6a-120">Example</span></span>

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="5ea6a-121">Min skriptet inte körs: använder DSC loggar för att diagnostisera skriptfel</span><span class="sxs-lookup"><span data-stu-id="5ea6a-121">My script won’t run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="5ea6a-122">Alla Windows-program, t.ex. DSC registrerar fel och händelser i [loggar](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) som kan visas från den [Loggboken](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span> <span data-ttu-id="5ea6a-123">Undersöka dessa loggar hjälper dig att förstå varför en viss åtgärd misslyckades, och förhindra fel i framtiden.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="5ea6a-124">Skriva konfigurationsskript kan vara svårt så för att underlätta spårning fel som du författare använder resursen DSC-loggen för att följa förloppet av konfigurationen i analytiska DSC-händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="5ea6a-125">Var finns DSC-händelseloggar?</span><span class="sxs-lookup"><span data-stu-id="5ea6a-125">Where are DSC event logs?</span></span>

<span data-ttu-id="5ea6a-126">I Loggboken DSC-händelser finns i: **program och tjänster loggar/Microsoft/Windows/önskade Tillståndskonfiguration**</span><span class="sxs-lookup"><span data-stu-id="5ea6a-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="5ea6a-127">Motsvarande PowerShell-cmdleten [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), kan också köra om du vill visa händelseloggar:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="5ea6a-128">Visas ovanför DSC-primära loggnamn är **Microsoft -> Windows -> DSC** (andra loggen namn under Windows visas inte här planeringsaspekter).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-128">As shown above, DSC’s primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="5ea6a-129">Det primära namnet läggs till Kanalnamn komplett logg namn.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="5ea6a-130">DSC-motorn skriver huvudsakligen till tre typer av loggar: [drift, analytiska, loggar och felsökningsloggar](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="5ea6a-131">Eftersom de analytiska loggar och felsökningsloggar är inaktiverade som standard, bör du aktivera dem i Loggboken.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="5ea6a-132">Gör detta genom att öppna Loggboken genom att skriva visa händelseloggen i Windows PowerShell; eller klicka på den **starta** , klicka på **Kontrollpanelen**, klickar du på **Administrationsverktyg**, och klicka sedan på **Loggboken**.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span> <span data-ttu-id="5ea6a-133">På den **visa** Klicka på menyn i Loggboken **visa analytiska loggar och felsökningsloggar**.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="5ea6a-134">Namnet på loggen för analytiska kanal är **Microsoft-Windows-Dsc/analytiska**, och debug-kanalen är **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="5ea6a-135">Du kan också använda den [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) verktyg för att aktivera loggarna, vilket visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="5ea6a-136">Vad innehåller DSC loggar?</span><span class="sxs-lookup"><span data-stu-id="5ea6a-136">What do DSC logs contain?</span></span>

<span data-ttu-id="5ea6a-137">DSC-loggar delas över de tre loggkanaler baserat på vikten av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="5ea6a-138">Arbetsloggen i DSC innehåller alla felmeddelanden och kan användas för att identifiera problem.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="5ea6a-139">Analytiska loggen har ett ökat antal händelser och kan identifiera där fel uppstod.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="5ea6a-140">Den här kanalen innehåller också utförliga meddelanden (eventuella).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="5ea6a-141">Debug-loggen innehåller loggarna som kan hjälpa dig att förstå hur felen inträffade.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="5ea6a-142">Händelsemeddelanden för DSC är strukturerade så att varje händelsemeddelande börjar med ett jobb-ID som unikt representerar en DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="5ea6a-143">Exemplet nedan försöker att hämta meddelandet från den första händelsen loggas i arbetsloggen i DSC.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="5ea6a-144">DSC-händelser loggas i en viss struktur som gör att användaren att aggregera händelser från ett DSC-jobb.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="5ea6a-145">Strukturen är följande:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-145">The structure is as follows:</span></span>

<span data-ttu-id="5ea6a-146">**Jobb-ID: <Guid>**
**<Event Message>**</span><span class="sxs-lookup"><span data-stu-id="5ea6a-146">**Job ID : <Guid>**
**<Event Message>**</span></span>

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="5ea6a-147">Samla in händelser från en enda DSC-åtgärd</span><span class="sxs-lookup"><span data-stu-id="5ea6a-147">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="5ea6a-148">DSC-händelseloggarna innehålla händelser som genererats av olika DSC-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-148">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="5ea6a-149">Du kommer dock vanligtvis att berörda med detaljer om en viss åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-149">However, you’ll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="5ea6a-150">Alla DSC-loggar kan grupperas efter egenskapen jobb-ID som är unik för varje DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-150">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="5ea6a-151">Jobb-ID visas som det första egenskapsvärdet i alla DSC-händelser.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-151">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="5ea6a-152">Följande steg förklarar hur du lagra alla händelser i en grupperad matris-struktur.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-152">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

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

<span data-ttu-id="5ea6a-153">Här, variabeln `$SeparateDscOperations` innehåller loggar grupperade efter jobb-ID: N.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-153">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="5ea6a-154">Varje element i matrisen för den här variabeln representerar en grupp av händelser som loggats av en annan DSC-åtgärd, att tillåta åtkomst till mer information om loggarna.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-154">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="5ea6a-155">Du kan extrahera data i variabeln `$SeparateDscOperations` med [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-155">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="5ea6a-156">Följande är fem scenarier som du kanske vill hämta data för att felsöka DSC:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-156">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="5ea6a-157">1: misslyckade</span><span class="sxs-lookup"><span data-stu-id="5ea6a-157">1: Operations failures</span></span>

<span data-ttu-id="5ea6a-158">Alla händelser har [allvarlighetsgrader](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-158">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="5ea6a-159">Den här informationen kan användas för att identifiera felhändelser:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-159">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="5ea6a-160">2: information om åtgärder som körs i senaste halvtimme</span><span class="sxs-lookup"><span data-stu-id="5ea6a-160">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="5ea6a-161">`TimeCreated`, en egenskap för varje Windows-händelse, anger den tid som händelsen skapades.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-161">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="5ea6a-162">Jämföra den här egenskapen med ett visst datum/tid-objekt kan användas för att filtrera alla händelser:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-162">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="5ea6a-163">3: meddelanden från den senaste åtgärden</span><span class="sxs-lookup"><span data-stu-id="5ea6a-163">3: Messages from the latest operation</span></span>

<span data-ttu-id="5ea6a-164">Den senaste åtgärden lagras i det första indexet i gruppen matris `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-164">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span> <span data-ttu-id="5ea6a-165">Frågar gruppens meddelanden för index 0 returnerar alla meddelanden för den senaste åtgärden:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-165">Querying the group’s messages for index 0 returns all messages for the latest operation:</span></span>

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="5ea6a-166">4: felmeddelanden som loggats för senaste misslyckade åtgärder</span><span class="sxs-lookup"><span data-stu-id="5ea6a-166">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="5ea6a-167">`$SeparateDscOperations[0].Group` innehåller en uppsättning händelser för den senaste åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-167">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="5ea6a-168">Kör den `Where-Object` cmdlet för att filtrera händelser utifrån deras nivå visningsnamn.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-168">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="5ea6a-169">Resultatet lagras i den `$myFailedEvent` variabel, vilket kan medföra ytterligare ut för att få meddelandet:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-169">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="5ea6a-170">5: alla händelser som genererats för ett specifikt jobb-ID.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-170">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="5ea6a-171">`$SeparateDscOperations` är en matris med grupper som har namn som unikt jobb-ID.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-171">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="5ea6a-172">Genom att köra den `Where-Object` cmdlet, som du kan extrahera de grupperna av händelser som har ett specifikt jobb-ID:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-172">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="5ea6a-173">Med hjälp av xDscDiagnostics att analysera DSC loggar</span><span class="sxs-lookup"><span data-stu-id="5ea6a-173">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="5ea6a-174">**xDscDiagnostics** är en PowerShell-modul som består av flera funktioner som kan hjälpa dig att analysera DSC-fel på din dator.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-174">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="5ea6a-175">Dessa funktioner kan hjälpa dig att identifiera alla lokala händelser från den senaste DSC operations eller DSC-händelser på fjärrdatorer (med giltiga autentiseringsuppgifter).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-175">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="5ea6a-176">Här används termen DSC-åtgärden för att definiera en enda unika DSC körning från dess start till dess slut.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-176">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="5ea6a-177">Till exempel `Test-DscConfiguration` skulle vara en separat DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-177">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="5ea6a-178">På liknande sätt kan alla andra cmdletar i DSC (t.ex `Get-DscConfiguration`, `Start-DscConfiguration`osv) kan varje identifieras som separata DSC-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-178">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="5ea6a-179">Funktionerna som beskrivs i [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-179">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span>
<span data-ttu-id="5ea6a-180">Hjälp är tillgänglig genom att köra `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-180">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="5ea6a-181">Hämta information om DSC-åtgärder</span><span class="sxs-lookup"><span data-stu-id="5ea6a-181">Getting details of DSC operations</span></span>

<span data-ttu-id="5ea6a-182">Den `Get-xDscOperation` funktionen kan du hitta resultaten av DSC-åtgärder som körs på en eller flera datorer och returnerar ett objekt som innehåller samlingen av händelser som genereras av varje DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-182">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span>
<span data-ttu-id="5ea6a-183">I följande utdata, till exempel körs tre kommandon.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-183">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="5ea6a-184">Den första som skickas och de andra två misslyckades.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-184">The first one passed, and the other two failed.</span></span> <span data-ttu-id="5ea6a-185">De här resultaten returneras sammanfattas i utdata för `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-185">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

<span data-ttu-id="5ea6a-186">Du kan också ange att du vill endast resultat för de senaste åtgärderna med hjälp av den `Newest` parameter:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-186">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

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

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="5ea6a-187">Hämta information om DSC-händelser</span><span class="sxs-lookup"><span data-stu-id="5ea6a-187">Getting details of DSC events</span></span>

<span data-ttu-id="5ea6a-188">Den `Trace-xDscOperation` cmdlet returnerar ett objekt som innehåller en uppsättning händelser, deras händelsetyper och meddelandet utdata genereras från en viss DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-188">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="5ea6a-189">Vanligtvis när du hittar ett fel i någon av de åtgärder som använder `Get-xDscOperation`, skulle du spåra åtgärden att ta reda på vilka av händelserna som orsakade ett fel.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-189">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="5ea6a-190">Använd den `SequenceID` parametern för att hämta händelser för en specifik åtgärd för en specifik dator.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-190">Use the  `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span> <span data-ttu-id="5ea6a-191">Till exempel om du anger en `SequenceID` 9, `Trace-xDscOperaion` hämta spårningen för DSC-åtgärden som var 9: e från den senaste åtgärden:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-191">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

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

<span data-ttu-id="5ea6a-192">Skicka den **GUID** tilldelas en specifik DSC-åtgärd (som returneras av den `Get-xDscOperation` cmldet) att hämta händelseinformation om för den DSC-åtgärden:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-192">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

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

<span data-ttu-id="5ea6a-193">Observera att eftersom `Trace-xDscOperation` aggregerar händelser från analys, felsökning och drift loggar, uppmanas du att aktivera dessa loggar som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-193">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="5ea6a-194">Alternativt kan du kan samla in information om händelser genom att spara resultatet av `Trace-xDscOperation` i en variabel.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-194">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="5ea6a-195">Du kan använda följande kommandon för att visa alla händelser för en viss DSC-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-195">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="5ea6a-196">Samma resultat som visas i `Get-WinEvent` cmdlet, exempelvis utdata nedan:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-196">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

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

<span data-ttu-id="5ea6a-197">Helst bör du först använder `Get-xDscOperation` för att lista ut senast några DSC-konfiguration körs på dina datorer.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-197">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="5ea6a-198">Detta kan du undersöka en enda åtgärd (med dess SequenceID eller JobID) med `Trace-xDscOperation` att identifiera det gjorde i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-198">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="5ea6a-199">Hämta händelser för en fjärransluten dator</span><span class="sxs-lookup"><span data-stu-id="5ea6a-199">Getting events for a remote computer</span></span>

<span data-ttu-id="5ea6a-200">Använd den `ComputerName` parameter för den `Trace-xDscOperation` för att hämta händelseinformationen på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-200">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="5ea6a-201">Du måste skapa en brandväggsregel för att tillåta fjärradministration på fjärrdatorn innan du kan göra detta:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-201">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
<span data-ttu-id="5ea6a-202">Nu kan du ange den datorn i anrop till `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-202">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="5ea6a-203">Mina resurser inte uppdatera: hur du återställer cachen</span><span class="sxs-lookup"><span data-stu-id="5ea6a-203">My resources won’t update: How to reset the cache</span></span>

<span data-ttu-id="5ea6a-204">DSC-motorn cachelagrar resurser som implementeras som en PowerShell-modul för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-204">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span> <span data-ttu-id="5ea6a-205">Detta kan emellertid orsaka problem när du redigerar en resurs och testar samtidigt eftersom DSC kommer att läsa in den cachelagrade versionen tills processen startas.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-205">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="5ea6a-206">Det enda sättet att läsa in den senare versionen DSC är att uttryckligen avsluta processen som är värd för DSC-motorn.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-206">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="5ea6a-207">På liknande sätt, när du kör `Start-DscConfiguration`, efter att lägga till och ändra en anpassad resurs ändringen kanske inte kan köras om eller tills, datorn startas.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-207">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="5ea6a-208">Detta beror på att DSC körs i värdprocessen för WMI-Provider (WmiPrvSE) och vanligtvis det finns många instanser av WmiPrvSE som körs på samma gång.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-208">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="5ea6a-209">När du startar om värdprocessen startas och cachen rensats.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-209">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="5ea6a-210">Om du vill att återvinna konfigurationen och rensa cachen utan att starta om, måste du stoppa och starta sedan om värdprocessen.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-210">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="5ea6a-211">Detta kan göras på grundval per instans där du identifiera processen, stoppa och starta om den.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-211">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="5ea6a-212">Du kan också använda `DebugMode`, som visas nedan, för att läsa in PowerShell DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-212">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="5ea6a-213">För att identifiera vilken process är värd för DSC-motorn och stoppa på grundval av per instans, kan du visa process-ID för WmiPrvSE som är värd för DSC-motorn.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-213">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="5ea6a-214">Stoppa sedan WmiPrvSE processen med nedanstående kommandon och kör sedan för att uppdatera providern **Start DscConfiguration** igen.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-214">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="5ea6a-215">Med hjälp av DebugMode</span><span class="sxs-lookup"><span data-stu-id="5ea6a-215">Using DebugMode</span></span>

<span data-ttu-id="5ea6a-216">Du kan konfigurera den DSC lokala Configuration Manager (MGM) att använda `DebugMode` att rensa cacheminnet alltid när värdprocessen startas.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-216">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="5ea6a-217">Om värdet är **SANT**, medför motorn alltid ladda PowerShell DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-217">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="5ea6a-218">När du är klar skrivs din resurs, kan du ändra det till **FALSKT** och motorn återgår till sitt beteende av cachelagring moduler.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-218">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="5ea6a-219">Följande är en demonstration att visa hur `DebugMode` kan automatiskt uppdatera cachen.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-219">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="5ea6a-220">Först ska vi titta på standardkonfigurationen:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-220">First, let’s look at the default configuration:</span></span>

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

<span data-ttu-id="5ea6a-221">Du kan se det `DebugMode` är inställd på **FALSKT**.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-221">You can see that `DebugMode` is set to **FALSE**.</span></span>

<span data-ttu-id="5ea6a-222">Att ställa in den `DebugMode` demonstration, Använd följande PowerShell-resurs:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-222">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="5ea6a-223">Nu kan skapa en konfiguration med hjälp av ovanstående resursen anropas `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-223">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="5ea6a-224">Du kan nu se att innehållet i filen ”:**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” är **1**.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-224">You will see that the contents of file: “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” is **1**.</span></span>

<span data-ttu-id="5ea6a-225">Uppdatera nu providern koden med följande skript:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-225">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="5ea6a-226">Det här skriptet genererar ett slumptal och uppdateras provider-koden.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-226">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="5ea6a-227">Med `DebugMode` inställt på false, innehållet i filen ”**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” aldrig ändras.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-227">With `DebugMode` set to false, the contents of the file “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” are never changed.</span></span>

<span data-ttu-id="5ea6a-228">Nu ska du ange `DebugMode` till **SANT** i skriptet konfiguration:</span><span class="sxs-lookup"><span data-stu-id="5ea6a-228">Now, set `DebugMode` to **TRUE** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

<span data-ttu-id="5ea6a-229">När du kör skriptet ovan, ser du att innehållet i filen är olika varje gång.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-229">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="5ea6a-230">(Du kan köra `Get-DscConfiguration` kontrollerar du detta).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-230">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="5ea6a-231">Nedan visas resultatet av två ytterligare körs (resultaten kan vara annorlunda när du kör skriptet):</span><span class="sxs-lookup"><span data-stu-id="5ea6a-231">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5ea6a-232">Se även</span><span class="sxs-lookup"><span data-stu-id="5ea6a-232">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="5ea6a-233">Referens</span><span class="sxs-lookup"><span data-stu-id="5ea6a-233">Reference</span></span>
* [<span data-ttu-id="5ea6a-234">DSC-loggen resurs</span><span class="sxs-lookup"><span data-stu-id="5ea6a-234">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="5ea6a-235">Begrepp</span><span class="sxs-lookup"><span data-stu-id="5ea6a-235">Concepts</span></span>
* [<span data-ttu-id="5ea6a-236">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="5ea6a-236">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="5ea6a-237">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="5ea6a-237">Other Resources</span></span>
* <span data-ttu-id="5ea6a-238">[Windows PowerShell Desired State Configuration-Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="5ea6a-238">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>