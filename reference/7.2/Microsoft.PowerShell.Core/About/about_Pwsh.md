---
description: Förklarar hur du använder `pwsh` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: b31563dd7058d85eb76f34c61d9bff5558a786b0
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693108"
---
# <a name="about-pwsh"></a>Om pwsh

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du använder `pwsh` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.

## <a name="long-description"></a>Lång beskrivning

## <a name="syntax"></a>Syntax

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a>Parametrar

Alla parametrar är inte Skift läges känsliga.

### <a name="-file---f"></a>-Fil | -f

Om värdet för `File` är `-` , läses kommando texten från standar din information.
Om du kör `pwsh -File -` utan omdirigerade standar ininformation startar en vanlig session. Detta är detsamma som att inte ange `File` parametern alls.

Detta är standard parametern om inga parametrar finns, men värden finns på kommando raden. Det angivna skriptet körs i det lokala omfånget ("punkt-källad"), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen. Ange sökvägen till skript filen och eventuella parametrar. Filen måste vara den sista parametern i kommandot eftersom alla tecken som skrivs efter fil parameterns namn tolkas som skript filens sökväg följt av skript parametrarna.

Normalt ingår eller utelämnas växel parametrarna för ett skript.
Följande kommando använder till exempel parametern all i Get-Script.ps1-skript filen: `-File .\Get-Script.ps1 -All`

I sällsynta fall kan du behöva ange ett **booleskt** värde för en switch-parameter. Om du vill ange ett **booleskt** värde för en växel parameter i värdet för **fil** parametern använder du parametern som normalt följs omedelbart av ett kolon och det booleska värdet, till exempel följande: `-File .\Get-Script.ps1 -All:$False` .

Parametrar som skickas till skriptet skickas som litterala strängar efter tolkning av det aktuella gränssnittet. Om du till exempel är i `cmd.exe` och vill skicka ett miljö variabel värde använder du `cmd.exe` syntaxen: `pwsh -File .\test.ps1 -TestParam %windir%`

Däremot körs `pwsh -File .\test.ps1 -TestParam $env:windir` i `cmd.exe` resulterar i skriptet som tar emot en litteral sträng `$env:windir` eftersom det inte har någon speciell betydelse för det aktuella `cmd.exe` gränssnittet. `$env:windir`Formatet för miljö variabel referens _kan_ användas i en **kommando** parameter, eftersom den tolkas som PowerShell-kod.

Om du vill köra samma kommando från ett _kommando skript_ använder du `%~dp0` i stället för `.\` eller `$PSScriptRoot` för att representera den aktuella körnings katalogen: `pwsh -File %~dp0test.ps1 -TestParam %windir%` . Om du i stället använde `.\test.ps1` , skulle PowerShell utlösa ett fel eftersom det inte går att hitta den litterala sökvägen `.\test.ps1`

När skript filen slutar med ett `exit` kommando, anges process avslutnings koden till det numeriska argument som används med `exit` kommandot. Vid normal avslutning är slut koden alltid `0` .

Precis som `-Command` när ett skript avslutas, anges avslutnings koden till `1` . Men till skillnad från `-Command` , när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd> , är slut koden `0` .

### <a name="-command---c"></a>-Kommando | -c

Kör de angivna kommandona (och alla parametrar) som om de skrevs i PowerShell-Kommandotolken och sedan avslutas, om inte `NoExit` parametern anges.

Värdet för **kommandot** kan vara `-` , ett skript block eller en sträng. Om **kommandots** värde är `-` läses kommando texten in från standar din information.

**Kommando** parametern accepterar bara ett-skript block för körning när det kan identifiera värdet som skickas till **kommandot** som en **script block** -typ. Detta är _endast_ möjligt när du kör `pwsh` från en annan PowerShell-värd. **Script block** -typen kan finnas i en befintlig variabel, returneras från ett uttryck eller parsas av PowerShell-värden som ett litteralt-skript block som omges av klammerparenteser ( `{}` ), innan de skickas till `pwsh` .

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

I finns `cmd.exe` det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng. Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.

En sträng som skickas till **kommandot** körs fortfarande som PowerShell-kod, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från `cmd.exe` . Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) `&` :

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

Om värdet för **kommandot** är en sträng måste **kommandot** vara den sista parametern för pwsh, eftersom alla argument som följer tolkas som en del av kommandot som ska köras.

När de anropas i en befintlig PowerShell-session returneras resultatet till det överordnade gränssnittet som avserialiserade XML-objekt, inte aktiva objekt. För andra gränssnitt returneras resultaten som strängar.

Om **kommandots** värde är `-` läses kommando texten in från standar din information. Du måste omdirigera standar din information när du använder **kommando** parametern med standar din information. Exempel:

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

### <a name="-configurationname---config"></a>-ConfigurationName | – config

Anger en konfigurations slut punkt där PowerShell körs. Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.

Exempel: `pwsh -ConfigurationName AdminRoles`

### <a name="-custompipename"></a>-CustomPipeName

Anger det namn som ska användas för ytterligare en IPC-Server (namngiven pipe) som används för fel sökning och annan Cross-process-kommunikation. Detta erbjuder en förutsägbar mekanism för att ansluta till andra PowerShell-instanser. Används vanligt vis med parametern **CustomPipeName** på `Enter-PSHostProcess` .

Den här parametern introducerades i PowerShell 6,2.

Exempel:

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a>-EncodedCommand | -e | – EC

Accepterar en Base64-kodad sträng version av ett kommando. Använd den här parametern för att skicka kommandon till PowerShell som kräver komplex, kapslad citat tecken. Base64-representationen måste vara en UTF-16LE-kodad sträng.

Exempel:

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a>-ExecutionPolicy | – ex | -EP

Anger standard körnings principen för den aktuella sessionen och sparar den i `$env:PSExecutionPolicyPreference` miljö variabeln. Den här parametern ändrar inte permanent konfigurerade körnings principer.

Den här parametern gäller endast för Windows-datorer. `$env:PSExecutionPolicyPreference`Miljövariabeln finns inte på plattformar som inte är Windows-plattformar.

### <a name="-inputformat---inp---if"></a>-InputFormat | -INP | – om

Beskriver formatet på data som skickas till PowerShell. Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).

### <a name="-interactive---i"></a>– Interaktiv | -i

Presentera en interaktiv prompt till användaren. Invertering för en ej interaktiv parameter.

### <a name="-login---l"></a>-Inloggning | -l

På Linux och macOS startar PowerShell som ett inloggnings gränssnitt med hjälp av/bin/sh för att köra inloggnings profiler som/etc/profile och ~/.Profile.
I Windows gör den här växeln ingenting.

> [!IMPORTANT]
> Den här parametern måste komma först för att starta PowerShell som ett inloggnings gränssnitt.
> Att skicka den här parametern i en annan position ignoreras.

Så här konfigurerar du `pwsh` som inloggnings gränssnitt på UNIX-liknande operativ system:

- Kontrol lera att den fullständiga absoluta sökvägen till `pwsh` visas under `/etc/shells`
  - Den här sökvägen är vanligt vis något som liknar `/usr/bin/pwsh` i Linux eller `/usr/local/bin/pwsh` MacOS
  - Med vissa installations metoder kommer den här posten att läggas till automatiskt vid installationen
  - Om `pwsh` inte finns i `/etc/shells` använder du en redigerare för att lägga till sökvägen till `pwsh` på den sista raden. Detta kräver förhöjd behörighet att redigera.
- Använd [chsh](https://linux.die.net/man/1/chsh) -verktyget för att ange den aktuella användarens gränssnitt till `pwsh` :

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> Inställningen `pwsh` som inloggnings gränssnitt stöds för närvarande inte i Windows-undersystemet för Linux (Wsl) och försöker ange `pwsh` som inloggnings gränssnitt. det kan leda till att det inte går att starta Wsl interaktivt.

### <a name="-mta"></a>-MTA

Starta PowerShell med en flertrådad inne slutning. Den här växeln är endast tillgänglig i Windows.

### <a name="-noexit---noe"></a>-Noexit | -noe

Avslutas inte när du har kört Start kommandon.

Exempel: `pwsh -NoExit -Command Get-Date`

### <a name="-nologo---nol"></a>-Nologo typ | -nol

Döljer Copyright-banderollen vid start av interaktiva sessioner.

### <a name="-noninteractive---noni"></a>-Ej interaktiv | -noni

Visar inte en interaktiv prompt till användaren. Alla försök att använda interaktiva funktioner, t `Read-Host` . ex. bekräftelser, resulterar i instruktionen-avslutar fel.

### <a name="-noprofile---nop"></a>-Noprofil | – NOP

Läser inte in PowerShell-profilerna.

### <a name="-outputformat---o---of"></a>-OutputFormat | -o | – av

Anger hur utdata från PowerShell formateras. Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).

Exempel: `pwsh -o XML -c Get-Date`

När du anropar med en PowerShell-session får du avserialiserade objekt som utdata i stället för vanliga strängar. Vid anrop från andra gränssnitt är utdata sträng data formaterade som CLIXML text.

### <a name="-settingsfile---settings"></a>-SettingsFile | – inställningar

Åsidosätter den systemomfattande `powershell.config.json` inställnings filen för sessionen. Som standard läses systemtäckande inställningar från `powershell.config.json` i `$PSHOME` katalogen.

Observera att de här inställningarna inte används av slut punkten som anges av `-ConfigurationName` argumentet.

Exempel: `pwsh -SettingsFile c:\myproject\powershell.config.json`

### <a name="-sshservermode---sshs"></a>-SSHServerMode | -sshs

Används i sshd_config för att köra PowerShell som ett SSH-undersystem. Den är inte avsedd eller stöds inte för någon annan användning.

### <a name="-sta"></a>– STA

Starta PowerShell med en enkel trådad inne slutning. Det här är standardinställningen. Den här växeln är endast tillgänglig i Windows.

### <a name="-version---v"></a>-Version | -v

Visar versionen av PowerShell. Ytterligare parametrar ignoreras.

### <a name="-windowstyle---w"></a>-WindowStyle | – w

Anger fönster formatet för sessionen. Giltiga värden är normal, minimerat, maximerat och dolt.

### <a name="-workingdirectory---wd"></a>-WorkingDirectory | -WD

Anger den inledande arbets katalogen genom att köra vid start. En giltig sökväg till PowerShell-filen stöds.

Om du vill starta PowerShell i din arbets katalog använder du: `pwsh -WorkingDirectory ~`

### <a name="-help---"></a>– Hjälp,-?,/?

Visar hjälp för `pwsh` . Om du skriver ett pwsh-kommando i PowerShell lägga kommando parametrarna med bindestreck ( `-` ), inte ett snedstreck ( `/` ).
