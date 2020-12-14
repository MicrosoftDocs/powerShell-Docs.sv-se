---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: df5056b4402664602409388825c8b2b8acd4e02f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891893"
---
# <span data-ttu-id="102b7-102">Save-Module</span><span class="sxs-lookup"><span data-stu-id="102b7-102">Save-Module</span></span>

## <span data-ttu-id="102b7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="102b7-103">SYNOPSIS</span></span>
<span data-ttu-id="102b7-104">Sparar en modul och dess beroenden på den lokala datorn, men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="102b7-104">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="102b7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="102b7-105">SYNTAX</span></span>

### <span data-ttu-id="102b7-106">NameAndPathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="102b7-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="102b7-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="102b7-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="102b7-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="102b7-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="102b7-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="102b7-109">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="102b7-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="102b7-110">DESCRIPTION</span></span>

<span data-ttu-id="102b7-111">`Save-Module`Cmdlet: en laddar ned en modul och eventuella beroenden från en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="102b7-111">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="102b7-112">`Save-Module` hämtar och sparar den mest aktuella versionen av en modul.</span><span class="sxs-lookup"><span data-stu-id="102b7-112">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="102b7-113">Filerna sparas till en angiven sökväg på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="102b7-113">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="102b7-114">Modulen är inte installerad, men innehållet är tillgängligt för granskning av en administratör.</span><span class="sxs-lookup"><span data-stu-id="102b7-114">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="102b7-115">Den sparade modulen kan sedan kopieras till den aktuella `$env:PSModulePath` platsen för den frånkopplade datorn.</span><span class="sxs-lookup"><span data-stu-id="102b7-115">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="102b7-116">`Get-PSRepository` visar den lokala datorns registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="102b7-116">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="102b7-117">Du kan använda `Find-Module` cmdleten för att söka i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="102b7-117">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="102b7-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="102b7-118">EXAMPLES</span></span>

### <span data-ttu-id="102b7-119">Exempel 1: Spara en modul</span><span class="sxs-lookup"><span data-stu-id="102b7-119">Example 1: Save a module</span></span>

<span data-ttu-id="102b7-120">I det här exemplet sparas en modul och dess beroenden på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="102b7-120">In this example, a module and its dependencies are saved to the local computer.</span></span>

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

<span data-ttu-id="102b7-121">`Save-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="102b7-121">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="102b7-122">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="102b7-122">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="102b7-123">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="102b7-123">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="102b7-124">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="102b7-124">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="102b7-125">Exempel 2: Spara en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="102b7-125">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="102b7-126">Det här exemplet visar hur du använder en parameter, till exempel **MaximumVersion** eller **RequiredVersion** för att ange en version av en modul.</span><span class="sxs-lookup"><span data-stu-id="102b7-126">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

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

<span data-ttu-id="102b7-127">`Save-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="102b7-127">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="102b7-128">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="102b7-128">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="102b7-129">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="102b7-129">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="102b7-130">**MaximumVersion** anger att version **2.1.0** har laddats ned och sparats.</span><span class="sxs-lookup"><span data-stu-id="102b7-130">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="102b7-131">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="102b7-131">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="102b7-132">Exempel 3: söka efter och spara en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="102b7-132">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="102b7-133">I det här exemplet finns en nödvändig modul version i lagrings platsen och sparas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="102b7-133">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

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

<span data-ttu-id="102b7-134">`Find-Module` använder parametern **Name** för att ange modulen **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="102b7-134">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="102b7-135">Parametern för **lagrings platsen** anger en registrerad lagrings plats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="102b7-135">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="102b7-136">**RequiredVersion** anger version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="102b7-136">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="102b7-137">Objektet skickas ned pipelinen till `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="102b7-137">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="102b7-138">Parametern **Path** anger var du vill lagra den nedladdade modulen.</span><span class="sxs-lookup"><span data-stu-id="102b7-138">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="102b7-139">När hämtningen är färdig `Get-ChildItem` visas innehållet i **sökvägen** där filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="102b7-139">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="102b7-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="102b7-140">PARAMETERS</span></span>

### <span data-ttu-id="102b7-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="102b7-141">-AcceptLicense</span></span>

<span data-ttu-id="102b7-142">Godkänn licens avtalet automatiskt om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="102b7-142">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="102b7-143">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="102b7-143">-AllowPrerelease</span></span>

<span data-ttu-id="102b7-144">Gör att du kan spara en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="102b7-144">Allows you to save a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="102b7-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="102b7-145">-Confirm</span></span>

<span data-ttu-id="102b7-146">Du uppmanas att bekräfta innan du kör `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="102b7-146">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="102b7-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="102b7-147">-Credential</span></span>

<span data-ttu-id="102b7-148">Anger ett användar konto som har behörighet att spara en modul.</span><span class="sxs-lookup"><span data-stu-id="102b7-148">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="102b7-149">-Force</span><span class="sxs-lookup"><span data-stu-id="102b7-149">-Force</span></span>

<span data-ttu-id="102b7-150">Tvingar `Save-Module` körning utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="102b7-150">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="102b7-151">– InputObject</span><span class="sxs-lookup"><span data-stu-id="102b7-151">-InputObject</span></span>

<span data-ttu-id="102b7-152">Accepterar ett **PSRepositoryItemInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="102b7-152">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="102b7-153">Till exempel, utdata `Find-Module` till en variabel och Använd variabeln som **InputObject** -argument.</span><span class="sxs-lookup"><span data-stu-id="102b7-153">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="102b7-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="102b7-154">-LiteralPath</span></span>

<span data-ttu-id="102b7-155">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="102b7-155">Specifies a path to one or more locations.</span></span> <span data-ttu-id="102b7-156">Värdet för parametern **LiteralPath** används precis som det anges.</span><span class="sxs-lookup"><span data-stu-id="102b7-156">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="102b7-157">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="102b7-157">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="102b7-158">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="102b7-158">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="102b7-159">PowerShell tolkar inte tecken som omges av enkla citat tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="102b7-159">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="102b7-160">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="102b7-160">-MaximumVersion</span></span>

<span data-ttu-id="102b7-161">Anger den maximala eller nyaste versionen av modulen som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="102b7-161">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="102b7-162">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="102b7-162">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="102b7-163">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="102b7-163">-MinimumVersion</span></span>

<span data-ttu-id="102b7-164">Anger den lägsta version av en enskild modul som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="102b7-164">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="102b7-165">Du kan inte lägga till den här parametern om du försöker installera flera moduler.</span><span class="sxs-lookup"><span data-stu-id="102b7-165">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="102b7-166">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="102b7-166">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="102b7-167">-Name</span><span class="sxs-lookup"><span data-stu-id="102b7-167">-Name</span></span>

<span data-ttu-id="102b7-168">Anger en matris med namn på moduler som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="102b7-168">Specifies an array of names of modules to save.</span></span>

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

### <span data-ttu-id="102b7-169">-Path</span><span class="sxs-lookup"><span data-stu-id="102b7-169">-Path</span></span>

<span data-ttu-id="102b7-170">Anger platsen på den lokala datorn där en sparad modul ska lagras.</span><span class="sxs-lookup"><span data-stu-id="102b7-170">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="102b7-171">Accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="102b7-171">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="102b7-172">-Proxy</span><span class="sxs-lookup"><span data-stu-id="102b7-172">-Proxy</span></span>

<span data-ttu-id="102b7-173">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="102b7-173">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="102b7-174">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="102b7-174">-ProxyCredential</span></span>

<span data-ttu-id="102b7-175">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="102b7-175">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="102b7-176">– Databas</span><span class="sxs-lookup"><span data-stu-id="102b7-176">-Repository</span></span>

<span data-ttu-id="102b7-177">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="102b7-177">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="102b7-178">Används `Get-PSRepository` för att visa registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="102b7-178">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="102b7-179">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="102b7-179">-RequiredVersion</span></span>

<span data-ttu-id="102b7-180">Anger det exakta versions numret för den modul som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="102b7-180">Specifies the exact version number of the module to save.</span></span>

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

### <span data-ttu-id="102b7-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="102b7-181">-WhatIf</span></span>

<span data-ttu-id="102b7-182">Visar vad som händer om `Save-Module` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="102b7-182">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="102b7-183">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="102b7-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="102b7-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="102b7-184">CommonParameters</span></span>

<span data-ttu-id="102b7-185">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="102b7-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="102b7-186">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="102b7-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="102b7-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="102b7-187">INPUTS</span></span>

### <span data-ttu-id="102b7-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="102b7-188">System.String[]</span></span>

### <span data-ttu-id="102b7-189">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="102b7-189">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="102b7-190">System. String</span><span class="sxs-lookup"><span data-stu-id="102b7-190">System.String</span></span>

### <span data-ttu-id="102b7-191">System. URI</span><span class="sxs-lookup"><span data-stu-id="102b7-191">System.Uri</span></span>

### <span data-ttu-id="102b7-192">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="102b7-192">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="102b7-193">UTDATA</span><span class="sxs-lookup"><span data-stu-id="102b7-193">OUTPUTS</span></span>

### <span data-ttu-id="102b7-194">System. Object</span><span class="sxs-lookup"><span data-stu-id="102b7-194">System.Object</span></span>

## <span data-ttu-id="102b7-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="102b7-195">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="102b7-196">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="102b7-196">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="102b7-197">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="102b7-197">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="102b7-198">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="102b7-198">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="102b7-199">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="102b7-199">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="102b7-200">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="102b7-200">RELATED LINKS</span></span>
