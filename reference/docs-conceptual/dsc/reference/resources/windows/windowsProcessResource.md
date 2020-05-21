---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsProcess-resurs
ms.openlocfilehash: 5c30af98bf7b99551396082630605c566a866697
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560499"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="d7255-103">DSC WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="d7255-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="d7255-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="d7255-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d7255-105">**WindowsProcess** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism som konfigurerar processer på en målnod.</span><span class="sxs-lookup"><span data-stu-id="d7255-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7255-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7255-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d7255-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d7255-107">Properties</span></span>

|<span data-ttu-id="d7255-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d7255-108">Property</span></span> |<span data-ttu-id="d7255-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d7255-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d7255-110">Argument</span><span class="sxs-lookup"><span data-stu-id="d7255-110">Arguments</span></span> |<span data-ttu-id="d7255-111">Anger en sträng med argument som ska skickas till processen i befintligt skick.</span><span class="sxs-lookup"><span data-stu-id="d7255-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="d7255-112">Om du behöver skicka flera argument sätter du dem i den här strängen.</span><span class="sxs-lookup"><span data-stu-id="d7255-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="d7255-113">Sökväg</span><span class="sxs-lookup"><span data-stu-id="d7255-113">Path</span></span> |<span data-ttu-id="d7255-114">Sökvägen till den körbara filen för processen.</span><span class="sxs-lookup"><span data-stu-id="d7255-114">The path to the process executable.</span></span> <span data-ttu-id="d7255-115">Om detta är fil namnet på den körbara filen (inte den fullständigt kvalificerade sökvägen) kommer DSC-resursen att söka i `$env:Path` miljövariabeln för att hitta den körbara filen.</span><span class="sxs-lookup"><span data-stu-id="d7255-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="d7255-116">Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, använder DSC inte `$env:Path` variabeln för att hitta filen och genererar ett fel om sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="d7255-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="d7255-117">Relativa sökvägar är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d7255-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="d7255-118">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="d7255-118">Credential</span></span> |<span data-ttu-id="d7255-119">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="d7255-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="d7255-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="d7255-120">StandardErrorPath</span></span> |<span data-ttu-id="d7255-121">Anger katalog Sök vägen för att skriva standard felet.</span><span class="sxs-lookup"><span data-stu-id="d7255-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="d7255-122">En befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="d7255-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="d7255-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="d7255-123">StandardInputPath</span></span> |<span data-ttu-id="d7255-124">Anger standard ingångs platsen.</span><span class="sxs-lookup"><span data-stu-id="d7255-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="d7255-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="d7255-125">StandardOutputPath</span></span> |<span data-ttu-id="d7255-126">Anger den plats där standard utdata ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="d7255-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="d7255-127">En befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="d7255-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="d7255-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="d7255-128">WorkingDirectory</span></span> |<span data-ttu-id="d7255-129">Anger den plats som ska användas som den aktuella arbets katalogen för processen.</span><span class="sxs-lookup"><span data-stu-id="d7255-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d7255-130">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="d7255-130">Common properties</span></span>

|<span data-ttu-id="d7255-131">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d7255-131">Property</span></span> |<span data-ttu-id="d7255-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d7255-132">Description</span></span> |
|---|---|
|<span data-ttu-id="d7255-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d7255-133">DependsOn</span></span> |<span data-ttu-id="d7255-134">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="d7255-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d7255-135">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="d7255-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d7255-136">Kontrol</span><span class="sxs-lookup"><span data-stu-id="d7255-136">Ensure</span></span> |<span data-ttu-id="d7255-137">Anger om processen finns.</span><span class="sxs-lookup"><span data-stu-id="d7255-137">Indicates if the process exists.</span></span> <span data-ttu-id="d7255-138">Ange att den här egenskapen **finns** för att se till att processen finns.</span><span class="sxs-lookup"><span data-stu-id="d7255-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="d7255-139">Annars anger du det som **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="d7255-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="d7255-140">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="d7255-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="d7255-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d7255-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="d7255-142">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="d7255-142">Sets the credential for running the entire resource as.</span></span> |
