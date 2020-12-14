---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 573bb0054b60e8c17b79da72ebc712c6ef5575a5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710758"
---
# <span data-ttu-id="58a08-102">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="58a08-102">Set-Variable</span></span>

## <span data-ttu-id="58a08-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="58a08-103">SYNOPSIS</span></span>
<span data-ttu-id="58a08-104">Anger värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="58a08-104">Sets the value of a variable.</span></span> <span data-ttu-id="58a08-105">Skapar variabeln om en med det begärda namnet inte finns.</span><span class="sxs-lookup"><span data-stu-id="58a08-105">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="58a08-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="58a08-106">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="58a08-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="58a08-107">DESCRIPTION</span></span>

<span data-ttu-id="58a08-108">`Set-Variable`Cmdlet: en tilldelar ett värde till en angiven variabel eller ändrar det aktuella värdet.</span><span class="sxs-lookup"><span data-stu-id="58a08-108">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="58a08-109">Om variabeln inte finns skapar cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="58a08-109">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="58a08-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="58a08-110">EXAMPLES</span></span>

### <span data-ttu-id="58a08-111">Exempel 1: Ange en variabel och hämta dess värde</span><span class="sxs-lookup"><span data-stu-id="58a08-111">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="58a08-112">De här kommandona ställer in värdet för `$desc` variabeln till `A description` och hämtar värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-112">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="58a08-113">Exempel 2: Ange en global, skrivskyddad variabel</span><span class="sxs-lookup"><span data-stu-id="58a08-113">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="58a08-114">I det här exemplet skapas en global, skrivskyddad variabel som innehåller alla processer i systemet och sedan visas alla egenskaper för variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-114">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="58a08-115">Kommandot använder `Set-Variable` cmdleten för att skapa variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-115">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="58a08-116">Parametern **Passthru** används för att skapa ett objekt som representerar den nya variabeln och använder pipelinen ( `|` ) för att skicka objektet till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="58a08-116">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="58a08-117">Den använder **egenskaps** parametern för `Format-List` med värdet all () för `*` att visa alla egenskaper för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-117">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="58a08-118">Värdet `(Get-Process)` omges av parenteser för att säkerställa att det körs innan det lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-118">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="58a08-119">Annars innehåller variabeln orden "**Get-process**".</span><span class="sxs-lookup"><span data-stu-id="58a08-119">Otherwise, the variable contains the words "**Get-Process**".</span></span>

### <span data-ttu-id="58a08-120">Exempel 3: förstå offentliga eller privata variabler</span><span class="sxs-lookup"><span data-stu-id="58a08-120">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="58a08-121">Det här exemplet visar hur du ändrar synligheten för en variabel till `Private` .</span><span class="sxs-lookup"><span data-stu-id="58a08-121">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="58a08-122">Den här variabeln kan läsas och ändras av skript med de behörigheter som krävs, men den är inte synlig för användaren.</span><span class="sxs-lookup"><span data-stu-id="58a08-122">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

<span data-ttu-id="58a08-123">Det här kommandot visar hur du ändrar synligheten för en variabel till privat.</span><span class="sxs-lookup"><span data-stu-id="58a08-123">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="58a08-124">Den här variabeln kan läsas och ändras av skript med de behörigheter som krävs, men den är inte synlig för användaren.</span><span class="sxs-lookup"><span data-stu-id="58a08-124">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="58a08-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="58a08-125">PARAMETERS</span></span>

### <span data-ttu-id="58a08-126">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="58a08-126">-Description</span></span>

<span data-ttu-id="58a08-127">Anger beskrivningen av variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-127">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="58a08-128">-Undanta</span><span class="sxs-lookup"><span data-stu-id="58a08-128">-Exclude</span></span>

<span data-ttu-id="58a08-129">Anger en matris med objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="58a08-129">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="58a08-130">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="58a08-130">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="58a08-131">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="58a08-131">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="58a08-132">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="58a08-132">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="58a08-133">-Force</span><span class="sxs-lookup"><span data-stu-id="58a08-133">-Force</span></span>

<span data-ttu-id="58a08-134">Gör att du kan skapa en variabel med samma namn som en befintlig skrivskyddad variabel eller ändra värdet för en skrivskyddad variabel.</span><span class="sxs-lookup"><span data-stu-id="58a08-134">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="58a08-135">Som standard kan du skriva över en variabel, om inte variabeln har ett alternativ värde för `ReadOnly` eller `Constant` .</span><span class="sxs-lookup"><span data-stu-id="58a08-135">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="58a08-136">Mer information finns i **alternativ** parametern.</span><span class="sxs-lookup"><span data-stu-id="58a08-136">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="58a08-137">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="58a08-137">-Include</span></span>

<span data-ttu-id="58a08-138">Anger en matris med objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="58a08-138">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="58a08-139">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="58a08-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="58a08-140">Ange ett namn eller namn mönster, till exempel `c*` .</span><span class="sxs-lookup"><span data-stu-id="58a08-140">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="58a08-141">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="58a08-141">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="58a08-142">-Name</span><span class="sxs-lookup"><span data-stu-id="58a08-142">-Name</span></span>

<span data-ttu-id="58a08-143">Anger variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="58a08-143">Specifies the variable name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="58a08-144">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="58a08-144">-Option</span></span>

<span data-ttu-id="58a08-145">Anger värdet för egenskapen **Options** för variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-145">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="58a08-146">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="58a08-146">Valid values are:</span></span>

- <span data-ttu-id="58a08-147">`None`: Anger inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="58a08-147">`None`: Sets no options.</span></span> <span data-ttu-id="58a08-148">("Ingen" är standard.)</span><span class="sxs-lookup"><span data-stu-id="58a08-148">("None" is the default.)</span></span>
- <span data-ttu-id="58a08-149">`ReadOnly`: Kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="58a08-149">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="58a08-150">Kan inte ändras, med undantag för parametern Force.</span><span class="sxs-lookup"><span data-stu-id="58a08-150">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="58a08-151">`Constant`: Kan inte tas bort eller ändras.</span><span class="sxs-lookup"><span data-stu-id="58a08-151">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="58a08-152">`Constant` är endast giltig när du skapar en variabel.</span><span class="sxs-lookup"><span data-stu-id="58a08-152">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="58a08-153">Det går inte att ändra alternativen för en befintlig variabel till `Constant` .</span><span class="sxs-lookup"><span data-stu-id="58a08-153">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="58a08-154">`Private`: Variabeln är endast tillgänglig i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="58a08-154">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="58a08-155">`AllScope`: Variabeln kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="58a08-155">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58a08-156">– PassThru</span><span class="sxs-lookup"><span data-stu-id="58a08-156">-PassThru</span></span>

<span data-ttu-id="58a08-157">Returnerar ett objekt som representerar den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-157">Returns an object representing the new variable.</span></span> <span data-ttu-id="58a08-158">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="58a08-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="58a08-159">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="58a08-159">-Scope</span></span>

<span data-ttu-id="58a08-160">Anger variabelns omfång. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="58a08-160">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="58a08-161">Global</span><span class="sxs-lookup"><span data-stu-id="58a08-161">Global</span></span>
- <span data-ttu-id="58a08-162">Lokal</span><span class="sxs-lookup"><span data-stu-id="58a08-162">Local</span></span>
- <span data-ttu-id="58a08-163">Skript</span><span class="sxs-lookup"><span data-stu-id="58a08-163">Script</span></span>
- <span data-ttu-id="58a08-164">Privat</span><span class="sxs-lookup"><span data-stu-id="58a08-164">Private</span></span>
- <span data-ttu-id="58a08-165">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).</span><span class="sxs-lookup"><span data-stu-id="58a08-165">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="58a08-166">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="58a08-166">Local is the default.</span></span>

<span data-ttu-id="58a08-167">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="58a08-167">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58a08-168">-Värde</span><span class="sxs-lookup"><span data-stu-id="58a08-168">-Value</span></span>

<span data-ttu-id="58a08-169">Anger värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-169">Specifies the value of the variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="58a08-170">-Synlighet</span><span class="sxs-lookup"><span data-stu-id="58a08-170">-Visibility</span></span>

<span data-ttu-id="58a08-171">Bestämmer om variabeln är synlig utanför den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="58a08-171">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="58a08-172">Den här parametern är avsedd för användning i skript och kommandon som skickas till andra användare.</span><span class="sxs-lookup"><span data-stu-id="58a08-172">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="58a08-173">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="58a08-173">Valid values are:</span></span>

- <span data-ttu-id="58a08-174">Offentlig: variabeln är synlig.</span><span class="sxs-lookup"><span data-stu-id="58a08-174">Public:  The variable is visible.</span></span> <span data-ttu-id="58a08-175">("Offentlig" är standard.)</span><span class="sxs-lookup"><span data-stu-id="58a08-175">("Public" is the default.)</span></span>
- <span data-ttu-id="58a08-176">Privat: variabeln är inte synlig.</span><span class="sxs-lookup"><span data-stu-id="58a08-176">Private: The variable is not visible.</span></span>

<span data-ttu-id="58a08-177">När en variabel är privat visas den inte i listor med variabler, till exempel de som returneras av `Get-Variable` eller i visar **variabeln:** enhet.</span><span class="sxs-lookup"><span data-stu-id="58a08-177">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="58a08-178">Kommandon för att läsa eller ändra värdet för en privat variabel returnerar ett fel.</span><span class="sxs-lookup"><span data-stu-id="58a08-178">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="58a08-179">Användaren kan dock köra kommandon som använder en privat variabel om kommandona skrevs i den session där variabeln definierades.</span><span class="sxs-lookup"><span data-stu-id="58a08-179">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58a08-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="58a08-180">-Confirm</span></span>

<span data-ttu-id="58a08-181">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="58a08-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="58a08-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="58a08-182">-WhatIf</span></span>

<span data-ttu-id="58a08-183">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="58a08-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="58a08-184">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="58a08-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="58a08-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="58a08-185">CommonParameters</span></span>

<span data-ttu-id="58a08-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="58a08-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="58a08-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="58a08-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="58a08-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="58a08-188">INPUTS</span></span>

### <span data-ttu-id="58a08-189">System. Object</span><span class="sxs-lookup"><span data-stu-id="58a08-189">System.Object</span></span>

<span data-ttu-id="58a08-190">Du kan skicka ett objekt som representerar värdet för variabeln till `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="58a08-190">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="58a08-191">UTDATA</span><span class="sxs-lookup"><span data-stu-id="58a08-191">OUTPUTS</span></span>

### <span data-ttu-id="58a08-192">Ingen eller system. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="58a08-192">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="58a08-193">När du använder parametern **Passthru** `Set-Variable` genereras ett **system. Management. Automation. PSVariable** -objekt som representerar den nya eller ändrade variabeln.</span><span class="sxs-lookup"><span data-stu-id="58a08-193">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="58a08-194">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="58a08-194">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="58a08-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="58a08-195">NOTES</span></span>

## <span data-ttu-id="58a08-196">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="58a08-196">RELATED LINKS</span></span>

[<span data-ttu-id="58a08-197">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="58a08-197">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="58a08-198">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="58a08-198">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="58a08-199">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="58a08-199">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="58a08-200">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="58a08-200">Remove-Variable</span></span>](Remove-Variable.md)
