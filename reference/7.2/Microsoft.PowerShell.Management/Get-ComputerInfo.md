---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: abc820bd6f8f5c8cd8c6301aacee268c82161d7e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710440"
---
# <span data-ttu-id="3b1d1-102">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="3b1d1-102">Get-ComputerInfo</span></span>

## <span data-ttu-id="3b1d1-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3b1d1-103">SYNOPSIS</span></span>
<span data-ttu-id="3b1d1-104">Hämtar ett konsoliderat objekt av system-och operativ system egenskaper.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-104">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="3b1d1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3b1d1-105">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="3b1d1-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3b1d1-106">DESCRIPTION</span></span>

<span data-ttu-id="3b1d1-107">`Get-ComputerInfo`Cmdlet: en hämtar ett konsoliderat objekt av system-och operativ system egenskaper.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-107">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="3b1d1-108">Den här cmdleten introducerades i Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-108">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="3b1d1-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3b1d1-109">EXAMPLES</span></span>

### <span data-ttu-id="3b1d1-110">Exempel 1: Hämta alla dator egenskaper</span><span class="sxs-lookup"><span data-stu-id="3b1d1-110">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="3b1d1-111">Det här kommandot hämtar alla system-och operativ system egenskaper från datorn.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-111">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="3b1d1-112">Exempel 2: Hämta alla egenskaper för datorns operativ system</span><span class="sxs-lookup"><span data-stu-id="3b1d1-112">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="3b1d1-113">Det här kommandot hämtar alla egenskaper för operativ systemet från datorn.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-113">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="3b1d1-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3b1d1-114">PARAMETERS</span></span>

### <span data-ttu-id="3b1d1-115">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="3b1d1-115">-Property</span></span>

<span data-ttu-id="3b1d1-116">Anger, som en sträng mat ris, de dator egenskaper som denna cmdlet visar.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-116">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

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

### <span data-ttu-id="3b1d1-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3b1d1-117">CommonParameters</span></span>

<span data-ttu-id="3b1d1-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3b1d1-119">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3b1d1-119">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3b1d1-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="3b1d1-120">INPUTS</span></span>

### <span data-ttu-id="3b1d1-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="3b1d1-121">System.String[]</span></span>

## <span data-ttu-id="3b1d1-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3b1d1-122">OUTPUTS</span></span>

### <span data-ttu-id="3b1d1-123">Microsoft. PowerShell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="3b1d1-123">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="3b1d1-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3b1d1-124">NOTES</span></span>

<span data-ttu-id="3b1d1-125">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="3b1d1-125">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="3b1d1-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3b1d1-126">RELATED LINKS</span></span>
