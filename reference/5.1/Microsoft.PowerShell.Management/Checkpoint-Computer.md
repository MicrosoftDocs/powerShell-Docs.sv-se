---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266265"
---
# <span data-ttu-id="f71c6-103">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="f71c6-103">Checkpoint-Computer</span></span>

## <span data-ttu-id="f71c6-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f71c6-104">SYNOPSIS</span></span>
<span data-ttu-id="f71c6-105">Skapar en system återställnings punkt på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f71c6-105">Creates a system restore point on the local computer.</span></span>

## <span data-ttu-id="f71c6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f71c6-106">SYNTAX</span></span>

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## <span data-ttu-id="f71c6-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f71c6-107">DESCRIPTION</span></span>

<span data-ttu-id="f71c6-108">`Checkpoint-Computer`Cmdleten skapar en system återställnings punkt på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f71c6-108">The `Checkpoint-Computer` cmdlet creates a system restore point on the local computer.</span></span>

<span data-ttu-id="f71c6-109">System återställnings punkter och `Checkpoint-Computer` cmdlet stöds endast på klient operativ system, till exempel Windows 8, Windows 7, Windows Vista och Windows XP.</span><span class="sxs-lookup"><span data-stu-id="f71c6-109">System restore points and the `Checkpoint-Computer` cmdlet are supported only on client operating systems, such as Windows 8, Windows 7, Windows Vista, and Windows XP.</span></span>

<span data-ttu-id="f71c6-110">Från och med Windows 8 kan du `Checkpoint-Computer` inte skapa fler än en kontroll punkt varje dag.</span><span class="sxs-lookup"><span data-stu-id="f71c6-110">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one checkpoint each day.</span></span>

## <span data-ttu-id="f71c6-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f71c6-111">EXAMPLES</span></span>

### <span data-ttu-id="f71c6-112">Exempel 1: skapa en system återställnings punkt</span><span class="sxs-lookup"><span data-stu-id="f71c6-112">Example 1: Create a system restore point</span></span>

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

<span data-ttu-id="f71c6-113">Det här kommandot skapar en system återställnings punkt som kallas installera MyApp.</span><span class="sxs-lookup"><span data-stu-id="f71c6-113">This command creates a system restore point called Install MyApp.</span></span>
<span data-ttu-id="f71c6-114">Den använder standard typen för APPLICATION_INSTALL återställnings punkt.</span><span class="sxs-lookup"><span data-stu-id="f71c6-114">It uses the default APPLICATION_INSTALL restore point type.</span></span>

### <span data-ttu-id="f71c6-115">Exempel 2: skapa en återställnings punkt för system MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="f71c6-115">Example 2: Create a system MODIFY_SETTINGS restore point</span></span>

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

<span data-ttu-id="f71c6-116">Det här kommandot skapar en MODIFY_SETTINGS system återställnings punkt med namnet "ChangeNetSettings".</span><span class="sxs-lookup"><span data-stu-id="f71c6-116">This command creates a MODIFY_SETTINGS system restore point called "ChangeNetSettings".</span></span>

## <span data-ttu-id="f71c6-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f71c6-117">PARAMETERS</span></span>

### <span data-ttu-id="f71c6-118">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f71c6-118">-Description</span></span>

<span data-ttu-id="f71c6-119">Anger ett beskrivande namn för återställnings punkten.</span><span class="sxs-lookup"><span data-stu-id="f71c6-119">Specifies a descriptive name for the restore point.</span></span>
<span data-ttu-id="f71c6-120">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="f71c6-120">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f71c6-121">-RestorePointType</span><span class="sxs-lookup"><span data-stu-id="f71c6-121">-RestorePointType</span></span>

<span data-ttu-id="f71c6-122">Anger typen av återställnings punkt.</span><span class="sxs-lookup"><span data-stu-id="f71c6-122">Specifies the type of restore point.</span></span>
<span data-ttu-id="f71c6-123">Standardvärdet är APPLICATION_INSTALL.</span><span class="sxs-lookup"><span data-stu-id="f71c6-123">The default is APPLICATION_INSTALL.</span></span>

<span data-ttu-id="f71c6-124">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="f71c6-124">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f71c6-125">APPLICATION_INSTALL</span><span class="sxs-lookup"><span data-stu-id="f71c6-125">APPLICATION_INSTALL</span></span>
- <span data-ttu-id="f71c6-126">APPLICATION_UNINSTALL</span><span class="sxs-lookup"><span data-stu-id="f71c6-126">APPLICATION_UNINSTALL</span></span>
- <span data-ttu-id="f71c6-127">DEVICE_DRIVER_INSTALL</span><span class="sxs-lookup"><span data-stu-id="f71c6-127">DEVICE_DRIVER_INSTALL</span></span>
- <span data-ttu-id="f71c6-128">MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="f71c6-128">MODIFY_SETTINGS</span></span>
- <span data-ttu-id="f71c6-129">CANCELLED_OPERATION</span><span class="sxs-lookup"><span data-stu-id="f71c6-129">CANCELLED_OPERATION</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f71c6-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f71c6-130">CommonParameters</span></span>

<span data-ttu-id="f71c6-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f71c6-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f71c6-132">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="f71c6-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f71c6-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="f71c6-133">INPUTS</span></span>

### <span data-ttu-id="f71c6-134">Inget</span><span class="sxs-lookup"><span data-stu-id="f71c6-134">None</span></span>

<span data-ttu-id="f71c6-135">Det går inte att skicka pipe-objekt till `Checkpoint-Computer` .</span><span class="sxs-lookup"><span data-stu-id="f71c6-135">You cannot pipe objects to `Checkpoint-Computer`.</span></span>

## <span data-ttu-id="f71c6-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f71c6-136">OUTPUTS</span></span>

### <span data-ttu-id="f71c6-137">Inget</span><span class="sxs-lookup"><span data-stu-id="f71c6-137">None</span></span>

<span data-ttu-id="f71c6-138">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f71c6-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f71c6-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f71c6-139">NOTES</span></span>

- <span data-ttu-id="f71c6-140">Denna cmdlet använder **CreateRestorePoint** -metoden för **SystemRestore** -klassen med en **BEGIN_SYSTEM_CHANGE** -händelse.</span><span class="sxs-lookup"><span data-stu-id="f71c6-140">This cmdlet uses the **CreateRestorePoint** method of the **SystemRestore** class with a **BEGIN_SYSTEM_CHANGE** event.</span></span>
- <span data-ttu-id="f71c6-141">Från och med Windows 8 kan du `Checkpoint-Computer` inte skapa fler än en system återställnings punkt varje dag.</span><span class="sxs-lookup"><span data-stu-id="f71c6-141">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one system restore point each day.</span></span> <span data-ttu-id="f71c6-142">Om du försöker skapa en ny återställnings punkt innan 24-timmarsperiod har förflutit, genererar Windows PowerShell följande fel:</span><span class="sxs-lookup"><span data-stu-id="f71c6-142">If you try to create a new restore point before the 24-hour period has elapsed, Windows PowerShell generates the following error:</span></span>

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## <span data-ttu-id="f71c6-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f71c6-143">RELATED LINKS</span></span>

[<span data-ttu-id="f71c6-144">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="f71c6-144">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="f71c6-145">Aktivera – ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="f71c6-145">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="f71c6-146">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="f71c6-146">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="f71c6-147">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="f71c6-147">Restore-Computer</span></span>](Restore-Computer.md)
