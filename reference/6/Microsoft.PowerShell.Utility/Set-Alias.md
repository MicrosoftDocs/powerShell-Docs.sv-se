---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 791b500660ed536eb1bd7ba4d6f37e8211078a0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266763"
---
# <span data-ttu-id="76179-103">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="76179-103">Set-Alias</span></span>

## <span data-ttu-id="76179-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="76179-104">SYNOPSIS</span></span>
<span data-ttu-id="76179-105">Skapar eller ändrar ett alias för en cmdlet eller något annat kommando i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-105">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="76179-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="76179-106">SYNTAX</span></span>

### <span data-ttu-id="76179-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="76179-107">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="76179-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="76179-108">DESCRIPTION</span></span>

<span data-ttu-id="76179-109">`Set-Alias`Cmdleten skapar eller ändrar ett alias för en cmdlet eller ett kommando, till exempel en funktion, ett skript, en fil eller en annan körbar fil.</span><span class="sxs-lookup"><span data-stu-id="76179-109">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="76179-110">Ett alias är ett alternativt namn som refererar till en cmdlet eller ett kommando.</span><span class="sxs-lookup"><span data-stu-id="76179-110">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="76179-111">Är till exempel `sal` alias för `Set-Alias` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-111">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="76179-112">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="76179-112">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="76179-113">En cmdlet kan ha flera alias, men ett alias kan bara associeras med en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="76179-113">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="76179-114">Du kan använda `Set-Alias` för att omtilldela ett befintligt alias till en annan cmdlet eller ändra ett Aliass egenskaper, till exempel beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="76179-114">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="76179-115">Ett alias som skapas eller ändras av `Set-Alias` är inte permanent och är bara tillgängligt under den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-115">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="76179-116">När PowerShell-sessionen stängs tas aliaset bort.</span><span class="sxs-lookup"><span data-stu-id="76179-116">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="76179-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="76179-117">EXAMPLES</span></span>

### <span data-ttu-id="76179-118">Exempel 1: skapa ett alias för en cmdlet</span><span class="sxs-lookup"><span data-stu-id="76179-118">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="76179-119">Det här kommandot skapar ett alias till en cmdlet i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-119">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="76179-120">`Set-Alias`Cmdleten skapar ett alias i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-120">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="76179-121">Parametern **Name** anger aliasets namn `list` .</span><span class="sxs-lookup"><span data-stu-id="76179-121">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="76179-122">Parametern **Value** anger den cmdlet som aliaset kör.</span><span class="sxs-lookup"><span data-stu-id="76179-122">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="76179-123">Om du vill köra aliaset skriver `list` du på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="76179-123">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="76179-124">Exempel 2: omtilldela ett befintligt alias till en annan cmdlet</span><span class="sxs-lookup"><span data-stu-id="76179-124">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="76179-125">Det här kommandot tilldelar om ett befintligt alias för att köra en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="76179-125">This command reassigns an existing alias to run a different cmdlet.</span></span>

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

<span data-ttu-id="76179-126">`Get-Alias`Cmdlet: en använder parametern **Name** för att visa `list` aliaset.</span><span class="sxs-lookup"><span data-stu-id="76179-126">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="76179-127">`list`Aliaset är associerat med `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-127">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="76179-128">När `list` aliaset körs visas objekten i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="76179-128">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="76179-129">`Set-Alias`Cmdleten använder **Name** -parametern för att ange `list` alias.</span><span class="sxs-lookup"><span data-stu-id="76179-129">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="76179-130">Parametern **Value** associerar aliaset med `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-130">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="76179-131">`Get-Alias`Cmdlet: en använder parametern **Name** för att visa `list` aliaset.</span><span class="sxs-lookup"><span data-stu-id="76179-131">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="76179-132">`list`Aliaset är associerat med `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-132">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="76179-133">När `list` aliaset körs visas den aktuella katalogens plats.</span><span class="sxs-lookup"><span data-stu-id="76179-133">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="76179-134">Exempel 3: skapa och ändra ett skrivskyddat alias</span><span class="sxs-lookup"><span data-stu-id="76179-134">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="76179-135">Det här kommandot skapar ett skrivskyddat alias.</span><span class="sxs-lookup"><span data-stu-id="76179-135">This command creates a read-only alias.</span></span> <span data-ttu-id="76179-136">Alternativet Skriv skydd förhindrar oönskade ändringar i ett alias.</span><span class="sxs-lookup"><span data-stu-id="76179-136">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="76179-137">Använd parametern **Force** om du vill ändra eller ta bort ett skrivskyddat alias.</span><span class="sxs-lookup"><span data-stu-id="76179-137">To change or delete a read-only alias, use the **Force** parameter.</span></span>

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

<span data-ttu-id="76179-138">`Set-Alias`Cmdleten skapar ett alias i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-138">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="76179-139">Parametern **Name** anger aliasets namn `loc` .</span><span class="sxs-lookup"><span data-stu-id="76179-139">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="76179-140">Parametern **Value** anger den `Get-Location` cmdlet som aliaset kör.</span><span class="sxs-lookup"><span data-stu-id="76179-140">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="76179-141">**Alternativ** parametern anger det **skrivskyddade** värdet.</span><span class="sxs-lookup"><span data-stu-id="76179-141">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="76179-142">Parametern **Passthru** representerar objektet alias och skickar objektet nedåt i pipeline till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-142">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="76179-143">`Format-List` använder **egenskaps** parametern med en asterisk ( `*` ) så att alla egenskaper visas.</span><span class="sxs-lookup"><span data-stu-id="76179-143">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="76179-144">I exempel resultatet visas en del av de här egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="76179-144">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="76179-145">`loc`Aliaset ändras med addition av två parametrar.</span><span class="sxs-lookup"><span data-stu-id="76179-145">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="76179-146">**Beskrivning** lägger till text för att förklara aliasets syfte.</span><span class="sxs-lookup"><span data-stu-id="76179-146">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="76179-147">Parametern **Force** krävs eftersom `loc` aliaset är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="76179-147">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="76179-148">Om **Force** -parametern inte används, Miss lyckas ändringen.</span><span class="sxs-lookup"><span data-stu-id="76179-148">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="76179-149">Exempel 4: skapa ett alias till en körbar fil</span><span class="sxs-lookup"><span data-stu-id="76179-149">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="76179-150">I det här exemplet skapas ett alias till en körbar fil på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="76179-150">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="76179-151">`Set-Alias`Cmdleten skapar ett alias i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-151">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="76179-152">Parametern **Name** anger aliasets namn `np` .</span><span class="sxs-lookup"><span data-stu-id="76179-152">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="76179-153">Parametern **Value** anger sökväg och program namn **C:\Windows\notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="76179-153">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe**.</span></span> <span data-ttu-id="76179-154">`Get-Alias`Cmdleten använder parametern **Name** för att visa att `np` aliaset är associerat med **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="76179-154">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe**.</span></span>

<span data-ttu-id="76179-155">Om du vill köra aliaset skriver du `np` på PowerShell-kommandoraden för att öppna **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="76179-155">To run the alias, type `np` on the PowerShell command line to open **notepad.exe**.</span></span>

### <span data-ttu-id="76179-156">Exempel 5: skapa ett alias för ett kommando med parametrar</span><span class="sxs-lookup"><span data-stu-id="76179-156">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="76179-157">Det här exemplet visar hur du tilldelar ett alias till ett kommando med parametrar.</span><span class="sxs-lookup"><span data-stu-id="76179-157">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="76179-158">Du kan skapa ett alias för en cmdlet, till exempel `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="76179-158">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="76179-159">Du kan inte skapa ett alias för ett kommando med parametrar och värden, till exempel `Set-Location -Path C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="76179-159">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="76179-160">Skapa ett alias för ett kommando genom att skapa en funktion som innehåller kommandot och sedan skapa ett alias för funktionen.</span><span class="sxs-lookup"><span data-stu-id="76179-160">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="76179-161">Mer information finns i [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span><span class="sxs-lookup"><span data-stu-id="76179-161">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="76179-162">En funktion `CD32` som heter skapas.</span><span class="sxs-lookup"><span data-stu-id="76179-162">A function named `CD32` is created.</span></span> <span data-ttu-id="76179-163">Funktionen använder `Set-Location` cmdleten med parametern **Path** för att ange katalogen, **C:\Windows\System32**.</span><span class="sxs-lookup"><span data-stu-id="76179-163">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, **C:\Windows\System32**.</span></span>

<span data-ttu-id="76179-164">`Set-Alias`Cmdleten skapar ett alias för funktionen i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76179-164">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="76179-165">Parametern **Name** anger aliasets namn `Go` .</span><span class="sxs-lookup"><span data-stu-id="76179-165">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="76179-166">Parametern **Value** anger funktionens namn, `CD32` .</span><span class="sxs-lookup"><span data-stu-id="76179-166">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="76179-167">Om du vill köra aliaset skriver `Go` du på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="76179-167">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="76179-168">`CD32`Funktionen körs och ändras till katalogen **C:\Windows\System32**.</span><span class="sxs-lookup"><span data-stu-id="76179-168">The `CD32` function runs and changes to the directory **C:\Windows\System32**.</span></span>

## <span data-ttu-id="76179-169">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="76179-169">PARAMETERS</span></span>

### <span data-ttu-id="76179-170">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="76179-170">-Description</span></span>

<span data-ttu-id="76179-171">Anger en beskrivning av aliaset.</span><span class="sxs-lookup"><span data-stu-id="76179-171">Specifies a description of the alias.</span></span> <span data-ttu-id="76179-172">Du kan ange valfri sträng.</span><span class="sxs-lookup"><span data-stu-id="76179-172">You can type any string.</span></span> <span data-ttu-id="76179-173">Om beskrivningen innehåller blank steg omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="76179-173">If the description includes spaces, enclose it single quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-174">-Force</span><span class="sxs-lookup"><span data-stu-id="76179-174">-Force</span></span>

<span data-ttu-id="76179-175">Använd parametern **Force** för att ändra eller ta bort ett alias som har **alternativ** parametern inställd på **skrivskyddad**.</span><span class="sxs-lookup"><span data-stu-id="76179-175">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly**.</span></span>

<span data-ttu-id="76179-176">**Force** -parametern kan inte ändra eller ta bort ett alias med **alternativ** parametern inställd på **konstant**.</span><span class="sxs-lookup"><span data-stu-id="76179-176">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-177">-Name</span><span class="sxs-lookup"><span data-stu-id="76179-177">-Name</span></span>

<span data-ttu-id="76179-178">Anger namnet på ett nytt alias.</span><span class="sxs-lookup"><span data-stu-id="76179-178">Specifies the name of a new alias.</span></span> <span data-ttu-id="76179-179">Ett aliasnamn får innehålla alfanumeriska tecken och bindestreck.</span><span class="sxs-lookup"><span data-stu-id="76179-179">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="76179-180">Aliasnamn får inte vara numeriska, till exempel 123.</span><span class="sxs-lookup"><span data-stu-id="76179-180">Alias names cannot be numeric, such as 123.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="76179-181">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="76179-181">-Option</span></span>

<span data-ttu-id="76179-182">Anger aliasets **alternativ** egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="76179-182">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="76179-183">Värden som **ReadOnly** och **konstant** skyddar ett alias från oavsiktliga ändringar.</span><span class="sxs-lookup"><span data-stu-id="76179-183">Values such as **ReadOnly** and **Constant** protect an alias from unintended changes.</span></span> <span data-ttu-id="76179-184">Om du vill se egenskapen **alternativ** för alla alias i sessionen skriver du `Get-Alias | Format-Table -Property Name, Options -Autosize` .</span><span class="sxs-lookup"><span data-stu-id="76179-184">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="76179-185">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="76179-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="76179-186">**AllScope** Aliaset kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="76179-186">**AllScope** The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="76179-187">**Konstant** Kan inte ändras eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="76179-187">**Constant** Cannot be changed or deleted.</span></span>
- <span data-ttu-id="76179-188">**Ingen** Anger inga alternativ och är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="76179-188">**None** Sets no options and is the default.</span></span>
- <span data-ttu-id="76179-189">**Privat** Aliaset är endast tillgängligt i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="76179-189">**Private** The alias is available only in the current scope.</span></span>
- <span data-ttu-id="76179-190">**ReadOnly** Kan inte ändras eller tas bort om inte parametern **Force** används.</span><span class="sxs-lookup"><span data-stu-id="76179-190">**ReadOnly** Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- <span data-ttu-id="76179-191">**Ospecificerat**</span><span class="sxs-lookup"><span data-stu-id="76179-191">**Unspecified**</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-192">– PassThru</span><span class="sxs-lookup"><span data-stu-id="76179-192">-PassThru</span></span>

<span data-ttu-id="76179-193">Returnerar ett objekt som representerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="76179-193">Returns an object that represents the alias.</span></span> <span data-ttu-id="76179-194">Använd en format-cmdlet, till exempel `Format-List` för att visa objektet.</span><span class="sxs-lookup"><span data-stu-id="76179-194">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="76179-195">`Set-Alias`Genererar inga utdata som standard.</span><span class="sxs-lookup"><span data-stu-id="76179-195">By default, `Set-Alias` does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-196">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="76179-196">-Scope</span></span>

<span data-ttu-id="76179-197">Anger omfattningen som detta alias är giltigt i.</span><span class="sxs-lookup"><span data-stu-id="76179-197">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="76179-198">Standardvärdet är **Local**.</span><span class="sxs-lookup"><span data-stu-id="76179-198">The default value is **Local**.</span></span> <span data-ttu-id="76179-199">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="76179-199">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="76179-200">De acceptabla värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="76179-200">The acceptable values are as follows:</span></span>

- <span data-ttu-id="76179-201">Global</span><span class="sxs-lookup"><span data-stu-id="76179-201">Global</span></span>
- <span data-ttu-id="76179-202">Lokal</span><span class="sxs-lookup"><span data-stu-id="76179-202">Local</span></span>
- <span data-ttu-id="76179-203">Privat</span><span class="sxs-lookup"><span data-stu-id="76179-203">Private</span></span>
- <span data-ttu-id="76179-204">Numrerade omfattningar</span><span class="sxs-lookup"><span data-stu-id="76179-204">Numbered scopes</span></span>
- <span data-ttu-id="76179-205">Skript</span><span class="sxs-lookup"><span data-stu-id="76179-205">Script</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-206">-Värde</span><span class="sxs-lookup"><span data-stu-id="76179-206">-Value</span></span>

<span data-ttu-id="76179-207">Anger namnet på den cmdlet eller det kommando som aliaset kör.</span><span class="sxs-lookup"><span data-stu-id="76179-207">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="76179-208">Parametern **Value** är aliasets **definitions** egenskap.</span><span class="sxs-lookup"><span data-stu-id="76179-208">The **Value** parameter is the alias's **Definition** property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="76179-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="76179-209">-Confirm</span></span>

<span data-ttu-id="76179-210">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-210">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="76179-211">-WhatIf</span></span>

<span data-ttu-id="76179-212">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="76179-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="76179-213">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="76179-213">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76179-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76179-214">CommonParameters</span></span>

<span data-ttu-id="76179-215">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76179-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76179-216">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="76179-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="76179-217">INDATA</span><span class="sxs-lookup"><span data-stu-id="76179-217">INPUTS</span></span>

### <span data-ttu-id="76179-218">Inget</span><span class="sxs-lookup"><span data-stu-id="76179-218">None</span></span>

<span data-ttu-id="76179-219">`Set-Alias` accepterar inte ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="76179-219">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="76179-220">UTDATA</span><span class="sxs-lookup"><span data-stu-id="76179-220">OUTPUTS</span></span>

### <span data-ttu-id="76179-221">Ingen eller system. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="76179-221">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="76179-222">När du använder parametern **Passthru** `Set-Alias` genereras ett **system. Management. Automation. AliasInfo** -objekt som representerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="76179-222">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="76179-223">Annars `Set-Alias` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="76179-223">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="76179-224">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="76179-224">NOTES</span></span>

<span data-ttu-id="76179-225">PowerShell innehåller inbyggda alias som är tillgängliga i varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="76179-225">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="76179-226">`Get-Alias`Cmdleten visar de alias som är tillgängliga i en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="76179-226">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="76179-227">Om du vill skapa ett alias använder du cmdletarna `Set-Alias` eller `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="76179-227">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="76179-228">I PowerShell 6, om du vill ta bort ett alias, använder du `Remove-Alias` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76179-228">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="76179-229">`Remove-Item` accepteras för bakåtkompatibilitet, till exempel för skript som skapats med tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76179-229">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="76179-230">Använd ett kommando som `Remove-Item -Path Alias:aliasname` .</span><span class="sxs-lookup"><span data-stu-id="76179-230">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="76179-231">Om du vill skapa ett alias som är tillgängligt i varje PowerShell-session lägger du till det i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="76179-231">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="76179-232">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="76179-232">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="76179-233">Ett alias kan sparas och återanvändas i en annan PowerShell-session genom att exportera och importera.</span><span class="sxs-lookup"><span data-stu-id="76179-233">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="76179-234">Använd om du vill spara ett alias i en fil `Export-Alias` .</span><span class="sxs-lookup"><span data-stu-id="76179-234">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="76179-235">Använd om du vill lägga till ett sparat alias i en ny PowerShell-session `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="76179-235">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="76179-236">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="76179-236">RELATED LINKS</span></span>

[<span data-ttu-id="76179-237">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="76179-237">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="76179-238">about_Functions</span><span class="sxs-lookup"><span data-stu-id="76179-238">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="76179-239">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="76179-239">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="76179-240">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="76179-240">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="76179-241">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="76179-241">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="76179-242">Get-alias</span><span class="sxs-lookup"><span data-stu-id="76179-242">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="76179-243">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="76179-243">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="76179-244">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="76179-244">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="76179-245">Ta bort-alias</span><span class="sxs-lookup"><span data-stu-id="76179-245">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="76179-246">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="76179-246">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)
