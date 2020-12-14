---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710104"
---
# <span data-ttu-id="822b0-102">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="822b0-102">Get-RunspaceDebug</span></span>

## <span data-ttu-id="822b0-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="822b0-103">SYNOPSIS</span></span>
<span data-ttu-id="822b0-104">Visar körnings utrymme fel söknings alternativ.</span><span class="sxs-lookup"><span data-stu-id="822b0-104">Shows runspace debugging options.</span></span>

## <span data-ttu-id="822b0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="822b0-105">SYNTAX</span></span>

### <span data-ttu-id="822b0-106">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="822b0-106">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="822b0-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="822b0-107">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="822b0-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="822b0-108">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="822b0-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="822b0-109">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="822b0-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="822b0-110">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="822b0-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="822b0-111">DESCRIPTION</span></span>

<span data-ttu-id="822b0-112">`Get-RunspaceDebug`Cmdleten visar körnings utrymme fel söknings alternativ.</span><span class="sxs-lookup"><span data-stu-id="822b0-112">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="822b0-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="822b0-113">EXAMPLES</span></span>

### <span data-ttu-id="822b0-114">1: Visa statusen för standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="822b0-114">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="822b0-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="822b0-115">PARAMETERS</span></span>

### <span data-ttu-id="822b0-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="822b0-116">-AppDomainName</span></span>

<span data-ttu-id="822b0-117">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="822b0-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="822b0-118">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="822b0-118">-ProcessName</span></span>

<span data-ttu-id="822b0-119">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="822b0-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="822b0-120">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="822b0-120">-Runspace</span></span>

<span data-ttu-id="822b0-121">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="822b0-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="822b0-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="822b0-122">-RunspaceId</span></span>

<span data-ttu-id="822b0-123">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="822b0-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="822b0-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="822b0-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="822b0-125">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="822b0-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="822b0-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="822b0-126">-RunspaceName</span></span>

<span data-ttu-id="822b0-127">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="822b0-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="822b0-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="822b0-128">CommonParameters</span></span>

<span data-ttu-id="822b0-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="822b0-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="822b0-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="822b0-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="822b0-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="822b0-131">INPUTS</span></span>

## <span data-ttu-id="822b0-132">UTDATA</span><span class="sxs-lookup"><span data-stu-id="822b0-132">OUTPUTS</span></span>

## <span data-ttu-id="822b0-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="822b0-133">NOTES</span></span>

## <span data-ttu-id="822b0-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="822b0-134">RELATED LINKS</span></span>

[<span data-ttu-id="822b0-135">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="822b0-135">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="822b0-136">Aktivera – RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="822b0-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

