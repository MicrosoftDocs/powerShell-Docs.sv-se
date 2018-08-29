---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Kommandoradshjälp för PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133849"
---
# <a name="powershellexe-command-line-help"></a>Kommandoradshjälp för PowerShell.exe

Du kan starta en PowerShell-session från kommandoraden för ett annat verktyg, till exempel Cmd.exe, med hjälp av PowerShell.exe eller använda den på PowerShell-kommandoraden för att starta en ny session. Använda parametrar för att anpassa sessionen.

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

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Accepterar en base-64-kodad strängversion av ett kommando. Använd den här parametern om du vill skicka till PowerShell-kommandon som kräver komplexa citattecken eller av klammerparenteser.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Anger principen för körning för den aktuella sessionen och sparar den i $env: PSExecutionPolicyPreference miljövariabeln. Den här parametern ändras inte PowerShell-körningsprincipen som anges i registret. Information om PowerShell-körningsprinciper, inklusive en lista över giltiga värden finns i [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Filen <FilePath> \[ <Parameters>]

Kör det angivna skriptet i det lokala scopet (”punkt källkod”), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen. Ange sökväg till skriptfilen och parametrar. **Filen** måste anges som sista parameter i kommandot. Alla värden efter den **-filen** parametern tolkas som skriptet som sökväg och parametrar skickades till skriptet.

Parametrarna som skickades till skriptet skickas som literala strängar (efter tolkning av den aktuella shell). Om du är i cmd.exe och vill skicka ett miljövariabelvärde du exempelvis använder du cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` skriptet i det här exemplet tar emot den exakta strängen `$env:windir` och inte värdet för den i miljövariabeln: `powershell -File .\test.ps1 -Sample $env:windir`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

Beskriver formatet för data som skickas till PowerShell. Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).

### <a name="-mta"></a>-Mta

Startar PowerShell med hjälp av en. Den här parametern introducerades i PowerShell 3.0. I PowerShell 3.0 är single-threaded apartment (STA) standard. I PowerShell 2.0 är inneslutning för flera trådar (MTA) standard.

### <a name="-noexit"></a>-NoExit

Inte avsluta när du har kört startkommandon.

### <a name="-nologo"></a>-NoLogo

Döljer copyright popup-meddelandet vid start.

### <a name="-noninteractive"></a>-Icke-interaktiv

Inte presentera en interaktiv prompt för användaren.

### <a name="-noprofile"></a>-NoProfile

Inte läsa in PowerShell-profilen.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Anger hur utdata från PowerShell ska formateras. Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Läser in den angivna filen i PowerShell-konsolen. Ange sökvägen och namnet på konsolfilen. Du kan skapa en MMC-konsol med den [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet i PowerShell.

### <a name="-sta"></a>-Sta

Startar PowerShell med hjälp av en single-threaded apartment. I PowerShell 3.0 är single-threaded apartment (STA) standard. I PowerShell 2.0 är inneslutning för flera trådar (MTA) standard.

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Startar den angivna versionen av PowerShell. Den version som du anger måste installeras på systemet. Om PowerShell 3.0 är installerad på datorn, är giltiga värden ”2.0” och ”3.0”. Standardvärdet är ”3.0”.

Om PowerShell 3.0 inte är installerad, är det enda giltiga värdet ”2.0”. Andra värden ignoreras.

Mer information finns i [installera Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Anger formatmallen fönster för sessionen. Giltiga värden är Normal, minimerat, maximerat och dold.

### <a name="-command"></a>-Kommandot

Kör de angivna kommandon (med några parametrar) som om de har skrivits i PowerShell-Kommandotolken. Efter körning, PowerShell avslutas om inte den `-NoExit` parameter har angetts.
Text efter `-Command` skickas som en enda kommandorad till PowerShell. Detta skiljer sig från hur `-File` hanterar parametrar som skickas till ett skript.

Värdet för kommandot kan vara ”-”, en sträng. eller ett skriptblock. Om värdet för kommandot är ”-”, kommandotexten läses från kommandoraden.

Skriptblocken måste stå inom klamrar ({}). Du kan ange ett skriptblock endast när du kör PowerShell.exe i PowerShell. Resultatet av skriptet returneras till överordnade gränssnittet som avserialiserade XML-objekt, inte live-objekt.

Om värdet för kommandot är en sträng **kommandot** måste anges som sista parameter i kommandot eftersom några tecken har angett när kommandot tolkas som kommandoradsargument.

Använd format för att skriva en sträng som kör ett PowerShell-kommando:

```powershell
"& {<command>}"
```

Citattecken anger en sträng och invoke-operatorn (&) gör att kommandot ska köras.

### <a name="-help---"></a>-Help-,?, /?

Visar syntaxen för powershell.exe. Om du skriver ett PowerShell.exe-kommando i PowerShell, Lägg till åtkomstgruppen kommandoparametrarna med ett bindestreck (-), inte ett snedstreck (/). Du kan använda ett bindestreck eller snedstreck i Cmd.exe.

> [!NOTE]
> Felsökningsmeddelande: I PowerShell 2.0, starta vissa program i Windows PowerShell konsolen inte med en LastExitCode av 0xc0000142.

## <a name="examples"></a>EXEMPEL

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
