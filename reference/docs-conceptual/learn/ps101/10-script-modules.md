---
title: Skript moduler
description: Skript moduler är ett enkelt sätt att paketera skript och funktioner i ett återanvändbart verktyg.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436514"
---
# <a name="chapter-10---script-modules"></a><span data-ttu-id="44759-103">Kapitel 10 – skript moduler</span><span class="sxs-lookup"><span data-stu-id="44759-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="44759-104">Att aktivera en-liners och skript i PowerShell till återanvändbara verktyg blir ännu viktigare om det är något som du kommer att använda ofta.</span><span class="sxs-lookup"><span data-stu-id="44759-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="44759-105">Genom att paketera dina funktioner i en-skript-modul kan de se ut och känna sig tryggare och gör dem lättare att dela.</span><span class="sxs-lookup"><span data-stu-id="44759-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="44759-106">Funktioner för punkt-källa</span><span class="sxs-lookup"><span data-stu-id="44759-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="44759-107">Något som vi inte pratar om i det förra kapitlet är funktioner för punkt-ursprung.</span><span class="sxs-lookup"><span data-stu-id="44759-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="44759-108">När en funktion i ett skript inte är en del av en modul, är det enda sättet att läsa in den i minnet att vara i punkt källa `.PS1` filen som den sparats i.</span><span class="sxs-lookup"><span data-stu-id="44759-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="44759-109">Följande funktion har sparats som `Get-MrPSVersion.ps1` .</span><span class="sxs-lookup"><span data-stu-id="44759-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="44759-110">När du kör skriptet händer ingenting.</span><span class="sxs-lookup"><span data-stu-id="44759-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="44759-111">Om du försöker anropa funktionen genererar det ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="44759-111">If you try to call the function, it generates an error message.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

<span data-ttu-id="44759-112">Du kan kontrol lera om funktioner läses in i minnet genom att kontrol lera om de finns i **funktionen** PSDrive.</span><span class="sxs-lookup"><span data-stu-id="44759-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

<span data-ttu-id="44759-113">Problemet med att anropa skriptet som innehåller funktionen är att funktionerna läses in i _skript_ omfånget.</span><span class="sxs-lookup"><span data-stu-id="44759-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="44759-114">När skriptet har slutförts tas omfattningen bort och funktionen tas bort med den.</span><span class="sxs-lookup"><span data-stu-id="44759-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="44759-115">Funktionen måste läsas in i det _globala_ omfånget.</span><span class="sxs-lookup"><span data-stu-id="44759-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="44759-116">Detta kan utföras av punkt-käll skriptet som innehåller funktionen.</span><span class="sxs-lookup"><span data-stu-id="44759-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="44759-117">Du kan använda den relativa sökvägen.</span><span class="sxs-lookup"><span data-stu-id="44759-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="44759-118">Den fullständigt kvalificerade sökvägen kan också användas.</span><span class="sxs-lookup"><span data-stu-id="44759-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="44759-119">Om en del av sökvägen lagras i en variabel, kan den kombineras med resten av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="44759-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="44759-120">Det finns ingen anledning att använda sträng sammanfogning för att kombinera variabeln tillsammans med resten av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="44759-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="44759-121">Nu när jag kontrollerar **funktionen** PSDrive `Get-MrPSVersion` finns funktionen.</span><span class="sxs-lookup"><span data-stu-id="44759-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="44759-122">Skript moduler</span><span class="sxs-lookup"><span data-stu-id="44759-122">Script Modules</span></span>

<span data-ttu-id="44759-123">En skript-modul i PowerShell är bara en fil som innehåller en eller flera funktioner som sparas som en `.PSM1` fil i stället för en `.PS1` fil.</span><span class="sxs-lookup"><span data-stu-id="44759-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="44759-124">Hur skapar du en-skript-modul?</span><span class="sxs-lookup"><span data-stu-id="44759-124">How do you create a script module?</span></span> <span data-ttu-id="44759-125">Du är förmodligen nöjd med ett kommando med namnet någonting `New-Module` .</span><span class="sxs-lookup"><span data-stu-id="44759-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="44759-126">Ditt antagande skulle vara fel.</span><span class="sxs-lookup"><span data-stu-id="44759-126">Your assumption would be wrong.</span></span> <span data-ttu-id="44759-127">Även om det finns ett kommando i PowerShell med namnet `New-Module` skapar det kommandot en dynamisk modul, inte en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="44759-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="44759-128">Se alltid till att läsa hjälpen för ett kommando även när du tror att du har hittat det kommando du behöver.</span><span class="sxs-lookup"><span data-stu-id="44759-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

<span data-ttu-id="44759-129">I föregående kapitel nämnde jag att funktioner ska använda godkända verb, annars genererar de ett varnings meddelande när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="44759-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="44759-130">Följande kod använder `New-Module` cmdleten för att skapa en dynamisk modul i minnet.</span><span class="sxs-lookup"><span data-stu-id="44759-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="44759-131">Den här modulen visar varningen för ej godkända verb.</span><span class="sxs-lookup"><span data-stu-id="44759-131">This module demonstrates the unapproved verb warning.</span></span>

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

<span data-ttu-id="44759-132">Bara att upprepa, även om `New-Module` cmdleten användes i föregående exempel, är det inte kommandot för att skapa skript moduler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44759-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="44759-133">Spara följande två funktioner i en fil med namnet `MyScriptModule.psm1` .</span><span class="sxs-lookup"><span data-stu-id="44759-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="44759-134">Försök att anropa en av funktionerna.</span><span class="sxs-lookup"><span data-stu-id="44759-134">Try to call one of the functions.</span></span>

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="44759-135">Ett fel meddelande skapas som säger att funktionen inte kan hittas.</span><span class="sxs-lookup"><span data-stu-id="44759-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="44759-136">Du kan också kontrol lera att **funktionen** PSDrive precis som tidigare och att det inte finns någon.</span><span class="sxs-lookup"><span data-stu-id="44759-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="44759-137">Du kan importera filen manuellt med `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="44759-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="44759-138">Funktionen automatisk inläsning av modulen introducerades i PowerShell version 3.</span><span class="sxs-lookup"><span data-stu-id="44759-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="44759-139">För att kunna dra nytta av automatisk inläsning av modulen måste en modul för skript sparas i en mapp med samma bas namn som `.PSM1` filen och på en plats som anges i `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="44759-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="44759-140">Det är svårt att läsa resultatet.</span><span class="sxs-lookup"><span data-stu-id="44759-140">The results are difficult to read.</span></span> <span data-ttu-id="44759-141">Eftersom Sök vägarna skiljs åt med ett semikolon kan du dela resultaten för att returnera varje sökväg på en separat rad.</span><span class="sxs-lookup"><span data-stu-id="44759-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="44759-142">Detta gör dem lättare att läsa.</span><span class="sxs-lookup"><span data-stu-id="44759-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="44759-143">De första tre Sök vägarna i listan är standard.</span><span class="sxs-lookup"><span data-stu-id="44759-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="44759-144">När SQL Server Management Studio installerades lades den senaste sökvägen till.</span><span class="sxs-lookup"><span data-stu-id="44759-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="44759-145">För att automatisk inläsning av modulen ska fungera `MyScriptModule.psm1` måste filen finnas i en mapp som heter `MyScriptModule` direkt inuti någon av dessa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="44759-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="44759-146">Inte så snabbt.</span><span class="sxs-lookup"><span data-stu-id="44759-146">Not so fast.</span></span> <span data-ttu-id="44759-147">För mig är min nuvarande användar Sök väg inte den första i listan.</span><span class="sxs-lookup"><span data-stu-id="44759-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="44759-148">Jag använder nästan aldrig den sökvägen eftersom jag loggar in i Windows med en annan användare än den som används för att köra PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44759-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="44759-149">Det innebär att den inte finns i min vanliga dokument-mapp.</span><span class="sxs-lookup"><span data-stu-id="44759-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="44759-150">Den andra sökvägen är **allusers** -sökvägen.</span><span class="sxs-lookup"><span data-stu-id="44759-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="44759-151">Detta är den plats där jag lagrar alla mina moduler.</span><span class="sxs-lookup"><span data-stu-id="44759-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="44759-152">Den tredje sökvägen är under `C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="44759-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="44759-153">Endast Microsoft ska lagra moduler på den platsen eftersom det finns i operativ systemets mapp.</span><span class="sxs-lookup"><span data-stu-id="44759-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="44759-154">När `.PSM1` filen finns på rätt sökväg, kommer modulen att läsas in automatiskt när ett av dess kommandon anropas.</span><span class="sxs-lookup"><span data-stu-id="44759-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="44759-155">Modul manifest</span><span class="sxs-lookup"><span data-stu-id="44759-155">Module Manifests</span></span>

<span data-ttu-id="44759-156">Alla moduler bör ha ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="44759-156">All modules should have a module manifest.</span></span> <span data-ttu-id="44759-157">Ett modul manifest innehåller metadata om modulen.</span><span class="sxs-lookup"><span data-stu-id="44759-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="44759-158">Fil namns tillägget för en modul manifest fil är `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="44759-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="44759-159">Alla filer med `.PSD1` fil namns tillägget är inte modul manifest.</span><span class="sxs-lookup"><span data-stu-id="44759-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="44759-160">De kan också användas för sådant som att lagra miljö delen av en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="44759-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="44759-161">`New-ModuleManifest`används för att skapa ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="44759-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="44759-162">**Sökväg** är det enda värde som krävs.</span><span class="sxs-lookup"><span data-stu-id="44759-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="44759-163">Modulen fungerar dock inte om **RootModule** inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="44759-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="44759-164">Det är en bra idé att ange **författare** och **Beskrivning** om du vill ladda upp modulen till en NuGet-lagringsplats med PowerShellGet eftersom dessa värden krävs i det scenariot.</span><span class="sxs-lookup"><span data-stu-id="44759-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="44759-165">Versionen av en modul utan manifest är 0,0.</span><span class="sxs-lookup"><span data-stu-id="44759-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="44759-166">Detta är en död Giveaway att modulen inte har något manifest.</span><span class="sxs-lookup"><span data-stu-id="44759-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="44759-167">Modul manifestet kan skapas med all den rekommenderade informationen.</span><span class="sxs-lookup"><span data-stu-id="44759-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="44759-168">Om någon av dessa uppgifter saknas under den inledande skapandet av modulen manifest, kan den läggas till eller uppdateras senare med `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="44759-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="44759-169">Återskapa inte manifestet med `New-ModuleManifest` när det redan har skapats, eftersom GUID ändras.</span><span class="sxs-lookup"><span data-stu-id="44759-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="44759-170">Definiera offentliga och privata funktioner</span><span class="sxs-lookup"><span data-stu-id="44759-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="44759-171">Du kan ha hjälp funktioner som du kanske vill vara privata och som endast kan nås av andra funktioner i modulen.</span><span class="sxs-lookup"><span data-stu-id="44759-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="44759-172">De är inte avsedda att vara tillgängliga för användare av modulen.</span><span class="sxs-lookup"><span data-stu-id="44759-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="44759-173">Det finns ett par olika sätt att åstadkomma detta.</span><span class="sxs-lookup"><span data-stu-id="44759-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="44759-174">Om du inte följer de bästa metoderna och bara har en `.PSM1` fil, är ditt enda alternativ att använda `Export-ModuleMember` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="44759-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="44759-175">I föregående exempel `Get-MrPSVersion` är bara funktionen tillgänglig för användare av modulen, men `Get-MrComputerName` funktionen är tillgänglig för andra funktioner i själva modulen.</span><span class="sxs-lookup"><span data-stu-id="44759-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="44759-176">Om du har lagt till ett modul-manifest i modulen (och du borde) rekommenderar vi att du anger de enskilda funktioner som du vill exportera i avsnittet **FunctionsToExport** i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="44759-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="44759-177">Det är inte nödvändigt att använda båda `Export-ModuleMember` i `.PSM1` filen och **FunctionsToExport** -avsnittet i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="44759-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="44759-178">En eller flera av dem räcker.</span><span class="sxs-lookup"><span data-stu-id="44759-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="44759-179">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="44759-179">Summary</span></span>

<span data-ttu-id="44759-180">I det här kapitlet har du lärt dig hur du förvandlar dina funktioner till en-skript-modul i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44759-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="44759-181">Du har också lagt till några av de bästa metoderna för att skapa skript moduler, till exempel skapa ett modul manifest för din skript-modul.</span><span class="sxs-lookup"><span data-stu-id="44759-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="44759-182">Granska</span><span class="sxs-lookup"><span data-stu-id="44759-182">Review</span></span>

1. <span data-ttu-id="44759-183">Hur skapar du en modul för skript i PowerShell?</span><span class="sxs-lookup"><span data-stu-id="44759-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="44759-184">Varför är det viktigt att dina funktioner använder ett godkänt verb?</span><span class="sxs-lookup"><span data-stu-id="44759-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="44759-185">Hur skapar du ett modul-manifest i PowerShell?</span><span class="sxs-lookup"><span data-stu-id="44759-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="44759-186">Vilka är de två alternativen bara för att exportera vissa funktioner från modulen?</span><span class="sxs-lookup"><span data-stu-id="44759-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="44759-187">Vad krävs för att dina moduler ska läsas in automatiskt när ett kommando anropas?</span><span class="sxs-lookup"><span data-stu-id="44759-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="44759-188">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="44759-188">Recommended Reading</span></span>

- <span data-ttu-id="44759-189">[Så här skapar du PowerShell-skriptfiler och modul manifest][]</span><span class="sxs-lookup"><span data-stu-id="44759-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="44759-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="44759-190">[about_Modules][]</span></span>
- <span data-ttu-id="44759-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="44759-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="44759-192">[Exportera – ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="44759-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[Så här skapar du PowerShell-skriptfiler och modul manifest]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Exportera – ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
