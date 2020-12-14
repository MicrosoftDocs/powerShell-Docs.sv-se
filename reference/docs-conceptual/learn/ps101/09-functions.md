---
title: Functions (Funktioner)
description: Med PowerShell-funktioner kan du skapa verktyg som kan återanvändas i skript.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 18566263f29b97834d78cb5572fa73b58c3a26bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96616020"
---
# <a name="chapter-9---functions"></a>Kapitel 9 – funktioner

Om du skriver PowerShell-liners eller-skript och du ofta behöver ändra dem för olika scenarier, är det en bra chans att det är en bra kandidat att bli inaktive rad i en funktion som kan återanvändas.

När det är möjligt föredrar jag att skriva funktioner eftersom de är mer orienterade. Jag kan placera funktionerna i en-skript-modul, placera modulen i `$env:PSModulePath` och anropa funktionerna utan att behöva placera dem fysiskt där de har sparats. Med PowerShellGet-modulen är det enkelt att dela dessa moduler i en NuGet-lagringsplats. PowerShellGet levereras med PowerShell version 5,0 och senare. Den är tillgänglig som en separat nedladdning för PowerShell version 3,0 och högre.

Du behöver inte göra några förkomplicerade saker. Håll det enkelt och Använd det bästa vanliga sättet för att utföra en uppgift. Undvik alias och positions parametrar i alla koder som du återanvänder. Formatera koden för läsbarhet. Hårdkoda inte värden; Använd parametrar och variabler. Skriv inte onödig kod även om den inte försämra något. Den lägger till onödig komplexitet. Information går bra när du skriver en PowerShell-kod.

## <a name="naming"></a>Namngivning

När du namnger dina funktioner i PowerShell använder du ett [Pascal-Case][] -namn med ett godkänt verb och ett singular substantiv. Jag rekommenderar också att du förkorrigerar substantiv. Till exempel: `<ApprovedVerb>-<Prefix><SingularNoun>`.

I PowerShell finns det en detaljerad lista över godkända verb som kan hämtas genom att köra `Get-Verb` .

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

I föregående exempel har jag sorterat resultaten efter kolumnen **verb** . I kolumnen **grupp** får du en uppfattning om hur dessa verb används. Det är viktigt att välja ett godkänt verb i PowerShell när funktioner läggs till i en modul. Modulen genererar ett varnings meddelande vid inläsnings tillfället om du väljer ett ej godkänt verb. Varnings meddelandet gör att dina funktioner ser ut att vara professionella. Icke-godkända verb begränsar också funktionernanas identifiering.

## <a name="a-simple-function"></a>En enkel funktion

En funktion i PowerShell deklareras med nyckelordet Function följt av funktions namnet och sedan en öppen och avslutande klammer. Den kod som funktionen ska köra finns inuti klammerparenteserna.

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

Funktionen som visas är ett enkelt exempel som returnerar versionen av PowerShell.

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Det finns en utmärkt chans att namn krockar med funktioner som kallas något som `Get-Version` standard kommandon i PowerShell eller kommandon som andra kan skriva. Det är därför jag rekommenderar att du förkorrigerar Substantiv delen av dina funktioner för att förhindra namngivnings konflikter. I följande exempel använder jag prefixet "PS".

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

Förutom namnet är den här funktionen identisk med föregående.

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Även när du förlöser substantiv med något som PS, finns det fortfarande en chans att ha en namn konflikt. Jag brukar prefix My Function substantiv med mina initialer. Utveckla ett standard-och-märke till den.

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

Den här funktionen skiljer sig inte från de tidigare två, förutom att använda ett mer lämpliga-namn för att försöka förhindra namn konflikter med andra PowerShell-kommandon.

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

När du har läst in i minnet kan du se funktioner i **funktionen** PSDrive.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

Om du vill ta bort dessa funktioner från den aktuella sessionen måste du ta bort dem från **funktionen** PSDrive eller stänga och öppna PowerShell igen.

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

Kontrol lera att funktionerna verkligen har tagits bort.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

Om funktionerna lästes in som en del av en modul kan modulen tas bort från minnet för att ta bort dem.

```powershell
Remove-Module -Name <ModuleName>
```

`Remove-Module`Cmdleten tar bort moduler från minnet i den aktuella PowerShell-sessionen, men den tas inte bort från systemet eller från disken.

## <a name="parameters"></a>Parameters (Parametrar)

Tilldela inte värden statiskt! Använd parametrar och variabler. När det gäller att namnge parametrarna använder du samma namn som standard-cmdletarna för dina parameter namn när det är möjligt.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Varför använde jag **computername** och inte **dator**, **Server namn** eller **värd** för mitt parameter namn? Det beror på att jag ville ha funktionen standard som standard-cmdletar.

Jag skapar en funktion för att fråga alla kommandon i ett system och returnera antalet som har vissa parameter namn.

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

Som du ser i resultaten som visas nedan, kan du 39 kommandon som har en **computername** -parameter. Det finns inga cmdletar som har parametrar som **dator**, **servername**, **Host** eller **Machine**.

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

Jag rekommenderar också att du använder samma Skift läge för parameter namn som standard-cmdletar. Använd `ComputerName` , inte `computername` . Detta gör att funktionerna ser ut och fungerar som standard-cmdletar. Personer som redan är bekanta med PowerShell känner sig till höger hemma.

Med `param` instruktionen kan du definiera en eller flera parametrar. Parameter definitionerna avgränsas med kommatecken ( `,` ). Mer information finns i [about_Functions_Advanced_Parameters][].

## <a name="advanced-functions"></a>Avancerade funktioner

Det är enkelt att aktivera en funktion i PowerShell i en avancerad funktion. En av skillnaderna mellan en funktion och en avancerad funktion är att avancerade funktioner har ett antal vanliga parametrar som läggs till i funktionen automatiskt. Dessa vanliga parametrar innehåller parametrar som **utförlig** och **fel sökning**.

Jag börjar med `Test-MrParameter` funktionen som användes i föregående avsnitt.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Vad jag vill att du ska märka är att `Test-MrParameter` funktionen inte har några gemensamma parametrar. Det finns ett par olika sätt att se de gemensamma parametrarna. Det ena är att visa syntaxen med hjälp av `Get-Command` .

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

En annan är att öka detalj nivån i parametrarna med `Get-Command` .

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

Lägg till `CmdletBinding` för att aktivera funktionen i en avancerad funktion.

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

När `CmdletBinding` du lägger till läggs de gemensamma parametrarna automatiskt till. `CmdletBinding` kräver ett `param` block, men `param` blocket kan vara tomt.

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

Gå nedåt i parametrarna med `Get-Command` visar de faktiska parameter namnen inklusive de vanliga.

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess` lägger till parametrarna **whatIf** och **Confirm** . De behövs bara för kommandon som gör ändringar.

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Observera att det nu finns **whatIf** och **Bekräfta** parametrarna.

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Du kan också använda `Get-Command` för att returnera en lista över de faktiska parameter namnen, inklusive de som är gemensamma tillsammans med whatIf och bekräfta.

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>Parameter validering

Verifiera inaktivitet tidigt. Varför kan din kod fortsätta på en sökväg när det inte går att köra utan giltiga indatamängdar?

Skriv alltid variablerna som används för parametrarna (ange en datatyp).

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

I det föregående exemplet har jag angett **sträng** som datatyp för parametern **computername** . Detta gör att det bara tillåter att ett enda dator namn anges. Om fler än ett dator namn anges via en kommaavgränsad lista, genereras ett fel.

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

Problemet med den aktuella definitionen är att det är giltigt att utelämna värdet för parametern **computername** , men ett värde krävs för att funktionen ska kunna slutföras. Det är där `Mandatory` attributet parameter är praktiskt.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

Syntaxen som används i föregående exempel är PowerShell version 3,0 och högre kompatibel.
`[Parameter(Mandatory=$true)]` kan anges i stället för att göra funktionen kompatibel med PowerShell version 2,0 och högre. Nu när **computername** krävs, om ett sådant inte har angetts, kommer funktionen att uppmanas att ange en.

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

Om du vill tillåta fler än ett värde för parametern **computername** använder du **sträng** data typen men lägger till öppna och stängda hakparenteser till data typen för att tillåta en sträng mat ris.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

Du kanske vill ange ett standardvärde för parametern **computername** om ingen sådan har angetts.
Problemet är att standardvärden inte kan användas med obligatoriska parametrar. I stället måste du använda `ValidateNotNullOrEmpty` attributet parameter validering med ett standardvärde.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

Försök att inte använda statiska värden även när du anger ett standardvärde. I föregående exempel `$env:COMPUTERNAME` används som standardvärde, som automatiskt översätts till det lokala dator namnet om ett värde inte anges.

## <a name="verbose-output"></a>Utförlig utdata

Även om kommentarer är användbara, särskilt om du skriver en komplicerad kod, visas de aldrig av användarna om de inte tittar på själva koden.

Funktionen som visas i följande exempel har en infogad kommentar i `foreach` slingan. Även om den här kommentaren kanske inte är så svår att hitta, Föreställ dig om funktionen innehöll hundratals kodrader.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

Ett bättre alternativ är att använda `Write-Verbose` i stället för infogade kommentarer.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

När funktionen anropas utan **verbose** -parametern visas inte utförliga utdata.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

När den anropas med **verbose** -parametern visas utförlig utdata.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>Pipeline-inmatade

Om du vill att din funktion ska godkänna pipeline-ininformation krävs ytterligare kod. Som tidigare nämnts i den här boken kan kommandon acceptera pipeline-inmatade **värde** (efter typ) eller **efter egenskaps namn**. Du kan skriva funktioner precis som de inbyggda kommandona så att de accepterar antingen en eller båda av de här typerna av inmatade.

Om du vill acceptera pipeline-inmatat **värde** anger du `ValueFromPipeline` parameterns parameter för den specifika parametern. Tänk på att du bara kan acceptera pipeline-indata **med värde** från en av varje datatyp. Om du t. ex. har två parametrar som accepterar inmatade strängar, kan bara en av dem acceptera pipeline-inmatade **värden** , eftersom om du har angett den för båda sträng parametrarna, vet inte pipeline-indatatypen vilken av dem som ska bindas till. Det här är ett annat orsak till varför jag anropar den här typen av pipeline-indatatyper _efter typ_ i stället för **efter värde**.

Pipeline-InInformationen kommer att finnas i ett objekt i taget på samma sätt som objekt hanteras i en `foreach` slinga.
Ett `process` block krävs minst för att bearbeta vart och ett av dessa objekt om du accepterar en matris som inmatad. Om du bara accepterar ett enda värde som indata är ett `process` block inte nödvändigt, men jag rekommenderar att du ändå anger det för konsekvens.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

Att acceptera pipeline-indata **efter egenskaps namn** är liknande förutom att det har angetts med `ValueFromPipelineByPropertyName` attributet parameter och det kan anges för valfritt antal parametrar oavsett datatyp. Nyckeln är att utdata från kommandot som skickas i måste ha ett egenskaps namn som matchar namnet på parametern eller ett parameter-alias för funktionen.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

`BEGIN` och `END` block är valfria. `BEGIN` anges före `PROCESS` blocket och används för att utföra alla inledande arbeten innan de objekt som tas emot från pipelinen. Detta är viktigt att förstå. Det går inte att komma åt värden som är skickas i `BEGIN` blocket. `END`Blocket anges efter `PROCESS` blocket och används för rensning när alla objekt som skickas har bearbetats.

## <a name="error-handling"></a>Felhantering

Funktionen som visas i följande exempel genererar ett ohanterat undantag när det inte går att kontakta en dator.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

Det finns ett par olika sätt att hantera fel i PowerShell. `Try/Catch` är det mer modern sättet att hantera fel.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Även om funktionen som visas i föregående exempel använder fel hantering, genererar den också ett ohanterat undantag eftersom kommandot inte genererar något avslutande fel. Detta är också viktigt att förstå. Det är bara att avsluta fel som har påträffats. Ange parametern **ErrorAction** med **stopp** som värde för att inaktivera ett icke-avslutande fel i en avslutning.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Ändra inte den globala `$ErrorActionPreference` variabeln om det inte är absolut nödvändigt. Om du använder något som .NET direkt från din PowerShell-funktion kan du inte ange **ErrorAction** i själva kommandot. I så fall kan du behöva ändra den globala `$ErrorActionPreference` variabeln, men om du ändrar den, ändrar du den direkt efter att du har försökt med kommandot.

## <a name="comment-based-help"></a>Comment-Based hjälp

Det anses vara en bra idé att lägga till kommenterad hjälp till dina funktioner så att de personer som du delar dem med vet hur de ska användas.

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

När du lägger till en kommenterad hjälp till dina funktioner kan du hämta hjälpen för dem precis som de inbyggda standard kommandona.

All syntax för att skriva en funktion i PowerShell kan verka överbelastad särskilt för någon som precis har börjat. Ofta om jag inte kan komma ihåg syntaxen för något, öppnar jag en andra kopia av ISE på en separat övervakare och visar kodfragmentet "cmdlet (avancerad funktion)-Complete" när du skriver in koden för min funktion. Du kan komma åt kod avsnitt i PowerShell ISE med tangentkombinationen <kbd>CTRL</kbd> + <kbd>J</kbd> .

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig grunderna i att skriva funktioner i PowerShell som innehåller information om hur du aktiverar en funktion i en avancerad funktion och några av de viktiga element som du bör tänka på när du skriver PowerShell-funktioner som parameter validering, utförlig utdata, pipeline-indata, fel hantering och kommenterad hjälp.

## <a name="review"></a>Genomgång

1. Hur får du en lista över godkända verb i PowerShell?
1. Hur aktiverar du en PowerShell-funktion i en avancerad funktion?
1. När ska **whatIf** -och **Confirm** -parametrar läggas till i dina PowerShell-funktioner?
1. Hur gör du ett icke-avslutande fel i ett avslutande meddelande?
1. Varför ska du lägga till kommenterad hjälp till dina funktioner?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [Video: PowerShell-Toolmaking med avancerade funktioner och skript-moduler][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Video: PowerShell-Toolmaking med avancerade funktioner och skript-moduler]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Pascal-fall]: /dotnet/standard/design-guidelines/capitalization-conventions
