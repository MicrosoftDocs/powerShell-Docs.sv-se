---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3ef54618e065a5fca3d52415897b3042d6ba4c65
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710878"
---
# <span data-ttu-id="86e97-102">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="86e97-102">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="86e97-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="86e97-103">SYNOPSIS</span></span>
<span data-ttu-id="86e97-104">Skapar en fil som definierar en uppsättning funktioner som ska exponeras via en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-104">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="86e97-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="86e97-105">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="86e97-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="86e97-106">DESCRIPTION</span></span>

<span data-ttu-id="86e97-107">`New-PSRoleCapabilityFile`Cmdleten skapar en fil som definierar en uppsättning användar funktioner som kan exponeras genom konfigurationsfiler för sessioner.</span><span class="sxs-lookup"><span data-stu-id="86e97-107">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="86e97-108">Detta omfattar att bestämma vilka cmdletar, funktioner och skript som är tillgängliga för användare.</span><span class="sxs-lookup"><span data-stu-id="86e97-108">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="86e97-109">Funktions filen är en läsbar textfil som innehåller en hash-tabell av konfigurations egenskaper och värden för sessioner.</span><span class="sxs-lookup"><span data-stu-id="86e97-109">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="86e97-110">Filen har fil namns tillägget. psrc och kan användas av mer än en-session-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="86e97-110">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="86e97-111">Alla parametrar för `New-PSRoleCapabilityFile` är valfria förutom för **Sök vägs** parametern, som anger fil Sök vägen för filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-111">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="86e97-112">Om du inte tar med en parameter när du kör cmdleten, kommenteras motsvarande nyckel i konfigurations filen för sessionen, förutom där anges i parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="86e97-112">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="86e97-113">Om du t. ex. inte inkluderar parametern **AssembliesToLoad** , kommenteras avsnittet i konfigurations filen för sessionen ut.</span><span class="sxs-lookup"><span data-stu-id="86e97-113">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="86e97-114">Om du vill använda roll funktions filen i en konfiguration av sessionen måste du först placera filen i en **RoleCapabilities** -undermapp i en giltig PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="86e97-114">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="86e97-115">Referera sedan till filen efter namn i fältet **RoleDefinitions** i en PowerShell-session konfigurations fil (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="86e97-115">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="86e97-116">Den här cmdleten introducerades i Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="86e97-116">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="86e97-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="86e97-117">EXAMPLES</span></span>

### <span data-ttu-id="86e97-118">Exempel 1: skapa en tom roll funktions fil</span><span class="sxs-lookup"><span data-stu-id="86e97-118">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="86e97-119">I det här exemplet skapas en ny roll funktions fil som använder standardvärdena (tomma).</span><span class="sxs-lookup"><span data-stu-id="86e97-119">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="86e97-120">Filen kan senare redige ras i en text redigerare för att ändra konfigurations inställningarna.</span><span class="sxs-lookup"><span data-stu-id="86e97-120">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="86e97-121">Exempel 2: skapa en roll funktions fil som gör det möjligt för användare att starta om tjänster och valfri VDI-dator</span><span class="sxs-lookup"><span data-stu-id="86e97-121">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="86e97-122">I det här exemplet skapas en funktions fil för exempel rollen som gör det möjligt för användare att starta om tjänster och datorer som matchar ett särskilt namn mönster.</span><span class="sxs-lookup"><span data-stu-id="86e97-122">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="86e97-123">Namn filtrering definieras genom att ange parametern **ValidatePattern** till det reguljära uttrycket `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="86e97-123">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

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

## <span data-ttu-id="86e97-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="86e97-124">PARAMETERS</span></span>

### <span data-ttu-id="86e97-125">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="86e97-125">-AliasDefinitions</span></span>

<span data-ttu-id="86e97-126">Lägger till angivna alias till sessioner som använder roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-126">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="86e97-127">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="86e97-127">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="86e97-128">Namn.</span><span class="sxs-lookup"><span data-stu-id="86e97-128">Name.</span></span> <span data-ttu-id="86e97-129">Aliasets namn.</span><span class="sxs-lookup"><span data-stu-id="86e97-129">Name of the alias.</span></span> <span data-ttu-id="86e97-130">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="86e97-130">This key is required.</span></span>
- <span data-ttu-id="86e97-131">Värde.</span><span class="sxs-lookup"><span data-stu-id="86e97-131">Value.</span></span> <span data-ttu-id="86e97-132">Kommandot som aliaset representerar.</span><span class="sxs-lookup"><span data-stu-id="86e97-132">The command that the alias represents.</span></span> <span data-ttu-id="86e97-133">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="86e97-133">This key is required.</span></span>
- <span data-ttu-id="86e97-134">Beskrivning.</span><span class="sxs-lookup"><span data-stu-id="86e97-134">Description.</span></span> <span data-ttu-id="86e97-135">En text sträng som beskriver aliaset.</span><span class="sxs-lookup"><span data-stu-id="86e97-135">A text string that describes the alias.</span></span> <span data-ttu-id="86e97-136">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="86e97-136">This key is optional.</span></span>
- <span data-ttu-id="86e97-137">Alternativ.</span><span class="sxs-lookup"><span data-stu-id="86e97-137">Options.</span></span> <span data-ttu-id="86e97-138">Alternativ för alias.</span><span class="sxs-lookup"><span data-stu-id="86e97-138">Alias options.</span></span> <span data-ttu-id="86e97-139">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="86e97-139">This key is optional.</span></span> <span data-ttu-id="86e97-140">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="86e97-140">The default value is None.</span></span> <span data-ttu-id="86e97-141">De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="86e97-141">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="86e97-142">Exempel: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="86e97-142">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

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

### <span data-ttu-id="86e97-143">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="86e97-143">-AssembliesToLoad</span></span>

<span data-ttu-id="86e97-144">Anger de sammansättningar som ska läsas in i de sessioner som använder roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-144">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

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

### <span data-ttu-id="86e97-145">– Författare</span><span class="sxs-lookup"><span data-stu-id="86e97-145">-Author</span></span>

<span data-ttu-id="86e97-146">Anger den användare som skapade roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-146">Specifies the user that created the role capability file.</span></span>

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

### <span data-ttu-id="86e97-147">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="86e97-147">-CompanyName</span></span>

<span data-ttu-id="86e97-148">Identifierar det företag som skapade roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-148">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="86e97-149">Standardvärdet är okänt.</span><span class="sxs-lookup"><span data-stu-id="86e97-149">The default value is Unknown.</span></span>

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

### <span data-ttu-id="86e97-150">– Copyright</span><span class="sxs-lookup"><span data-stu-id="86e97-150">-Copyright</span></span>

<span data-ttu-id="86e97-151">Anger en upphovs rätt för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-151">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="86e97-152">Om du utelämnar den här parametern `New-PSRoleCapabilityFile` genererar en Copyright-instruktion med hjälp av värdet för parametern **Author** .</span><span class="sxs-lookup"><span data-stu-id="86e97-152">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="86e97-153">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86e97-153">-Description</span></span>

<span data-ttu-id="86e97-154">Anger en beskrivning av roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-154">Specifies a description for the role capability file.</span></span>

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

### <span data-ttu-id="86e97-155">– EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="86e97-155">-EnvironmentVariables</span></span>

<span data-ttu-id="86e97-156">Anger miljövariabler för sessioner som exponerar den här roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-156">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="86e97-157">Ange en hash-tabell där nycklarna är miljö variabel namnen och värdena är Miljövariabelns värden.</span><span class="sxs-lookup"><span data-stu-id="86e97-157">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="86e97-158">Exempel: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="86e97-158">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

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

### <span data-ttu-id="86e97-159">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="86e97-159">-FormatsToProcess</span></span>

<span data-ttu-id="86e97-160">Anger de formateringsattribut (. ps1xml) som körs i sessioner som använder sig av roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-160">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="86e97-161">Värdet för den här parametern måste vara en fullständig eller absolut sökväg till filerna.</span><span class="sxs-lookup"><span data-stu-id="86e97-161">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="86e97-162">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="86e97-162">-FunctionDefinitions</span></span>

<span data-ttu-id="86e97-163">Lägger till angivna funktioner till sessioner som visar roll kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="86e97-163">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="86e97-164">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="86e97-164">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="86e97-165">Namn.</span><span class="sxs-lookup"><span data-stu-id="86e97-165">Name.</span></span> <span data-ttu-id="86e97-166">Namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-166">Name of the function.</span></span> <span data-ttu-id="86e97-167">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="86e97-167">This key is required.</span></span>
- <span data-ttu-id="86e97-168">Script block.</span><span class="sxs-lookup"><span data-stu-id="86e97-168">ScriptBlock.</span></span> <span data-ttu-id="86e97-169">Funktions text.</span><span class="sxs-lookup"><span data-stu-id="86e97-169">Function body.</span></span> <span data-ttu-id="86e97-170">Ange ett skript block.</span><span class="sxs-lookup"><span data-stu-id="86e97-170">Enter a script block.</span></span> <span data-ttu-id="86e97-171">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="86e97-171">This key is required.</span></span>
- <span data-ttu-id="86e97-172">Alternativ.</span><span class="sxs-lookup"><span data-stu-id="86e97-172">Options.</span></span> <span data-ttu-id="86e97-173">Funktions alternativ.</span><span class="sxs-lookup"><span data-stu-id="86e97-173">Function options.</span></span> <span data-ttu-id="86e97-174">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="86e97-174">This key is optional.</span></span> <span data-ttu-id="86e97-175">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="86e97-175">The default value is None.</span></span> <span data-ttu-id="86e97-176">De acceptabla värdena för den här parametern är: är ingen, ReadOnly, konstant, privat eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="86e97-176">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="86e97-177">Exempel:</span><span class="sxs-lookup"><span data-stu-id="86e97-177">For example:</span></span>

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

### <span data-ttu-id="86e97-178">-GUID</span><span class="sxs-lookup"><span data-stu-id="86e97-178">-Guid</span></span>

<span data-ttu-id="86e97-179">Anger en unik identifierare för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-179">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="86e97-180">Om du utelämnar den här parametern `New-PSRoleCapabilityFile` genererar ett GUID för filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-180">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="86e97-181">Om du vill skapa ett nytt GUID i PowerShell skriver du `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="86e97-181">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="86e97-182">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="86e97-182">-ModulesToImport</span></span>

<span data-ttu-id="86e97-183">Anger de moduler som importeras automatiskt till sessioner som använder roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-183">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="86e97-184">Som standard visas alla kommandon i de moduler som visas.</span><span class="sxs-lookup"><span data-stu-id="86e97-184">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="86e97-185">När det används med **VisibleCmdlets** eller **VisibleFunctions** kan de kommandon som visas i de angivna modulerna begränsas.</span><span class="sxs-lookup"><span data-stu-id="86e97-185">When used with **VisibleCmdlets** or **VisibleFunctions**, the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="86e97-186">Varje modul som används i värdet för den här parametern kan representeras av en sträng eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="86e97-186">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="86e97-187">En modul sträng består bara av namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="86e97-187">A module string consists only of the name of the module.</span></span> <span data-ttu-id="86e97-188">En modul hash-tabell kan innehålla **Modulnamn**, **ModuleVersion** och **GUID** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="86e97-188">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="86e97-189">Endast nyckeln **Modulnamn** krävs.</span><span class="sxs-lookup"><span data-stu-id="86e97-189">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="86e97-190">Följande värde består till exempel av en sträng och en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="86e97-190">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="86e97-191">En valfri kombination av strängar och hash-tabeller, i vilken ordning som helst, är giltig.</span><span class="sxs-lookup"><span data-stu-id="86e97-191">Any combination of strings and hash tables, in any order, is valid.</span></span>

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

### <span data-ttu-id="86e97-192">-Path</span><span class="sxs-lookup"><span data-stu-id="86e97-192">-Path</span></span>

<span data-ttu-id="86e97-193">Anger sökväg och fil namn för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-193">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="86e97-194">Filen måste ha ett `.psrc` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="86e97-194">The file must have a `.psrc` filename extension.</span></span>

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

### <span data-ttu-id="86e97-195">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="86e97-195">-ScriptsToProcess</span></span>

<span data-ttu-id="86e97-196">Anger skript som ska läggas till i sessioner som använder en roll funktions fil.</span><span class="sxs-lookup"><span data-stu-id="86e97-196">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="86e97-197">Ange sökväg och fil namn för skripten.</span><span class="sxs-lookup"><span data-stu-id="86e97-197">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="86e97-198">Värdet för den här parametern måste vara en fullständig eller absolut sökväg till skript fil namnen.</span><span class="sxs-lookup"><span data-stu-id="86e97-198">The value of this parameter must be a full or absolute path of the script file names.</span></span>

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

### <span data-ttu-id="86e97-199">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="86e97-199">-TypesToProcess</span></span>

<span data-ttu-id="86e97-200">Anger typ filer (. ps1xml) som ska läggas till i sessioner som använder sig av roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-200">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="86e97-201">Ange typ fil namn.</span><span class="sxs-lookup"><span data-stu-id="86e97-201">Enter the type filenames.</span></span> <span data-ttu-id="86e97-202">Värdet för den här parametern måste vara en fullständig eller absolut sökväg av typ fil namnen.</span><span class="sxs-lookup"><span data-stu-id="86e97-202">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

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

### <span data-ttu-id="86e97-203">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="86e97-203">-VariableDefinitions</span></span>

<span data-ttu-id="86e97-204">Anger variabler som ska läggas till i sessioner som använder sig av roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="86e97-204">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="86e97-205">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="86e97-205">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="86e97-206">Namn.</span><span class="sxs-lookup"><span data-stu-id="86e97-206">Name.</span></span> <span data-ttu-id="86e97-207">Variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="86e97-207">Name of the variable.</span></span> <span data-ttu-id="86e97-208">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="86e97-208">This key is required.</span></span>
- <span data-ttu-id="86e97-209">Värde.</span><span class="sxs-lookup"><span data-stu-id="86e97-209">Value.</span></span> <span data-ttu-id="86e97-210">Variabel värde.</span><span class="sxs-lookup"><span data-stu-id="86e97-210">Variable value.</span></span> <span data-ttu-id="86e97-211">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="86e97-211">This key is required.</span></span>
- <span data-ttu-id="86e97-212">Alternativ.</span><span class="sxs-lookup"><span data-stu-id="86e97-212">Options.</span></span> <span data-ttu-id="86e97-213">Variabel alternativ.</span><span class="sxs-lookup"><span data-stu-id="86e97-213">Variable options.</span></span> <span data-ttu-id="86e97-214">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="86e97-214">This key is optional.</span></span> <span data-ttu-id="86e97-215">Standardvärdet är none.</span><span class="sxs-lookup"><span data-stu-id="86e97-215">The default value is None.</span></span> <span data-ttu-id="86e97-216">De acceptabla värdena för den här parametern är: är ingen, ReadOnly, konstant, privat eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="86e97-216">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="86e97-217">Exempel: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="86e97-217">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

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

### <span data-ttu-id="86e97-218">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="86e97-218">-VisibleAliases</span></span>

<span data-ttu-id="86e97-219">Begränsar alias i sessionen till de alias som anges i värdet för den här parametern, plus alla alias som du definierar i parametern **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="86e97-219">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="86e97-220">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="86e97-220">Wildcard characters are supported.</span></span>
<span data-ttu-id="86e97-221">Som standard visas alla alias som definieras av PowerShell-motorn och alla alias som moduler exporterar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-221">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="86e97-222">Om du till exempel vill begränsa tillgängliga alias till GM och GCM använder du följande syntax: `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="86e97-222">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="86e97-223">När en **Visible** -parameter ingår i roll funktions filen, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-223">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="86e97-224">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="86e97-224">-VisibleCmdlets</span></span>

<span data-ttu-id="86e97-225">Begränsar cmdletarna i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="86e97-225">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="86e97-226">Jokertecken och kvalificerade namn för module stöds.</span><span class="sxs-lookup"><span data-stu-id="86e97-226">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="86e97-227">Som standard visas alla cmdletar som modulerna i sessionen exporterar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-227">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="86e97-228">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-228">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="86e97-229">Om inga moduler i **ModulesToImport** exponerar cmdleten `New-PSRoleCapabilityFile` försöker läsa in lämplig modul.</span><span class="sxs-lookup"><span data-stu-id="86e97-229">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="86e97-230">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-230">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="86e97-231">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="86e97-231">-VisibleExternalCommands</span></span>

<span data-ttu-id="86e97-232">Begränsar de externa binärfilerna, skripten och kommandona som kan köras i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="86e97-232">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="86e97-233">Som standard visas inga externa kommandon i den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-233">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="86e97-234">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-234">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="86e97-235">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="86e97-235">-VisibleFunctions</span></span>

<span data-ttu-id="86e97-236">Begränsar funktionerna i sessionen till de som anges i värdet för den här parametern, plus de funktioner som du definierar i parametern **FunctionDefinitions** .</span><span class="sxs-lookup"><span data-stu-id="86e97-236">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="86e97-237">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="86e97-237">Wildcard characters are supported.</span></span>

<span data-ttu-id="86e97-238">Som standard visas alla funktioner som exporteras av moduler i sessionen i den sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-238">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="86e97-239">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-239">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="86e97-240">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-240">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="86e97-241">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="86e97-241">-VisibleProviders</span></span>

<span data-ttu-id="86e97-242">Begränsar PowerShell-providern i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="86e97-242">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="86e97-243">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="86e97-243">Wildcard characters are supported.</span></span>

<span data-ttu-id="86e97-244">Som standard visas alla providrar som exporteras av en modul i sessionen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-244">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="86e97-245">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-245">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="86e97-246">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="86e97-246">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="86e97-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86e97-247">CommonParameters</span></span>

<span data-ttu-id="86e97-248">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="86e97-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86e97-249">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="86e97-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="86e97-250">INDATA</span><span class="sxs-lookup"><span data-stu-id="86e97-250">INPUTS</span></span>

## <span data-ttu-id="86e97-251">UTDATA</span><span class="sxs-lookup"><span data-stu-id="86e97-251">OUTPUTS</span></span>

## <span data-ttu-id="86e97-252">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="86e97-252">NOTES</span></span>

## <span data-ttu-id="86e97-253">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="86e97-253">RELATED LINKS</span></span>

[<span data-ttu-id="86e97-254">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="86e97-254">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="86e97-255">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="86e97-255">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)

