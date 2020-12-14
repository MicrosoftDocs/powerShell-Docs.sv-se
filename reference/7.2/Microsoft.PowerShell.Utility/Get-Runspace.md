---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 34843894cb6253e3d8e89072cf79cb9237d4fc19
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710110"
---
# <span data-ttu-id="eae7c-102">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="eae7c-102">Get-Runspace</span></span>

## <span data-ttu-id="eae7c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eae7c-103">SYNOPSIS</span></span>
<span data-ttu-id="eae7c-104">Hämtar aktiva körnings utrymmen i en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="eae7c-104">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="eae7c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eae7c-105">SYNTAX</span></span>

### <span data-ttu-id="eae7c-106">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="eae7c-106">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="eae7c-107">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="eae7c-107">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="eae7c-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="eae7c-108">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="eae7c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eae7c-109">DESCRIPTION</span></span>

<span data-ttu-id="eae7c-110">`Get-Runspace`Cmdleten hämtar aktiva körnings utrymmen i en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="eae7c-110">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="eae7c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eae7c-111">EXAMPLES</span></span>

### <span data-ttu-id="eae7c-112">Exempel 1: Hämta körnings utrymmen</span><span class="sxs-lookup"><span data-stu-id="eae7c-112">Example 1: Get runspaces</span></span>

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

### <span data-ttu-id="eae7c-113">Exempel 2: Hämta körnings utrymme efter ID</span><span class="sxs-lookup"><span data-stu-id="eae7c-113">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="eae7c-114">Exempel 3: Hämta körnings utrymme efter namn</span><span class="sxs-lookup"><span data-stu-id="eae7c-114">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="eae7c-115">Exempel 4: Hämta körnings utrymme av InstanceId</span><span class="sxs-lookup"><span data-stu-id="eae7c-115">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="eae7c-116">I det här exemplet identifierar vi en tillgänglig körnings utrymme med `Name` parametern och lagrar returvärdet till variabeln `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="eae7c-116">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="eae7c-117">På så sätt kan du använda egenskaperna för **körnings utrymme** i efterföljande körningar av `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="eae7c-117">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="eae7c-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eae7c-118">PARAMETERS</span></span>

### <span data-ttu-id="eae7c-119">-ID</span><span class="sxs-lookup"><span data-stu-id="eae7c-119">-Id</span></span>

<span data-ttu-id="eae7c-120">Anger ID för en körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="eae7c-120">Specifies the Id of a runspace</span></span>

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

### <span data-ttu-id="eae7c-121">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="eae7c-121">-InstanceId</span></span>

<span data-ttu-id="eae7c-122">Anger instans-ID-GUID för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="eae7c-122">Specifies the instance ID GUID of a running job.</span></span>

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

### <span data-ttu-id="eae7c-123">-Name</span><span class="sxs-lookup"><span data-stu-id="eae7c-123">-Name</span></span>

<span data-ttu-id="eae7c-124">Anger namnet på en körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="eae7c-124">Specifies the Name of a runspace</span></span>

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

### <span data-ttu-id="eae7c-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eae7c-125">CommonParameters</span></span>

<span data-ttu-id="eae7c-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eae7c-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eae7c-127">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eae7c-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eae7c-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="eae7c-128">INPUTS</span></span>

## <span data-ttu-id="eae7c-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eae7c-129">OUTPUTS</span></span>

### <span data-ttu-id="eae7c-130">System. Management. Automation. körnings utrymmen. körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="eae7c-130">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="eae7c-131">Du kan skicka vidare resultatet av ett `Get-Runspace` kommando till `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="eae7c-131">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="eae7c-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eae7c-132">NOTES</span></span>

## <span data-ttu-id="eae7c-133">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eae7c-133">RELATED LINKS</span></span>

[<span data-ttu-id="eae7c-134">Felsök – körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="eae7c-134">Debug-Runspace</span></span>](Debug-Runspace.md)

