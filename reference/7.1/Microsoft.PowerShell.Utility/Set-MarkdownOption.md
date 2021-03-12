---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-MarkdownOption
ms.openlocfilehash: 5e19dc25d0b10888f6ce2f915926610f0780daf6
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195311"
---
# <span data-ttu-id="7ce57-102">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="7ce57-102">Set-MarkdownOption</span></span>

## <span data-ttu-id="7ce57-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7ce57-103">SYNOPSIS</span></span>
<span data-ttu-id="7ce57-104">Anger de färger och format som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7ce57-104">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="7ce57-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7ce57-105">SYNTAX</span></span>

### <span data-ttu-id="7ce57-106">IndividualSetting (standard)</span><span class="sxs-lookup"><span data-stu-id="7ce57-106">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="7ce57-107">Tema</span><span class="sxs-lookup"><span data-stu-id="7ce57-107">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="7ce57-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="7ce57-108">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="7ce57-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7ce57-109">DESCRIPTION</span></span>

<span data-ttu-id="7ce57-110">Anger de färger och format som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7ce57-110">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="7ce57-111">Dessa format definieras med ANSI Escape-koder som ändrar färg och format på den markdown text som återges.</span><span class="sxs-lookup"><span data-stu-id="7ce57-111">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="7ce57-112">Mer information om markdown finns på [CommonMark](https://commonmark.org/) -webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="7ce57-112">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="7ce57-113">Sträng värden som används i inställningarna är de tecken som följer **Escape** -tecknet ( `[char]0x1B` ) för ANSI Escape-sekvensen.</span><span class="sxs-lookup"><span data-stu-id="7ce57-113">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="7ce57-114">Inkludera inte **Escape** -tecken i strängen.</span><span class="sxs-lookup"><span data-stu-id="7ce57-114">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="7ce57-115">Mer information om hur ANSI Escape-koder fungerar finns i [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="7ce57-115">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="7ce57-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7ce57-116">EXAMPLES</span></span>

### <span data-ttu-id="7ce57-117">Exempel 1 – växla till det ljusa temat</span><span class="sxs-lookup"><span data-stu-id="7ce57-117">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="7ce57-118">I det här exemplet väljer du det **ljusa** temat och visar den nya konfigurationen med hjälp av parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="7ce57-118">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### <span data-ttu-id="7ce57-119">Exempel 2 – anpassa inställningarna för färg och stil</span><span class="sxs-lookup"><span data-stu-id="7ce57-119">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="7ce57-120">I det här exemplet ändras Escape-koden för markdown-huvudena.</span><span class="sxs-lookup"><span data-stu-id="7ce57-120">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="7ce57-121">Standard konfigurationen för huvuden återges som understruken text i olika färger.</span><span class="sxs-lookup"><span data-stu-id="7ce57-121">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="7ce57-122">Den här ändringen tar bort understryknings formatet.</span><span class="sxs-lookup"><span data-stu-id="7ce57-122">This change removes the underline style.</span></span>

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## <span data-ttu-id="7ce57-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7ce57-123">PARAMETERS</span></span>

### <span data-ttu-id="7ce57-124">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7ce57-124">-BoldForegroundColor</span></span>

<span data-ttu-id="7ce57-125">Anger förgrunds färgen för rendering av fet markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-125">Sets the foreground color for rendering bold Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-126">-Kod</span><span class="sxs-lookup"><span data-stu-id="7ce57-126">-Code</span></span>

<span data-ttu-id="7ce57-127">Anger färgen för åter givning av kod block och intervall i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-127">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-128">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="7ce57-128">-Header1Color</span></span>

<span data-ttu-id="7ce57-129">Anger färgen för åter givning av Header1-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-129">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-130">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="7ce57-130">-Header2Color</span></span>

<span data-ttu-id="7ce57-131">Anger färgen för åter givning av Header2-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-131">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-132">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="7ce57-132">-Header3Color</span></span>

<span data-ttu-id="7ce57-133">Anger färgen för åter givning av Header3-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-133">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-134">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="7ce57-134">-Header4Color</span></span>

<span data-ttu-id="7ce57-135">Anger färgen för åter givning av Header4-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-135">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-136">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="7ce57-136">-Header5Color</span></span>

<span data-ttu-id="7ce57-137">Anger färgen för åter givning av Header5-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-137">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-138">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="7ce57-138">-Header6Color</span></span>

<span data-ttu-id="7ce57-139">Anger färgen för åter givning av Header6-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-139">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-140">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7ce57-140">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="7ce57-141">Anger förgrunds färgen för åter givning av alternativ text för ett bild element i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-141">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-142">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7ce57-142">-InputObject</span></span>

<span data-ttu-id="7ce57-143">Ett **PSMarkdownOptionInfo** -objekt som innehåller den konfiguration som ska ställas in.</span><span class="sxs-lookup"><span data-stu-id="7ce57-143">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-144">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7ce57-144">-ItalicsForegroundColor</span></span>

<span data-ttu-id="7ce57-145">Anger förgrunds färgen för att återge kursiv stilarna i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-145">Sets the foreground color for rendering the italics in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-146">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7ce57-146">-LinkForegroundColor</span></span>

<span data-ttu-id="7ce57-147">Anger förgrunds färgen för åter givning av hyperlänkar i markdown text.</span><span class="sxs-lookup"><span data-stu-id="7ce57-147">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-148">– PassThru</span><span class="sxs-lookup"><span data-stu-id="7ce57-148">-PassThru</span></span>

<span data-ttu-id="7ce57-149">Gör att cmdleten genererar ett **PSMarkdownOptionInfo** -objekt som innehåller den nya konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="7ce57-149">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="7ce57-150">– Tema</span><span class="sxs-lookup"><span data-stu-id="7ce57-150">-Theme</span></span>

<span data-ttu-id="7ce57-151">Väljer ett tema som innehåller fördefinierade färg inställningar.</span><span class="sxs-lookup"><span data-stu-id="7ce57-151">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="7ce57-152">De möjliga värdena är **mörka** och **ljusa**.</span><span class="sxs-lookup"><span data-stu-id="7ce57-152">The possible values are **Dark** and **Light**.</span></span>

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce57-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ce57-153">CommonParameters</span></span>

<span data-ttu-id="7ce57-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7ce57-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7ce57-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7ce57-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7ce57-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="7ce57-156">INPUTS</span></span>

### <span data-ttu-id="7ce57-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7ce57-157">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="7ce57-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7ce57-158">OUTPUTS</span></span>

### <span data-ttu-id="7ce57-159">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="7ce57-159">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="7ce57-160">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7ce57-160">NOTES</span></span>

<span data-ttu-id="7ce57-161">De sträng värden som används för att definiera färgen och formatet måste matcha det reguljära uttrycket `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="7ce57-161">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="7ce57-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7ce57-162">RELATED LINKS</span></span>

[<span data-ttu-id="7ce57-163">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="7ce57-163">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="7ce57-164">ConvertFrom – markdown</span><span class="sxs-lookup"><span data-stu-id="7ce57-164">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="7ce57-165">Visa markdown</span><span class="sxs-lookup"><span data-stu-id="7ce57-165">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="7ce57-166">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="7ce57-166">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="7ce57-167">CommonMark</span><span class="sxs-lookup"><span data-stu-id="7ce57-167">CommonMark</span></span>](https://commonmark.org/)

