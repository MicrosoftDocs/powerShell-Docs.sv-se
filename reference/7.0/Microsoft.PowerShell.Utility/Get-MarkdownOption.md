---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: b4dec8766b283dd16ccee0e73dd893582ed5fc8e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194483"
---
# <span data-ttu-id="25fa4-102">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="25fa4-102">Get-MarkdownOption</span></span>

## <span data-ttu-id="25fa4-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="25fa4-103">SYNOPSIS</span></span>
<span data-ttu-id="25fa4-104">Returnerar de aktuella färgerna och formaten som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="25fa4-104">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="25fa4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="25fa4-105">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="25fa4-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="25fa4-106">DESCRIPTION</span></span>

<span data-ttu-id="25fa4-107">Returnerar de aktuella färgerna och formaten som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="25fa4-107">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="25fa4-108">Strängarna som visas i utdata från den här cmdleten innehåller ANSI-Escape-koderna som används för att ändra färg och format på den markdown text som återges.</span><span class="sxs-lookup"><span data-stu-id="25fa4-108">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="25fa4-109">Mer information om markdown finns på [CommonMark](https://commonmark.org/) -webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="25fa4-109">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="25fa4-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="25fa4-110">EXAMPLES</span></span>

### <span data-ttu-id="25fa4-111">Exempel 1 – Hämta aktuella färger och format</span><span class="sxs-lookup"><span data-stu-id="25fa4-111">Example 1 - Get the current colors and style</span></span>

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> <span data-ttu-id="25fa4-112">Sträng värdena som visas i utdata är de tecken som följer **Escape** -tecknet ( `[char]0x1B` ) för ANSI Escape-sekvensen.</span><span class="sxs-lookup"><span data-stu-id="25fa4-112">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="25fa4-113">Mer information om hur ANSI Escape-koder fungerar finns i [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="25fa4-113">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="25fa4-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="25fa4-114">PARAMETERS</span></span>

### <span data-ttu-id="25fa4-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25fa4-115">CommonParameters</span></span>

<span data-ttu-id="25fa4-116">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="25fa4-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25fa4-117">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="25fa4-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25fa4-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="25fa4-118">INPUTS</span></span>

### <span data-ttu-id="25fa4-119">Inget</span><span class="sxs-lookup"><span data-stu-id="25fa4-119">None</span></span>

## <span data-ttu-id="25fa4-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="25fa4-120">OUTPUTS</span></span>

### <span data-ttu-id="25fa4-121">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="25fa4-121">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="25fa4-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="25fa4-122">NOTES</span></span>

## <span data-ttu-id="25fa4-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="25fa4-123">RELATED LINKS</span></span>

[<span data-ttu-id="25fa4-124">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="25fa4-124">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="25fa4-125">ConvertFrom – markdown</span><span class="sxs-lookup"><span data-stu-id="25fa4-125">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="25fa4-126">Visa markdown</span><span class="sxs-lookup"><span data-stu-id="25fa4-126">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="25fa4-127">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="25fa4-127">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="25fa4-128">CommonMark</span><span class="sxs-lookup"><span data-stu-id="25fa4-128">CommonMark</span></span>](https://commonmark.org/)
