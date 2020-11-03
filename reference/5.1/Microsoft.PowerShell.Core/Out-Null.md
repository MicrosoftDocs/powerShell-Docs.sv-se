---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 5a949629cdf0f0822866863822e82e70fc38d8c2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264224"
---
# <span data-ttu-id="800e4-103">Out-Null</span><span class="sxs-lookup"><span data-stu-id="800e4-103">Out-Null</span></span>

## <span data-ttu-id="800e4-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="800e4-104">SYNOPSIS</span></span>
<span data-ttu-id="800e4-105">Döljer utdata i stället för att skicka den till pipelinen eller genom att visa den.</span><span class="sxs-lookup"><span data-stu-id="800e4-105">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="800e4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="800e4-106">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="800e4-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="800e4-107">DESCRIPTION</span></span>
<span data-ttu-id="800e4-108">Cmdleten **out-null** skickar utdata till null, i praktiken, tar bort den från pipelinen och förhindrar att utdata visas på skärmen.</span><span class="sxs-lookup"><span data-stu-id="800e4-108">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span> <span data-ttu-id="800e4-109">Detta påverkar bara standardutdata-dataströmmen.</span><span class="sxs-lookup"><span data-stu-id="800e4-109">This only affects the standard output stream.</span></span>
<span data-ttu-id="800e4-110">Andra utgående strömmar, t. ex. fel strömmen, påverkas inte.</span><span class="sxs-lookup"><span data-stu-id="800e4-110">Other output streams, like the Error stream are not affected.</span></span> <span data-ttu-id="800e4-111">Undantag visas.</span><span class="sxs-lookup"><span data-stu-id="800e4-111">Exceptions will be displayed.</span></span> <span data-ttu-id="800e4-112">Detta gör det enklare att testa kommandot för eventuella fel.</span><span class="sxs-lookup"><span data-stu-id="800e4-112">This makes it easier to test your command for any errors.</span></span>

## <span data-ttu-id="800e4-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="800e4-113">EXAMPLES</span></span>

### <span data-ttu-id="800e4-114">Exempel 1: ta bort utdata</span><span class="sxs-lookup"><span data-stu-id="800e4-114">Example 1: Delete output</span></span>

```
PS C:\> Get-ChildItem | Out-Null
```

<span data-ttu-id="800e4-115">Detta kommando hämtar objekt på den aktuella platsen/katalogen, men utdata skickas inte via pipelinen eller visas inte på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="800e4-115">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="800e4-116">Detta är användbart för att dölja utdata som du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="800e4-116">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="800e4-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="800e4-117">PARAMETERS</span></span>

### <span data-ttu-id="800e4-118">– InputObject</span><span class="sxs-lookup"><span data-stu-id="800e4-118">-InputObject</span></span>
<span data-ttu-id="800e4-119">Anger det objekt som ska skickas till NULL (tas bort från pipelinen).</span><span class="sxs-lookup"><span data-stu-id="800e4-119">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="800e4-120">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="800e4-120">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="800e4-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="800e4-121">CommonParameters</span></span>
<span data-ttu-id="800e4-122">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="800e4-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="800e4-123">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="800e4-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="800e4-124">INDATA</span><span class="sxs-lookup"><span data-stu-id="800e4-124">INPUTS</span></span>

### <span data-ttu-id="800e4-125">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="800e4-125">System.Management.Automation.PSObject</span></span>
<span data-ttu-id="800e4-126">Du kan skicka alla objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="800e4-126">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="800e4-127">UTDATA</span><span class="sxs-lookup"><span data-stu-id="800e4-127">OUTPUTS</span></span>

### <span data-ttu-id="800e4-128">Inget</span><span class="sxs-lookup"><span data-stu-id="800e4-128">None</span></span>
<span data-ttu-id="800e4-129">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="800e4-129">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="800e4-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="800e4-130">NOTES</span></span>

* <span data-ttu-id="800e4-131">De cmdletar som **innehåller verbet** ( **out** -cmdletarna) har inga parametrar för namn eller fil Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="800e4-131">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="800e4-132">Om du vill skicka data till en **out** -cmdlet använder du en pipeline-operator (|) för att skicka utdata från ett Windows PowerShell-kommando till-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="800e4-132">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a Windows PowerShell command to the cmdlet.</span></span> <span data-ttu-id="800e4-133">Du kan också lagra data i en variabel och använda parametern *InputObject* för att skicka data till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="800e4-133">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="800e4-134">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="800e4-134">For more information, see the examples.</span></span>
* <span data-ttu-id="800e4-135">**Out-null** returnerar inga utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="800e4-135">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="800e4-136">Om du skickar utdata från **out-null** till Get-Member-cmdlet: en **får** du rapporter om att inga objekt har angetts.</span><span class="sxs-lookup"><span data-stu-id="800e4-136">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="800e4-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="800e4-137">RELATED LINKS</span></span>

[<span data-ttu-id="800e4-138">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="800e4-138">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="800e4-139">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="800e4-139">Out-Host</span></span>](Out-Host.md)
