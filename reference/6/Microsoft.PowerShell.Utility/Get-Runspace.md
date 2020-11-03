---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 12530b9cf30b34598dfc3a049f5553920abecc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267032"
---
# <span data-ttu-id="5a79f-103">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="5a79f-103">Get-Runspace</span></span>

## <span data-ttu-id="5a79f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5a79f-104">SYNOPSIS</span></span>
<span data-ttu-id="5a79f-105">Hämtar aktiva körnings utrymmen i en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="5a79f-105">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="5a79f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a79f-106">SYNTAX</span></span>

### <span data-ttu-id="5a79f-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="5a79f-107">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="5a79f-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a79f-108">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="5a79f-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a79f-109">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="5a79f-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5a79f-110">DESCRIPTION</span></span>

<span data-ttu-id="5a79f-111">`Get-Runspace`Cmdleten hämtar aktiva körnings utrymmen i en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="5a79f-111">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="5a79f-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5a79f-112">EXAMPLES</span></span>

### <span data-ttu-id="5a79f-113">Exempel 1: Hämta körnings utrymmen</span><span class="sxs-lookup"><span data-stu-id="5a79f-113">Example 1: Get runspaces</span></span>

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### <span data-ttu-id="5a79f-114">Exempel 2: Hämta körnings utrymme efter ID</span><span class="sxs-lookup"><span data-stu-id="5a79f-114">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="5a79f-115">Exempel 3: Hämta körnings utrymme efter namn</span><span class="sxs-lookup"><span data-stu-id="5a79f-115">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="5a79f-116">Exempel 4: Hämta körnings utrymme av InstanceId</span><span class="sxs-lookup"><span data-stu-id="5a79f-116">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="5a79f-117">I det här exemplet identifierar vi en tillgänglig körnings utrymme med `Name` parametern och lagrar returvärdet till variabeln `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="5a79f-117">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="5a79f-118">På så sätt kan du använda egenskaperna för **körnings utrymme** i efterföljande körningar av `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="5a79f-118">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="5a79f-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5a79f-119">PARAMETERS</span></span>

### <span data-ttu-id="5a79f-120">-ID</span><span class="sxs-lookup"><span data-stu-id="5a79f-120">-Id</span></span>

<span data-ttu-id="5a79f-121">Anger ID för en körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="5a79f-121">Specifies the Id of a runspace</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a79f-122">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="5a79f-122">-InstanceId</span></span>

<span data-ttu-id="5a79f-123">Anger instans-ID-GUID för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="5a79f-123">Specifies the instance ID GUID of a running job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a79f-124">-Name</span><span class="sxs-lookup"><span data-stu-id="5a79f-124">-Name</span></span>

<span data-ttu-id="5a79f-125">Anger namnet på en körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="5a79f-125">Specifies the Name of a runspace</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a79f-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a79f-126">CommonParameters</span></span>

<span data-ttu-id="5a79f-127">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a79f-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a79f-128">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5a79f-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a79f-129">INDATA</span><span class="sxs-lookup"><span data-stu-id="5a79f-129">INPUTS</span></span>

## <span data-ttu-id="5a79f-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5a79f-130">OUTPUTS</span></span>

### <span data-ttu-id="5a79f-131">System. Management. Automation. körnings utrymmen. körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="5a79f-131">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="5a79f-132">Du kan skicka vidare resultatet av ett `Get-Runspace` kommando till `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="5a79f-132">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="5a79f-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5a79f-133">NOTES</span></span>

## <span data-ttu-id="5a79f-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5a79f-134">RELATED LINKS</span></span>

[<span data-ttu-id="5a79f-135">Felsök – körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="5a79f-135">Debug-Runspace</span></span>](Debug-Runspace.md)
