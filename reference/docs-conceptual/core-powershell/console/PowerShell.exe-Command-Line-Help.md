---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "PowerShell.exe hjälpen för kommandoraden"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe hjälp
Windows PowerShell-sessionen. Du kan starta en PowerShell-session från kommandoraden av ett annat verktyg, till exempel Cmd.exe, med hjälp av PowerShell.exe eller använda den på PowerShell-kommandoraden för att starta en ny session. Använda parametrar för att anpassa sessionen.

## <a name="syntax"></a>Syntax

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Parametrar

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand<Base64EncodedCommand>
Accepterar en base-64-kodad strängversion av ett kommando. Använd den här parametern om du vill skicka till PowerShell-kommandon som kräver komplexa citattecken eller klammerparenteser.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy<ExecutionPolicy>
Anger standardprincipen för körning för den aktuella sessionen och sparar den i $env: PSExecutionPolicyPreference miljövariabeln. Den här parametern ändras inte PowerShell-körningsprincipen som anges i registret. Mer information om principer för körning av PowerShell, inklusive en lista över giltiga värden finns about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).

### <a name="-file-filepath-parameters"></a>-Filen <FilePath> \[ <Parameters>]
Kör det angivna skriptet i den lokala omfattningen (”punkt-källkod”), så att de funktioner och variabler som skapas är tillgängliga i den aktuella sessionen. Ange sökväg till skriptfilen och eventuella parametrar. **Filen** måste vara den sista parametern i kommandot, eftersom alla tecken skrev efter den **filen** parameternamnet tolkas som sökväg till skriptfilen följt av skriptparametrarna och deras värden.

Du kan inkludera parametrarna för ett skript och parametervärden, i värdet för den **filen** parameter. Till exempel: `-File .\Get-Script.ps1 -Domain Central` Observera att parametrar som skickas till skriptet skickas som literal strängar (efter tolkning av den aktuella shell).
Till exempel om du är i cmd.exe och vill skicka ett miljövariabelvärde du skulle använda cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` om du skulle använda PowerShell-syntax och sedan i det här exemplet i skriptet kan få literalen ”$env: windir” och inte värdet för som miljövariabeln:`powershell -File .\test.ps1 -Sample $env:windir`

Normalt är parametrarna växel för ett skript ingår eller utelämnas. Till exempel följande kommando använder den **alla** parametern i Get-Script.ps1 skriptfil:`-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}
Beskriver formatet för data som skickas till PowerShell. Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).

### <a name="-mta"></a>-Mta
Startar PowerShell med hjälp av en flertrådad inneslutning. Den här parametern introduceras i PowerShell 3.0. I PowerShell 3.0 används enkeltrådad inneslutning (STA) som standard. I PowerShell 2.0 används inneslutning för flera trådar (MTA) som standard.

### <a name="-noexit"></a>-NoExit
Inte avslutas när du har kört startkommandon.

### <a name="-nologo"></a>-NoLogo
Döljer copyright banderoll vid start.

### <a name="-noninteractive"></a>-Icke-interaktiv
Inte innebär en interaktiv prompt för användaren.

### <a name="-noprofile"></a>-NoProfile
Inte att läsa in PowerShell-profil.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}
Avgör hur utdata från PowerShell är formaterad. Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile<FilePath>
Läser in den angivna filen i PowerShell-konsolen. Ange sökvägen och filnamnet för konsolen. Så här skapar du en MMC-konsol på [Export konsolen](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet i PowerShell.

### <a name="-sta"></a>-Sta
Startar PowerShell med hjälp av en enkeltrådad inneslutning. I PowerShell 3.0 används enkeltrådad inneslutning (STA) som standard. I PowerShell 2.0 används inneslutning för flera trådar (MTA) som standard.

### <a name="-version-powershell-version"></a>-Version<PowerShell Version>
Startar den angivna versionen av PowerShell. Den version som du anger måste installeras på datorn. Om PowerShell 3.0 är installerat på datorn, är giltiga värden ”2.0” och ”3.0”. Standardvärdet är ”3.0”.

Om PowerShell 3.0 inte är installerad, är det enda giltiga värdet ”2.0”. Andra värden ignoreras.

Mer information finns i ”installera PowerShell” i den [komma igång med PowerShell [gamla MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).

### <a name="-windowstyle-window-style"></a>-WindowStyle<Window style>
Anger fönsterformatet för sessionen. Giltiga värden är Normal, minimerat, maximerat och dold.

### <a name="-command"></a>-Kommandot
Kör angivet kommando (och eventuella parametrar) som om de har skrivits i PowerShell-Kommandotolken och sedan avslutas, såvida inte parametern NoExit har angetts.
I princip alla text efter `-Command` skickas som en enda kommandorad till PowerShell (Detta skiljer sig från hur `-File` hanterar parametrar som skickas till ett skript).

Värdet för kommandot kan vara ”-”, en sträng. eller ett skriptblock. Om värdet för kommandot är ”-”, kommandotexten läses från standardindata.

Skriptblocken måste stå inom klamrar ({}). Du kan ange ett skriptblock bara när du kör PowerShell.exe i PowerShell. Resultaten av skriptet returneras till överordnade shell som avserialiserat XML-objekt, inte live-objekt.

Om värdet för kommandot är en sträng, **kommandot** måste vara den sista parametern i kommandot, eftersom alla tecken angav efter kommandot tolkas som kommandoargument.

Använd format för att skriva en sträng som kör ett PowerShell-kommando:

```
"& {<command>}"
```

där citattecken anger att en sträng och invoke-operatorn (&) gör att kommandot ska köras.

### <a name="-help---"></a>-Help-,?, /?
Visar det här meddelandet. Om du skriver kommandot PowerShell.exe i PowerShell lägga kommandoparametrarna med ett bindestreck (-), inte ett snedstreck (/). Du kan använda ett bindestreck eller snedstreck i Cmd.exe.

> [!NOTE]
> Felsökningsanteckning: I PowerShell 2.0, starta vissa program i Windows PowerShell konsolen inte med en LastExitCode av 0xc0000142.

## <a name="examples"></a>EXEMPEL

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

