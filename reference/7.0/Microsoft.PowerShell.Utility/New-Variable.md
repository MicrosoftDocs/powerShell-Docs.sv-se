---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: 8d45f8b6b0272394fe855be07243412bd3a15d71
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262376"
---
# <span data-ttu-id="5f2a0-103">New-Variable</span><span class="sxs-lookup"><span data-stu-id="5f2a0-103">New-Variable</span></span>

## <span data-ttu-id="5f2a0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5f2a0-104">SYNOPSIS</span></span>
<span data-ttu-id="5f2a0-105">Skapar en ny variabel.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-105">Creates a new variable.</span></span>

## <span data-ttu-id="5f2a0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f2a0-106">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5f2a0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5f2a0-107">DESCRIPTION</span></span>
<span data-ttu-id="5f2a0-108">Cmdleten **New-Variable** skapar en ny variabel i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-108">The **New-Variable** cmdlet creates a new variable in PowerShell.</span></span>
<span data-ttu-id="5f2a0-109">Du kan tilldela ett värde till variabeln när du skapar den, eller tilldela eller ändra värdet när det har skapats.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-109">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="5f2a0-110">Du kan använda parametrarna för **New-Variable** för att ange egenskaperna för variabeln, ange en variabels omfång och avgöra om variablerna är offentliga eller privata.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-110">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="5f2a0-111">Normalt skapar du en ny variabel genom att skriva variabel namnet och dess värde, till exempel `$Var = 3` , men du kan använda cmdleten **New-Variable** för att använda dess parametrar.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-111">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="5f2a0-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5f2a0-112">EXAMPLES</span></span>

### <span data-ttu-id="5f2a0-113">Exempel 1: skapa en variabel</span><span class="sxs-lookup"><span data-stu-id="5f2a0-113">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="5f2a0-114">Det här kommandot skapar en ny variabel med namnet dagar.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-114">This command creates a new variable named days.</span></span>
<span data-ttu-id="5f2a0-115">Du behöver inte ange *namn* parametern.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-115">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="5f2a0-116">Exempel 2: skapa en variabel och tilldela den ett värde</span><span class="sxs-lookup"><span data-stu-id="5f2a0-116">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="5f2a0-117">Det här kommandot skapar en variabel med namnet Postummer och tilldelar den värdet 98033.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-117">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="5f2a0-118">Exempel 3: skapa en variabel med alternativet ReadOnly</span><span class="sxs-lookup"><span data-stu-id="5f2a0-118">Example 3: Create a variable with the ReadOnly option</span></span>

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

<span data-ttu-id="5f2a0-119">Det här exemplet visar hur du använder alternativet ReadOnly för **New-Variable** för att skydda en variabel från att skrivas över.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-119">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="5f2a0-120">Det första kommandot skapar en ny variabel med namnet max och anger dess värde till 256.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-120">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="5f2a0-121">Den använder *alternativ* parametern med värdet ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-121">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="5f2a0-122">Det andra kommandot försöker skapa en andra variabel med samma namn.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-122">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="5f2a0-123">Det här kommandot returnerar ett fel eftersom det skrivskyddade alternativet är inställt på variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-123">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="5f2a0-124">Det tredje kommandot använder *Force* -parametern för att åsidosätta det skrivskyddade skyddet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-124">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="5f2a0-125">I det här fallet slutförs kommandot för att skapa en ny variabel med samma namn.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-125">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="5f2a0-126">Exempel 4: skapa en privat variabel</span><span class="sxs-lookup"><span data-stu-id="5f2a0-126">Example 4: Create a private variable</span></span>

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

<span data-ttu-id="5f2a0-127">Det här kommandot visar beteendet för en privat variabel i en modul.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-127">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="5f2a0-128">Modulen innehåller Get-Counter-cmdleten, som har en privat variabel med namnet Counter.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-128">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="5f2a0-129">Kommandot använder parametern *visibility* med värdet Private för att skapa variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-129">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="5f2a0-130">Exempel resultatet visar beteendet för en privat variabel.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-130">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="5f2a0-131">Användaren som har läst in modulen kan inte Visa eller ändra värdet för Counter-variabeln, men räknar variabeln kan läsas och ändras av kommandona i modulen.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-131">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="5f2a0-132">Exempel 5: skapa en variabel med ett blank steg</span><span class="sxs-lookup"><span data-stu-id="5f2a0-132">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="5f2a0-133">Det här kommandot visar att variabler med blank steg kan skapas.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-133">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="5f2a0-134">Du kan komma åt variablerna med hjälp av cmdleten **Get-Variable** eller direkt genom att begränsa en variabel med klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-134">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="5f2a0-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5f2a0-135">PARAMETERS</span></span>

### <span data-ttu-id="5f2a0-136">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5f2a0-136">-Description</span></span>
<span data-ttu-id="5f2a0-137">Anger en beskrivning av variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-137">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="5f2a0-138">-Force</span><span class="sxs-lookup"><span data-stu-id="5f2a0-138">-Force</span></span>
<span data-ttu-id="5f2a0-139">Anger att cmdleten skapar en variabel med samma namn som en befintlig skrivskyddad variabel.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-139">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="5f2a0-140">Som standard kan du skriva över en variabel om inte variabeln har ett alternativ värde av ReadOnly eller konstant.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-140">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="5f2a0-141">Mer information finns i *alternativ* parametern.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-141">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="5f2a0-142">-Name</span><span class="sxs-lookup"><span data-stu-id="5f2a0-142">-Name</span></span>
<span data-ttu-id="5f2a0-143">Anger ett namn för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-143">Specifies a name for the new variable.</span></span>

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

### <span data-ttu-id="5f2a0-144">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="5f2a0-144">-Option</span></span>
<span data-ttu-id="5f2a0-145">Anger värdet för egenskapen **Options** för variabeln. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5f2a0-145">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5f2a0-146">Inga.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-146">None.</span></span>
<span data-ttu-id="5f2a0-147">Anger inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-147">Sets no options.</span></span>
<span data-ttu-id="5f2a0-148">(Ingen är standard.)</span><span class="sxs-lookup"><span data-stu-id="5f2a0-148">(None is the default.)</span></span>
- <span data-ttu-id="5f2a0-149">ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-149">ReadOnly.</span></span>
<span data-ttu-id="5f2a0-150">Kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-150">Can be deleted.</span></span>
<span data-ttu-id="5f2a0-151">Kan inte ändras, med undantag för parametern *Force* .</span><span class="sxs-lookup"><span data-stu-id="5f2a0-151">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="5f2a0-152">Personligt.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-152">Private.</span></span>
<span data-ttu-id="5f2a0-153">Variabeln är endast tillgänglig i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-153">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="5f2a0-154">AllScope.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-154">AllScope.</span></span>
<span data-ttu-id="5f2a0-155">Variabeln kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-155">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="5f2a0-156">Konstant.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-156">Constant.</span></span>
<span data-ttu-id="5f2a0-157">Kan inte tas bort eller ändras.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-157">Cannot be deleted or changed.</span></span>
<span data-ttu-id="5f2a0-158">Konstant är bara giltig när du skapar en variabel.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-158">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="5f2a0-159">Det går inte att ändra alternativen för en befintlig variabel till konstant.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-159">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="5f2a0-160">Om du vill se egenskapen **alternativ** för alla variabler i sessionen skriver du `Get-Variable | Format-Table -Property name, options -autosize` .</span><span class="sxs-lookup"><span data-stu-id="5f2a0-160">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="5f2a0-161">– PassThru</span><span class="sxs-lookup"><span data-stu-id="5f2a0-161">-PassThru</span></span>
<span data-ttu-id="5f2a0-162">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-162">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="5f2a0-163">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-163">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5f2a0-164">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="5f2a0-164">-Scope</span></span>
<span data-ttu-id="5f2a0-165">Anger omfånget för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-165">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="5f2a0-166">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5f2a0-166">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5f2a0-167">EAN.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-167">Global.</span></span>
<span data-ttu-id="5f2a0-168">Variabler som skapas i det globala omfånget är tillgängliga överallt i en PowerShell-process.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-168">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="5f2a0-169">Inställningar.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-169">Local.</span></span>
<span data-ttu-id="5f2a0-170">Det lokala omfånget refererar till det aktuella omfånget. Detta kan vara vilken omfattning som helst, beroende på kontexten.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-170">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="5f2a0-171">Över.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-171">Script.</span></span>
<span data-ttu-id="5f2a0-172">Variabler som skapas i skript omfånget är endast tillgängliga inom skript filen eller modulen de skapas i.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-172">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="5f2a0-173">Personligt.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-173">Private.</span></span>
<span data-ttu-id="5f2a0-174">Det går inte att komma åt variabler som har skapats i det privata området utanför den omfattning som de finns i.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-174">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="5f2a0-175">Du kan använda privat omfattning för att skapa en privat version av ett objekt med samma namn i ett annat omfång.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-175">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="5f2a0-176">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget, 1 är överordnat, 2 överordnat till det överordnade omfånget osv.).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-176">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="5f2a0-177">Det går inte att använda negativa tal.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-177">Negative numbers cannot be used.</span></span>

<span data-ttu-id="5f2a0-178">Lokalt är standard omfånget när omfångs parametern inte anges.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-178">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="5f2a0-179">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-179">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="5f2a0-180">-Värde</span><span class="sxs-lookup"><span data-stu-id="5f2a0-180">-Value</span></span>
<span data-ttu-id="5f2a0-181">Anger det inledande värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-181">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="5f2a0-182">-Synlighet</span><span class="sxs-lookup"><span data-stu-id="5f2a0-182">-Visibility</span></span>
<span data-ttu-id="5f2a0-183">Bestämmer om variabeln är synlig utanför den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-183">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="5f2a0-184">Den här parametern är avsedd för användning i skript och kommandon som skickas till andra användare.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-184">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="5f2a0-185">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5f2a0-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5f2a0-186">Folkhälsan.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-186">Public.</span></span>
<span data-ttu-id="5f2a0-187">Variabeln är synlig.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-187">The variable is visible.</span></span>
<span data-ttu-id="5f2a0-188">(Offentlig är standard.)</span><span class="sxs-lookup"><span data-stu-id="5f2a0-188">(Public is the default.)</span></span>
- <span data-ttu-id="5f2a0-189">Personligt.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-189">Private.</span></span>
<span data-ttu-id="5f2a0-190">Variabeln är inte synlig.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-190">The variable is not visible.</span></span>

<span data-ttu-id="5f2a0-191">När en variabel är privat visas den inte i listor med variabler, t. ex. de som returneras av Get-Variable eller som visas i variabeln: enhet.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-191">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="5f2a0-192">Kommandon för att läsa eller ändra värdet för en privat variabel returnerar ett fel.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-192">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="5f2a0-193">Användaren kan dock köra kommandon som använder en privat variabel om kommandona skrevs i den session där variabeln definierades.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-193">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="5f2a0-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5f2a0-194">-Confirm</span></span>
<span data-ttu-id="5f2a0-195">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5f2a0-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5f2a0-196">-WhatIf</span></span>
<span data-ttu-id="5f2a0-197">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5f2a0-198">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5f2a0-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f2a0-199">CommonParameters</span></span>
<span data-ttu-id="5f2a0-200">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f2a0-201">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f2a0-202">INDATA</span><span class="sxs-lookup"><span data-stu-id="5f2a0-202">INPUTS</span></span>

### <span data-ttu-id="5f2a0-203">System. Object</span><span class="sxs-lookup"><span data-stu-id="5f2a0-203">System.Object</span></span>
<span data-ttu-id="5f2a0-204">Du kan skicka vidare ett värde till **New-Variable**.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-204">You can pipe a value to **New-Variable**.</span></span>

## <span data-ttu-id="5f2a0-205">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5f2a0-205">OUTPUTS</span></span>

### <span data-ttu-id="5f2a0-206">Ingen eller system. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="5f2a0-206">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="5f2a0-207">När du använder parametern *Passthru* genererar **New-variabel** ett **system. Management. Automation. PSVariable** -objekt som representerar den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-207">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="5f2a0-208">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5f2a0-209">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5f2a0-209">NOTES</span></span>

## <span data-ttu-id="5f2a0-210">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5f2a0-210">RELATED LINKS</span></span>

[<span data-ttu-id="5f2a0-211">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="5f2a0-211">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="5f2a0-212">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="5f2a0-212">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="5f2a0-213">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="5f2a0-213">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="5f2a0-214">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="5f2a0-214">Set-Variable</span></span>](Set-Variable.md)