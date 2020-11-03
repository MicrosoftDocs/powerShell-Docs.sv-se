---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 58665cd06e39784721be9a538b70dd8b7c2a1c14
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262521"
---
# <span data-ttu-id="57f8e-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="57f8e-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="57f8e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="57f8e-104">SYNOPSIS</span></span>
<span data-ttu-id="57f8e-105">Inaktiverar fel sökning på en eller flera körnings utrymmen och släpper eventuella väntande fel söknings program.</span><span class="sxs-lookup"><span data-stu-id="57f8e-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="57f8e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="57f8e-106">SYNTAX</span></span>

### <span data-ttu-id="57f8e-107">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="57f8e-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="57f8e-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="57f8e-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="57f8e-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="57f8e-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="57f8e-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="57f8e-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="57f8e-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="57f8e-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="57f8e-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="57f8e-112">DESCRIPTION</span></span>

<span data-ttu-id="57f8e-113">`Disable-RunspaceDebug`Cmdleten inaktiverar fel sökning på en eller flera körnings utrymmen och släpper eventuella väntande fel söknings program.</span><span class="sxs-lookup"><span data-stu-id="57f8e-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="57f8e-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="57f8e-114">EXAMPLES</span></span>

### <span data-ttu-id="57f8e-115">1: inaktivera standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="57f8e-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="57f8e-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="57f8e-116">PARAMETERS</span></span>

### <span data-ttu-id="57f8e-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="57f8e-117">-AppDomainName</span></span>

<span data-ttu-id="57f8e-118">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="57f8e-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="57f8e-119">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="57f8e-119">-ProcessName</span></span>

<span data-ttu-id="57f8e-120">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="57f8e-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="57f8e-121">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="57f8e-121">-Runspace</span></span>

<span data-ttu-id="57f8e-122">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="57f8e-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="57f8e-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="57f8e-123">-RunspaceId</span></span>

<span data-ttu-id="57f8e-124">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="57f8e-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="57f8e-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="57f8e-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="57f8e-126">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="57f8e-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="57f8e-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="57f8e-127">-RunspaceName</span></span>

<span data-ttu-id="57f8e-128">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="57f8e-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="57f8e-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57f8e-129">CommonParameters</span></span>

<span data-ttu-id="57f8e-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="57f8e-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="57f8e-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="57f8e-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="57f8e-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="57f8e-132">INPUTS</span></span>

## <span data-ttu-id="57f8e-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="57f8e-133">OUTPUTS</span></span>

## <span data-ttu-id="57f8e-134">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="57f8e-134">NOTES</span></span>

## <span data-ttu-id="57f8e-135">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="57f8e-135">RELATED LINKS</span></span>

[<span data-ttu-id="57f8e-136">Aktivera – RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="57f8e-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="57f8e-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="57f8e-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)