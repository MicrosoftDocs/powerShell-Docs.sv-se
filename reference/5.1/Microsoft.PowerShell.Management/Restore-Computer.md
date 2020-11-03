---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265424"
---
# <span data-ttu-id="8ae02-103">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="8ae02-103">Restore-Computer</span></span>

## <span data-ttu-id="8ae02-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8ae02-104">SYNOPSIS</span></span>
<span data-ttu-id="8ae02-105">Startar en system återställning på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8ae02-105">Starts a system restore on the local computer.</span></span>

## <span data-ttu-id="8ae02-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ae02-106">SYNTAX</span></span>

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8ae02-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8ae02-107">DESCRIPTION</span></span>
<span data-ttu-id="8ae02-108">Cmdleten **restore-Computer** återställer den lokala datorn till den angivna system återställnings punkten.</span><span class="sxs-lookup"><span data-stu-id="8ae02-108">The **Restore-Computer** cmdlet restores the local computer to the specified system restore point.</span></span>

<span data-ttu-id="8ae02-109">**Restore-Computer** startar om datorn.</span><span class="sxs-lookup"><span data-stu-id="8ae02-109">**Restore-Computer** restarts the computer.</span></span>
<span data-ttu-id="8ae02-110">Återställningen slutförs under omstarten.</span><span class="sxs-lookup"><span data-stu-id="8ae02-110">The restore is completed during the restart operation.</span></span>

<span data-ttu-id="8ae02-111">System återställnings punkter och **återställning – datorn** stöds endast på klient operativ system, till exempel Windows 7, Windows Vista och Windows XP.</span><span class="sxs-lookup"><span data-stu-id="8ae02-111">System restore points and **Restore-Computer** are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="8ae02-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8ae02-112">EXAMPLES</span></span>

### <span data-ttu-id="8ae02-113">Exempel 1: Återställ den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="8ae02-113">Example 1: Restore the local computer</span></span>

```
PS C:\> Restore-Computer -RestorePoint 253
```

<span data-ttu-id="8ae02-114">Det här kommandot återställer den lokala datorn till återställnings punkten med sekvensnummer 253.</span><span class="sxs-lookup"><span data-stu-id="8ae02-114">This command restores the local computer to the restore point that has sequence number 253.</span></span>

### <span data-ttu-id="8ae02-115">Exempel 2: Återställ den lokala datorn med bekräftelse</span><span class="sxs-lookup"><span data-stu-id="8ae02-115">Example 2: Restore the local computer with confirmation</span></span>

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="8ae02-116">Det här kommandot återställer den lokala datorn till återställnings punkten med sekvensnummer 255.</span><span class="sxs-lookup"><span data-stu-id="8ae02-116">This command restores the local computer to the restore point that has sequence number 255.</span></span>
<span data-ttu-id="8ae02-117">Parametern *Confirm* används för att fråga användaren innan åtgärden utförs.</span><span class="sxs-lookup"><span data-stu-id="8ae02-117">It uses the *Confirm* parameter to prompt the user before actually performing the operation.</span></span>

### <span data-ttu-id="8ae02-118">Exempel 3: återställa en dator och kontrol lera statusen</span><span class="sxs-lookup"><span data-stu-id="8ae02-118">Example 3: Restore a computer and check the status</span></span>

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

<span data-ttu-id="8ae02-119">Kommandona kör en system återställning och kontrollerar sedan dess status.</span><span class="sxs-lookup"><span data-stu-id="8ae02-119">These commands run a system restore and then check its status.</span></span>

<span data-ttu-id="8ae02-120">Det första kommandot använder **Get-ComputerRestorePoint** för att hämta återställnings punkterna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8ae02-120">The first command uses **Get-ComputerRestorePoint** to get the restore points on the local computer.</span></span>

<span data-ttu-id="8ae02-121">Det andra kommandot återställer datorn till återställnings punkten med sekvensnumret 255.</span><span class="sxs-lookup"><span data-stu-id="8ae02-121">The second command restores the computer to the restore point with sequence number 255.</span></span>

<span data-ttu-id="8ae02-122">Det tredje kommandot använder parametern *LastStatus* för *Get-ComputerRestorePoint* -cmdlet: en för att kontrol lera status för återställnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8ae02-122">The third command uses the *LastStatus* parameter of *Get-ComputerRestorePoint* cmdlet to check the status of the restore operation.</span></span>
<span data-ttu-id="8ae02-123">Eftersom **restore-Computer** tvingar fram en omstart skulle det här kommandot anges efter att datorn startats om.</span><span class="sxs-lookup"><span data-stu-id="8ae02-123">Because **Restore-Computer** forces a restart, this command would be entered after the computer restarts.</span></span>

## <span data-ttu-id="8ae02-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8ae02-124">PARAMETERS</span></span>

### <span data-ttu-id="8ae02-125">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="8ae02-125">-RestorePoint</span></span>
<span data-ttu-id="8ae02-126">Anger återställnings punktens ordnings nummer.</span><span class="sxs-lookup"><span data-stu-id="8ae02-126">Specifies the sequence number of the restore point.</span></span>
<span data-ttu-id="8ae02-127">Använd Get-ComputerRestorePoint-cmdleten för att hitta sekvensnumret.</span><span class="sxs-lookup"><span data-stu-id="8ae02-127">To find the sequence number, use the Get-ComputerRestorePoint cmdlet.</span></span>
<span data-ttu-id="8ae02-128">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="8ae02-128">This parameter is required.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ae02-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8ae02-129">-Confirm</span></span>
<span data-ttu-id="8ae02-130">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8ae02-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8ae02-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8ae02-131">-WhatIf</span></span>
<span data-ttu-id="8ae02-132">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="8ae02-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8ae02-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="8ae02-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8ae02-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ae02-134">CommonParameters</span></span>
<span data-ttu-id="8ae02-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8ae02-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ae02-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8ae02-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ae02-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="8ae02-137">INPUTS</span></span>

### <span data-ttu-id="8ae02-138">Inget</span><span class="sxs-lookup"><span data-stu-id="8ae02-138">None</span></span>
<span data-ttu-id="8ae02-139">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ae02-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8ae02-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8ae02-140">OUTPUTS</span></span>

### <span data-ttu-id="8ae02-141">Inget</span><span class="sxs-lookup"><span data-stu-id="8ae02-141">None</span></span>
<span data-ttu-id="8ae02-142">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="8ae02-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8ae02-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8ae02-143">NOTES</span></span>

* <span data-ttu-id="8ae02-144">Om du vill köra ett Restore-Computer kommando i Windows Vista och senare versioner av Windows-operativsystemet öppnar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="8ae02-144">To run a Restore-Computer command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="8ae02-145">Denna cmdlet använder klassen Windows Management Instrumentation (WMI) **SystemRestore** .</span><span class="sxs-lookup"><span data-stu-id="8ae02-145">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

## <span data-ttu-id="8ae02-146">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8ae02-146">RELATED LINKS</span></span>

[<span data-ttu-id="8ae02-147">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="8ae02-147">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="8ae02-148">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="8ae02-148">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="8ae02-149">Aktivera – ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="8ae02-149">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="8ae02-150">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="8ae02-150">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="8ae02-151">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="8ae02-151">Restart-Computer</span></span>](Restart-Computer.md)
