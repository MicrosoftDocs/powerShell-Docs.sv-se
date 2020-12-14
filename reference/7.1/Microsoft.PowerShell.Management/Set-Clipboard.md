---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 1ee55dfaf4ecd3e46bedd8f356b1f677180c9c62
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564562"
---
# <span data-ttu-id="e80e4-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e80e4-103">Set-Clipboard</span></span>

## <span data-ttu-id="e80e4-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e80e4-104">SYNOPSIS</span></span>
<span data-ttu-id="e80e4-105">Anger innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="e80e4-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="e80e4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e80e4-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e80e4-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e80e4-107">DESCRIPTION</span></span>

<span data-ttu-id="e80e4-108">`Set-Clipboard`Cmdleten anger innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="e80e4-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="e80e4-109">I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="e80e4-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="e80e4-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e80e4-110">EXAMPLES</span></span>

### <span data-ttu-id="e80e4-111">Exempel 1: kopiera text till Urklipp</span><span class="sxs-lookup"><span data-stu-id="e80e4-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="e80e4-112">Exempel 2: kopiera innehållet i en fil till Urklipp</span><span class="sxs-lookup"><span data-stu-id="e80e4-112">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="e80e4-113">Det här exemplet rör innehållet i en fil till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="e80e4-113">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="e80e4-114">I det här exemplet hämtar vi en offentlig SSH-nyckel så att den kan klistras in i ett annat program, t. ex. GitHub.</span><span class="sxs-lookup"><span data-stu-id="e80e4-114">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="e80e4-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e80e4-115">PARAMETERS</span></span>

### <span data-ttu-id="e80e4-116">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="e80e4-116">-Append</span></span>

<span data-ttu-id="e80e4-117">Anger att cmdleten inte rensar Urklipp och lägger till innehåll i den.</span><span class="sxs-lookup"><span data-stu-id="e80e4-117">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="e80e4-118">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e80e4-118">-Confirm</span></span>

<span data-ttu-id="e80e4-119">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e80e4-119">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e80e4-120">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e80e4-120">-WhatIf</span></span>

<span data-ttu-id="e80e4-121">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e80e4-121">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e80e4-122">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e80e4-122">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e80e4-123">-Värde</span><span class="sxs-lookup"><span data-stu-id="e80e4-123">-Value</span></span>

<span data-ttu-id="e80e4-124">De sträng värden som ska läggas till i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="e80e4-124">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="e80e4-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e80e4-125">CommonParameters</span></span>

<span data-ttu-id="e80e4-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e80e4-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e80e4-127">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e80e4-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e80e4-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="e80e4-128">INPUTS</span></span>

### <span data-ttu-id="e80e4-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e80e4-129">System.String[]</span></span>

## <span data-ttu-id="e80e4-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e80e4-130">OUTPUTS</span></span>

## <span data-ttu-id="e80e4-131">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e80e4-131">NOTES</span></span>

<span data-ttu-id="e80e4-132">I sällsynta fall när `Set-Clipboard` du använder med ett stort antal värden i snabb följd, som i en slinga, kan du sporadiskt få ett tomt värde från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="e80e4-132">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="e80e4-133">Detta kan åtgärdas med hjälp av `Start-Sleep -Milliseconds 1` i slingan.</span><span class="sxs-lookup"><span data-stu-id="e80e4-133">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="e80e4-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e80e4-134">RELATED LINKS</span></span>

[<span data-ttu-id="e80e4-135">Hämta Urklipp</span><span class="sxs-lookup"><span data-stu-id="e80e4-135">Get-Clipboard</span></span>](Get-Clipboard.md)
