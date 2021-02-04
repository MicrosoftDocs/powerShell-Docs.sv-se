---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 6ac35c698cc1b4f2571becdee48b1f73f21249e7
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098728"
---
# <span data-ttu-id="c41ca-102">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="c41ca-102">Clear-RecycleBin</span></span>

## <span data-ttu-id="c41ca-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c41ca-103">SYNOPSIS</span></span>
<span data-ttu-id="c41ca-104">Rensar innehållet i en pappers korg.</span><span class="sxs-lookup"><span data-stu-id="c41ca-104">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="c41ca-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c41ca-105">SYNTAX</span></span>

### <span data-ttu-id="c41ca-106">Alla</span><span class="sxs-lookup"><span data-stu-id="c41ca-106">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c41ca-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c41ca-107">DESCRIPTION</span></span>

<span data-ttu-id="c41ca-108">`Clear-RecycleBin`Cmdleten tar bort innehållet i en dators pappers korg.</span><span class="sxs-lookup"><span data-stu-id="c41ca-108">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="c41ca-109">Den här åtgärden påminner om att använda Windows **tomt Pappers korgen**.</span><span class="sxs-lookup"><span data-stu-id="c41ca-109">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="c41ca-110">Den här cmdleten lades till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c41ca-110">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="c41ca-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c41ca-111">EXAMPLES</span></span>

### <span data-ttu-id="c41ca-112">1: Rensa alla pappers korgar</span><span class="sxs-lookup"><span data-stu-id="c41ca-112">1: Clear all recycle bins</span></span>

<span data-ttu-id="c41ca-113">I det här exemplet rensas alla lokala datorer i pappers korgen.</span><span class="sxs-lookup"><span data-stu-id="c41ca-113">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c41ca-114">`Clear-RecycleBin` uppmanas användaren att bekräfta att alla pappers korgar tas bort från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c41ca-114">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="c41ca-115">2: Rensa en angiven pappers korg</span><span class="sxs-lookup"><span data-stu-id="c41ca-115">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="c41ca-116">I det här exemplet rensas pappers korgen för en angiven enhets beteckning.</span><span class="sxs-lookup"><span data-stu-id="c41ca-116">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="c41ca-117">`Clear-RecycleBin` använder parametern **DriveLetter** för att ange pappers korgen på **C** -volymen.</span><span class="sxs-lookup"><span data-stu-id="c41ca-117">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="c41ca-118">Användaren uppmanas att bekräfta att kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="c41ca-118">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="c41ca-119">3: Rensa alla pappers korgar utan bekräftelse</span><span class="sxs-lookup"><span data-stu-id="c41ca-119">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="c41ca-120">I det här exemplet visas ingen bekräftelse för att ta bort den lokala datorns pappers korg.</span><span class="sxs-lookup"><span data-stu-id="c41ca-120">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="c41ca-121">`Clear-RecycleBin` använder **Force** -parametern och uppmanas inte användaren att bekräfta att alla pappers korgar tas bort från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c41ca-121">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="c41ca-122">Ett alternativ är att ersätta `-Force` med `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="c41ca-122">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="c41ca-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c41ca-123">PARAMETERS</span></span>

### <span data-ttu-id="c41ca-124">-DriveLetter</span><span class="sxs-lookup"><span data-stu-id="c41ca-124">-DriveLetter</span></span>

<span data-ttu-id="c41ca-125">Anger pappers korgen för att rensa en enskild enhets beteckning eller en matris med enhets beteckningar.</span><span class="sxs-lookup"><span data-stu-id="c41ca-125">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c41ca-126">-Force</span><span class="sxs-lookup"><span data-stu-id="c41ca-126">-Force</span></span>

<span data-ttu-id="c41ca-127">Anger att användaren inte behöver bekräfta att en pappers korgen ska rensas.</span><span class="sxs-lookup"><span data-stu-id="c41ca-127">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span> <span data-ttu-id="c41ca-128">Parametern **Force** åsidosätter också parametrarna **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="c41ca-128">The **Force** parameter also overrides the **WhatIf** and **Confirm** parameters.</span></span>

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

### <span data-ttu-id="c41ca-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c41ca-129">-Confirm</span></span>

<span data-ttu-id="c41ca-130">Uppmanas att bekräfta användaren innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c41ca-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="c41ca-131">Användaren uppmanas att bekräfta även om parametern **Confirm** inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="c41ca-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="c41ca-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c41ca-132">-WhatIf</span></span>

<span data-ttu-id="c41ca-133">Visar vad som händer om `Clear-RecycleBin` körs.</span><span class="sxs-lookup"><span data-stu-id="c41ca-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="c41ca-134">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c41ca-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c41ca-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c41ca-135">CommonParameters</span></span>

<span data-ttu-id="c41ca-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c41ca-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c41ca-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c41ca-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c41ca-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="c41ca-138">INPUTS</span></span>

## <span data-ttu-id="c41ca-139">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c41ca-139">OUTPUTS</span></span>

### <span data-ttu-id="c41ca-140">Inget</span><span class="sxs-lookup"><span data-stu-id="c41ca-140">None</span></span>

## <span data-ttu-id="c41ca-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c41ca-141">NOTES</span></span>

<span data-ttu-id="c41ca-142">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="c41ca-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="c41ca-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c41ca-143">RELATED LINKS</span></span>
