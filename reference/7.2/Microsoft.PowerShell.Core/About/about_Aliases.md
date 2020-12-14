---
description: Beskriver hur du använder alternativa namn för cmdlets och kommandon i PowerShell.
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: e8b93e2b687e779048784c1eedb15fa53972b8b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94711034"
---
# <a name="about-aliases"></a><span data-ttu-id="a5812-103">Om alias</span><span class="sxs-lookup"><span data-stu-id="a5812-103">About Aliases</span></span>

## <a name="short-description"></a><span data-ttu-id="a5812-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a5812-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a5812-105">Beskriver hur du använder alternativa namn för cmdlets och kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5812-105">Describes how to use alternate names for cmdlets and commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a5812-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a5812-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a5812-107">Ett alias är ett alternativt namn eller smek namn för en cmdlet eller ett kommando element, till exempel en funktion, ett skript, en fil eller en körbar fil.</span><span class="sxs-lookup"><span data-stu-id="a5812-107">An alias is an alternate name or nickname for a cmdlet or for a command element, such as a function, script, file, or executable file.</span></span> <span data-ttu-id="a5812-108">Du kan använda aliaset i stället för kommando namnet i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="a5812-108">You can use the alias instead of the command name in any PowerShell commands.</span></span>

<span data-ttu-id="a5812-109">Använd New-Alias-cmdleten om du vill skapa ett alias.</span><span class="sxs-lookup"><span data-stu-id="a5812-109">To create an alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="a5812-110">Följande kommando skapar till exempel "gasen"-alias för `Get-AuthenticodeSignature` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="a5812-110">For example, the following command creates the "gas" alias for the `Get-AuthenticodeSignature` cmdlet:</span></span>

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

<span data-ttu-id="a5812-111">När du har skapat aliaset för cmdlet-namnet kan du använda aliaset i stället för namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5812-111">After you create the alias for the cmdlet name, you can use the alias instead of the cmdlet name.</span></span> <span data-ttu-id="a5812-112">Om du till exempel vill hämta Authenticode-signaturen för SqlScript.ps1-filen skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-112">For example, to get the Authenticode signature for the SqlScript.ps1 file, type:</span></span>

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

<span data-ttu-id="a5812-113">Eller skriv:</span><span class="sxs-lookup"><span data-stu-id="a5812-113">Or, type:</span></span>

```powershell
gas SqlScript.ps1
```

<span data-ttu-id="a5812-114">Om du skapar "Word" som alias för Microsoft Office Word kan du skriva "Word" i stället för följande:</span><span class="sxs-lookup"><span data-stu-id="a5812-114">If you create "word" as the alias for Microsoft Office Word, you can type "word" instead of the following:</span></span>

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a><span data-ttu-id="a5812-115">INBYGGDA ALIAS</span><span class="sxs-lookup"><span data-stu-id="a5812-115">BUILT-IN ALIASES</span></span>

<span data-ttu-id="a5812-116">PowerShell innehåller en uppsättning inbyggda alias, inklusive "CD" och "chdir" för Set-Location-cmdleten och "LS" och "dir" för Get-ChildItem-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5812-116">PowerShell includes a set of built-in aliases, including "cd" and "chdir" for the Set-Location cmdlet, and "ls" and "dir" for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="a5812-117">Om du vill hämta alla alias på datorn, inklusive inbyggda alias, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-117">To get all the aliases on the computer, including the built-in aliases, type:</span></span>

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a><span data-ttu-id="a5812-118">ALIAS-CMDLETAR</span><span class="sxs-lookup"><span data-stu-id="a5812-118">ALIAS CMDLETS</span></span>

<span data-ttu-id="a5812-119">PowerShell innehåller följande cmdletar, som är utformade för att fungera med alias:</span><span class="sxs-lookup"><span data-stu-id="a5812-119">PowerShell includes the following cmdlets, which are designed for working with aliases:</span></span>

- <span data-ttu-id="a5812-120">`Get-Alias` -Hämtar alla alias i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a5812-120">`Get-Alias` - Gets all the aliases in the current session.</span></span>
- <span data-ttu-id="a5812-121">`New-Alias` -Skapar ett nytt alias.</span><span class="sxs-lookup"><span data-stu-id="a5812-121">`New-Alias` - Creates a new alias.</span></span>
- <span data-ttu-id="a5812-122">`Set-Alias` -Skapar eller ändrar ett alias.</span><span class="sxs-lookup"><span data-stu-id="a5812-122">`Set-Alias` - Creates or changes an alias.</span></span>
- <span data-ttu-id="a5812-123">`Export-Alias` -Exporterar ett eller flera alias till en fil.</span><span class="sxs-lookup"><span data-stu-id="a5812-123">`Export-Alias` - Exports one or more aliases to a file.</span></span>
- <span data-ttu-id="a5812-124">`Import-Alias` – Importerar en aliasresurspost till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5812-124">`Import-Alias` - Imports an alias file into PowerShell.</span></span>

<span data-ttu-id="a5812-125">Om du vill ha detaljerad information om cmdletarna skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-125">For detailed information about the cmdlets, type:</span></span>

```powershell
Get-Help <cmdlet-Name> -Detailed
```

<span data-ttu-id="a5812-126">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="a5812-126">For example, type:</span></span>

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a><span data-ttu-id="a5812-127">SKAPA ETT ALIAS</span><span class="sxs-lookup"><span data-stu-id="a5812-127">CREATING AN ALIAS</span></span>

<span data-ttu-id="a5812-128">Använd New-Alias-cmdleten om du vill skapa ett nytt alias.</span><span class="sxs-lookup"><span data-stu-id="a5812-128">To create a new alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="a5812-129">Om du till exempel vill skapa aliaset "förnamn" för Get-Help skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-129">For example, to create the "gh" alias for Get-Help, type:</span></span>

```powershell
New-Alias -Name gh -Value Get-Help
```

<span data-ttu-id="a5812-130">Du kan använda aliaset i kommandon, precis som du använder det fullständiga cmdlet-namnet, och du kan använda aliaset med parametrarna.</span><span class="sxs-lookup"><span data-stu-id="a5812-130">You can use the alias in commands, just as you would use the full cmdlet name, and you can use the alias with parameters.</span></span>

<span data-ttu-id="a5812-131">Om du till exempel vill få detaljerad hjälp för Get-WmiObject-cmdlet skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-131">For example, to get detailed Help for the Get-WmiObject cmdlet, type:</span></span>

```powershell
Get-Help Get-WmiObject -Detailed
```

<span data-ttu-id="a5812-132">Eller skriv:</span><span class="sxs-lookup"><span data-stu-id="a5812-132">Or, type:</span></span>

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a><span data-ttu-id="a5812-133">SPARAR ALIAS</span><span class="sxs-lookup"><span data-stu-id="a5812-133">SAVING ALIASES</span></span>

<span data-ttu-id="a5812-134">De alias som du skapar sparas bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a5812-134">The aliases that you create are saved only in the current session.</span></span> <span data-ttu-id="a5812-135">Om du vill använda alias i en annan session lägger du till aliaset i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="a5812-135">To use the aliases in a different session, add the alias to your PowerShell profile.</span></span> <span data-ttu-id="a5812-136">Du kan också använda Export-Alias cmdlet för att spara alias till en fil.</span><span class="sxs-lookup"><span data-stu-id="a5812-136">Or, use the Export-Alias cmdlet to save the aliases to a file.</span></span>

<span data-ttu-id="a5812-137">Om du vill ha mer information skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-137">For more information, type:</span></span>

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a><span data-ttu-id="a5812-138">HÄMTAR ALIAS</span><span class="sxs-lookup"><span data-stu-id="a5812-138">GETTING ALIASES</span></span>

<span data-ttu-id="a5812-139">Om du vill hämta alla alias i den aktuella sessionen, inklusive inbyggda alias, alias i dina PowerShell-profiler och de alias som du har skapat i den aktuella sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-139">To get all the aliases in the current session, including the built-in aliases, the aliases in your PowerShell profiles, and the aliases that you have created in the current session, type:</span></span>

```powershell
Get-Alias
```

<span data-ttu-id="a5812-140">Om du vill hämta särskilda alias använder du parametern name i Get-Alias-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5812-140">To get particular aliases, use the Name parameter of the Get-Alias cmdlet.</span></span> <span data-ttu-id="a5812-141">Om du till exempel vill hämta alias som börjar med "p" skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-141">For example, to get aliases that begin with "p", type:</span></span>

```powershell
Get-Alias -Name p*
```

<span data-ttu-id="a5812-142">Använd definitions parametern för att hämta alias för ett visst objekt.</span><span class="sxs-lookup"><span data-stu-id="a5812-142">To get the aliases for a particular item, use the Definition parameter.</span></span> <span data-ttu-id="a5812-143">Till exempel för att hämta alias för Get-ChildItem cmdlet-typ:</span><span class="sxs-lookup"><span data-stu-id="a5812-143">For example, to get the aliases for the Get-ChildItem cmdlet type:</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a><span data-ttu-id="a5812-144">GET-ALIAS FÖR UTDATA</span><span class="sxs-lookup"><span data-stu-id="a5812-144">GET-ALIAS OUTPUT</span></span>

<span data-ttu-id="a5812-145">Get-Alias returnerar endast en typ av objekt, ett AliasInfo-objekt (system. Management. Automation. AliasInfo).</span><span class="sxs-lookup"><span data-stu-id="a5812-145">Get-Alias returns only one type of object, an AliasInfo object (System.Management.Automation.AliasInfo).</span></span> <span data-ttu-id="a5812-146">Namnet på alias som inte innehåller något bindestreck, till exempel "CD", visas i följande format:</span><span class="sxs-lookup"><span data-stu-id="a5812-146">The name of aliases that don't include a hyphen, such as "cd" are displayed in the following format:</span></span>

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

<span data-ttu-id="a5812-147">Detta gör det mycket snabbt och enkelt att få den information som du behöver.</span><span class="sxs-lookup"><span data-stu-id="a5812-147">This makes it very quick and easy to get the information that you need.</span></span>

<span data-ttu-id="a5812-148">Formatet för den pilbaserade aliaset används inte för alias som innehåller bindestreck.</span><span class="sxs-lookup"><span data-stu-id="a5812-148">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="a5812-149">Detta är sannolikt att föredra ersättnings namn för cmdlets och functions, i stället för vanliga förkortningar eller smek namn, och författaren kanske inte vill att de ska vara så tydliga.</span><span class="sxs-lookup"><span data-stu-id="a5812-149">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames, and the author might not want them to be as evident.</span></span>

## <a name="alternate-names-for-commands-with-parameters"></a><span data-ttu-id="a5812-150">ALTERNATIVA NAMN FÖR KOMMANDON MED PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a5812-150">ALTERNATE NAMES FOR COMMANDS WITH PARAMETERS</span></span>

<span data-ttu-id="a5812-151">Du kan tilldela ett alias till en cmdlet, ett skript, en funktion eller en körbar fil.</span><span class="sxs-lookup"><span data-stu-id="a5812-151">You can assign an alias to a cmdlet, script, function, or executable file.</span></span> <span data-ttu-id="a5812-152">Du kan inte tilldela ett alias till ett kommando och dess parametrar.</span><span class="sxs-lookup"><span data-stu-id="a5812-152">You cannot assign an alias to a command and its parameters.</span></span> <span data-ttu-id="a5812-153">Du kan till exempel tilldela ett alias till `Get-Eventlog` cmdleten, men du kan inte tilldela ett alias till `Get-Eventlog -LogName System` kommandot.</span><span class="sxs-lookup"><span data-stu-id="a5812-153">For example, you can assign an alias to the `Get-Eventlog` cmdlet, but you cannot assign an alias to the `Get-Eventlog -LogName System` command.</span></span>

<span data-ttu-id="a5812-154">Du kan skapa en funktion som innehåller kommandot.</span><span class="sxs-lookup"><span data-stu-id="a5812-154">You can create a function that includes the command.</span></span> <span data-ttu-id="a5812-155">Om du vill skapa en funktion skriver du ordet "function" följt av ett namn för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a5812-155">To create a function, type the word "function" followed by a name for the function.</span></span> <span data-ttu-id="a5812-156">Skriv kommandot och omge det med klammerparenteser ( {} ).</span><span class="sxs-lookup"><span data-stu-id="a5812-156">Type the command, and enclose it in braces ({}).</span></span>

<span data-ttu-id="a5812-157">Till exempel skapar följande kommando syslog-funktionen.</span><span class="sxs-lookup"><span data-stu-id="a5812-157">For example, the following command creates the syslog function.</span></span> <span data-ttu-id="a5812-158">Den här funktionen representerar `Get-Eventlog -LogName System` kommandot:</span><span class="sxs-lookup"><span data-stu-id="a5812-158">This function represents the `Get-Eventlog -LogName System` command:</span></span>

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

<span data-ttu-id="a5812-159">Nu kan du skriva "syslog" i stället för kommandot.</span><span class="sxs-lookup"><span data-stu-id="a5812-159">You can now type "syslog" instead of the command.</span></span> <span data-ttu-id="a5812-160">Du kan också skapa alias för den nya funktionen.</span><span class="sxs-lookup"><span data-stu-id="a5812-160">And, you can create aliases for the new function.</span></span>

<span data-ttu-id="a5812-161">Om du vill ha mer information om funktioner skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-161">For more information about functions, type:</span></span>

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a><span data-ttu-id="a5812-162">ALIAS-OBJEKT</span><span class="sxs-lookup"><span data-stu-id="a5812-162">ALIAS OBJECTS</span></span>

<span data-ttu-id="a5812-163">PowerShell-alias representeras av objekt som är instanser av klassen system. Management. Automation. AliasInfo.</span><span class="sxs-lookup"><span data-stu-id="a5812-163">PowerShell aliases are represented by objects that are instances of the System.Management.Automation.AliasInfo class.</span></span> <span data-ttu-id="a5812-164">Mer information om den här typen av objekt finns i [AliasInfo-klassen][aliasinfo] i PowerShell SDK.</span><span class="sxs-lookup"><span data-stu-id="a5812-164">For more information about this type of object, see [AliasInfo Class][aliasinfo] in the PowerShell SDK.</span></span>

<span data-ttu-id="a5812-165">Hämta aliasen om du vill visa egenskaper och metoder för alias-objekten.</span><span class="sxs-lookup"><span data-stu-id="a5812-165">To view the properties and methods of the alias objects, get the aliases.</span></span>
<span data-ttu-id="a5812-166">Sedan kan du skicka vidare till Get-Member-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="a5812-166">Then, pipe them to the Get-Member cmdlet.</span></span> <span data-ttu-id="a5812-167">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a5812-167">For example:</span></span>

```powershell
Get-Alias | Get-Member
```

<span data-ttu-id="a5812-168">Om du vill visa värdena för egenskaperna för ett speciellt alias, till exempel `dir` alias, hämtar du aliaset.</span><span class="sxs-lookup"><span data-stu-id="a5812-168">To view the values of the properties of a specific alias, such as the `dir` alias, get the alias.</span></span> <span data-ttu-id="a5812-169">Sedan går du till den Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5812-169">Then, pipe it to the Format-List cmdlet.</span></span> <span data-ttu-id="a5812-170">Följande kommando hämtar till exempel "dir"-aliaset.</span><span class="sxs-lookup"><span data-stu-id="a5812-170">For example, the following command gets the "dir" alias.</span></span> <span data-ttu-id="a5812-171">Därefter rör kommandot aliaset till Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5812-171">Next, the command pipes the alias to the Format-List cmdlet.</span></span> <span data-ttu-id="a5812-172">Sedan använder kommandot egenskaps parametern för Format-List med ett jokertecken ( \* ) för att visa alla egenskaper för `dir` aliaset.</span><span class="sxs-lookup"><span data-stu-id="a5812-172">Then, the command uses the Property parameter of Format-List with a wildcard character (\*) to display all the properties of the `dir` alias.</span></span> <span data-ttu-id="a5812-173">Följande kommando utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="a5812-173">The following command performs these tasks:</span></span>

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a><span data-ttu-id="a5812-174">PowerShell-ALIASRESURSPOST</span><span class="sxs-lookup"><span data-stu-id="a5812-174">PowerShell ALIAS PROVIDER</span></span>

<span data-ttu-id="a5812-175">PowerShell inkluderar alias-providern.</span><span class="sxs-lookup"><span data-stu-id="a5812-175">PowerShell includes the Alias provider.</span></span> <span data-ttu-id="a5812-176">Med hjälp av Ali Aset providern kan du Visa alias i PowerShell som om de fanns på en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="a5812-176">The Alias provider lets you view the aliases in PowerShell as though they were on a file system drive.</span></span>

<span data-ttu-id="a5812-177">Ali Aset-providern visar aliaset: Drive.</span><span class="sxs-lookup"><span data-stu-id="a5812-177">The Alias provider exposes the Alias: drive.</span></span> <span data-ttu-id="a5812-178">För att gå till aliaset: enhet, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-178">To go into the Alias: drive, type:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="a5812-179">Om du vill visa innehållet i enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-179">To view the contents of the drive, type:</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="a5812-180">Om du vill visa innehållet i enheten från en annan PowerShell-enhet börjar du med sökvägen med enhets namnet.</span><span class="sxs-lookup"><span data-stu-id="a5812-180">To view the contents of the drive from another PowerShell drive, begin the path with the drive name.</span></span> <span data-ttu-id="a5812-181">Inkludera kolon (:).</span><span class="sxs-lookup"><span data-stu-id="a5812-181">Include the colon (:).</span></span> <span data-ttu-id="a5812-182">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a5812-182">For example:</span></span>

```powershell
Get-ChildItem -Path Alias:
```

<span data-ttu-id="a5812-183">Om du vill hämta information om ett visst alias, anger du enhets namn och aliasnamn.</span><span class="sxs-lookup"><span data-stu-id="a5812-183">To get information about a particular alias, type the drive name and the alias name.</span></span> <span data-ttu-id="a5812-184">Eller Skriv ett namn mönster.</span><span class="sxs-lookup"><span data-stu-id="a5812-184">Or, type a name pattern.</span></span> <span data-ttu-id="a5812-185">Om du till exempel vill hämta alla alias som börjar med "p" skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-185">For example, to get all the aliases that begin with "p", type:</span></span>

```powershell
Get-ChildItem -Path Alias:p*
```

<span data-ttu-id="a5812-186">Om du vill ha mer information om PowerShell-Aliern skriver du:</span><span class="sxs-lookup"><span data-stu-id="a5812-186">For more information about the PowerShell Alias provider, type:</span></span>

```powershell
Get-Help Alias
```

## <a name="see-also"></a><span data-ttu-id="a5812-187">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a5812-187">SEE ALSO</span></span>

- [<span data-ttu-id="a5812-188">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="a5812-188">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="a5812-189">Get-alias</span><span class="sxs-lookup"><span data-stu-id="a5812-189">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="a5812-190">Set-alias</span><span class="sxs-lookup"><span data-stu-id="a5812-190">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [<span data-ttu-id="a5812-191">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="a5812-191">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="a5812-192">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="a5812-192">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="a5812-193">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a5812-193">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [<span data-ttu-id="a5812-194">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a5812-194">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="a5812-195">about_functions</span><span class="sxs-lookup"><span data-stu-id="a5812-195">about_functions</span></span>](about_functions.md)
- [<span data-ttu-id="a5812-196">about_profiles</span><span class="sxs-lookup"><span data-stu-id="a5812-196">about_profiles</span></span>](about_profiles.md)
- [<span data-ttu-id="a5812-197">about_providers</span><span class="sxs-lookup"><span data-stu-id="a5812-197">about_providers</span></span>](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
