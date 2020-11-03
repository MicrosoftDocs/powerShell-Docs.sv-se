---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: f4740bca33bd70d4d8eca51ed45ba6204b5d2acb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263427"
---
# <span data-ttu-id="37c85-103">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="37c85-103">Show-Markdown</span></span>

## <span data-ttu-id="37c85-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="37c85-104">SYNOPSIS</span></span>
<span data-ttu-id="37c85-105">Visar en MARKDOWN-fil eller-sträng i-konsolen på ett användarvänligt sätt med VT100 escape-sekvenser eller i en webbläsare med HTML.</span><span class="sxs-lookup"><span data-stu-id="37c85-105">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="37c85-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="37c85-106">SYNTAX</span></span>

### <span data-ttu-id="37c85-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="37c85-107">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="37c85-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="37c85-108">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="37c85-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="37c85-109">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="37c85-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="37c85-110">DESCRIPTION</span></span>

<span data-ttu-id="37c85-111">`Show-Markdown`Cmdleten används för att rendera markdown i ett läsligt format, antingen i en terminal eller i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="37c85-111">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="37c85-112">`Show-Markdown` kan returnera en sträng som innehåller de VT100 escape-sekvenser som terminalen återger (om det stöder VT100 escape-sekvenser).</span><span class="sxs-lookup"><span data-stu-id="37c85-112">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="37c85-113">Detta används främst för att Visa markdown-filer i en Terminal.</span><span class="sxs-lookup"><span data-stu-id="37c85-113">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="37c85-114">Du kan också hämta den här strängen via `ConvertFrom-Markdown` genom att ange parametern **AsVT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="37c85-114">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="37c85-115">`Show-Markdown` har också möjlighet att öppna en webbläsare och visa en renderad version av markdown.</span><span class="sxs-lookup"><span data-stu-id="37c85-115">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="37c85-116">Den återger markdown genom att omvandla den till HTML och öppna HTML-filen i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="37c85-116">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="37c85-117">Du kan ändra hur `Show-Markdown` renderar markdown i en Terminal med hjälp av `Set-MarkdownOption` .</span><span class="sxs-lookup"><span data-stu-id="37c85-117">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="37c85-118">Denna cmdlet introducerades i PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="37c85-118">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="37c85-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="37c85-119">EXAMPLES</span></span>

### <span data-ttu-id="37c85-120">Exempel 1: enkelt exempel som anger en sökväg</span><span class="sxs-lookup"><span data-stu-id="37c85-120">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="37c85-121">Exempel 2: enkelt exempel som anger en sträng</span><span class="sxs-lookup"><span data-stu-id="37c85-121">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="37c85-122">Exempel 2: öppna markdown i en webbläsare</span><span class="sxs-lookup"><span data-stu-id="37c85-122">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="37c85-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="37c85-123">PARAMETERS</span></span>

### <span data-ttu-id="37c85-124">– InputObject</span><span class="sxs-lookup"><span data-stu-id="37c85-124">-InputObject</span></span>

<span data-ttu-id="37c85-125">En markdown-sträng som ska visas i terminalen.</span><span class="sxs-lookup"><span data-stu-id="37c85-125">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="37c85-126">Om du inte skickar i ett format som stöds `Show-Markdown` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="37c85-126">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

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

### <span data-ttu-id="37c85-127">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="37c85-127">-LiteralPath</span></span>

<span data-ttu-id="37c85-128">Anger sökvägen till en MARKDOWN-fil.</span><span class="sxs-lookup"><span data-stu-id="37c85-128">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="37c85-129">Till skillnad från parametern Path används värdet för LiteralPath exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="37c85-129">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="37c85-130">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="37c85-130">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="37c85-131">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="37c85-131">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="37c85-132">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="37c85-132">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="37c85-133">-Path</span><span class="sxs-lookup"><span data-stu-id="37c85-133">-Path</span></span>

<span data-ttu-id="37c85-134">Anger sökvägen till en MARKDOWN-fil som ska renderas.</span><span class="sxs-lookup"><span data-stu-id="37c85-134">Specifies the path to a Markdown file to be rendered.</span></span>

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

### <span data-ttu-id="37c85-135">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="37c85-135">-UseBrowser</span></span>

<span data-ttu-id="37c85-136">Kompilerar markdown-ingången som HTML och öppnar den i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="37c85-136">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

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

### <span data-ttu-id="37c85-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="37c85-137">CommonParameters</span></span>

<span data-ttu-id="37c85-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="37c85-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="37c85-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="37c85-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="37c85-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="37c85-140">INPUTS</span></span>

### <span data-ttu-id="37c85-141">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="37c85-141">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="37c85-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="37c85-142">System.String[]</span></span>

## <span data-ttu-id="37c85-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="37c85-143">OUTPUTS</span></span>

### <span data-ttu-id="37c85-144">System. String</span><span class="sxs-lookup"><span data-stu-id="37c85-144">System.String</span></span>

## <span data-ttu-id="37c85-145">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="37c85-145">NOTES</span></span>

## <span data-ttu-id="37c85-146">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="37c85-146">RELATED LINKS</span></span>

[<span data-ttu-id="37c85-147">ConvertFrom – markdown</span><span class="sxs-lookup"><span data-stu-id="37c85-147">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

