---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: e89efb5363df5843e536a9c58db331291c07b7b0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266439"
---
# <span data-ttu-id="3e5ff-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3e5ff-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="3e5ff-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3e5ff-104">SYNOPSIS</span></span>
<span data-ttu-id="3e5ff-105">Aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="3e5ff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e5ff-106">SYNTAX</span></span>

### <span data-ttu-id="3e5ff-107">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="3e5ff-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3e5ff-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="3e5ff-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="3e5ff-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3e5ff-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="3e5ff-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3e5ff-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="3e5ff-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3e5ff-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="3e5ff-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3e5ff-112">DESCRIPTION</span></span>

<span data-ttu-id="3e5ff-113">`Enable-RunspaceDebug`Cmdleten aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="3e5ff-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3e5ff-114">EXAMPLES</span></span>

### <span data-ttu-id="3e5ff-115">1: Aktivera standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="3e5ff-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="3e5ff-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3e5ff-116">PARAMETERS</span></span>

### <span data-ttu-id="3e5ff-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="3e5ff-117">-AppDomainName</span></span>

<span data-ttu-id="3e5ff-118">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="3e5ff-119">-BreakAll</span></span>

<span data-ttu-id="3e5ff-120">Gör att kommando-eller skript som körs i körnings utrymme kan stoppas i steg-läge, oavsett om en fel sökare för närvarande är ansluten eller inte.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="3e5ff-121">Skriptet eller kommandot förblir stoppat tills en fel sökare är ansluten för att felsöka den aktuella stopp punkten.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-122">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="3e5ff-122">-ProcessName</span></span>

<span data-ttu-id="3e5ff-123">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-123">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-124">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="3e5ff-124">-Runspace</span></span>

<span data-ttu-id="3e5ff-125">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-125">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="3e5ff-126">-RunspaceId</span></span>

<span data-ttu-id="3e5ff-127">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-127">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="3e5ff-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="3e5ff-129">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-129">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="3e5ff-130">-RunspaceName</span></span>

<span data-ttu-id="3e5ff-131">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-131">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e5ff-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e5ff-132">CommonParameters</span></span>

<span data-ttu-id="3e5ff-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e5ff-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e5ff-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3e5ff-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e5ff-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="3e5ff-135">INPUTS</span></span>

## <span data-ttu-id="3e5ff-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3e5ff-136">OUTPUTS</span></span>

## <span data-ttu-id="3e5ff-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3e5ff-137">NOTES</span></span>

## <span data-ttu-id="3e5ff-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3e5ff-138">RELATED LINKS</span></span>

[<span data-ttu-id="3e5ff-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3e5ff-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="3e5ff-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3e5ff-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

