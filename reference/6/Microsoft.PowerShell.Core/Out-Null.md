---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: a9d5c47eaf189e37f7f16b11cd48101f7b0e584d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266852"
---
# <span data-ttu-id="7dcbd-103">Out-Null</span><span class="sxs-lookup"><span data-stu-id="7dcbd-103">Out-Null</span></span>

## <span data-ttu-id="7dcbd-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7dcbd-104">SYNOPSIS</span></span>
<span data-ttu-id="7dcbd-105">Döljer utdata i stället för att skicka den till pipelinen eller genom att visa den.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-105">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="7dcbd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7dcbd-106">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="7dcbd-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7dcbd-107">DESCRIPTION</span></span>

<span data-ttu-id="7dcbd-108">Cmdleten **out-null** skickar utdata till null, i praktiken, tar bort den från pipelinen och förhindrar att utdata visas på skärmen.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-108">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span>

## <span data-ttu-id="7dcbd-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7dcbd-109">EXAMPLES</span></span>

### <span data-ttu-id="7dcbd-110">Exempel 1: ta bort utdata</span><span class="sxs-lookup"><span data-stu-id="7dcbd-110">Example 1: Delete output</span></span>

```powershell
Get-ChildItem | Out-Null
```

<span data-ttu-id="7dcbd-111">Detta kommando hämtar objekt på den aktuella platsen/katalogen, men utdata skickas inte via pipelinen eller visas inte på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-111">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="7dcbd-112">Detta är användbart för att dölja utdata som du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-112">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="7dcbd-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7dcbd-113">PARAMETERS</span></span>

### <span data-ttu-id="7dcbd-114">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7dcbd-114">-InputObject</span></span>

<span data-ttu-id="7dcbd-115">Anger det objekt som ska skickas till NULL (tas bort från pipelinen).</span><span class="sxs-lookup"><span data-stu-id="7dcbd-115">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="7dcbd-116">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-116">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7dcbd-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7dcbd-117">CommonParameters</span></span>

<span data-ttu-id="7dcbd-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7dcbd-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7dcbd-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7dcbd-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="7dcbd-120">INPUTS</span></span>

### <span data-ttu-id="7dcbd-121">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7dcbd-121">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7dcbd-122">Du kan skicka alla objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-122">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="7dcbd-123">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7dcbd-123">OUTPUTS</span></span>

### <span data-ttu-id="7dcbd-124">Inget</span><span class="sxs-lookup"><span data-stu-id="7dcbd-124">None</span></span>

<span data-ttu-id="7dcbd-125">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-125">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7dcbd-126">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7dcbd-126">NOTES</span></span>

* <span data-ttu-id="7dcbd-127">De cmdletar som **innehåller verbet** ( **out** -cmdletarna) har inga parametrar för namn eller fil Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-127">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="7dcbd-128">Om du vill skicka data till en **out** -cmdlet använder du en pipeline-operator (|) för att skicka utdata från ett PowerShell-kommando till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-128">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a PowerShell command to the cmdlet.</span></span> <span data-ttu-id="7dcbd-129">Du kan också lagra data i en variabel och använda parametern *InputObject* för att skicka data till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-129">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="7dcbd-130">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-130">For more information, see the examples.</span></span>
* <span data-ttu-id="7dcbd-131">**Out-null** returnerar inga utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-131">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="7dcbd-132">Om du skickar utdata från **out-null** till Get-Member-cmdlet: en **får** du rapporter om att inga objekt har angetts.</span><span class="sxs-lookup"><span data-stu-id="7dcbd-132">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="7dcbd-133">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7dcbd-133">RELATED LINKS</span></span>

[<span data-ttu-id="7dcbd-134">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="7dcbd-134">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="7dcbd-135">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="7dcbd-135">Out-Host</span></span>](Out-Host.md)
