---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 61a144ca5bc74d63738e9ccfc65188ddf1e27c02
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262629"
---
# <span data-ttu-id="52657-103">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="52657-103">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="52657-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="52657-104">SYNOPSIS</span></span>
<span data-ttu-id="52657-105">Skapar en fil som definierar en uppsättning funktioner som ska exponeras via en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-105">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="52657-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52657-106">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="52657-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="52657-107">DESCRIPTION</span></span>

<span data-ttu-id="52657-108">`New-PSRoleCapabilityFile`Cmdleten skapar en fil som definierar en uppsättning användar funktioner som kan exponeras genom konfigurationsfiler för sessioner.</span><span class="sxs-lookup"><span data-stu-id="52657-108">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="52657-109">Detta omfattar att bestämma vilka cmdletar, funktioner och skript som är tillgängliga för användare.</span><span class="sxs-lookup"><span data-stu-id="52657-109">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="52657-110">Funktions filen är en läsbar textfil som innehåller en hash-tabell av konfigurations egenskaper och värden för sessioner.</span><span class="sxs-lookup"><span data-stu-id="52657-110">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="52657-111">Filen har fil namns tillägget. psrc och kan användas av mer än en-session-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="52657-111">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="52657-112">Alla parametrar för `New-PSRoleCapabilityFile` är valfria förutom för **Sök vägs** parametern, som anger fil Sök vägen för filen.</span><span class="sxs-lookup"><span data-stu-id="52657-112">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="52657-113">Om du inte tar med en parameter när du kör cmdleten, kommenteras motsvarande nyckel i konfigurations filen för sessionen, förutom där anges i parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="52657-113">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="52657-114">Om du t. ex. inte inkluderar parametern **AssembliesToLoad** , kommenteras avsnittet i konfigurations filen för sessionen ut.</span><span class="sxs-lookup"><span data-stu-id="52657-114">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="52657-115">Om du vill använda roll funktions filen i en konfiguration av sessionen måste du först placera filen i en **RoleCapabilities** -undermapp i en giltig PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="52657-115">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="52657-116">Referera sedan till filen efter namn i fältet **RoleDefinitions** i en PowerShell-session konfigurations fil (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="52657-116">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="52657-117">Den här cmdleten introducerades i Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="52657-117">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="52657-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52657-118">EXAMPLES</span></span>

### <span data-ttu-id="52657-119">Exempel 1: skapa en tom roll funktions fil</span><span class="sxs-lookup"><span data-stu-id="52657-119">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="52657-120">I det här exemplet skapas en ny roll funktions fil som använder standardvärdena (tomma).</span><span class="sxs-lookup"><span data-stu-id="52657-120">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="52657-121">Filen kan senare redige ras i en text redigerare för att ändra konfigurations inställningarna.</span><span class="sxs-lookup"><span data-stu-id="52657-121">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="52657-122">Exempel 2: skapa en roll funktions fil som gör det möjligt för användare att starta om tjänster och valfri VDI-dator</span><span class="sxs-lookup"><span data-stu-id="52657-122">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="52657-123">I det här exemplet skapas en funktions fil för exempel rollen som gör det möjligt för användare att starta om tjänster och datorer som matchar ett särskilt namn mönster.</span><span class="sxs-lookup"><span data-stu-id="52657-123">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="52657-124">Namn filtrering definieras genom att ange parametern **ValidatePattern** till det reguljära uttrycket `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="52657-124">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## <span data-ttu-id="52657-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="52657-125">PARAMETERS</span></span>

### <span data-ttu-id="52657-126">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="52657-126">-AliasDefinitions</span></span>

<span data-ttu-id="52657-127">Lägger till angivna alias till sessioner som använder roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-127">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="52657-128">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="52657-128">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="52657-129">Namn.</span><span class="sxs-lookup"><span data-stu-id="52657-129">Name.</span></span> <span data-ttu-id="52657-130">Aliasets namn.</span><span class="sxs-lookup"><span data-stu-id="52657-130">Name of the alias.</span></span> <span data-ttu-id="52657-131">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="52657-131">This key is required.</span></span>
- <span data-ttu-id="52657-132">Värde.</span><span class="sxs-lookup"><span data-stu-id="52657-132">Value.</span></span> <span data-ttu-id="52657-133">Kommandot som aliaset representerar.</span><span class="sxs-lookup"><span data-stu-id="52657-133">The command that the alias represents.</span></span> <span data-ttu-id="52657-134">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="52657-134">This key is required.</span></span>
- <span data-ttu-id="52657-135">Beskrivning.</span><span class="sxs-lookup"><span data-stu-id="52657-135">Description.</span></span> <span data-ttu-id="52657-136">En text sträng som beskriver aliaset.</span><span class="sxs-lookup"><span data-stu-id="52657-136">A text string that describes the alias.</span></span> <span data-ttu-id="52657-137">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="52657-137">This key is optional.</span></span>
- <span data-ttu-id="52657-138">Alternativ.</span><span class="sxs-lookup"><span data-stu-id="52657-138">Options.</span></span> <span data-ttu-id="52657-139">Alternativ för alias.</span><span class="sxs-lookup"><span data-stu-id="52657-139">Alias options.</span></span> <span data-ttu-id="52657-140">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="52657-140">This key is optional.</span></span> <span data-ttu-id="52657-141">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="52657-141">The default value is None.</span></span> <span data-ttu-id="52657-142">De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="52657-142">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="52657-143">Exempelvis: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="52657-143">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-144">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="52657-144">-AssembliesToLoad</span></span>

<span data-ttu-id="52657-145">Anger de sammansättningar som ska läsas in i de sessioner som använder roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-145">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

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

### <span data-ttu-id="52657-146">– Författare</span><span class="sxs-lookup"><span data-stu-id="52657-146">-Author</span></span>

<span data-ttu-id="52657-147">Anger den användare som skapade roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="52657-147">Specifies the user that created the role capability file.</span></span>

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

### <span data-ttu-id="52657-148">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="52657-148">-CompanyName</span></span>

<span data-ttu-id="52657-149">Identifierar det företag som skapade roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="52657-149">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="52657-150">Standardvärdet är okänt.</span><span class="sxs-lookup"><span data-stu-id="52657-150">The default value is Unknown.</span></span>

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

### <span data-ttu-id="52657-151">– Copyright</span><span class="sxs-lookup"><span data-stu-id="52657-151">-Copyright</span></span>

<span data-ttu-id="52657-152">Anger en upphovs rätt för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-152">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="52657-153">Om du utelämnar den här parametern `New-PSRoleCapabilityFile` genererar en Copyright-instruktion med hjälp av värdet för parametern **Author** .</span><span class="sxs-lookup"><span data-stu-id="52657-153">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="52657-154">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="52657-154">-Description</span></span>

<span data-ttu-id="52657-155">Anger en beskrivning av roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="52657-155">Specifies a description for the role capability file.</span></span>

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

### <span data-ttu-id="52657-156">– EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="52657-156">-EnvironmentVariables</span></span>

<span data-ttu-id="52657-157">Anger miljövariabler för sessioner som exponerar den här roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-157">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="52657-158">Ange en hash-tabell där nycklarna är miljö variabel namnen och värdena är Miljövariabelns värden.</span><span class="sxs-lookup"><span data-stu-id="52657-158">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="52657-159">Exempelvis: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="52657-159">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-160">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="52657-160">-FormatsToProcess</span></span>

<span data-ttu-id="52657-161">Anger de formateringsattribut (. ps1xml) som körs i sessioner som använder sig av roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-161">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="52657-162">Värdet för den här parametern måste vara en fullständig eller absolut sökväg till filerna.</span><span class="sxs-lookup"><span data-stu-id="52657-162">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="52657-163">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="52657-163">-FunctionDefinitions</span></span>

<span data-ttu-id="52657-164">Lägger till angivna funktioner till sessioner som visar roll kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="52657-164">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="52657-165">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="52657-165">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="52657-166">Namn.</span><span class="sxs-lookup"><span data-stu-id="52657-166">Name.</span></span> <span data-ttu-id="52657-167">Namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="52657-167">Name of the function.</span></span> <span data-ttu-id="52657-168">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="52657-168">This key is required.</span></span>
- <span data-ttu-id="52657-169">Script block.</span><span class="sxs-lookup"><span data-stu-id="52657-169">ScriptBlock.</span></span> <span data-ttu-id="52657-170">Funktions text.</span><span class="sxs-lookup"><span data-stu-id="52657-170">Function body.</span></span> <span data-ttu-id="52657-171">Ange ett skript block.</span><span class="sxs-lookup"><span data-stu-id="52657-171">Enter a script block.</span></span> <span data-ttu-id="52657-172">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="52657-172">This key is required.</span></span>
- <span data-ttu-id="52657-173">Alternativ.</span><span class="sxs-lookup"><span data-stu-id="52657-173">Options.</span></span> <span data-ttu-id="52657-174">Funktions alternativ.</span><span class="sxs-lookup"><span data-stu-id="52657-174">Function options.</span></span> <span data-ttu-id="52657-175">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="52657-175">This key is optional.</span></span> <span data-ttu-id="52657-176">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="52657-176">The default value is None.</span></span> <span data-ttu-id="52657-177">De acceptabla värdena för den här parametern är: är ingen, ReadOnly, konstant, privat eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="52657-177">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="52657-178">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="52657-178">For example:</span></span>

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-179">-GUID</span><span class="sxs-lookup"><span data-stu-id="52657-179">-Guid</span></span>

<span data-ttu-id="52657-180">Anger en unik identifierare för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-180">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="52657-181">Om du utelämnar den här parametern `New-PSRoleCapabilityFile` genererar ett GUID för filen.</span><span class="sxs-lookup"><span data-stu-id="52657-181">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="52657-182">Om du vill skapa ett nytt GUID i PowerShell skriver du `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="52657-182">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-183">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="52657-183">-ModulesToImport</span></span>

<span data-ttu-id="52657-184">Anger de moduler som importeras automatiskt till sessioner som använder roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-184">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="52657-185">Som standard visas alla kommandon i de moduler som visas.</span><span class="sxs-lookup"><span data-stu-id="52657-185">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="52657-186">När det används med **VisibleCmdlets** eller **VisibleFunctions** kan de kommandon som visas i de angivna modulerna begränsas.</span><span class="sxs-lookup"><span data-stu-id="52657-186">When used with **VisibleCmdlets** or **VisibleFunctions** , the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="52657-187">Varje modul som används i värdet för den här parametern kan representeras av en sträng eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="52657-187">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="52657-188">En modul sträng består bara av namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="52657-188">A module string consists only of the name of the module.</span></span> <span data-ttu-id="52657-189">En modul hash-tabell kan innehålla **Modulnamn** , **ModuleVersion** och **GUID** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="52657-189">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="52657-190">Endast nyckeln **Modulnamn** krävs.</span><span class="sxs-lookup"><span data-stu-id="52657-190">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="52657-191">Följande värde består till exempel av en sträng och en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="52657-191">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="52657-192">En valfri kombination av strängar och hash-tabeller, i vilken ordning som helst, är giltig.</span><span class="sxs-lookup"><span data-stu-id="52657-192">Any combination of strings and hash tables, in any order, is valid.</span></span>

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-193">-Path</span><span class="sxs-lookup"><span data-stu-id="52657-193">-Path</span></span>

<span data-ttu-id="52657-194">Anger sökväg och fil namn för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-194">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="52657-195">Filen måste ha ett `.psrc` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="52657-195">The file must have a `.psrc` filename extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-196">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="52657-196">-ScriptsToProcess</span></span>

<span data-ttu-id="52657-197">Anger skript som ska läggas till i sessioner som använder en roll funktions fil.</span><span class="sxs-lookup"><span data-stu-id="52657-197">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="52657-198">Ange sökväg och fil namn för skripten.</span><span class="sxs-lookup"><span data-stu-id="52657-198">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="52657-199">Värdet för den här parametern måste vara en fullständig eller absolut sökväg till skript fil namnen.</span><span class="sxs-lookup"><span data-stu-id="52657-199">The value of this parameter must be a full or absolute path of the script file names.</span></span>

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

### <span data-ttu-id="52657-200">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="52657-200">-TypesToProcess</span></span>

<span data-ttu-id="52657-201">Anger typ filer (. ps1xml) som ska läggas till i sessioner som använder sig av roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="52657-201">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="52657-202">Ange typ fil namn.</span><span class="sxs-lookup"><span data-stu-id="52657-202">Enter the type filenames.</span></span> <span data-ttu-id="52657-203">Värdet för den här parametern måste vara en fullständig eller absolut sökväg av typ fil namnen.</span><span class="sxs-lookup"><span data-stu-id="52657-203">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

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

### <span data-ttu-id="52657-204">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="52657-204">-VariableDefinitions</span></span>

<span data-ttu-id="52657-205">Anger variabler som ska läggas till i sessioner som använder sig av roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="52657-205">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="52657-206">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="52657-206">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="52657-207">Namn.</span><span class="sxs-lookup"><span data-stu-id="52657-207">Name.</span></span> <span data-ttu-id="52657-208">Variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="52657-208">Name of the variable.</span></span> <span data-ttu-id="52657-209">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="52657-209">This key is required.</span></span>
- <span data-ttu-id="52657-210">Värde.</span><span class="sxs-lookup"><span data-stu-id="52657-210">Value.</span></span> <span data-ttu-id="52657-211">Variabel värde.</span><span class="sxs-lookup"><span data-stu-id="52657-211">Variable value.</span></span> <span data-ttu-id="52657-212">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="52657-212">This key is required.</span></span>
- <span data-ttu-id="52657-213">Alternativ.</span><span class="sxs-lookup"><span data-stu-id="52657-213">Options.</span></span> <span data-ttu-id="52657-214">Variabel alternativ.</span><span class="sxs-lookup"><span data-stu-id="52657-214">Variable options.</span></span> <span data-ttu-id="52657-215">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="52657-215">This key is optional.</span></span> <span data-ttu-id="52657-216">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="52657-216">The default value is None.</span></span> <span data-ttu-id="52657-217">De acceptabla värdena för den här parametern är: är ingen, ReadOnly, konstant, privat eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="52657-217">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="52657-218">Exempelvis: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="52657-218">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52657-219">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="52657-219">-VisibleAliases</span></span>

<span data-ttu-id="52657-220">Begränsar alias i sessionen till de alias som anges i värdet för den här parametern, plus alla alias som du definierar i parametern **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="52657-220">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="52657-221">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="52657-221">Wildcard characters are supported.</span></span>
<span data-ttu-id="52657-222">Som standard visas alla alias som definieras av PowerShell-motorn och alla alias som moduler exporterar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-222">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="52657-223">Om du till exempel vill begränsa tillgängliga alias till GM och GCM använder du följande syntax: `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="52657-223">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="52657-224">När en **Visible** -parameter ingår i roll funktions filen, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-224">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="52657-225">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="52657-225">-VisibleCmdlets</span></span>

<span data-ttu-id="52657-226">Begränsar cmdletarna i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="52657-226">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="52657-227">Jokertecken och kvalificerade namn för module stöds.</span><span class="sxs-lookup"><span data-stu-id="52657-227">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="52657-228">Som standard visas alla cmdletar som modulerna i sessionen exporterar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-228">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="52657-229">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-229">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="52657-230">Om inga moduler i **ModulesToImport** exponerar cmdleten `New-PSRoleCapabilityFile` försöker läsa in lämplig modul.</span><span class="sxs-lookup"><span data-stu-id="52657-230">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="52657-231">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-231">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="52657-232">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="52657-232">-VisibleExternalCommands</span></span>

<span data-ttu-id="52657-233">Begränsar de externa binärfilerna, skripten och kommandona som kan köras i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="52657-233">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="52657-234">Som standard visas inga externa kommandon i den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-234">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="52657-235">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-235">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="52657-236">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="52657-236">-VisibleFunctions</span></span>

<span data-ttu-id="52657-237">Begränsar funktionerna i sessionen till de som anges i värdet för den här parametern, plus de funktioner som du definierar i parametern **FunctionDefinitions** .</span><span class="sxs-lookup"><span data-stu-id="52657-237">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="52657-238">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="52657-238">Wildcard characters are supported.</span></span>

<span data-ttu-id="52657-239">Som standard visas alla funktioner som exporteras av moduler i sessionen i den sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-239">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="52657-240">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-240">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="52657-241">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-241">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="52657-242">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="52657-242">-VisibleProviders</span></span>

<span data-ttu-id="52657-243">Begränsar PowerShell-providern i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="52657-243">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="52657-244">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="52657-244">Wildcard characters are supported.</span></span>

<span data-ttu-id="52657-245">Som standard visas alla providrar som exporteras av en modul i sessionen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-245">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="52657-246">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-246">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="52657-247">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="52657-247">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="52657-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52657-248">CommonParameters</span></span>

<span data-ttu-id="52657-249">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52657-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52657-250">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="52657-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52657-251">INDATA</span><span class="sxs-lookup"><span data-stu-id="52657-251">INPUTS</span></span>

## <span data-ttu-id="52657-252">UTDATA</span><span class="sxs-lookup"><span data-stu-id="52657-252">OUTPUTS</span></span>

## <span data-ttu-id="52657-253">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="52657-253">NOTES</span></span>

## <span data-ttu-id="52657-254">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="52657-254">RELATED LINKS</span></span>

[<span data-ttu-id="52657-255">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="52657-255">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="52657-256">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="52657-256">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)