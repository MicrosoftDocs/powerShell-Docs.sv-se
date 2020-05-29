---
title: Allt du ville veta om undantag
description: Fel hanteringen är bara en del av livs cykeln när den kommer att skriva kod.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fd3ddacbf14d1faeee98682697161f86c6ff0c72
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149882"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>Allt du ville veta om undantag

Fel hanteringen är bara en del av livs cykeln när den kommer att skriva kod. Vi kan ofta kontrol lera och validera villkor för förväntat beteende. När det oväntade inträffar aktiverar vi undantags hantering. Du kan enkelt hantera undantag som skapats av andra personers kod eller så kan du skapa egna undantag för andra att hantera.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="basic-terminology"></a>Grundläggande terminologi

Vi måste behandla några grundläggande villkor innan vi hoppar till den här.

### <a name="exception"></a>Undantag

Ett undantag är som en händelse som skapas när normal fel hantering inte kan hantera problemet.
Att försöka dividera ett tal med noll eller slut på minne är några exempel på något som skapar ett undantag. Ibland kan författaren till den kod som du använder skapa undantag för vissa problem när de inträffar.

### <a name="throw-and-catch"></a>Throw och catch

När ett undantag inträffar säger vi att ett undantag uppstår. För att hantera ett utlöst undantag måste du fånga det. Om ett undantags fel uppstår och det inte fångas av något, slutar skriptet att köras.

### <a name="the-call-stack"></a>Anrops stacken

Anrops stacken är en lista över funktioner som har anropat varandra. När en funktion anropas läggs den till i stacken eller överst i listan. När funktionen avslutas eller returneras tas den bort från stacken.

När ett undantag genereras, kontrol leras anrops stacken för att en undantags hanterare ska kunna fånga den.

### <a name="terminating-and-non-terminating-errors"></a>Avbryta och icke-avslutande fel

Ett undantag är vanligt vis ett avslutande fel. Ett utlöst undantag har antingen fångats upp eller avslutar den aktuella körningen. Som standard genereras ett icke-avslutande fel av `Write-Error` och ett fel läggs till i utdataströmmen utan att ett undantag utlöses.

Jag pekar `Write-Error` på detta, eftersom andra icke-avslutande fel inte utlöser `catch` .

### <a name="swallowing-an-exception"></a>Förtäring av undantag

Detta är när du fångar ett fel bara för att ignorera det. Gör detta med försiktighet eftersom det kan göra fel söknings problem mycket svårt.

## <a name="basic-command-syntax"></a>Basic-kommandosyntax

Här är en snabb översikt över den grundläggande syntaxen för undantags hantering som används i PowerShell.

### <a name="throw"></a>Genereras

För att skapa en egen undantags händelse genererar vi ett undantag med `throw` nyckelordet.

```powershell
function Do-Something
{
    throw "Bad thing happened"
}
```

Detta skapar ett körnings undantag som är ett avbrotts fel. Den hanteras av en `catch` i en anropande funktion eller avslutar skriptet med ett meddelande som detta.

```powershell
PS> Do-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Skriv-Error-ErrorAction-stopp

Jag nämnde att det `Write-Error` inte uppstår något avslutande fel som standard. Om du anger `-ErrorAction Stop` `Write-Error` genererar ett avslutande fel som kan hanteras med en `catch` .

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

Tack för att du Pettersson dagligen för att påminna om hur du använder `-ErrorAction Stop` det här sättet.

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet-ErrorAction-stopp

Om du anger `-ErrorAction Stop` en avancerad funktion eller cmdlet, aktiverar den alla `Write-Error` instruktioner för att avsluta fel som slutar att köras eller som kan hanteras av en `catch` .

```powershell
Do-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Prova/fånga

Hur undantags hanteringen fungerar i PowerShell (och många andra språk) är att du först är `try` en del av koden och om den genererar ett fel, så kan du `catch` . Här är ett snabbt exempel.

```powershell
try
{
    Do-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Do-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

`catch`Skriptet körs bara om det finns ett avslutande fel. Om `try` körningen är korrekt hoppar den över `catch` .

### <a name="tryfinally"></a>Try/finally

Ibland behöver du inte hantera ett fel men ändå behöver en kod för att köras om ett undantag inträffar eller inte. Ett `finally` skript gör exakt det.

Ta en titt på det här exemplet:

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

När du öppnar eller ansluter till en resurs ska du stänga den. Om `ExecuteNonQuery()` ett undantag utlöses stängs inte anslutningen. Här är samma kod inuti ett `try/finally` block.

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

I det här exemplet stängs anslutningen om det uppstår ett fel. Den stängs också om det inte finns något fel. `finally`Skriptet körs varje gång.

Eftersom du inte fångar undantaget, kommer det fortfarande att spridas till anrops stacken.

### <a name="trycatchfinally"></a>Try/catch/finally

Den är perfekt giltig att användas `catch` och `finally` tillsammans. I de flesta fall kommer du att använda en av de andra, men du kan hitta scenarier där du använder båda.

## <a name="psitem"></a>$PSItem

Nu när vi har lärt dig grunderna, kan vi göra en aning djupare.

Inuti `catch` blocket finns en automatisk variabel ( `$PSItem` eller `$_` ) av typen `ErrorRecord` som innehåller information om undantaget. Här är en snabb översikt över några av nyckel egenskaperna.

I de här exemplen använde jag en ogiltig sökväg i `ReadAllText` för att generera detta undantag.

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem. ToString ()

Detta ger dig det rensade meddelande som ska användas vid loggning och allmänna utdata. `ToString()`anropas automatiskt om `$PSItem` är placerad inuti en sträng.

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem. InvocationInfo

Den här egenskapen innehåller ytterligare information som samlas in av PowerShell om funktionen eller skriptet där undantaget uppstod. Här är `InvocationInfo` från det exempel-undantag som jag skapade.

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

Den viktiga informationen här visar `ScriptName` , `Line` koden och `ScriptLineNumber` var anropet startades.

### <a name="psitemscriptstacktrace"></a>$PSItem. ScriptStackTrace

Den här egenskapen visar ordningen på funktions anrop som har fått till gång till koden där undantaget genererades.

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Do-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

Jag gör bara anrop till funktioner i samma skript, men detta spårar anropen om flera skript var involverade.

### <a name="psitemexception"></a>$PSItem. Exception

Detta är det faktiska undantaget som utlöstes.

#### <a name="psitemexceptionmessage"></a>$PSItem. Exception. Message

Detta är det allmänna meddelandet som beskriver undantaget och är en korrekt start punkt vid fel sökning. De flesta undantag har ett standard meddelande men kan också ställas in på något anpassat när undantaget genereras.

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

Detta är även det meddelande som returneras vid anrop `$PSItem.ToString()` om det inte fanns någon uppsättning på `ErrorRecord` .

#### <a name="psitemexceptioninnerexception"></a>$PSItem. Exception. InnerException

Undantag kan innehålla inre undantag. Detta är ofta fallet när den kod som du anropar fångar ett undantag och genererar ett annat undantag. Det ursprungliga undantaget placeras inuti det nya undantaget.

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

Jag går tillbaka senare när jag pratar om undantag.

#### <a name="psitemexceptionstacktrace"></a>$PSItem. Exception. StackTrace

Detta är `StackTrace` för undantaget. Jag visade en `ScriptStackTrace` ovan, men det här är ett för anrop till hanterad kod.

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

Du får bara den här stack spårningen när händelsen genereras från hanterad kod. Jag anropar en .NET Framework-funktion direkt så att vi kan se det i det här exemplet. Vanligt vis när du tittar på en stack spårning är du säker på var koden stoppas och system anropen börjar.

## <a name="working-with-exceptions"></a>Arbeta med undantag

Det finns fler undantag än grundläggande syntax och undantags egenskaper.

### <a name="catching-typed-exceptions"></a>Fångst av skrivna undantag

Du kan vara selektiv med de undantag som du har fångat. Undantag har en typ och du kan ange vilken typ av undantag du vill fånga.

```powershell
try
{
    Do-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

Undantags typen kontrol leras för varje `catch` block tills ett hittas som matchar ditt undantag.
Det är viktigt att du inser att undantag kan ärva från andra undantag. I exemplet ovan `FileNotFoundException` ärver från `IOException` . Så om du `IOException` först var det skulle den anropas i stället. Endast ett catch-block anropas även om det finns flera matchningar.

Om vi hade ett `System.IO.PathTooLongException` , `IOException` skulle det matcha, men om vi hade ett så skulle vi inte `InsufficientMemoryException` fånga det och det skulle spridas i stacken.

### <a name="catch-multiple-types-at-once"></a>Fånga flera typer samtidigt

Det är möjligt att fånga flera undantags typer med samma `catch` instruktion.

```powershell
try
{
    Do-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

Tack för att du `/u/Sheppard_Ra` föreslår det här tillägget.

### <a name="throwing-typed-exceptions"></a>Utlös ande undantag

Du kan kasta skrivna undantag i PowerShell. I stället för att anropa `throw` med en sträng:

```powershell
throw "Could not find: $path"
```

Använd en undantags Accelerator så här:

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

Men du måste ange ett meddelande när du gör det på det sättet.

Du kan också skapa en ny instans av ett undantag som ska genereras. Meddelandet är valfritt när du gör detta eftersom systemet innehåller standard meddelanden för alla inbyggda undantag.

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

Om du inte använder PowerShell 5,0 eller senare måste du använda den äldre `New-Object` metoden.

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

Genom att använda ett inskrivet undantag kan du (eller andra) fånga undantagen enligt den typ som anges i föregående avsnitt.

#### <a name="write-error--exception"></a>Skriv-Error-Exception

Vi kan lägga till de här skrivna undantagen i `Write-Error` och vi kan fortfarande `catch` fel efter undantags typ. Använd `Write-Error` som i följande exempel:

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

Sedan kan vi fånga den så här:

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>Den stora listan med .NET-undantag

Jag har kompilerat en huvud lista med hjälp av [Reddit/r/PowerShell-communityn][] som innehåller hundratals .net-undantag för att komplettera det här inlägget.

- [Den stora listan med .NET-undantag][]

Jag börjar med att söka i listan efter undantag som ser ut som att de passar bra för min situation. Du bör försöka använda undantag i bas `System` namn området.

### <a name="exceptions-are-objects"></a>Undantag är objekt

Om du börjar använda flera skrivna undantag, kom ihåg att de är objekt. Olika undantag har olika konstruktorer och egenskaper. Om vi tittar på [FileNotFoundException][] -dokumentationen för `System.IO.FileNotFoundException` ser vi att vi kan skicka i ett meddelande och en fil Sök väg.

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

Och har en `FileName` egenskap som visar fil Sök vägen.

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

Du bör läsa [.net-dokumentationen][] för andra konstruktörer och objekt egenskaper.

### <a name="re-throwing-an-exception"></a>Återskapar ett undantag

Om allt du kommer att göra i `catch` blockeringen är `throw` samma undantag `catch` . Du bör bara ha `catch` ett undantag som du planerar att hantera eller utföra en åtgärd när det händer.

Det finns tillfällen när du vill utföra en åtgärd i ett undantag, men som återskapar undantaget så att något går ut i förhållande till det. Vi kan skriva ett meddelande eller logga problemet nära den plats där vi upptäcker det men hantera problemet ytterligare i stacken.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

Vi är tillräckligt intressant och kan anropa inifrån `throw` `catch` och återskapar det aktuella undantaget.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

Vi vill återställa undantaget för att bevara den ursprungliga körnings informationen som käll skript och rad nummer. Om vi genererar ett nytt undantag i det här läget, döljs var undantaget startades.

#### <a name="re-throwing-a-new-exception"></a>Återskapa ett nytt undantag

Om du fångar ett undantag, men vill kasta ett annat, ska du kapsla det ursprungliga undantaget inuti det nya. På så sätt kan någon av stackarna få till gång till den som `$PSItem.Exception.InnerException` .

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet. ThrowTerminatingError ()

En sak som jag inte vill använda `throw` för obehandlade undantag är att fel meddelandet pekar på `throw` instruktionen och indikerar att raden är den plats där problemet finns.

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```


Om du får ett fel meddelande om att mitt skript är brutet, eftersom jag har anropat `throw` på rad 31 är ett dåligt meddelande för användare av ditt skript att se. Det ser inte ut som om det är något användbart.

Dhami påpekade att jag kan använda `ThrowTerminatingError()` för att åtgärda detta.

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

Om vi antar att `ThrowTerminatingError()` anropades inuti en funktion som kallas `Get-Resource` , är det här felet som vi skulle se.

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

Ser du hur det pekar på `Get-Resource` funktionen som orsaken till problemet? Detta talar om för användaren något användbart.

Eftersom `$PSItem` är en `ErrorRecord` kan vi även använda `ThrowTerminatingError` det här sättet för att utlösa igen.

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

Detta ändrar källan till felet till cmdleten och döljer de interna funktionerna från användarna av din cmdlet.

## <a name="try-can-create-terminating-errors"></a>Försök att skapa avslutande fel

Kirks Munro pekar ut om att vissa undantag endast avslutar fel när de körs inuti ett `try/catch` block. Här är exemplet han fick mig som genererade ett divisions fel med körnings undantag.

```powershell
function Do-Something { 1/(1-1) }
```

Sedan anropar du det som det här för att se hur det genererar felet och fortsätter att skriva ut meddelandet.

```powershell
&{ Do-Something; Write-Output "We did it. Send Email" }
```

Men genom att placera samma kod inuti en `try/catch` , ser vi något annat.

```powershell
try
{
    &{ Do-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```


Vi ser felet blir ett avbrotts fel och ger inte ut det första meddelandet. Vad jag inte tycker om det här är att du kan ha den här koden i en funktion och den fungerar annorlunda om någon använder en `try/catch` .

Jag har inte stött på problem med det här, men det är ett hörn fall som är medvetet om.

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet. ThrowTerminatingError () inuti try/catch

En Nuance av `$PSCmdlet.ThrowTerminatingError()` är att den skapar ett avbrotts fel i din cmdlet, men det går in i ett icke-avslutande fel när cmdleten har lämnat din cmdlet. Detta gör att den som anropar en funktion kan hantera felet. De kan ändra tillbaka till ett avslutande fel genom att använda `-ErrorAction Stop` eller anropa det inifrån en `try{...}catch{...}` .

### <a name="public-function-templates"></a>Mallar för offentliga funktioner

Ett sista sätt att använda min konversation med Kirks Munro var att han var `try{...}catch{...}` runt varje `begin` , `process` och `end` blockerar i alla sina avancerade funktioner. I dessa generiska catch-block kan han som en enda linje `$PSCmdlet.ThrowTerminatingError($PSitem)` hantera alla undantag som lämnar sina uppgifter.

```powershell
function Do-Something
{
    [cmdletbinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSitem)
        }
    }
}
```

Eftersom allt är i en `try` instruktion inom sina funktioner fungerar allt konsekvent. Detta ger också rena fel till slutanvändaren som döljer den interna koden från det genererade felet.

## <a name="trap"></a>Väll

Jag fokuserar på `try/catch` aspekten av undantag. Men det finns en äldre funktion jag måste säga innan vi kan packa upp den här.

En `trap` placeras i ett skript eller en funktion för att fånga alla undantag som inträffar i det aktuella omfånget. När ett undantag inträffar fortsätter koden i att `trap` köras och sedan fortsätter den normala koden. Om flera undantag inträffar anropas trapen över och över.

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

Jag har aldrig tillfrågat den här metoden, men jag kan se värdet i administratörs-eller kontrollantens skript som loggar alla eventuella undantag och fortfarande fortsätta att köra.

## <a name="closing-remarks"></a>Avslutande anmärkningar

Genom att lägga till korrekt undantags hantering i dina skript kan du inte bara göra dem mer stabila, utan även göra det enklare för dig att felsöka undantagen.

Jag har ägnat mycket tid åt `throw` att prata eftersom det är ett Core-koncept när vi pratar om undantags hantering. PowerShell gav också oss `Write-Error` som hanterar alla situationer där du skulle använda `throw` . Tänk på att du inte behöver använda `throw` det när du har läst det här.

Nu när jag har tagit tid att skriva om undantags hantering i den här informationen ska jag växla över till `Write-Error -Stop` att använda för att generera fel i koden. Jag ska också ta Kirks-råd och göra `ThrowTerminatingError` min goto undantags hanterare för varje funktion.

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[ursprunglig version]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Reddit/r/PowerShell-community]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[Den stora listan med .NET-undantag]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: https://docs.microsoft.com/dotnet/api/System.IO.FileNotFoundException
[.NET-dokumentation]: https://docs.microsoft.com/dotnet/api