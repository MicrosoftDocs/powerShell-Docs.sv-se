---
description: Beskriver hur PowerShell avgör vilket kommando som ska köras.
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 0b1ad7dc0fae9c6c0ec16929b3d538e5db4aea55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710243"
---
# <a name="about-command-precedence"></a><span data-ttu-id="b1746-103">Om kommando prioritet</span><span class="sxs-lookup"><span data-stu-id="b1746-103">About Command Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="b1746-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b1746-104">Short description</span></span>
<span data-ttu-id="b1746-105">Beskriver hur PowerShell avgör vilket kommando som ska köras.</span><span class="sxs-lookup"><span data-stu-id="b1746-105">Describes how PowerShell determines which command to run.</span></span>

## <a name="long-description"></a><span data-ttu-id="b1746-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b1746-106">Long description</span></span>

<span data-ttu-id="b1746-107">Kommando prioriteten beskriver hur PowerShell avgör vilket kommando som ska köras när en session innehåller fler än ett kommando med samma namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-107">Command precedence describes how PowerShell determines which command to run when a session contains more than one command with the same name.</span></span> <span data-ttu-id="b1746-108">Kommandon i en session kan döljas eller ersättas av kommandon med samma namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-108">Commands within a session can be hidden or replaced by commands with the same name.</span></span> <span data-ttu-id="b1746-109">Den här artikeln visar hur du kör dolda kommandon och hur du undviker kommando namns konflikter.</span><span class="sxs-lookup"><span data-stu-id="b1746-109">This article shows you how to run hidden commands and how to avoid command-name conflicts.</span></span>

## <a name="command-precedence"></a><span data-ttu-id="b1746-110">Kommando prioritet</span><span class="sxs-lookup"><span data-stu-id="b1746-110">Command precedence</span></span>

<span data-ttu-id="b1746-111">När en PowerShell-session innehåller fler än ett kommando som har samma namn, avgör PowerShell vilket kommando som ska köras med hjälp av följande regler.</span><span class="sxs-lookup"><span data-stu-id="b1746-111">When a PowerShell session includes more than one command that has the same name, PowerShell determines which command to run by using the following rules.</span></span>

<span data-ttu-id="b1746-112">Om du anger sökvägen till ett kommando kör PowerShell kommandot på den plats som anges i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b1746-112">If you specify the path to a command, PowerShell runs the command at the location specified by the path.</span></span>

<span data-ttu-id="b1746-113">Följande kommando kör till exempel FindDocs.ps1-skriptet i katalogen "C: \\ TechDocs":</span><span class="sxs-lookup"><span data-stu-id="b1746-113">For example, the following command runs the FindDocs.ps1 script in the "C:\\TechDocs" directory:</span></span>

```
C:\TechDocs\FindDocs.ps1
```

<span data-ttu-id="b1746-114">Som en säkerhetsfunktion kör PowerShell inte körbara (interna) kommandon, inklusive PowerShell-skript, om inte kommandot finns i en sökväg som anges i miljövariabeln PATH `$env:path` eller om du inte anger sökvägen till skript filen.</span><span class="sxs-lookup"><span data-stu-id="b1746-114">As a security feature, PowerShell does not run executable (native) commands, including PowerShell scripts, unless the command is located in a path that is listed in the Path environment variable `$env:path` or unless you specify the path to the script file.</span></span>

<span data-ttu-id="b1746-115">Om du vill köra ett skript som finns i den aktuella katalogen anger du den fullständiga sökvägen eller anger en punkt `.\` som representerar den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="b1746-115">To run a script that is in the current directory, specify the full path, or type a dot `.\` to represent the current directory.</span></span>

<span data-ttu-id="b1746-116">Om du till exempel vill köra FindDocs.ps1-filen i den aktuella katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="b1746-116">For example, to run the FindDocs.ps1 file in the current directory, type:</span></span>

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a><span data-ttu-id="b1746-117">Använda jokertecken i körningen</span><span class="sxs-lookup"><span data-stu-id="b1746-117">Using wildcards in execution</span></span>

<span data-ttu-id="b1746-118">Du kan använda jokertecken i kommando körningen.</span><span class="sxs-lookup"><span data-stu-id="b1746-118">You may use wildcards in command execution.</span></span> <span data-ttu-id="b1746-119">Användning av jokertecken kallas även *globbing*.</span><span class="sxs-lookup"><span data-stu-id="b1746-119">Using wildcard characters is also known as *globbing*.</span></span>

<span data-ttu-id="b1746-120">PowerShell kör en fil som har en matchning med jokertecken, före en literal matchning.</span><span class="sxs-lookup"><span data-stu-id="b1746-120">PowerShell executes a file that has a wildcard match, before a literal match.</span></span>

<span data-ttu-id="b1746-121">Överväg till exempel en katalog med följande filer:</span><span class="sxs-lookup"><span data-stu-id="b1746-121">For example, consider a directory with the following files:</span></span>

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

<span data-ttu-id="b1746-122">Båda skriptfilerna har samma innehåll: `$MyInvocation.MyCommand.Path` .</span><span class="sxs-lookup"><span data-stu-id="b1746-122">Both script files have the same content: `$MyInvocation.MyCommand.Path`.</span></span>
<span data-ttu-id="b1746-123">Det här kommandot visar namnet på det skript som anropas.</span><span class="sxs-lookup"><span data-stu-id="b1746-123">This command displays the name of the script that is invoked.</span></span>

<span data-ttu-id="b1746-124">När du kör körs `[a1].ps1` filen `a.ps1` även om filen `[a1].ps1` är en litteral matchning.</span><span class="sxs-lookup"><span data-stu-id="b1746-124">When you run `[a1].ps1`, the file `a.ps1` is executed even though the file `[a1].ps1` is a literal match.</span></span>

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

<span data-ttu-id="b1746-125">Nu ska vi ta bort `a.ps1` filen och försöka köra den igen.</span><span class="sxs-lookup"><span data-stu-id="b1746-125">Now let's delete the `a.ps1` file and attempt to run it again.</span></span>

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

<span data-ttu-id="b1746-126">Du kan se från utdata som `[a1].ps1` kör den här gången eftersom litteral matchning är den enda fil matchningen för mönster i jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b1746-126">You can see from the output that `[a1].ps1` runs this time because the literal match is the only file match for that wildcard pattern.</span></span>

<span data-ttu-id="b1746-127">Mer information om hur PowerShell använder jokertecken finns [about_Wildcards](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="b1746-127">For more information about how PowerShell uses wildcards, see [about_Wildcards](about_Wildcards.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b1746-128">Om du vill begränsa sökningen till en relativ sökväg måste du ge prefixet skriptet namnet med `.\` sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b1746-128">To limit the search to a relative path, you must prefix the script name with the `.\` path.</span></span> <span data-ttu-id="b1746-129">Detta begränsar Sök funktionen för kommandon till filer i den relativa sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b1746-129">This limits the search for commands to files in that relative path.</span></span> <span data-ttu-id="b1746-130">Utan det här prefixet kan andra PowerShell-syntaxen stå i konflikt och det finns några garantier som filen kan hittas.</span><span class="sxs-lookup"><span data-stu-id="b1746-130">Without this prefix, other PowerShell syntax may conflict and there are few guarantees that the file will be found.</span></span>

<span data-ttu-id="b1746-131">Om du inte anger en sökväg, använder PowerShell följande prioritetsordning när den kör kommandon för alla objekt som lästs in i den aktuella sessionen:</span><span class="sxs-lookup"><span data-stu-id="b1746-131">If you do not specify a path, PowerShell uses the following precedence order when it runs commands for all items loaded in the current session:</span></span>

  1. <span data-ttu-id="b1746-132">Alias</span><span class="sxs-lookup"><span data-stu-id="b1746-132">Alias</span></span>
  2. <span data-ttu-id="b1746-133">Funktion</span><span class="sxs-lookup"><span data-stu-id="b1746-133">Function</span></span>
  3. <span data-ttu-id="b1746-134">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b1746-134">Cmdlet</span></span>
  4. <span data-ttu-id="b1746-135">Externa körbara filer (program och icke-PowerShell-skript)</span><span class="sxs-lookup"><span data-stu-id="b1746-135">External executable files (programs and non-PowerShell scripts)</span></span>

<span data-ttu-id="b1746-136">Om du skriver "Help" letar PowerShell därför först efter ett alias med namnet `help` , sedan en funktion med namnet `Help` och slutligen en cmdlet med namnet `Help` .</span><span class="sxs-lookup"><span data-stu-id="b1746-136">Therefore, if you type "help", PowerShell first looks for an alias named `help`, then a function named `Help`, and finally a cmdlet named `Help`.</span></span> <span data-ttu-id="b1746-137">Den kör det första `help` objektet som hittas.</span><span class="sxs-lookup"><span data-stu-id="b1746-137">It runs the first `help` item that it finds.</span></span>

<span data-ttu-id="b1746-138">Om sessionen t. ex. innehåller en cmdlet och en funktion, både namngivna `Get-Map` , och när du skriver `Get-Map` , kör PowerShell funktionen.</span><span class="sxs-lookup"><span data-stu-id="b1746-138">For example, if your session contains a cmdlet and a function, both named `Get-Map`, when you type `Get-Map`, PowerShell runs the function.</span></span>

> [!NOTE]
> <span data-ttu-id="b1746-139">Detta gäller endast för inlästa kommandon.</span><span class="sxs-lookup"><span data-stu-id="b1746-139">This only applies to loaded commands.</span></span> <span data-ttu-id="b1746-140">Om det finns en `build` körbar fil och ett alias `build` för en funktion med namnet i `Invoke-Build` en modul som inte har lästs in i den aktuella sessionen, kör PowerShell den `build` körbara filen i stället.</span><span class="sxs-lookup"><span data-stu-id="b1746-140">If there is a `build` executable and an Alias `build` for a function with the name of `Invoke-Build` inside a module that is not loaded into the current session, PowerShell runs the `build` executable instead.</span></span> <span data-ttu-id="b1746-141">Modulerna läses inte in automatiskt om den externa körbara filen hittas i det här fallet.</span><span class="sxs-lookup"><span data-stu-id="b1746-141">It does not auto-load modules if it finds the external executable in this case.</span></span> <span data-ttu-id="b1746-142">Det är bara när ingen extern körbar fil hittas som ett alias, en funktion eller en cmdlet med det namnet anropas, vilket utlöser automatisk inläsning av sin modul.</span><span class="sxs-lookup"><span data-stu-id="b1746-142">It is only when no external executable is found that an alias, function, or cmdlet with the given name is invoked, thereby triggering auto-loading of its module.</span></span>

<span data-ttu-id="b1746-143">När sessionen innehåller objekt av samma typ som har samma namn, kör PowerShell det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="b1746-143">When the session contains items of the same type that have the same name, PowerShell runs the newer item.</span></span>

<span data-ttu-id="b1746-144">Om du till exempel importerar en annan `Get-Date` cmdlet från en modul, `Get-Date` kör PowerShell den importerade versionen över den ursprungliga.</span><span class="sxs-lookup"><span data-stu-id="b1746-144">For example, if you import another `Get-Date` cmdlet from a module, when you type `Get-Date`, PowerShell runs the imported version over the native one.</span></span>

## <a name="hidden-and-replaced-items"></a><span data-ttu-id="b1746-145">Dolda och ersatta objekt</span><span class="sxs-lookup"><span data-stu-id="b1746-145">Hidden and replaced items</span></span>

<span data-ttu-id="b1746-146">Som ett resultat av dessa regler kan objekt ersättas eller döljas av objekt med samma namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-146">As a result of these rules, items can be replaced or hidden by items with the same name.</span></span>

<span data-ttu-id="b1746-147">Objekten är "dolda" eller "skuggade" om du fortfarande har åtkomst till det ursprungliga objektet, till exempel genom att kvalificera objekt namnet med en modul eller ett namn på snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="b1746-147">Items are "hidden" or "shadowed" if you can still access the original item, such as by qualifying the item name with a module or snap-in name.</span></span>

<span data-ttu-id="b1746-148">Om du till exempel importerar en funktion som har samma namn som en cmdlet i sessionen är cmdleten dold (men inte ersatt) eftersom den har importer ATS från en snapin-modul eller modul.</span><span class="sxs-lookup"><span data-stu-id="b1746-148">For example, if you import a function that has the same name as a cmdlet in the session, the cmdlet is hidden (but not replaced) because it was imported from a snap-in or module.</span></span>

<span data-ttu-id="b1746-149">Objekt är "ersatta" eller "överskrivna" om du inte längre kan komma åt det ursprungliga objektet.</span><span class="sxs-lookup"><span data-stu-id="b1746-149">Items are "replaced" or "overwritten" if you can no longer access the original item.</span></span>

<span data-ttu-id="b1746-150">Om du till exempel importerar en variabel som har samma namn som en variabel i sessionen, ersätts den ursprungliga variabeln och är inte längre tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="b1746-150">For example, if you import a variable that has the same name as a variable in the session, the original variable is replaced and is no longer accessible.</span></span>
<span data-ttu-id="b1746-151">Du kan inte kvalificera en variabel med ett modulnamn.</span><span class="sxs-lookup"><span data-stu-id="b1746-151">You cannot qualify a variable with a module name.</span></span>

<span data-ttu-id="b1746-152">Om du skriver en funktion på kommando raden och sedan importerar en funktion med samma namn, ersätts den ursprungliga funktionen och är inte längre tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="b1746-152">Also, if you type a function at the command line and then import a function with the same name, the original function is replaced and is no longer accessible.</span></span>

### <a name="finding-hidden-commands"></a><span data-ttu-id="b1746-153">Hitta dolda kommandon</span><span class="sxs-lookup"><span data-stu-id="b1746-153">Finding hidden commands</span></span>

<span data-ttu-id="b1746-154">Parametern **all** för cmdleten [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) hämtar alla kommandon med det angivna namnet, även om de är dolda eller ersatta.</span><span class="sxs-lookup"><span data-stu-id="b1746-154">The **All** parameter of the [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet gets all commands with the specified name, even if they are hidden or replaced.</span></span> <span data-ttu-id="b1746-155">Från och med PowerShell 3,0 hämtar som standard `Get-Command` bara de kommandon som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-155">Beginning in PowerShell 3.0, by default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="b1746-156">I följande exempel innehåller sessionen en `Get-Date` funktion och en [Get-date-](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1746-156">In the following examples, the session includes a `Get-Date` function and a [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span></span>

<span data-ttu-id="b1746-157">Följande kommando hämtar det `Get-Date` kommando som körs när du skriver `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="b1746-157">The following command gets the `Get-Date` command that runs when you type `Get-Date`.</span></span>

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

<span data-ttu-id="b1746-158">Följande kommando använder parametern **all** för att hämta alla `Get-Date` kommandon.</span><span class="sxs-lookup"><span data-stu-id="b1746-158">The following command uses the **All** parameter to get all `Get-Date` commands.</span></span>

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a><span data-ttu-id="b1746-159">Köra dolda kommandon</span><span class="sxs-lookup"><span data-stu-id="b1746-159">Running hidden commands</span></span>

<span data-ttu-id="b1746-160">Du kan köra vissa kommandon genom att ange objekt egenskaper som särskiljer kommandot från andra kommandon som kan ha samma namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-160">You can run particular commands by specifying item properties that distinguish the command from other commands that might have the same name.</span></span> <span data-ttu-id="b1746-161">Du kan använda den här metoden för att köra ett kommando, men det är särskilt användbart för att köra dolda kommandon.</span><span class="sxs-lookup"><span data-stu-id="b1746-161">You can use this method to run any command, but it is especially useful for running hidden commands.</span></span>

#### <a name="qualified-names"></a><span data-ttu-id="b1746-162">Kvalificerade namn</span><span class="sxs-lookup"><span data-stu-id="b1746-162">Qualified names</span></span>

<span data-ttu-id="b1746-163">Med hjälp av det module-kvalificerade namnet för en cmdlet kan du köra kommandon som är dolda med ett objekt med samma namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-163">Using the module-qualified name of a cmdlet allows you to run commands hidden by an item with the same name.</span></span> <span data-ttu-id="b1746-164">Du kan till exempel köra `Get-Date` cmdleten genom att kvalificera den med dess Modulnamn **Microsoft. PowerShell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="b1746-164">For example, you can run the `Get-Date` cmdlet by qualifying it with its module name **Microsoft.PowerShell.Utility**.</span></span>

<span data-ttu-id="b1746-165">Använd den här bästa metoden när du skriver skript som du vill distribuera.</span><span class="sxs-lookup"><span data-stu-id="b1746-165">Use this preferred method when writing scripts that you intend to distribute.</span></span> <span data-ttu-id="b1746-166">Du kan inte förutse vilka kommandon som kan finnas i sessionen där skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="b1746-166">You cannot predict which commands might be present in the session in which the script runs.</span></span>

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

<span data-ttu-id="b1746-167">Om du vill köra ett `New-Map` kommando som har lagts till av `MapFunctions` modulen använder du dess kvalificerade namn:</span><span class="sxs-lookup"><span data-stu-id="b1746-167">To run a `New-Map` command that was added by the `MapFunctions` module, use its module-qualified name:</span></span>

```powershell
MapFunctions\New-Map
```

<span data-ttu-id="b1746-168">Om du vill hitta modulen som ett kommando har importer ATS från använder du egenskapen **Modulnamn** för kommandon.</span><span class="sxs-lookup"><span data-stu-id="b1746-168">To find the module from which a command was imported, use the **ModuleName** property of commands.</span></span>

```
(Get-Command <command-name>).ModuleName
```

<span data-ttu-id="b1746-169">Om du till exempel vill hitta källan till `Get-Date` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="b1746-169">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> <span data-ttu-id="b1746-170">Du kan inte kvalificera variabler eller alias.</span><span class="sxs-lookup"><span data-stu-id="b1746-170">You cannot qualify variables or aliases.</span></span>

#### <a name="call-operator"></a><span data-ttu-id="b1746-171">Anrops operator</span><span class="sxs-lookup"><span data-stu-id="b1746-171">Call operator</span></span>

<span data-ttu-id="b1746-172">Du kan också använda `Call` operatorn `&` för att köra dolda kommandon genom att kombinera den med ett anrop till [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (aliaset är "dir") `Get-Command` eller [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).</span><span class="sxs-lookup"><span data-stu-id="b1746-172">You can also use the `Call` operator `&` to run hidden commands by combining it with a call to [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (the alias is "dir"), `Get-Command` or [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

<span data-ttu-id="b1746-173">Anrops operatorn kör strängar och skript block i ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="b1746-173">The call operator executes strings and script blocks in a child scope.</span></span> <span data-ttu-id="b1746-174">Mer information finns i [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="b1746-174">For more information, see [about_Operators](about_Operators.md).</span></span>

<span data-ttu-id="b1746-175">Om du till exempel har en funktion med namnet `Map` som är dold av ett alias som heter `Map` , använder du följande kommando för att köra funktionen.</span><span class="sxs-lookup"><span data-stu-id="b1746-175">For example, if you have a function named `Map` that is hidden by an alias named `Map`, use the following command to run the function.</span></span>

```powershell
&(Get-Command -Name Map -CommandType Function)
```

<span data-ttu-id="b1746-176">eller</span><span class="sxs-lookup"><span data-stu-id="b1746-176">or</span></span>

```powershell
&(dir Function:\map)
```

<span data-ttu-id="b1746-177">Du kan också spara ditt dolda kommando i en variabel för att göra det enklare att köra det.</span><span class="sxs-lookup"><span data-stu-id="b1746-177">You can also save your hidden command in a variable to make it easier to run.</span></span>

<span data-ttu-id="b1746-178">Följande kommando sparar till exempel `Map` funktionen i `$myMap` variabeln och använder sedan `Call` operatorn för att köra den.</span><span class="sxs-lookup"><span data-stu-id="b1746-178">For example, the following command saves the `Map` function in the `$myMap` variable and then uses the `Call` operator to run it.</span></span>

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a><span data-ttu-id="b1746-179">Ersatta objekt</span><span class="sxs-lookup"><span data-stu-id="b1746-179">Replaced items</span></span>

<span data-ttu-id="b1746-180">Ett "ersatt" objekt är ett som du inte längre kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="b1746-180">A "replaced" item is one that you can no longer access.</span></span> <span data-ttu-id="b1746-181">Du kan ersätta objekt genom att importera objekt av samma namn från en modul eller snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="b1746-181">You can replace items by importing items of the same name from a module or snap-in.</span></span>

<span data-ttu-id="b1746-182">Om du till exempel skriver en `Get-Map` funktion i sessionen och du importerar en funktion som kallas `Get-Map` , ersätter den den ursprungliga funktionen.</span><span class="sxs-lookup"><span data-stu-id="b1746-182">For example, if you type a `Get-Map` function in your session, and you import a function called `Get-Map`, it replaces the original function.</span></span> <span data-ttu-id="b1746-183">Det går inte att hämta det i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b1746-183">You cannot retrieve it in the current session.</span></span>

<span data-ttu-id="b1746-184">Det går inte att dölja variabler och alias eftersom du inte kan använda en anrops operator eller ett kvalificerat namn för att köra dem.</span><span class="sxs-lookup"><span data-stu-id="b1746-184">Variables and aliases cannot be hidden because you cannot use a call operator or a qualified name to run them.</span></span> <span data-ttu-id="b1746-185">När du importerar variabler och alias från en modul eller snapin-modul ersätter de variabler i sessionen med samma namn.</span><span class="sxs-lookup"><span data-stu-id="b1746-185">When you import variables and aliases from a module or snap-in, they replace variables in the session with the same name.</span></span>

### <a name="avoiding-name-conflicts"></a><span data-ttu-id="b1746-186">Undvika namn konflikter</span><span class="sxs-lookup"><span data-stu-id="b1746-186">Avoiding name conflicts</span></span>

<span data-ttu-id="b1746-187">Det bästa sättet att hantera kommando namns konflikter är att förhindra dem.</span><span class="sxs-lookup"><span data-stu-id="b1746-187">The best way to manage command name conflicts is to prevent them.</span></span> <span data-ttu-id="b1746-188">Använd ett unikt namn när du namnger kommandona.</span><span class="sxs-lookup"><span data-stu-id="b1746-188">When you name your commands, use a unique name.</span></span> <span data-ttu-id="b1746-189">Du kan till exempel lägga till dina initialer eller företagets namn akronym till substantiven i dina kommandon.</span><span class="sxs-lookup"><span data-stu-id="b1746-189">For example, add your initials or company name acronym to the nouns in your commands.</span></span>

<span data-ttu-id="b1746-190">När du importerar kommandon till din session från en PowerShell-modul eller från en annan session, använder du dessutom `Prefix` parametern för [modulen importera](xref:Microsoft.PowerShell.Core.Import-Module) eller</span><span class="sxs-lookup"><span data-stu-id="b1746-190">Also, when you import commands into your session from a PowerShell module or from another session, use the `Prefix` parameter of the [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) or</span></span>

<span data-ttu-id="b1746-191">[Import-PSSession-](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet: en för att lägga till ett prefix till substantiven i namn på kommandon.</span><span class="sxs-lookup"><span data-stu-id="b1746-191">[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet to add a prefix to the nouns in the names of commands.</span></span>

<span data-ttu-id="b1746-192">Följande kommando undviker till exempel en konflikt med de `Get-Date` och- `Set-Date` cmdletar som medföljer PowerShell när du importerar `DateFunctions` modulen.</span><span class="sxs-lookup"><span data-stu-id="b1746-192">For example, the following command avoids any conflict with the `Get-Date` and `Set-Date` cmdlets that come with PowerShell when you import the `DateFunctions` module.</span></span>

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

<span data-ttu-id="b1746-193">Mer information finns i `Import-Module` och `Import-PSSession` nedan.</span><span class="sxs-lookup"><span data-stu-id="b1746-193">For more information, see `Import-Module` and `Import-PSSession` below.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1746-194">Se även</span><span class="sxs-lookup"><span data-stu-id="b1746-194">See also</span></span>

- [<span data-ttu-id="b1746-195">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="b1746-195">about_Path_Syntax</span></span>](about_Path_Syntax.md)
- [<span data-ttu-id="b1746-196">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="b1746-196">about_Aliases</span></span>](about_Aliases.md)
- [<span data-ttu-id="b1746-197">about_Functions</span><span class="sxs-lookup"><span data-stu-id="b1746-197">about_Functions</span></span>](about_Functions.md)
- [<span data-ttu-id="b1746-198">Alias-Provider</span><span class="sxs-lookup"><span data-stu-id="b1746-198">Alias-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [<span data-ttu-id="b1746-199">Funktion-Provider</span><span class="sxs-lookup"><span data-stu-id="b1746-199">Function-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [<span data-ttu-id="b1746-200">Get-Command</span><span class="sxs-lookup"><span data-stu-id="b1746-200">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="b1746-201">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="b1746-201">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="b1746-202">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="b1746-202">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)
