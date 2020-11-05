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
# <a name="about-logging-non-windows"></a>Om loggning av icke-Windows

## <a name="short-description"></a>Kort beskrivning
PowerShell loggar interna åtgärder från motorn, providers och cmdlets.

## <a name="long-description"></a>Lång beskrivning

PowerShell loggar information om PowerShell-åtgärder. PowerShell loggar till exempel åtgärder som att starta och stoppa motorn, starta och stoppa providrar. Den kommer också att logga information om PowerShell-kommandon.

Platsen för PowerShell-loggar är beroende av mål plattformen. I **Linux** kan PowerShell-loggar till **syslog** och **rsyslog. conf** användas. Mer information finns på Linux-datorns lokala `man` sidor. I **MacOS** används **os_log** loggnings systemet. Mer information finns i [os_log Developer-dokumentation](https://developer.apple.com/documentation/os/os_log).

## <a name="viewing-powershell-log-output-on-linux"></a>Visa PowerShell-loggens utdata på Linux

PowerShell-loggar till **syslog** i Linux och de verktyg som ofta används för att visa **syslog** -innehåll kan användas.

Formatet för logg posterna använder följande mall:

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|Fält        |Beskrivning                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |Ett datum/tid när logg posten genererades.            |
|`MACHINENAME`|Namnet på systemet där loggen skapades.      |
|`PID`        |Process-ID för processen som skrev logg posten. |
|`COMMITID`   |Det `git commit` ID eller den tagg som används för att skapa bygget.   |
|`TID`        |Tråd-ID för tråden som skrev logg posten.   |
|`CID`        |Den hexadecimala kanal identifieraren för logg posten.            |
|             |10 = drift, 11 = analys                         |
|`EVENTID`    |Händelse identifieraren för logg posten.                  |
|`TASK`       |Aktivitets identifieraren för händelse posten                 |
|`OPCODE`     |Opcode för händelse posten                          |
|`LEVEL`      |Logg nivån för händelse posten                       |
|`MESSAGE`    |Det meddelande som är associerat med händelse posten             |

> [!NOTE]
> `EVENTID`, `TASK` , `OPCODE` , och `LEVEL` är samma värden som när du loggar in på Windows-händelseloggen.

### <a name="filtering-powershell-log-entries-using-rsyslog"></a>Filtrera PowerShell-logg poster med rsyslog

Normalt skrivs PowerShell-logg poster till standardvärdet `location/file` för **syslog**. Det går dock att omdirigera posterna till en anpassad fil.

1. Skapa en conf för PowerShell-logg konfiguration och ange ett tal som är mindre än 50 (för `50-default.conf` ), till exempel `40-powershell.conf` . Filen ska placeras under `/etc/rsyslog.d` .

1. Lägg till följande post i filen:

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. Se till att `/etc/rsyslog.conf` innehåller den nya filen. Ofta har den ett generiskt include-uttryck som ser ut som följande konfiguration:

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   Om den inte gör det måste du lägga till en include-instruktion manuellt.

1. Kontrol lera att attribut och behörigheter är korrekt inställda.

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. Ange ägare till **rot**.

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. Ange åtkomst behörigheter: **roten** har Läs-och Skriv behörighet, **användare** har läst.

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a>Visa PowerShell-loggens utdata på macOS

Den enklaste metoden för att Visa PowerShell-loggens utdata på macOS är att använda **konsol** programmet.

1. Sök efter **konsol** programmet och starta det.
1. Välj dator namnet under **enheter**.
1. I **Sök** fältet anger `pwsh` du för den huvudsakliga binärfilen för PowerShell.
1. Ändra Sök filtret från `Any` till `Process` .
1. Utför åtgärderna.
1. Du kan också spara sökningen för framtida användning.

För att filtrera på en speciell process instans av PowerShell i- **konsolen** innehåller variabeln `$pid` process-ID.

1. Ange **PID** (process-ID) i **Sök** fältet.
1. Ändra Sök filtret till `PID` .
1. Utför åtgärderna.

### <a name="viewing-powershell-log-output-from-a-command-line"></a>Visa PowerShell-loggens utdata från en kommando rad

`log`Kommandot kan användas för att Visa PowerShell-logg poster från kommando raden.

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a>Bevara PowerShell-loggens utdata

Som standard använder PowerShell standard-endast minnes loggning på macOS. Du kan ändra det här beteendet om du vill aktivera persistence med `log config` kommandot.

Följande skript aktiverar loggning och persistence på informations nivå:

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

Följande kommando återställer PowerShell-loggningen till standard läget:

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

När persistence har Aktiver ATS `log show` kan du använda kommandot för att exportera logg objekt. Kommandot innehåller alternativ för att exportera de senaste N objekten, artiklar sedan en bestämd tid eller objekt inom ett angivet tidsintervall.

Följande kommando exporterar till exempel objekt sedan `9am on April 5 of 2018` :

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

Du kan få hjälp `log` genom att köra `log show --help` Ytterligare information.

> [!TIP]
> När du kör något av logg kommandona från en PowerShell-prompt eller ett skript, använder du dubbla citat tecken runt hela predikatet och enkla citat tecken i. På så sätt undviker du att undvika dubbla citat tecken i predikatet.

Du kanske också vill överväga att spara händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator. Du kan konfigurera SIEM i Azure. Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).

## <a name="configuring-logging-on-a-non-windows-system"></a>Konfigurera loggning på ett system som inte är från Windows

I Windows konfigureras loggning genom att skapa ETW spårnings lyssnare eller genom att använda Loggboken för att aktivera analytisk loggning. På Linux och macOS konfigureras loggning med hjälp av filen `powershell.config.json` . Resten av det här avsnittet beskriver hur du konfigurerar PowerShell-loggning på ett system som inte är från Windows.

Som standard aktiverar PowerShell informations loggning till den operativa kanalen. Det här innebär att alla logg utdata som genereras av PowerShell och som har marker ATS som operativa och som har en logg (spårning) som är större än information kommer att loggas. Ibland kan diagnoser kräva ytterligare logg data, t. ex. utförlig logg utdata eller för att aktivera analys loggs utdata.

Filen `powershell.config.json` är en **JSON** -formaterad fil som finns i PowerShell- `$PSHOME` katalogen. Varje installation av PowerShell använder en egen kopia av den här filen. För normal drift ändras den här filen oförändrad. Även om det kan vara användbart, ändra några av inställningarna i filen för diagnostik eller för att skilja mellan flera PowerShell-versioner på samma system eller till och med flera kopior av samma version (se `LogIdentity` tabellen nedan).

Följande kod är ett exempel på en konfiguration:

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

Egenskaperna för att konfigurera PowerShell-loggning visas i följande tabell. Värden som är markerade med en asterisk, till exempel `Operational*` , anger standardvärdet när inget värde anges i filen.

|Egenskap   |Värden        |Beskrivning                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|(sträng namn) |Namnet som ska användas vid loggning. Som standard tilldelar  |
|           |PowerShell   |PowerShell är identiteten. Det här värdet kan vara|
|           |              |används för att berätta skillnaden mellan två      |
|           |              |instanser av en PowerShell-installation, t. ex. |
|           |              |som version och beta version. Det här värdet är |
|           |              |används också för att omdirigera logg utdata till en        |
|           |              |separat fil på Linux. Se diskussionen om|
|           |              |**rsyslog** ovan.                           |
|`LogChannels`|Verksamhetsrelaterade  |Kanaler som ska aktive ras. Avgränsa värdena|
|           |Analys      |med ett kommatecken när du anger fler än ett.  |
|`LogLevel`   |Always        |Ange ett enskilt värde. Värdet aktiverar  |
|           |Kritiskt      |sig själv och alla värden ovanför den i        |
|           |Fel         |i listan till vänster.                            |
|           |Varning       |                                             |
|           |Informations|                                             |
|           |Verbose       |                                             |
|           |Felsökning         |                                             |
|`LogKeywords`|Körnings utrymme      |Nyckelord ger möjlighet att begränsa loggning|
|           |Pipeline      |till vissa komponenter i PowerShell. Efter |
|           |Protokoll      |standard är alla nyckelord aktiverade och ändras |
|           |Transport     |Det här värdet är bara användbart för mycket           |
|           |Värd          |specialiserad fel sökning.                |
|           |Cmdletar       |                                             |
|           |Serialiserare    |                                             |
|           |Session       |                                             |
|           |ManagedPlugin |                                             |

## <a name="see-also"></a>Se även

För Linux **syslog** och **rsyslog. conf** information, se Linux-datorns lokala `man` sidor.

För macOS **os_log** information, se [os_log Developer-dokumentation](https://developer.apple.com/documentation/os/os_log).

[about_Logging_Windows](about_Logging_Windows.md)

[Allmän SIEM-integration](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
