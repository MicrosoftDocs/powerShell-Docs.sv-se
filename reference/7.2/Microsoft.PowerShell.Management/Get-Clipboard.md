---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: b0a9e5d1707e0d2f46c25991ddceff27d1b85287
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710435"
---
# <span data-ttu-id="5b021-102">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="5b021-102">Get-Clipboard</span></span>

## <span data-ttu-id="5b021-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5b021-103">SYNOPSIS</span></span>
<span data-ttu-id="5b021-104">Hämtar innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="5b021-104">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="5b021-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b021-105">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="5b021-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5b021-106">DESCRIPTION</span></span>

<span data-ttu-id="5b021-107">`Get-Clipboard`Cmdleten hämtar innehållet i Urklipp som text.</span><span class="sxs-lookup"><span data-stu-id="5b021-107">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="5b021-108">Flera rader med text returneras som en sträng mat ris som liknar `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="5b021-108">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="5b021-109">I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="5b021-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span> <span data-ttu-id="5b021-110">Denna cmdlet stöds inte på macOS.</span><span class="sxs-lookup"><span data-stu-id="5b021-110">This cmdlet is not supported on macOS.</span></span>

## <span data-ttu-id="5b021-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5b021-111">EXAMPLES</span></span>

### <span data-ttu-id="5b021-112">Exempel 1: hämta innehållet i Urklipp och visa det på kommando raden</span><span class="sxs-lookup"><span data-stu-id="5b021-112">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="5b021-113">I det här exemplet har vi kopierat texten "Hej" till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="5b021-113">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="5b021-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5b021-114">PARAMETERS</span></span>

### <span data-ttu-id="5b021-115">– RAW</span><span class="sxs-lookup"><span data-stu-id="5b021-115">-Raw</span></span>

<span data-ttu-id="5b021-116">Hämtar hela innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="5b021-116">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="5b021-117">Flerradig text returneras som en enskild Multiline-sträng i stället för en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="5b021-117">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="5b021-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b021-118">CommonParameters</span></span>

<span data-ttu-id="5b021-119">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b021-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b021-120">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b021-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b021-121">INDATA</span><span class="sxs-lookup"><span data-stu-id="5b021-121">INPUTS</span></span>

## <span data-ttu-id="5b021-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5b021-122">OUTPUTS</span></span>

### <span data-ttu-id="5b021-123">System. String</span><span class="sxs-lookup"><span data-stu-id="5b021-123">System.String</span></span>

## <span data-ttu-id="5b021-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5b021-124">NOTES</span></span>

## <span data-ttu-id="5b021-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5b021-125">RELATED LINKS</span></span>

[<span data-ttu-id="5b021-126">Ange Urklipp</span><span class="sxs-lookup"><span data-stu-id="5b021-126">Set-Clipboard</span></span>](Set-Clipboard.md)
