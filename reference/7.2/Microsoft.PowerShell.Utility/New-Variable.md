---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: c77eb9c64022d028c3c4b2de6bf4551886b940e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708587"
---
# <span data-ttu-id="14a26-102">New-Variable</span><span class="sxs-lookup"><span data-stu-id="14a26-102">New-Variable</span></span>

## <span data-ttu-id="14a26-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="14a26-103">SYNOPSIS</span></span>
<span data-ttu-id="14a26-104">Skapar en ny variabel.</span><span class="sxs-lookup"><span data-stu-id="14a26-104">Creates a new variable.</span></span>

## <span data-ttu-id="14a26-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="14a26-105">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="14a26-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="14a26-106">DESCRIPTION</span></span>
<span data-ttu-id="14a26-107">Cmdleten **New-Variable** skapar en ny variabel i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14a26-107">The **New-Variable** cmdlet creates a new variable in PowerShell.</span></span>
<span data-ttu-id="14a26-108">Du kan tilldela ett värde till variabeln när du skapar den, eller tilldela eller ändra värdet när det har skapats.</span><span class="sxs-lookup"><span data-stu-id="14a26-108">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="14a26-109">Du kan använda parametrarna för **New-Variable** för att ange egenskaperna för variabeln, ange en variabels omfång och avgöra om variablerna är offentliga eller privata.</span><span class="sxs-lookup"><span data-stu-id="14a26-109">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="14a26-110">Normalt skapar du en ny variabel genom att skriva variabel namnet och dess värde, till exempel `$Var = 3` , men du kan använda cmdleten **New-Variable** för att använda dess parametrar.</span><span class="sxs-lookup"><span data-stu-id="14a26-110">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="14a26-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="14a26-111">EXAMPLES</span></span>

### <span data-ttu-id="14a26-112">Exempel 1: skapa en variabel</span><span class="sxs-lookup"><span data-stu-id="14a26-112">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="14a26-113">Det här kommandot skapar en ny variabel med namnet dagar.</span><span class="sxs-lookup"><span data-stu-id="14a26-113">This command creates a new variable named days.</span></span>
<span data-ttu-id="14a26-114">Du behöver inte ange *namn* parametern.</span><span class="sxs-lookup"><span data-stu-id="14a26-114">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="14a26-115">Exempel 2: skapa en variabel och tilldela den ett värde</span><span class="sxs-lookup"><span data-stu-id="14a26-115">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="14a26-116">Det här kommandot skapar en variabel med namnet Postummer och tilldelar den värdet 98033.</span><span class="sxs-lookup"><span data-stu-id="14a26-116">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="14a26-117">Exempel 3: skapa en variabel med alternativet ReadOnly</span><span class="sxs-lookup"><span data-stu-id="14a26-117">Example 3: Create a variable with the ReadOnly option</span></span>

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

<span data-ttu-id="14a26-118">Det här exemplet visar hur du använder alternativet ReadOnly för **New-Variable** för att skydda en variabel från att skrivas över.</span><span class="sxs-lookup"><span data-stu-id="14a26-118">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="14a26-119">Det första kommandot skapar en ny variabel med namnet max och anger dess värde till 256.</span><span class="sxs-lookup"><span data-stu-id="14a26-119">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="14a26-120">Den använder *alternativ* parametern med värdet ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="14a26-120">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="14a26-121">Det andra kommandot försöker skapa en andra variabel med samma namn.</span><span class="sxs-lookup"><span data-stu-id="14a26-121">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="14a26-122">Det här kommandot returnerar ett fel eftersom det skrivskyddade alternativet är inställt på variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-122">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="14a26-123">Det tredje kommandot använder *Force* -parametern för att åsidosätta det skrivskyddade skyddet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-123">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="14a26-124">I det här fallet slutförs kommandot för att skapa en ny variabel med samma namn.</span><span class="sxs-lookup"><span data-stu-id="14a26-124">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="14a26-125">Exempel 4: skapa en privat variabel</span><span class="sxs-lookup"><span data-stu-id="14a26-125">Example 4: Create a private variable</span></span>

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

<span data-ttu-id="14a26-126">Det här kommandot visar beteendet för en privat variabel i en modul.</span><span class="sxs-lookup"><span data-stu-id="14a26-126">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="14a26-127">Modulen innehåller Get-Counter-cmdleten, som har en privat variabel med namnet Counter.</span><span class="sxs-lookup"><span data-stu-id="14a26-127">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="14a26-128">Kommandot använder parametern *visibility* med värdet Private för att skapa variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-128">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="14a26-129">Exempel resultatet visar beteendet för en privat variabel.</span><span class="sxs-lookup"><span data-stu-id="14a26-129">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="14a26-130">Användaren som har läst in modulen kan inte Visa eller ändra värdet för Counter-variabeln, men räknar variabeln kan läsas och ändras av kommandona i modulen.</span><span class="sxs-lookup"><span data-stu-id="14a26-130">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="14a26-131">Exempel 5: skapa en variabel med ett blank steg</span><span class="sxs-lookup"><span data-stu-id="14a26-131">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="14a26-132">Det här kommandot visar att variabler med blank steg kan skapas.</span><span class="sxs-lookup"><span data-stu-id="14a26-132">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="14a26-133">Du kan komma åt variablerna med hjälp av cmdleten **Get-Variable** eller direkt genom att begränsa en variabel med klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="14a26-133">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="14a26-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="14a26-134">PARAMETERS</span></span>

### <span data-ttu-id="14a26-135">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="14a26-135">-Description</span></span>
<span data-ttu-id="14a26-136">Anger en beskrivning av variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-136">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="14a26-137">-Force</span><span class="sxs-lookup"><span data-stu-id="14a26-137">-Force</span></span>
<span data-ttu-id="14a26-138">Anger att cmdleten skapar en variabel med samma namn som en befintlig skrivskyddad variabel.</span><span class="sxs-lookup"><span data-stu-id="14a26-138">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="14a26-139">Som standard kan du skriva över en variabel om inte variabeln har ett alternativ värde av ReadOnly eller konstant.</span><span class="sxs-lookup"><span data-stu-id="14a26-139">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="14a26-140">Mer information finns i *alternativ* parametern.</span><span class="sxs-lookup"><span data-stu-id="14a26-140">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="14a26-141">-Name</span><span class="sxs-lookup"><span data-stu-id="14a26-141">-Name</span></span>
<span data-ttu-id="14a26-142">Anger ett namn för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-142">Specifies a name for the new variable.</span></span>

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

### <span data-ttu-id="14a26-143">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="14a26-143">-Option</span></span>
<span data-ttu-id="14a26-144">Anger värdet för egenskapen **Options** för variabeln. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="14a26-144">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="14a26-145">Inga.</span><span class="sxs-lookup"><span data-stu-id="14a26-145">None.</span></span>
<span data-ttu-id="14a26-146">Anger inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="14a26-146">Sets no options.</span></span>
<span data-ttu-id="14a26-147">(Ingen är standard.)</span><span class="sxs-lookup"><span data-stu-id="14a26-147">(None is the default.)</span></span>
- <span data-ttu-id="14a26-148">ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="14a26-148">ReadOnly.</span></span>
<span data-ttu-id="14a26-149">Kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="14a26-149">Can be deleted.</span></span>
<span data-ttu-id="14a26-150">Kan inte ändras, med undantag för parametern *Force* .</span><span class="sxs-lookup"><span data-stu-id="14a26-150">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="14a26-151">Personligt.</span><span class="sxs-lookup"><span data-stu-id="14a26-151">Private.</span></span>
<span data-ttu-id="14a26-152">Variabeln är endast tillgänglig i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="14a26-152">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="14a26-153">AllScope.</span><span class="sxs-lookup"><span data-stu-id="14a26-153">AllScope.</span></span>
<span data-ttu-id="14a26-154">Variabeln kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="14a26-154">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="14a26-155">Konstant.</span><span class="sxs-lookup"><span data-stu-id="14a26-155">Constant.</span></span>
<span data-ttu-id="14a26-156">Kan inte tas bort eller ändras.</span><span class="sxs-lookup"><span data-stu-id="14a26-156">Cannot be deleted or changed.</span></span>
<span data-ttu-id="14a26-157">Konstant är bara giltig när du skapar en variabel.</span><span class="sxs-lookup"><span data-stu-id="14a26-157">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="14a26-158">Det går inte att ändra alternativen för en befintlig variabel till konstant.</span><span class="sxs-lookup"><span data-stu-id="14a26-158">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="14a26-159">Om du vill se egenskapen **alternativ** för alla variabler i sessionen skriver du `Get-Variable | Format-Table -Property name, options -autosize` .</span><span class="sxs-lookup"><span data-stu-id="14a26-159">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="14a26-160">– PassThru</span><span class="sxs-lookup"><span data-stu-id="14a26-160">-PassThru</span></span>
<span data-ttu-id="14a26-161">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="14a26-161">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="14a26-162">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="14a26-162">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="14a26-163">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="14a26-163">-Scope</span></span>
<span data-ttu-id="14a26-164">Anger omfånget för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-164">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="14a26-165">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="14a26-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="14a26-166">EAN.</span><span class="sxs-lookup"><span data-stu-id="14a26-166">Global.</span></span>
<span data-ttu-id="14a26-167">Variabler som skapas i det globala omfånget är tillgängliga överallt i en PowerShell-process.</span><span class="sxs-lookup"><span data-stu-id="14a26-167">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="14a26-168">Inställningar.</span><span class="sxs-lookup"><span data-stu-id="14a26-168">Local.</span></span>
<span data-ttu-id="14a26-169">Det lokala omfånget refererar till det aktuella omfånget. Detta kan vara vilken omfattning som helst, beroende på kontexten.</span><span class="sxs-lookup"><span data-stu-id="14a26-169">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="14a26-170">Över.</span><span class="sxs-lookup"><span data-stu-id="14a26-170">Script.</span></span>
<span data-ttu-id="14a26-171">Variabler som skapas i skript omfånget är endast tillgängliga inom skript filen eller modulen de skapas i.</span><span class="sxs-lookup"><span data-stu-id="14a26-171">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="14a26-172">Personligt.</span><span class="sxs-lookup"><span data-stu-id="14a26-172">Private.</span></span>
<span data-ttu-id="14a26-173">Det går inte att komma åt variabler som har skapats i det privata området utanför den omfattning som de finns i.</span><span class="sxs-lookup"><span data-stu-id="14a26-173">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="14a26-174">Du kan använda privat omfattning för att skapa en privat version av ett objekt med samma namn i ett annat omfång.</span><span class="sxs-lookup"><span data-stu-id="14a26-174">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="14a26-175">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget, 1 är överordnat, 2 överordnat till det överordnade omfånget osv.).</span><span class="sxs-lookup"><span data-stu-id="14a26-175">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="14a26-176">Det går inte att använda negativa tal.</span><span class="sxs-lookup"><span data-stu-id="14a26-176">Negative numbers cannot be used.</span></span>

<span data-ttu-id="14a26-177">Lokalt är standard omfånget när omfångs parametern inte anges.</span><span class="sxs-lookup"><span data-stu-id="14a26-177">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="14a26-178">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="14a26-178">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="14a26-179">-Värde</span><span class="sxs-lookup"><span data-stu-id="14a26-179">-Value</span></span>
<span data-ttu-id="14a26-180">Anger det inledande värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-180">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="14a26-181">-Synlighet</span><span class="sxs-lookup"><span data-stu-id="14a26-181">-Visibility</span></span>
<span data-ttu-id="14a26-182">Bestämmer om variabeln är synlig utanför den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="14a26-182">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="14a26-183">Den här parametern är avsedd för användning i skript och kommandon som skickas till andra användare.</span><span class="sxs-lookup"><span data-stu-id="14a26-183">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="14a26-184">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="14a26-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="14a26-185">Folkhälsan.</span><span class="sxs-lookup"><span data-stu-id="14a26-185">Public.</span></span>
<span data-ttu-id="14a26-186">Variabeln är synlig.</span><span class="sxs-lookup"><span data-stu-id="14a26-186">The variable is visible.</span></span>
<span data-ttu-id="14a26-187">(Offentlig är standard.)</span><span class="sxs-lookup"><span data-stu-id="14a26-187">(Public is the default.)</span></span>
- <span data-ttu-id="14a26-188">Personligt.</span><span class="sxs-lookup"><span data-stu-id="14a26-188">Private.</span></span>
<span data-ttu-id="14a26-189">Variabeln är inte synlig.</span><span class="sxs-lookup"><span data-stu-id="14a26-189">The variable is not visible.</span></span>

<span data-ttu-id="14a26-190">När en variabel är privat visas den inte i listor med variabler, t. ex. de som returneras av Get-Variable eller som visas i variabeln: enhet.</span><span class="sxs-lookup"><span data-stu-id="14a26-190">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="14a26-191">Kommandon för att läsa eller ändra värdet för en privat variabel returnerar ett fel.</span><span class="sxs-lookup"><span data-stu-id="14a26-191">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="14a26-192">Användaren kan dock köra kommandon som använder en privat variabel om kommandona skrevs i den session där variabeln definierades.</span><span class="sxs-lookup"><span data-stu-id="14a26-192">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14a26-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="14a26-193">-Confirm</span></span>
<span data-ttu-id="14a26-194">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="14a26-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="14a26-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="14a26-195">-WhatIf</span></span>
<span data-ttu-id="14a26-196">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="14a26-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="14a26-197">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="14a26-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="14a26-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14a26-198">CommonParameters</span></span>
<span data-ttu-id="14a26-199">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14a26-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14a26-200">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14a26-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14a26-201">INDATA</span><span class="sxs-lookup"><span data-stu-id="14a26-201">INPUTS</span></span>

### <span data-ttu-id="14a26-202">System. Object</span><span class="sxs-lookup"><span data-stu-id="14a26-202">System.Object</span></span>
<span data-ttu-id="14a26-203">Du kan skicka vidare ett värde till **New-Variable**.</span><span class="sxs-lookup"><span data-stu-id="14a26-203">You can pipe a value to **New-Variable**.</span></span>

## <span data-ttu-id="14a26-204">UTDATA</span><span class="sxs-lookup"><span data-stu-id="14a26-204">OUTPUTS</span></span>

### <span data-ttu-id="14a26-205">Ingen eller system. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="14a26-205">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="14a26-206">När du använder parametern *Passthru* genererar **New-variabel** ett **system. Management. Automation. PSVariable** -objekt som representerar den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="14a26-206">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="14a26-207">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="14a26-207">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="14a26-208">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="14a26-208">NOTES</span></span>

## <span data-ttu-id="14a26-209">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="14a26-209">RELATED LINKS</span></span>

[<span data-ttu-id="14a26-210">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="14a26-210">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="14a26-211">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="14a26-211">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="14a26-212">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="14a26-212">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="14a26-213">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="14a26-213">Set-Variable</span></span>](Set-Variable.md)

