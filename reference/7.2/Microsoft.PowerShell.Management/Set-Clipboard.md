---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 7772c3e7a5f7492713e0be9a94e92b8c41cd3dd4
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564569"
---
# <span data-ttu-id="41946-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="41946-102">Set-Clipboard</span></span>

## <span data-ttu-id="41946-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="41946-103">SYNOPSIS</span></span>
<span data-ttu-id="41946-104">Anger innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="41946-104">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="41946-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41946-105">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="41946-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="41946-106">DESCRIPTION</span></span>

<span data-ttu-id="41946-107">`Set-Clipboard`Cmdleten anger innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="41946-107">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="41946-108">I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="41946-108">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="41946-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="41946-109">EXAMPLES</span></span>

### <span data-ttu-id="41946-110">Exempel 1: kopiera text till Urklipp</span><span class="sxs-lookup"><span data-stu-id="41946-110">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="41946-111">Exempel 2: kopiera innehållet i en fil till Urklipp</span><span class="sxs-lookup"><span data-stu-id="41946-111">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="41946-112">Det här exemplet rör innehållet i en fil till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="41946-112">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="41946-113">I det här exemplet hämtar vi en offentlig SSH-nyckel så att den kan klistras in i ett annat program, t. ex. GitHub.</span><span class="sxs-lookup"><span data-stu-id="41946-113">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="41946-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="41946-114">PARAMETERS</span></span>

### <span data-ttu-id="41946-115">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="41946-115">-Append</span></span>

<span data-ttu-id="41946-116">Anger att cmdleten inte rensar Urklipp och lägger till innehåll i den.</span><span class="sxs-lookup"><span data-stu-id="41946-116">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="41946-117">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41946-117">-Confirm</span></span>

<span data-ttu-id="41946-118">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="41946-118">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41946-119">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41946-119">-WhatIf</span></span>

<span data-ttu-id="41946-120">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="41946-120">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="41946-121">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="41946-121">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="41946-122">-Värde</span><span class="sxs-lookup"><span data-stu-id="41946-122">-Value</span></span>

<span data-ttu-id="41946-123">De sträng värden som ska läggas till i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="41946-123">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="41946-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41946-124">CommonParameters</span></span>

<span data-ttu-id="41946-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41946-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41946-126">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="41946-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41946-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="41946-127">INPUTS</span></span>

### <span data-ttu-id="41946-128">System.String[]</span><span class="sxs-lookup"><span data-stu-id="41946-128">System.String[]</span></span>

## <span data-ttu-id="41946-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="41946-129">OUTPUTS</span></span>

## <span data-ttu-id="41946-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="41946-130">NOTES</span></span>

<span data-ttu-id="41946-131">I sällsynta fall när `Set-Clipboard` du använder med ett stort antal värden i snabb följd, som i en slinga, kan du sporadiskt få ett tomt värde från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="41946-131">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="41946-132">Detta kan åtgärdas med hjälp av `Start-Sleep -Milliseconds 1` i slingan.</span><span class="sxs-lookup"><span data-stu-id="41946-132">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="41946-133">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="41946-133">RELATED LINKS</span></span>

[<span data-ttu-id="41946-134">Hämta Urklipp</span><span class="sxs-lookup"><span data-stu-id="41946-134">Get-Clipboard</span></span>](Get-Clipboard.md)