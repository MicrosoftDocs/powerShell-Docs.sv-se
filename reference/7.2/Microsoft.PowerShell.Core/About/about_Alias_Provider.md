---
description: Alias
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Aliasresurspost
ms.openlocfilehash: d6bfbaf878a6d971b1e01d963faec8c8ece5d1fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710723"
---
# <a name="alias-provider"></a><span data-ttu-id="a0253-103">Aliasresurspost</span><span class="sxs-lookup"><span data-stu-id="a0253-103">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="a0253-104">Providernamn</span><span class="sxs-lookup"><span data-stu-id="a0253-104">Provider name</span></span>
<span data-ttu-id="a0253-105">Alias</span><span class="sxs-lookup"><span data-stu-id="a0253-105">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="a0253-106">Enheter</span><span class="sxs-lookup"><span data-stu-id="a0253-106">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="a0253-107">Funktioner</span><span class="sxs-lookup"><span data-stu-id="a0253-107">Capabilities</span></span>

<span data-ttu-id="a0253-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="a0253-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="a0253-109">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0253-109">Short description</span></span>

<span data-ttu-id="a0253-110">Ger åtkomst till PowerShell-alias och de värden som de representerar.</span><span class="sxs-lookup"><span data-stu-id="a0253-110">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="a0253-111">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0253-111">Detailed description</span></span>

<span data-ttu-id="a0253-112">Med PowerShell- **Ali** -leverantören kan du hämta, lägga till, ändra, radera och ta bort alias i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0253-112">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="a0253-113">Ett alias är ett alternativt namn för en cmdlet, Function, körbar fil, inklusive skript.</span><span class="sxs-lookup"><span data-stu-id="a0253-113">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="a0253-114">PowerShell innehåller en uppsättning inbyggda alias.</span><span class="sxs-lookup"><span data-stu-id="a0253-114">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="a0253-115">Du kan lägga till egna alias till den aktuella sessionen och till din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="a0253-115">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="a0253-116">**Ali Aset** är ett platt namn område som bara innehåller Ali-objekten.</span><span class="sxs-lookup"><span data-stu-id="a0253-116">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="a0253-117">Aliasen har inga underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="a0253-117">The aliases have no child items.</span></span>

<span data-ttu-id="a0253-118">**Alias** -providern stöder följande cmdlets, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="a0253-118">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="a0253-119">Get-location</span><span class="sxs-lookup"><span data-stu-id="a0253-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="a0253-120">Ange plats</span><span class="sxs-lookup"><span data-stu-id="a0253-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="a0253-121">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="a0253-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="a0253-122">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="a0253-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="a0253-123">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="a0253-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="a0253-124">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="a0253-124">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="a0253-125">PowerShell innehåller en uppsättning cmdletar som är utformade för att visa och ändra alias.</span><span class="sxs-lookup"><span data-stu-id="a0253-125">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="a0253-126">När du använder **alias** -cmdletar behöver du inte ange `Alias:` enheten i namnet.</span><span class="sxs-lookup"><span data-stu-id="a0253-126">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="a0253-127">Den här artikeln beskriver inte hur du arbetar med **alias** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a0253-127">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="a0253-128">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="a0253-128">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="a0253-129">Get-alias</span><span class="sxs-lookup"><span data-stu-id="a0253-129">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="a0253-130">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="a0253-130">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="a0253-131">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="a0253-131">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="a0253-132">Set-alias</span><span class="sxs-lookup"><span data-stu-id="a0253-132">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="a0253-133">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="a0253-133">Types exposed by this provider</span></span>

<span data-ttu-id="a0253-134">Varje alias är en instans av klassen [system. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .</span><span class="sxs-lookup"><span data-stu-id="a0253-134">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="a0253-135">Navigera mellan Ali medie enheten</span><span class="sxs-lookup"><span data-stu-id="a0253-135">Navigating the Alias drive</span></span>

<span data-ttu-id="a0253-136">**Ali Aset** visar data lagret i `Alias:` enheten.</span><span class="sxs-lookup"><span data-stu-id="a0253-136">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="a0253-137">Om du vill arbeta med alias kan du ändra din plats till `Alias:` enheten med hjälp av följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a0253-137">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="a0253-138">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="a0253-138">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="a0253-139">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="a0253-139">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="a0253-140">Du kan också arbeta med Ali Aset provider från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="a0253-140">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="a0253-141">Om du vill referera till ett alias från en annan plats använder du `Alias:` enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a0253-141">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="a0253-142">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="a0253-142">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="a0253-143">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="a0253-143">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="a0253-144">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="a0253-144">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="a0253-145">Visar innehållet i aliaset: enhet</span><span class="sxs-lookup"><span data-stu-id="a0253-145">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="a0253-146">Det här kommandot hämtar listan över alla alias när den aktuella platsen är `Alias:` enheten.</span><span class="sxs-lookup"><span data-stu-id="a0253-146">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="a0253-147">Ett jokertecken används `*` för att ange allt innehåll på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="a0253-147">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="a0253-148">I `Alias:` enheten, en punkt `.` som representerar den aktuella platsen och ett jokertecken `*` , som representerar alla objekt på den aktuella platsen, har samma resultat.</span><span class="sxs-lookup"><span data-stu-id="a0253-148">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="a0253-149">Till exempel `Get-Item -Path .` eller `Get-Item \*` skapa samma resultat.</span><span class="sxs-lookup"><span data-stu-id="a0253-149">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="a0253-150">Ali Aset-providern har inga behållare, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="a0253-150">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="a0253-151">Hämta ett markerat alias</span><span class="sxs-lookup"><span data-stu-id="a0253-151">Get a selected alias</span></span>

<span data-ttu-id="a0253-152">Det här kommandot hämtar `ls` aliaset.</span><span class="sxs-lookup"><span data-stu-id="a0253-152">This command gets the `ls` alias.</span></span>
<span data-ttu-id="a0253-153">Eftersom det innehåller sökvägen kan du använda den på valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="a0253-153">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="a0253-154">Om du är i `Alias:` enheten kan du utelämna enhets namnet från sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a0253-154">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="a0253-155">Du kan också hämta definitionen för ett alias genom att förlösa providerns sökväg med dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="a0253-155">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="a0253-156">Hämta alla alias för en angiven cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0253-156">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="a0253-157">Det här kommandot hämtar en lista över de alias som är associerade med `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0253-157">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="a0253-158">Den använder **definitions** egenskapen som lagrar cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="a0253-158">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="a0253-159">Skapa alias</span><span class="sxs-lookup"><span data-stu-id="a0253-159">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="a0253-160">Skapa ett alias från aliaset: enhet</span><span class="sxs-lookup"><span data-stu-id="a0253-160">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="a0253-161">Det här kommandot skapar `serv` aliaset för `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0253-161">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="a0253-162">Eftersom den aktuella platsen finns i `Alias:` enheten `-Path` behövs ingen parameter.</span><span class="sxs-lookup"><span data-stu-id="a0253-162">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="a0253-163">Det här kommandot använder också den `-Options` dynamiska parametern för att ange alternativet **AllScope** i aliaset.</span><span class="sxs-lookup"><span data-stu-id="a0253-163">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="a0253-164">`-Options`Parametern är bara tillgänglig i `New-Item` cmdleten när du befinner dig i `Alias:` enheten.</span><span class="sxs-lookup"><span data-stu-id="a0253-164">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="a0253-165">Punkten ( `.` ) visar den aktuella katalogen, som är Ali Aset.</span><span class="sxs-lookup"><span data-stu-id="a0253-165">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="a0253-166">Skapa ett alias med en absolut sökväg</span><span class="sxs-lookup"><span data-stu-id="a0253-166">Create an alias with an absolute path</span></span>

<span data-ttu-id="a0253-167">Du kan skapa ett alias för alla objekt som anropar ett kommando.</span><span class="sxs-lookup"><span data-stu-id="a0253-167">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="a0253-168">Det här kommandot skapar `np` alias för `Notepad.exe` .</span><span class="sxs-lookup"><span data-stu-id="a0253-168">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="a0253-169">Skapa ett alias för en ny funktion</span><span class="sxs-lookup"><span data-stu-id="a0253-169">Create an alias to a new function</span></span>

<span data-ttu-id="a0253-170">Du kan skapa ett alias för vilken funktion som helst.</span><span class="sxs-lookup"><span data-stu-id="a0253-170">You can create an alias for any function.</span></span> <span data-ttu-id="a0253-171">Du kan använda den här funktionen för att skapa ett alias som innehåller både en cmdlet och dess parametrar.</span><span class="sxs-lookup"><span data-stu-id="a0253-171">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="a0253-172">Det första kommandot skapar `CD32` funktionen, som ändrar den aktuella katalogen till `System32` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a0253-172">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="a0253-173">Det andra kommandot skapar `go` aliaset för `CD32` funktionen.</span><span class="sxs-lookup"><span data-stu-id="a0253-173">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="a0253-174">När kommandot har slutförts kan du använda antingen `CD32` eller `go` för att anropa funktionen.</span><span class="sxs-lookup"><span data-stu-id="a0253-174">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="a0253-175">Ändra alias</span><span class="sxs-lookup"><span data-stu-id="a0253-175">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="a0253-176">Ändra alternativen för ett alias</span><span class="sxs-lookup"><span data-stu-id="a0253-176">Change the options of an alias</span></span>

<span data-ttu-id="a0253-177">Du kan använda `Set-Item` cmdleten med den `-Options` dynamiska parametern för att ändra värdet för `-Options` egenskapen för ett alias.</span><span class="sxs-lookup"><span data-stu-id="a0253-177">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="a0253-178">Det här kommandot anger **AllScope** och **ReadOnly** -alternativen för `dir` aliaset.</span><span class="sxs-lookup"><span data-stu-id="a0253-178">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="a0253-179">Kommandot använder `-Options` `Set-Item` cmdletens dynamiska parameter.</span><span class="sxs-lookup"><span data-stu-id="a0253-179">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="a0253-180">`-Options`Parametern är tillgänglig i `Set-Item` när du använder den med **alias** -eller **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="a0253-180">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="a0253-181">Ändra ett alias som refereras till kommandot</span><span class="sxs-lookup"><span data-stu-id="a0253-181">Change an aliases referenced command</span></span>

<span data-ttu-id="a0253-182">Detta kommando använder `Set-Item` cmdleten för att ändra `gp` alias så att det representerar `Get-Process` cmdleten i stället för `Get-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0253-182">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="a0253-183">`-Force`Parametern är obligatorisk eftersom värdet på egenskapen **alternativ** för `gp` aliaset är inställt på `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="a0253-183">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="a0253-184">Eftersom kommandot skickas inifrån `Alias:` enheten, anges inte enheten i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a0253-184">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="a0253-185">Ändringen påverkar de fyra egenskaperna som definierar associationen mellan aliaset och kommandot.</span><span class="sxs-lookup"><span data-stu-id="a0253-185">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="a0253-186">Skriv följande kommando om du vill visa ändrings resultatet:</span><span class="sxs-lookup"><span data-stu-id="a0253-186">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="a0253-187">Byta namn på ett alias</span><span class="sxs-lookup"><span data-stu-id="a0253-187">Rename an alias</span></span>

<span data-ttu-id="a0253-188">Det här kommandot använder `Rename-Item` cmdleten för att ändra `popd` aliaset till `pop` .</span><span class="sxs-lookup"><span data-stu-id="a0253-188">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="a0253-189">Kopierar ett alias</span><span class="sxs-lookup"><span data-stu-id="a0253-189">Copying an alias</span></span>

<span data-ttu-id="a0253-190">Det här kommandot kopierar `pushd` aliaset så att ett nytt `push` alias skapas för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0253-190">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="a0253-191">När det nya aliaset skapas har egenskapen **Description** värdet null.</span><span class="sxs-lookup"><span data-stu-id="a0253-191">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="a0253-192">Och dess **alternativ** egenskap har värdet `None` .</span><span class="sxs-lookup"><span data-stu-id="a0253-192">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="a0253-193">Om kommandot utfärdas inifrån `Alias:` enheten kan du utelämna enhets namnet från `-Path` parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="a0253-193">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="a0253-194">Tar bort ett alias</span><span class="sxs-lookup"><span data-stu-id="a0253-194">Deleting an alias</span></span>

<span data-ttu-id="a0253-195">Det här kommandot tar bort `serv` aliaset från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a0253-195">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="a0253-196">Du kan använda det här kommandot i valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="a0253-196">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="a0253-197">Det här kommandot tar bort alias som börjar med "s".</span><span class="sxs-lookup"><span data-stu-id="a0253-197">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="a0253-198">Det tar inte bort skrivskyddade alias.</span><span class="sxs-lookup"><span data-stu-id="a0253-198">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="a0253-199">Ta bort skrivskyddade alias</span><span class="sxs-lookup"><span data-stu-id="a0253-199">Delete read-only aliases</span></span>

<span data-ttu-id="a0253-200">Det här kommandot tar bort alla alias från den aktuella sessionen, förutom de med värdet `Constant` för egenskapen **Options** .</span><span class="sxs-lookup"><span data-stu-id="a0253-200">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="a0253-201">`-Force`Parametern tillåter kommandot att ta bort alias vars **alternativ** egenskap har värdet `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="a0253-201">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="a0253-202">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="a0253-202">Dynamic parameters</span></span>

<span data-ttu-id="a0253-203">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="a0253-203">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="a0253-204">Alternativ [system. Management. Automation. ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="a0253-204">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="a0253-205">Anger värdet för egenskapen **Options** för ett alias.</span><span class="sxs-lookup"><span data-stu-id="a0253-205">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="a0253-206">**Ingen**: inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="a0253-206">**None**: No options.</span></span> <span data-ttu-id="a0253-207">Detta värde är standard.</span><span class="sxs-lookup"><span data-stu-id="a0253-207">This value is the default.</span></span>
- <span data-ttu-id="a0253-208">**Konstant**: det går inte att ta bort aliaset och dess egenskaper kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="a0253-208">**Constant**:The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="a0253-209">**Konstant** är endast tillgängligt när du skapar ett alias.</span><span class="sxs-lookup"><span data-stu-id="a0253-209">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="a0253-210">Det går inte att ändra alternativet för ett befintligt alias till **konstant**.</span><span class="sxs-lookup"><span data-stu-id="a0253-210">You cannot change the option of an existing alias to **Constant**.</span></span>
- <span data-ttu-id="a0253-211">**Privat**: aliaset är endast synligt i det aktuella omfånget, inte i de underordnade omfången.</span><span class="sxs-lookup"><span data-stu-id="a0253-211">**Private**:The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="a0253-212">**ReadOnly**: egenskaperna för aliaset kan inte ändras förutom genom att använda `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="a0253-212">**ReadOnly**:The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="a0253-213">Du kan använda `Remove-Item` för att ta bort aliaset.</span><span class="sxs-lookup"><span data-stu-id="a0253-213">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="a0253-214">**AllScope**: aliaset kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="a0253-214">**AllScope**:The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a0253-215">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a0253-215">Cmdlets supported</span></span>

- [<span data-ttu-id="a0253-216">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="a0253-216">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="a0253-217">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="a0253-217">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="a0253-218">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="a0253-218">Using the pipeline</span></span>

<span data-ttu-id="a0253-219">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="a0253-219">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="a0253-220">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0253-220">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="a0253-221">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="a0253-221">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="a0253-222">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="a0253-222">Getting help</span></span>

<span data-ttu-id="a0253-223">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="a0253-223">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="a0253-224">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="a0253-224">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="a0253-225">Se även</span><span class="sxs-lookup"><span data-stu-id="a0253-225">See also</span></span>

[<span data-ttu-id="a0253-226">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="a0253-226">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="a0253-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a0253-227">about_Providers</span></span>](../About/about_Providers.md)

