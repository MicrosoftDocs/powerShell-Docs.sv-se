---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: 21b8dc249c93ae68ad3e43f998ede5dfe7a82766
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264477"
---
# <span data-ttu-id="b4356-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="b4356-103">Find-Script</span></span>

## <span data-ttu-id="b4356-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b4356-104">SYNOPSIS</span></span>
<span data-ttu-id="b4356-105">Söker efter ett skript.</span><span class="sxs-lookup"><span data-stu-id="b4356-105">Finds a script.</span></span>

## <span data-ttu-id="b4356-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b4356-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="b4356-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b4356-107">DESCRIPTION</span></span>

<span data-ttu-id="b4356-108">Cmdleten **find-script** söker efter ett angivet skript i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="b4356-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="b4356-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b4356-109">EXAMPLES</span></span>

### <span data-ttu-id="b4356-110">Exempel 1: Sök efter alla tillgängliga skript</span><span class="sxs-lookup"><span data-stu-id="b4356-110">Example 1: Find all available scripts</span></span>

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

<span data-ttu-id="b4356-111">Det här kommandot hittar alla tillgängliga skript.</span><span class="sxs-lookup"><span data-stu-id="b4356-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="b4356-112">Exempel 2: Sök efter ett skript efter namn</span><span class="sxs-lookup"><span data-stu-id="b4356-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="b4356-113">Det här kommandot hittar skriptet med namnet start-WFContosoServer.</span><span class="sxs-lookup"><span data-stu-id="b4356-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="b4356-114">Exempel 3: Sök efter ett skript efter namn, version som krävs och från en angiven lagrings plats</span><span class="sxs-lookup"><span data-stu-id="b4356-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="b4356-115">Det här kommandot hittar ett skript efter namn och nödvändig version i LocalRepo01-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="b4356-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="b4356-116">Exempel 4: hitta ett skript och formatera utdata som en lista</span><span class="sxs-lookup"><span data-stu-id="b4356-116">Example 4: Find a script and format the output as a list</span></span>

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

<span data-ttu-id="b4356-117">Det här kommandot hittar Required-Script2 i LocalRepo1-lagringsplatsen och skickar sedan det resulterande **PSRepositoryItemInfo** -objektet till Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b4356-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="b4356-118">Exempel 5: hitta ett skript i det angivna versions intervallet</span><span class="sxs-lookup"><span data-stu-id="b4356-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="b4356-119">Det här kommandot hittar alla versioner av RequiredScript2 mellan versionerna 2,1 och 2,5 i LocalRepo1-lager.</span><span class="sxs-lookup"><span data-stu-id="b4356-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="b4356-120">Exempel 6: hitta alla versioner av ett skript</span><span class="sxs-lookup"><span data-stu-id="b4356-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="b4356-121">Det här kommandot hittar alla versioner av required-Script02.</span><span class="sxs-lookup"><span data-stu-id="b4356-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="b4356-122">Exempel 7: Sök efter ett skript och dess beroenden</span><span class="sxs-lookup"><span data-stu-id="b4356-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="b4356-123">Det här kommandot hittar ett skript och dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="b4356-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="b4356-124">Exempel 8: hitta skript med den angivna taggen</span><span class="sxs-lookup"><span data-stu-id="b4356-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="b4356-125">Det här kommandot hittar skript som har taggen Tagg1 i LocalRepo1-lagringsplatsen</span><span class="sxs-lookup"><span data-stu-id="b4356-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="b4356-126">Exempel 9: hitta skript med angivet kommando namn</span><span class="sxs-lookup"><span data-stu-id="b4356-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="b4356-127">Det här kommandot hittar ett skript som innehåller det angivna kommando namnet.</span><span class="sxs-lookup"><span data-stu-id="b4356-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="b4356-128">Exempel 10: hitta skript med arbets flöden</span><span class="sxs-lookup"><span data-stu-id="b4356-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="b4356-129">Det här kommandot hittar arbets flödes skript i LocalRepo1-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="b4356-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="b4356-130">Exempel 11: hitta skript med jokertecken</span><span class="sxs-lookup"><span data-stu-id="b4356-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="b4356-131">Det här kommandot använder jokertecknet (\*) för att hitta skript som börjar med required-script.</span><span class="sxs-lookup"><span data-stu-id="b4356-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="b4356-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b4356-132">PARAMETERS</span></span>

### <span data-ttu-id="b4356-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="b4356-133">-AllowPrerelease</span></span>

<span data-ttu-id="b4356-134">Innehåller i de resultat skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="b4356-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="b4356-135">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="b4356-135">-AllVersions</span></span>

<span data-ttu-id="b4356-136">Anger att den här åtgärden hittar alla skript versioner.</span><span class="sxs-lookup"><span data-stu-id="b4356-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="b4356-137">-Kommando</span><span class="sxs-lookup"><span data-stu-id="b4356-137">-Command</span></span>

<span data-ttu-id="b4356-138">Anger en matris med kommandon som ska hittas i skript.</span><span class="sxs-lookup"><span data-stu-id="b4356-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="b4356-139">Ett kommando kan vara en funktion eller ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="b4356-139">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="b4356-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="b4356-140">-Credential</span></span>

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

### <span data-ttu-id="b4356-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="b4356-141">-Filter</span></span>

<span data-ttu-id="b4356-142">Söker efter skript baserat på PackageManagement-providerspecifika söksyntax.</span><span class="sxs-lookup"><span data-stu-id="b4356-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

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

### <span data-ttu-id="b4356-143">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="b4356-143">-IncludeDependencies</span></span>

<span data-ttu-id="b4356-144">Anger att den här åtgärden hämtar alla skript som är beroende av det skript som anges i parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="b4356-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="b4356-145">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="b4356-145">-Includes</span></span>

<span data-ttu-id="b4356-146">Anger vilken typ av skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="b4356-146">Specifies type of script to get.</span></span>
<span data-ttu-id="b4356-147">De acceptabla värdena för den här parametern är: funktion, arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="b4356-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

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

### <span data-ttu-id="b4356-148">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b4356-148">-MaximumVersion</span></span>

<span data-ttu-id="b4356-149">Anger den maximala eller nyaste versionen av skriptet som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="b4356-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="b4356-150">Parametrarna *MaximumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="b4356-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="b4356-151">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b4356-151">-MinimumVersion</span></span>

<span data-ttu-id="b4356-152">Anger den lägsta version av skriptet som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="b4356-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="b4356-153">Parametrarna *MinimumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="b4356-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="b4356-154">-Name</span><span class="sxs-lookup"><span data-stu-id="b4356-154">-Name</span></span>

<span data-ttu-id="b4356-155">Anger en matris med namn på de skript som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="b4356-155">Specifies an array of names of scripts to find.</span></span>

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

### <span data-ttu-id="b4356-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="b4356-156">-Proxy</span></span>

<span data-ttu-id="b4356-157">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="b4356-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="b4356-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b4356-158">-ProxyCredential</span></span>

<span data-ttu-id="b4356-159">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="b4356-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b4356-160">– Databas</span><span class="sxs-lookup"><span data-stu-id="b4356-160">-Repository</span></span>

<span data-ttu-id="b4356-161">Anger det egna namnet på en lagrings plats som har registrerats genom att köra register-PSRepository.</span><span class="sxs-lookup"><span data-stu-id="b4356-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

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

### <span data-ttu-id="b4356-162">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b4356-162">-RequiredVersion</span></span>

<span data-ttu-id="b4356-163">Anger det exakta versions numret för det skript som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="b4356-163">Specifies the exact version number of the script to find.</span></span>

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

### <span data-ttu-id="b4356-164">-Tagga</span><span class="sxs-lookup"><span data-stu-id="b4356-164">-Tag</span></span>

<span data-ttu-id="b4356-165">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="b4356-165">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="b4356-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b4356-166">CommonParameters</span></span>

<span data-ttu-id="b4356-167">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b4356-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b4356-168">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b4356-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b4356-169">INDATA</span><span class="sxs-lookup"><span data-stu-id="b4356-169">INPUTS</span></span>

## <span data-ttu-id="b4356-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b4356-170">OUTPUTS</span></span>

### <span data-ttu-id="b4356-171">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="b4356-171">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="b4356-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b4356-172">NOTES</span></span>

## <span data-ttu-id="b4356-173">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b4356-173">RELATED LINKS</span></span>

[<span data-ttu-id="b4356-174">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="b4356-174">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="b4356-175">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="b4356-175">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="b4356-176">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="b4356-176">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="b4356-177">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="b4356-177">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="b4356-178">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="b4356-178">Update-Script</span></span>](Update-Script.md)