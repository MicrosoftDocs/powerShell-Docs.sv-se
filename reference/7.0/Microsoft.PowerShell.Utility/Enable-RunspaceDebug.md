---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: dc33195db1ddfb0c2b3e87aaab44845e9f6580a7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263222"
---
# <span data-ttu-id="8b41a-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8b41a-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="8b41a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8b41a-104">SYNOPSIS</span></span>
<span data-ttu-id="8b41a-105">Aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="8b41a-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="8b41a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b41a-106">SYNTAX</span></span>

### <span data-ttu-id="8b41a-107">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="8b41a-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8b41a-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="8b41a-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="8b41a-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="8b41a-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="8b41a-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="8b41a-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="8b41a-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="8b41a-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8b41a-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8b41a-112">DESCRIPTION</span></span>

<span data-ttu-id="8b41a-113">`Enable-RunspaceDebug`Cmdleten aktiverar fel sökning på körnings utrymmen där en Bryt punkt bevaras tills en fel sökare är ansluten.</span><span class="sxs-lookup"><span data-stu-id="8b41a-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="8b41a-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8b41a-114">EXAMPLES</span></span>

### <span data-ttu-id="8b41a-115">1: Aktivera standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="8b41a-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="8b41a-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8b41a-116">PARAMETERS</span></span>

### <span data-ttu-id="8b41a-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="8b41a-117">-AppDomainName</span></span>

<span data-ttu-id="8b41a-118">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="8b41a-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="8b41a-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="8b41a-119">-BreakAll</span></span>

<span data-ttu-id="8b41a-120">Gör att kommando-eller skript som körs i körnings utrymme kan stoppas i steg-läge, oavsett om en fel sökare för närvarande är ansluten eller inte.</span><span class="sxs-lookup"><span data-stu-id="8b41a-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="8b41a-121">Skriptet eller kommandot förblir stoppat tills en fel sökare är ansluten för att felsöka den aktuella stopp punkten.</span><span class="sxs-lookup"><span data-stu-id="8b41a-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

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

### <span data-ttu-id="8b41a-122">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="8b41a-122">-ProcessName</span></span>

<span data-ttu-id="8b41a-123">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="8b41a-123">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="8b41a-124">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="8b41a-124">-Runspace</span></span>

<span data-ttu-id="8b41a-125">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="8b41a-125">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="8b41a-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="8b41a-126">-RunspaceId</span></span>

<span data-ttu-id="8b41a-127">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="8b41a-127">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="8b41a-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="8b41a-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="8b41a-129">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="8b41a-129">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="8b41a-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="8b41a-130">-RunspaceName</span></span>

<span data-ttu-id="8b41a-131">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="8b41a-131">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="8b41a-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b41a-132">CommonParameters</span></span>

<span data-ttu-id="8b41a-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b41a-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b41a-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8b41a-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b41a-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="8b41a-135">INPUTS</span></span>

## <span data-ttu-id="8b41a-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8b41a-136">OUTPUTS</span></span>

## <span data-ttu-id="8b41a-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8b41a-137">NOTES</span></span>

## <span data-ttu-id="8b41a-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8b41a-138">RELATED LINKS</span></span>

[<span data-ttu-id="8b41a-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8b41a-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="8b41a-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8b41a-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)