---
description: PowerShell loggar interna åtgärder från motorn, providers och cmdlets.
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: f70e2cb2c04287e36ecdf21a97dd099fcfd23d65
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355501"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="2d7fb-104">Om loggning av icke-Windows</span><span class="sxs-lookup"><span data-stu-id="2d7fb-104">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="2d7fb-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-105">Short description</span></span>
<span data-ttu-id="2d7fb-106">PowerShell loggar interna åtgärder från motorn, providers och cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="2d7fb-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-107">Long description</span></span>

<span data-ttu-id="2d7fb-108">PowerShell loggar information om PowerShell-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-108">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="2d7fb-109">PowerShell loggar till exempel åtgärder som att starta och stoppa motorn, starta och stoppa providrar.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-109">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="2d7fb-110">Den kommer också att logga information om PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-110">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="2d7fb-111">Platsen för PowerShell-loggar är beroende av mål plattformen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-111">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="2d7fb-112">I **Linux** kan PowerShell-loggar till **syslog** och **rsyslog. conf** användas.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-112">On **Linux** , PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="2d7fb-113">Mer information finns på Linux-datorns lokala `man` sidor.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-113">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="2d7fb-114">I **MacOS** används **os_log** loggnings systemet.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-114">On **macOS** , the **os_log** logging system is used.</span></span> <span data-ttu-id="2d7fb-115">Mer information finns i [os_log Developer-dokumentation](https://developer.apple.com/documentation/os/os_log).</span><span class="sxs-lookup"><span data-stu-id="2d7fb-115">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="2d7fb-116">Visa PowerShell-loggens utdata på Linux</span><span class="sxs-lookup"><span data-stu-id="2d7fb-116">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="2d7fb-117">PowerShell-loggar till **syslog** i Linux och de verktyg som ofta används för att visa **syslog** -innehåll kan användas.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-117">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="2d7fb-118">Formatet för logg posterna använder följande mall:</span><span class="sxs-lookup"><span data-stu-id="2d7fb-118">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="2d7fb-119">Fält</span><span class="sxs-lookup"><span data-stu-id="2d7fb-119">Field</span></span>        |<span data-ttu-id="2d7fb-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-120">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="2d7fb-121">Ett datum/tid när logg posten genererades.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-121">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="2d7fb-122">Namnet på systemet där loggen skapades.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-122">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="2d7fb-123">Process-ID för processen som skrev logg posten.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-123">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="2d7fb-124">Det `git commit` ID eller den tagg som används för att skapa bygget.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-124">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="2d7fb-125">Tråd-ID för tråden som skrev logg posten.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-125">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="2d7fb-126">Den hexadecimala kanal identifieraren för logg posten.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-126">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="2d7fb-127">10 = drift, 11 = analys</span><span class="sxs-lookup"><span data-stu-id="2d7fb-127">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="2d7fb-128">Händelse identifieraren för logg posten.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-128">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="2d7fb-129">Aktivitets identifieraren för händelse posten</span><span class="sxs-lookup"><span data-stu-id="2d7fb-129">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="2d7fb-130">Opcode för händelse posten</span><span class="sxs-lookup"><span data-stu-id="2d7fb-130">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="2d7fb-131">Logg nivån för händelse posten</span><span class="sxs-lookup"><span data-stu-id="2d7fb-131">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="2d7fb-132">Det meddelande som är associerat med händelse posten</span><span class="sxs-lookup"><span data-stu-id="2d7fb-132">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="2d7fb-133">`EVENTID`, `TASK` , `OPCODE` , och `LEVEL` är samma värden som när du loggar in på Windows-händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-133">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="2d7fb-134">Filtrera PowerShell-logg poster med rsyslog</span><span class="sxs-lookup"><span data-stu-id="2d7fb-134">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="2d7fb-135">Normalt skrivs PowerShell-logg poster till standardvärdet `location/file` för **syslog**.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-135">Normally, PowerShell log entries are written to the default `location/file` for **syslog**.</span></span> <span data-ttu-id="2d7fb-136">Det går dock att omdirigera posterna till en anpassad fil.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-136">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="2d7fb-137">Skapa en conf för PowerShell-logg konfiguration och ange ett tal som är mindre än 50 (för `50-default.conf` ), till exempel `40-powershell.conf` .</span><span class="sxs-lookup"><span data-stu-id="2d7fb-137">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="2d7fb-138">Filen ska placeras under `/etc/rsyslog.d` .</span><span class="sxs-lookup"><span data-stu-id="2d7fb-138">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="2d7fb-139">Lägg till följande post i filen:</span><span class="sxs-lookup"><span data-stu-id="2d7fb-139">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="2d7fb-140">Se till att `/etc/rsyslog.conf` innehåller den nya filen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-140">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="2d7fb-141">Ofta har den ett generiskt include-uttryck som ser ut som följande konfiguration:</span><span class="sxs-lookup"><span data-stu-id="2d7fb-141">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="2d7fb-142">Om den inte gör det måste du lägga till en include-instruktion manuellt.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-142">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="2d7fb-143">Kontrol lera att attribut och behörigheter är korrekt inställda.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-143">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="2d7fb-144">Ange ägare till **rot**.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-144">Set ownership to **root**.</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="2d7fb-145">Ange åtkomst behörigheter: **roten** har Läs-och Skriv behörighet, **användare** har läst.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-145">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="2d7fb-146">Visa PowerShell-loggens utdata på macOS</span><span class="sxs-lookup"><span data-stu-id="2d7fb-146">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="2d7fb-147">Den enklaste metoden för att Visa PowerShell-loggens utdata på macOS är att använda **konsol** programmet.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-147">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="2d7fb-148">Sök efter **konsol** programmet och starta det.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-148">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="2d7fb-149">Välj dator namnet under **enheter**.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-149">Select the Machine name under **Devices**.</span></span>
1. <span data-ttu-id="2d7fb-150">I **Sök** fältet anger `pwsh` du för den huvudsakliga binärfilen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-150">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="2d7fb-151">Ändra Sök filtret från `Any` till `Process` .</span><span class="sxs-lookup"><span data-stu-id="2d7fb-151">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="2d7fb-152">Utför åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-152">Perform the operations.</span></span>
1. <span data-ttu-id="2d7fb-153">Du kan också spara sökningen för framtida användning.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-153">Optionally, save the search for future use.</span></span>

<span data-ttu-id="2d7fb-154">För att filtrera på en speciell process instans av PowerShell i- **konsolen** innehåller variabeln `$pid` process-ID.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-154">To filter on a specific process instance of PowerShell in the **Console** , the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="2d7fb-155">Ange **PID** (process-ID) i **Sök** fältet.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-155">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="2d7fb-156">Ändra Sök filtret till `PID` .</span><span class="sxs-lookup"><span data-stu-id="2d7fb-156">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="2d7fb-157">Utför åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-157">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="2d7fb-158">Visa PowerShell-loggens utdata från en kommando rad</span><span class="sxs-lookup"><span data-stu-id="2d7fb-158">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="2d7fb-159">`log`Kommandot kan användas för att Visa PowerShell-logg poster från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-159">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="2d7fb-160">Bevara PowerShell-loggens utdata</span><span class="sxs-lookup"><span data-stu-id="2d7fb-160">Persisting PowerShell log output</span></span>

<span data-ttu-id="2d7fb-161">Som standard använder PowerShell standard-endast minnes loggning på macOS.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-161">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="2d7fb-162">Du kan ändra det här beteendet om du vill aktivera persistence med `log config` kommandot.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-162">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="2d7fb-163">Följande skript aktiverar loggning och persistence på informations nivå:</span><span class="sxs-lookup"><span data-stu-id="2d7fb-163">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="2d7fb-164">Följande kommando återställer PowerShell-loggningen till standard läget:</span><span class="sxs-lookup"><span data-stu-id="2d7fb-164">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="2d7fb-165">När persistence har Aktiver ATS `log show` kan du använda kommandot för att exportera logg objekt.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-165">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="2d7fb-166">Kommandot innehåller alternativ för att exportera de senaste N objekten, artiklar sedan en bestämd tid eller objekt inom ett angivet tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-166">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="2d7fb-167">Följande kommando exporterar till exempel objekt sedan `9am on April 5 of 2018` :</span><span class="sxs-lookup"><span data-stu-id="2d7fb-167">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="2d7fb-168">Du kan få hjälp `log` genom att köra `log show --help` Ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-168">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="2d7fb-169">När du kör något av logg kommandona från en PowerShell-prompt eller ett skript, använder du dubbla citat tecken runt hela predikatet och enkla citat tecken i.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-169">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="2d7fb-170">På så sätt undviker du att undvika dubbla citat tecken i predikatet.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-170">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="2d7fb-171">Du kanske också vill överväga att spara händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-171">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="2d7fb-172">Du kan konfigurera SIEM i Azure.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-172">You can set up SIEM in Azure.</span></span> <span data-ttu-id="2d7fb-173">Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="2d7fb-173">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="2d7fb-174">Konfigurera loggning på ett system som inte är från Windows</span><span class="sxs-lookup"><span data-stu-id="2d7fb-174">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="2d7fb-175">I Windows konfigureras loggning genom att skapa ETW spårnings lyssnare eller genom att använda Loggboken för att aktivera analytisk loggning.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-175">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="2d7fb-176">På Linux och macOS konfigureras loggning med hjälp av filen `powershell.config.json` .</span><span class="sxs-lookup"><span data-stu-id="2d7fb-176">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="2d7fb-177">Resten av det här avsnittet beskriver hur du konfigurerar PowerShell-loggning på ett system som inte är från Windows.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-177">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="2d7fb-178">Som standard aktiverar PowerShell informations loggning till den operativa kanalen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-178">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="2d7fb-179">Det här innebär att alla logg utdata som genereras av PowerShell och som har marker ATS som operativa och som har en logg (spårning) som är större än information kommer att loggas.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-179">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="2d7fb-180">Ibland kan diagnoser kräva ytterligare logg data, t. ex. utförlig logg utdata eller för att aktivera analys loggs utdata.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-180">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="2d7fb-181">Filen `powershell.config.json` är en **JSON** -formaterad fil som finns i PowerShell- `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-181">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="2d7fb-182">Varje installation av PowerShell använder en egen kopia av den här filen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-182">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="2d7fb-183">För normal drift ändras den här filen oförändrad.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-183">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="2d7fb-184">Även om det kan vara användbart, ändra några av inställningarna i filen för diagnostik eller för att skilja mellan flera PowerShell-versioner på samma system eller till och med flera kopior av samma version (se `LogIdentity` tabellen nedan).</span><span class="sxs-lookup"><span data-stu-id="2d7fb-184">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="2d7fb-185">Följande kod är ett exempel på en konfiguration:</span><span class="sxs-lookup"><span data-stu-id="2d7fb-185">The following code is an example configuration:</span></span>

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

<span data-ttu-id="2d7fb-186">Egenskaperna för att konfigurera PowerShell-loggning visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-186">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="2d7fb-187">Värden som är markerade med en asterisk, till exempel `Operational*` , anger standardvärdet när inget värde anges i filen.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-187">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="2d7fb-188">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2d7fb-188">Property</span></span>   |<span data-ttu-id="2d7fb-189">Värden</span><span class="sxs-lookup"><span data-stu-id="2d7fb-189">Values</span></span>        |<span data-ttu-id="2d7fb-190">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-190">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="2d7fb-191">(sträng namn)</span><span class="sxs-lookup"><span data-stu-id="2d7fb-191">(string name)</span></span> |<span data-ttu-id="2d7fb-192">Namnet som ska användas vid loggning.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-192">The name to use when logging.</span></span> <span data-ttu-id="2d7fb-193">Som standard tilldelar</span><span class="sxs-lookup"><span data-stu-id="2d7fb-193">By default,</span></span>  |
|           |<span data-ttu-id="2d7fb-194">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d7fb-194">powershell\*</span></span>   |<span data-ttu-id="2d7fb-195">PowerShell är identiteten.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-195">powershell is the identity.</span></span> <span data-ttu-id="2d7fb-196">Det här värdet kan vara</span><span class="sxs-lookup"><span data-stu-id="2d7fb-196">This value can be</span></span>|
|           |              |<span data-ttu-id="2d7fb-197">används för att berätta skillnaden mellan två</span><span class="sxs-lookup"><span data-stu-id="2d7fb-197">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="2d7fb-198">instanser av en PowerShell-installation, t. ex.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-198">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="2d7fb-199">som version och beta version.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-199">as a release and beta version.</span></span> <span data-ttu-id="2d7fb-200">Det här värdet är</span><span class="sxs-lookup"><span data-stu-id="2d7fb-200">This value is</span></span> |
|           |              |<span data-ttu-id="2d7fb-201">används också för att omdirigera logg utdata till en</span><span class="sxs-lookup"><span data-stu-id="2d7fb-201">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="2d7fb-202">separat fil på Linux.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-202">separate file on Linux.</span></span> <span data-ttu-id="2d7fb-203">Se diskussionen om</span><span class="sxs-lookup"><span data-stu-id="2d7fb-203">See the discussion of</span></span>|
|           |              |<span data-ttu-id="2d7fb-204">**rsyslog** ovan.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-204">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="2d7fb-205">Verksamhetsrelaterade</span><span class="sxs-lookup"><span data-stu-id="2d7fb-205">Operational\*</span></span>  |<span data-ttu-id="2d7fb-206">Kanaler som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-206">The channels to enable.</span></span> <span data-ttu-id="2d7fb-207">Avgränsa värdena</span><span class="sxs-lookup"><span data-stu-id="2d7fb-207">Separate the values</span></span>|
|           |<span data-ttu-id="2d7fb-208">Analys</span><span class="sxs-lookup"><span data-stu-id="2d7fb-208">Analytic</span></span>      |<span data-ttu-id="2d7fb-209">med ett kommatecken när du anger fler än ett.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-209">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="2d7fb-210">Always</span><span class="sxs-lookup"><span data-stu-id="2d7fb-210">Always</span></span>        |<span data-ttu-id="2d7fb-211">Ange ett enskilt värde.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-211">Specify a single value.</span></span> <span data-ttu-id="2d7fb-212">Värdet aktiverar</span><span class="sxs-lookup"><span data-stu-id="2d7fb-212">The value enables</span></span>  |
|           |<span data-ttu-id="2d7fb-213">Kritiskt</span><span class="sxs-lookup"><span data-stu-id="2d7fb-213">Critical</span></span>      |<span data-ttu-id="2d7fb-214">sig själv och alla värden ovanför den i</span><span class="sxs-lookup"><span data-stu-id="2d7fb-214">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="2d7fb-215">Fel</span><span class="sxs-lookup"><span data-stu-id="2d7fb-215">Error</span></span>         |<span data-ttu-id="2d7fb-216">i listan till vänster.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-216">list to the left.</span></span>                            |
|           |<span data-ttu-id="2d7fb-217">Varning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-217">Warning</span></span>       |                                             |
|           |<span data-ttu-id="2d7fb-218">Informations</span><span class="sxs-lookup"><span data-stu-id="2d7fb-218">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="2d7fb-219">Verbose</span><span class="sxs-lookup"><span data-stu-id="2d7fb-219">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="2d7fb-220">Felsökning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-220">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="2d7fb-221">Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="2d7fb-221">Runspace</span></span>      |<span data-ttu-id="2d7fb-222">Nyckelord ger möjlighet att begränsa loggning</span><span class="sxs-lookup"><span data-stu-id="2d7fb-222">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="2d7fb-223">Pipeline</span><span class="sxs-lookup"><span data-stu-id="2d7fb-223">Pipeline</span></span>      |<span data-ttu-id="2d7fb-224">till vissa komponenter i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-224">to specific components within PowerShell.</span></span> <span data-ttu-id="2d7fb-225">Efter</span><span class="sxs-lookup"><span data-stu-id="2d7fb-225">By</span></span> |
|           |<span data-ttu-id="2d7fb-226">Protokoll</span><span class="sxs-lookup"><span data-stu-id="2d7fb-226">Protocol</span></span>      |<span data-ttu-id="2d7fb-227">standard är alla nyckelord aktiverade och ändras</span><span class="sxs-lookup"><span data-stu-id="2d7fb-227">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="2d7fb-228">Transport</span><span class="sxs-lookup"><span data-stu-id="2d7fb-228">Transport</span></span>     |<span data-ttu-id="2d7fb-229">Det här värdet är bara användbart för mycket</span><span class="sxs-lookup"><span data-stu-id="2d7fb-229">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="2d7fb-230">Värd</span><span class="sxs-lookup"><span data-stu-id="2d7fb-230">Host</span></span>          |<span data-ttu-id="2d7fb-231">specialiserad fel sökning.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-231">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="2d7fb-232">Cmdletar</span><span class="sxs-lookup"><span data-stu-id="2d7fb-232">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="2d7fb-233">Serialiserare</span><span class="sxs-lookup"><span data-stu-id="2d7fb-233">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="2d7fb-234">Session</span><span class="sxs-lookup"><span data-stu-id="2d7fb-234">Session</span></span>       |                                             |
|           |<span data-ttu-id="2d7fb-235">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="2d7fb-235">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="2d7fb-236">Se även</span><span class="sxs-lookup"><span data-stu-id="2d7fb-236">See also</span></span>

<span data-ttu-id="2d7fb-237">För Linux **syslog** och **rsyslog. conf** information, se Linux-datorns lokala `man` sidor.</span><span class="sxs-lookup"><span data-stu-id="2d7fb-237">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="2d7fb-238">För macOS **os_log** information, se [os_log Developer-dokumentation](https://developer.apple.com/documentation/os/os_log).</span><span class="sxs-lookup"><span data-stu-id="2d7fb-238">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="2d7fb-239">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="2d7fb-239">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="2d7fb-240">Allmän SIEM-integration</span><span class="sxs-lookup"><span data-stu-id="2d7fb-240">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
