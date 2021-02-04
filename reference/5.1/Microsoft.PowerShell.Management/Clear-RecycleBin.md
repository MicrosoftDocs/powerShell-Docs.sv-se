---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: f59cc9ff4e6d1b6579292c84f440bbbdd156b65c
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098571"
---
# <span data-ttu-id="834a2-102">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="834a2-102">Clear-RecycleBin</span></span>

## <span data-ttu-id="834a2-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="834a2-103">SYNOPSIS</span></span>
<span data-ttu-id="834a2-104">Rensar innehållet i en pappers korg.</span><span class="sxs-lookup"><span data-stu-id="834a2-104">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="834a2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="834a2-105">SYNTAX</span></span>

### <span data-ttu-id="834a2-106">Alla</span><span class="sxs-lookup"><span data-stu-id="834a2-106">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="834a2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="834a2-107">DESCRIPTION</span></span>

<span data-ttu-id="834a2-108">`Clear-RecycleBin`Cmdleten tar bort innehållet i en dators pappers korg.</span><span class="sxs-lookup"><span data-stu-id="834a2-108">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="834a2-109">Den här åtgärden påminner om att använda Windows **tomt Pappers korgen**.</span><span class="sxs-lookup"><span data-stu-id="834a2-109">This action is like using Windows **Empty Recycle Bin**.</span></span>

## <span data-ttu-id="834a2-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="834a2-110">EXAMPLES</span></span>

### <span data-ttu-id="834a2-111">1: Rensa alla pappers korgar</span><span class="sxs-lookup"><span data-stu-id="834a2-111">1: Clear all recycle bins</span></span>

<span data-ttu-id="834a2-112">I det här exemplet rensas alla lokala datorer i pappers korgen.</span><span class="sxs-lookup"><span data-stu-id="834a2-112">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="834a2-113">`Clear-RecycleBin` uppmanas användaren att bekräfta att alla pappers korgar tas bort från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="834a2-113">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="834a2-114">2: Rensa en angiven pappers korg</span><span class="sxs-lookup"><span data-stu-id="834a2-114">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="834a2-115">I det här exemplet rensas pappers korgen för en angiven enhets beteckning.</span><span class="sxs-lookup"><span data-stu-id="834a2-115">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="834a2-116">`Clear-RecycleBin` använder parametern **DriveLetter** för att ange pappers korgen på **C** -volymen.</span><span class="sxs-lookup"><span data-stu-id="834a2-116">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="834a2-117">Användaren uppmanas att bekräfta att kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="834a2-117">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="834a2-118">3: Rensa alla pappers korgar utan bekräftelse</span><span class="sxs-lookup"><span data-stu-id="834a2-118">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="834a2-119">I det här exemplet visas ingen bekräftelse för att ta bort den lokala datorns pappers korg.</span><span class="sxs-lookup"><span data-stu-id="834a2-119">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="834a2-120">`Clear-RecycleBin` använder **Force** -parametern och uppmanas inte användaren att bekräfta att alla pappers korgar tas bort från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="834a2-120">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="834a2-121">Ett alternativ är att ersätta `-Force` med `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="834a2-121">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="834a2-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="834a2-122">PARAMETERS</span></span>

### <span data-ttu-id="834a2-123">-DriveLetter</span><span class="sxs-lookup"><span data-stu-id="834a2-123">-DriveLetter</span></span>

<span data-ttu-id="834a2-124">Anger pappers korgen för att rensa en enskild enhets beteckning eller en matris med enhets beteckningar.</span><span class="sxs-lookup"><span data-stu-id="834a2-124">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="834a2-125">-Force</span><span class="sxs-lookup"><span data-stu-id="834a2-125">-Force</span></span>

<span data-ttu-id="834a2-126">Anger att användaren inte behöver bekräfta att en pappers korgen ska rensas.</span><span class="sxs-lookup"><span data-stu-id="834a2-126">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span> <span data-ttu-id="834a2-127">Parametern **Force** åsidosätter också parametrarna **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="834a2-127">The **Force** parameter also overrides the **WhatIf** and **Confirm** parameters.</span></span>

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

### <span data-ttu-id="834a2-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="834a2-128">-Confirm</span></span>

<span data-ttu-id="834a2-129">Uppmanas att bekräfta användaren innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="834a2-129">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="834a2-130">Användaren uppmanas att bekräfta även om parametern **Confirm** inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="834a2-130">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="834a2-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="834a2-131">-WhatIf</span></span>

<span data-ttu-id="834a2-132">Visar vad som händer om `Clear-RecycleBin` körs.</span><span class="sxs-lookup"><span data-stu-id="834a2-132">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="834a2-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="834a2-133">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="834a2-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="834a2-134">CommonParameters</span></span>

<span data-ttu-id="834a2-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="834a2-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="834a2-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="834a2-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="834a2-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="834a2-137">INPUTS</span></span>

## <span data-ttu-id="834a2-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="834a2-138">OUTPUTS</span></span>

### <span data-ttu-id="834a2-139">Inget</span><span class="sxs-lookup"><span data-stu-id="834a2-139">None</span></span>

## <span data-ttu-id="834a2-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="834a2-140">NOTES</span></span>

## <span data-ttu-id="834a2-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="834a2-141">RELATED LINKS</span></span>
