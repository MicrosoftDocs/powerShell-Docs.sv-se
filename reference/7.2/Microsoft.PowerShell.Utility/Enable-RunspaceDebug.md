---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 26ab9b9135eedafa0238eab5c07aa7abb7880ed4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709798"
---
# <span data-ttu-id="15f9c-102">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="15f9c-102">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="15f9c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="15f9c-103">SYNOPSIS</span></span>
<span data-ttu-id="15f9c-104">Aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="15f9c-104">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="15f9c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15f9c-105">SYNTAX</span></span>

### <span data-ttu-id="15f9c-106">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="15f9c-106">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="15f9c-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="15f9c-107">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="15f9c-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="15f9c-108">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="15f9c-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="15f9c-109">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="15f9c-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="15f9c-110">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="15f9c-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="15f9c-111">DESCRIPTION</span></span>

<span data-ttu-id="15f9c-112">`Enable-RunspaceDebug`Cmdleten aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="15f9c-112">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="15f9c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="15f9c-113">EXAMPLES</span></span>

### <span data-ttu-id="15f9c-114">1: Aktivera standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="15f9c-114">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="15f9c-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="15f9c-115">PARAMETERS</span></span>

### <span data-ttu-id="15f9c-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="15f9c-116">-AppDomainName</span></span>

<span data-ttu-id="15f9c-117">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="15f9c-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="15f9c-118">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="15f9c-118">-BreakAll</span></span>

<span data-ttu-id="15f9c-119">Gör att kommando-eller skript som körs i körnings utrymme kan stoppas i steg-läge, oavsett om en fel sökare för närvarande är ansluten eller inte.</span><span class="sxs-lookup"><span data-stu-id="15f9c-119">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="15f9c-120">Skriptet eller kommandot förblir stoppat tills en fel sökare är ansluten för att felsöka den aktuella stopp punkten.</span><span class="sxs-lookup"><span data-stu-id="15f9c-120">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

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

### <span data-ttu-id="15f9c-121">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="15f9c-121">-ProcessName</span></span>

<span data-ttu-id="15f9c-122">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="15f9c-122">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="15f9c-123">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="15f9c-123">-Runspace</span></span>

<span data-ttu-id="15f9c-124">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="15f9c-124">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="15f9c-125">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="15f9c-125">-RunspaceId</span></span>

<span data-ttu-id="15f9c-126">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="15f9c-126">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="15f9c-127">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="15f9c-127">-RunspaceInstanceId</span></span>

<span data-ttu-id="15f9c-128">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="15f9c-128">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="15f9c-129">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="15f9c-129">-RunspaceName</span></span>

<span data-ttu-id="15f9c-130">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="15f9c-130">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="15f9c-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15f9c-131">CommonParameters</span></span>

<span data-ttu-id="15f9c-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15f9c-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15f9c-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="15f9c-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15f9c-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="15f9c-134">INPUTS</span></span>

## <span data-ttu-id="15f9c-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="15f9c-135">OUTPUTS</span></span>

## <span data-ttu-id="15f9c-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="15f9c-136">NOTES</span></span>

## <span data-ttu-id="15f9c-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="15f9c-137">RELATED LINKS</span></span>

[<span data-ttu-id="15f9c-138">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="15f9c-138">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="15f9c-139">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="15f9c-139">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

