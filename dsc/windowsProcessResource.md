---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsProcess resurs
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="633f2-103">DSC WindowsProcess resurs</span><span class="sxs-lookup"><span data-stu-id="633f2-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="633f2-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="633f2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="633f2-105">Den **WindowsProcess** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att konfigurera processer på målnoden.</span><span class="sxs-lookup"><span data-stu-id="633f2-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="633f2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="633f2-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="633f2-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="633f2-107">Properties</span></span>
|  <span data-ttu-id="633f2-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="633f2-108">Property</span></span>  |  <span data-ttu-id="633f2-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="633f2-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="633f2-110">Argument</span><span class="sxs-lookup"><span data-stu-id="633f2-110">Arguments</span></span>| <span data-ttu-id="633f2-111">Anger en sträng med argument som ska skickas till processen som-är.</span><span class="sxs-lookup"><span data-stu-id="633f2-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="633f2-112">Om du behöver ange flera argument placeras i den här strängen.</span><span class="sxs-lookup"><span data-stu-id="633f2-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="633f2-113">Sökväg</span><span class="sxs-lookup"><span data-stu-id="633f2-113">Path</span></span>| <span data-ttu-id="633f2-114">Sökvägen till den körbara filen processen.</span><span class="sxs-lookup"><span data-stu-id="633f2-114">The path to the process executable.</span></span> <span data-ttu-id="633f2-115">Om det här namnet på den körbara filen (inte fullständigt kvalificerade sökvägen) DSC-resurs söker miljön **sökväg** variabeln (`$env:Path`) att hitta den körbara filen.</span><span class="sxs-lookup"><span data-stu-id="633f2-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="633f2-116">Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, DSC kommer inte att använda den **sökväg** miljövariabeln för att hitta filen, och ett fel genereras om sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="633f2-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="633f2-117">Relativa sökvägar tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="633f2-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="633f2-118">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="633f2-118">Credential</span></span>| <span data-ttu-id="633f2-119">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="633f2-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="633f2-120">Se till att</span><span class="sxs-lookup"><span data-stu-id="633f2-120">Ensure</span></span>| <span data-ttu-id="633f2-121">Anger om processen finns.</span><span class="sxs-lookup"><span data-stu-id="633f2-121">Indicates if the process exists.</span></span> <span data-ttu-id="633f2-122">Ange egenskapen ”aktuella” så att processen finns.</span><span class="sxs-lookup"><span data-stu-id="633f2-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="633f2-123">Ange annars det till ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="633f2-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="633f2-124">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="633f2-124">The default is "Present".</span></span>|
| <span data-ttu-id="633f2-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="633f2-125">DependsOn</span></span> | <span data-ttu-id="633f2-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="633f2-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="633f2-127">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="633f2-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="633f2-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="633f2-128">StandardErrorPath</span></span>| <span data-ttu-id="633f2-129">Anger sökvägen till om du vill skriva standardfelet.</span><span class="sxs-lookup"><span data-stu-id="633f2-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="633f2-130">Alla befintliga filen skrivs över.</span><span class="sxs-lookup"><span data-stu-id="633f2-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="633f2-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="633f2-131">StandardInputPath</span></span>| <span data-ttu-id="633f2-132">Anger den inkommande standardplatsen.</span><span class="sxs-lookup"><span data-stu-id="633f2-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="633f2-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="633f2-133">StandardOutputPath</span></span>| <span data-ttu-id="633f2-134">Indikerar platsen om du vill skriva standardutdata.</span><span class="sxs-lookup"><span data-stu-id="633f2-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="633f2-135">Alla befintliga filen skrivs över.</span><span class="sxs-lookup"><span data-stu-id="633f2-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="633f2-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="633f2-136">WorkingDirectory</span></span>| <span data-ttu-id="633f2-137">Anger den plats som ska användas som den aktuella arbetskatalogen för processen.</span><span class="sxs-lookup"><span data-stu-id="633f2-137">Indicates the location that will be used as the current working directory for the process.</span></span>|