---
description: Windows PowerShell skapar en Windows-händelseloggen med namnet "Windows PowerShell" för att registrera Windows PowerShell-händelser. Du kan visa den här loggen i Loggboken eller genom att använda cmdlets som hämtar händelser, t `Get-EventLog` . ex. cmdleten. Som standard registreras Windows PowerShell-motor och-Provider-händelser i händelse loggen, men du kan använda variablerna för händelse loggen för att anpassa händelse loggen. Du kan till exempel lägga till händelser om Windows PowerShell-kommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272156"
---
# <a name="about-eventlogs"></a><span data-ttu-id="c05a5-107">Om EventLogs</span><span class="sxs-lookup"><span data-stu-id="c05a5-107">About Eventlogs</span></span>

## <a name="short-description"></a><span data-ttu-id="c05a5-108">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="c05a5-108">Short Description</span></span>

<span data-ttu-id="c05a5-109">Windows PowerShell skapar en Windows-händelseloggen med namnet "Windows PowerShell" för att registrera Windows PowerShell-händelser.</span><span class="sxs-lookup"><span data-stu-id="c05a5-109">Windows PowerShell creates a Windows event log that is named "Windows PowerShell" to record Windows PowerShell events.</span></span> <span data-ttu-id="c05a5-110">Du kan visa den här loggen i Loggboken eller genom att använda cmdlets som hämtar händelser, t `Get-EventLog` . ex. cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c05a5-110">You can view this log in Event Viewer or by using cmdlets that get events, such as the `Get-EventLog` cmdlet.</span></span> <span data-ttu-id="c05a5-111">Som standard registreras Windows PowerShell-motor och-Provider-händelser i händelse loggen, men du kan använda variablerna för händelse loggen för att anpassa händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="c05a5-111">By default, Windows PowerShell engine and provider events are recorded in the event log, but you can use the event log preference variables to customize the event log.</span></span> <span data-ttu-id="c05a5-112">Du kan till exempel lägga till händelser om Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="c05a5-112">For example, you can add events about Windows PowerShell commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="c05a5-113">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="c05a5-113">Long Description</span></span>

<span data-ttu-id="c05a5-114">Händelse loggen i Windows PowerShell registrerar information om Windows PowerShell-åtgärder, till exempel starta och stoppa program motorn och starta och stoppa Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="c05a5-114">The Windows PowerShell event log records details of Windows PowerShell operations, such as starting and stopping the program engine and starting and stopping the Windows PowerShell providers.</span></span> <span data-ttu-id="c05a5-115">Du kan också logga information om Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="c05a5-115">You can also log details about Windows PowerShell commands.</span></span>

<span data-ttu-id="c05a5-116">Händelse loggen för Windows PowerShell finns i gruppen program-och tjänst loggar.</span><span class="sxs-lookup"><span data-stu-id="c05a5-116">The Windows PowerShell event log is in the Application and Services Logs group.</span></span> <span data-ttu-id="c05a5-117">Windows PowerShell-loggen är en klassisk händelse logg som inte använder Windows Eventing-teknik.</span><span class="sxs-lookup"><span data-stu-id="c05a5-117">The Windows PowerShell log is a classic event log that does not use the Windows Eventing technology.</span></span> <span data-ttu-id="c05a5-118">Om du vill visa loggen använder du cmdletarna som har utformats för klassiska händelse loggar, till exempel `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="c05a5-118">To view the log, use the cmdlets designed for classic event logs, such as `Get-EventLog`.</span></span>

## <a name="viewing-the-windows-powershell-event-log"></a><span data-ttu-id="c05a5-119">Visa händelse loggen för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c05a5-119">Viewing the Windows PowerShell Event Log</span></span>

<span data-ttu-id="c05a5-120">Du kan visa händelse loggen för Windows PowerShell i Loggboken eller genom att `Get-EventLog` använda `Get-WmiObject` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="c05a5-120">You can view the Windows PowerShell event log in Event Viewer or by using the `Get-EventLog` and `Get-WmiObject` cmdlets.</span></span> <span data-ttu-id="c05a5-121">Om du vill visa innehållet i Windows PowerShell-loggen skriver du:</span><span class="sxs-lookup"><span data-stu-id="c05a5-121">To view the contents of the Windows PowerShell log, type:</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

<span data-ttu-id="c05a5-122">Om du vill undersöka händelserna och deras egenskaper använder du `Sort-Object` cmdleten, `Group-Object` cmdleten och cmdletarna som innehåller `Format` verbet ( `Format` cmdletarna).</span><span class="sxs-lookup"><span data-stu-id="c05a5-122">To examine the events and their properties, use the `Sort-Object` cmdlet, the `Group-Object` cmdlet, and the cmdlets that contain the `Format` verb (the `Format` cmdlets).</span></span>

<span data-ttu-id="c05a5-123">Om du till exempel vill visa händelserna i loggen grupperade efter händelse-ID, skriver du:</span><span class="sxs-lookup"><span data-stu-id="c05a5-123">For example, to view the events in the log grouped by the event ID, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

<span data-ttu-id="c05a5-124">Eller skriv:</span><span class="sxs-lookup"><span data-stu-id="c05a5-124">Or, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

<span data-ttu-id="c05a5-125">Om du vill visa alla klassiska händelse loggar skriver du:</span><span class="sxs-lookup"><span data-stu-id="c05a5-125">To view all the classic event logs, type:</span></span>

```powershell
Get-EventLog -List
```

<span data-ttu-id="c05a5-126">Du kan också använda `Get-WmiObject` cmdleten för att använda Event-relaterade Windows Management Instrumentation (WMI)-klasser för att undersöka händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="c05a5-126">You can also use the `Get-WmiObject` cmdlet to use the event-related Windows Management Instrumentation (WMI) classes to examine the event log.</span></span> <span data-ttu-id="c05a5-127">Om du till exempel vill visa alla egenskaper för händelse logg filen skriver du:</span><span class="sxs-lookup"><span data-stu-id="c05a5-127">For example, to view all the properties of the event log file, type:</span></span>

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

<span data-ttu-id="c05a5-128">Du hittar Win32 Event-relaterade WMI-klasser genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="c05a5-128">To find the Win32 event-related WMI classes, type:</span></span>

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

<span data-ttu-id="c05a5-129">Om du vill ha mer information skriver du "Get-Help get-EventLog" och "Get-Help get-WmiObject".</span><span class="sxs-lookup"><span data-stu-id="c05a5-129">For more information, type "Get-Help Get-EventLog" and "Get-Help Get-WmiObject".</span></span>

## <a name="selecting-events-for-the-windows-powershell-event-log"></a><span data-ttu-id="c05a5-130">Välja händelser för händelse loggen i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c05a5-130">Selecting Events for the Windows PowerShell Event Log</span></span>

<span data-ttu-id="c05a5-131">Du kan använda variablerna för inställning av händelse logg för att avgöra vilka händelser som registreras i händelse loggen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c05a5-131">You can use the event log preference variables to determine which events are recorded in the Windows PowerShell event log.</span></span>

<span data-ttu-id="c05a5-132">Det finns sex variabler för händelse logg inställningar. två variabler för var och en av de tre loggnings komponenterna: motorn (Windows PowerShell-program), providers och kommandona.</span><span class="sxs-lookup"><span data-stu-id="c05a5-132">There are six event log preference variables; two variables for each of the three logging components: the engine (the Windows PowerShell program), the providers, and the commands.</span></span> <span data-ttu-id="c05a5-133">LifeCycleEvent-variablerna loggar normal start och stopp av händelser.</span><span class="sxs-lookup"><span data-stu-id="c05a5-133">The LifeCycleEvent variables log normal starting and stopping events.</span></span> <span data-ttu-id="c05a5-134">Fel händelser för loggen för hälso tillstånd.</span><span class="sxs-lookup"><span data-stu-id="c05a5-134">The Health variables log error events.</span></span>

<span data-ttu-id="c05a5-135">I följande tabell visas variablerna för händelse logg inställningar.</span><span class="sxs-lookup"><span data-stu-id="c05a5-135">The following table lists the event log preference variables.</span></span>

|<span data-ttu-id="c05a5-136">Variabel</span><span class="sxs-lookup"><span data-stu-id="c05a5-136">Variable</span></span>                  |<span data-ttu-id="c05a5-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c05a5-137">Description</span></span>                                    |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="c05a5-138">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-138">$LogEngineLifeCycleEvent</span></span>  |<span data-ttu-id="c05a5-139">Loggar start och stopp av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c05a5-139">Logs the start and stop of PowerShell</span></span>          |
|<span data-ttu-id="c05a5-140">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-140">$LogEngineHealthEvent</span></span>     |<span data-ttu-id="c05a5-141">Loggar PowerShell-program fel</span><span class="sxs-lookup"><span data-stu-id="c05a5-141">Logs PowerShell program errors</span></span>                 |
|<span data-ttu-id="c05a5-142">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-142">$LogProviderLifeCycleEvent</span></span>|<span data-ttu-id="c05a5-143">Loggar start och stopp för PowerShell-leverantörer</span><span class="sxs-lookup"><span data-stu-id="c05a5-143">Logs the start and stop of PowerShell providers</span></span>|
|<span data-ttu-id="c05a5-144">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-144">$LogProviderHealthEvent</span></span>   |<span data-ttu-id="c05a5-145">Loggar PowerShell-providerfelmeddelandet</span><span class="sxs-lookup"><span data-stu-id="c05a5-145">Logs PowerShell provider errors</span></span>                |
|<span data-ttu-id="c05a5-146">$LogCommandLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-146">$LogCommandLifeCycleEvent</span></span> |<span data-ttu-id="c05a5-147">Loggar start och slut för ande av kommandon</span><span class="sxs-lookup"><span data-stu-id="c05a5-147">Logs the starting and completion of commands</span></span>   |
|<span data-ttu-id="c05a5-148">$LogCommandHealthEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-148">$LogCommandHealthEvent</span></span>    |<span data-ttu-id="c05a5-149">Loggar kommando fel</span><span class="sxs-lookup"><span data-stu-id="c05a5-149">Logs command errors</span></span>                            |

<span data-ttu-id="c05a5-150">(Information om Windows PowerShell-providers finns i [about_Providers](about_Providers.md).)</span><span class="sxs-lookup"><span data-stu-id="c05a5-150">(For information about Windows PowerShell providers, see [about_Providers](about_Providers.md).)</span></span>

<span data-ttu-id="c05a5-151">Som standard är endast följande händelse typer aktiverade:</span><span class="sxs-lookup"><span data-stu-id="c05a5-151">By default, only the following event types are enabled:</span></span>

* <span data-ttu-id="c05a5-152">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-152">$LogEngineLifeCycleEvent</span></span>
* <span data-ttu-id="c05a5-153">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-153">$LogEngineHealthEvent</span></span>
* <span data-ttu-id="c05a5-154">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-154">$LogProviderLifeCycleEvent</span></span>
* <span data-ttu-id="c05a5-155">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="c05a5-155">$LogProviderHealthEvent</span></span>

<span data-ttu-id="c05a5-156">Om du vill aktivera en händelse typ anger du variabeln Preference för den händelse typen till $true.</span><span class="sxs-lookup"><span data-stu-id="c05a5-156">To enable an event type, set the preference variable for that event type to $true.</span></span> <span data-ttu-id="c05a5-157">Om du till exempel vill aktivera kommando livs cykel händelser skriver du:</span><span class="sxs-lookup"><span data-stu-id="c05a5-157">For example, to enable command life-cycle events, type:</span></span>

```powershell
$LogCommandLifeCycleEvent
```

<span data-ttu-id="c05a5-158">Eller skriv:</span><span class="sxs-lookup"><span data-stu-id="c05a5-158">Or, type:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="c05a5-159">Om du vill inaktivera en händelse typ anger du variabeln Preference för den händelse typen till $false.</span><span class="sxs-lookup"><span data-stu-id="c05a5-159">To disable an event type, set the preference variable for that event type to $false.</span></span> <span data-ttu-id="c05a5-160">Om du till exempel vill inaktivera kommando livs cykel händelser skriver du:</span><span class="sxs-lookup"><span data-stu-id="c05a5-160">For example, to disable command life-cycle events, type:</span></span>

```powershell
$LogProviderLifeCycleEvent = $false
```

<span data-ttu-id="c05a5-161">Du kan inaktivera vilken händelse som helst, förutom de händelser som indikerar att Windows PowerShell-motorn och Core-providern har startats.</span><span class="sxs-lookup"><span data-stu-id="c05a5-161">You can disable any event, except for the events that indicate that the Windows PowerShell engine and the core providers are started.</span></span> <span data-ttu-id="c05a5-162">Dessa händelser genereras innan Windows PowerShell-profilerna körs och innan värd programmet kan ta emot kommandon.</span><span class="sxs-lookup"><span data-stu-id="c05a5-162">These events are generated before the Windows PowerShell profiles are run and before the host program is ready to accept commands.</span></span>

<span data-ttu-id="c05a5-163">Variabel inställningarna gäller endast för den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c05a5-163">The variable settings apply only for the current Windows PowerShell session.</span></span>
<span data-ttu-id="c05a5-164">Om du vill tillämpa dem på alla Windows PowerShell-sessioner lägger du till dem i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="c05a5-164">To apply them to all Windows PowerShell sessions, add them to your Windows PowerShell profile.</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="c05a5-165">Loggning av module-händelser</span><span class="sxs-lookup"><span data-stu-id="c05a5-165">Logging Module Events</span></span>

<span data-ttu-id="c05a5-166">Från och med Windows PowerShell 3,0 kan du registrera körnings händelser för cmdlets och Functions i Windows PowerShell-moduler och snapin-moduler genom att ange egenskapen LogPipelineExecutionDetails för moduler och snapin-moduler till sant.</span><span class="sxs-lookup"><span data-stu-id="c05a5-166">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets and functions in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="c05a5-167">Den här funktionen är endast tillgänglig för snapin-moduler i Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="c05a5-167">In Windows PowerShell 2.0, this feature is available only for snap-ins.</span></span>

<span data-ttu-id="c05a5-168">När värdet för egenskapen LogPipelineExecutionDetails är TRUE ( `$true` ), skriver Windows PowerShell cmdlet-och Function-körningarna i sessionen till Windows PowerShell-loggen i Loggboken.</span><span class="sxs-lookup"><span data-stu-id="c05a5-168">When the LogPipelineExecutionDetails property value is TRUE (`$true`), Windows PowerShell writes cmdlet and function execution events in the session to the Windows PowerShell log in Event Viewer.</span></span> <span data-ttu-id="c05a5-169">Inställningen är endast effektiv i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c05a5-169">The setting is effective only in the current session.</span></span>

<span data-ttu-id="c05a5-170">Om du vill aktivera loggning av körnings händelser av cmdletar och funktioner i en modul använder du följande kommandosekvens.</span><span class="sxs-lookup"><span data-stu-id="c05a5-170">To enable logging of execution events of cmdlets and functions in a module, use the following command sequence.</span></span>

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

<span data-ttu-id="c05a5-171">Om du vill aktivera loggning av körnings händelser av cmdletar i en snapin-modul använder du följande kommandosekvens.</span><span class="sxs-lookup"><span data-stu-id="c05a5-171">To enable logging of execution events of cmdlets in a snap-in, use the following command sequence.</span></span>

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

<span data-ttu-id="c05a5-172">Om du vill inaktivera loggning använder du samma kommando sekvens för att ange värdet FALSKT () för egenskap svärdet `$false` .</span><span class="sxs-lookup"><span data-stu-id="c05a5-172">To disable logging, use the same command sequence to set the property value to FALSE (`$false`).</span></span>

<span data-ttu-id="c05a5-173">Du kan också använda grupprincip inställningen "Aktivera loggning av modul" för att aktivera och inaktivera modul-och snapin-loggning.</span><span class="sxs-lookup"><span data-stu-id="c05a5-173">You can also use the "Turn on Module Logging" Group Policy setting to enable and disable module and snap-in logging.</span></span> <span data-ttu-id="c05a5-174">Princip svärdet innehåller en lista över modul-och snapin-namn.</span><span class="sxs-lookup"><span data-stu-id="c05a5-174">The policy value includes a list of module and snap-in names.</span></span> <span data-ttu-id="c05a5-175">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="c05a5-175">Wildcards are supported.</span></span>

<span data-ttu-id="c05a5-176">När "Aktivera loggning av modul" har angetts för en modul är värdet för LogPipelineExecutionDetails-egenskapen i modulen sann i alla sessioner och kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="c05a5-176">When "Turn on Module Logging" is set for a module, the value of the LogPipelineExecutionDetails property of the module is TRUE in all sessions and it cannot be changed.</span></span>

<span data-ttu-id="c05a5-177">Grup princip inställningen Aktivera modul loggning finns i följande grupprincip sökvägar:</span><span class="sxs-lookup"><span data-stu-id="c05a5-177">The Turn On Module Logging group policy setting is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="c05a5-178">Användar konfigurations principen har företräde framför princip för dator konfiguration och båda principerna har företräde framför värdet för egenskapen LogPipelineExecutionDetails för moduler och snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="c05a5-178">The User Configuration policy takes precedence over the Computer Configuration policy, and both policies take preference over the value of the LogPipelineExecutionDetails property of modules and snap-ins.</span></span>

<span data-ttu-id="c05a5-179">Mer information om den här grupprincip inställningen finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="c05a5-179">For more information about this Group Policy setting, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="security-and-auditing"></a><span data-ttu-id="c05a5-180">Säkerhet och granskning</span><span class="sxs-lookup"><span data-stu-id="c05a5-180">Security and Auditing</span></span>

<span data-ttu-id="c05a5-181">Händelse loggen i Windows PowerShell är utformad för att indikera aktivitet och för att ge drifts information för fel sökning.</span><span class="sxs-lookup"><span data-stu-id="c05a5-181">The Windows PowerShell event log is designed to indicate activity and to provide operational details for troubleshooting.</span></span>

<span data-ttu-id="c05a5-182">Men precis som de flesta Windows-baserade program händelse loggar är Windows PowerShell-händelseloggen inte utformad för att vara säker.</span><span class="sxs-lookup"><span data-stu-id="c05a5-182">However, like most Windows-based application event logs, the Windows PowerShell event log is not designed to be secure.</span></span> <span data-ttu-id="c05a5-183">Den bör inte användas för att granska säkerheten eller registrera konfidentiell eller patentskyddad information.</span><span class="sxs-lookup"><span data-stu-id="c05a5-183">It should not be used to audit security or to record confidential or proprietary information.</span></span>

<span data-ttu-id="c05a5-184">Händelse loggar är utformade för att läsas och förstås av användare.</span><span class="sxs-lookup"><span data-stu-id="c05a5-184">Event logs are designed to be read and understood by users.</span></span> <span data-ttu-id="c05a5-185">Användare kan läsa från och skriva till loggen.</span><span class="sxs-lookup"><span data-stu-id="c05a5-185">Users can read from and write to the log.</span></span> <span data-ttu-id="c05a5-186">En obehörig användare kan läsa en händelse logg på en lokal dator eller fjärrdator, registrera falska data och sedan förhindra att deras aktiviteter loggas.</span><span class="sxs-lookup"><span data-stu-id="c05a5-186">A malicious user could read an event log on a local or remote computer, record false data, and then prevent the logging of their activities.</span></span>

## <a name="notes"></a><span data-ttu-id="c05a5-187">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c05a5-187">Notes</span></span>

<span data-ttu-id="c05a5-188">Författare av modulens författare kan lägga till loggnings funktioner i sina moduler.</span><span class="sxs-lookup"><span data-stu-id="c05a5-188">Authors of module authors can add logging features to their modules.</span></span> <span data-ttu-id="c05a5-189">Mer information finns i [skriva en Windows PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="c05a5-189">For more information, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="see-also"></a><span data-ttu-id="c05a5-190">Se även</span><span class="sxs-lookup"><span data-stu-id="c05a5-190">See Also</span></span>

[<span data-ttu-id="c05a5-191">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="c05a5-191">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="c05a5-192">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="c05a5-192">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="c05a5-193">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="c05a5-193">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="c05a5-194">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c05a5-194">about_Preference_Variables</span></span>](about_Preference_Variables.md)
