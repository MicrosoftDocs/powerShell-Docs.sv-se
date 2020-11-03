---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 54fb9500a924d2e5de98489fa4fb391accb23d0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265119"
---
# <span data-ttu-id="f0e66-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f0e66-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="f0e66-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f0e66-104">SYNOPSIS</span></span>
<span data-ttu-id="f0e66-105">Aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="f0e66-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="f0e66-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0e66-106">SYNTAX</span></span>

### <span data-ttu-id="f0e66-107">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f0e66-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f0e66-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0e66-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="f0e66-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0e66-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="f0e66-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0e66-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="f0e66-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0e66-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="f0e66-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f0e66-112">DESCRIPTION</span></span>

<span data-ttu-id="f0e66-113">`Enable-RunspaceDebug`Cmdleten aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="f0e66-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="f0e66-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f0e66-114">EXAMPLES</span></span>

### <span data-ttu-id="f0e66-115">1: Aktivera standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="f0e66-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="f0e66-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f0e66-116">PARAMETERS</span></span>

### <span data-ttu-id="f0e66-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="f0e66-117">-AppDomainName</span></span>

<span data-ttu-id="f0e66-118">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f0e66-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="f0e66-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="f0e66-119">-BreakAll</span></span>

<span data-ttu-id="f0e66-120">Gör att kommando-eller skript som körs i körnings utrymme kan stoppas i steg-läge, oavsett om en fel sökare för närvarande är ansluten eller inte.</span><span class="sxs-lookup"><span data-stu-id="f0e66-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="f0e66-121">Skriptet eller kommandot förblir stoppat tills en fel sökare är ansluten för att felsöka den aktuella stopp punkten.</span><span class="sxs-lookup"><span data-stu-id="f0e66-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

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

### <span data-ttu-id="f0e66-122">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="f0e66-122">-ProcessName</span></span>

<span data-ttu-id="f0e66-123">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f0e66-123">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="f0e66-124">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="f0e66-124">-Runspace</span></span>

<span data-ttu-id="f0e66-125">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="f0e66-125">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="f0e66-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="f0e66-126">-RunspaceId</span></span>

<span data-ttu-id="f0e66-127">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="f0e66-127">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="f0e66-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="f0e66-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="f0e66-129">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="f0e66-129">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="f0e66-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="f0e66-130">-RunspaceName</span></span>

<span data-ttu-id="f0e66-131">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="f0e66-131">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="f0e66-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0e66-132">CommonParameters</span></span>

<span data-ttu-id="f0e66-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0e66-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0e66-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0e66-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0e66-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="f0e66-135">INPUTS</span></span>

## <span data-ttu-id="f0e66-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f0e66-136">OUTPUTS</span></span>

## <span data-ttu-id="f0e66-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f0e66-137">NOTES</span></span>

## <span data-ttu-id="f0e66-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f0e66-138">RELATED LINKS</span></span>

[<span data-ttu-id="f0e66-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f0e66-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="f0e66-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f0e66-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
