---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagement resurs
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753795"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="6b399-103">DSC PackageManagement resurs</span><span class="sxs-lookup"><span data-stu-id="6b399-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="6b399-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b399-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="6b399-105">Den **PackageManagement** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera paketet Management-paketen på målnoden.</span><span class="sxs-lookup"><span data-stu-id="6b399-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="6b399-106">Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="6b399-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b399-107">Den **PackageManagement** modulen bör vara minst version 1.1.7.0 med följande information för egenskapen ska vara giltig.</span><span class="sxs-lookup"><span data-stu-id="6b399-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b399-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b399-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="6b399-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6b399-109">Properties</span></span>

|  <span data-ttu-id="6b399-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6b399-110">Property</span></span>  |  <span data-ttu-id="6b399-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6b399-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="6b399-112">Namn</span><span class="sxs-lookup"><span data-stu-id="6b399-112">Name</span></span>| <span data-ttu-id="6b399-113">Anger namnet på paketet som ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6b399-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="6b399-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="6b399-114">AdditionalParameters</span></span>| <span data-ttu-id="6b399-115">Providern specifika hash av parametrar som skickas till `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="6b399-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="6b399-116">Du kan till exempel överföra ytterligare parametrar som DestinationPath för NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="6b399-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="6b399-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="6b399-117">Ensure</span></span>| <span data-ttu-id="6b399-118">Anger om paketet ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="6b399-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="6b399-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6b399-119">MaximumVersion</span></span>|<span data-ttu-id="6b399-120">Anger högsta tillåtna version av paketet som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="6b399-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="6b399-121">Om du inte lägga till den här parametern hittar den högsta tillgängliga versionen av paketet i resursen.</span><span class="sxs-lookup"><span data-stu-id="6b399-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="6b399-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6b399-122">MinimumVersion</span></span>|<span data-ttu-id="6b399-123">Anger det minsta tillåtna version av paketet som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="6b399-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="6b399-124">Om du inte lägga till den här parametern resursen hittar den högsta tillgängliga versionen av paketet som också uppfyller alla angivna högsta version som anges av den _MaximumVersion_ parameter.</span><span class="sxs-lookup"><span data-stu-id="6b399-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="6b399-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="6b399-125">ProviderName</span></span>| <span data-ttu-id="6b399-126">Anger ett provider-namn för paketet som du vill begränsa sökningen paketet.</span><span class="sxs-lookup"><span data-stu-id="6b399-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="6b399-127">Du kan hämta paketet providernamn genom att köra den `Get-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b399-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="6b399-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6b399-128">RequiredVersion</span></span>| <span data-ttu-id="6b399-129">Anger den exakta versionen av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="6b399-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="6b399-130">Om du inte anger den här parametern DSC resursen installerar den senaste tillgängliga versionen av paketet som också uppfyller alla högsta version som anges av den _MaximumVersion_ parameter.</span><span class="sxs-lookup"><span data-stu-id="6b399-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="6b399-131">Källa</span><span class="sxs-lookup"><span data-stu-id="6b399-131">Source</span></span>| <span data-ttu-id="6b399-132">Anger namnet på paketkällan där paketet kan hittas.</span><span class="sxs-lookup"><span data-stu-id="6b399-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="6b399-133">Detta kan antingen vara en URI eller en källa som har registrerats med `Register-PackageSource` eller PackageManagementSource DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6b399-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="6b399-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="6b399-134">SourceCredential</span></span> | <span data-ttu-id="6b399-135">Anger ett användarkonto som har behörighet att installera ett paket för ett angivet paket provider eller källa.</span><span class="sxs-lookup"><span data-stu-id="6b399-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="6b399-136">Ytterligare parametrar</span><span class="sxs-lookup"><span data-stu-id="6b399-136">Additional Parameters</span></span>

<span data-ttu-id="6b399-137">I följande tabell visas alternativ för egenskapen AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="6b399-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="6b399-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="6b399-138">Parameter</span></span>  | <span data-ttu-id="6b399-139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6b399-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="6b399-140">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="6b399-140">DestinationPath</span></span>| <span data-ttu-id="6b399-141">Används av providrar, till exempel den inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="6b399-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6b399-142">Anger en plats där du vill att paket som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="6b399-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="6b399-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="6b399-143">InstallationPolicy</span></span>| <span data-ttu-id="6b399-144">Används av providrar, till exempel den inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="6b399-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6b399-145">Anger om du litar på den paketkällan.</span><span class="sxs-lookup"><span data-stu-id="6b399-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="6b399-146">En av: ”betrodd”, ”betrodd”.</span><span class="sxs-lookup"><span data-stu-id="6b399-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="6b399-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="6b399-147">Example</span></span>

<span data-ttu-id="6b399-148">Det här exemplet installerar den **JQuery** NuGet-paketet och **GistProvider** PowerShell-modulen använder den **PackageManagement** DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6b399-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="6b399-149">Det här exemplet ser först källorna nödvändigt paket är tillgängliga och sedan definierar förväntade tillståndet för den **JQuery** och **GistProvider** paket (NuGet och PowerShell, respektive).</span><span class="sxs-lookup"><span data-stu-id="6b399-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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