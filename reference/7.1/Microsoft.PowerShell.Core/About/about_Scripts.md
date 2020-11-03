---
description: Beskriver hur du kör och skriver skript i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: c877627f8caeab8309326826caa4ec13d65d5d9d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270158"
---
# <a name="about-scripts"></a>Om skript

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du kör och skriver skript i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Ett skript är en oformaterad textfil som innehåller ett eller flera PowerShell-kommandon.
PowerShell-skript har ett `.ps1` fil namns tillägg.

Att köra ett skript är ett mycket som att köra en cmdlet. Du anger sökvägen och fil namnet för skriptet och använder parametrar för att skicka data och ange alternativ. Du kan köra skript på datorn eller i en fjärran sluten session på en annan dator.

Att skriva ett skript sparar ett kommando för senare användning och gör det enkelt att dela med andra. Viktigast är att du kan köra kommandona genom att skriva skript Sök vägen och fil namnet. Skript kan vara lika enkla som ett enda kommando i en fil eller som ett komplext program.

Skript har ytterligare funktioner, till exempel `#Requires` särskilda kommentarer, användning av parametrar, stöd för data avsnitt och digital signering för säkerhet.
Du kan också skriva Hjälp avsnitt för skript och för alla funktioner i skriptet.

## <a name="how-to-run-a-script"></a>Så här kör du ett skript

Innan du kan köra ett skript i Windows måste du ändra standard körnings principen för PowerShell. Körnings principen gäller inte för PowerShell som körs på andra plattformar än Windows-plattformar.

Standard körnings principen, `Restricted` , förhindrar att alla skript körs, inklusive skript som du skriver på den lokala datorn. Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).

Körnings principen sparas i registret, så du behöver bara ändra den en gång på varje dator.

Använd följande procedur om du vill ändra körnings principen.

Skriv följande i kommandotolken:

```powershell
Set-ExecutionPolicy AllSigned
```

eller

```powershell
Set-ExecutionPolicy RemoteSigned
```

Ändringen träder i kraft omedelbart.

Om du vill köra ett skript anger du det fullständiga namnet och den fullständiga sökvägen till skript filen.

Om du till exempel vill köra Get-ServiceLog.ps1-skriptet i C:\Scripts-katalogen skriver du:

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

Om du vill köra ett skript i den aktuella katalogen anger du sökvägen till den aktuella katalogen eller använder en punkt för att representera den aktuella katalogen, följt av en sökväg för omvänt snedstreck ( `.\` ).

Om du till exempel vill köra ServicesLog.ps1-skriptet i den lokala katalogen skriver du:

```powershell
.\Get-ServiceLog.ps1
```

Om skriptet har parametrar anger du parametrarna och parameter värdena efter skript fil namnet.

Följande kommando använder till exempel parametern ServiceName i Get-ServiceLog-skriptet för att begära en logg över WinRM-tjänsteaktiviteten.

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

Som en säkerhetsfunktion kör PowerShell inte skript när du dubbelklickar på skript ikonen i Utforskaren eller när du skriver skript namnet utan en fullständig sökväg, även om skriptet finns i den aktuella katalogen. Mer information om att köra kommandon och skript i PowerShell finns [about_Command_Precedence](about_Command_Precedence.md).

### <a name="run-with-powershell"></a>Kör med PowerShell

Från och med PowerShell 3,0 kan du köra skript från Utforskaren.

Använda funktionen "kör med PowerShell":

Kör Utforskaren, högerklicka på skript filen och välj sedan kör med PowerShell.

Funktionen "kör med PowerShell" är utformad för att köra skript som inte har nödvändiga parametrar och som inte returnerar utdata till kommando tolken.

Mer information finns i [about_Run_With_PowerShell](about_Run_With_PowerShell.md).

### <a name="running-scripts-on-other-computers"></a>Köra skript på andra datorer

Om du vill köra ett skript på en eller flera fjärrdatorer använder du parametern **sökväg** för `Invoke-Command` cmdleten.

Ange sökvägen och fil namnet för skriptet som värdet för parametern **sökväg** . Skriptet måste finnas på den lokala datorn eller i en katalog som den lokala datorn kan komma åt.

Följande kommando kör `Get-ServiceLog.ps1` skriptet på fjärrdatorerna med namnet Server01 och Server02.

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a>Få hjälp med skript

Get-Help-cmdlet: en hämtar hjälp avsnitten för skript samt för cmdlets och andra typer av kommandon. Om du vill hämta hjälp avsnittet för ett skript skriver du `Get-Help` följt av Skriptets sökväg och namn. Om skript Sök vägen är i din `Path` miljö variabel kan du utelämna sökvägen.

Om du till exempel vill få hjälp med ServicesLog.ps1 skriptet skriver du:

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a>Så här skriver du ett skript

Ett skript kan innehålla alla giltiga PowerShell-kommandon, inklusive enskilda kommandon, kommandon som använder pipeline-, Function-och kontroll strukturer som if-satser och for-slingor.

Om du vill skriva ett skript öppnar du en ny fil i en text redigerare, skriver kommandon och sparar dem i en fil med ett giltigt fil namn med `.ps1` fil namns tillägget.

Följande exempel är ett enkelt skript som hämtar de tjänster som körs på det aktuella systemet och sparar dem i en loggfil. Logg fil namnet skapas från det aktuella datumet.

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

Om du vill skapa skriptet öppnar du en text redigerare eller en skript redigerare, skriver dessa kommandon och sparar dem i en fil med namnet `ServiceLog.ps1` .

### <a name="parameters-in-scripts"></a>Parametrar i skript

Använd en param-instruktion för att definiera parametrar i ett skript. `Param`Instruktionen måste vara den första instruktionen i ett skript, förutom kommentarer och eventuella `#Require` instruktioner.

Skript parametrar fungerar som funktions parametrar. Parameter värden är tillgängliga för alla kommandon i skriptet. Alla funktioner i funktions parametrar, inklusive parameter-attributet och de namngivna argumenten, är också giltiga i skript.

När skriptet körs skriver skript användare parametrarna efter skript namnet.

I följande exempel visas ett `Test-Remote.ps1` skript som har en **computername** -parameter. Båda skript funktionerna kan komma åt värdet för parametern **computername** .

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

Om du vill köra skriptet skriver du parameter namnet efter skript namnet. Ett exempel:

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

Mer information om param-instruktionen och funktions parametrarna finns i [about_Functions](about_Functions.md) och [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

### <a name="writing-help-for-scripts"></a>Skriver hjälp för skript

Du kan skriva ett hjälp avsnitt för ett skript med någon av följande två metoder:

- Comment-Based hjälp för skript

  Skapa ett hjälp avsnitt genom att använda särskilda nyckelord i kommentarerna. Om du vill skapa en kommenterad hjälp för ett skript måste kommentarerna placeras i början eller slutet av skript filen. Mer information om kommenterad hjälp finns [about_Comment_Based_Help](about_Comment_Based_Help.md).

- XML-Based hjälp för skript

  Skapa ett XML-baserat hjälp avsnitt, till exempel den typ som vanligt vis skapas för cmdletar. XML-baserad hjälp krävs om du översätter hjälp ämnen till flera språk.

Om du vill associera skriptet med det XML-baserade hjälp avsnittet använder du. ExternalHelp hjälp kommentar nyckelord. Mer information om nyckelordet ExternalHelp finns [about_Comment_Based_Help](about_Comment_Based_Help.md). Mer information om XML-baserad hjälp finns i [så här skriver du cmdlet-hjälpen](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).

### <a name="returning-an-exit-value"></a>Returnerar ett slut värde

Som standard returnerar skript inte en avslutnings status när skriptet slutar. Du måste använda `exit` instruktionen för att returnera en avslutnings kod från ett skript. Som standard `exit` returnerar instruktionen `0` . Du kan ange ett numeriskt värde för att returnera en annan avslutnings status. En avslutnings kod som inte är noll signalerar vanligt vis ett haveri.

I Windows är alla siffror mellan `[int]::MinValue` och `[int]::MaxValue` tillåtna.

På UNIX tillåts endast positiva tal mellan `[byte]::MinValue` (0) och `[byte]::MaxValue` (255). Ett negativt tal i intervallet `-1` genom `-255` översätts automatiskt till ett positivt tal genom att lägga till
256. `-2`Transformera till exempel till `254` .

I PowerShell `exit` anger instruktionen värdet för `$LASTEXITCODE` variabeln. I kommando tolken i Windows (cmd.exe) anger avslutnings instruktionen värdet för `%ERRORLEVEL%` miljövariabeln.

Alla argument som inte är numeriska eller utanför det plattformsspecifika intervallet översätts till värdet `0` .

## <a name="script-scope-and-dot-sourcing"></a>Skript omfattning och punkt källa

Varje skript körs i sitt eget omfång. Funktioner, variabler, alias och enheter som skapas i skriptet finns bara i skript omfånget. Du kan inte komma åt dessa objekt eller deras värden i omfånget där skriptet körs.

Om du vill köra ett skript i ett annat omfång kan du ange ett omfång, till exempel globalt eller lokalt, eller så kan du dot-källan till skriptet.

Med funktionen punkt-ursprung kan du köra ett skript i det aktuella omfånget i stället för i skript omfånget. När du kör ett skript som är i punkt form körs kommandona i skriptet som om du hade skrivit dem i kommando tolken. De funktioner, variabler, alias och enheter som skriptet skapar skapas i den omfattning som du arbetar med. När skriptet har körts kan du använda de skapade objekten och komma åt deras värden i sessionen.

Skriv en punkt (.) och ett blank steg före skript Sök vägen för att ange ett skript för punkt källa.

Ett exempel:

```powershell
. C:\scripts\UtilityFunctions.ps1
```

eller

```powershell
. .\UtilityFunctions.ps1
```

När `UtilityFunctions.ps1` skriptet har körts läggs de funktioner och variabler som skriptet skapar till i det aktuella omfånget.

Skriptet skapar till exempel `UtilityFunctions.ps1` `New-Profile` funktionen och `$ProfileName` variabeln.

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

Om du kör `UtilityFunctions.ps1` skriptet i en egen skript omfattning, `New-Profile` finns funktionen och `$ProfileName` variabeln bara när skriptet körs. När skriptet avslutas tas funktionen och variabeln bort, som visas i följande exempel.

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

När du dot-källans skript och kör det skapar skriptet `New-Profile` funktionen och `$ProfileName` variabeln i din-session i ditt omfång. När skriptet har körts kan du använda `New-Profile` funktionen i din session, som du ser i följande exempel.

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

Mer information om omfång finns i about_Scopes.

## <a name="scripts-in-modules"></a>Skript i moduler

En modul är en uppsättning relaterade PowerShell-resurser som kan distribueras som en enhet. Du kan använda moduler för att organisera skript, funktioner och andra resurser. Du kan också använda moduler för att distribuera din kod till andra och hämta kod från betrodda källor.

Du kan inkludera skript i dina moduler, eller så kan du skapa en-skript-modul, som är en modul som helt eller huvudsakligen består av ett skript och stöd resurser. En skript-modul är bara ett skript med fil namns tillägget. psm1.

Mer information om moduler finns i [about_Modules](about_Modules.md).

## <a name="other-script-features"></a>Andra skript funktioner

PowerShell har många användbara funktioner som du kan använda i skript.

- `#Requires` -Du kan använda en `#Requires` instruktion för att förhindra att ett skript körs utan angivna moduler eller snapin-moduler och en angiven version av PowerShell. Mer information finns i about_Requires.

- `$PSCommandPath` -Innehåller den fullständiga sökvägen till och namnet på skriptet som körs. Den här parametern är giltig i alla skript. Den här automatiska variabeln introduceras i PowerShell 3,0.

- `$PSScriptRoot` -Innehåller den katalog som ett skript körs från. I PowerShell 2,0 är den här variabeln endast giltig i script modules ( `.psm1` ).
  Från och med PowerShell 3,0 är det giltigt i alla skript.

- `$MyInvocation` -Den `$MyInvocation` automatiska variabeln innehåller information om det aktuella skriptet, inklusive information om hur det startades eller "anropades". Du kan använda den här variabeln och dess egenskaper för att hämta information om skriptet medan det körs. Till exempel `$MyInvocation` . En ' for Command. Path '-variabel innehåller sökvägen och fil namnet för skriptet. `$MyInvocation`. Raden innehåller kommandot som startade skriptet, inklusive alla parametrar och värden.

  Från och med PowerShell 3,0 `$MyInvocation` har två nya egenskaper som ger information om skriptet som anropade eller anropade det aktuella skriptet. Värdena för dessa egenskaper fylls bara i när anroparen eller anroparen är ett skript.

  - **PSCommandPath** innehåller den fullständiga sökvägen till och namnet på skriptet som anropade eller anropade det aktuella skriptet.

  - **PSScriptRoot** innehåller katalogen i skriptet som anropade eller anropade det aktuella skriptet.

  Till skillnad från `$PSCommandPath` de `$PSScriptRoot` automatiska variablerna, som innehåller information om det aktuella skriptet, innehåller egenskaperna **PSCommandPath** och **PSScriptRoot** för `$MyInvocation` variabeln information om det skript som anropade det aktuella skriptet.

- Data avsnitt – du kan använda `Data` nyckelordet för att separera data från logik i skript. Data avsnitt kan också förenkla lokaliseringen. Mer information finns i [about_Data_Sections](about_Data_Sections.md) och [about_Script_Internationalization](about_Script_Internationalization.md).

- Skript signering – du kan lägga till en digital signatur i ett skript. Beroende på körnings principen kan du använda digitala signaturer för att begränsa körningen av skript som kan innehålla osäkra kommandon. Mer information finns i [about_Execution_Policies](about_Execution_Policies.md) och [about_Signing](about_Signing.md).

## <a name="see-also"></a>Se även

[about_Command_Precedence](about_Command_Precedence.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Functions](about_Functions.md)

[about_Modules](about_Modules.md)

[about_Profiles](about_Profiles.md)

[about_Requires](about_Requires.md)

[about_Run_With_PowerShell](about_Run_With_PowerShell.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Signing](about_Signing.md)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)
