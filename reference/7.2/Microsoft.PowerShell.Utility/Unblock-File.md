---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 8bbfe761a71b38b541f23730d84eb0023a059318
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709703"
---
# <span data-ttu-id="1f9a7-102">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="1f9a7-102">Unblock-File</span></span>

## <span data-ttu-id="1f9a7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1f9a7-103">SYNOPSIS</span></span>
<span data-ttu-id="1f9a7-104">Avblockerar filer som har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-104">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="1f9a7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1f9a7-105">SYNTAX</span></span>

### <span data-ttu-id="1f9a7-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="1f9a7-106">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1f9a7-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1f9a7-107">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1f9a7-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1f9a7-108">DESCRIPTION</span></span>

<span data-ttu-id="1f9a7-109">Med `Unblock-File` cmdleten kan du öppna filer som har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-109">The `Unblock-File` cmdlet lets you open files that were downloaded from the Internet.</span></span> <span data-ttu-id="1f9a7-110">Den blockerar PowerShell-skriptfiler som hämtades från Internet så att du kan köra dem, även när PowerShell-körnings principen är **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-110">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="1f9a7-111">Som standard blockeras de här filerna för att skydda datorn från ej betrodda filer.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-111">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="1f9a7-112">Innan du använder `Unblock-File` cmdleten granskar du filen och dess källa och kontrollerar att den är säker att öppna.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-112">Before using the `Unblock-File` cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="1f9a7-113">Internt `Unblock-File` tar cmdleten bort zonen. identifierare, alternativ data ström som har värdet "3" för att indikera att den har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-113">Internally, the `Unblock-File` cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="1f9a7-114">Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="1f9a7-114">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="1f9a7-115">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-115">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="1f9a7-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1f9a7-116">EXAMPLES</span></span>

### <span data-ttu-id="1f9a7-117">Exempel 1: avblockera en fil</span><span class="sxs-lookup"><span data-stu-id="1f9a7-117">Example 1: Unblock a file</span></span>

<span data-ttu-id="1f9a7-118">Det här kommandot avblockerar filen PowerShellTips. chm.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-118">This command unblocks the PowerShellTips.chm file.</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### <span data-ttu-id="1f9a7-119">Exempel 2: avblockera flera filer</span><span class="sxs-lookup"><span data-stu-id="1f9a7-119">Example 2: Unblock multiple files</span></span>

<span data-ttu-id="1f9a7-120">Detta kommando avblockerar alla filer i `C:\Downloads` katalogen med namn som innehåller "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="1f9a7-120">This command unblocks all of the files in the `C:\Downloads` directory whose names include "PowerShell".</span></span> <span data-ttu-id="1f9a7-121">Kör inte något kommando som det här förrän du har kontrollerat att alla filer är säkra.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-121">Do not run a command like this one until you have verified that all files are safe.</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### <span data-ttu-id="1f9a7-122">Exempel 3: Sök och avblockera skript</span><span class="sxs-lookup"><span data-stu-id="1f9a7-122">Example 3: Find and unblock scripts</span></span>

<span data-ttu-id="1f9a7-123">Det här kommandot visar hur du hittar och avblockerar PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-123">This command shows how to find and unblock PowerShell scripts.</span></span>

<span data-ttu-id="1f9a7-124">Det första kommandot använder **Stream** -parametern för cmdleten *Get-item* för att hämta filer med zonen. identifierarens data ström.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-124">The first command uses the **Stream** parameter of the *Get-Item* cmdlet get files with the Zone.Identifier stream.</span></span>

<span data-ttu-id="1f9a7-125">Det andra kommandot visar vad som händer när du kör ett blockerat skript i en PowerShell-session där körnings principen är **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-125">The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="1f9a7-126">RemoteSigned-principen förhindrar att du kör skript som har hämtats från Internet om de inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-126">The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.</span></span>

<span data-ttu-id="1f9a7-127">Det tredje kommandot använder `Unblock-File` cmdleten för att avblockera skriptet så att det kan köras i sessionen.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-127">The third command uses the `Unblock-File` cmdlet to unblock the script so it can run in the session.</span></span>

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## <span data-ttu-id="1f9a7-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1f9a7-128">PARAMETERS</span></span>

### <span data-ttu-id="1f9a7-129">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1f9a7-129">-LiteralPath</span></span>

<span data-ttu-id="1f9a7-130">Anger de filer som ska avblockeras.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-130">Specifies the files to unblock.</span></span> <span data-ttu-id="1f9a7-131">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-131">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="1f9a7-132">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-132">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1f9a7-133">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-133">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1f9a7-134">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-134">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f9a7-135">-Path</span><span class="sxs-lookup"><span data-stu-id="1f9a7-135">-Path</span></span>

<span data-ttu-id="1f9a7-136">Anger de filer som ska avblockeras.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-136">Specifies the files to unblock.</span></span> <span data-ttu-id="1f9a7-137">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-137">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1f9a7-138">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1f9a7-138">-Confirm</span></span>

<span data-ttu-id="1f9a7-139">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-139">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1f9a7-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1f9a7-140">-WhatIf</span></span>

<span data-ttu-id="1f9a7-141">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-141">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1f9a7-142">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-142">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1f9a7-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1f9a7-143">CommonParameters</span></span>

<span data-ttu-id="1f9a7-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1f9a7-145">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1f9a7-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1f9a7-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="1f9a7-146">INPUTS</span></span>

### <span data-ttu-id="1f9a7-147">System. String</span><span class="sxs-lookup"><span data-stu-id="1f9a7-147">System.String</span></span>

<span data-ttu-id="1f9a7-148">Du kan skicka en fil Sök väg till `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="1f9a7-148">You can pipe a file path to `Unblock-File`.</span></span>

## <span data-ttu-id="1f9a7-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1f9a7-149">OUTPUTS</span></span>

### <span data-ttu-id="1f9a7-150">Inga</span><span class="sxs-lookup"><span data-stu-id="1f9a7-150">None</span></span>

<span data-ttu-id="1f9a7-151">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-151">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1f9a7-152">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1f9a7-152">NOTES</span></span>

- <span data-ttu-id="1f9a7-153">Stöd för macOS lades till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-153">Support for macOS was added in PowerShell 7.</span></span>
- <span data-ttu-id="1f9a7-154">`Unblock-File`Cmdleten fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-154">The `Unblock-File` cmdlet works only in file system drives.</span></span>
- <span data-ttu-id="1f9a7-155">`Unblock-File` utför samma åtgärd som knappen **Häv blockering** i dialog rutan **Egenskaper** i Utforskaren i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-155">`Unblock-File` performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
- <span data-ttu-id="1f9a7-156">Om du använder `Unblock-File` cmdleten på en fil som inte är blockerad har kommandot ingen påverkan på den ej blockerade filen och cmdleten genererar inga fel.</span><span class="sxs-lookup"><span data-stu-id="1f9a7-156">If you use the `Unblock-File` cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="1f9a7-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1f9a7-157">RELATED LINKS</span></span>

[<span data-ttu-id="1f9a7-158">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="1f9a7-158">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="1f9a7-159">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="1f9a7-159">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="1f9a7-160">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="1f9a7-160">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="1f9a7-161">FileSystem-Provider</span><span class="sxs-lookup"><span data-stu-id="1f9a7-161">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
