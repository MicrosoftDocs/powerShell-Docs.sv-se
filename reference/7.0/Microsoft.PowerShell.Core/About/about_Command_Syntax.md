---
description: Beskriver de syntax-diagram som används i PowerShell.
keywords: powershell,cmdlet
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: 143d1673ca03e390a85651f0083cef6ab6e43ba3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270081"
---
# <a name="about-command-syntax"></a><span data-ttu-id="ce746-104">Om kommandosyntax</span><span class="sxs-lookup"><span data-stu-id="ce746-104">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="ce746-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ce746-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ce746-106">Beskriver de syntax-diagram som används i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce746-106">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ce746-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ce746-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ce746-108">Cmdletarna [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) och [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) visar syntax-diagram som hjälper dig att skapa kommandon på rätt sätt.</span><span class="sxs-lookup"><span data-stu-id="ce746-108">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="ce746-109">I det här avsnittet beskrivs hur du tolkar syntax-diagram.</span><span class="sxs-lookup"><span data-stu-id="ce746-109">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="ce746-110">SYNTAX DIAGRAM</span><span class="sxs-lookup"><span data-stu-id="ce746-110">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="ce746-111">Varje stycke i ett kommando för kommandosyntaxen representerar en giltig form av kommandot.</span><span class="sxs-lookup"><span data-stu-id="ce746-111">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="ce746-112">Om du vill skapa ett kommando följer du syntaxen för diagrammet från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="ce746-112">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="ce746-113">Välj bland de valfria parametrarna och ange värden för plats hållarna.</span><span class="sxs-lookup"><span data-stu-id="ce746-113">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="ce746-114">PowerShell använder följande notation för syntax-diagram.</span><span class="sxs-lookup"><span data-stu-id="ce746-114">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="ce746-115">Följande är syntaxen för cmdleten [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .</span><span class="sxs-lookup"><span data-stu-id="ce746-115">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="ce746-116">Syntaxen är kapitaliserad för läsbarhet, men PowerShell är Skift läges okänsligt.</span><span class="sxs-lookup"><span data-stu-id="ce746-116">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="ce746-117">Syntax-diagrammet innehåller följande element.</span><span class="sxs-lookup"><span data-stu-id="ce746-117">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="ce746-118">Kommando namn</span><span class="sxs-lookup"><span data-stu-id="ce746-118">Command name</span></span>

<span data-ttu-id="ce746-119">Kommandon börjar alltid med ett kommando namn, till exempel `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="ce746-119">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="ce746-120">Skriv kommando namnet eller dess alias, t. ex. "GCM" för `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="ce746-120">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="ce746-121">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ce746-121">Parameters</span></span>

<span data-ttu-id="ce746-122">Parametrarna för ett kommando är alternativ som avgör vad kommandot gör.</span><span class="sxs-lookup"><span data-stu-id="ce746-122">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="ce746-123">Vissa parametrar tar ett "värde" som är indata från användaren till kommandot.</span><span class="sxs-lookup"><span data-stu-id="ce746-123">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="ce746-124">Till exempel `Get-Help` har kommandot en **namn** parameter som gör att du kan ange namnet på det ämne som hjälpen visas för.</span><span class="sxs-lookup"><span data-stu-id="ce746-124">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="ce746-125">Ämnes namnet är värdet för parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="ce746-125">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="ce746-126">I ett PowerShell-kommando börjar parameter namn alltid med ett bindestreck.</span><span class="sxs-lookup"><span data-stu-id="ce746-126">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="ce746-127">Bindestrecket talar om för PowerShell att objektet i kommandot är ett parameter namn.</span><span class="sxs-lookup"><span data-stu-id="ce746-127">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="ce746-128">Om du till exempel vill använda namn parametern för `New-Alias` skriver du följande:</span><span class="sxs-lookup"><span data-stu-id="ce746-128">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="ce746-129">Parametrar kan vara obligatoriska eller valfria.</span><span class="sxs-lookup"><span data-stu-id="ce746-129">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="ce746-130">Valfria objekt omges av hakparenteser i ett syntax diagram `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="ce746-130">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="ce746-131">Mer information om parametrar finns i [about_Parameters](about_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ce746-131">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="ce746-132">Parametervärden</span><span class="sxs-lookup"><span data-stu-id="ce746-132">Parameter Values</span></span>

<span data-ttu-id="ce746-133">Ett parameter värde är den Indatatyp som parametern tar.</span><span class="sxs-lookup"><span data-stu-id="ce746-133">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="ce746-134">Eftersom Windows PowerShell baseras på Microsoft .NET Framework representeras parameter värden i syntax-diagrammet av deras .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="ce746-134">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="ce746-135">Till exempel använder name-parametern för `Get-Help` ett "String"-värde, som är en text sträng, till exempel ett enstaka ord eller flera ord som omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ce746-135">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="ce746-136">.NET-typen för ett parameter värde omges av vinkelparenteser `< >` för att indikera att den är plats hållare för ett värde och inte en literal som du skriver in i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-136">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="ce746-137">Om du vill använda parametern ersätter du plats hållaren för .NET-typ med ett objekt som har den angivna .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="ce746-137">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="ce746-138">Om du till exempel vill använda **namn** parametern skriver du "-name" följt av en sträng, till exempel följande:</span><span class="sxs-lookup"><span data-stu-id="ce746-138">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="ce746-139">Parametrar utan värden</span><span class="sxs-lookup"><span data-stu-id="ce746-139">Parameters with no values</span></span>

<span data-ttu-id="ce746-140">Vissa parametrar accepterar inte indatatyper, så de har inte något parameter värde.</span><span class="sxs-lookup"><span data-stu-id="ce746-140">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="ce746-141">Parametrar utan värden kallas "växla parametrar" eftersom de fungerar som på/av växlar.</span><span class="sxs-lookup"><span data-stu-id="ce746-141">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="ce746-142">Du inkluderar dem (på) eller utelämnar dem (av) från ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-142">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="ce746-143">Om du vill använda en växlings parameter skriver du bara parameter namnet och föregås av ett bindestreck.</span><span class="sxs-lookup"><span data-stu-id="ce746-143">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="ce746-144">Om du till exempel vill använda parametern **whatIf** för `New-Alias` cmdleten skriver du följande:</span><span class="sxs-lookup"><span data-stu-id="ce746-144">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="ce746-145">Parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="ce746-145">Parameter Sets</span></span>

<span data-ttu-id="ce746-146">Parametrarna för ett kommando visas i parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="ce746-146">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="ce746-147">Parameter uppsättningar ser ut som stycken i ett syntax-diagram.</span><span class="sxs-lookup"><span data-stu-id="ce746-147">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="ce746-148">`New-Alias`Cmdleten har en parameter uppsättning, men många cmdlets har flera parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="ce746-148">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="ce746-149">Några av cmdlet-parametrarna är unika för en parameter uppsättning och andra visas i flera parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="ce746-149">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="ce746-150">Varje parameter uppsättning representerar formatet för ett giltigt kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-150">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="ce746-151">En parameter uppsättning inkluderar bara parametrar som kan användas tillsammans i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-151">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="ce746-152">Om det inte går att använda parametrar i samma kommando, visas de i separata parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="ce746-152">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="ce746-153">Till exempel har cmdleten [Get-slumpmässig](xref:Microsoft.PowerShell.Utility.Get-Random) följande parameter uppsättningar:</span><span class="sxs-lookup"><span data-stu-id="ce746-153">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="ce746-154">Den första parameter uppsättningen, som returnerar ett slumptal, har de **lägsta** och **högsta** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ce746-154">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="ce746-155">Den andra parameter uppsättningen, som returnerar ett slumpmässigt valt objekt från en uppsättning objekt, innehåller parametrarna **InputObject** och **Count** .</span><span class="sxs-lookup"><span data-stu-id="ce746-155">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="ce746-156">Båda parameter uppsättningarna har parametern **SetSeed** och de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ce746-156">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="ce746-157">Dessa parameter uppsättningar visar att du kan använda parametrarna **InputObject** och **Count** i samma kommando, men du kan inte använda parametrarna **maximum** och **Count** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-157">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="ce746-158">Du anger vilken parameter uppsättning du vill använda med hjälp av parametrarna i den parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ce746-158">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="ce746-159">Varje cmdlet har dock även en standard parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="ce746-159">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="ce746-160">Standard parameter uppsättningen används när du inte anger parametrar som är unika för en parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="ce746-160">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="ce746-161">Om du till exempel använder `Get-Random` utan parametrar förutsätter Windows PowerShell att du använder den **numeriska** parameter uppsättningen och returnerar ett slumpmässigt nummer.</span><span class="sxs-lookup"><span data-stu-id="ce746-161">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="ce746-162">I varje parameter uppsättning visas parametrarna i positions ordning.</span><span class="sxs-lookup"><span data-stu-id="ce746-162">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="ce746-163">Ordningen på parametrarna i ett kommando fråga endast när du utelämnar valfria parameter namn.</span><span class="sxs-lookup"><span data-stu-id="ce746-163">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="ce746-164">När parameter namn utelämnas tilldelar PowerShell värden till parametrar efter position och typ.</span><span class="sxs-lookup"><span data-stu-id="ce746-164">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="ce746-165">Mer information om parameter placering finns i `about_Parameters` .</span><span class="sxs-lookup"><span data-stu-id="ce746-165">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="ce746-166">Symboler i syntax diagram</span><span class="sxs-lookup"><span data-stu-id="ce746-166">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="ce746-167">I syntax-diagrammet visas kommando namn, kommando parametrar och parameter värden.</span><span class="sxs-lookup"><span data-stu-id="ce746-167">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="ce746-168">Den använder också symboler för att visa hur du skapar ett giltigt kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-168">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="ce746-169">I syntax diagrammen används följande symboler:</span><span class="sxs-lookup"><span data-stu-id="ce746-169">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="ce746-170">Ett bindestreck `-` anger ett parameter namn.</span><span class="sxs-lookup"><span data-stu-id="ce746-170">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="ce746-171">I ett kommando skriver du bindestrecket omedelbart före parameter namnet utan några mellanliggande blank steg, som du ser i syntax-diagrammet.</span><span class="sxs-lookup"><span data-stu-id="ce746-171">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="ce746-172">Om du till exempel vill använda **namn** parametern för `New-Alias` skriver du:</span><span class="sxs-lookup"><span data-stu-id="ce746-172">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="ce746-173">Vinkelparenteser `<>` visar platshållartext.</span><span class="sxs-lookup"><span data-stu-id="ce746-173">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="ce746-174">Du anger inte vinkelparenteser eller platshållartexten i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce746-174">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="ce746-175">I stället ersätter du det med det objekt som beskrivs.</span><span class="sxs-lookup"><span data-stu-id="ce746-175">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="ce746-176">Vinkelparenteser används för att identifiera .NET-typen för värdet som en parameter tar.</span><span class="sxs-lookup"><span data-stu-id="ce746-176">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="ce746-177">Om du till exempel vill använda parametern **Name** för `New-Alias` cmdlet: en, ersätter du `<string>` med en sträng, som är ett enstaka ord eller en grupp med ord som omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ce746-177">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="ce746-178">Hakparenteser `[ ]` indikerar valfria objekt.</span><span class="sxs-lookup"><span data-stu-id="ce746-178">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="ce746-179">En parameter och dess värde kan vara valfritt, eller så kan namnet på en obligatorisk parameter vara valfritt.</span><span class="sxs-lookup"><span data-stu-id="ce746-179">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="ce746-180">Exempel: **beskrivnings** parametern för `New-Alias` och dess värde omges av hakparenteser eftersom de båda är valfria.</span><span class="sxs-lookup"><span data-stu-id="ce746-180">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="ce746-181">Hakparenteserna visar också att värdet för namn parametern `<string>` är obligatoriskt, men parameter namnet, "name", är valfritt.</span><span class="sxs-lookup"><span data-stu-id="ce746-181">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="ce746-182">En höger-och vänsterparentes `[]` som läggs till i en .net-typ indikerar att parametern kan acceptera ett eller flera värden av den typen.</span><span class="sxs-lookup"><span data-stu-id="ce746-182">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="ce746-183">Ange värdena i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="ce746-183">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="ce746-184">Till exempel tar cmdleten **Name** -parametern `New-Alias` bara en sträng, men **namn** parametern för [Get-process](xref:Microsoft.PowerShell.Management.Get-Process) kan ta en eller flera strängar.</span><span class="sxs-lookup"><span data-stu-id="ce746-184">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="ce746-185">Klammerparenteser `{}` anger en "uppräkning", som är en uppsättning giltiga värden för en parameter.</span><span class="sxs-lookup"><span data-stu-id="ce746-185">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="ce746-186">Värdena i klamrarna separeras med lodräta staplar `|` .</span><span class="sxs-lookup"><span data-stu-id="ce746-186">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="ce746-187">Staplarna visar ett "exklusivt OR"-alternativ, vilket innebär att du bara kan välja ett värde från den uppsättning värden som visas innanför klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="ce746-187">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="ce746-188">Syntaxen för `New-Alias` cmdleten innehåller till exempel följande värde uppräkning för **alternativ** parametern:</span><span class="sxs-lookup"><span data-stu-id="ce746-188">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="ce746-189">Klamrarna och de lodräta staplarna visar att du kan välja något av de angivna värdena för **alternativ** parametern, till exempel "ReadOnly" eller "AllScope".</span><span class="sxs-lookup"><span data-stu-id="ce746-189">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="ce746-190">Valfria objekt</span><span class="sxs-lookup"><span data-stu-id="ce746-190">Optional Items</span></span>

<span data-ttu-id="ce746-191">Hakparenteser `[]` omger valfria objekt.</span><span class="sxs-lookup"><span data-stu-id="ce746-191">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="ce746-192">I `New-Alias` beskrivningen för cmdlet-syntaxen är till exempel parametern **omfattning** valfri.</span><span class="sxs-lookup"><span data-stu-id="ce746-192">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="ce746-193">Detta anges i syntaxen med hakparenteserna Runt parameter namnet och typen:</span><span class="sxs-lookup"><span data-stu-id="ce746-193">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="ce746-194">Följande exempel är korrekt användning av `New-Alias` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="ce746-194">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="ce746-195">Ett parameter namn kan vara valfritt även om värdet för den parametern är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="ce746-195">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="ce746-196">Detta anges i syntaxen med hakparenteserna Runt parameter namnet men inte parameter typen, som i det här exemplet från `New-Alias` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ce746-196">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="ce746-197">Följande kommandon använder `New-Alias` cmdleten korrekt.</span><span class="sxs-lookup"><span data-stu-id="ce746-197">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="ce746-198">Kommandona ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="ce746-198">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="ce746-199">Om parameter namnet inte ingår i instruktionen som skrivet försöker Windows PowerShell använda positionen för argumenten för att tilldela värdena till parametrar.</span><span class="sxs-lookup"><span data-stu-id="ce746-199">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="ce746-200">Följande exempel är inte klart:</span><span class="sxs-lookup"><span data-stu-id="ce746-200">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="ce746-201">Denna cmdlet kräver värden för både **namn** -och **värde** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ce746-201">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="ce746-202">I syntaxen används hakparenteser även för namngivning och databyte till .NET Framework typer.</span><span class="sxs-lookup"><span data-stu-id="ce746-202">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="ce746-203">I det här sammanhanget anger hakparenteser inte ett element är valfritt.</span><span class="sxs-lookup"><span data-stu-id="ce746-203">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce746-204">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="ce746-204">SEE ALSO</span></span>

- [<span data-ttu-id="ce746-205">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="ce746-205">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="ce746-206">Get-Command</span><span class="sxs-lookup"><span data-stu-id="ce746-206">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="ce746-207">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="ce746-207">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)
