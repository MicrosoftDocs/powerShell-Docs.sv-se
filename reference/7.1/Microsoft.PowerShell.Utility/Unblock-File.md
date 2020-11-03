---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: ebe3a882cc6eaf9747a31532d858608b8ad2969c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266433"
---
# <span data-ttu-id="52f6e-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="52f6e-103">Unblock-File</span></span>

## <span data-ttu-id="52f6e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="52f6e-104">SYNOPSIS</span></span>
<span data-ttu-id="52f6e-105">Avblockerar filer som har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="52f6e-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="52f6e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52f6e-106">SYNTAX</span></span>

### <span data-ttu-id="52f6e-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="52f6e-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="52f6e-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="52f6e-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="52f6e-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="52f6e-109">DESCRIPTION</span></span>

<span data-ttu-id="52f6e-110">Med cmdleten **upplåsningskod-File** kan du öppna filer som har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="52f6e-110">The **Unblock-File** cmdlet lets you open files that were downloaded from the Internet.</span></span>
<span data-ttu-id="52f6e-111">Den blockerar PowerShell-skriptfiler som hämtades från Internet så att du kan köra dem, även när PowerShell-körnings principen är **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="52f6e-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned**.</span></span>
<span data-ttu-id="52f6e-112">Som standard blockeras de här filerna för att skydda datorn från ej betrodda filer.</span><span class="sxs-lookup"><span data-stu-id="52f6e-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="52f6e-113">Innan du använder **Avblocks-File-** cmdleten granskar du filen och dess källa och kontrollerar att den är säker att öppna.</span><span class="sxs-lookup"><span data-stu-id="52f6e-113">Before using the **Unblock-File** cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="52f6e-114">Internt tar **Avblocks fil-** cmdleten bort zonen. identifierare, alternativ data ström som har värdet "3" för att indikera att den har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="52f6e-114">Internally, the **Unblock-File** cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="52f6e-115">Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="52f6e-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="52f6e-116">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="52f6e-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="52f6e-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52f6e-117">EXAMPLES</span></span>

### <span data-ttu-id="52f6e-118">Exempel 1: avblockera en fil</span><span class="sxs-lookup"><span data-stu-id="52f6e-118">Example 1: Unblock a file</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

<span data-ttu-id="52f6e-119">Det här kommandot avblockerar filen PowerShellTips. chm.</span><span class="sxs-lookup"><span data-stu-id="52f6e-119">This command unblocks the PowerShellTips.chm file.</span></span>

### <span data-ttu-id="52f6e-120">Exempel 2: avblockera flera filer</span><span class="sxs-lookup"><span data-stu-id="52f6e-120">Example 2: Unblock multiple files</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

<span data-ttu-id="52f6e-121">Detta kommando avblockerar alla filer i C:\Downloads-katalogen vars namn innehåller "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="52f6e-121">This command unblocks all of the files in the C:\Downloads directory whose names include "PowerShell".</span></span>
<span data-ttu-id="52f6e-122">Kör inte något kommando som det här förrän du har kontrollerat att alla filer är säkra.</span><span class="sxs-lookup"><span data-stu-id="52f6e-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

### <span data-ttu-id="52f6e-123">Exempel 3: Sök och avblockera skript</span><span class="sxs-lookup"><span data-stu-id="52f6e-123">Example 3: Find and unblock scripts</span></span>

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

<span data-ttu-id="52f6e-124">Det här kommandot visar hur du hittar och avblockerar PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="52f6e-124">This command shows how to find and unblock PowerShell scripts.</span></span>

## <span data-ttu-id="52f6e-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="52f6e-125">PARAMETERS</span></span>

### <span data-ttu-id="52f6e-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="52f6e-126">-LiteralPath</span></span>
<span data-ttu-id="52f6e-127">Anger de filer som ska avblockeras.</span><span class="sxs-lookup"><span data-stu-id="52f6e-127">Specifies the files to unblock.</span></span>
<span data-ttu-id="52f6e-128">Till skillnad från *sökväg* används värdet för parametern *LiteralPath* exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="52f6e-128">Unlike *Path* , the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="52f6e-129">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="52f6e-129">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="52f6e-130">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="52f6e-130">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="52f6e-131">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="52f6e-131">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="52f6e-132">-Path</span><span class="sxs-lookup"><span data-stu-id="52f6e-132">-Path</span></span>
<span data-ttu-id="52f6e-133">Anger de filer som ska avblockeras.</span><span class="sxs-lookup"><span data-stu-id="52f6e-133">Specifies the files to unblock.</span></span>
<span data-ttu-id="52f6e-134">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="52f6e-134">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="52f6e-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="52f6e-135">-Confirm</span></span>

<span data-ttu-id="52f6e-136">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52f6e-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="52f6e-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="52f6e-137">-WhatIf</span></span>

<span data-ttu-id="52f6e-138">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="52f6e-138">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="52f6e-139">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="52f6e-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="52f6e-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52f6e-140">CommonParameters</span></span>

<span data-ttu-id="52f6e-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52f6e-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52f6e-142">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="52f6e-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52f6e-143">INDATA</span><span class="sxs-lookup"><span data-stu-id="52f6e-143">INPUTS</span></span>

### <span data-ttu-id="52f6e-144">System. String</span><span class="sxs-lookup"><span data-stu-id="52f6e-144">System.String</span></span>

<span data-ttu-id="52f6e-145">Du kan skicka en fil Sök väg till **unblock-File**.</span><span class="sxs-lookup"><span data-stu-id="52f6e-145">You can pipe a file path to **Unblock-File**.</span></span>

## <span data-ttu-id="52f6e-146">UTDATA</span><span class="sxs-lookup"><span data-stu-id="52f6e-146">OUTPUTS</span></span>

### <span data-ttu-id="52f6e-147">Inget</span><span class="sxs-lookup"><span data-stu-id="52f6e-147">None</span></span>

<span data-ttu-id="52f6e-148">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="52f6e-148">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="52f6e-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="52f6e-149">NOTES</span></span>

- <span data-ttu-id="52f6e-150">Stöd för macOS lades till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="52f6e-150">Support for macOS was added in PowerShell 7.</span></span>
- <span data-ttu-id="52f6e-151">`Unblock-File`Cmdleten fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="52f6e-151">The `Unblock-File` cmdlet works only in file system drives.</span></span>
- <span data-ttu-id="52f6e-152">`Unblock-File` utför samma åtgärd som knappen **Häv blockering** i dialog rutan **Egenskaper** i Utforskaren i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="52f6e-152">`Unblock-File` performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
- <span data-ttu-id="52f6e-153">Om du använder `Unblock-File` cmdleten på en fil som inte är blockerad har kommandot ingen påverkan på den ej blockerade filen och cmdleten genererar inga fel.</span><span class="sxs-lookup"><span data-stu-id="52f6e-153">If you use the `Unblock-File` cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="52f6e-154">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="52f6e-154">RELATED LINKS</span></span>

[<span data-ttu-id="52f6e-155">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="52f6e-155">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="52f6e-156">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="52f6e-156">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="52f6e-157">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="52f6e-157">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="52f6e-158">FileSystem-Provider</span><span class="sxs-lookup"><span data-stu-id="52f6e-158">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)

