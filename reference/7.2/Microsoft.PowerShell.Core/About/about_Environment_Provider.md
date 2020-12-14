---
description: Miljö
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Miljö leverantör
ms.openlocfilehash: f50558ba23d21b5ca145a06086c1c6d9b1fcd3bf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710627"
---
# <a name="environment-provider"></a><span data-ttu-id="f712c-103">Miljö leverantör</span><span class="sxs-lookup"><span data-stu-id="f712c-103">Environment provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="f712c-104">Providernamn</span><span class="sxs-lookup"><span data-stu-id="f712c-104">Provider name</span></span>
<span data-ttu-id="f712c-105">Miljö</span><span class="sxs-lookup"><span data-stu-id="f712c-105">Environment</span></span>

## <a name="drives"></a><span data-ttu-id="f712c-106">Enheter</span><span class="sxs-lookup"><span data-stu-id="f712c-106">Drives</span></span>

`Env:`

## <a name="capabilities"></a><span data-ttu-id="f712c-107">Funktioner</span><span class="sxs-lookup"><span data-stu-id="f712c-107">Capabilities</span></span>

<span data-ttu-id="f712c-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="f712c-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="f712c-109">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="f712c-109">Short description</span></span>

<span data-ttu-id="f712c-110">Ger åtkomst till Windows-miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="f712c-110">Provides access to the Windows environment variables.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="f712c-111">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="f712c-111">Detailed description</span></span>

<span data-ttu-id="f712c-112">Med PowerShell **-operatören** kan du hämta, lägga till, ändra, radera och ta bort miljövariabler och värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f712c-112">The PowerShell **Environment** provider lets you get, add, change, clear, and delete environment variables and values in PowerShell.</span></span>

<span data-ttu-id="f712c-113">**Miljövariabler är** dynamiskt namngivna variabler som beskriver i vilken miljö dina program körs.</span><span class="sxs-lookup"><span data-stu-id="f712c-113">**Environment** variables are dynamically named variables that describe the environment in which your programs run.</span></span> <span data-ttu-id="f712c-114">Windows och PowerShell använder miljövariabler för att lagra beständig information som påverkar system-och process körning.</span><span class="sxs-lookup"><span data-stu-id="f712c-114">Windows and PowerShell use environment variables to store persistent information that affect system and process execution.</span></span> <span data-ttu-id="f712c-115">Till skillnad från PowerShell-variabler omfattas miljövariabler inte av omfattnings begränsningar.</span><span class="sxs-lookup"><span data-stu-id="f712c-115">Unlike PowerShell variables, environment variables are not subject to scope constraints.</span></span>

<span data-ttu-id="f712c-116">**Miljö** enheten är ett plant namn område som innehåller miljövariablerna som är speciella för den aktuella användarens session.</span><span class="sxs-lookup"><span data-stu-id="f712c-116">The **Environment** drive is a flat namespace containing the environment variables specific to the current user's session.</span></span> <span data-ttu-id="f712c-117">Miljövariablerna har inga underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="f712c-117">The environment variables have no child items.</span></span>

<span data-ttu-id="f712c-118">- **Miljö** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="f712c-118">The **Environment** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="f712c-119">Get-location</span><span class="sxs-lookup"><span data-stu-id="f712c-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="f712c-120">Ange plats</span><span class="sxs-lookup"><span data-stu-id="f712c-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="f712c-121">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="f712c-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="f712c-122">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="f712c-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="f712c-123">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="f712c-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="f712c-124">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="f712c-124">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="f712c-125">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="f712c-125">Types exposed by this provider</span></span>

<span data-ttu-id="f712c-126">Varje miljö variabel är en instans av klassen [system. Collections. typen DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) .</span><span class="sxs-lookup"><span data-stu-id="f712c-126">Each environment variable is an instance of the [System.Collections.DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) class.</span></span> <span data-ttu-id="f712c-127">Namnet på variabeln är ord listans nyckel.</span><span class="sxs-lookup"><span data-stu-id="f712c-127">The name of the variable is the dictionary key.</span></span> <span data-ttu-id="f712c-128">Värdet för miljö variabeln är värdet för ord listan.</span><span class="sxs-lookup"><span data-stu-id="f712c-128">The value of the environment variable is the dictionary value.</span></span>

## <a name="navigating-the-environment-drive"></a><span data-ttu-id="f712c-129">Navigera i miljö enheten</span><span class="sxs-lookup"><span data-stu-id="f712c-129">Navigating the Environment drive</span></span>

<span data-ttu-id="f712c-130">- **Miljö** leverantören exponerar data lagret i `Env:` enheten.</span><span class="sxs-lookup"><span data-stu-id="f712c-130">The **Environment** provider exposes its data store in the `Env:` drive.</span></span> <span data-ttu-id="f712c-131">Ändra platsen till `Env:` enheten ( `Set-Location Env:` ) eller arbeta från en annan PowerShell-enhet om du vill arbeta med miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="f712c-131">To work with environment variables, change your location to the `Env:` drive (`Set-Location Env:`), or work from another PowerShell drive.</span></span> <span data-ttu-id="f712c-132">Om du vill referera till en miljö variabel från en annan plats använder du `Env:` enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="f712c-132">To reference an environment variable from another location, use the `Env:` drive name in the path.</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="f712c-133">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="f712c-133">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="f712c-134">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="f712c-134">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="f712c-135">Du kan också arbeta med- **miljö** leverantören från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="f712c-135">You can also work with the **Environment** provider from any other PowerShell drive.</span></span> <span data-ttu-id="f712c-136">Om du vill referera till en miljö variabel från en annan plats använder du enhets namnet `Env:` i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="f712c-136">To reference an environment variable from another location, use the drive name `Env:` in the path.</span></span>

<span data-ttu-id="f712c-137">- **Miljö** leverantören exponerar också miljövariabler med hjälp av ett variabel prefix `$env:` .</span><span class="sxs-lookup"><span data-stu-id="f712c-137">The **Environment** provider also exposes environment variables using a variable prefix of `$env:`.</span></span>  <span data-ttu-id="f712c-138">Följande kommando visar innehållet i miljövariabeln **ProgramFiles** .</span><span class="sxs-lookup"><span data-stu-id="f712c-138">The following command views the contents of the **ProgramFiles** environment variable.</span></span> <span data-ttu-id="f712c-139">Det `$env:` variabla prefixet kan användas från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="f712c-139">The `$env:` variable prefix can be used from any PowerShell drive.</span></span>

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

<span data-ttu-id="f712c-140">Du kan också ändra värdet för en miljö variabel med hjälp av `$env:` variabeln prefix.</span><span class="sxs-lookup"><span data-stu-id="f712c-140">You can also change the value of an environment variable using the `$env:` variable prefix.</span></span>  <span data-ttu-id="f712c-141">Alla ändringar som gjorts gäller bara för den aktuella PowerShell-sessionen så länge den är aktiv.</span><span class="sxs-lookup"><span data-stu-id="f712c-141">Any changes made only pertain to the current PowerShell session for as long as it is active.</span></span>

> [!NOTE]
> <span data-ttu-id="f712c-142">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="f712c-142">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="f712c-143">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="f712c-143">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="f712c-144">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="f712c-144">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-environment-variables"></a><span data-ttu-id="f712c-145">Hämtar miljövariabler</span><span class="sxs-lookup"><span data-stu-id="f712c-145">Getting environment variables</span></span>

<span data-ttu-id="f712c-146">Det här kommandot visar alla miljövariabler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f712c-146">This command lists all the environment variables in the current session.</span></span>

```powershell
Get-Item -Path Env:
```

<span data-ttu-id="f712c-147">Du kan använda det här kommandot från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="f712c-147">You can use this command from any PowerShell drive.</span></span>

<span data-ttu-id="f712c-148">Det finns inga behållare i miljö leverantören, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="f712c-148">The Environment provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a><span data-ttu-id="f712c-149">Hämta en vald miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-149">Get a selected environment variable</span></span>

<span data-ttu-id="f712c-150">Det här kommandot hämtar `WINDIR` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="f712c-150">This command gets the `WINDIR` environment Variable.</span></span>

```powershell
Get-ChildItem -Path Env:windir
```

<span data-ttu-id="f712c-151">Du kan också använda formatet variabel prefix.</span><span class="sxs-lookup"><span data-stu-id="f712c-151">You can also use the variable prefix format as well.</span></span>

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a><span data-ttu-id="f712c-152">Skapa en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-152">Create an environment variable</span></span>

<span data-ttu-id="f712c-153">Det här kommandot skapar `USERMODE` miljövariabeln med värdet "icke-admin".</span><span class="sxs-lookup"><span data-stu-id="f712c-153">This command creates the `USERMODE` environment variable with a value of "Non-Admin".</span></span> <span data-ttu-id="f712c-154">`-Path`Parametervärdet skapar det nya objektet i `Env:` enheten.</span><span class="sxs-lookup"><span data-stu-id="f712c-154">The `-Path` parameter value creates the new item in the `Env:` drive.</span></span> <span data-ttu-id="f712c-155">Den nya miljö variabeln kan bara användas i den aktuella PowerShell-sessionen så länge den är aktiv.</span><span class="sxs-lookup"><span data-stu-id="f712c-155">The new environment variable is only usable in the current PowerShell session for as long as it is active.</span></span>

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a><span data-ttu-id="f712c-156">Ändra en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-156">Changing an environment variable</span></span>

### <a name="rename-an-environment-variable"></a><span data-ttu-id="f712c-157">Byta namn på en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-157">Rename an environment variable</span></span>

<span data-ttu-id="f712c-158">Detta kommando använder `Rename-Item` cmdleten för att ändra namnet på den `USERMODE` miljö variabel som du skapade till `USERROLE` .</span><span class="sxs-lookup"><span data-stu-id="f712c-158">This command uses the `Rename-Item` cmdlet to change the name of the `USERMODE` environment variable that you created to `USERROLE`.</span></span> <span data-ttu-id="f712c-159">Ändra inte namnet på en miljö variabel som används i systemet.</span><span class="sxs-lookup"><span data-stu-id="f712c-159">Do not change the name of an environment variable that the system uses.</span></span> <span data-ttu-id="f712c-160">Även om dessa ändringar endast påverkar den aktuella sessionen kan det leda till att systemet eller ett program fungerar felaktigt.</span><span class="sxs-lookup"><span data-stu-id="f712c-160">Although these changes affect only the current session, they might cause the system or a program to operate incorrectly.</span></span>

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a><span data-ttu-id="f712c-161">Ändra en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-161">Change an environment variable</span></span>

<span data-ttu-id="f712c-162">Det här kommandot använder `Set-Item` cmdleten för att ändra värdet för `USERROLE` miljövariabeln till "administratör".</span><span class="sxs-lookup"><span data-stu-id="f712c-162">This command uses the `Set-Item` cmdlet to change the value of the `USERROLE` environment variable to "Administrator".</span></span>

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a><span data-ttu-id="f712c-163">Kopiera en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-163">Copy an environment variable</span></span>

<span data-ttu-id="f712c-164">Det här kommandot kopierar värdet för `USERROLE` miljö variabeln till `USERROLE2` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="f712c-164">This command copies the value of the `USERROLE` environment variable to the `USERROLE2` environment Variable.</span></span>

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a><span data-ttu-id="f712c-165">Ta bort en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="f712c-165">Remove an environment variable</span></span>

<span data-ttu-id="f712c-166">Det här kommandot tar bort `USERROLE2` miljövariabeln från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f712c-166">This command deletes the `USERROLE2` environment variable from the current session.</span></span>

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a><span data-ttu-id="f712c-167">Ta bort en miljö variabel med Clear-Item</span><span class="sxs-lookup"><span data-stu-id="f712c-167">Remove an environment variable with Clear-Item</span></span>

<span data-ttu-id="f712c-168">Det här kommandot tar bort `USERROLE` miljövariabeln genom att rensa dess värde.</span><span class="sxs-lookup"><span data-stu-id="f712c-168">This command deletes the `USERROLE` environment variable by clearing its value.</span></span>

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a><span data-ttu-id="f712c-169">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="f712c-169">Using the pipeline</span></span>

<span data-ttu-id="f712c-170">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="f712c-170">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="f712c-171">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f712c-171">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="f712c-172">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="f712c-172">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="f712c-173">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="f712c-173">Getting help</span></span>

<span data-ttu-id="f712c-174">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="f712c-174">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="f712c-175">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="f712c-175">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a><span data-ttu-id="f712c-176">Se även</span><span class="sxs-lookup"><span data-stu-id="f712c-176">See also</span></span>

[<span data-ttu-id="f712c-177">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f712c-177">about_Providers</span></span>](../About/about_Providers.md)

