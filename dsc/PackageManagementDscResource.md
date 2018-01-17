---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagement resurs
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="e4f79-103">DSC PackageManagement resurs</span><span class="sxs-lookup"><span data-stu-id="e4f79-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="e4f79-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4f79-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e4f79-105">Den **PackageManagement** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera paketet Management-paketen på målnoden.</span><span class="sxs-lookup"><span data-stu-id="e4f79-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="e4f79-106">Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="e4f79-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4f79-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4f79-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e4f79-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="e4f79-108">Properties</span></span>
|  <span data-ttu-id="e4f79-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="e4f79-109">Property</span></span>  |  <span data-ttu-id="e4f79-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e4f79-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="e4f79-111">Namn</span><span class="sxs-lookup"><span data-stu-id="e4f79-111">Name</span></span>| <span data-ttu-id="e4f79-112">Anger namnet på paketet som ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="e4f79-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="e4f79-113">Källa</span><span class="sxs-lookup"><span data-stu-id="e4f79-113">Source</span></span>| <span data-ttu-id="e4f79-114">Anger namnet på paketkällan där paketet kan hittas.</span><span class="sxs-lookup"><span data-stu-id="e4f79-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="e4f79-115">Detta kan antingen vara en URI eller en källa som har registrerats med registrera PackageSource eller PackageManagementSource DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="e4f79-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="e4f79-116">DSC-resursen MSFT_PackageManagementSource kan också registrera en paketkällan.</span><span class="sxs-lookup"><span data-stu-id="e4f79-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="e4f79-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="e4f79-117">Ensure</span></span>| <span data-ttu-id="e4f79-118">Anger om paketet ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="e4f79-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="e4f79-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e4f79-119">RequiredVersion</span></span>| <span data-ttu-id="e4f79-120">Anger den exakta versionen av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="e4f79-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="e4f79-121">Om du inte anger den här parametern installerar den senaste tillgängliga versionen av paketet som också uppfyller alla högsta version som anges av parametern MaximumVersion i den här DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="e4f79-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="e4f79-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e4f79-122">MinimumVersion</span></span>| <span data-ttu-id="e4f79-123">Anger det minsta tillåtna version av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="e4f79-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="e4f79-124">Om du inte lägga till den här parametern anges den här DSC resurs intalls högsta tillgängliga versionen av paketet som också uppfyller eventuella maximalt angivna versionen av parametern MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="e4f79-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="e4f79-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e4f79-125">MaximumVersion</span></span>| <span data-ttu-id="e4f79-126">Anger högsta tillåtna version av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="e4f79-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="e4f79-127">Om du inte anger den här parametern installerar den här DSC-resursen högsta numret tillgänglig version av paketet.</span><span class="sxs-lookup"><span data-stu-id="e4f79-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="e4f79-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="e4f79-128">SourceCredential</span></span> | <span data-ttu-id="e4f79-129">Anger ett användarkonto som har behörighet att installera ett paket för ett angivet paket provider eller källa.</span><span class="sxs-lookup"><span data-stu-id="e4f79-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="e4f79-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e4f79-130">ProviderName</span></span>| <span data-ttu-id="e4f79-131">Anger ett provider-namn för paketet som du vill begränsa sökningen paketet.</span><span class="sxs-lookup"><span data-stu-id="e4f79-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="e4f79-132">Du kan hämta paketet providernamn genom att köra cmdlet Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="e4f79-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="e4f79-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="e4f79-133">AdditionalParameters</span></span>| <span data-ttu-id="e4f79-134">Providern specifika parametrar som skickas som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e4f79-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="e4f79-135">Du kan till exempel överföra ytterligare parametrar som DestinationPath för NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="e4f79-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="e4f79-136">Ytterligare parametrar</span><span class="sxs-lookup"><span data-stu-id="e4f79-136">Additional Parameters</span></span>
<span data-ttu-id="e4f79-137">I följande tabell visas alternativ för egenskapen AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="e4f79-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="e4f79-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="e4f79-138">Parameter</span></span>  | <span data-ttu-id="e4f79-139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e4f79-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="e4f79-140">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="e4f79-140">DestinationPath</span></span>| <span data-ttu-id="e4f79-141">Används av providrar, till exempel den inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="e4f79-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e4f79-142">Anger en plats där du vill att paket som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="e4f79-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="e4f79-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="e4f79-143">InstallationPolicy</span></span>| <span data-ttu-id="e4f79-144">Används av providrar, till exempel den inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="e4f79-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e4f79-145">Anger om du litar på den paketkällan.</span><span class="sxs-lookup"><span data-stu-id="e4f79-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="e4f79-146">En av: ”betrodd”, ”betrodd”.</span><span class="sxs-lookup"><span data-stu-id="e4f79-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="e4f79-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="e4f79-147">Example</span></span>

<span data-ttu-id="e4f79-148">Det här exemplet installerar den **JQuery** NuGet-paketet och **GistProvider** PowerShell-modulen använder den **PackageManagement** DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="e4f79-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="e4f79-149">Det här exemplet ser först källorna nödvändigt paket är tillgängliga och sedan definierar förväntade tillståndet för den **JQuery** och **GistProvider** paket (NuGet och PowerShell, respektive).</span><span class="sxs-lookup"><span data-stu-id="e4f79-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

