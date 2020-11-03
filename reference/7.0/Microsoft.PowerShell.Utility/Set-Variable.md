---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 876129fc8df9a78df257bf95220fc6587e68b9a2
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273567"
---
# <span data-ttu-id="03272-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="03272-103">Set-Variable</span></span>

## <span data-ttu-id="03272-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="03272-104">SYNOPSIS</span></span>
<span data-ttu-id="03272-105">Anger värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="03272-105">Sets the value of a variable.</span></span> <span data-ttu-id="03272-106">Skapar variabeln om en med det begärda namnet inte finns.</span><span class="sxs-lookup"><span data-stu-id="03272-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="03272-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="03272-107">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="03272-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="03272-108">DESCRIPTION</span></span>

<span data-ttu-id="03272-109">`Set-Variable`Cmdlet: en tilldelar ett värde till en angiven variabel eller ändrar det aktuella värdet.</span><span class="sxs-lookup"><span data-stu-id="03272-109">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="03272-110">Om variabeln inte finns skapar cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="03272-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="03272-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="03272-111">EXAMPLES</span></span>

### <span data-ttu-id="03272-112">Exempel 1: Ange en variabel och hämta dess värde</span><span class="sxs-lookup"><span data-stu-id="03272-112">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="03272-113">De här kommandona ställer in värdet för `$desc` variabeln till `A description` och hämtar värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-113">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="03272-114">Exempel 2: Ange en global, skrivskyddad variabel</span><span class="sxs-lookup"><span data-stu-id="03272-114">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="03272-115">I det här exemplet skapas en global, skrivskyddad variabel som innehåller alla processer i systemet och sedan visas alla egenskaper för variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-115">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="03272-116">Kommandot använder `Set-Variable` cmdleten för att skapa variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-116">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="03272-117">Parametern **Passthru** används för att skapa ett objekt som representerar den nya variabeln och använder pipelinen ( `|` ) för att skicka objektet till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="03272-117">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="03272-118">Den använder **egenskaps** parametern för `Format-List` med värdet all () för `*` att visa alla egenskaper för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-118">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="03272-119">Värdet `(Get-Process)` omges av parenteser för att säkerställa att det körs innan det lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-119">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="03272-120">Annars innehåller variabeln orden " **Get-process** ".</span><span class="sxs-lookup"><span data-stu-id="03272-120">Otherwise, the variable contains the words " **Get-Process** ".</span></span>

### <span data-ttu-id="03272-121">Exempel 3: förstå offentliga eller privata variabler</span><span class="sxs-lookup"><span data-stu-id="03272-121">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="03272-122">Det här exemplet visar hur du ändrar synligheten för en variabel till `Private` .</span><span class="sxs-lookup"><span data-stu-id="03272-122">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="03272-123">Den här variabeln kan läsas och ändras av skript med de behörigheter som krävs, men den är inte synlig för användaren.</span><span class="sxs-lookup"><span data-stu-id="03272-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

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

<span data-ttu-id="03272-124">Det här kommandot visar hur du ändrar synligheten för en variabel till privat.</span><span class="sxs-lookup"><span data-stu-id="03272-124">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="03272-125">Den här variabeln kan läsas och ändras av skript med de behörigheter som krävs, men den är inte synlig för användaren.</span><span class="sxs-lookup"><span data-stu-id="03272-125">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="03272-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="03272-126">PARAMETERS</span></span>

### <span data-ttu-id="03272-127">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="03272-127">-Description</span></span>

<span data-ttu-id="03272-128">Anger beskrivningen av variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-128">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="03272-129">-Undanta</span><span class="sxs-lookup"><span data-stu-id="03272-129">-Exclude</span></span>

<span data-ttu-id="03272-130">Anger en matris med objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="03272-130">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="03272-131">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="03272-131">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="03272-132">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="03272-132">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="03272-133">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="03272-133">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="03272-134">-Force</span><span class="sxs-lookup"><span data-stu-id="03272-134">-Force</span></span>

<span data-ttu-id="03272-135">Gör att du kan skapa en variabel med samma namn som en befintlig skrivskyddad variabel eller ändra värdet för en skrivskyddad variabel.</span><span class="sxs-lookup"><span data-stu-id="03272-135">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="03272-136">Som standard kan du skriva över en variabel, om inte variabeln har ett alternativ värde för `ReadOnly` eller `Constant` .</span><span class="sxs-lookup"><span data-stu-id="03272-136">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="03272-137">Mer information finns i **alternativ** parametern.</span><span class="sxs-lookup"><span data-stu-id="03272-137">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="03272-138">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="03272-138">-Include</span></span>

<span data-ttu-id="03272-139">Anger en matris med objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="03272-139">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="03272-140">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="03272-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="03272-141">Ange ett namn eller namn mönster, till exempel `c*` .</span><span class="sxs-lookup"><span data-stu-id="03272-141">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="03272-142">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="03272-142">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="03272-143">-Name</span><span class="sxs-lookup"><span data-stu-id="03272-143">-Name</span></span>

<span data-ttu-id="03272-144">Anger variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="03272-144">Specifies the variable name.</span></span>

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

### <span data-ttu-id="03272-145">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="03272-145">-Option</span></span>

<span data-ttu-id="03272-146">Anger värdet för egenskapen **Options** för variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-146">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="03272-147">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="03272-147">Valid values are:</span></span>

- <span data-ttu-id="03272-148">`None`: Anger inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="03272-148">`None`: Sets no options.</span></span> <span data-ttu-id="03272-149">("Ingen" är standard.)</span><span class="sxs-lookup"><span data-stu-id="03272-149">("None" is the default.)</span></span>
- <span data-ttu-id="03272-150">`ReadOnly`: Kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="03272-150">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="03272-151">Kan inte ändras, med undantag för parametern Force.</span><span class="sxs-lookup"><span data-stu-id="03272-151">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="03272-152">`Constant`: Kan inte tas bort eller ändras.</span><span class="sxs-lookup"><span data-stu-id="03272-152">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="03272-153">`Constant` är endast giltig när du skapar en variabel.</span><span class="sxs-lookup"><span data-stu-id="03272-153">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="03272-154">Det går inte att ändra alternativen för en befintlig variabel till `Constant` .</span><span class="sxs-lookup"><span data-stu-id="03272-154">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="03272-155">`Private`: Variabeln är endast tillgänglig i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="03272-155">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="03272-156">`AllScope`: Variabeln kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="03272-156">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

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

### <span data-ttu-id="03272-157">– PassThru</span><span class="sxs-lookup"><span data-stu-id="03272-157">-PassThru</span></span>

<span data-ttu-id="03272-158">Returnerar ett objekt som representerar den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-158">Returns an object representing the new variable.</span></span> <span data-ttu-id="03272-159">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="03272-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="03272-160">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="03272-160">-Scope</span></span>

<span data-ttu-id="03272-161">Anger variabelns omfång. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="03272-161">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="03272-162">Global</span><span class="sxs-lookup"><span data-stu-id="03272-162">Global</span></span>
- <span data-ttu-id="03272-163">Lokal</span><span class="sxs-lookup"><span data-stu-id="03272-163">Local</span></span>
- <span data-ttu-id="03272-164">Skript</span><span class="sxs-lookup"><span data-stu-id="03272-164">Script</span></span>
- <span data-ttu-id="03272-165">Privat</span><span class="sxs-lookup"><span data-stu-id="03272-165">Private</span></span>
- <span data-ttu-id="03272-166">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).</span><span class="sxs-lookup"><span data-stu-id="03272-166">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="03272-167">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="03272-167">Local is the default.</span></span>

<span data-ttu-id="03272-168">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="03272-168">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

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

### <span data-ttu-id="03272-169">-Värde</span><span class="sxs-lookup"><span data-stu-id="03272-169">-Value</span></span>

<span data-ttu-id="03272-170">Anger värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-170">Specifies the value of the variable.</span></span>

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

### <span data-ttu-id="03272-171">-Synlighet</span><span class="sxs-lookup"><span data-stu-id="03272-171">-Visibility</span></span>

<span data-ttu-id="03272-172">Bestämmer om variabeln är synlig utanför den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="03272-172">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="03272-173">Den här parametern är avsedd för användning i skript och kommandon som skickas till andra användare.</span><span class="sxs-lookup"><span data-stu-id="03272-173">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="03272-174">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="03272-174">Valid values are:</span></span>

- <span data-ttu-id="03272-175">Offentlig: variabeln är synlig.</span><span class="sxs-lookup"><span data-stu-id="03272-175">Public:  The variable is visible.</span></span> <span data-ttu-id="03272-176">("Offentlig" är standard.)</span><span class="sxs-lookup"><span data-stu-id="03272-176">("Public" is the default.)</span></span>
- <span data-ttu-id="03272-177">Privat: variabeln är inte synlig.</span><span class="sxs-lookup"><span data-stu-id="03272-177">Private: The variable is not visible.</span></span>

<span data-ttu-id="03272-178">När en variabel är privat visas den inte i listor med variabler, till exempel de som returneras av `Get-Variable` eller i visar **variabeln:** enhet.</span><span class="sxs-lookup"><span data-stu-id="03272-178">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="03272-179">Kommandon för att läsa eller ändra värdet för en privat variabel returnerar ett fel.</span><span class="sxs-lookup"><span data-stu-id="03272-179">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="03272-180">Användaren kan dock köra kommandon som använder en privat variabel om kommandona skrevs i den session där variabeln definierades.</span><span class="sxs-lookup"><span data-stu-id="03272-180">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="03272-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="03272-181">-Confirm</span></span>

<span data-ttu-id="03272-182">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="03272-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="03272-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="03272-183">-WhatIf</span></span>

<span data-ttu-id="03272-184">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="03272-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="03272-185">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="03272-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="03272-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="03272-186">CommonParameters</span></span>

<span data-ttu-id="03272-187">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="03272-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="03272-188">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="03272-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="03272-189">INDATA</span><span class="sxs-lookup"><span data-stu-id="03272-189">INPUTS</span></span>

### <span data-ttu-id="03272-190">System. Object</span><span class="sxs-lookup"><span data-stu-id="03272-190">System.Object</span></span>

<span data-ttu-id="03272-191">Du kan skicka ett objekt som representerar värdet för variabeln till `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="03272-191">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="03272-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="03272-192">OUTPUTS</span></span>

### <span data-ttu-id="03272-193">Ingen eller system. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="03272-193">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="03272-194">När du använder parametern **Passthru** `Set-Variable` genereras ett **system. Management. Automation. PSVariable** -objekt som representerar den nya eller ändrade variabeln.</span><span class="sxs-lookup"><span data-stu-id="03272-194">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="03272-195">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="03272-195">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="03272-196">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="03272-196">NOTES</span></span>

## <span data-ttu-id="03272-197">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="03272-197">RELATED LINKS</span></span>

[<span data-ttu-id="03272-198">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="03272-198">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="03272-199">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="03272-199">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="03272-200">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="03272-200">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="03272-201">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="03272-201">Remove-Variable</span></span>](Remove-Variable.md)
