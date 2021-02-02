---
description: PowerShell loggar interna åtgärder från motorn, providers och cmdlets.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: e74e357d81eddf87ad27d023eb9a8ba2977156e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708483"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="ffd8c-103">Om loggning av icke-Windows</span><span class="sxs-lookup"><span data-stu-id="ffd8c-103">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="ffd8c-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-104">Short description</span></span>
<span data-ttu-id="ffd8c-105">PowerShell loggar interna åtgärder från motorn, providers och cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-105">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="ffd8c-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-106">Long description</span></span>

<span data-ttu-id="ffd8c-107">PowerShell loggar information om PowerShell-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-107">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="ffd8c-108">PowerShell loggar till exempel åtgärder som att starta och stoppa motorn, starta och stoppa providrar.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-108">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="ffd8c-109">Den kommer också att logga information om PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-109">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="ffd8c-110">Platsen för PowerShell-loggar är beroende av mål plattformen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-110">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="ffd8c-111">I **Linux** kan PowerShell-loggar till **syslog** och **rsyslog. conf** användas.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-111">On **Linux**, PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="ffd8c-112">Mer information finns på Linux-datorns lokala `man` sidor.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-112">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="ffd8c-113">I **MacOS** används **os_log** loggnings systemet.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-113">On **macOS**, the **os_log** logging system is used.</span></span> <span data-ttu-id="ffd8c-114">Mer information finns i [os_log Developer-dokumentation](https://developer.apple.com/documentation/os/os_log).</span><span class="sxs-lookup"><span data-stu-id="ffd8c-114">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="ffd8c-115">Visa PowerShell-loggens utdata på Linux</span><span class="sxs-lookup"><span data-stu-id="ffd8c-115">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="ffd8c-116">PowerShell-loggar till **syslog** i Linux och de verktyg som ofta används för att visa **syslog** -innehåll kan användas.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-116">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="ffd8c-117">Formatet för logg posterna använder följande mall:</span><span class="sxs-lookup"><span data-stu-id="ffd8c-117">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="ffd8c-118">Fält</span><span class="sxs-lookup"><span data-stu-id="ffd8c-118">Field</span></span>        |<span data-ttu-id="ffd8c-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-119">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="ffd8c-120">Ett datum/tid när logg posten genererades.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-120">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="ffd8c-121">Namnet på systemet där loggen skapades.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-121">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="ffd8c-122">Process-ID för processen som skrev logg posten.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-122">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="ffd8c-123">Det `git commit` ID eller den tagg som används för att skapa bygget.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-123">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="ffd8c-124">Tråd-ID för tråden som skrev logg posten.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-124">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="ffd8c-125">Den hexadecimala kanal identifieraren för logg posten.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-125">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="ffd8c-126">10 = drift, 11 = analys</span><span class="sxs-lookup"><span data-stu-id="ffd8c-126">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="ffd8c-127">Händelse identifieraren för logg posten.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-127">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="ffd8c-128">Aktivitets identifieraren för händelse posten</span><span class="sxs-lookup"><span data-stu-id="ffd8c-128">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="ffd8c-129">Opcode för händelse posten</span><span class="sxs-lookup"><span data-stu-id="ffd8c-129">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="ffd8c-130">Logg nivån för händelse posten</span><span class="sxs-lookup"><span data-stu-id="ffd8c-130">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="ffd8c-131">Det meddelande som är associerat med händelse posten</span><span class="sxs-lookup"><span data-stu-id="ffd8c-131">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="ffd8c-132">`EVENTID`, `TASK` , `OPCODE` , och `LEVEL` är samma värden som när du loggar in på Windows-händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-132">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="ffd8c-133">Filtrera PowerShell-logg poster med rsyslog</span><span class="sxs-lookup"><span data-stu-id="ffd8c-133">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="ffd8c-134">Normalt skrivs PowerShell-logg poster till standardvärdet `location/file` för **syslog**.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-134">Normally, PowerShell log entries are written to the default `location/file` for **syslog**.</span></span> <span data-ttu-id="ffd8c-135">Det går dock att omdirigera posterna till en anpassad fil.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-135">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="ffd8c-136">Skapa en conf för PowerShell-logg konfiguration och ange ett tal som är mindre än 50 (för `50-default.conf` ), till exempel `40-powershell.conf` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-136">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="ffd8c-137">Filen ska placeras under `/etc/rsyslog.d` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-137">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="ffd8c-138">Lägg till följande post i filen:</span><span class="sxs-lookup"><span data-stu-id="ffd8c-138">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="ffd8c-139">Se till att `/etc/rsyslog.conf` innehåller den nya filen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-139">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="ffd8c-140">Ofta har den ett generiskt include-uttryck som ser ut som följande konfiguration:</span><span class="sxs-lookup"><span data-stu-id="ffd8c-140">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="ffd8c-141">Om den inte gör det måste du lägga till en include-instruktion manuellt.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-141">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="ffd8c-142">Kontrol lera att attribut och behörigheter är korrekt inställda.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-142">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="ffd8c-143">Ange ägare till **rot**.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-143">Set ownership to **root**.</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="ffd8c-144">Ange åtkomst behörigheter: **roten** har Läs-och Skriv behörighet, **användare** har läst.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-144">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="ffd8c-145">Visa PowerShell-loggens utdata på macOS</span><span class="sxs-lookup"><span data-stu-id="ffd8c-145">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="ffd8c-146">Den enklaste metoden för att Visa PowerShell-loggens utdata på macOS är att använda **konsol** programmet.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-146">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="ffd8c-147">Sök efter **konsol** programmet och starta det.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-147">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="ffd8c-148">Välj dator namnet under **enheter**.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-148">Select the Machine name under **Devices**.</span></span>
1. <span data-ttu-id="ffd8c-149">I **Sök** fältet anger `pwsh` du för den huvudsakliga binärfilen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-149">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="ffd8c-150">Ändra Sök filtret från `Any` till `Process` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-150">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="ffd8c-151">Utför åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-151">Perform the operations.</span></span>
1. <span data-ttu-id="ffd8c-152">Du kan också spara sökningen för framtida användning.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-152">Optionally, save the search for future use.</span></span>

<span data-ttu-id="ffd8c-153">För att filtrera på en speciell process instans av PowerShell i- **konsolen** innehåller variabeln `$pid` process-ID.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-153">To filter on a specific process instance of PowerShell in the **Console**, the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="ffd8c-154">Ange **PID** (process-ID) i **Sök** fältet.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-154">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="ffd8c-155">Ändra Sök filtret till `PID` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-155">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="ffd8c-156">Utför åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-156">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="ffd8c-157">Visa PowerShell-loggens utdata från en kommando rad</span><span class="sxs-lookup"><span data-stu-id="ffd8c-157">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="ffd8c-158">`log`Kommandot kan användas för att Visa PowerShell-logg poster från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-158">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="ffd8c-159">Bevara PowerShell-loggens utdata</span><span class="sxs-lookup"><span data-stu-id="ffd8c-159">Persisting PowerShell log output</span></span>

<span data-ttu-id="ffd8c-160">Som standard använder PowerShell standard-endast minnes loggning på macOS.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-160">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="ffd8c-161">Du kan ändra det här beteendet om du vill aktivera persistence med `log config` kommandot.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-161">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="ffd8c-162">Följande skript aktiverar loggning och persistence på informations nivå:</span><span class="sxs-lookup"><span data-stu-id="ffd8c-162">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="ffd8c-163">Följande kommando återställer PowerShell-loggningen till standard läget:</span><span class="sxs-lookup"><span data-stu-id="ffd8c-163">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="ffd8c-164">När persistence har Aktiver ATS `log show` kan du använda kommandot för att exportera logg objekt.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-164">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="ffd8c-165">Kommandot innehåller alternativ för att exportera de senaste N objekten, artiklar sedan en bestämd tid eller objekt inom ett angivet tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-165">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="ffd8c-166">Följande kommando exporterar till exempel objekt sedan `9am on April 5 of 2018` :</span><span class="sxs-lookup"><span data-stu-id="ffd8c-166">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="ffd8c-167">Du kan få hjälp `log` genom att köra `log show --help` Ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-167">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="ffd8c-168">När du kör något av logg kommandona från en PowerShell-prompt eller ett skript, använder du dubbla citat tecken runt hela predikatet och enkla citat tecken i.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-168">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="ffd8c-169">På så sätt undviker du att undvika dubbla citat tecken i predikatet.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-169">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="ffd8c-170">Du kanske också vill överväga att spara händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-170">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="ffd8c-171">Du kan konfigurera SIEM i Azure.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-171">You can set up SIEM in Azure.</span></span> <span data-ttu-id="ffd8c-172">Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="ffd8c-172">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="ffd8c-173">Konfigurera loggning på ett system som inte är från Windows</span><span class="sxs-lookup"><span data-stu-id="ffd8c-173">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="ffd8c-174">I Windows konfigureras loggning genom att skapa ETW spårnings lyssnare eller genom att använda Loggboken för att aktivera analytisk loggning.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-174">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="ffd8c-175">På Linux och macOS konfigureras loggning med hjälp av filen `powershell.config.json` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-175">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="ffd8c-176">Resten av det här avsnittet beskriver hur du konfigurerar PowerShell-loggning på ett system som inte är från Windows.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-176">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="ffd8c-177">Som standard aktiverar PowerShell informations loggning till den operativa kanalen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-177">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="ffd8c-178">Det här innebär att alla logg utdata som genereras av PowerShell och som har marker ATS som operativa och som har en logg (spårning) som är större än information kommer att loggas.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-178">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="ffd8c-179">Ibland kan diagnoser kräva ytterligare logg data, t. ex. utförlig logg utdata eller för att aktivera analys loggs utdata.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-179">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="ffd8c-180">Filen `powershell.config.json` är en **JSON** -formaterad fil som finns i PowerShell- `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-180">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="ffd8c-181">Varje installation av PowerShell använder en egen kopia av den här filen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-181">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="ffd8c-182">För normal drift ändras den här filen oförändrad.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-182">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="ffd8c-183">Även om det kan vara användbart, ändra några av inställningarna i filen för diagnostik eller för att skilja mellan flera PowerShell-versioner på samma system eller till och med flera kopior av samma version (se `LogIdentity` tabellen nedan).</span><span class="sxs-lookup"><span data-stu-id="ffd8c-183">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="ffd8c-184">Följande kod är ett exempel på en konfiguration:</span><span class="sxs-lookup"><span data-stu-id="ffd8c-184">The following code is an example configuration:</span></span>

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

<span data-ttu-id="ffd8c-185">Egenskaperna för att konfigurera PowerShell-loggning visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-185">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="ffd8c-186">Värden som är markerade med en asterisk, till exempel `Operational*` , anger standardvärdet när inget värde anges i filen.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-186">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="ffd8c-187">Egenskap</span><span class="sxs-lookup"><span data-stu-id="ffd8c-187">Property</span></span>   |<span data-ttu-id="ffd8c-188">Värden</span><span class="sxs-lookup"><span data-stu-id="ffd8c-188">Values</span></span>        |<span data-ttu-id="ffd8c-189">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-189">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="ffd8c-190">(sträng namn)</span><span class="sxs-lookup"><span data-stu-id="ffd8c-190">(string name)</span></span> |<span data-ttu-id="ffd8c-191">Namnet som ska användas vid loggning.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-191">The name to use when logging.</span></span> <span data-ttu-id="ffd8c-192">Som standard tilldelar</span><span class="sxs-lookup"><span data-stu-id="ffd8c-192">By default,</span></span>  |
|           |<span data-ttu-id="ffd8c-193">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffd8c-193">powershell\*</span></span>   |<span data-ttu-id="ffd8c-194">PowerShell är identiteten.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-194">powershell is the identity.</span></span> <span data-ttu-id="ffd8c-195">Det här värdet kan vara</span><span class="sxs-lookup"><span data-stu-id="ffd8c-195">This value can be</span></span>|
|           |              |<span data-ttu-id="ffd8c-196">används för att berätta skillnaden mellan två</span><span class="sxs-lookup"><span data-stu-id="ffd8c-196">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="ffd8c-197">instanser av en PowerShell-installation, t. ex.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-197">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="ffd8c-198">som version och beta version.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-198">as a release and beta version.</span></span> <span data-ttu-id="ffd8c-199">Det här värdet är</span><span class="sxs-lookup"><span data-stu-id="ffd8c-199">This value is</span></span> |
|           |              |<span data-ttu-id="ffd8c-200">används också för att omdirigera logg utdata till en</span><span class="sxs-lookup"><span data-stu-id="ffd8c-200">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="ffd8c-201">separat fil på Linux.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-201">separate file on Linux.</span></span> <span data-ttu-id="ffd8c-202">Se diskussionen om</span><span class="sxs-lookup"><span data-stu-id="ffd8c-202">See the discussion of</span></span>|
|           |              |<span data-ttu-id="ffd8c-203">**rsyslog** ovan.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-203">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="ffd8c-204">Verksamhetsrelaterade</span><span class="sxs-lookup"><span data-stu-id="ffd8c-204">Operational\*</span></span>  |<span data-ttu-id="ffd8c-205">Kanaler som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-205">The channels to enable.</span></span> <span data-ttu-id="ffd8c-206">Avgränsa värdena</span><span class="sxs-lookup"><span data-stu-id="ffd8c-206">Separate the values</span></span>|
|           |<span data-ttu-id="ffd8c-207">Analys</span><span class="sxs-lookup"><span data-stu-id="ffd8c-207">Analytic</span></span>      |<span data-ttu-id="ffd8c-208">med ett kommatecken när du anger fler än ett.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-208">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="ffd8c-209">Always</span><span class="sxs-lookup"><span data-stu-id="ffd8c-209">Always</span></span>        |<span data-ttu-id="ffd8c-210">Ange ett enskilt värde.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-210">Specify a single value.</span></span> <span data-ttu-id="ffd8c-211">Värdet aktiverar</span><span class="sxs-lookup"><span data-stu-id="ffd8c-211">The value enables</span></span>  |
|           |<span data-ttu-id="ffd8c-212">Kritiskt</span><span class="sxs-lookup"><span data-stu-id="ffd8c-212">Critical</span></span>      |<span data-ttu-id="ffd8c-213">sig själv och alla värden ovanför den i</span><span class="sxs-lookup"><span data-stu-id="ffd8c-213">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="ffd8c-214">Fel</span><span class="sxs-lookup"><span data-stu-id="ffd8c-214">Error</span></span>         |<span data-ttu-id="ffd8c-215">i listan till vänster.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-215">list to the left.</span></span>                            |
|           |<span data-ttu-id="ffd8c-216">Varning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-216">Warning</span></span>       |                                             |
|           |<span data-ttu-id="ffd8c-217">Informations</span><span class="sxs-lookup"><span data-stu-id="ffd8c-217">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="ffd8c-218">Verbose</span><span class="sxs-lookup"><span data-stu-id="ffd8c-218">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="ffd8c-219">Felsökning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-219">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="ffd8c-220">Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="ffd8c-220">Runspace</span></span>      |<span data-ttu-id="ffd8c-221">Nyckelord ger möjlighet att begränsa loggning</span><span class="sxs-lookup"><span data-stu-id="ffd8c-221">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="ffd8c-222">Pipeline</span><span class="sxs-lookup"><span data-stu-id="ffd8c-222">Pipeline</span></span>      |<span data-ttu-id="ffd8c-223">till vissa komponenter i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-223">to specific components within PowerShell.</span></span> <span data-ttu-id="ffd8c-224">Efter</span><span class="sxs-lookup"><span data-stu-id="ffd8c-224">By</span></span> |
|           |<span data-ttu-id="ffd8c-225">Protokoll</span><span class="sxs-lookup"><span data-stu-id="ffd8c-225">Protocol</span></span>      |<span data-ttu-id="ffd8c-226">standard är alla nyckelord aktiverade och ändras</span><span class="sxs-lookup"><span data-stu-id="ffd8c-226">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="ffd8c-227">Transport</span><span class="sxs-lookup"><span data-stu-id="ffd8c-227">Transport</span></span>     |<span data-ttu-id="ffd8c-228">Det här värdet är bara användbart för mycket</span><span class="sxs-lookup"><span data-stu-id="ffd8c-228">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="ffd8c-229">Värd</span><span class="sxs-lookup"><span data-stu-id="ffd8c-229">Host</span></span>          |<span data-ttu-id="ffd8c-230">specialiserad fel sökning.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-230">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="ffd8c-231">Cmdletar</span><span class="sxs-lookup"><span data-stu-id="ffd8c-231">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="ffd8c-232">Serialiserare</span><span class="sxs-lookup"><span data-stu-id="ffd8c-232">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="ffd8c-233">Session</span><span class="sxs-lookup"><span data-stu-id="ffd8c-233">Session</span></span>       |                                             |
|           |<span data-ttu-id="ffd8c-234">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="ffd8c-234">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="ffd8c-235">Se även</span><span class="sxs-lookup"><span data-stu-id="ffd8c-235">See also</span></span>

<span data-ttu-id="ffd8c-236">För Linux **syslog** och **rsyslog. conf** information, se Linux-datorns lokala `man` sidor.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-236">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="ffd8c-237">För macOS **os_log** information, se [os_log Developer-dokumentation](https://developer.apple.com/documentation/os/os_log).</span><span class="sxs-lookup"><span data-stu-id="ffd8c-237">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="ffd8c-238">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="ffd8c-238">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="ffd8c-239">Allmän SIEM-integration</span><span class="sxs-lookup"><span data-stu-id="ffd8c-239">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management