---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: 876ce5ff32863281ba9bc1ae94ece8b0a12c9efd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262400"
---
# <span data-ttu-id="8af3d-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="8af3d-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="8af3d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8af3d-104">SYNOPSIS</span></span>
<span data-ttu-id="8af3d-105">Hämtar ett konsoliderat objekt av system-och operativ system egenskaper.</span><span class="sxs-lookup"><span data-stu-id="8af3d-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="8af3d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8af3d-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8af3d-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8af3d-107">DESCRIPTION</span></span>

<span data-ttu-id="8af3d-108">`Get-ComputerInfo`Cmdlet: en hämtar ett konsoliderat objekt av system-och operativ system egenskaper.</span><span class="sxs-lookup"><span data-stu-id="8af3d-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="8af3d-109">Den här cmdleten introducerades i Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="8af3d-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="8af3d-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8af3d-110">EXAMPLES</span></span>

### <span data-ttu-id="8af3d-111">Exempel 1: Hämta alla dator egenskaper</span><span class="sxs-lookup"><span data-stu-id="8af3d-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="8af3d-112">Det här kommandot hämtar alla system-och operativ system egenskaper från datorn.</span><span class="sxs-lookup"><span data-stu-id="8af3d-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="8af3d-113">Exempel 2: Hämta alla egenskaper för datorns operativ system</span><span class="sxs-lookup"><span data-stu-id="8af3d-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="8af3d-114">Det här kommandot hämtar alla egenskaper för operativ systemet från datorn.</span><span class="sxs-lookup"><span data-stu-id="8af3d-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="8af3d-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8af3d-115">PARAMETERS</span></span>

### <span data-ttu-id="8af3d-116">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="8af3d-116">-Property</span></span>

<span data-ttu-id="8af3d-117">Anger, som en sträng mat ris, de dator egenskaper som denna cmdlet visar.</span><span class="sxs-lookup"><span data-stu-id="8af3d-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8af3d-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8af3d-118">CommonParameters</span></span>

<span data-ttu-id="8af3d-119">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8af3d-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8af3d-120">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="8af3d-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8af3d-121">INDATA</span><span class="sxs-lookup"><span data-stu-id="8af3d-121">INPUTS</span></span>

### <span data-ttu-id="8af3d-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="8af3d-122">System.String[]</span></span>

## <span data-ttu-id="8af3d-123">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8af3d-123">OUTPUTS</span></span>

### <span data-ttu-id="8af3d-124">Microsoft. PowerShell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="8af3d-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="8af3d-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8af3d-125">NOTES</span></span>

## <span data-ttu-id="8af3d-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8af3d-126">RELATED LINKS</span></span>
