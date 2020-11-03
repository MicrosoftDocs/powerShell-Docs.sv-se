---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266180"
---
# <span data-ttu-id="848e5-103">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="848e5-103">Enable-ComputerRestore</span></span>

## <span data-ttu-id="848e5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="848e5-104">SYNOPSIS</span></span>
<span data-ttu-id="848e5-105">Aktiverar funktionen system återställning på den angivna fil system enheten.</span><span class="sxs-lookup"><span data-stu-id="848e5-105">Enables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="848e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="848e5-106">SYNTAX</span></span>

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="848e5-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="848e5-107">DESCRIPTION</span></span>
<span data-ttu-id="848e5-108">Cmdlet **: en Enable-ComputerRestore** aktiverar system återställnings funktionen på en eller flera fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="848e5-108">The **Enable-ComputerRestore** cmdlet turns on the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="848e5-109">Därför kan du använda verktyg som Restore-Computer-cmdlet för att återställa datorn till ett tidigare tillstånd.</span><span class="sxs-lookup"><span data-stu-id="848e5-109">As a result, you can use tools, such as the Restore-Computer cmdlet, to restore the computer to a previous state.</span></span>

<span data-ttu-id="848e5-110">Som standard aktive ras system återställning på alla kvalificerade enheter, men du kan inaktivera det, till exempel genom att använda Disable-ComputerRestore-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="848e5-110">By default, System Restore is enabled on all eligible drives, but you can disable it, such as by using the Disable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="848e5-111">Om du vill aktivera (eller återaktivera) system återställning på valfri enhet måste den vara aktive rad på system enheten, antingen första eller samtidigt.</span><span class="sxs-lookup"><span data-stu-id="848e5-111">To enable (or re-enable) System Restore on any drive, it must be enabled on the system drive, either first or concurrently.</span></span>
<span data-ttu-id="848e5-112">Använd Rstrui.exe för att hitta status för system återställning för varje enhet.</span><span class="sxs-lookup"><span data-stu-id="848e5-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="848e5-113">System återställnings punkter och ComputerRestore-cmdlets stöds endast på klient operativ system, till exempel Windows 7, Windows Vista och Windows XP.</span><span class="sxs-lookup"><span data-stu-id="848e5-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="848e5-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="848e5-114">EXAMPLES</span></span>

### <span data-ttu-id="848e5-115">Exempel 1: Aktivera system återställning på den angivna enheten</span><span class="sxs-lookup"><span data-stu-id="848e5-115">Example 1: Enable System Restore on the specified drive</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="848e5-116">Det här kommandot aktiverar system återställning på enhet C: på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="848e5-116">This command enables System Restore on the C: drive of the local computer.</span></span>

### <span data-ttu-id="848e5-117">Exempel 2: Aktivera system återställning på flera enheter</span><span class="sxs-lookup"><span data-stu-id="848e5-117">Example 2: Enable System Restore on multiple drives</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

<span data-ttu-id="848e5-118">Det här kommandot aktiverar system återställning på enhetarna C: och D: på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="848e5-118">This command enables System Restore on the C: and D: drives of the local computer.</span></span>

## <span data-ttu-id="848e5-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="848e5-119">PARAMETERS</span></span>

### <span data-ttu-id="848e5-120">– Enhet</span><span class="sxs-lookup"><span data-stu-id="848e5-120">-Drive</span></span>
<span data-ttu-id="848e5-121">Anger fil systemets enheter.</span><span class="sxs-lookup"><span data-stu-id="848e5-121">Specifies the file system drives.</span></span>
<span data-ttu-id="848e5-122">Ange en eller flera enhets beteckningar för fil systemet, varje följt av ett kolon och ett omvänt snedstreck som omges av citat tecken, t. ex. C:\ eller D:\.</span><span class="sxs-lookup"><span data-stu-id="848e5-122">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="848e5-123">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="848e5-123">This parameter is required.</span></span>

<span data-ttu-id="848e5-124">Du kan inte använda denna cmdlet för att aktivera system återställning på en fjärran sluten nätverks enhet, även om enheten är mappad till den lokala datorn och du inte kan aktivera system återställning på enheter som inte är berättigade till system återställning, t. ex. externa enheter.</span><span class="sxs-lookup"><span data-stu-id="848e5-124">You cannot use this cmdlet to enable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot enable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="848e5-125">Om du vill aktivera system återställning på valfri enhet måste system återställning vara aktiverat på system enheten, antingen före eller samtidigt.</span><span class="sxs-lookup"><span data-stu-id="848e5-125">To enable System Restore on any drive, System Restore must be enabled on the system drive, either before or concurrently.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="848e5-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="848e5-126">-Confirm</span></span>
<span data-ttu-id="848e5-127">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="848e5-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="848e5-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="848e5-128">-WhatIf</span></span>
<span data-ttu-id="848e5-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="848e5-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="848e5-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="848e5-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="848e5-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="848e5-131">CommonParameters</span></span>
<span data-ttu-id="848e5-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="848e5-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="848e5-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="848e5-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="848e5-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="848e5-134">INPUTS</span></span>

### <span data-ttu-id="848e5-135">Inget</span><span class="sxs-lookup"><span data-stu-id="848e5-135">None</span></span>
<span data-ttu-id="848e5-136">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="848e5-136">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="848e5-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="848e5-137">OUTPUTS</span></span>

### <span data-ttu-id="848e5-138">Inget</span><span class="sxs-lookup"><span data-stu-id="848e5-138">None</span></span>
<span data-ttu-id="848e5-139">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="848e5-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="848e5-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="848e5-140">NOTES</span></span>

* <span data-ttu-id="848e5-141">Om du vill köra denna cmdlet på Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="848e5-141">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="848e5-142">Om du vill hitta de fil system enheter som är kvalificerade för system återställning går du till fliken System skydd i system på kontroll panelen. Om du vill öppna den här fliken i Windows PowerShell skriver du `SystemPropertiesProtection` .</span><span class="sxs-lookup"><span data-stu-id="848e5-142">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="848e5-143">Denna cmdlet använder klassen Windows Management Instrumentation (WMI) **SystemRestore** .</span><span class="sxs-lookup"><span data-stu-id="848e5-143">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="848e5-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="848e5-144">RELATED LINKS</span></span>

[<span data-ttu-id="848e5-145">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="848e5-145">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="848e5-146">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="848e5-146">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="848e5-147">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="848e5-147">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="848e5-148">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="848e5-148">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="848e5-149">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="848e5-149">Restore-Computer</span></span>](Restore-Computer.md)
