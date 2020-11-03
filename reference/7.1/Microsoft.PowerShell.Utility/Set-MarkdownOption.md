---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e7e70637afcf53f84c719b489575f5267f9048b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263457"
---
# <span data-ttu-id="ac352-101">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="ac352-101">Set-MarkdownOption</span></span>

## <span data-ttu-id="ac352-102">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ac352-102">SYNOPSIS</span></span>
<span data-ttu-id="ac352-103">Anger de färger och format som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ac352-103">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="ac352-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ac352-104">SYNTAX</span></span>

### <span data-ttu-id="ac352-105">IndividualSetting (standard)</span><span class="sxs-lookup"><span data-stu-id="ac352-105">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="ac352-106">Tema</span><span class="sxs-lookup"><span data-stu-id="ac352-106">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="ac352-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="ac352-107">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="ac352-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ac352-108">DESCRIPTION</span></span>

<span data-ttu-id="ac352-109">Anger de färger och format som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ac352-109">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="ac352-110">Dessa format definieras med ANSI Escape-koder som ändrar färg och format på den markdown text som återges.</span><span class="sxs-lookup"><span data-stu-id="ac352-110">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="ac352-111">Mer information om markdown finns på [CommonMark](https://commonmark.org/) -webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="ac352-111">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="ac352-112">Sträng värden som används i inställningarna är de tecken som följer **Escape** -tecknet ( `[char]0x1B` ) för ANSI Escape-sekvensen.</span><span class="sxs-lookup"><span data-stu-id="ac352-112">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="ac352-113">Inkludera inte **Escape** -tecken i strängen.</span><span class="sxs-lookup"><span data-stu-id="ac352-113">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="ac352-114">Mer information om hur ANSI Escape-koder fungerar finns i [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="ac352-114">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="ac352-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ac352-115">EXAMPLES</span></span>

### <span data-ttu-id="ac352-116">Exempel 1 – växla till det ljusa temat</span><span class="sxs-lookup"><span data-stu-id="ac352-116">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="ac352-117">I det här exemplet väljer du det **ljusa** temat och visar den nya konfigurationen med hjälp av parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="ac352-117">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

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

### <span data-ttu-id="ac352-118">Exempel 2 – anpassa inställningarna för färg och stil</span><span class="sxs-lookup"><span data-stu-id="ac352-118">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="ac352-119">I det här exemplet ändras Escape-koden för markdown-huvudena.</span><span class="sxs-lookup"><span data-stu-id="ac352-119">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="ac352-120">Standard konfigurationen för huvuden återges som understruken text i olika färger.</span><span class="sxs-lookup"><span data-stu-id="ac352-120">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="ac352-121">Den här ändringen tar bort understryknings formatet.</span><span class="sxs-lookup"><span data-stu-id="ac352-121">This change removes the underline style.</span></span>

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

## <span data-ttu-id="ac352-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ac352-122">PARAMETERS</span></span>

### <span data-ttu-id="ac352-123">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ac352-123">-BoldForegroundColor</span></span>

<span data-ttu-id="ac352-124">Anger förgrunds färgen för rendering av fet markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-124">Sets the foreground color for rendering bold Markdown text.</span></span>

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

### <span data-ttu-id="ac352-125">-Kod</span><span class="sxs-lookup"><span data-stu-id="ac352-125">-Code</span></span>

<span data-ttu-id="ac352-126">Anger färgen för åter givning av kod block och intervall i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-126">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-127">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="ac352-127">-Header1Color</span></span>

<span data-ttu-id="ac352-128">Anger färgen för åter givning av Header1-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-128">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-129">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="ac352-129">-Header2Color</span></span>

<span data-ttu-id="ac352-130">Anger färgen för åter givning av Header2-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-130">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-131">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="ac352-131">-Header3Color</span></span>

<span data-ttu-id="ac352-132">Anger färgen för åter givning av Header3-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-132">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-133">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="ac352-133">-Header4Color</span></span>

<span data-ttu-id="ac352-134">Anger färgen för åter givning av Header4-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-134">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-135">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="ac352-135">-Header5Color</span></span>

<span data-ttu-id="ac352-136">Anger färgen för åter givning av Header5-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-136">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-137">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="ac352-137">-Header6Color</span></span>

<span data-ttu-id="ac352-138">Anger färgen för åter givning av Header6-block i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-138">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-139">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ac352-139">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="ac352-140">Anger förgrunds färgen för åter givning av alternativ text för ett bild element i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-140">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-141">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ac352-141">-InputObject</span></span>

<span data-ttu-id="ac352-142">Ett **PSMarkdownOptionInfo** -objekt som innehåller den konfiguration som ska ställas in.</span><span class="sxs-lookup"><span data-stu-id="ac352-142">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

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

### <span data-ttu-id="ac352-143">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ac352-143">-ItalicsForegroundColor</span></span>

<span data-ttu-id="ac352-144">Anger förgrunds färgen för att återge kursiv stilarna i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-144">Sets the foreground color for rendering the italics in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-145">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ac352-145">-LinkForegroundColor</span></span>

<span data-ttu-id="ac352-146">Anger förgrunds färgen för åter givning av hyperlänkar i markdown text.</span><span class="sxs-lookup"><span data-stu-id="ac352-146">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

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

### <span data-ttu-id="ac352-147">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ac352-147">-PassThru</span></span>

<span data-ttu-id="ac352-148">Gör att cmdleten genererar ett **PSMarkdownOptionInfo** -objekt som innehåller den nya konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ac352-148">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="ac352-149">– Tema</span><span class="sxs-lookup"><span data-stu-id="ac352-149">-Theme</span></span>

<span data-ttu-id="ac352-150">Väljer ett tema som innehåller fördefinierade färg inställningar.</span><span class="sxs-lookup"><span data-stu-id="ac352-150">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="ac352-151">De möjliga värdena är **mörka** och **ljusa**.</span><span class="sxs-lookup"><span data-stu-id="ac352-151">The possible values are **Dark** and **Light**.</span></span>

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

### <span data-ttu-id="ac352-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac352-152">CommonParameters</span></span>

<span data-ttu-id="ac352-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ac352-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ac352-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ac352-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ac352-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="ac352-155">INPUTS</span></span>

### <span data-ttu-id="ac352-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="ac352-156">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="ac352-157">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ac352-157">OUTPUTS</span></span>

### <span data-ttu-id="ac352-158">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="ac352-158">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="ac352-159">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ac352-159">NOTES</span></span>

<span data-ttu-id="ac352-160">De sträng värden som används för att definiera färgen och formatet måste matcha det reguljära uttrycket `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="ac352-160">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="ac352-161">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ac352-161">RELATED LINKS</span></span>

[<span data-ttu-id="ac352-162">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="ac352-162">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="ac352-163">ConvertFrom – markdown</span><span class="sxs-lookup"><span data-stu-id="ac352-163">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="ac352-164">Visa markdown</span><span class="sxs-lookup"><span data-stu-id="ac352-164">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="ac352-165">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="ac352-165">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="ac352-166">CommonMark</span><span class="sxs-lookup"><span data-stu-id="ac352-166">CommonMark</span></span>](https://commonmark.org/)

