---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC ProcessSet-resurs
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077117"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="41f5a-103">DSC WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="41f5a-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="41f5a-104">_Gäller för: Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="41f5a-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="41f5a-105">Den **ProcessSet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att konfigurera processer på målnoden.</span><span class="sxs-lookup"><span data-stu-id="41f5a-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="41f5a-106">Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [WindowsProcess-resurs](windowsProcessResource.md) för varje grupp som anges i den `GroupName` parametern.</span><span class="sxs-lookup"><span data-stu-id="41f5a-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="41f5a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="41f5a-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="41f5a-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="41f5a-108">Properties</span></span>

| <span data-ttu-id="41f5a-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="41f5a-109">Property</span></span> | <span data-ttu-id="41f5a-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41f5a-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="41f5a-111">Argument</span><span class="sxs-lookup"><span data-stu-id="41f5a-111">Arguments</span></span>| <span data-ttu-id="41f5a-112">En sträng som innehåller argument ska skickas till processen som – är.</span><span class="sxs-lookup"><span data-stu-id="41f5a-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="41f5a-113">Om du vill ange flera argument kan du placera dem på den här strängen.</span><span class="sxs-lookup"><span data-stu-id="41f5a-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="41f5a-114">Sökväg</span><span class="sxs-lookup"><span data-stu-id="41f5a-114">Path</span></span>| <span data-ttu-id="41f5a-115">Sökvägar till processen körbara filer.</span><span class="sxs-lookup"><span data-stu-id="41f5a-115">The paths to the process executables.</span></span> <span data-ttu-id="41f5a-116">Om dessa är namnen på de körbara filerna (inte fullständigt kvalificerade sökvägar), DSC-resurs söker miljön **sökväg** variabeln (`$env:Path`) och hitta filerna.</span><span class="sxs-lookup"><span data-stu-id="41f5a-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="41f5a-117">Om värdena för den här egenskapen är fullständigt kvalificerade sökvägar, DSC kommer inte att använda den **sökväg** miljövariabeln och hitta filerna och genererar ett fel om någon av sökvägarna som inte finns.</span><span class="sxs-lookup"><span data-stu-id="41f5a-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="41f5a-118">Relativa sökvägar är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41f5a-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="41f5a-119">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="41f5a-119">Credential</span></span>| <span data-ttu-id="41f5a-120">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="41f5a-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="41f5a-121">Se till att</span><span class="sxs-lookup"><span data-stu-id="41f5a-121">Ensure</span></span>| <span data-ttu-id="41f5a-122">Anger om processerna som finns.</span><span class="sxs-lookup"><span data-stu-id="41f5a-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="41f5a-123">Ange egenskapen ”aktuella” så att processen finns.</span><span class="sxs-lookup"><span data-stu-id="41f5a-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="41f5a-124">Annars kan ange den till ””.</span><span class="sxs-lookup"><span data-stu-id="41f5a-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="41f5a-125">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="41f5a-125">The default is "Present".</span></span>|
| <span data-ttu-id="41f5a-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="41f5a-126">StandardErrorPath</span></span>| <span data-ttu-id="41f5a-127">Sökvägen som processerna skriva standardfel.</span><span class="sxs-lookup"><span data-stu-id="41f5a-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="41f5a-128">Alla befintliga filer kommer att skrivas över.</span><span class="sxs-lookup"><span data-stu-id="41f5a-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="41f5a-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="41f5a-129">StandardInputPath</span></span>| <span data-ttu-id="41f5a-130">Dataströmmen som processen tar emot standardindata.</span><span class="sxs-lookup"><span data-stu-id="41f5a-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="41f5a-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="41f5a-131">StandardOutputPath</span></span>| <span data-ttu-id="41f5a-132">Sökvägen till filen som processerna skriva standardutdata.</span><span class="sxs-lookup"><span data-stu-id="41f5a-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="41f5a-133">Alla befintliga filer kommer att skrivas över.</span><span class="sxs-lookup"><span data-stu-id="41f5a-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="41f5a-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="41f5a-134">WorkingDirectory</span></span>| <span data-ttu-id="41f5a-135">Den plats som används som den aktuella arbetskatalogen för processer.</span><span class="sxs-lookup"><span data-stu-id="41f5a-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="41f5a-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="41f5a-136">DependsOn</span></span> | <span data-ttu-id="41f5a-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="41f5a-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="41f5a-138">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **_ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="41f5a-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
