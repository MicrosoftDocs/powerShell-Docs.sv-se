---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: 6eb617987b437337dc3c42c33f55033b64ec8a79
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262305"
---
# <span data-ttu-id="9d815-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="9d815-103">Find-Script</span></span>

## <span data-ttu-id="9d815-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9d815-104">SYNOPSIS</span></span>
<span data-ttu-id="9d815-105">Söker efter ett skript.</span><span class="sxs-lookup"><span data-stu-id="9d815-105">Finds a script.</span></span>

## <span data-ttu-id="9d815-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9d815-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="9d815-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9d815-107">DESCRIPTION</span></span>

<span data-ttu-id="9d815-108">Cmdleten **find-script** söker efter ett angivet skript i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="9d815-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="9d815-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9d815-109">EXAMPLES</span></span>

### <span data-ttu-id="9d815-110">Exempel 1: Sök efter alla tillgängliga skript</span><span class="sxs-lookup"><span data-stu-id="9d815-110">Example 1: Find all available scripts</span></span>

```
PS C:\> Find-Script
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
2.5        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
2.5        Fabrikam-ServerScript               Script     LocalRepo1           Description for the Fabrikam-ServerScript script
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        Script-WithDependencies2            Script     LocalRepo1           Description for the Script-WithDependencies2 script
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
2.1        Test-Script1                        Script     LocalRepo1           Test-Script1 Script example
2.0        Test-Script2                        Script     LocalRepo1           Test-Script2 Script example
1.0        TestRunbook                         Script     LocalRepo1           Contoso Script example
```

<span data-ttu-id="9d815-111">Det här kommandot hittar alla tillgängliga skript.</span><span class="sxs-lookup"><span data-stu-id="9d815-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="9d815-112">Exempel 2: Sök efter ett skript efter namn</span><span class="sxs-lookup"><span data-stu-id="9d815-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="9d815-113">Det här kommandot hittar skriptet med namnet start-WFContosoServer.</span><span class="sxs-lookup"><span data-stu-id="9d815-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="9d815-114">Exempel 3: Sök efter ett skript efter namn, version som krävs och från en angiven lagrings plats</span><span class="sxs-lookup"><span data-stu-id="9d815-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="9d815-115">Det här kommandot hittar ett skript efter namn och nödvändig version i LocalRepo01-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="9d815-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="9d815-116">Exempel 4: hitta ett skript och formatera utdata som en lista</span><span class="sxs-lookup"><span data-stu-id="9d815-116">Example 4: Find a script and format the output as a list</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo1" | Format-List * -Force
Name                       : Required-Script2
Version                    : 2.0
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/14/2015 2:37:01 PM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {, Tag1, Tag2, Tag-Required-Script2-2.0...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : C:\MyLocalRepo
Repository                 : LocalRepo01
PackageManagementProvider  : NuGet
```

<span data-ttu-id="9d815-117">Det här kommandot hittar Required-Script2 i LocalRepo1-lagringsplatsen och skickar sedan det resulterande **PSRepositoryItemInfo** -objektet till Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9d815-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="9d815-118">Exempel 5: hitta ett skript i det angivna versions intervallet</span><span class="sxs-lookup"><span data-stu-id="9d815-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="9d815-119">Det här kommandot hittar alla versioner av RequiredScript2 mellan versionerna 2,1 och 2,5 i LocalRepo1-lager.</span><span class="sxs-lookup"><span data-stu-id="9d815-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="9d815-120">Exempel 6: hitta alla versioner av ett skript</span><span class="sxs-lookup"><span data-stu-id="9d815-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="9d815-121">Det här kommandot hittar alla versioner av required-Script02.</span><span class="sxs-lookup"><span data-stu-id="9d815-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="9d815-122">Exempel 7: Sök efter ett skript och dess beroenden</span><span class="sxs-lookup"><span data-stu-id="9d815-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="9d815-123">Det här kommandot hittar ett skript och dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="9d815-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="9d815-124">Exempel 8: hitta skript med den angivna taggen</span><span class="sxs-lookup"><span data-stu-id="9d815-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="9d815-125">Det här kommandot hittar skript som har taggen Tagg1 i LocalRepo1-lagringsplatsen</span><span class="sxs-lookup"><span data-stu-id="9d815-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="9d815-126">Exempel 9: hitta skript med angivet kommando namn</span><span class="sxs-lookup"><span data-stu-id="9d815-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="9d815-127">Det här kommandot hittar ett skript som innehåller det angivna kommando namnet.</span><span class="sxs-lookup"><span data-stu-id="9d815-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="9d815-128">Exempel 10: hitta skript med arbets flöden</span><span class="sxs-lookup"><span data-stu-id="9d815-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="9d815-129">Det här kommandot hittar arbets flödes skript i LocalRepo1-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="9d815-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="9d815-130">Exempel 11: hitta skript med jokertecken</span><span class="sxs-lookup"><span data-stu-id="9d815-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="9d815-131">Det här kommandot använder jokertecknet (\*) för att hitta skript som börjar med required-script.</span><span class="sxs-lookup"><span data-stu-id="9d815-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="9d815-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9d815-132">PARAMETERS</span></span>

### <span data-ttu-id="9d815-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9d815-133">-AllowPrerelease</span></span>

<span data-ttu-id="9d815-134">Innehåller i de resultat skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="9d815-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="9d815-135">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="9d815-135">-AllVersions</span></span>

<span data-ttu-id="9d815-136">Anger att den här åtgärden hittar alla skript versioner.</span><span class="sxs-lookup"><span data-stu-id="9d815-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="9d815-137">-Kommando</span><span class="sxs-lookup"><span data-stu-id="9d815-137">-Command</span></span>

<span data-ttu-id="9d815-138">Anger en matris med kommandon som ska hittas i skript.</span><span class="sxs-lookup"><span data-stu-id="9d815-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="9d815-139">Ett kommando kan vara en funktion eller ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="9d815-139">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="9d815-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="9d815-140">-Credential</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="9d815-141">-Filter</span></span>

<span data-ttu-id="9d815-142">Söker efter skript baserat på PackageManagement-providerspecifika söksyntax.</span><span class="sxs-lookup"><span data-stu-id="9d815-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

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

### <span data-ttu-id="9d815-143">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="9d815-143">-IncludeDependencies</span></span>

<span data-ttu-id="9d815-144">Anger att den här åtgärden hämtar alla skript som är beroende av det skript som anges i parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="9d815-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="9d815-145">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="9d815-145">-Includes</span></span>

<span data-ttu-id="9d815-146">Anger vilken typ av skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="9d815-146">Specifies type of script to get.</span></span>
<span data-ttu-id="9d815-147">De acceptabla värdena för den här parametern är: funktion, arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="9d815-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Function, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-148">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9d815-148">-MaximumVersion</span></span>

<span data-ttu-id="9d815-149">Anger den maximala eller nyaste versionen av skriptet som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="9d815-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="9d815-150">Parametrarna *MaximumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="9d815-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-151">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9d815-151">-MinimumVersion</span></span>

<span data-ttu-id="9d815-152">Anger den lägsta version av skriptet som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="9d815-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="9d815-153">Parametrarna *MinimumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="9d815-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-154">-Name</span><span class="sxs-lookup"><span data-stu-id="9d815-154">-Name</span></span>

<span data-ttu-id="9d815-155">Anger en matris med namn på de skript som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="9d815-155">Specifies an array of names of scripts to find.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9d815-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="9d815-156">-Proxy</span></span>

<span data-ttu-id="9d815-157">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="9d815-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="9d815-158">-ProxyCredential</span></span>

<span data-ttu-id="9d815-159">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="9d815-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-160">– Databas</span><span class="sxs-lookup"><span data-stu-id="9d815-160">-Repository</span></span>

<span data-ttu-id="9d815-161">Anger det egna namnet på en lagrings plats som har registrerats genom att köra register-PSRepository.</span><span class="sxs-lookup"><span data-stu-id="9d815-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

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

### <span data-ttu-id="9d815-162">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9d815-162">-RequiredVersion</span></span>

<span data-ttu-id="9d815-163">Anger det exakta versions numret för det skript som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="9d815-163">Specifies the exact version number of the script to find.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9d815-164">-Tagga</span><span class="sxs-lookup"><span data-stu-id="9d815-164">-Tag</span></span>

<span data-ttu-id="9d815-165">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="9d815-165">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="9d815-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9d815-166">CommonParameters</span></span>

<span data-ttu-id="9d815-167">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9d815-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9d815-168">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9d815-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9d815-169">INDATA</span><span class="sxs-lookup"><span data-stu-id="9d815-169">INPUTS</span></span>

### <span data-ttu-id="9d815-170">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9d815-170">System.String[]</span></span>

### <span data-ttu-id="9d815-171">System. String</span><span class="sxs-lookup"><span data-stu-id="9d815-171">System.String</span></span>

### <span data-ttu-id="9d815-172">System. URI</span><span class="sxs-lookup"><span data-stu-id="9d815-172">System.Uri</span></span>

### <span data-ttu-id="9d815-173">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="9d815-173">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="9d815-174">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9d815-174">OUTPUTS</span></span>

### <span data-ttu-id="9d815-175">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="9d815-175">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="9d815-176">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9d815-176">NOTES</span></span>

## <span data-ttu-id="9d815-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9d815-177">RELATED LINKS</span></span>

[<span data-ttu-id="9d815-178">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="9d815-178">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="9d815-179">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="9d815-179">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="9d815-180">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="9d815-180">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="9d815-181">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="9d815-181">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="9d815-182">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="9d815-182">Update-Script</span></span>](Update-Script.md)
