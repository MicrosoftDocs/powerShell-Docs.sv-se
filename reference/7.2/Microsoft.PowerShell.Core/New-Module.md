---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 487fd85bdcc918b7fb360f9c9d23388a06b35f86
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710501"
---
# <span data-ttu-id="1b2ab-102">New-Module</span><span class="sxs-lookup"><span data-stu-id="1b2ab-102">New-Module</span></span>

## <span data-ttu-id="1b2ab-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1b2ab-103">SYNOPSIS</span></span>
<span data-ttu-id="1b2ab-104">Skapar en ny dynamisk modul som bara finns i minnet.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-104">Creates a new dynamic module that exists only in memory.</span></span>

## <span data-ttu-id="1b2ab-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b2ab-105">SYNTAX</span></span>

### <span data-ttu-id="1b2ab-106">Script block (standard)</span><span class="sxs-lookup"><span data-stu-id="1b2ab-106">ScriptBlock (Default)</span></span>

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1b2ab-107">Namn</span><span class="sxs-lookup"><span data-stu-id="1b2ab-107">Name</span></span>

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="1b2ab-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1b2ab-108">DESCRIPTION</span></span>

<span data-ttu-id="1b2ab-109">`New-Module`Cmdleten skapar en dynamisk modul från ett skript block.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-109">The `New-Module` cmdlet creates a dynamic module from a script block.</span></span> <span data-ttu-id="1b2ab-110">Medlemmarna i den dynamiska modulen, till exempel Functions och variabler, är omedelbart tillgängliga i sessionen och förblir tillgängliga tills du stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-110">The members of the dynamic module, such as functions and variables, are immediately available in the session and remain available until you close the session.</span></span>

<span data-ttu-id="1b2ab-111">Precis som statiska moduler exporteras som standard cmdletarna och funktionerna i en dynamisk modul, och variablerna och aliasen är inte.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-111">Like static modules, by default, the cmdlets and functions in a dynamic module are exported and the variables and aliases are not.</span></span> <span data-ttu-id="1b2ab-112">Du kan dock använda Export-ModuleMember-cmdleten och parametrarna för `New-Module` för att åsidosätta standardvärdena.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-112">However, you can use the Export-ModuleMember cmdlet and the parameters of `New-Module` to override the defaults.</span></span>

<span data-ttu-id="1b2ab-113">Du kan också använda **AsCustomObject** -parametern för `New-Module` för att returnera den dynamiska modulen som ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-113">You can also use the **AsCustomObject** parameter of `New-Module` to return the dynamic module as a custom object.</span></span> <span data-ttu-id="1b2ab-114">Medlemmarna i modulerna, till exempel functions, implementeras som skript metoder för det anpassade objektet i stället för att importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-114">The members of the modules, such as functions, are implemented as script methods of the custom object instead of being imported into the session.</span></span>

<span data-ttu-id="1b2ab-115">Dynamiska moduler finns bara i minnet, inte på disk.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-115">Dynamic modules exist only in memory, not on disk.</span></span> <span data-ttu-id="1b2ab-116">Precis som alla moduler körs medlemmarna i dynamiska moduler i en privat modul som är underordnad det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-116">Like all modules, the members of dynamic modules run in a private module scope that is a child of the global scope.</span></span> <span data-ttu-id="1b2ab-117">Get-Module kan inte hämta en dynamisk modul, men Get-Command kan hämta de exporterade medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-117">Get-Module cannot get a dynamic module, but Get-Command can get the exported members.</span></span>

<span data-ttu-id="1b2ab-118">Om du vill göra en dynamisk modul tillgänglig för, kan du skicka ett `Get-Module` `New-Module` kommando till import-module eller skicka en pipe till-objektet som `New-Module` returneras till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b2ab-118">To make a dynamic module available to `Get-Module`, pipe a `New-Module` command to Import-Module, or pipe the module object that `New-Module` returns to `Import-Module`.</span></span> <span data-ttu-id="1b2ab-119">Den här åtgärden lägger till den dynamiska modulen i `Get-Module` listan, men den sparar inte modulen på disken eller gör den beständig.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-119">This action adds the dynamic module to the `Get-Module` list, but it does not save the module to disk or make it persistent.</span></span>

## <span data-ttu-id="1b2ab-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1b2ab-120">EXAMPLES</span></span>

### <span data-ttu-id="1b2ab-121">Exempel 1: skapa en dynamisk modul</span><span class="sxs-lookup"><span data-stu-id="1b2ab-121">Example 1: Create a dynamic module</span></span>

<span data-ttu-id="1b2ab-122">I det här exemplet skapas en ny dynamisk modul med en funktion som kallas `Hello` .</span><span class="sxs-lookup"><span data-stu-id="1b2ab-122">This example creates a new dynamic module with a function called `Hello`.</span></span> <span data-ttu-id="1b2ab-123">Kommandot returnerar ett modul-objekt som representerar den nya dynamiska modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-123">The command returns a module object that represents the new dynamic module.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### <span data-ttu-id="1b2ab-124">Exempel 2: arbeta med dynamiska moduler och Get-Module och Get-Command</span><span class="sxs-lookup"><span data-stu-id="1b2ab-124">Example 2: Working with dynamic modules and Get-Module and Get-Command</span></span>

<span data-ttu-id="1b2ab-125">Det här exemplet visar att dynamiska moduler inte returneras av `Get-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-125">This example demonstrates that dynamic modules are not returned by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="1b2ab-126">De medlemmar som exporteras returneras av `Get-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-126">The members that they export are returned by the `Get-Command` cmdlet.</span></span>

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### <span data-ttu-id="1b2ab-127">Exempel 3: exportera en variabel till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="1b2ab-127">Example 3: Export a variable into the current session</span></span>

<span data-ttu-id="1b2ab-128">I det här exemplet används `Export-ModuleMember` cmdleten för att exportera en variabel till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-128">This example uses the `Export-ModuleMember` cmdlet to export a variable into the current session.</span></span>
<span data-ttu-id="1b2ab-129">Utan `Export-ModuleMember` kommandot exporteras endast funktionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-129">Without the `Export-ModuleMember` command, only the function is exported.</span></span>

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

<span data-ttu-id="1b2ab-130">Resultatet visar att både variabeln och funktionen exporterades till sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-130">The output shows that both the variable and the function were exported into the session.</span></span>

### <span data-ttu-id="1b2ab-131">Exempel 4: gör en dynamisk modul tillgänglig för Get-Module</span><span class="sxs-lookup"><span data-stu-id="1b2ab-131">Example 4: Make a dynamic module available to Get-Module</span></span>

<span data-ttu-id="1b2ab-132">Det här exemplet visar att du kan göra en dynamisk modul tillgänglig för genom att skicka `Get-Module` den dynamiska modulen till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b2ab-132">This example demonstrates that you can make a dynamic module available to `Get-Module` by piping the dynamic module to `Import-Module`.</span></span>

<span data-ttu-id="1b2ab-133">`New-Module` skapar ett modul-objekt som är skickas till `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-133">`New-Module` creates a module object that is piped to the `Import-Module` cmdlet.</span></span> <span data-ttu-id="1b2ab-134">Parametern **Name** i `New-Module` tilldelar modulen ett eget namn.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-134">The **Name** parameter of `New-Module` assigns a friendly name to the module.</span></span> <span data-ttu-id="1b2ab-135">Eftersom inte `Import-Module` returnerar några objekt som standard, finns det inga utdata från det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-135">Because `Import-Module` does not return any objects by default, there is no output from this command.</span></span> <span data-ttu-id="1b2ab-136">`Get-Module` att **GreetingModule** har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-136">`Get-Module` that the **GreetingModule** has been imported into the current session.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

<span data-ttu-id="1b2ab-137">`Get-Command`Cmdleten visar den `Hello` funktion som den dynamiska modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-137">The `Get-Command` cmdlet shows the `Hello` function that the dynamic module exports.</span></span>

### <span data-ttu-id="1b2ab-138">Exempel 5: generera ett anpassat objekt som har exporterade funktioner</span><span class="sxs-lookup"><span data-stu-id="1b2ab-138">Example 5: Generate a custom object that has exported functions</span></span>

<span data-ttu-id="1b2ab-139">Det här exemplet visar hur du använder **AsCustomObject** -parametern för `New-Module` för att skapa ett anpassat objekt som har skript metoder som representerar de exporterade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-139">This example shows how to use the **AsCustomObject** parameter of `New-Module` to generate a custom object that has script methods that represent the exported functions.</span></span>

<span data-ttu-id="1b2ab-140">`New-Module`Cmdleten skapar en dynamisk modul med två funktioner `Hello` och `Goodbye` .</span><span class="sxs-lookup"><span data-stu-id="1b2ab-140">The `New-Module` cmdlet creates a dynamic module with two functions, `Hello` and `Goodbye`.</span></span> <span data-ttu-id="1b2ab-141">Parametern **AsCustomObject** skapar ett anpassat objekt i stället för **PSModuleInfo** -objektet som `New-Module` genererar som standard.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-141">The **AsCustomObject** parameter creates a custom object instead of the **PSModuleInfo** object that `New-Module` generates by default.</span></span> <span data-ttu-id="1b2ab-142">Det här anpassade objektet sparas i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-142">This custom object is saved in the `$m` variable.</span></span>
<span data-ttu-id="1b2ab-143">`$m`Variabeln verkar inte ha ett tilldelat värde.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-143">The `$m` variable appears to have no assigned value.</span></span>

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

<span data-ttu-id="1b2ab-144">I- `$m` `Get-Member` cmdleten visas egenskaper och metoder för det anpassade objektet.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-144">Piping `$m` to the `Get-Member` cmdlet displays the properties and methods of the custom object.</span></span> <span data-ttu-id="1b2ab-145">Utdata visar att objektet har skript metoder som representerar-och- `Hello` `Goodbye` funktionerna.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-145">The output shows that the object has script methods that represent the `Hello` and `Goodbye` functions.</span></span>
<span data-ttu-id="1b2ab-146">Slutligen anropar vi dessa skript metoder och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-146">Finally, we call these script methods and display the results.</span></span>

### <span data-ttu-id="1b2ab-147">Exempel 6: Hämta resultatet från skript blocket</span><span class="sxs-lookup"><span data-stu-id="1b2ab-147">Example 6: Get the results of the script block</span></span>

<span data-ttu-id="1b2ab-148">I det här exemplet används parametern **ReturnResult** för att begära resultatet av att köra skript blocket i stället för att begära ett modul-objekt.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-148">This example uses the **ReturnResult** parameter to request the results of running the script block instead of requesting a module object.</span></span> <span data-ttu-id="1b2ab-149">Skript blocket i den nya modulen definierar `SayHello` funktionen och anropar sedan funktionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-149">The script block in the new module defines the `SayHello` function and then calls the function.</span></span>

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## <span data-ttu-id="1b2ab-150">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1b2ab-150">PARAMETERS</span></span>

### <span data-ttu-id="1b2ab-151">– Argument List</span><span class="sxs-lookup"><span data-stu-id="1b2ab-151">-ArgumentList</span></span>

<span data-ttu-id="1b2ab-152">Anger en matris med argument som är parameter värden som skickas till skript blocket.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-152">Specifies an array of arguments which are parameter values that are passed to the script block.</span></span> <span data-ttu-id="1b2ab-153">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="1b2ab-153">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b2ab-154">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="1b2ab-154">-AsCustomObject</span></span>

<span data-ttu-id="1b2ab-155">Anger att denna cmdlet returnerar ett anpassat objekt som representerar den dynamiska modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-155">Indicates that this cmdlet returns a custom object that represents the dynamic module.</span></span> <span data-ttu-id="1b2ab-156">Modulens medlemmar implementeras som skript metoder för det anpassade objektet, men de importeras inte till sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-156">The module members are implemented as script methods of the custom object, but they are not imported into the session.</span></span> <span data-ttu-id="1b2ab-157">Du kan spara det anpassade objektet i en variabel och använda punkt notation för att anropa medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-157">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

<span data-ttu-id="1b2ab-158">Om modulen har flera medlemmar med samma namn, till exempel en funktion och en variabel som både heter A, kan bara en medlem med varje namn nås från det anpassade objektet.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-158">If the module has multiple members with the same name, such as a function and a variable that are both named A, only one member with each name can be accessed from the custom object.</span></span>

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

### <span data-ttu-id="1b2ab-159">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b2ab-159">-Cmdlet</span></span>

<span data-ttu-id="1b2ab-160">Anger en matris med cmdletar som denna cmdlet exporterar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-160">Specifies an array of cmdlets that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="1b2ab-161">Ange en kommaavgränsad lista med cmdletar.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-161">Enter a comma-separated list of cmdlets.</span></span> <span data-ttu-id="1b2ab-162">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-162">Wildcard characters are permitted.</span></span> <span data-ttu-id="1b2ab-163">Som standard exporteras alla cmdletar i modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-163">By default, all cmdlets in the module are exported.</span></span>

<span data-ttu-id="1b2ab-164">Det går inte att definiera cmdletar i ett-skript block, men en dynamisk modul kan innehålla cmdletar om den importerar cmdlets från en binär modul.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-164">You cannot define cmdlets in a script block, but a dynamic module can include cmdlets if it imports the cmdlets from a binary module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b2ab-165">– Funktion</span><span class="sxs-lookup"><span data-stu-id="1b2ab-165">-Function</span></span>

<span data-ttu-id="1b2ab-166">Anger en matris med funktioner som denna cmdlet exporterar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-166">Specifies an array of functions that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="1b2ab-167">Ange en kommaavgränsad lista med funktioner.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-167">Enter a comma-separated list of functions.</span></span> <span data-ttu-id="1b2ab-168">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="1b2ab-169">Som standard exporteras alla funktioner som definierats i en modul.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-169">By default, all functions defined in a module are exported.</span></span>

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

### <span data-ttu-id="1b2ab-170">-Name</span><span class="sxs-lookup"><span data-stu-id="1b2ab-170">-Name</span></span>

<span data-ttu-id="1b2ab-171">Anger ett namn för den nya modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-171">Specifies a name for the new module.</span></span> <span data-ttu-id="1b2ab-172">Du kan också skicka ett modulnamn till en ny modul.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-172">You can also pipe a module name to New-Module.</span></span>

<span data-ttu-id="1b2ab-173">Standardvärdet är ett automatiskt genererat namn som börjar med `__DynamicModule_` och följt av ett GUID som anger sökvägen till den dynamiska modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-173">The default value is an autogenerated name that starts with `__DynamicModule_` and is followed by a GUID that specifies the path of the dynamic module.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1b2ab-174">-ReturnResult</span><span class="sxs-lookup"><span data-stu-id="1b2ab-174">-ReturnResult</span></span>

<span data-ttu-id="1b2ab-175">Anger att den här cmdleten kör skript blocket och returnerar skript block resultatet i stället för att returnera ett modul objekt.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-175">Indicates that this cmdlet runs the script block and returns the script block results instead of returning a module object.</span></span>

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

### <span data-ttu-id="1b2ab-176">– Script block</span><span class="sxs-lookup"><span data-stu-id="1b2ab-176">-ScriptBlock</span></span>

<span data-ttu-id="1b2ab-177">Anger innehållet i den dynamiska modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-177">Specifies the contents of the dynamic module.</span></span> <span data-ttu-id="1b2ab-178">Omge innehållet i klammerparenteser ( `{}` ) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-178">Enclose the contents in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="1b2ab-179">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-179">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b2ab-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b2ab-180">CommonParameters</span></span>

<span data-ttu-id="1b2ab-181">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b2ab-182">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1b2ab-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b2ab-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="1b2ab-183">INPUTS</span></span>

### <span data-ttu-id="1b2ab-184">System. String</span><span class="sxs-lookup"><span data-stu-id="1b2ab-184">System.String</span></span>

<span data-ttu-id="1b2ab-185">Du kan skicka vidare ett modulnamn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-185">You can pipe a module name to this cmdlet.</span></span>

## <span data-ttu-id="1b2ab-186">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1b2ab-186">OUTPUTS</span></span>

### <span data-ttu-id="1b2ab-187">System. Management. Automation. PSModuleInfo, system. Management. Automation. PSCustomObject eller none</span><span class="sxs-lookup"><span data-stu-id="1b2ab-187">System.Management.Automation.PSModuleInfo, System.Management.Automation.PSCustomObject, or None</span></span>

<span data-ttu-id="1b2ab-188">Denna cmdlet genererar ett **PSModuleInfo** -objekt som standard.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-188">This cmdlet generates a **PSModuleInfo** object, by default.</span></span> <span data-ttu-id="1b2ab-189">Om du använder parametern **AsCustomObject** genereras ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-189">If you use the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span> <span data-ttu-id="1b2ab-190">Om du använder parametern **ReturnResult** , returnerar den resultatet av att utvärdera skript blocket i den dynamiska modulen.</span><span class="sxs-lookup"><span data-stu-id="1b2ab-190">If you use the **ReturnResult** parameter, it returns the result of evaluating the script block in the dynamic module.</span></span>

## <span data-ttu-id="1b2ab-191">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1b2ab-191">NOTES</span></span>

<span data-ttu-id="1b2ab-192">Du kan också referera till `New-Module` baserat på dess alias `nmo` .</span><span class="sxs-lookup"><span data-stu-id="1b2ab-192">You can also refer to `New-Module` by its alias, `nmo`.</span></span> <span data-ttu-id="1b2ab-193">Mer information finns i [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="1b2ab-193">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="1b2ab-194">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1b2ab-194">RELATED LINKS</span></span>

[<span data-ttu-id="1b2ab-195">Exportera – ModuleMember</span><span class="sxs-lookup"><span data-stu-id="1b2ab-195">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="1b2ab-196">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="1b2ab-196">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="1b2ab-197">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="1b2ab-197">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="1b2ab-198">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="1b2ab-198">Remove-Module</span></span>](Remove-Module.md)

