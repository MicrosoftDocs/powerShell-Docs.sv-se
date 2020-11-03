---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265418"
---
# <span data-ttu-id="91a50-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="91a50-103">Set-Clipboard</span></span>

## <span data-ttu-id="91a50-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="91a50-104">SYNOPSIS</span></span>
<span data-ttu-id="91a50-105">Anger det aktuella urklipps posten i Windows.</span><span class="sxs-lookup"><span data-stu-id="91a50-105">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="91a50-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="91a50-106">SYNTAX</span></span>

### <span data-ttu-id="91a50-107">Sträng (standard)</span><span class="sxs-lookup"><span data-stu-id="91a50-107">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="91a50-108">Värde</span><span class="sxs-lookup"><span data-stu-id="91a50-108">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="91a50-109">Sökväg</span><span class="sxs-lookup"><span data-stu-id="91a50-109">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="91a50-110">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="91a50-110">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="91a50-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="91a50-111">DESCRIPTION</span></span>

<span data-ttu-id="91a50-112">`Set-Clipboard`Cmdleten anger det aktuella urklipps posten i Windows.</span><span class="sxs-lookup"><span data-stu-id="91a50-112">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="91a50-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="91a50-113">EXAMPLES</span></span>

### <span data-ttu-id="91a50-114">Exempel 1: kopiera text till Urklipp</span><span class="sxs-lookup"><span data-stu-id="91a50-114">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="91a50-115">Exempel 2: kopiera innehållet i en katalog till Urklipp</span><span class="sxs-lookup"><span data-stu-id="91a50-115">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="91a50-116">Det här kommandot kopierar innehållet i den angivna mappen till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="91a50-116">This command copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## <span data-ttu-id="91a50-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="91a50-117">PARAMETERS</span></span>

### <span data-ttu-id="91a50-118">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="91a50-118">-Append</span></span>

<span data-ttu-id="91a50-119">Anger att cmdleten inte rensar Urklipp och lägger till innehåll i den.</span><span class="sxs-lookup"><span data-stu-id="91a50-119">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="91a50-120">-HTML</span><span class="sxs-lookup"><span data-stu-id="91a50-120">-AsHtml</span></span>

<span data-ttu-id="91a50-121">Anger att cmdleten återger innehållet som HTML i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="91a50-121">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="91a50-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="91a50-122">-LiteralPath</span></span>

<span data-ttu-id="91a50-123">Anger sökvägen till det objekt som kopieras till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="91a50-123">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="91a50-124">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="91a50-124">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="91a50-125">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="91a50-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="91a50-126">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="91a50-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="91a50-127">Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="91a50-127">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91a50-128">-Path</span><span class="sxs-lookup"><span data-stu-id="91a50-128">-Path</span></span>

<span data-ttu-id="91a50-129">Anger sökvägen till det objekt som kopieras till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="91a50-129">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="91a50-130">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="91a50-130">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="91a50-131">-Värde</span><span class="sxs-lookup"><span data-stu-id="91a50-131">-Value</span></span>

<span data-ttu-id="91a50-132">Anger, som en sträng mat ris, det innehåll som ska kopieras till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="91a50-132">Specifies, as a string array, the content to copy to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="91a50-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="91a50-133">-Confirm</span></span>

<span data-ttu-id="91a50-134">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="91a50-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="91a50-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="91a50-135">-WhatIf</span></span>

<span data-ttu-id="91a50-136">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="91a50-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="91a50-137">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="91a50-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="91a50-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="91a50-138">CommonParameters</span></span>

<span data-ttu-id="91a50-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="91a50-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="91a50-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="91a50-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="91a50-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="91a50-141">INPUTS</span></span>

### <span data-ttu-id="91a50-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="91a50-142">System.String[]</span></span>

## <span data-ttu-id="91a50-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="91a50-143">OUTPUTS</span></span>

## <span data-ttu-id="91a50-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="91a50-144">NOTES</span></span>

<span data-ttu-id="91a50-145">I sällsynta fall när `Set-Clipboard` du använder med ett stort antal värden i snabb följd, som i en slinga, kan du sporadiskt få ett tomt värde från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="91a50-145">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="91a50-146">Detta kan åtgärdas med hjälp av `Start-Sleep -Milliseconds 1` i slingan.</span><span class="sxs-lookup"><span data-stu-id="91a50-146">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="91a50-147">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="91a50-147">RELATED LINKS</span></span>

[<span data-ttu-id="91a50-148">Hämta Urklipp</span><span class="sxs-lookup"><span data-stu-id="91a50-148">Get-Clipboard</span></span>](Get-Clipboard.md)
