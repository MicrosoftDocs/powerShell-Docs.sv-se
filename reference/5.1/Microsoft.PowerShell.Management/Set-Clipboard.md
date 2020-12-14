---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: c1cf126e41a5e918afffbc41d30f957e650efdf5
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564511"
---
# <span data-ttu-id="83dae-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="83dae-102">Set-Clipboard</span></span>

## <span data-ttu-id="83dae-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="83dae-103">SYNOPSIS</span></span>
<span data-ttu-id="83dae-104">Anger det aktuella urklipps posten i Windows.</span><span class="sxs-lookup"><span data-stu-id="83dae-104">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="83dae-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="83dae-105">SYNTAX</span></span>

### <span data-ttu-id="83dae-106">Sträng (standard)</span><span class="sxs-lookup"><span data-stu-id="83dae-106">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="83dae-107">Värde</span><span class="sxs-lookup"><span data-stu-id="83dae-107">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="83dae-108">Sökväg</span><span class="sxs-lookup"><span data-stu-id="83dae-108">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="83dae-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="83dae-109">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="83dae-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="83dae-110">DESCRIPTION</span></span>

<span data-ttu-id="83dae-111">`Set-Clipboard`Cmdleten anger det aktuella urklipps posten i Windows.</span><span class="sxs-lookup"><span data-stu-id="83dae-111">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="83dae-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="83dae-112">EXAMPLES</span></span>

### <span data-ttu-id="83dae-113">Exempel 1: kopiera text till Urklipp</span><span class="sxs-lookup"><span data-stu-id="83dae-113">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="83dae-114">Exempel 2: kopiera innehållet i en katalog till Urklipp</span><span class="sxs-lookup"><span data-stu-id="83dae-114">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="83dae-115">I det här exemplet kopieras innehållet i den angivna mappen till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-115">This example copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

### <span data-ttu-id="83dae-116">Exempel 3: kopiera innehållet i en fil till Urklipp</span><span class="sxs-lookup"><span data-stu-id="83dae-116">Example 3: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="83dae-117">Det här exemplet rör innehållet i en fil till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-117">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="83dae-118">I det här exemplet hämtar vi en offentlig SSH-nyckel så att den kan klistras in i ett annat program, t. ex. GitHub.</span><span class="sxs-lookup"><span data-stu-id="83dae-118">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="83dae-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="83dae-119">PARAMETERS</span></span>

### <span data-ttu-id="83dae-120">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="83dae-120">-Append</span></span>

<span data-ttu-id="83dae-121">Anger att cmdleten inte rensar Urklipp och lägger till innehåll i den.</span><span class="sxs-lookup"><span data-stu-id="83dae-121">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="83dae-122">-HTML</span><span class="sxs-lookup"><span data-stu-id="83dae-122">-AsHtml</span></span>

<span data-ttu-id="83dae-123">Anger att cmdleten återger innehållet som HTML i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-123">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="83dae-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="83dae-124">-LiteralPath</span></span>

<span data-ttu-id="83dae-125">Anger sökvägen till det objekt som kopieras till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-125">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="83dae-126">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="83dae-126">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="83dae-127">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="83dae-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="83dae-128">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="83dae-128">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="83dae-129">Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="83dae-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="83dae-130">-Path</span><span class="sxs-lookup"><span data-stu-id="83dae-130">-Path</span></span>

<span data-ttu-id="83dae-131">Anger sökvägen till det objekt som kopieras till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-131">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="83dae-132">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="83dae-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="83dae-133">-Värde</span><span class="sxs-lookup"><span data-stu-id="83dae-133">-Value</span></span>

<span data-ttu-id="83dae-134">Anger, som en sträng mat ris, det innehåll som ska kopieras till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-134">Specifies, as a string array, the content to copy to the clipboard.</span></span>

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

### <span data-ttu-id="83dae-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="83dae-135">-Confirm</span></span>

<span data-ttu-id="83dae-136">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="83dae-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="83dae-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="83dae-137">-WhatIf</span></span>

<span data-ttu-id="83dae-138">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="83dae-138">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="83dae-139">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="83dae-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="83dae-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="83dae-140">CommonParameters</span></span>

<span data-ttu-id="83dae-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="83dae-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="83dae-142">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="83dae-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="83dae-143">INDATA</span><span class="sxs-lookup"><span data-stu-id="83dae-143">INPUTS</span></span>

### <span data-ttu-id="83dae-144">System.String[]</span><span class="sxs-lookup"><span data-stu-id="83dae-144">System.String[]</span></span>

## <span data-ttu-id="83dae-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="83dae-145">OUTPUTS</span></span>

## <span data-ttu-id="83dae-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="83dae-146">NOTES</span></span>

<span data-ttu-id="83dae-147">I sällsynta fall när `Set-Clipboard` du använder med ett stort antal värden i snabb följd, som i en slinga, kan du sporadiskt få ett tomt värde från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="83dae-147">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="83dae-148">Detta kan åtgärdas med hjälp av `Start-Sleep -Milliseconds 1` i slingan.</span><span class="sxs-lookup"><span data-stu-id="83dae-148">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="83dae-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="83dae-149">RELATED LINKS</span></span>

[<span data-ttu-id="83dae-150">Hämta Urklipp</span><span class="sxs-lookup"><span data-stu-id="83dae-150">Get-Clipboard</span></span>](Get-Clipboard.md)
