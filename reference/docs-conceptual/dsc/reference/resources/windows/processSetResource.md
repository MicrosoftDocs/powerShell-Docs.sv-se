---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC ProcessSet-resurs
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941371"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="c9ea9-103">DSC ProcessSet-resurs</span><span class="sxs-lookup"><span data-stu-id="c9ea9-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="c9ea9-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="c9ea9-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="c9ea9-105">**ProcessSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism som konfigurerar processer på en målnod.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9ea9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9ea9-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c9ea9-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="c9ea9-107">Properties</span></span>

|<span data-ttu-id="c9ea9-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c9ea9-108">Property</span></span> |<span data-ttu-id="c9ea9-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c9ea9-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c9ea9-110">Sökväg</span><span class="sxs-lookup"><span data-stu-id="c9ea9-110">Path</span></span> |<span data-ttu-id="c9ea9-111">Sökvägen till den körbara filen för processen.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-111">The path to the process executable.</span></span> <span data-ttu-id="c9ea9-112">Om dessa är namnen på de körbara filerna (inte fullständigt kvalificerade sökvägar) kommer DSC-resursen att söka i `$env:Path` miljövariabeln för att hitta filerna.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="c9ea9-113">Om värdet för den här egenskapen är fullständigt kvalificerade sökvägar använder `$env:Path` DSC inte miljövariabeln för att hitta filerna och genererar ett fel om någon av Sök vägarna inte finns.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="c9ea9-114">Relativa sökvägar är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="c9ea9-115">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="c9ea9-115">Credential</span></span> |<span data-ttu-id="c9ea9-116">Anger autentiseringsuppgifterna för att starta processen.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="c9ea9-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="c9ea9-117">StandardErrorPath</span></span> |<span data-ttu-id="c9ea9-118">Sökvägen till vilken processerna skriver standard fel.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="c9ea9-119">En befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="c9ea9-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="c9ea9-120">StandardInputPath</span></span> |<span data-ttu-id="c9ea9-121">Den data ström som processen tar emot standar in från.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="c9ea9-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="c9ea9-122">StandardOutputPath</span></span> |<span data-ttu-id="c9ea9-123">Sökvägen till filen som processerna skriver till standard utdata till.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="c9ea9-124">En befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="c9ea9-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="c9ea9-125">WorkingDirectory</span></span> |<span data-ttu-id="c9ea9-126">Den plats som används som den aktuella arbets katalogen för processerna.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c9ea9-127">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="c9ea9-127">Common properties</span></span>

|<span data-ttu-id="c9ea9-128">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c9ea9-128">Property</span></span> |<span data-ttu-id="c9ea9-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c9ea9-129">Description</span></span> |
|---|---|
|<span data-ttu-id="c9ea9-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c9ea9-130">DependsOn</span></span> |<span data-ttu-id="c9ea9-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c9ea9-132">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c9ea9-133">Kontrol</span><span class="sxs-lookup"><span data-stu-id="c9ea9-133">Ensure</span></span> |<span data-ttu-id="c9ea9-134">Anger om processerna finns.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="c9ea9-135">Ange att den här egenskapen **finns** för att se till att processen finns.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="c9ea9-136">Annars anger du det som **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-136">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="c9ea9-137">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="c9ea9-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="c9ea9-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c9ea9-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="c9ea9-139">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c9ea9-140">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="c9ea9-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c9ea9-141">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="c9ea9-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>