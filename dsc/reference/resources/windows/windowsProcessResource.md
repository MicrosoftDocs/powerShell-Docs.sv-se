---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsProcess-resurs
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076777"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="69f98-103">DSC WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="69f98-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="69f98-104">_Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="69f98-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="69f98-105">Den **WindowsProcess** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att konfigurera processer på målnoden.</span><span class="sxs-lookup"><span data-stu-id="69f98-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="69f98-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="69f98-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="69f98-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="69f98-107">Properties</span></span>

| <span data-ttu-id="69f98-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="69f98-108">Property</span></span> | <span data-ttu-id="69f98-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="69f98-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="69f98-110">Argument</span><span class="sxs-lookup"><span data-stu-id="69f98-110">Arguments</span></span>| <span data-ttu-id="69f98-111">Anger en sträng med argument som ska skickas till processen som – är.</span><span class="sxs-lookup"><span data-stu-id="69f98-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="69f98-112">Om du vill ange flera argument kan du placera dem på den här strängen.</span><span class="sxs-lookup"><span data-stu-id="69f98-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="69f98-113">Sökväg</span><span class="sxs-lookup"><span data-stu-id="69f98-113">Path</span></span>| <span data-ttu-id="69f98-114">Sökvägen till den process körbara filen.</span><span class="sxs-lookup"><span data-stu-id="69f98-114">The path to the process executable.</span></span> <span data-ttu-id="69f98-115">Om det här namnet på den körbara filen (inte fullständigt kvalificerade sökvägen) DSC-resurs söker igenom miljön **sökväg** variabeln (`$env:Path`) att hitta den körbara filen.</span><span class="sxs-lookup"><span data-stu-id="69f98-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="69f98-116">Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, DSC kommer inte att använda den **sökväg** miljövariabeln att hitta filen, och genererar ett fel om sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="69f98-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="69f98-117">Relativa sökvägar är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="69f98-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="69f98-118">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="69f98-118">Credential</span></span>| <span data-ttu-id="69f98-119">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="69f98-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="69f98-120">Se till att</span><span class="sxs-lookup"><span data-stu-id="69f98-120">Ensure</span></span>| <span data-ttu-id="69f98-121">Anger om processen finns.</span><span class="sxs-lookup"><span data-stu-id="69f98-121">Indicates if the process exists.</span></span> <span data-ttu-id="69f98-122">Ange egenskapen ”aktuella” så att processen finns.</span><span class="sxs-lookup"><span data-stu-id="69f98-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="69f98-123">Annars kan ange den till ””.</span><span class="sxs-lookup"><span data-stu-id="69f98-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="69f98-124">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="69f98-124">The default is "Present".</span></span>|
| <span data-ttu-id="69f98-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="69f98-125">DependsOn</span></span> | <span data-ttu-id="69f98-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="69f98-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="69f98-127">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="69f98-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="69f98-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="69f98-128">StandardErrorPath</span></span>| <span data-ttu-id="69f98-129">Anger sökvägen till om du vill skriva standardfelet.</span><span class="sxs-lookup"><span data-stu-id="69f98-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="69f98-130">Alla befintliga filer kommer att skrivas över.</span><span class="sxs-lookup"><span data-stu-id="69f98-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="69f98-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="69f98-131">StandardInputPath</span></span>| <span data-ttu-id="69f98-132">Anger standardplats för indata.</span><span class="sxs-lookup"><span data-stu-id="69f98-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="69f98-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="69f98-133">StandardOutputPath</span></span>| <span data-ttu-id="69f98-134">Anger platsen för att skriva standardutdata.</span><span class="sxs-lookup"><span data-stu-id="69f98-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="69f98-135">Alla befintliga filer kommer att skrivas över.</span><span class="sxs-lookup"><span data-stu-id="69f98-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="69f98-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="69f98-136">WorkingDirectory</span></span>| <span data-ttu-id="69f98-137">Anger den plats som ska användas som den aktuella arbetskatalogen för processen.</span><span class="sxs-lookup"><span data-stu-id="69f98-137">Indicates the location that will be used as the current working directory for the process.</span></span>|