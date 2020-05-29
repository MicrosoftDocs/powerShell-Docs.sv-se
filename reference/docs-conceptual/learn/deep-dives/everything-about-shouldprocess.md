---
title: Allt du ville veta om ShouldProcess
description: ShouldProcess är en viktig funktion som ofta är påslagen. Parametrarna WhatIf och Confirm gör det enkelt att lägga till dina funktioner.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1d9110302a191b90bd11bdf742f77704a8c9d6f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149840"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>Allt du ville veta om ShouldProcess

PowerShell-funktioner har flera funktioner som avsevärt förbättrar hur användare interagerar med dem.
En viktig funktion som ofta förbises är `-WhatIf` och `-Confirm` stöder och det är enkelt att lägga till funktioner. I den här artikeln går vi djupare till hur du implementerar den här funktionen.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

Det här är en enkel funktion som du kan aktivera i dina funktioner för att tillhandahålla ett säkerhets nät för de användare som behöver det. Det finns inget scarier än att köra ett kommando som du vet kan vara farligt för första gången. Alternativet att köra det med `-WhatIf` kan göra stor skillnad.

## <a name="commonparameters"></a>CommonParameters

Innan vi tittar på implementering av de här [vanliga parametrarna][]vill jag ta en titt på hur de används.

## <a name="using--whatif"></a>Använda-WhatIf

När ett kommando stöder `-WhatIf` parametern kan du se hur kommandot skulle ha gjort i stället för att göra ändringar. Det är ett bra sätt att testa effekten av ett kommando, särskilt innan du gör något destruktivt.

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Om kommandot implementeras korrekt `ShouldProcess` bör du Visa alla ändringar som har gjorts. Här är ett exempel som använder jokertecken för att ta bort flera filer.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>Använder-Confirm

Kommandon som stöder stöder `-WhatIf` också `-Confirm` . Det ger dig en chans att bekräfta en åtgärd innan du utför den.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

I det här fallet har du flera alternativ som gör att du kan fortsätta, hoppa över en ändring eller stoppa skriptet. I hjälp avsnittet beskrivs var och en av dessa alternativ som detta.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>Lokalisering

Den här prompten lokaliseras i PowerShell så att språket ändras baserat på operativ systemets språk. Detta är en mer precis som PowerShell hanterar för dig.

### <a name="switch-parameters"></a>Växla parametrar

Låt oss ta en stund att titta på olika sätt att skicka ett värde till en switch-parameter. Det främsta skälet till att jag kallar det här är att du ofta vill skicka parameter värden till de funktioner som du anropar.

Den första metoden är en speciell parameter-syntax som kan användas för alla parametrar, men du kan se den som används för växlings parametrar. Du anger ett kolon för att bifoga ett värde till parametern.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

Du kan göra samma sak med en variabel.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

Den andra metoden är att använda en hash-hash för att splat värdet.

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

Om du är nybörjare på hash eller ihopbuntning har jag en annan artikel som täcker [allt du ville veta om hash][].

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

Det första steget för att aktivera `-WhatIf` och `-Confirm` stödja är att ange `SupportsShouldProcess` i `CmdletBinding` din funktion.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

Genom `SupportsShouldProcess` att ange på det här sättet kan vi nu anropa vår funktion med `-WhatIf` (eller `-Confirm` ).

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Observera att jag inte har skapat någon parameter med namnet `-WhatIf` . `SupportsShouldProcess`Om du anger det skapas det automatiskt för oss. När vi anger `-WhatIf` parametern på `Test-ShouldProcess` , är vissa saker som vi kallar också `-WhatIf` bearbetning.

### <a name="trust-but-verify"></a>Förtroende men verifiera

Det finns viss risk för att lita på att allt du anropar ärver `-WhatIf` värden. I resten av exemplen kommer jag att anta att det inte fungerar och är mycket explicit när du gör anrop till andra kommandon. Jag rekommenderar att du gör samma sak.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

Jag kommer att gå tillbaka till olika delarna senare när du har en bättre förståelse för alla delar i spelet.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet. ShouldProcess

Metoden som gör att du kan implementera `SupportsShouldProcess` är `$PSCmdlet.ShouldProcess` . Du `$PSCmdlet.ShouldProcess(...)` kan ringa för att se om du bör bearbeta en del logik och PowerShell för att ta hand om resten. Vi börjar med ett exempel:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

Anropet `$PSCmdlet.ShouldProcess($file.name)` för att kontrol lera `-WhatIf` (och `-Confirm` parametern) hanterar sedan det därefter. `-WhatIf`Orsakerna `ShouldProcess` till en beskrivning av ändringen och retur `$false` :

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

Ett anrop med `-Confirm` pausar skriptet och användaren uppmanas att välja att fortsätta. Den returneras `$true` om användaren har valts `Y` .

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

En fantastisk funktion i `$PSCmdlet.ShouldProcess` är att den dubbleras som utförliga utdata. Jag är beroende av detta ofta när de implementeras `ShouldProcess` .

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>Överlagringar

Det finns några olika överlagringar för `$PSCmdlet.ShouldProcess` med olika parametrar för att anpassa meddelande tjänsten. Vi såg redan den första i exemplet ovan. Låt oss ta en närmare titt på den.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

Detta ger utdata som innehåller både funktions namnet och målet (värdet för parametern).

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

Om du anger en andra parameter som åtgärd används åtgärd svärdet i stället för funktions namnet i meddelandet.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

Nästa alternativ är att ange tre parametrar för att helt anpassa meddelandet. När tre parametrar används, är det första meddelandet. De andra två parametrarna används fortfarande i `-Confirm` meddelandets utdata.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>Snabb parameter referens

Om du bara kommer hit för att ta reda på vilka parametrar du ska använda, är det en snabb referens som visar hur parametrarna ändrar meddelandet i olika `-WhatIf` scenarier.

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

Jag brukar använda den med två parametrar.

### <a name="shouldprocessreason"></a>ShouldProcessReason

Vi har en fjärde överlagring som är mer avancerad än de andra. Det gör att du kan få orsaken till att du `ShouldProcess` har körts. Jag lägger bara till detta för fullständighet eftersom vi bara kan kontrol lera om `$WhatIf` är `$true` i stället.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

Vi måste skicka `$reason` variabeln till den fjärde parametern som en referens variabel med `[ref]` . `ShouldProcess`fylls `$reason` med värdet `None` eller `WhatIf` . Jag säger inte att detta var användbart och jag har inte haft någon anledning att någonsin använda det.

### <a name="where-to-place-it"></a>Var du ska placera den

Du använder `ShouldProcess` för att göra skripten säkrare. Så du använder det när dina skript gör ändringar. Jag vill placera `$PSCmdlet.ShouldProcess` anropet så nära ändringen som möjligt.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

Om jag bearbetar en samling objekt anropas den för varje objekt. Anropet placeras i den förgrunds slingan.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

Anledningen till varför jag `ShouldProcess` är nära ändringen, är att jag vill att så mycket kod som helst ska köras när `-WhatIf` har angetts. Jag vill att installationen och verifieringen ska köras om möjligt så att användaren kan se dessa fel.

Jag vill också använda detta i mina pester-test som validerar mina projekt. Om jag har en del av logiken som är svår att modellera i pester kan jag ofta figursätta den i `ShouldProcess` och anropa den med `-WhatIf` i mina tester. Det är bättre att testa en del av din kod än någon.

### <a name="whatifpreference"></a>$WhatIfPreference

Den första preferens variabeln som vi har är `$WhatIfPreference` . Detta är `$false` som standard. Om du ställer in den på så `$true` körs funktionen som om du har angett `-WhatIf` . Om du ställer in detta i din session utför alla kommandon `-WhatIf` körning.

När du anropar en funktion med `-WhatIf` är värdet för `$WhatIfPreference` inställt på `$true` inom omfånget för din funktion.

## <a name="confirmimpact"></a>ConfirmImpact

De flesta av mina exempel är för, `-WhatIf` men allt så att allt så långt kan också användas för `-Confirm` att uppmana användaren att göra det. Du kan ställa in `ConfirmImpact` funktionen på hög och uppmanas användaren som om den anropades med `-Confirm` .

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Detta anrop till `Test-ShouldProcess` utför åtgärden på `-Confirm` grund av `High` påverkan.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

Det uppenbara problemet är att nu är det svårare att använda i andra skript utan att användaren tillfrågas. I det här fallet kan vi skicka en `$false` till `-Confirm` för att förhindra prompten.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

Jag lär dig hur du lägger till `-Force` stöd i ett senare avsnitt.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference`är en automatisk variabel som styr när `ConfirmImpact` du uppmanas att bekräfta körning. Här följer de möjliga värdena för både `$ConfirmPreference` och `ConfirmImpact` .

- `High`
- `Medium`
- `Low`
- `None`

Med dessa värden kan du ange olika effekt nivåer för varje funktion. Om du har `$ConfirmPreference` angett ett värde som är högre än `ConfirmImpact` , uppmanas du inte att bekräfta körningen.

Som standard `$ConfirmPreference` är anges till `High` och `ConfirmImpact` `Medium` . Om du vill att din funktion automatiskt ska ställa in användaren, ställer du in `ConfirmImpact` på `High` . Annars ställer du in den på `Medium` om den är förstörande och används `Low` om kommandot alltid är säkert körs i produktion. Om du ställer in den som `none` fråga visas den inte även om `-Confirm` har angetts (men det ger fortfarande `-WhatIf` support).

När du anropar en funktion med `-Confirm` är värdet för `$ConfirmPreference` inställt på `Low` inom omfånget för din funktion.

### <a name="suppressing-nested-confirm-prompts"></a>Ignorera inkapslade bekräftelse meddelanden

De `$ConfirmPreference` kan hämtas av funktioner som du anropar. Detta kan skapa scenarier där du lägger till en bekräfta-prompt och funktionen som du anropar även efterfrågar användaren.

Vad jag brukar göra är att ange `-Confirm:$false` på de kommandon som jag anropar när jag redan har hanterat frågan.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

Detta gör att vi återgår till en tidigare varning: det finns olika delarna när `-WhatIf` inte skickas till en funktion och skickas `-Confirm` till en funktion. Jag lovar att jag kommer tillbaka till detta senare.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet. ShouldContinue

Om du behöver mer kontroll än `ShouldProcess` tillhandahåller kan du utlösa prompten direkt med `ShouldContinue` . `ShouldContinue`ignorerar,,, och, om det `$ConfirmPreference` `ConfirmImpact` `-Confirm` `$WhatIfPreference` `-WhatIf` sker varje gång det körs.

Det är enkelt att förväxla `ShouldProcess` och `ShouldContinue` . Jag brukar komma ihåg att använda `ShouldProcess` eftersom parametern anropas `SupportsShouldProcess` i `CmdletBinding` .
Du bör använda `ShouldProcess` i nästan alla scenarier. Det är därför jag täckte den metoden först.

Låt oss ta en titt på `ShouldContinue` åtgärden.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Det ger oss en enklare prompt med färre alternativ.

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Det största problemet med `ShouldContinue` är att användaren måste köra den interaktivt eftersom den alltid efterfrågar användaren. Du bör alltid skapa verktyg som kan användas av andra skript. På det sätt som du gör är det att implementera `-Force` . Jag går tillbaka till den här idén senare.

### <a name="yes-to-all"></a>Ja till alla

Detta hanteras automatiskt med `ShouldProcess` men vi måste göra lite mer arbete för `ShouldContinue` . Det finns en andra metod för överbelastning där vi måste skicka in några värden med hjälp av referens för att kontrol lera logiken.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

Jag har lagt till en `foreach` loop och en samling för att visa att den fungerar. Jag hämtade `ShouldContinue` anropet från `if` instruktionen för att göra det lättare att läsa. Att anropa en metod med fyra parametrar börjar få en liten fula, men jag försökte göra det så att det ser ut så rensat som jag kunde.

## <a name="implementing--force"></a>Implementera-Force

`ShouldProcess`och `ShouldContinue` måste implementera `-Force` på olika sätt. Sticket till dessa implementeringar är att `ShouldProcess` alltid ska köras, men `ShouldContinue` ska inte köras om `-Force` har angetts.

### <a name="shouldprocess--force"></a>ShouldProcess – Force

Om du väljer `ConfirmImpact` att göra `high` det är det första som användarna kommer att försöka att förhindra det med `-Force` . Det är det första jag gör.

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

Om du återkallar från `ConfirmImpact` avsnittet måste du faktiskt anropa det så här:

```powershell
Test-ShouldProcess -Confirm:$false
```

Alla inser att de inte behöver göra det och `-Confirm:$false` utelämna dem inte `ShouldContinue` .
Vi bör därför implementera `-Force` för Sanity av våra användare. Ta en titt på det här fullständiga exemplet här:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Vi lägger till vår egna `-Force` växel som en parameter och använder den `$Confirm` automatiska parametern som är tillgänglig när `SupportsShouldProcess` du lägger till den i `CmdletBinding` .

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

Fokusera på `-Force` logiken här:

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

Om användaren anger `-Force` vill vi ignorera bekräftelse uppmaningen om de inte också anges `-Confirm` . Detta gör att en användare kan tvinga fram en ändring men fortfarande bekräfta ändringen. Sedan ställer vi in `$ConfirmPreference` i det lokala omfånget där vi ringer till `ShouldProcess` identifierings funktionen.

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

Om någon anger både `-Force` och `-WhatIf` , `-WhatIf` måste du prioritera. Den här metoden bevarar `-WhatIf` bearbetningen eftersom `ShouldProcess` alltid körs.

Lägg inte till en kontroll för `$Force` värdet i IF-instruktionen med `ShouldProcess` . Det är ett anti-mönster för det här scenariot, även om det är det som visas i nästa avsnitt för `ShouldContinue` .

### <a name="shouldcontinue--force"></a>ShouldContinue – Force

Detta är det korrekta sättet att implementera `-Force` med `ShouldContinue` .

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Genom att placera `$Force` till vänster om `-or` operatorn utvärderas det först. Om du skriver på det sättet kortas körningen av `if` instruktionen. Om `$force` är `$true` , `ShouldContinue` körs inte.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

Vi behöver inte bekymra dig om `-Confirm` eller `-WhatIf` i det här scenariot eftersom de inte stöds av `ShouldContinue` . Det är därför det måste hanteras på ett annat sätt än `ShouldProcess` .

## <a name="scope-issues"></a>Omfattnings problem

Använder `-WhatIf` och ska `-Confirm` användas för allt i funktionerna och allt de kallar. De gör detta genom att ställa in `$WhatIfPreference` till `$true` eller ställa in `$ConfirmPreference` till `Low` i det lokala omfånget för funktionen. Anrop att använda dessa värden när du anropar en annan funktion `ShouldProcess` .

Detta fungerar faktiskt för det mesta av tiden. När du anropar en inbyggd cmdlet eller en funktion i samma omfång, fungerar den som den ska. Det fungerar också när du anropar ett skript eller en funktion i en skript-modul från-konsolen.

Den enda plats där det inte fungerar är när ett skript eller en skript-modul anropar en funktion i en annan modul. Detta kanske inte kan likna ett stort problem, men de flesta moduler som du skapar eller hämtar från PSGallery är skript moduler.

Kärn problemet är att skriptfilerna inte ärver värdena för `$WhatIfPreference` eller `$ConfirmPreference` (och flera andra) när de anropas från funktioner i andra skript moduler.

Det bästa sättet att sammanfatta detta som en allmän regel är att det fungerar korrekt för binära moduler och aldrig litar på att det fungerar för skript moduler. Om du inte är säker kan du antingen testa det eller bara anta att det inte fungerar som det ska.

Jag tycker att det är mycket farligt eftersom det skapar scenarier där du lägger till `-WhatIf` stöd för flera moduler som fungerar korrekt i isolering, men som inte fungerar korrekt när de anropar varandra.

Vi har en GitHub-RFC som fungerar för att få det här problemet åtgärdat. Mer information finns i avsnittet om att [sprida körnings inställningar utöver skript modulens omfång][RFC] .

## <a name="in-closing"></a>I stängning

Jag måste leta upp hur man använder `ShouldProcess` varje gång jag behöver använda det. Det tog lång tid att skilja `ShouldProcess` från `ShouldContinue` . Jag behöver nästan alltid se vilka parametrar som ska användas. Du behöver inte oroa dig om du fortfarande kan växla från tid till gång. Den här artikeln är här när du behöver den. Jag är säker på att jag ska referera till det ofta.

Om du gillade det här inlägget kan du dela dina tankar med mig på Twitter med hjälp av länken nedan. Jag vill alltid höra från personer som får värde från mitt innehåll.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[vanliga parametrar]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[allt du ville veta om hash]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
