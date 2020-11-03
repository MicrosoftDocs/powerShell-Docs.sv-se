---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 7e34db6eb29bf60da5ce1217653db815347d69ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267735"
---
# <span data-ttu-id="e8338-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="e8338-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="e8338-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e8338-104">SYNOPSIS</span></span>
<span data-ttu-id="e8338-105">Rensar innehållet i en pappers korg.</span><span class="sxs-lookup"><span data-stu-id="e8338-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="e8338-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8338-106">SYNTAX</span></span>

### <span data-ttu-id="e8338-107">Alla</span><span class="sxs-lookup"><span data-stu-id="e8338-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e8338-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e8338-108">DESCRIPTION</span></span>

<span data-ttu-id="e8338-109">`Clear-RecycleBin`Cmdleten tar bort innehållet i en dators pappers korg.</span><span class="sxs-lookup"><span data-stu-id="e8338-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="e8338-110">Den här åtgärden påminner om att använda Windows **tomt Pappers korgen**.</span><span class="sxs-lookup"><span data-stu-id="e8338-110">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="e8338-111">Den här cmdleten lades till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e8338-111">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="e8338-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e8338-112">EXAMPLES</span></span>

### <span data-ttu-id="e8338-113">1: Rensa alla pappers korgar</span><span class="sxs-lookup"><span data-stu-id="e8338-113">1: Clear all recycle bins</span></span>

<span data-ttu-id="e8338-114">I det här exemplet rensas alla lokala datorer i pappers korgen.</span><span class="sxs-lookup"><span data-stu-id="e8338-114">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="e8338-115">`Clear-RecycleBin` uppmanas användaren att bekräfta att alla pappers korgar tas bort från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e8338-115">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="e8338-116">2: Rensa en angiven pappers korg</span><span class="sxs-lookup"><span data-stu-id="e8338-116">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="e8338-117">I det här exemplet rensas pappers korgen för en angiven enhets beteckning.</span><span class="sxs-lookup"><span data-stu-id="e8338-117">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="e8338-118">`Clear-RecycleBin` använder parametern **DriveLetter** för att ange pappers korgen på **C** -volymen.</span><span class="sxs-lookup"><span data-stu-id="e8338-118">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="e8338-119">Användaren uppmanas att bekräfta att kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="e8338-119">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="e8338-120">3: Rensa alla pappers korgar utan bekräftelse</span><span class="sxs-lookup"><span data-stu-id="e8338-120">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="e8338-121">I det här exemplet visas ingen bekräftelse för att ta bort den lokala datorns pappers korg.</span><span class="sxs-lookup"><span data-stu-id="e8338-121">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="e8338-122">`Clear-RecycleBin` använder **Force** -parametern och uppmanas inte användaren att bekräfta att alla pappers korgar tas bort från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e8338-122">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="e8338-123">Ett alternativ är att ersätta `-Force` med `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="e8338-123">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="e8338-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e8338-124">PARAMETERS</span></span>

### <span data-ttu-id="e8338-125">-DriveLetter</span><span class="sxs-lookup"><span data-stu-id="e8338-125">-DriveLetter</span></span>

<span data-ttu-id="e8338-126">Anger pappers korgen för att rensa en enskild enhets beteckning eller en matris med enhets beteckningar.</span><span class="sxs-lookup"><span data-stu-id="e8338-126">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="e8338-127">-Force</span><span class="sxs-lookup"><span data-stu-id="e8338-127">-Force</span></span>

<span data-ttu-id="e8338-128">Anger att användaren inte behöver bekräfta att en pappers korgen ska rensas.</span><span class="sxs-lookup"><span data-stu-id="e8338-128">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="e8338-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e8338-129">-Confirm</span></span>

<span data-ttu-id="e8338-130">Uppmanas att bekräfta användaren innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e8338-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="e8338-131">Användaren uppmanas att bekräfta även om parametern **Confirm** inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="e8338-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="e8338-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e8338-132">-WhatIf</span></span>

<span data-ttu-id="e8338-133">Visar vad som händer om `Clear-RecycleBin` körs.</span><span class="sxs-lookup"><span data-stu-id="e8338-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="e8338-134">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e8338-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e8338-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8338-135">CommonParameters</span></span>

<span data-ttu-id="e8338-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8338-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8338-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e8338-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8338-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="e8338-138">INPUTS</span></span>

## <span data-ttu-id="e8338-139">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e8338-139">OUTPUTS</span></span>

### <span data-ttu-id="e8338-140">Inget</span><span class="sxs-lookup"><span data-stu-id="e8338-140">None</span></span>

## <span data-ttu-id="e8338-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e8338-141">NOTES</span></span>

## <span data-ttu-id="e8338-142">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e8338-142">RELATED LINKS</span></span>

