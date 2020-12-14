---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 9aff0ff794bea42da7690a77357c1d76f747a004
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892177"
---
# <span data-ttu-id="ae3f3-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="ae3f3-103">Save-Module</span></span>

## <span data-ttu-id="ae3f3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ae3f3-104">SYNOPSIS</span></span>
<span data-ttu-id="ae3f3-105">Sparar en modul och dess beroenden på den lokala datorn, men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="ae3f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ae3f3-106">SYNTAX</span></span>

### <span data-ttu-id="ae3f3-107">NameAndPathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ae3f3-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ae3f3-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ae3f3-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ae3f3-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ae3f3-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ae3f3-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ae3f3-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ae3f3-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ae3f3-111">DESCRIPTION</span></span>

<span data-ttu-id="ae3f3-112">`Save-Module`Cmdlet: en laddar ned en modul och eventuella beroenden från en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="ae3f3-113">`Save-Module` hämtar och sparar den mest aktuella versionen av en modul.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="ae3f3-114">Filerna sparas till en angiven sökväg på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="ae3f3-115">Modulen är inte installerad, men innehållet är tillgängligt för granskning av en administratör.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="ae3f3-116">Den sparade modulen kan sedan kopieras till den aktuella `$env:PSModulePath` platsen för den frånkopplade datorn.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="ae3f3-117">`Get-PSRepository` visar den lokala datorns registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="ae3f3-118">Du kan använda `Find-Module` cmdleten för att söka i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="ae3f3-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ae3f3-119">EXAMPLES</span></span>

### <span data-ttu-id="ae3f3-120">Exempel 1: Spara en modul</span><span class="sxs-lookup"><span data-stu-id="ae3f3-120">Example 1: Save a module</span></span>

<span data-ttu-id="ae3f3-121">I det här exemplet sparas en modul och dess beroenden på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="ae3f3-122">`Save-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="ae3f3-123">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="ae3f3-124">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-124">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="ae3f3-125">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="ae3f3-126">Exempel 2: Spara en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="ae3f3-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="ae3f3-127">Det här exemplet visar hur du använder en parameter, till exempel **MaximumVersion** eller **RequiredVersion** för att ange en version av en modul.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-127">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="ae3f3-128">`Save-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="ae3f3-129">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="ae3f3-130">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-130">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="ae3f3-131">**MaximumVersion** anger att version **2.1.0** har laddats ned och sparats.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="ae3f3-132">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="ae3f3-133">Exempel 3: söka efter och spara en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="ae3f3-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="ae3f3-134">I det här exemplet finns en nödvändig modul version i lagrings platsen och sparas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="ae3f3-135">`Find-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="ae3f3-136">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-136">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="ae3f3-137">**RequiredVersion** anger version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-137">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="ae3f3-138">Objektet skickas ned pipelinen till `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="ae3f3-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="ae3f3-139">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="ae3f3-140">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="ae3f3-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ae3f3-141">PARAMETERS</span></span>

### <span data-ttu-id="ae3f3-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ae3f3-142">-AcceptLicense</span></span>

<span data-ttu-id="ae3f3-143">Godkänn licens avtalet automatiskt om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-143">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="ae3f3-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ae3f3-144">-AllowPrerelease</span></span>

<span data-ttu-id="ae3f3-145">Gör att du kan spara en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-145">Allows you to save a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ae3f3-146">-Confirm</span></span>

<span data-ttu-id="ae3f3-147">Du uppmanas att bekräfta innan du kör `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="ae3f3-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="ae3f3-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="ae3f3-148">-Credential</span></span>

<span data-ttu-id="ae3f3-149">Anger ett användar konto som har behörighet att spara en modul.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-149">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="ae3f3-150">-Force</span><span class="sxs-lookup"><span data-stu-id="ae3f3-150">-Force</span></span>

<span data-ttu-id="ae3f3-151">Tvingar `Save-Module` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ae3f3-152">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ae3f3-152">-InputObject</span></span>

<span data-ttu-id="ae3f3-153">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="ae3f3-154">Till exempel, utdata `Find-Module` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ae3f3-155">-LiteralPath</span></span>

<span data-ttu-id="ae3f3-156">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ae3f3-157">Värdet för parametern **LiteralPath** används precis som det anges.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="ae3f3-158">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ae3f3-159">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="ae3f3-160">PowerShell tolkar inte tecken som omges av enkla citat tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-161">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ae3f3-161">-MaximumVersion</span></span>

<span data-ttu-id="ae3f3-162">Anger den maximala eller nyaste versionen av modulen som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="ae3f3-163">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-164">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ae3f3-164">-MinimumVersion</span></span>

<span data-ttu-id="ae3f3-165">Anger den lägsta version av en enskild modul som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="ae3f3-166">Du kan inte lägga till den här parametern om du försöker installera flera moduler.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="ae3f3-167">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-168">-Name</span><span class="sxs-lookup"><span data-stu-id="ae3f3-168">-Name</span></span>

<span data-ttu-id="ae3f3-169">Anger en matris med namn på moduler som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-169">Specifies an array of names of modules to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-170">-Path</span><span class="sxs-lookup"><span data-stu-id="ae3f3-170">-Path</span></span>

<span data-ttu-id="ae3f3-171">Anger platsen på den lokala datorn där en sparad modul ska lagras.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="ae3f3-172">Accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-172">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ae3f3-173">-Proxy</span><span class="sxs-lookup"><span data-stu-id="ae3f3-173">-Proxy</span></span>

<span data-ttu-id="ae3f3-174">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="ae3f3-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ae3f3-175">-ProxyCredential</span></span>

<span data-ttu-id="ae3f3-176">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="ae3f3-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="ae3f3-177">– Databas</span><span class="sxs-lookup"><span data-stu-id="ae3f3-177">-Repository</span></span>

<span data-ttu-id="ae3f3-178">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="ae3f3-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="ae3f3-179">Används `Get-PSRepository` för att visa registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-179">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-180">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ae3f3-180">-RequiredVersion</span></span>

<span data-ttu-id="ae3f3-181">Anger det exakta versions numret för den modul som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-181">Specifies the exact version number of the module to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae3f3-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ae3f3-182">-WhatIf</span></span>

<span data-ttu-id="ae3f3-183">Visar vad som händer om `Save-Module` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="ae3f3-184">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ae3f3-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ae3f3-185">CommonParameters</span></span>

<span data-ttu-id="ae3f3-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ae3f3-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ae3f3-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ae3f3-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="ae3f3-188">INPUTS</span></span>

### <span data-ttu-id="ae3f3-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ae3f3-189">System.String[]</span></span>

### <span data-ttu-id="ae3f3-190">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="ae3f3-190">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="ae3f3-191">System. String</span><span class="sxs-lookup"><span data-stu-id="ae3f3-191">System.String</span></span>

### <span data-ttu-id="ae3f3-192">System. URI</span><span class="sxs-lookup"><span data-stu-id="ae3f3-192">System.Uri</span></span>

### <span data-ttu-id="ae3f3-193">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="ae3f3-193">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="ae3f3-194">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ae3f3-194">OUTPUTS</span></span>

### <span data-ttu-id="ae3f3-195">System. Object</span><span class="sxs-lookup"><span data-stu-id="ae3f3-195">System.Object</span></span>

## <span data-ttu-id="ae3f3-196">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ae3f3-196">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae3f3-197">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-197">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="ae3f3-198">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-198">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="ae3f3-199">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="ae3f3-199">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="ae3f3-200">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="ae3f3-200">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="ae3f3-201">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ae3f3-201">RELATED LINKS</span></span>
