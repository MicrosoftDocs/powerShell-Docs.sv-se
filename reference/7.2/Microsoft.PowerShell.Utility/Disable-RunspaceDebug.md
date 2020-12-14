---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 589c8cb36a91de510ffc30973fe70729700ad020
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709810"
---
# <span data-ttu-id="10b57-102">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="10b57-102">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="10b57-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="10b57-103">SYNOPSIS</span></span>
<span data-ttu-id="10b57-104">Inaktiverar fel sökning på en eller flera körnings utrymmen och släpper eventuella väntande fel söknings program.</span><span class="sxs-lookup"><span data-stu-id="10b57-104">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="10b57-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="10b57-105">SYNTAX</span></span>

### <span data-ttu-id="10b57-106">RunspaceNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="10b57-106">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="10b57-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="10b57-107">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="10b57-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="10b57-108">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="10b57-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="10b57-109">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="10b57-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="10b57-110">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="10b57-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="10b57-111">DESCRIPTION</span></span>

<span data-ttu-id="10b57-112">`Disable-RunspaceDebug`Cmdleten inaktiverar fel sökning på en eller flera körnings utrymmen och släpper eventuella väntande fel söknings program.</span><span class="sxs-lookup"><span data-stu-id="10b57-112">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="10b57-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="10b57-113">EXAMPLES</span></span>

### <span data-ttu-id="10b57-114">1: inaktivera standard körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="10b57-114">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="10b57-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="10b57-115">PARAMETERS</span></span>

### <span data-ttu-id="10b57-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="10b57-116">-AppDomainName</span></span>

<span data-ttu-id="10b57-117">Namnet på den program domän som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="10b57-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="10b57-118">– ProcessName</span><span class="sxs-lookup"><span data-stu-id="10b57-118">-ProcessName</span></span>

<span data-ttu-id="10b57-119">Namnet på processen som är värd för PowerShell-körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="10b57-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="10b57-120">– Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="10b57-120">-Runspace</span></span>

<span data-ttu-id="10b57-121">Ett eller flera **körnings utrymme** -objekt som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="10b57-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="10b57-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="10b57-122">-RunspaceId</span></span>

<span data-ttu-id="10b57-123">Ett eller flera **körnings utrymme** -ID-nummer som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="10b57-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="10b57-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="10b57-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="10b57-125">Ett eller flera **körnings utrymme** -GUID som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="10b57-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="10b57-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="10b57-126">-RunspaceName</span></span>

<span data-ttu-id="10b57-127">Ett eller flera **körnings utrymme** -namn måste inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="10b57-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="10b57-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10b57-128">CommonParameters</span></span>

<span data-ttu-id="10b57-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="10b57-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10b57-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="10b57-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10b57-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="10b57-131">INPUTS</span></span>

## <span data-ttu-id="10b57-132">UTDATA</span><span class="sxs-lookup"><span data-stu-id="10b57-132">OUTPUTS</span></span>

## <span data-ttu-id="10b57-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="10b57-133">NOTES</span></span>

## <span data-ttu-id="10b57-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="10b57-134">RELATED LINKS</span></span>

[<span data-ttu-id="10b57-135">Aktivera – RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="10b57-135">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="10b57-136">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="10b57-136">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

