---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/09/2019
online version: https://go.microsoft.com/fwlink/?linkid=526220
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 271d9191a0968b03b1e7ec3d283eacc36e633516
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273542"
---
# <span data-ttu-id="4f900-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="4f900-103">Set-Clipboard</span></span>

## <span data-ttu-id="4f900-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4f900-104">SYNOPSIS</span></span>
<span data-ttu-id="4f900-105">Anger innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4f900-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="4f900-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f900-106">SYNTAX</span></span>

```
Set-Clipboard [-Value] <string[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4f900-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4f900-107">DESCRIPTION</span></span>

<span data-ttu-id="4f900-108">`Set-Clipboard`Cmdleten anger innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4f900-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="4f900-109">I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="4f900-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="4f900-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4f900-110">EXAMPLES</span></span>

### <span data-ttu-id="4f900-111">Exempel 1: kopiera text till Urklipp</span><span class="sxs-lookup"><span data-stu-id="4f900-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

## <span data-ttu-id="4f900-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4f900-112">PARAMETERS</span></span>

### <span data-ttu-id="4f900-113">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="4f900-113">-Append</span></span>

<span data-ttu-id="4f900-114">Anger att cmdleten inte rensar Urklipp och lägger till innehåll i den.</span><span class="sxs-lookup"><span data-stu-id="4f900-114">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="4f900-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4f900-115">-Confirm</span></span>

<span data-ttu-id="4f900-116">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4f900-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4f900-117">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4f900-117">-WhatIf</span></span>

<span data-ttu-id="4f900-118">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4f900-118">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4f900-119">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4f900-119">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4f900-120">-Värde</span><span class="sxs-lookup"><span data-stu-id="4f900-120">-Value</span></span>

<span data-ttu-id="4f900-121">De sträng värden som ska läggas till i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4f900-121">The string values to be added to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f900-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f900-122">CommonParameters</span></span>

<span data-ttu-id="4f900-123">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f900-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f900-124">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f900-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f900-125">INDATA</span><span class="sxs-lookup"><span data-stu-id="4f900-125">INPUTS</span></span>

### <span data-ttu-id="4f900-126">System.String[]</span><span class="sxs-lookup"><span data-stu-id="4f900-126">System.String[]</span></span>

## <span data-ttu-id="4f900-127">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4f900-127">OUTPUTS</span></span>

## <span data-ttu-id="4f900-128">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4f900-128">NOTES</span></span>

<span data-ttu-id="4f900-129">I sällsynta fall när `Set-Clipboard` du använder med ett stort antal värden i snabb följd, som i en slinga, kan du sporadiskt få ett tomt värde från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4f900-129">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="4f900-130">Detta kan åtgärdas med hjälp av `Start-Sleep -Milliseconds 1` i slingan.</span><span class="sxs-lookup"><span data-stu-id="4f900-130">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="4f900-131">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4f900-131">RELATED LINKS</span></span>

[<span data-ttu-id="4f900-132">Hämta Urklipp</span><span class="sxs-lookup"><span data-stu-id="4f900-132">Get-Clipboard</span></span>](Get-Clipboard.md)
