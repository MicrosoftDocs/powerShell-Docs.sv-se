---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: d14e6332a2da5c86c4f8ada0d110c64e080437e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709744"
---
# <span data-ttu-id="aca30-102">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="aca30-102">Show-Markdown</span></span>

## <span data-ttu-id="aca30-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aca30-103">SYNOPSIS</span></span>
<span data-ttu-id="aca30-104">Visar en MARKDOWN-fil eller-sträng i-konsolen på ett användarvänligt sätt med VT100 escape-sekvenser eller i en webbläsare med HTML.</span><span class="sxs-lookup"><span data-stu-id="aca30-104">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="aca30-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aca30-105">SYNTAX</span></span>

### <span data-ttu-id="aca30-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="aca30-106">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="aca30-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="aca30-107">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="aca30-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aca30-108">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="aca30-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aca30-109">DESCRIPTION</span></span>

<span data-ttu-id="aca30-110">`Show-Markdown`Cmdleten används för att rendera markdown i ett läsligt format, antingen i en terminal eller i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="aca30-110">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="aca30-111">`Show-Markdown` kan returnera en sträng som innehåller de VT100 escape-sekvenser som terminalen återger (om det stöder VT100 escape-sekvenser).</span><span class="sxs-lookup"><span data-stu-id="aca30-111">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="aca30-112">Detta används främst för att Visa markdown-filer i en Terminal.</span><span class="sxs-lookup"><span data-stu-id="aca30-112">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="aca30-113">Du kan också hämta den här strängen via `ConvertFrom-Markdown` genom att ange parametern **AsVT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="aca30-113">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="aca30-114">`Show-Markdown` har också möjlighet att öppna en webbläsare och visa en renderad version av markdown.</span><span class="sxs-lookup"><span data-stu-id="aca30-114">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="aca30-115">Den återger markdown genom att omvandla den till HTML och öppna HTML-filen i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="aca30-115">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="aca30-116">Du kan ändra hur `Show-Markdown` renderar markdown i en Terminal med hjälp av `Set-MarkdownOption` .</span><span class="sxs-lookup"><span data-stu-id="aca30-116">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="aca30-117">Denna cmdlet introducerades i PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="aca30-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="aca30-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aca30-118">EXAMPLES</span></span>

### <span data-ttu-id="aca30-119">Exempel 1: enkelt exempel som anger en sökväg</span><span class="sxs-lookup"><span data-stu-id="aca30-119">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="aca30-120">Exempel 2: enkelt exempel som anger en sträng</span><span class="sxs-lookup"><span data-stu-id="aca30-120">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="aca30-121">Exempel 2: öppna markdown i en webbläsare</span><span class="sxs-lookup"><span data-stu-id="aca30-121">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="aca30-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aca30-122">PARAMETERS</span></span>

### <span data-ttu-id="aca30-123">– InputObject</span><span class="sxs-lookup"><span data-stu-id="aca30-123">-InputObject</span></span>

<span data-ttu-id="aca30-124">En markdown-sträng som ska visas i terminalen.</span><span class="sxs-lookup"><span data-stu-id="aca30-124">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="aca30-125">Om du inte skickar i ett format som stöds `Show-Markdown` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="aca30-125">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aca30-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aca30-126">-LiteralPath</span></span>

<span data-ttu-id="aca30-127">Anger sökvägen till en MARKDOWN-fil.</span><span class="sxs-lookup"><span data-stu-id="aca30-127">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="aca30-128">Till skillnad från parametern Path används värdet för LiteralPath exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="aca30-128">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="aca30-129">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aca30-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="aca30-130">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="aca30-130">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="aca30-131">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="aca30-131">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aca30-132">-Path</span><span class="sxs-lookup"><span data-stu-id="aca30-132">-Path</span></span>

<span data-ttu-id="aca30-133">Anger sökvägen till en MARKDOWN-fil som ska renderas.</span><span class="sxs-lookup"><span data-stu-id="aca30-133">Specifies the path to a Markdown file to be rendered.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="aca30-134">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="aca30-134">-UseBrowser</span></span>

<span data-ttu-id="aca30-135">Kompilerar markdown-ingången som HTML och öppnar den i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="aca30-135">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aca30-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aca30-136">CommonParameters</span></span>

<span data-ttu-id="aca30-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aca30-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aca30-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aca30-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aca30-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="aca30-139">INPUTS</span></span>

### <span data-ttu-id="aca30-140">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="aca30-140">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="aca30-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="aca30-141">System.String[]</span></span>

## <span data-ttu-id="aca30-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aca30-142">OUTPUTS</span></span>

### <span data-ttu-id="aca30-143">System. String</span><span class="sxs-lookup"><span data-stu-id="aca30-143">System.String</span></span>

## <span data-ttu-id="aca30-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aca30-144">NOTES</span></span>

## <span data-ttu-id="aca30-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aca30-145">RELATED LINKS</span></span>

[<span data-ttu-id="aca30-146">ConvertFrom – markdown</span><span class="sxs-lookup"><span data-stu-id="aca30-146">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

