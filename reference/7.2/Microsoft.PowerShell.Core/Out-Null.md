---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: fe28f52088a82b93799724de7a7a3f20ce42e36b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710489"
---
# <span data-ttu-id="cbda1-102">Out-Null</span><span class="sxs-lookup"><span data-stu-id="cbda1-102">Out-Null</span></span>

## <span data-ttu-id="cbda1-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cbda1-103">SYNOPSIS</span></span>
<span data-ttu-id="cbda1-104">Döljer utdata i stället för att skicka den till pipelinen eller genom att visa den.</span><span class="sxs-lookup"><span data-stu-id="cbda1-104">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="cbda1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cbda1-105">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="cbda1-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cbda1-106">DESCRIPTION</span></span>

<span data-ttu-id="cbda1-107">Cmdleten **out-null** skickar utdata till null, i praktiken, tar bort den från pipelinen och förhindrar att utdata visas på skärmen.</span><span class="sxs-lookup"><span data-stu-id="cbda1-107">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span>

## <span data-ttu-id="cbda1-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cbda1-108">EXAMPLES</span></span>

### <span data-ttu-id="cbda1-109">Exempel 1: ta bort utdata</span><span class="sxs-lookup"><span data-stu-id="cbda1-109">Example 1: Delete output</span></span>

```powershell
Get-ChildItem | Out-Null
```

<span data-ttu-id="cbda1-110">Detta kommando hämtar objekt på den aktuella platsen/katalogen, men utdata skickas inte via pipelinen eller visas inte på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="cbda1-110">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="cbda1-111">Detta är användbart för att dölja utdata som du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="cbda1-111">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="cbda1-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cbda1-112">PARAMETERS</span></span>

### <span data-ttu-id="cbda1-113">– InputObject</span><span class="sxs-lookup"><span data-stu-id="cbda1-113">-InputObject</span></span>

<span data-ttu-id="cbda1-114">Anger det objekt som ska skickas till NULL (tas bort från pipelinen).</span><span class="sxs-lookup"><span data-stu-id="cbda1-114">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="cbda1-115">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="cbda1-115">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="cbda1-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbda1-116">CommonParameters</span></span>

<span data-ttu-id="cbda1-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cbda1-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbda1-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cbda1-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbda1-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="cbda1-119">INPUTS</span></span>

### <span data-ttu-id="cbda1-120">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="cbda1-120">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="cbda1-121">Du kan skicka alla objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cbda1-121">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="cbda1-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cbda1-122">OUTPUTS</span></span>

### <span data-ttu-id="cbda1-123">Inga</span><span class="sxs-lookup"><span data-stu-id="cbda1-123">None</span></span>

<span data-ttu-id="cbda1-124">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="cbda1-124">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cbda1-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cbda1-125">NOTES</span></span>

* <span data-ttu-id="cbda1-126">De cmdletar som **innehåller verbet** ( **out** -cmdletarna) har inga parametrar för namn eller fil Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="cbda1-126">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="cbda1-127">Om du vill skicka data till en **out** -cmdlet använder du en pipeline-operator (|) för att skicka utdata från ett PowerShell-kommando till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="cbda1-127">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a PowerShell command to the cmdlet.</span></span> <span data-ttu-id="cbda1-128">Du kan också lagra data i en variabel och använda parametern *InputObject* för att skicka data till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cbda1-128">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="cbda1-129">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="cbda1-129">For more information, see the examples.</span></span>
* <span data-ttu-id="cbda1-130">**Out-null** returnerar inga utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="cbda1-130">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="cbda1-131">Om du skickar utdata från **out-null** till Get-Member-cmdlet: en **får** du rapporter om att inga objekt har angetts.</span><span class="sxs-lookup"><span data-stu-id="cbda1-131">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="cbda1-132">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cbda1-132">RELATED LINKS</span></span>

[<span data-ttu-id="cbda1-133">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="cbda1-133">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="cbda1-134">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="cbda1-134">Out-Host</span></span>](Out-Host.md)

