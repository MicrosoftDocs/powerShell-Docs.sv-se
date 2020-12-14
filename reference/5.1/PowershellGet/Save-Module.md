---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: e058bff552b4460d068909f8bf4ab31b976ef978
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889733"
---
# <span data-ttu-id="48dc8-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="48dc8-103">Save-Module</span></span>

## <span data-ttu-id="48dc8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="48dc8-104">SYNOPSIS</span></span>
<span data-ttu-id="48dc8-105">Sparar en modul och dess beroenden på den lokala datorn, men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="48dc8-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="48dc8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="48dc8-106">SYNTAX</span></span>

### <span data-ttu-id="48dc8-107">NameAndPathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="48dc8-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense]  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="48dc8-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="48dc8-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense]  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="48dc8-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="48dc8-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="48dc8-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="48dc8-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="48dc8-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="48dc8-111">DESCRIPTION</span></span>

<span data-ttu-id="48dc8-112">`Save-Module`Cmdlet: en laddar ned en modul och eventuella beroenden från en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="48dc8-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="48dc8-113">`Save-Module` hämtar och sparar den mest aktuella versionen av en modul.</span><span class="sxs-lookup"><span data-stu-id="48dc8-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="48dc8-114">Filerna sparas till en angiven sökväg på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="48dc8-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="48dc8-115">Modulen är inte installerad, men innehållet är tillgängligt för granskning av en administratör.</span><span class="sxs-lookup"><span data-stu-id="48dc8-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="48dc8-116">Den sparade modulen kan sedan kopieras till den aktuella `$env:PSModulePath` platsen för den frånkopplade datorn.</span><span class="sxs-lookup"><span data-stu-id="48dc8-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="48dc8-117">`Get-PSRepository` visar den lokala datorns registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="48dc8-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="48dc8-118">Du kan använda `Find-Module` cmdleten för att söka i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="48dc8-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="48dc8-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="48dc8-119">EXAMPLES</span></span>

### <span data-ttu-id="48dc8-120">Exempel 1: Spara en modul</span><span class="sxs-lookup"><span data-stu-id="48dc8-120">Example 1: Save a module</span></span>

<span data-ttu-id="48dc8-121">I det här exemplet sparas en modul och dess beroenden på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="48dc8-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

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

<span data-ttu-id="48dc8-122">`Save-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="48dc8-123">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="48dc8-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="48dc8-124">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-124">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="48dc8-125">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="48dc8-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="48dc8-126">Exempel 2: Spara en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="48dc8-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="48dc8-127">Det här exemplet visar hur du använder en parameter, till exempel **MaximumVersion** eller **RequiredVersion** för att ange en version av en modul.</span><span class="sxs-lookup"><span data-stu-id="48dc8-127">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

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

<span data-ttu-id="48dc8-128">`Save-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="48dc8-129">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="48dc8-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="48dc8-130">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-130">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="48dc8-131">**MaximumVersion** anger att version **2.1.0** har laddats ned och sparats.</span><span class="sxs-lookup"><span data-stu-id="48dc8-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="48dc8-132">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="48dc8-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="48dc8-133">Exempel 3: söka efter och spara en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="48dc8-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="48dc8-134">I det här exemplet finns en nödvändig modul version i lagrings platsen och sparas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="48dc8-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

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

<span data-ttu-id="48dc8-135">`Find-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="48dc8-136">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-136">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="48dc8-137">**RequiredVersion** anger version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="48dc8-137">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="48dc8-138">Objektet skickas ned pipelinen till `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="48dc8-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="48dc8-139">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="48dc8-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="48dc8-140">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="48dc8-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="48dc8-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="48dc8-141">PARAMETERS</span></span>

### <span data-ttu-id="48dc8-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="48dc8-142">-AcceptLicense</span></span>

<span data-ttu-id="48dc8-143">Godkänn licens avtalet automatiskt om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="48dc8-143">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="48dc8-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="48dc8-144">-AllowPrerelease</span></span>

<span data-ttu-id="48dc8-145">Gör att du kan spara en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="48dc8-145">Allows you to save a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="48dc8-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="48dc8-146">-Confirm</span></span>

<span data-ttu-id="48dc8-147">Du uppmanas att bekräfta innan du kör `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="48dc8-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="48dc8-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="48dc8-148">-Credential</span></span>

<span data-ttu-id="48dc8-149">Anger ett användar konto som har behörighet att spara en modul.</span><span class="sxs-lookup"><span data-stu-id="48dc8-149">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="48dc8-150">-Force</span><span class="sxs-lookup"><span data-stu-id="48dc8-150">-Force</span></span>

<span data-ttu-id="48dc8-151">Tvingar `Save-Module` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="48dc8-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="48dc8-152">– InputObject</span><span class="sxs-lookup"><span data-stu-id="48dc8-152">-InputObject</span></span>

<span data-ttu-id="48dc8-153">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="48dc8-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="48dc8-154">Till exempel, utdata `Find-Module` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="48dc8-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="48dc8-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="48dc8-155">-LiteralPath</span></span>

<span data-ttu-id="48dc8-156">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="48dc8-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="48dc8-157">Värdet för parametern **LiteralPath** används precis som det anges.</span><span class="sxs-lookup"><span data-stu-id="48dc8-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="48dc8-158">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="48dc8-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="48dc8-159">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="48dc8-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="48dc8-160">PowerShell tolkar inte tecken som omges av enkla citat tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="48dc8-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="48dc8-161">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="48dc8-161">-MaximumVersion</span></span>

<span data-ttu-id="48dc8-162">Anger den maximala eller nyaste versionen av modulen som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="48dc8-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="48dc8-163">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="48dc8-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="48dc8-164">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="48dc8-164">-MinimumVersion</span></span>

<span data-ttu-id="48dc8-165">Anger den lägsta version av en enskild modul som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="48dc8-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="48dc8-166">Du kan inte lägga till den här parametern om du försöker installera flera moduler.</span><span class="sxs-lookup"><span data-stu-id="48dc8-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="48dc8-167">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="48dc8-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="48dc8-168">-Name</span><span class="sxs-lookup"><span data-stu-id="48dc8-168">-Name</span></span>

<span data-ttu-id="48dc8-169">Anger en matris med namn på moduler som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="48dc8-169">Specifies an array of names of modules to save.</span></span>

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

### <span data-ttu-id="48dc8-170">-Path</span><span class="sxs-lookup"><span data-stu-id="48dc8-170">-Path</span></span>

<span data-ttu-id="48dc8-171">Anger platsen på den lokala datorn där en sparad modul ska lagras.</span><span class="sxs-lookup"><span data-stu-id="48dc8-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="48dc8-172">Accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="48dc8-172">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="48dc8-173">-Proxy</span><span class="sxs-lookup"><span data-stu-id="48dc8-173">-Proxy</span></span>

<span data-ttu-id="48dc8-174">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="48dc8-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="48dc8-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="48dc8-175">-ProxyCredential</span></span>

<span data-ttu-id="48dc8-176">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="48dc8-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="48dc8-177">– Databas</span><span class="sxs-lookup"><span data-stu-id="48dc8-177">-Repository</span></span>

<span data-ttu-id="48dc8-178">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="48dc8-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="48dc8-179">Används `Get-PSRepository` för att visa registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="48dc8-179">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="48dc8-180">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="48dc8-180">-RequiredVersion</span></span>

<span data-ttu-id="48dc8-181">Anger det exakta versions numret för den modul som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="48dc8-181">Specifies the exact version number of the module to save.</span></span>

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

### <span data-ttu-id="48dc8-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="48dc8-182">-WhatIf</span></span>

<span data-ttu-id="48dc8-183">Visar vad som händer om `Save-Module` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="48dc8-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="48dc8-184">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="48dc8-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="48dc8-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48dc8-185">CommonParameters</span></span>

<span data-ttu-id="48dc8-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48dc8-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48dc8-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="48dc8-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48dc8-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="48dc8-188">INPUTS</span></span>

## <span data-ttu-id="48dc8-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="48dc8-189">OUTPUTS</span></span>

## <span data-ttu-id="48dc8-190">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="48dc8-190">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48dc8-191">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="48dc8-191">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="48dc8-192">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="48dc8-192">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="48dc8-193">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="48dc8-193">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="48dc8-194">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="48dc8-194">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="48dc8-195">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="48dc8-195">RELATED LINKS</span></span>
