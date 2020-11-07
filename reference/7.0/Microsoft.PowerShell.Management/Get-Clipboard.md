---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: ed56dc5655f640dae1d80c66850581ff12dbb7ee
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347609"
---
# <span data-ttu-id="fcc51-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="fcc51-103">Get-Clipboard</span></span>

## <span data-ttu-id="fcc51-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fcc51-104">SYNOPSIS</span></span>
<span data-ttu-id="fcc51-105">Hämtar innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="fcc51-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="fcc51-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fcc51-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="fcc51-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fcc51-107">DESCRIPTION</span></span>

<span data-ttu-id="fcc51-108">`Get-Clipboard`Cmdleten hämtar innehållet i Urklipp som text.</span><span class="sxs-lookup"><span data-stu-id="fcc51-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="fcc51-109">Flera rader med text returneras som en sträng mat ris som liknar `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="fcc51-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc51-110">I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fcc51-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span> <span data-ttu-id="fcc51-111">Denna cmdlet stöds inte på macOS.</span><span class="sxs-lookup"><span data-stu-id="fcc51-111">This cmdlet is not supported on macOS.</span></span>

## <span data-ttu-id="fcc51-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fcc51-112">EXAMPLES</span></span>

### <span data-ttu-id="fcc51-113">Exempel 1: hämta innehållet i Urklipp och visa det på kommando raden</span><span class="sxs-lookup"><span data-stu-id="fcc51-113">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="fcc51-114">I det här exemplet har vi kopierat texten "Hej" till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="fcc51-114">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="fcc51-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fcc51-115">PARAMETERS</span></span>

### <span data-ttu-id="fcc51-116">– RAW</span><span class="sxs-lookup"><span data-stu-id="fcc51-116">-Raw</span></span>

<span data-ttu-id="fcc51-117">Hämtar hela innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="fcc51-117">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="fcc51-118">Flerradig text returneras som en enskild Multiline-sträng i stället för en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="fcc51-118">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="fcc51-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fcc51-119">CommonParameters</span></span>

<span data-ttu-id="fcc51-120">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fcc51-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fcc51-121">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fcc51-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fcc51-122">INDATA</span><span class="sxs-lookup"><span data-stu-id="fcc51-122">INPUTS</span></span>

## <span data-ttu-id="fcc51-123">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fcc51-123">OUTPUTS</span></span>

### <span data-ttu-id="fcc51-124">System. String</span><span class="sxs-lookup"><span data-stu-id="fcc51-124">System.String</span></span>

## <span data-ttu-id="fcc51-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fcc51-125">NOTES</span></span>

## <span data-ttu-id="fcc51-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fcc51-126">RELATED LINKS</span></span>

[<span data-ttu-id="fcc51-127">Ange Urklipp</span><span class="sxs-lookup"><span data-stu-id="fcc51-127">Set-Clipboard</span></span>](Set-Clipboard.md)
