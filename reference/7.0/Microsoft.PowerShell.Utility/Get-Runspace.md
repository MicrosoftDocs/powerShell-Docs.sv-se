---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 7d2dc7ce170d3f5de15fe5ad289e664e9f11847b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262682"
---
# <span data-ttu-id="4bc1a-103">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="4bc1a-103">Get-Runspace</span></span>

## <span data-ttu-id="4bc1a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4bc1a-104">SYNOPSIS</span></span>
<span data-ttu-id="4bc1a-105">Hämtar aktiva körnings utrymmen i en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="4bc1a-105">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="4bc1a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4bc1a-106">SYNTAX</span></span>

### <span data-ttu-id="4bc1a-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="4bc1a-107">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="4bc1a-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="4bc1a-108">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="4bc1a-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="4bc1a-109">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="4bc1a-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4bc1a-110">DESCRIPTION</span></span>

<span data-ttu-id="4bc1a-111">`Get-Runspace`Cmdleten hämtar aktiva körnings utrymmen i en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="4bc1a-111">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="4bc1a-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4bc1a-112">EXAMPLES</span></span>

### <span data-ttu-id="4bc1a-113">Exempel 1: Hämta körnings utrymmen</span><span class="sxs-lookup"><span data-stu-id="4bc1a-113">Example 1: Get runspaces</span></span>

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

### <span data-ttu-id="4bc1a-114">Exempel 2: Hämta körnings utrymme efter ID</span><span class="sxs-lookup"><span data-stu-id="4bc1a-114">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="4bc1a-115">Exempel 3: Hämta körnings utrymme efter namn</span><span class="sxs-lookup"><span data-stu-id="4bc1a-115">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="4bc1a-116">Exempel 4: Hämta körnings utrymme av InstanceId</span><span class="sxs-lookup"><span data-stu-id="4bc1a-116">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="4bc1a-117">I det här exemplet identifierar vi en tillgänglig körnings utrymme med `Name` parametern och lagrar returvärdet till variabeln `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="4bc1a-117">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="4bc1a-118">På så sätt kan du använda egenskaperna för **körnings utrymme** i efterföljande körningar av `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="4bc1a-118">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="4bc1a-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4bc1a-119">PARAMETERS</span></span>

### <span data-ttu-id="4bc1a-120">-ID</span><span class="sxs-lookup"><span data-stu-id="4bc1a-120">-Id</span></span>

<span data-ttu-id="4bc1a-121">Anger ID för en körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="4bc1a-121">Specifies the Id of a runspace</span></span>

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

### <span data-ttu-id="4bc1a-122">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4bc1a-122">-InstanceId</span></span>

<span data-ttu-id="4bc1a-123">Anger instans-ID-GUID för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="4bc1a-123">Specifies the instance ID GUID of a running job.</span></span>

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

### <span data-ttu-id="4bc1a-124">-Name</span><span class="sxs-lookup"><span data-stu-id="4bc1a-124">-Name</span></span>

<span data-ttu-id="4bc1a-125">Anger namnet på en körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="4bc1a-125">Specifies the Name of a runspace</span></span>

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

### <span data-ttu-id="4bc1a-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4bc1a-126">CommonParameters</span></span>

<span data-ttu-id="4bc1a-127">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4bc1a-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4bc1a-128">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4bc1a-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4bc1a-129">INDATA</span><span class="sxs-lookup"><span data-stu-id="4bc1a-129">INPUTS</span></span>

## <span data-ttu-id="4bc1a-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4bc1a-130">OUTPUTS</span></span>

### <span data-ttu-id="4bc1a-131">System. Management. Automation. körnings utrymmen. körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="4bc1a-131">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="4bc1a-132">Du kan skicka vidare resultatet av ett `Get-Runspace` kommando till `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="4bc1a-132">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="4bc1a-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4bc1a-133">NOTES</span></span>

## <span data-ttu-id="4bc1a-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4bc1a-134">RELATED LINKS</span></span>

[<span data-ttu-id="4bc1a-135">Felsök – körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="4bc1a-135">Debug-Runspace</span></span>](Debug-Runspace.md)
