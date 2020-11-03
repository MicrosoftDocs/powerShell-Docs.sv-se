---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: dd4e8169310f23182697ba6bf4263d916f747b84
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262940"
---
# <span data-ttu-id="91279-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="91279-103">Install-Script</span></span>

## <span data-ttu-id="91279-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="91279-104">SYNOPSIS</span></span>
<span data-ttu-id="91279-105">Installerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="91279-105">Installs a script.</span></span>

## <span data-ttu-id="91279-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="91279-106">SYNTAX</span></span>

### <span data-ttu-id="91279-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="91279-107">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="91279-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="91279-108">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="91279-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="91279-109">DESCRIPTION</span></span>

<span data-ttu-id="91279-110">`Install-Script`Cmdlet: en hämtar en skript nytto Last från en lagrings plats, verifierar att nytto lasten är ett giltigt PowerShell-skript och kopierar skript filen till en angiven installations plats.</span><span class="sxs-lookup"><span data-stu-id="91279-110">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="91279-111">Standard databaserna `Install-Script` fungerar i kan konfigureras via `Register-PSRepository` `Set-PSRepository` `Unregister-PSRepository` cmdletarna,, och `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="91279-111">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="91279-112">När du arbetar med flera databaser `Install-Script` installerar det första skriptet som matchar de angivna Sök kriterierna ( **namn** , **MinimumVersion** eller **MaximumVersion** ) från den första lagrings platsen utan fel.</span><span class="sxs-lookup"><span data-stu-id="91279-112">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria ( **Name** , **MinimumVersion** , or **MaximumVersion** ) from the first repository without any error.</span></span>

## <span data-ttu-id="91279-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="91279-113">EXAMPLES</span></span>

### <span data-ttu-id="91279-114">Exempel 1: hitta ett skript och installera det</span><span class="sxs-lookup"><span data-stu-id="91279-114">Example 1: Find a script and install it</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

<span data-ttu-id="91279-115">Det första kommandot hittar skriptet som heter `Required-Script2` från Local1-lagringsplatsen och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="91279-115">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="91279-116">Det andra kommandot hittar `Required-Script2` skriptet och använder sedan pipeline-operatorn för att skicka det till `Install-Script` cmdlet: en för att installera det.</span><span class="sxs-lookup"><span data-stu-id="91279-116">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="91279-117">Det tredje kommandot använder `Get-Command` cmdleten för att hämta `Required-Script2` och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="91279-117">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="91279-118">Det fjärde kommandot använder `Get-InstalledScript` cmdleten för att hämta `Required-Script2` och visa resultaten.</span><span class="sxs-lookup"><span data-stu-id="91279-118">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="91279-119">Det femte kommandot hämtar `Required-Script2` och använder pipeline-operatorn för att skicka den till `Format-List` cmdlet: en för att formatera utdata.</span><span class="sxs-lookup"><span data-stu-id="91279-119">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="91279-120">Exempel 2: installera ett skript med AllUsers-scope</span><span class="sxs-lookup"><span data-stu-id="91279-120">Example 2: Install a script with AllUsers scope</span></span>

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

<span data-ttu-id="91279-121">Det första kommandot installerar skriptet med namnet `Required-Script3` och tilldelar det allusers-omfånget.</span><span class="sxs-lookup"><span data-stu-id="91279-121">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="91279-122">Det andra kommandot hämtar det installerade skriptet `Required-Script3` och visar information om det.</span><span class="sxs-lookup"><span data-stu-id="91279-122">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="91279-123">Det tredje kommandot hämtar `Required-Script3` och använder pipeline-operatorn för att skicka den till `Format-List` cmdlet: en för att formatera utdata.</span><span class="sxs-lookup"><span data-stu-id="91279-123">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="91279-124">Exempel 3: installera ett skript och dess beroenden</span><span class="sxs-lookup"><span data-stu-id="91279-124">Example 3: Install a script and its dependencies</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

<span data-ttu-id="91279-125">Det första kommandot hittar skriptet med namnet `Script-WithDependencies2` och dess beroenden i Local1-lagringsplatsen och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="91279-125">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="91279-126">Det andra kommandot installeras `Script-WithDependencies2` .</span><span class="sxs-lookup"><span data-stu-id="91279-126">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="91279-127">Det tredje kommandot använder `Get-InstalledScript` skript-cmdleten för att hämta installerade skript och visa resultaten.</span><span class="sxs-lookup"><span data-stu-id="91279-127">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="91279-128">Det fjärde kommandot använder `Get-InstalledModule` cmdleten för att hämta installerade moduler och visa resultatet.</span><span class="sxs-lookup"><span data-stu-id="91279-128">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="91279-129">Det femte kommandot använder `Find-Script` cmdleten för att hitta skript där namnet börjar med `Required-Script` och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="91279-129">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="91279-130">Det sjätte kommandot installerar skripten där namnet börjar med `Required-Script` i Local1-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="91279-130">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="91279-131">Det sista kommandot hämtar installerade skript och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="91279-131">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="91279-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="91279-132">PARAMETERS</span></span>

### <span data-ttu-id="91279-133">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="91279-133">-AcceptLicense</span></span>

<span data-ttu-id="91279-134">Godkänn licens avtalet automatiskt under installationen om modulen kräver det.</span><span class="sxs-lookup"><span data-stu-id="91279-134">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="91279-135">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="91279-135">-AllowPrerelease</span></span>

<span data-ttu-id="91279-136">Gör att du kan installera ett skript som är markerat som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="91279-136">Allows you to install a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91279-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="91279-137">-Confirm</span></span>

<span data-ttu-id="91279-138">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="91279-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="91279-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="91279-139">-Credential</span></span>

<span data-ttu-id="91279-140">Anger ett användar konto som har behörighet att installera ett skript för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="91279-140">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="91279-141">-Force</span><span class="sxs-lookup"><span data-stu-id="91279-141">-Force</span></span>

<span data-ttu-id="91279-142">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="91279-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="91279-143">– InputObject</span><span class="sxs-lookup"><span data-stu-id="91279-143">-InputObject</span></span>

<span data-ttu-id="91279-144">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="91279-144">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="91279-145">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="91279-145">-MaximumVersion</span></span>

<span data-ttu-id="91279-146">Anger den högsta versionen av ett enstaka skript som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="91279-146">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="91279-147">Du kan inte lägga till den här parametern om du försöker installera flera skript.</span><span class="sxs-lookup"><span data-stu-id="91279-147">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="91279-148">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="91279-148">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91279-149">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="91279-149">-MinimumVersion</span></span>

<span data-ttu-id="91279-150">Anger den lägsta version av ett enskilt skript som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="91279-150">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="91279-151">Du kan inte lägga till den här parametern om du försöker installera flera skript.</span><span class="sxs-lookup"><span data-stu-id="91279-151">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="91279-152">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="91279-152">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91279-153">-Name</span><span class="sxs-lookup"><span data-stu-id="91279-153">-Name</span></span>

<span data-ttu-id="91279-154">Anger en matris med namn på skript som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="91279-154">Specifies an array of names of scripts to install.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91279-155">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="91279-155">-NoPathUpdate</span></span>

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

### <span data-ttu-id="91279-156">– PassThru</span><span class="sxs-lookup"><span data-stu-id="91279-156">-PassThru</span></span>

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

### <span data-ttu-id="91279-157">-Proxy</span><span class="sxs-lookup"><span data-stu-id="91279-157">-Proxy</span></span>

<span data-ttu-id="91279-158">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="91279-158">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="91279-159">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="91279-159">-ProxyCredential</span></span>

<span data-ttu-id="91279-160">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="91279-160">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="91279-161">– Databas</span><span class="sxs-lookup"><span data-stu-id="91279-161">-Repository</span></span>

<span data-ttu-id="91279-162">Anger det egna namnet på en lagrings plats som har registrerats med `Register-PSRepository` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="91279-162">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="91279-163">Standardvärdet är alla registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="91279-163">The default is all registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91279-164">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="91279-164">-RequiredVersion</span></span>

<span data-ttu-id="91279-165">Anger det exakta versions numret för det skript som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="91279-165">Specifies the exact version number of the script to install.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91279-166">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="91279-166">-Scope</span></span>

<span data-ttu-id="91279-167">Anger skriptets installations omfång.</span><span class="sxs-lookup"><span data-stu-id="91279-167">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="91279-168">Giltiga värden är: AllUsers och CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="91279-168">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="91279-169">Med AllUsers omfattning kan moduler installeras på en plats som är tillgänglig för alla användare av datorn, det vill säga `$env:ProgramFiles\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="91279-169">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="91279-170">I CurrentUser-scopet kan moduler endast installeras till `$home\Documents\WindowsPowerShell\Scripts` , så att modulen endast är tillgänglig för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="91279-170">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="91279-171">När inget **omfång** har definierats anges standardvärdet baserat på den aktuella sessionen:</span><span class="sxs-lookup"><span data-stu-id="91279-171">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="91279-172">För en upphöjd **PowerShell-session** är standardvärdet allusers;</span><span class="sxs-lookup"><span data-stu-id="91279-172">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="91279-173">För icke-förhöjda PowerShell-sessioner i [PowerShellGet-versioner 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) och senare, är **omfånget** CurrentUser;</span><span class="sxs-lookup"><span data-stu-id="91279-173">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="91279-174">För icke-förhöjda PowerShell-sessioner i PowerShellGet-versioner 1.6.7 och tidigare, är **omfånget** odefinierat och `Install-Module` fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="91279-174">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91279-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="91279-175">-WhatIf</span></span>

<span data-ttu-id="91279-176">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="91279-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="91279-177">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="91279-177">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="91279-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="91279-178">CommonParameters</span></span>

<span data-ttu-id="91279-179">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="91279-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="91279-180">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="91279-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="91279-181">INDATA</span><span class="sxs-lookup"><span data-stu-id="91279-181">INPUTS</span></span>

### <span data-ttu-id="91279-182">System.String[]</span><span class="sxs-lookup"><span data-stu-id="91279-182">System.String[]</span></span>

### <span data-ttu-id="91279-183">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="91279-183">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="91279-184">System. String</span><span class="sxs-lookup"><span data-stu-id="91279-184">System.String</span></span>

### <span data-ttu-id="91279-185">System. URI</span><span class="sxs-lookup"><span data-stu-id="91279-185">System.Uri</span></span>

### <span data-ttu-id="91279-186">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="91279-186">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="91279-187">UTDATA</span><span class="sxs-lookup"><span data-stu-id="91279-187">OUTPUTS</span></span>

### <span data-ttu-id="91279-188">System. Object</span><span class="sxs-lookup"><span data-stu-id="91279-188">System.Object</span></span>

## <span data-ttu-id="91279-189">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="91279-189">NOTES</span></span>

## <span data-ttu-id="91279-190">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="91279-190">RELATED LINKS</span></span>

[<span data-ttu-id="91279-191">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="91279-191">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="91279-192">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="91279-192">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="91279-193">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="91279-193">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="91279-194">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="91279-194">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="91279-195">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="91279-195">Update-Script</span></span>](Update-Script.md)
