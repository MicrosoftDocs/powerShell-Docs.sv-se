---
title: Functions
description: Med PowerShell-funktioner kan du skapa verktyg som kan återanvändas i skript.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ca48f3020fa306f8a24328bd18648d5954c48a94
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436458"
---
# <a name="chapter-9---functions"></a><span data-ttu-id="7a1f0-103">Kapitel 9 – funktioner</span><span class="sxs-lookup"><span data-stu-id="7a1f0-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="7a1f0-104">Om du skriver PowerShell-liners eller-skript och du ofta behöver ändra dem för olika scenarier, är det en bra chans att det är en bra kandidat att bli inaktive rad i en funktion som kan återanvändas.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="7a1f0-105">När det är möjligt föredrar jag att skriva funktioner eftersom de är mer orienterade.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="7a1f0-106">Jag kan placera funktionerna i en-skript-modul, placera modulen i `$env:PSModulePath` och anropa funktionerna utan att behöva placera dem fysiskt där de har sparats.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="7a1f0-107">Med PowerShellGet-modulen är det enkelt att dela dessa moduler i en NuGet-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="7a1f0-108">PowerShellGet levereras med PowerShell version 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="7a1f0-109">Den är tillgänglig som en separat nedladdning för PowerShell version 3,0 och högre.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="7a1f0-110">Du behöver inte göra några förkomplicerade saker.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-110">Don't over complicate things.</span></span> <span data-ttu-id="7a1f0-111">Håll det enkelt och Använd det bästa vanliga sättet för att utföra en uppgift.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="7a1f0-112">Undvik alias och positions parametrar i alla koder som du återanvänder.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="7a1f0-113">Formatera koden för läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-113">Format your code for readability.</span></span> <span data-ttu-id="7a1f0-114">Hårdkoda inte värden; Använd parametrar och variabler.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="7a1f0-115">Skriv inte onödig kod även om den inte försämra något.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="7a1f0-116">Den lägger till onödig komplexitet.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="7a1f0-117">Information går bra när du skriver en PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="7a1f0-118">Namngivning</span><span class="sxs-lookup"><span data-stu-id="7a1f0-118">Naming</span></span>

<span data-ttu-id="7a1f0-119">När du namnger dina funktioner i PowerShell använder du ett [Pascal Case] []-namn med ett godkänt verb och ett singular substantiv.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="7a1f0-120">Jag rekommenderar också att du förkorrigerar substantiv.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="7a1f0-121">Exempel: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="7a1f0-122">I PowerShell finns det en detaljerad lista över godkända verb som kan hämtas genom att köra `Get-Verb` .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

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

<span data-ttu-id="7a1f0-123">I föregående exempel har jag sorterat resultaten efter kolumnen **verb** .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="7a1f0-124">I kolumnen **grupp** får du en uppfattning om hur dessa verb används.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="7a1f0-125">Det är viktigt att välja ett godkänt verb i PowerShell när funktioner läggs till i en modul.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="7a1f0-126">Modulen genererar ett varnings meddelande vid inläsnings tillfället om du väljer ett ej godkänt verb.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="7a1f0-127">Varnings meddelandet gör att dina funktioner ser ut att vara professionella.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="7a1f0-128">Icke-godkända verb begränsar också funktionernanas identifiering.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="7a1f0-129">En enkel funktion</span><span class="sxs-lookup"><span data-stu-id="7a1f0-129">A simple function</span></span>

<span data-ttu-id="7a1f0-130">En funktion i PowerShell deklareras med nyckelordet Function följt av funktions namnet och sedan en öppen och avslutande klammer.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="7a1f0-131">Den kod som funktionen ska köra finns inuti klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="7a1f0-132">Funktionen som visas är ett enkelt exempel som returnerar versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="7a1f0-133">Det finns en utmärkt chans att namn krockar med funktioner som kallas något som `Get-Version` standard kommandon i PowerShell eller kommandon som andra kan skriva.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="7a1f0-134">Det är därför jag rekommenderar att du förkorrigerar Substantiv delen av dina funktioner för att förhindra namngivnings konflikter.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="7a1f0-135">I följande exempel använder jag prefixet "PS".</span><span class="sxs-lookup"><span data-stu-id="7a1f0-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="7a1f0-136">Förutom namnet är den här funktionen identisk med föregående.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="7a1f0-137">Även när du förlöser substantiv med något som PS, finns det fortfarande en chans att ha en namn konflikt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="7a1f0-138">Jag brukar prefix My Function substantiv med mina initialer.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="7a1f0-139">Utveckla ett standard-och-märke till den.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="7a1f0-140">Den här funktionen skiljer sig inte från de tidigare två, förutom att använda ett mer lämpliga-namn för att försöka förhindra namn konflikter med andra PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="7a1f0-141">När du har läst in i minnet kan du se funktioner i **funktionen** PSDrive.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

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

<span data-ttu-id="7a1f0-142">Om du vill ta bort dessa funktioner från den aktuella sessionen måste du ta bort dem från **funktionen** PSDrive eller stänga och öppna PowerShell igen.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="7a1f0-143">Kontrol lera att funktionerna verkligen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="7a1f0-144">Om funktionerna lästes in som en del av en modul kan modulen tas bort från minnet för att ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="7a1f0-145">`Remove-Module`Cmdleten tar bort moduler från minnet i den aktuella PowerShell-sessionen, men den tas inte bort från systemet eller från disken.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="7a1f0-146">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7a1f0-146">Parameters</span></span>

<span data-ttu-id="7a1f0-147">Tilldela inte värden statiskt!</span><span class="sxs-lookup"><span data-stu-id="7a1f0-147">Don't statically assign values!</span></span> <span data-ttu-id="7a1f0-148">Använd parametrar och variabler.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-148">Use parameters and variables.</span></span> <span data-ttu-id="7a1f0-149">När det gäller att namnge parametrarna använder du samma namn som standard-cmdletarna för dina parameter namn när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="7a1f0-150">Varför använde jag **computername** och inte **dator**, **Server namn**eller **värd** för mitt parameter namn?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-150">Why did I use **ComputerName** and not **Computer**, **ServerName**, or **Host** for my parameter name?</span></span> <span data-ttu-id="7a1f0-151">Det beror på att jag ville ha funktionen standard som standard-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="7a1f0-152">Jag skapar en funktion för att fråga alla kommandon i ett system och returnera antalet som har vissa parameter namn.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

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

<span data-ttu-id="7a1f0-153">Som du ser i resultaten som visas nedan, kan du 39 kommandon som har en **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="7a1f0-154">Det finns inga cmdletar som har parametrar som **dator**, **servername**, **Host**eller **Machine**.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-154">There aren't any cmdlets that have parameters such as **Computer**, **ServerName**, **Host**, or **Machine**.</span></span>

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

<span data-ttu-id="7a1f0-155">Jag rekommenderar också att du använder samma Skift läge för parameter namn som standard-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="7a1f0-156">Använd `ComputerName` , inte `computername` .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="7a1f0-157">Detta gör att funktionerna ser ut och fungerar som standard-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="7a1f0-158">Personer som redan är bekanta med PowerShell känner sig till höger hemma.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-158">People who are already familiar with PowerShell will feel right at home.</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="7a1f0-159">Avancerade funktioner</span><span class="sxs-lookup"><span data-stu-id="7a1f0-159">Advanced Functions</span></span>

<span data-ttu-id="7a1f0-160">Det är enkelt att aktivera en funktion i PowerShell i en avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-160">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="7a1f0-161">En av skillnaderna mellan en funktion och en avancerad funktion är att avancerade funktioner har ett antal vanliga parametrar som läggs till i funktionen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-161">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="7a1f0-162">Dessa vanliga parametrar innehåller parametrar som **utförlig** och **fel sökning**.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-162">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="7a1f0-163">Jag börjar med `Test-MrParameter` funktionen som användes i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-163">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="7a1f0-164">Vad jag vill att du ska märka är att `Test-MrParameter` funktionen inte har några gemensamma parametrar.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-164">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="7a1f0-165">Det finns ett par olika sätt att se de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-165">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="7a1f0-166">Det ena är att visa syntaxen med hjälp av `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-166">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="7a1f0-167">En annan är att öka detalj nivån i parametrarna med `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-167">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="7a1f0-168">Lägg till `CmdletBinding` för att aktivera funktionen i en avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-168">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="7a1f0-169">När `CmdletBinding` du lägger till läggs de gemensamma parametrarna automatiskt till.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-169">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="7a1f0-170">`CmdletBinding`kräver ett `param` block, men `param` blocket kan vara tomt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-170">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="7a1f0-171">Gå nedåt i parametrarna med `Get-Command` visar de faktiska parameter namnen inklusive de vanliga.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-171">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

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

## <a name="supportsshouldprocess"></a><span data-ttu-id="7a1f0-172">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="7a1f0-172">SupportsShouldProcess</span></span>

<span data-ttu-id="7a1f0-173">`SupportsShouldProcess`lägger till parametrarna **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-173">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="7a1f0-174">De behövs bara för kommandon som gör ändringar.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-174">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="7a1f0-175">Observera att det nu finns **whatIf** och **Bekräfta** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-175">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="7a1f0-176">Du kan också använda `Get-Command` för att returnera en lista över de faktiska parameter namnen, inklusive de som är gemensamma tillsammans med whatIf och bekräfta.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-176">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

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

## <a name="parameter-validation"></a><span data-ttu-id="7a1f0-177">Parameter validering</span><span class="sxs-lookup"><span data-stu-id="7a1f0-177">Parameter Validation</span></span>

<span data-ttu-id="7a1f0-178">Verifiera inaktivitet tidigt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-178">Validate input early on.</span></span> <span data-ttu-id="7a1f0-179">Varför kan din kod fortsätta på en sökväg när det inte går att köra utan giltiga indatamängdar?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-179">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="7a1f0-180">Skriv alltid variablerna som används för parametrarna (ange en datatyp).</span><span class="sxs-lookup"><span data-stu-id="7a1f0-180">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="7a1f0-181">I det föregående exemplet har jag angett **sträng** som datatyp för parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-181">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="7a1f0-182">Detta gör att det bara tillåter att ett enda dator namn anges.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-182">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="7a1f0-183">Om fler än ett dator namn anges via en kommaavgränsad lista, genereras ett fel.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-183">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

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

<span data-ttu-id="7a1f0-184">Problemet med den aktuella definitionen är att det är giltigt att utelämna värdet för parametern **computername** , men ett värde krävs för att funktionen ska kunna slutföras.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-184">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="7a1f0-185">Det är där `Mandatory` attributet parameter är praktiskt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-185">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

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

<span data-ttu-id="7a1f0-186">Syntaxen som används i föregående exempel är PowerShell version 3,0 och högre kompatibel.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-186">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="7a1f0-187">`[Parameter(Mandatory=$true)]`kan anges i stället för att göra funktionen kompatibel med PowerShell version 2,0 och högre.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-187">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="7a1f0-188">Nu när **computername** krävs, om ett sådant inte har angetts, kommer funktionen att uppmanas att ange en.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-188">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="7a1f0-189">Om du vill tillåta fler än ett värde för parametern **computername** använder du **sträng** data typen men lägger till öppna och stängda hakparenteser till data typen för att tillåta en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-189">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

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

<span data-ttu-id="7a1f0-190">Du kanske vill ange ett standardvärde för parametern **computername** om ingen sådan har angetts.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-190">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="7a1f0-191">Problemet är att standardvärden inte kan användas med obligatoriska parametrar.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-191">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="7a1f0-192">I stället måste du använda `ValidateNotNullOrEmpty` attributet parameter validering med ett standardvärde.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-192">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

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

<span data-ttu-id="7a1f0-193">Försök att inte använda statiska värden även när du anger ett standardvärde.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-193">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="7a1f0-194">I föregående exempel `$env:COMPUTERNAME` används som standardvärde, som automatiskt översätts till det lokala dator namnet om ett värde inte anges.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-194">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="7a1f0-195">Utförlig utdata</span><span class="sxs-lookup"><span data-stu-id="7a1f0-195">Verbose Output</span></span>

<span data-ttu-id="7a1f0-196">Även om kommentarer är användbara, särskilt om du skriver en komplicerad kod, visas de aldrig av användarna om de inte tittar på själva koden.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-196">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="7a1f0-197">Funktionen som visas i följande exempel har en infogad kommentar i `foreach` slingan.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-197">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="7a1f0-198">Även om den här kommentaren kanske inte är så svår att hitta, Föreställ dig om funktionen innehöll hundratals kodrader.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-198">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

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

<span data-ttu-id="7a1f0-199">Ett bättre alternativ är att använda `Write-Verbose` i stället för infogade kommentarer.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-199">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

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

<span data-ttu-id="7a1f0-200">När funktionen anropas utan **verbose** -parametern visas inte utförliga utdata.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-200">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="7a1f0-201">När den anropas med **verbose** -parametern visas utförlig utdata.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-201">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="7a1f0-202">Pipeline-inmatade</span><span class="sxs-lookup"><span data-stu-id="7a1f0-202">Pipeline Input</span></span>

<span data-ttu-id="7a1f0-203">Om du vill att din funktion ska godkänna pipeline-ininformation krävs ytterligare kod.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-203">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="7a1f0-204">Som tidigare nämnts i den här boken kan kommandon acceptera pipeline-inmatade **värde** (efter typ) eller **efter egenskaps namn**.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-204">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="7a1f0-205">Du kan skriva funktioner precis som de inbyggda kommandona så att de accepterar antingen en eller båda av de här typerna av inmatade.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-205">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="7a1f0-206">Om du vill acceptera pipeline-inmatat **värde**anger du `ValueFromPipeline` parameterns parameter för den specifika parametern.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-206">To accept pipeline input **by value**, specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="7a1f0-207">Tänk på att du bara kan acceptera pipeline-indata **med värde** från en av varje datatyp.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-207">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="7a1f0-208">Om du t. ex. har två parametrar som accepterar inmatade strängar, kan bara en av dem acceptera pipeline-inmatade **värden** , eftersom om du har angett den för båda sträng parametrarna, vet inte pipeline-indatatypen vilken av dem som ska bindas till.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-208">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="7a1f0-209">Det här är ett annat orsak till varför jag anropar den här typen av pipeline-indatatyper _efter typ_ i stället för **efter värde**.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-209">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="7a1f0-210">Pipeline-InInformationen kommer att finnas i ett objekt i taget på samma sätt som objekt hanteras i en `foreach` slinga.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-210">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="7a1f0-211">Ett `process` block krävs minst för att bearbeta vart och ett av dessa objekt om du accepterar en matris som inmatad.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-211">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="7a1f0-212">Om du bara accepterar ett enda värde som indata är ett `process` block inte nödvändigt, men jag rekommenderar att du ändå anger det för konsekvens.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-212">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

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

<span data-ttu-id="7a1f0-213">Att acceptera pipeline-indata **efter egenskaps namn** är liknande förutom att det har angetts med `ValueFromPipelineByPropertyName` attributet parameter och det kan anges för valfritt antal parametrar oavsett datatyp.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-213">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="7a1f0-214">Nyckeln är att utdata från kommandot som skickas i måste ha ett egenskaps namn som matchar namnet på parametern eller ett parameter-alias för funktionen.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-214">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

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

<span data-ttu-id="7a1f0-215">`BEGIN`och `END` block är valfria.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-215">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="7a1f0-216">`BEGIN`anges före `PROCESS` blocket och används för att utföra alla inledande arbeten innan de objekt som tas emot från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-216">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="7a1f0-217">Detta är viktigt att förstå.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-217">This is important to understand.</span></span> <span data-ttu-id="7a1f0-218">Det går inte att komma åt värden som är skickas i `BEGIN` blocket.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-218">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="7a1f0-219">`END`Blocket anges efter `PROCESS` blocket och används för rensning när alla objekt som skickas har bearbetats.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-219">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="7a1f0-220">Felhantering</span><span class="sxs-lookup"><span data-stu-id="7a1f0-220">Error Handling</span></span>

<span data-ttu-id="7a1f0-221">Funktionen som visas i följande exempel genererar ett ohanterat undantag när det inte går att kontakta en dator.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-221">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

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

<span data-ttu-id="7a1f0-222">Det finns ett par olika sätt att hantera fel i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-222">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="7a1f0-223">`Try/Catch`är det mer modern sättet att hantera fel.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-223">`Try/Catch` is the more modern way to handle errors.</span></span>

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

<span data-ttu-id="7a1f0-224">Även om funktionen som visas i föregående exempel använder fel hantering, genererar den också ett ohanterat undantag eftersom kommandot inte genererar något avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-224">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="7a1f0-225">Detta är också viktigt att förstå.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-225">This is also important to understand.</span></span> <span data-ttu-id="7a1f0-226">Det är bara att avsluta fel som har påträffats.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-226">Only terminating errors are caught.</span></span> <span data-ttu-id="7a1f0-227">Ange parametern **ErrorAction** med **stopp** som värde för att inaktivera ett icke-avslutande fel i en avslutning.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-227">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

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

<span data-ttu-id="7a1f0-228">Ändra inte den globala `$ErrorActionPreference` variabeln om det inte är absolut nödvändigt.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-228">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="7a1f0-229">Om du använder något som .NET direkt från din PowerShell-funktion kan du inte ange **ErrorAction** i själva kommandot.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-229">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="7a1f0-230">I så fall kan du behöva ändra den globala `$ErrorActionPreference` variabeln, men om du ändrar den, ändrar du den direkt efter att du har försökt med kommandot.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-230">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="7a1f0-231">Kommenterings-baserad hjälp</span><span class="sxs-lookup"><span data-stu-id="7a1f0-231">Comment-Based Help</span></span>

<span data-ttu-id="7a1f0-232">Det anses vara en bra idé att lägga till kommenterad hjälp till dina funktioner så att de personer som du delar dem med vet hur de ska användas.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-232">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

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

<span data-ttu-id="7a1f0-233">När du lägger till en kommenterad hjälp till dina funktioner kan du hämta hjälpen för dem precis som de inbyggda standard kommandona.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-233">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="7a1f0-234">All syntax för att skriva en funktion i PowerShell kan verka överbelastad särskilt för någon som precis har börjat.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-234">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="7a1f0-235">Ofta om jag inte kan komma ihåg syntaxen för något, öppnar jag en andra kopia av ISE på en separat övervakare och visar kodfragmentet "cmdlet (avancerad funktion)-Complete" när du skriver in koden för min funktion.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-235">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="7a1f0-236">Du kan komma åt kod avsnitt i PowerShell ISE med tangentkombinationen <kbd>CTRL</kbd> + <kbd>J</kbd> .</span><span class="sxs-lookup"><span data-stu-id="7a1f0-236">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="7a1f0-237">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="7a1f0-237">Summary</span></span>

<span data-ttu-id="7a1f0-238">I det här kapitlet har du lärt dig grunderna i att skriva funktioner i PowerShell som innehåller information om hur du aktiverar en funktion i en avancerad funktion och några av de viktiga element som du bör tänka på när du skriver PowerShell-funktioner som parameter validering, utförlig utdata, pipeline-indata, fel hantering och kommenterad hjälp.</span><span class="sxs-lookup"><span data-stu-id="7a1f0-238">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="7a1f0-239">Granska</span><span class="sxs-lookup"><span data-stu-id="7a1f0-239">Review</span></span>

1. <span data-ttu-id="7a1f0-240">Hur får du en lista över godkända verb i PowerShell?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-240">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="7a1f0-241">Hur aktiverar du en PowerShell-funktion i en avancerad funktion?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-241">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="7a1f0-242">När ska **whatIf** -och **Confirm** -parametrar läggas till i dina PowerShell-funktioner?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-242">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="7a1f0-243">Hur gör du ett icke-avslutande fel i ett avslutande meddelande?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-243">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="7a1f0-244">Varför ska du lägga till kommenterad hjälp till dina funktioner?</span><span class="sxs-lookup"><span data-stu-id="7a1f0-244">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="7a1f0-245">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="7a1f0-245">Recommended Reading</span></span>

- <span data-ttu-id="7a1f0-246">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-246">[about_Functions][]</span></span>
- <span data-ttu-id="7a1f0-247">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-247">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="7a1f0-248">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-248">[about_CommonParameters][]</span></span>
- <span data-ttu-id="7a1f0-249">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-249">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="7a1f0-250">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-250">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="7a1f0-251">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-251">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="7a1f0-252">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-252">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="7a1f0-253">[Video: PowerShell-Toolmaking med avancerade funktioner och skript moduler] []</span><span class="sxs-lookup"><span data-stu-id="7a1f0-253">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Video: PowerShell-Toolmaking med avancerade funktioner och skript moduler]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal Case]:/dotNet/standard/design-Guidelines/capitalization-Conventions
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventionss
