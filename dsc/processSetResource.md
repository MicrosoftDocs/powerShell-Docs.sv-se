---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC ProcessSet resurs
ms.openlocfilehash: b713d1a9c34eab6966de4f342991ead32c19df5d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="8e569-103">DSC WindowsProcess resurs</span><span class="sxs-lookup"><span data-stu-id="8e569-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="8e569-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8e569-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8e569-105">Den **ProcessSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att konfigurera processer på målnoden.</span><span class="sxs-lookup"><span data-stu-id="8e569-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="8e569-106">Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [WindowsProcess resurs](windowsProcessResource.md) för varje grupp som anges i den `GroupName` parametern.</span><span class="sxs-lookup"><span data-stu-id="8e569-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e569-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e569-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="8e569-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="8e569-108">Properties</span></span>
|  <span data-ttu-id="8e569-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="8e569-109">Property</span></span>  |  <span data-ttu-id="8e569-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8e569-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="8e569-111">Argument</span><span class="sxs-lookup"><span data-stu-id="8e569-111">Arguments</span></span>| <span data-ttu-id="8e569-112">En sträng som innehåller argument som ska skickas till processen som-är.</span><span class="sxs-lookup"><span data-stu-id="8e569-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="8e569-113">Om du behöver ange flera argument placeras i den här strängen.</span><span class="sxs-lookup"><span data-stu-id="8e569-113">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="8e569-114">Sökväg</span><span class="sxs-lookup"><span data-stu-id="8e569-114">Path</span></span>| <span data-ttu-id="8e569-115">Sökvägar till processen körbara filer.</span><span class="sxs-lookup"><span data-stu-id="8e569-115">The paths to the process executables.</span></span> <span data-ttu-id="8e569-116">Om dessa är namnen på de körbara filerna (inte fullständigt kvalificerade sökvägar) DSC-resurs söker miljön **sökväg** variabeln (`$env:Path`) att hitta filerna.</span><span class="sxs-lookup"><span data-stu-id="8e569-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="8e569-117">Om du värdena för den här egenskapen är fullständigt kvalificerade sökvägar, DSC kommer inte att använda den **sökväg** miljövariabeln kan hitta filerna och genereras ett fel om någon av sökvägarna som inte finns.</span><span class="sxs-lookup"><span data-stu-id="8e569-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="8e569-118">Relativa sökvägar tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="8e569-118">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="8e569-119">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="8e569-119">Credential</span></span>| <span data-ttu-id="8e569-120">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="8e569-120">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="8e569-121">Se till att</span><span class="sxs-lookup"><span data-stu-id="8e569-121">Ensure</span></span>| <span data-ttu-id="8e569-122">Anger om det finns processer.</span><span class="sxs-lookup"><span data-stu-id="8e569-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="8e569-123">Ange egenskapen ”aktuella” så att processen finns.</span><span class="sxs-lookup"><span data-stu-id="8e569-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="8e569-124">Ange annars det till ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="8e569-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="8e569-125">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="8e569-125">The default is "Present".</span></span>| 
| <span data-ttu-id="8e569-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="8e569-126">StandardErrorPath</span></span>| <span data-ttu-id="8e569-127">Sökvägen som standard fel vid skrivning av processer.</span><span class="sxs-lookup"><span data-stu-id="8e569-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="8e569-128">Alla befintliga filen skrivs över.</span><span class="sxs-lookup"><span data-stu-id="8e569-128">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="8e569-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="8e569-129">StandardInputPath</span></span>| <span data-ttu-id="8e569-130">Dataströmmen som processen tar emot standardindata.</span><span class="sxs-lookup"><span data-stu-id="8e569-130">The stream from which the process receives standard input.</span></span>| 
| <span data-ttu-id="8e569-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="8e569-131">StandardOutputPath</span></span>| <span data-ttu-id="8e569-132">Sökvägen till filen som processerna skriva standardutdata.</span><span class="sxs-lookup"><span data-stu-id="8e569-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="8e569-133">Alla befintliga filen skrivs över.</span><span class="sxs-lookup"><span data-stu-id="8e569-133">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="8e569-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="8e569-134">WorkingDirectory</span></span>| <span data-ttu-id="8e569-135">Den plats som används som den aktuella arbetskatalogen för processer.</span><span class="sxs-lookup"><span data-stu-id="8e569-135">The location used as the current working directory for the processes.</span></span>| 
| <span data-ttu-id="8e569-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8e569-136">DependsOn</span></span> | <span data-ttu-id="8e569-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="8e569-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8e569-138">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **_ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="8e569-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\` .</span></span>| 

