---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: 52c0a94304156a7c1cf89bbc5ae98a0668789bd2
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/21/2020
ms.locfileid: "93261499"
---
# <span data-ttu-id="dc509-101">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="dc509-101">Get-MarkdownOption</span></span>

## <span data-ttu-id="dc509-102">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dc509-102">SYNOPSIS</span></span>
<span data-ttu-id="dc509-103">Returnerar de aktuella färgerna och formaten som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="dc509-103">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="dc509-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc509-104">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="dc509-105">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dc509-105">DESCRIPTION</span></span>

<span data-ttu-id="dc509-106">Returnerar de aktuella färgerna och formaten som används för att återge markdown-innehåll i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="dc509-106">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="dc509-107">Strängarna som visas i utdata från den här cmdleten innehåller ANSI-Escape-koderna som används för att ändra färg och format på den markdown text som återges.</span><span class="sxs-lookup"><span data-stu-id="dc509-107">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="dc509-108">Mer information om markdown finns på [CommonMark](https://commonmark.org/) -webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="dc509-108">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="dc509-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dc509-109">EXAMPLES</span></span>

### <span data-ttu-id="dc509-110">Exempel 1 – Hämta aktuella färger och format</span><span class="sxs-lookup"><span data-stu-id="dc509-110">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="dc509-111">Sträng värdena som visas i utdata är de tecken som följer **Escape** -tecknet ( `[char]0x1B` ) för ANSI Escape-sekvensen.</span><span class="sxs-lookup"><span data-stu-id="dc509-111">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="dc509-112">Mer information om hur ANSI Escape-koder fungerar finns i [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="dc509-112">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="dc509-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dc509-113">PARAMETERS</span></span>

### <span data-ttu-id="dc509-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc509-114">CommonParameters</span></span>

<span data-ttu-id="dc509-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dc509-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc509-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dc509-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc509-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="dc509-117">INPUTS</span></span>

### <span data-ttu-id="dc509-118">Inget</span><span class="sxs-lookup"><span data-stu-id="dc509-118">None</span></span>

## <span data-ttu-id="dc509-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dc509-119">OUTPUTS</span></span>

### <span data-ttu-id="dc509-120">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="dc509-120">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="dc509-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dc509-121">NOTES</span></span>

## <span data-ttu-id="dc509-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dc509-122">RELATED LINKS</span></span>

[<span data-ttu-id="dc509-123">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="dc509-123">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="dc509-124">ConvertFrom – markdown</span><span class="sxs-lookup"><span data-stu-id="dc509-124">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="dc509-125">Visa markdown</span><span class="sxs-lookup"><span data-stu-id="dc509-125">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="dc509-126">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="dc509-126">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="dc509-127">CommonMark</span><span class="sxs-lookup"><span data-stu-id="dc509-127">CommonMark</span></span>](https://commonmark.org/)

