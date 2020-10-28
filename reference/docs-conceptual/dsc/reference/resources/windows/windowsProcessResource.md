---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsProcess-resurs
description: DSC WindowsProcess-resurs
ms.openlocfilehash: 3958d1cf90f0ce19b28b5b26cc1fbb8da03626a3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656433"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="20e7c-103">DSC WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="20e7c-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="20e7c-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="20e7c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="20e7c-105">**WindowsProcess** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism som konfigurerar processer på en målnod.</span><span class="sxs-lookup"><span data-stu-id="20e7c-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="20e7c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="20e7c-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="20e7c-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="20e7c-107">Properties</span></span>

|<span data-ttu-id="20e7c-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="20e7c-108">Property</span></span> |<span data-ttu-id="20e7c-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="20e7c-109">Description</span></span> |
|---|---|
|<span data-ttu-id="20e7c-110">Argument</span><span class="sxs-lookup"><span data-stu-id="20e7c-110">Arguments</span></span> |<span data-ttu-id="20e7c-111">Anger en sträng med argument som ska skickas till processen i befintligt skick.</span><span class="sxs-lookup"><span data-stu-id="20e7c-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="20e7c-112">Om du behöver skicka flera argument sätter du dem i den här strängen.</span><span class="sxs-lookup"><span data-stu-id="20e7c-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="20e7c-113">Sökväg</span><span class="sxs-lookup"><span data-stu-id="20e7c-113">Path</span></span> |<span data-ttu-id="20e7c-114">Sökvägen till den körbara filen för processen.</span><span class="sxs-lookup"><span data-stu-id="20e7c-114">The path to the process executable.</span></span> <span data-ttu-id="20e7c-115">Om detta är fil namnet på den körbara filen (inte den fullständigt kvalificerade sökvägen) kommer DSC-resursen att söka i `$env:Path` miljövariabeln för att hitta den körbara filen.</span><span class="sxs-lookup"><span data-stu-id="20e7c-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="20e7c-116">Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, använder DSC inte `$env:Path` variabeln för att hitta filen och genererar ett fel om sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="20e7c-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="20e7c-117">Relativa sökvägar är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="20e7c-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="20e7c-118">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="20e7c-118">Credential</span></span> |<span data-ttu-id="20e7c-119">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="20e7c-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="20e7c-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="20e7c-120">StandardErrorPath</span></span> |<span data-ttu-id="20e7c-121">Anger katalog Sök vägen för att skriva standard felet.</span><span class="sxs-lookup"><span data-stu-id="20e7c-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="20e7c-122">En befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="20e7c-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="20e7c-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="20e7c-123">StandardInputPath</span></span> |<span data-ttu-id="20e7c-124">Anger standard ingångs platsen.</span><span class="sxs-lookup"><span data-stu-id="20e7c-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="20e7c-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="20e7c-125">StandardOutputPath</span></span> |<span data-ttu-id="20e7c-126">Anger den plats där standard utdata ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="20e7c-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="20e7c-127">En befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="20e7c-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="20e7c-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="20e7c-128">WorkingDirectory</span></span> |<span data-ttu-id="20e7c-129">Anger den plats som ska användas som den aktuella arbets katalogen för processen.</span><span class="sxs-lookup"><span data-stu-id="20e7c-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="20e7c-130">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="20e7c-130">Common properties</span></span>

|<span data-ttu-id="20e7c-131">Egenskap</span><span class="sxs-lookup"><span data-stu-id="20e7c-131">Property</span></span> |<span data-ttu-id="20e7c-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="20e7c-132">Description</span></span> |
|---|---|
|<span data-ttu-id="20e7c-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="20e7c-133">DependsOn</span></span> |<span data-ttu-id="20e7c-134">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="20e7c-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="20e7c-135">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="20e7c-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="20e7c-136">Kontrol</span><span class="sxs-lookup"><span data-stu-id="20e7c-136">Ensure</span></span> |<span data-ttu-id="20e7c-137">Anger om processen finns.</span><span class="sxs-lookup"><span data-stu-id="20e7c-137">Indicates if the process exists.</span></span> <span data-ttu-id="20e7c-138">Ange att den här egenskapen **finns** för att se till att processen finns.</span><span class="sxs-lookup"><span data-stu-id="20e7c-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="20e7c-139">Annars anger du det som **frånvarande** .</span><span class="sxs-lookup"><span data-stu-id="20e7c-139">Otherwise, set it to **Absent** .</span></span> <span data-ttu-id="20e7c-140">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="20e7c-140">The default value is **Present** .</span></span> |
|<span data-ttu-id="20e7c-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="20e7c-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="20e7c-142">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="20e7c-142">Sets the credential for running the entire resource as.</span></span> |
