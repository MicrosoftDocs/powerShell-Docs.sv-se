---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266181"
---
# <span data-ttu-id="caf34-103">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="caf34-103">Disable-ComputerRestore</span></span>

## <span data-ttu-id="caf34-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="caf34-104">SYNOPSIS</span></span>
<span data-ttu-id="caf34-105">Inaktiverar funktionen system återställning på den angivna fil system enheten.</span><span class="sxs-lookup"><span data-stu-id="caf34-105">Disables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="caf34-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="caf34-106">SYNTAX</span></span>

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="caf34-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="caf34-107">DESCRIPTION</span></span>
<span data-ttu-id="caf34-108">Cmdlet **: en Disable-ComputerRestore** inaktiverar funktionen system återställning på en eller flera fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="caf34-108">The **Disable-ComputerRestore** cmdlet turns off the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="caf34-109">Det innebär att försök att återställa datorn inte påverkar den angivna enheten.</span><span class="sxs-lookup"><span data-stu-id="caf34-109">As a result, attempts to restore the computer do not affect the specified drive.</span></span>

<span data-ttu-id="caf34-110">Om du vill inaktivera system återställning på en enhet måste den vara inaktive rad på system enheten, antingen först eller samtidigt.</span><span class="sxs-lookup"><span data-stu-id="caf34-110">To disable System Restore on any drive, it must be disabled on the system drive, either first or concurrently.</span></span>

<span data-ttu-id="caf34-111">Använd Enable-ComputerRestore-cmdleten om du vill återaktivera system återställning.</span><span class="sxs-lookup"><span data-stu-id="caf34-111">To re-enable System Restore, use the Enable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="caf34-112">Använd Rstrui.exe för att hitta status för system återställning för varje enhet.</span><span class="sxs-lookup"><span data-stu-id="caf34-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="caf34-113">System återställnings punkter och ComputerRestore-cmdlets stöds endast på klient operativ system, till exempel Windows 7, Windows Vista och Windows XP.</span><span class="sxs-lookup"><span data-stu-id="caf34-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="caf34-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="caf34-114">EXAMPLES</span></span>

### <span data-ttu-id="caf34-115">Exempel 1: inaktivera system återställning på den angivna enheten</span><span class="sxs-lookup"><span data-stu-id="caf34-115">Example 1: Disable System Restore on the specified drive</span></span>

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="caf34-116">Detta kommando inaktiverar system återställning på enheten C:.</span><span class="sxs-lookup"><span data-stu-id="caf34-116">This command disables System Restore on the C: drive.</span></span>

### <span data-ttu-id="caf34-117">Exempel 2: inaktivera system återställning på flera enheter</span><span class="sxs-lookup"><span data-stu-id="caf34-117">Example 2: Disable System Restore on multiple drives</span></span>

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

<span data-ttu-id="caf34-118">Detta kommando inaktiverar system återställning på enheterna C: och D:.</span><span class="sxs-lookup"><span data-stu-id="caf34-118">This command disables System Restore on the C: and D: drives.</span></span>
<span data-ttu-id="caf34-119">Kommandot använder *enhets* parametern, men utelämnar enhets parameterns namn.</span><span class="sxs-lookup"><span data-stu-id="caf34-119">The command uses the *Drive* parameter, but it omits the Drive parameter name.</span></span>

## <span data-ttu-id="caf34-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="caf34-120">PARAMETERS</span></span>

### <span data-ttu-id="caf34-121">– Enhet</span><span class="sxs-lookup"><span data-stu-id="caf34-121">-Drive</span></span>
<span data-ttu-id="caf34-122">Anger fil systemets enheter.</span><span class="sxs-lookup"><span data-stu-id="caf34-122">Specifies the file system drives.</span></span>
<span data-ttu-id="caf34-123">Ange en eller flera enhets beteckningar för fil systemet, varje följt av ett kolon och ett omvänt snedstreck som omges av citat tecken, t. ex. C:\ eller D:\.</span><span class="sxs-lookup"><span data-stu-id="caf34-123">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="caf34-124">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="caf34-124">This parameter is required.</span></span>

<span data-ttu-id="caf34-125">Du kan inte använda denna cmdlet för att inaktivera system återställning på en fjärran sluten nätverks enhet, även om enheten är mappad till den lokala datorn och du inte kan inaktivera system återställning på enheter som inte är berättigade till system återställning, till exempel externa enheter.</span><span class="sxs-lookup"><span data-stu-id="caf34-125">You cannot use this cmdlet to disable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot disable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="caf34-126">Om du vill inaktivera system återställning på någon enhet måste system återställning vara inaktiverat på system enheten, antingen före eller samtidigt.</span><span class="sxs-lookup"><span data-stu-id="caf34-126">To disable System Restore on any drive, System Restore must be disabled on the system drive, either before or concurrently.</span></span>

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

### <span data-ttu-id="caf34-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="caf34-127">-Confirm</span></span>
<span data-ttu-id="caf34-128">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="caf34-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="caf34-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="caf34-129">-WhatIf</span></span>
<span data-ttu-id="caf34-130">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="caf34-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="caf34-131">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="caf34-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="caf34-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="caf34-132">CommonParameters</span></span>
<span data-ttu-id="caf34-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="caf34-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="caf34-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="caf34-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="caf34-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="caf34-135">INPUTS</span></span>

### <span data-ttu-id="caf34-136">Inget</span><span class="sxs-lookup"><span data-stu-id="caf34-136">None</span></span>
<span data-ttu-id="caf34-137">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="caf34-137">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="caf34-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="caf34-138">OUTPUTS</span></span>

### <span data-ttu-id="caf34-139">Inget</span><span class="sxs-lookup"><span data-stu-id="caf34-139">None</span></span>
<span data-ttu-id="caf34-140">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="caf34-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="caf34-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="caf34-141">NOTES</span></span>

* <span data-ttu-id="caf34-142">Om du vill köra denna cmdlet på Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="caf34-142">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="caf34-143">Om du vill hitta de fil system enheter som är kvalificerade för system återställning går du till fliken System skydd i system på kontroll panelen. Om du vill öppna den här fliken i Windows PowerShell skriver du `SystemPropertiesProtection` .</span><span class="sxs-lookup"><span data-stu-id="caf34-143">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="caf34-144">Denna cmdlet använder klassen Windows Management Instrumentation (WMI) **SystemRestore** .</span><span class="sxs-lookup"><span data-stu-id="caf34-144">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="caf34-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="caf34-145">RELATED LINKS</span></span>

[<span data-ttu-id="caf34-146">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="caf34-146">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="caf34-147">Aktivera – ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="caf34-147">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="caf34-148">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="caf34-148">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="caf34-149">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="caf34-149">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="caf34-150">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="caf34-150">Restore-Computer</span></span>](Restore-Computer.md)
