---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 26fc71546c03fbb49bf8824f6779e6b6371daa0e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891149"
---
# <span data-ttu-id="8a721-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="8a721-103">Publish-Script</span></span>

## <span data-ttu-id="8a721-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8a721-104">SYNOPSIS</span></span>
<span data-ttu-id="8a721-105">Publicerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="8a721-105">Publishes a script.</span></span>

## <span data-ttu-id="8a721-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a721-106">SYNTAX</span></span>

### <span data-ttu-id="8a721-107">PathParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="8a721-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8a721-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="8a721-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a721-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8a721-109">DESCRIPTION</span></span>

<span data-ttu-id="8a721-110">`Publish-Script`Cmdleten publicerar det angivna skriptet till onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="8a721-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="8a721-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8a721-111">EXAMPLES</span></span>

### <span data-ttu-id="8a721-112">Exempel 1: skapa en skript fil, Lägg till innehåll i den och publicera den</span><span class="sxs-lookup"><span data-stu-id="8a721-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="8a721-113">`New-ScriptFileInfo`Cmdleten skapar en skript fil med namnet `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="8a721-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="8a721-114">`Get-Content` visar innehållet i `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="8a721-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="8a721-115">`Add-Content`Cmdleten lägger till en funktion och ett arbets flöde i `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="8a721-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

```powershell
$newScriptInfo = @{
  Path = 'D:\ScriptSharingDemo\Demo-Script.ps1'
  Version = '1.0'
  Author = 'author@contoso.com'
  Description = "my test script file description goes here"
}
New-ScriptFileInfo @newScriptInfo
Get-Content -Path $newScriptInfo.Path
```

```Output
<#PSScriptInfo

.VERSION 1.0

.AUTHOR pattif@microsoft.com

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES
#>

<#
.DESCRIPTION
 my test script file description goes here
#>
Param()
```

```powershell
Add-Content -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Value @"

Function Demo-ScriptFunction { 'Demo-ScriptFunction' }

Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }

Demo-ScriptFunction
Demo-ScriptWorkflow
"@
Test-ScriptFileInfo -Path D:\ScriptSharingDemo\Demo-Script.ps1
```

```Output
Version    Name                 Author                   Description
-------    ----                 ------                   -----------
1.0        Demo-Script          author@contoso.com       my test script file description goes here
```

```powershell
Publish-Script -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Repository LocalRepo1
Find-Script -Repository LocalRepo1 -Name "Demo-Script"
```

```Output
Version    Name                 Type       Repository    Description
-------    ----                 ----       ----------    -----------
1.0        Demo-Script          Script     LocalRepo1    my test script file description goes here
```

<span data-ttu-id="8a721-116">`Test-ScriptFileInfo`Cmdleten verifieras `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="8a721-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="8a721-117">`Publish-Script`Cmdleten publicerar skriptet till **LocalRepo1** -lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="8a721-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="8a721-118">Slutligen</span><span class="sxs-lookup"><span data-stu-id="8a721-118">Finally.</span></span> <span data-ttu-id="8a721-119">`Find-Script` används för att söka efter `Demo-Script.ps1` i **LocalRepo1** -lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="8a721-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="8a721-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8a721-120">PARAMETERS</span></span>

### <span data-ttu-id="8a721-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a721-121">-Confirm</span></span>

<span data-ttu-id="8a721-122">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8a721-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a721-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="8a721-123">-Credential</span></span>

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

### <span data-ttu-id="8a721-124">-Force</span><span class="sxs-lookup"><span data-stu-id="8a721-124">-Force</span></span>

<span data-ttu-id="8a721-125">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="8a721-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="8a721-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8a721-126">-LiteralPath</span></span>

<span data-ttu-id="8a721-127">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="8a721-127">Specifies a path to one or more locations.</span></span> <span data-ttu-id="8a721-128">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** precis som det anges.</span><span class="sxs-lookup"><span data-stu-id="8a721-128">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="8a721-129">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8a721-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8a721-130">Om sökvägen innehåller escape-tecken, omger du dem med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="8a721-130">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="8a721-131">Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="8a721-131">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8a721-132">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="8a721-132">-NuGetApiKey</span></span>

<span data-ttu-id="8a721-133">Anger den API-nyckel som du vill använda för att publicera ett skript i onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="8a721-133">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="8a721-134">API-nyckeln är en del av din profil i online-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8a721-134">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="8a721-135">Mer information finns i [Hantera API-nycklar](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span><span class="sxs-lookup"><span data-stu-id="8a721-135">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="8a721-136">-Path</span><span class="sxs-lookup"><span data-stu-id="8a721-136">-Path</span></span>

<span data-ttu-id="8a721-137">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="8a721-137">Specifies a path to one or more locations.</span></span> <span data-ttu-id="8a721-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="8a721-138">Wildcards are permitted.</span></span> <span data-ttu-id="8a721-139">Standard platsen är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="8a721-139">The default location is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: Named
Default value: <Current location>
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8a721-140">– Databas</span><span class="sxs-lookup"><span data-stu-id="8a721-140">-Repository</span></span>

<span data-ttu-id="8a721-141">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="8a721-141">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="8a721-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a721-142">-WhatIf</span></span>

<span data-ttu-id="8a721-143">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="8a721-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8a721-144">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="8a721-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8a721-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a721-145">CommonParameters</span></span>

<span data-ttu-id="8a721-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a721-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a721-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8a721-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a721-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="8a721-148">INPUTS</span></span>

### <span data-ttu-id="8a721-149">System. String</span><span class="sxs-lookup"><span data-stu-id="8a721-149">System.String</span></span>

### <span data-ttu-id="8a721-150">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="8a721-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="8a721-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8a721-151">OUTPUTS</span></span>

### <span data-ttu-id="8a721-152">System. Object</span><span class="sxs-lookup"><span data-stu-id="8a721-152">System.Object</span></span>

## <span data-ttu-id="8a721-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8a721-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a721-154">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="8a721-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="8a721-155">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8a721-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="8a721-156">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="8a721-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="8a721-157">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="8a721-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="8a721-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8a721-158">RELATED LINKS</span></span>

[<span data-ttu-id="8a721-159">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="8a721-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="8a721-160">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="8a721-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="8a721-161">Publicera – skript</span><span class="sxs-lookup"><span data-stu-id="8a721-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="8a721-162">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="8a721-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="8a721-163">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="8a721-163">Update-Script</span></span>](Update-Script.md)
