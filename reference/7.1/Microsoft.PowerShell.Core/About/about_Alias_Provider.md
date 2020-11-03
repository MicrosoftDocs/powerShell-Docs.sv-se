---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Aliasresurspost
ms.openlocfilehash: 8edd1a406862e6bf1dcbc5e8215b60c93ac7b13f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271742"
---
# <a name="alias-provider"></a><span data-ttu-id="077d9-104">Aliasresurspost</span><span class="sxs-lookup"><span data-stu-id="077d9-104">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="077d9-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="077d9-105">Provider name</span></span>
<span data-ttu-id="077d9-106">Alias</span><span class="sxs-lookup"><span data-stu-id="077d9-106">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="077d9-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="077d9-107">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="077d9-108">Funktioner</span><span class="sxs-lookup"><span data-stu-id="077d9-108">Capabilities</span></span>

<span data-ttu-id="077d9-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="077d9-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="077d9-110">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="077d9-110">Short description</span></span>

<span data-ttu-id="077d9-111">Ger åtkomst till PowerShell-alias och de värden som de representerar.</span><span class="sxs-lookup"><span data-stu-id="077d9-111">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="077d9-112">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="077d9-112">Detailed description</span></span>

<span data-ttu-id="077d9-113">Med PowerShell- **Ali** -leverantören kan du hämta, lägga till, ändra, radera och ta bort alias i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="077d9-113">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="077d9-114">Ett alias är ett alternativt namn för en cmdlet, Function, körbar fil, inklusive skript.</span><span class="sxs-lookup"><span data-stu-id="077d9-114">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="077d9-115">PowerShell innehåller en uppsättning inbyggda alias.</span><span class="sxs-lookup"><span data-stu-id="077d9-115">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="077d9-116">Du kan lägga till egna alias till den aktuella sessionen och till din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="077d9-116">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="077d9-117">**Ali Aset** är ett platt namn område som bara innehåller Ali-objekten.</span><span class="sxs-lookup"><span data-stu-id="077d9-117">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="077d9-118">Aliasen har inga underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="077d9-118">The aliases have no child items.</span></span>

<span data-ttu-id="077d9-119">**Alias** -providern stöder följande cmdlets, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="077d9-119">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="077d9-120">Get-location</span><span class="sxs-lookup"><span data-stu-id="077d9-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="077d9-121">Ange plats</span><span class="sxs-lookup"><span data-stu-id="077d9-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="077d9-122">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="077d9-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="077d9-123">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="077d9-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="077d9-124">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="077d9-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="077d9-125">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="077d9-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="077d9-126">PowerShell innehåller en uppsättning cmdletar som är utformade för att visa och ändra alias.</span><span class="sxs-lookup"><span data-stu-id="077d9-126">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="077d9-127">När du använder **alias** -cmdletar behöver du inte ange `Alias:` enheten i namnet.</span><span class="sxs-lookup"><span data-stu-id="077d9-127">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="077d9-128">Den här artikeln beskriver inte hur du arbetar med **alias** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="077d9-128">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="077d9-129">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="077d9-129">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="077d9-130">Get-alias</span><span class="sxs-lookup"><span data-stu-id="077d9-130">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="077d9-131">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="077d9-131">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="077d9-132">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="077d9-132">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="077d9-133">Set-alias</span><span class="sxs-lookup"><span data-stu-id="077d9-133">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="077d9-134">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="077d9-134">Types exposed by this provider</span></span>

<span data-ttu-id="077d9-135">Varje alias är en instans av klassen [system. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .</span><span class="sxs-lookup"><span data-stu-id="077d9-135">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="077d9-136">Navigera mellan Ali medie enheten</span><span class="sxs-lookup"><span data-stu-id="077d9-136">Navigating the Alias drive</span></span>

<span data-ttu-id="077d9-137">**Ali Aset** visar data lagret i `Alias:` enheten.</span><span class="sxs-lookup"><span data-stu-id="077d9-137">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="077d9-138">Om du vill arbeta med alias kan du ändra din plats till `Alias:` enheten med hjälp av följande kommando:</span><span class="sxs-lookup"><span data-stu-id="077d9-138">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="077d9-139">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="077d9-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="077d9-140">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="077d9-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="077d9-141">Du kan också arbeta med Ali Aset provider från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="077d9-141">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="077d9-142">Om du vill referera till ett alias från en annan plats använder du `Alias:` enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="077d9-142">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="077d9-143">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="077d9-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="077d9-144">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="077d9-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="077d9-145">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="077d9-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="077d9-146">Visar innehållet i aliaset: enhet</span><span class="sxs-lookup"><span data-stu-id="077d9-146">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="077d9-147">Det här kommandot hämtar listan över alla alias när den aktuella platsen är `Alias:` enheten.</span><span class="sxs-lookup"><span data-stu-id="077d9-147">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="077d9-148">Ett jokertecken används `*` för att ange allt innehåll på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="077d9-148">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="077d9-149">I `Alias:` enheten, en punkt `.` som representerar den aktuella platsen och ett jokertecken `*` , som representerar alla objekt på den aktuella platsen, har samma resultat.</span><span class="sxs-lookup"><span data-stu-id="077d9-149">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="077d9-150">Till exempel `Get-Item -Path .` eller `Get-Item \*` skapa samma resultat.</span><span class="sxs-lookup"><span data-stu-id="077d9-150">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="077d9-151">Ali Aset-providern har inga behållare, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="077d9-151">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="077d9-152">Hämta ett markerat alias</span><span class="sxs-lookup"><span data-stu-id="077d9-152">Get a selected alias</span></span>

<span data-ttu-id="077d9-153">Det här kommandot hämtar `ls` aliaset.</span><span class="sxs-lookup"><span data-stu-id="077d9-153">This command gets the `ls` alias.</span></span>
<span data-ttu-id="077d9-154">Eftersom det innehåller sökvägen kan du använda den på valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="077d9-154">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="077d9-155">Om du är i `Alias:` enheten kan du utelämna enhets namnet från sökvägen.</span><span class="sxs-lookup"><span data-stu-id="077d9-155">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="077d9-156">Du kan också hämta definitionen för ett alias genom att förlösa providerns sökväg med dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="077d9-156">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="077d9-157">Hämta alla alias för en angiven cmdlet</span><span class="sxs-lookup"><span data-stu-id="077d9-157">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="077d9-158">Det här kommandot hämtar en lista över de alias som är associerade med `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="077d9-158">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="077d9-159">Den använder **definitions** egenskapen som lagrar cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="077d9-159">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="077d9-160">Skapa alias</span><span class="sxs-lookup"><span data-stu-id="077d9-160">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="077d9-161">Skapa ett alias från aliaset: enhet</span><span class="sxs-lookup"><span data-stu-id="077d9-161">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="077d9-162">Det här kommandot skapar `serv` aliaset för `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="077d9-162">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="077d9-163">Eftersom den aktuella platsen finns i `Alias:` enheten `-Path` behövs ingen parameter.</span><span class="sxs-lookup"><span data-stu-id="077d9-163">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="077d9-164">Det här kommandot använder också den `-Options` dynamiska parametern för att ange alternativet **AllScope** i aliaset.</span><span class="sxs-lookup"><span data-stu-id="077d9-164">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="077d9-165">`-Options`Parametern är bara tillgänglig i `New-Item` cmdleten när du befinner dig i `Alias:` enheten.</span><span class="sxs-lookup"><span data-stu-id="077d9-165">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="077d9-166">Punkten ( `.` ) visar den aktuella katalogen, som är Ali Aset.</span><span class="sxs-lookup"><span data-stu-id="077d9-166">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="077d9-167">Skapa ett alias med en absolut sökväg</span><span class="sxs-lookup"><span data-stu-id="077d9-167">Create an alias with an absolute path</span></span>

<span data-ttu-id="077d9-168">Du kan skapa ett alias för alla objekt som anropar ett kommando.</span><span class="sxs-lookup"><span data-stu-id="077d9-168">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="077d9-169">Det här kommandot skapar `np` alias för `Notepad.exe` .</span><span class="sxs-lookup"><span data-stu-id="077d9-169">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="077d9-170">Skapa ett alias för en ny funktion</span><span class="sxs-lookup"><span data-stu-id="077d9-170">Create an alias to a new function</span></span>

<span data-ttu-id="077d9-171">Du kan skapa ett alias för vilken funktion som helst.</span><span class="sxs-lookup"><span data-stu-id="077d9-171">You can create an alias for any function.</span></span> <span data-ttu-id="077d9-172">Du kan använda den här funktionen för att skapa ett alias som innehåller både en cmdlet och dess parametrar.</span><span class="sxs-lookup"><span data-stu-id="077d9-172">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="077d9-173">Det första kommandot skapar `CD32` funktionen, som ändrar den aktuella katalogen till `System32` katalogen.</span><span class="sxs-lookup"><span data-stu-id="077d9-173">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="077d9-174">Det andra kommandot skapar `go` aliaset för `CD32` funktionen.</span><span class="sxs-lookup"><span data-stu-id="077d9-174">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="077d9-175">När kommandot har slutförts kan du använda antingen `CD32` eller `go` för att anropa funktionen.</span><span class="sxs-lookup"><span data-stu-id="077d9-175">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="077d9-176">Ändra alias</span><span class="sxs-lookup"><span data-stu-id="077d9-176">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="077d9-177">Ändra alternativen för ett alias</span><span class="sxs-lookup"><span data-stu-id="077d9-177">Change the options of an alias</span></span>

<span data-ttu-id="077d9-178">Du kan använda `Set-Item` cmdleten med den `-Options` dynamiska parametern för att ändra värdet för `-Options` egenskapen för ett alias.</span><span class="sxs-lookup"><span data-stu-id="077d9-178">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="077d9-179">Det här kommandot anger **AllScope** och **ReadOnly** -alternativen för `dir` aliaset.</span><span class="sxs-lookup"><span data-stu-id="077d9-179">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="077d9-180">Kommandot använder `-Options` `Set-Item` cmdletens dynamiska parameter.</span><span class="sxs-lookup"><span data-stu-id="077d9-180">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="077d9-181">`-Options`Parametern är tillgänglig i `Set-Item` när du använder den med **alias** -eller **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="077d9-181">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="077d9-182">Ändra ett alias som refereras till kommandot</span><span class="sxs-lookup"><span data-stu-id="077d9-182">Change an aliases referenced command</span></span>

<span data-ttu-id="077d9-183">Detta kommando använder `Set-Item` cmdleten för att ändra `gp` alias så att det representerar `Get-Process` cmdleten i stället för `Get-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="077d9-183">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="077d9-184">`-Force`Parametern är obligatorisk eftersom värdet på egenskapen **alternativ** för `gp` aliaset är inställt på `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="077d9-184">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="077d9-185">Eftersom kommandot skickas inifrån `Alias:` enheten, anges inte enheten i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="077d9-185">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="077d9-186">Ändringen påverkar de fyra egenskaperna som definierar associationen mellan aliaset och kommandot.</span><span class="sxs-lookup"><span data-stu-id="077d9-186">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="077d9-187">Skriv följande kommando om du vill visa ändrings resultatet:</span><span class="sxs-lookup"><span data-stu-id="077d9-187">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="077d9-188">Byta namn på ett alias</span><span class="sxs-lookup"><span data-stu-id="077d9-188">Rename an alias</span></span>

<span data-ttu-id="077d9-189">Det här kommandot använder `Rename-Item` cmdleten för att ändra `popd` aliaset till `pop` .</span><span class="sxs-lookup"><span data-stu-id="077d9-189">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="077d9-190">Kopierar ett alias</span><span class="sxs-lookup"><span data-stu-id="077d9-190">Copying an alias</span></span>

<span data-ttu-id="077d9-191">Det här kommandot kopierar `pushd` aliaset så att ett nytt `push` alias skapas för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="077d9-191">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="077d9-192">När det nya aliaset skapas har egenskapen **Description** värdet null.</span><span class="sxs-lookup"><span data-stu-id="077d9-192">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="077d9-193">Och dess **alternativ** egenskap har värdet `None` .</span><span class="sxs-lookup"><span data-stu-id="077d9-193">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="077d9-194">Om kommandot utfärdas inifrån `Alias:` enheten kan du utelämna enhets namnet från `-Path` parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="077d9-194">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="077d9-195">Tar bort ett alias</span><span class="sxs-lookup"><span data-stu-id="077d9-195">Deleting an alias</span></span>

<span data-ttu-id="077d9-196">Det här kommandot tar bort `serv` aliaset från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="077d9-196">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="077d9-197">Du kan använda det här kommandot i valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="077d9-197">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="077d9-198">Det här kommandot tar bort alias som börjar med "s".</span><span class="sxs-lookup"><span data-stu-id="077d9-198">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="077d9-199">Det tar inte bort skrivskyddade alias.</span><span class="sxs-lookup"><span data-stu-id="077d9-199">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="077d9-200">Ta bort skrivskyddade alias</span><span class="sxs-lookup"><span data-stu-id="077d9-200">Delete read-only aliases</span></span>

<span data-ttu-id="077d9-201">Det här kommandot tar bort alla alias från den aktuella sessionen, förutom de med värdet `Constant` för egenskapen **Options** .</span><span class="sxs-lookup"><span data-stu-id="077d9-201">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="077d9-202">`-Force`Parametern tillåter kommandot att ta bort alias vars **alternativ** egenskap har värdet `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="077d9-202">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="077d9-203">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="077d9-203">Dynamic parameters</span></span>

<span data-ttu-id="077d9-204">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="077d9-204">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="077d9-205">Alternativ [system. Management. Automation. ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="077d9-205">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="077d9-206">Anger värdet för egenskapen **Options** för ett alias.</span><span class="sxs-lookup"><span data-stu-id="077d9-206">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="077d9-207">**Ingen** : inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="077d9-207">**None** : No options.</span></span> <span data-ttu-id="077d9-208">Detta värde är standard.</span><span class="sxs-lookup"><span data-stu-id="077d9-208">This value is the default.</span></span>
- <span data-ttu-id="077d9-209">**Konstant** : det går inte att ta bort aliaset och dess egenskaper kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="077d9-209">**Constant** :The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="077d9-210">**Konstant** är endast tillgängligt när du skapar ett alias.</span><span class="sxs-lookup"><span data-stu-id="077d9-210">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="077d9-211">Det går inte att ändra alternativet för ett befintligt alias till **konstant**.</span><span class="sxs-lookup"><span data-stu-id="077d9-211">You cannot change the option of an existing alias to **Constant**.</span></span>
- <span data-ttu-id="077d9-212">**Privat** : aliaset är endast synligt i det aktuella omfånget, inte i de underordnade omfången.</span><span class="sxs-lookup"><span data-stu-id="077d9-212">**Private** :The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="077d9-213">**ReadOnly** : egenskaperna för aliaset kan inte ändras förutom genom att använda `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="077d9-213">**ReadOnly** :The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="077d9-214">Du kan använda `Remove-Item` för att ta bort aliaset.</span><span class="sxs-lookup"><span data-stu-id="077d9-214">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="077d9-215">**AllScope** : aliaset kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="077d9-215">**AllScope** :The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="077d9-216">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="077d9-216">Cmdlets supported</span></span>

- [<span data-ttu-id="077d9-217">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="077d9-217">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="077d9-218">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="077d9-218">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="077d9-219">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="077d9-219">Using the pipeline</span></span>

<span data-ttu-id="077d9-220">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="077d9-220">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="077d9-221">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="077d9-221">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="077d9-222">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="077d9-222">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="077d9-223">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="077d9-223">Getting help</span></span>

<span data-ttu-id="077d9-224">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="077d9-224">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="077d9-225">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="077d9-225">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="077d9-226">Se även</span><span class="sxs-lookup"><span data-stu-id="077d9-226">See also</span></span>

[<span data-ttu-id="077d9-227">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="077d9-227">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="077d9-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="077d9-228">about_Providers</span></span>](../About/about_Providers.md)

