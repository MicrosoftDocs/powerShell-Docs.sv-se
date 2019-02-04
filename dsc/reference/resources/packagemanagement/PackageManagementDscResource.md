---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagement resurs
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686868"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="13cf7-103">DSC PackageManagement resurs</span><span class="sxs-lookup"><span data-stu-id="13cf7-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="13cf7-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="13cf7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="13cf7-105">Den **PackageManagement** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att installera eller avinstallera pakethantering paket på målnoden.</span><span class="sxs-lookup"><span data-stu-id="13cf7-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="13cf7-106">Den här resursen kräver den **PackageManagement** modulen, som är tillgängliga från [ http://PowerShellGallery.com ](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="13cf7-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13cf7-107">Den **PackageManagement** modul bör vara minst version 1.1.7.0 för egenskapen följande ska vara giltig.</span><span class="sxs-lookup"><span data-stu-id="13cf7-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="13cf7-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="13cf7-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="13cf7-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="13cf7-109">Properties</span></span>

| <span data-ttu-id="13cf7-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="13cf7-110">Property</span></span> | <span data-ttu-id="13cf7-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13cf7-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="13cf7-112">Namn</span><span class="sxs-lookup"><span data-stu-id="13cf7-112">Name</span></span>| <span data-ttu-id="13cf7-113">Anger namnet på paketet installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="13cf7-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="13cf7-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="13cf7-114">AdditionalParameters</span></span>| <span data-ttu-id="13cf7-115">Providern specifika hashtabell med parametrar som skulle skickas till `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="13cf7-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="13cf7-116">Du kan exempelvis skicka ytterligare parametrar som målsökväg för NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="13cf7-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="13cf7-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="13cf7-117">Ensure</span></span>| <span data-ttu-id="13cf7-118">Anger om paketet ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="13cf7-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="13cf7-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="13cf7-119">MaximumVersion</span></span>|<span data-ttu-id="13cf7-120">Anger det högsta tillåtna version av det paket som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="13cf7-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="13cf7-121">Om du inte lägga till den här parametern hittar den senaste tillgängliga versionen av paketet i resursen.</span><span class="sxs-lookup"><span data-stu-id="13cf7-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="13cf7-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="13cf7-122">MinimumVersion</span></span>|<span data-ttu-id="13cf7-123">Anger den lägsta tillåtna versionen på det paket som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="13cf7-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="13cf7-124">Om du inte lägga till den här parametern resursen hittar den högsta tillgängliga versionen av paketet som också uppfyller alla högsta angivna version som anges av den _MaximumVersion_ parametern.</span><span class="sxs-lookup"><span data-stu-id="13cf7-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="13cf7-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="13cf7-125">ProviderName</span></span>| <span data-ttu-id="13cf7-126">Anger ett namn på providern som du vill begränsa sökningen paketet.</span><span class="sxs-lookup"><span data-stu-id="13cf7-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="13cf7-127">Du kan hämta paketet providernamn genom att köra den `Get-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="13cf7-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="13cf7-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="13cf7-128">RequiredVersion</span></span>| <span data-ttu-id="13cf7-129">Anger den exakta versionen av det paket som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="13cf7-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="13cf7-130">Om du inte anger den här parametern, den här DSC-resursen installerar den senaste tillgängliga versionen av paketet som också uppfyller alla högsta version som anges av den _MaximumVersion_ parametern.</span><span class="sxs-lookup"><span data-stu-id="13cf7-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="13cf7-131">Källa</span><span class="sxs-lookup"><span data-stu-id="13cf7-131">Source</span></span>| <span data-ttu-id="13cf7-132">Anger namnet på paketkällan där paketet kan hittas.</span><span class="sxs-lookup"><span data-stu-id="13cf7-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="13cf7-133">Detta kan vara en URI eller en källa som har registrerats med `Register-PackageSource` eller PackageManagementSource DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="13cf7-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="13cf7-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="13cf7-134">SourceCredential</span></span> | <span data-ttu-id="13cf7-135">Anger ett användarkonto som har behörighet att installera ett paket för en angiven paket-providern eller källa.</span><span class="sxs-lookup"><span data-stu-id="13cf7-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="13cf7-136">Ytterligare parametrar</span><span class="sxs-lookup"><span data-stu-id="13cf7-136">Additional Parameters</span></span>

<span data-ttu-id="13cf7-137">I följande tabell visas alternativ för egenskapen AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="13cf7-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="13cf7-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="13cf7-138">Parameter</span></span> | <span data-ttu-id="13cf7-139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13cf7-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="13cf7-140">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="13cf7-140">DestinationPath</span></span>| <span data-ttu-id="13cf7-141">Används av providrar, till exempel inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="13cf7-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="13cf7-142">Anger en plats där du vill att paketet installeras.</span><span class="sxs-lookup"><span data-stu-id="13cf7-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="13cf7-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="13cf7-143">InstallationPolicy</span></span>| <span data-ttu-id="13cf7-144">Används av providrar, till exempel inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="13cf7-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="13cf7-145">Anger om du litar på den paketkällan.</span><span class="sxs-lookup"><span data-stu-id="13cf7-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="13cf7-146">En av: `Untrusted`, `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="13cf7-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="13cf7-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="13cf7-147">Example</span></span>

<span data-ttu-id="13cf7-148">Det här exemplet installerar den **JQuery** NuGet-paketet och **GistProvider** PowerShell-modulen med den **PackageManagement** DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="13cf7-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="13cf7-149">Det här exemplet ser först till källor för paket som krävs är tillgängliga och sedan definierar det förväntade tillståndet för den **JQuery** och **GistProvider** paket (NuGet och PowerShell, respektive).</span><span class="sxs-lookup"><span data-stu-id="13cf7-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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