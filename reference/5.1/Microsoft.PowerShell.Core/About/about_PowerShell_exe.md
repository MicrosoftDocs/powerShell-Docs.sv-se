---
description: Förklarar hur du använder `powershell.exe` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272024"
---
# <a name="about-powershellexe"></a>Om PowerShell.exe

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du använder `powershell.exe` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.

## <a name="long-description"></a>Lång beskrivning

### <a name="syntax"></a>SYNTAX

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a>Parametrar

#### <a name="-psconsolefile-filepath"></a>-PSConsoleFile \<FilePath\>

Läser in den angivna filen med PowerShell-konsolen. Ange sökvägen till och namnet på konsol filen. Om du vill skapa en konsol fil använder du Export-Console cmdlet i PowerShell.

#### <a name="-version-powershell-version"></a>-Version \<PowerShell Version\>

Startar den angivna versionen av PowerShell. Giltiga värden är 2,0 och 3,0. Den version som du anger måste vara installerad i systemet. Om Windows PowerShell 3,0 är installerat på datorn är "3,0" standard versionen.
Annars är "2,0" standard versionen. Mer information finns i [Installera PowerShell](/powershell/scripting/install/installing-windows-powershell).

#### <a name="-nologo"></a>-Nologo typ

Döljer Copyright-banderollen vid start.

#### <a name="-noexit"></a>-Noexit

Avslutas inte när du har kört Start kommandon.

#### <a name="-sta"></a>– Sta

Startar PowerShell med en enkel trådad inne slutning. I Windows PowerShell 2,0 är flertrådad inne slutning standardvärdet. I Windows PowerShell 3,0 är en enkel trådad Apartment (STA) som standard.

#### <a name="-mta"></a>-Mta

Startar PowerShell med en flertrådad inne slutning. Den här parametern introduceras i PowerShell 3,0. I PowerShell 2,0 är flertrådad inne slutning standardvärdet. I PowerShell 3,0 är en enkel trådad Apartment (STA) som standard.

#### <a name="-noprofile"></a>-Noprofil

Läser inte in PowerShell-profilen.

#### <a name="-noninteractive"></a>-Ej interaktiv

Visar inte en interaktiv prompt till användaren.

#### <a name="-inputformat-text--xml"></a>-InputFormat {text | FIL

Beskriver formatet på data som skickas till PowerShell. Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).

#### <a name="-outputformat-text--xml"></a>-OutputFormat {text | FIL

Anger hur utdata från PowerShell formateras. Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).

#### <a name="-windowstyle-window-style"></a>– WindowStyle \<Window style\>

Anger fönster formatet för sessionen. Giltiga värden är normal, minimerat, maximerat och dolt.

#### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand \<Base64EncodedCommand\>

Accepterar en Base-64-kodad sträng version av ett kommando. Använd den här parametern för att skicka kommandon till PowerShell som kräver komplexa citat tecken eller klammerparenteser. Strängen måste vara formaterad med UTF-16LE tecken kodning.

#### <a name="-configurationname-string"></a>– ConfigurationName \<string\>

Anger en konfigurations slut punkt där PowerShell körs. Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.

#### <a name="-file----filepath-args"></a>-Fil-| \<filePath\>\<args\>

Om värdet för **filen** är "-" läses kommando texten in från standar din data.
Om du kör `powershell -File -` utan omdirigerade standar ininformation startar en vanlig session. Detta är detsamma som att inte ange **fil** parametern alls.

Om **filens** värde är en fil Sök väg körs skriptet i det lokala omfånget ("punkt-källad"), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen. Ange sökvägen till skript filen och eventuella parametrar. **Filen** måste vara den sista parametern i kommandot. Alla värden som skrivs efter **fil** parametern tolkas som skript filens sökväg och parametrar som skickas till skriptet.

Parametrar som skickas till skriptet skickas som litterala strängar efter tolkning av det aktuella gränssnittet. Om du till exempel är i **cmd.exe** och vill skicka ett miljö variabel värde, använder du **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`

I motsats, som körs `powershell.exe -File .\test.ps1 -TestParam $env:windir` i **cmd.exe** , resulterar i att skriptet tar emot en litteral sträng `$env:windir` , eftersom det inte har någon särskild betydelse för det aktuella **cmd.exe** gränssnittet. `$env:windir`Formatet för miljö variabel referens _kan_ användas i en **kommando** parameter, eftersom den tolkas som PowerShell-kod.

Om du vill köra samma kommando från ett **kommando skript** använder du `%~dp0` i stället för `.\` eller `$PSScriptRoot` för att representera den aktuella körnings katalogen: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .
Om du i stället använde `.\test.ps1` , skulle PowerShell utlösa ett fel eftersom det inte går att hitta den litterala sökvägen `.\test.ps1`

När **filens värde är en** fil Sök väg måste **filen** _must_ vara den sista parametern i kommandot eftersom eventuella tecken som skrivs efter **fil** parameterns namn tolkas som skript filens sökväg följt av skript parametrarna.

Du kan inkludera skript parametrar och värden i värdet för **fil** parametern. Exempelvis: `-File .\Get-Script.ps1 -Domain Central`

Normalt ingår eller utelämnas växel parametrarna för ett skript.
Följande kommando använder till exempel parametern **all** i `Get-Script.ps1` skript filen: `-File .\Get-Script.ps1 -All`

I sällsynta fall kan du behöva ange ett **booleskt** värde för en parameter.
Det går inte att skicka ett explicit booleskt värde för en växel parameter när ett skript körs på det här sättet. Den här begränsningen har tagits bort i PowerShell 6 ( `pwsh.exe` ).

#### <a name="-executionpolicy-executionpolicy"></a>– ExecutionPolicy \<ExecutionPolicy\>

Anger standard körnings principen för den aktuella sessionen och sparar den i `$env:PSExecutionPolicyPreference` miljö variabeln. Den här parametern ändrar inte den körnings princip för PowerShell som anges i registret. Information om körnings principer för PowerShell, inklusive en lista över giltiga värden, finns [about_Execution_Policies](about_Execution_Policies.md).

#### <a name="-command"></a>-Kommando

Kör de angivna kommandona (och alla parametrar) som om de skrevs i PowerShell-Kommandotolken och sedan avslutas, om inte `NoExit` parametern anges.

Värdet för **kommandot** kan vara `-` , ett skript block eller en sträng. Om **kommandots** värde är `-` läses kommando texten in från standar din information.

**Kommando** parametern accepterar bara ett-skript block för körning när det kan identifiera värdet som skickas till **kommandot** som en **script block** -typ. Detta är _endast_ möjligt när du kör `powershell.exe` från en annan PowerShell-värd. **Script block** -typen kan finnas i en befintlig variabel, returneras från ett uttryck eller parsas av PowerShell-värden som ett litteralt-skript block som omges av klammerparenteser ( `{}` ), innan de skickas till `powershell.exe` .

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

I finns `cmd.exe` det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng. Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.

En sträng som skickas till **kommandot** körs fortfarande som PowerShell-kod, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från `cmd.exe` . Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) `&` :

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

Om värdet för **kommandot** är en sträng måste **kommandot** vara den sista parametern för pwsh, eftersom alla argument som följer tolkas som en del av kommandot som ska köras.

När de anropas i en befintlig PowerShell-session returneras resultatet till det överordnade gränssnittet som avserialiserade XML-objekt, inte aktiva objekt. För andra gränssnitt returneras resultaten som strängar.

Om **kommandots** värde är `-` läses kommando texten in från standar din information. Du måste omdirigera standar din information när du använder **kommando** parametern med standar din information. Ett exempel:

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

I det här exemplet skapas följande utdata:

```Output
in
hi there
out
```

Avslutnings koden för processen avgörs av status för det sista (körda) kommandot i skript blocket. Slut koden är `0` när `$?` är `$true` eller `1` när `$?` är `$false` . Om det sista kommandot är ett externt program eller ett PowerShell-skript som explicit anger en slut kod som `0` inte `1` är eller, konverteras slut koden till `1` för process avslutnings kod. Om du vill bevara den angivna slut koden lägger du till den `exit $LASTEXITCODE` i kommando strängen eller skript blocket.

På samma sätt returneras värdet 1 när ett skript avslutas (körnings utrymme), till exempel ett `throw` eller `-ErrorAction Stop` , inträffar eller när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd>.

Det går _bara_ att köra **PowerShell.exe** från en annan PowerShell-värd.
**Script block** -typen kan finnas i en befintlig variabel, returnerad från ett uttryck eller parsas av PowerShell-värden som ett litteralt skript block inom klammerparenteser `{}` innan de skickas till **PowerShell.exe**.

I **cmd.exe** finns det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng. Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.

En sträng som skickas till **kommandot** körs fortfarande som PowerShell, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från **cmd.exe**. Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) 
 `&` :

```console
"& {<command>}"
```

#### <a name="-help---"></a>– Hjälp,-?,/?

Visar hjälp för **PowerShell.exe**. Om du skriver ett **PowerShell.exe** kommando i en PowerShell-session, lägga kommando parametrarna med bindestreck (-), inte ett snedstreck (/). Du kan använda antingen bindestreck eller snedstreck i **cmd.exe**.

### <a name="remarks"></a>REMARKS

Fel söknings meddelande: i PowerShell 2,0 går det inte att starta vissa program från PowerShell-konsolen med en **LastExitCode** av 0xc0000142.

### <a name="examples"></a>EXEMPEL

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
