---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: 821b532dc44702af4243bf36ca7f5d4089a057d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264356"
---
# <span data-ttu-id="fba63-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="fba63-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="fba63-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fba63-104">SYNOPSIS</span></span>
<span data-ttu-id="fba63-105">Visar körnings utrymme fel söknings alternativ.</span><span class="sxs-lookup"><span data-stu-id="fba63-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="fba63-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fba63-106">SYNTAX</span></span>

### <span data-ttu-id="fba63-107">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="fba63-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="fba63-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="fba63-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="fba63-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="fba63-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="fba63-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="fba63-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="fba63-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="fba63-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="fba63-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fba63-112">DESCRIPTION</span></span>

<span data-ttu-id="fba63-113">`Get-RunspaceDebug`Cmdleten visar körnings utrymme fel söknings alternativ.</span><span class="sxs-lookup"><span data-stu-id="fba63-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="fba63-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fba63-114">EXAMPLES</span></span>

### <span data-ttu-id="fba63-115">1: Visa statusen för standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="fba63-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="fba63-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fba63-116">PARAMETERS</span></span>

### <span data-ttu-id="fba63-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="fba63-117">-AppDomainName</span></span>

<span data-ttu-id="fba63-118">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="fba63-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="fba63-119">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="fba63-119">-ProcessName</span></span>

<span data-ttu-id="fba63-120">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="fba63-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="fba63-121">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="fba63-121">-Runspace</span></span>

<span data-ttu-id="fba63-122">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="fba63-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="fba63-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="fba63-123">-RunspaceId</span></span>

<span data-ttu-id="fba63-124">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="fba63-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="fba63-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="fba63-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="fba63-126">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="fba63-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="fba63-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="fba63-127">-RunspaceName</span></span>

<span data-ttu-id="fba63-128">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="fba63-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="fba63-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fba63-129">CommonParameters</span></span>

<span data-ttu-id="fba63-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fba63-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fba63-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fba63-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fba63-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="fba63-132">INPUTS</span></span>

## <span data-ttu-id="fba63-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fba63-133">OUTPUTS</span></span>

## <span data-ttu-id="fba63-134">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fba63-134">NOTES</span></span>

## <span data-ttu-id="fba63-135">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fba63-135">RELATED LINKS</span></span>

[<span data-ttu-id="fba63-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="fba63-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="fba63-137">Aktivera – RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="fba63-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

