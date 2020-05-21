---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC PackageManagement-resurs
ms.openlocfilehash: ba8ab1e6c2d79e98084a52e3cffec39d57d800c9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557166"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="f8a0f-103">DSC PackageManagement-resurs</span><span class="sxs-lookup"><span data-stu-id="f8a0f-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="f8a0f-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0, Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="f8a0f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f8a0f-105">**PackageManagement** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera paket hanterings paket på en målnod.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="f8a0f-106">Den här resursen kräver **PackageManagement** -modulen som är tillgänglig från [https://PowerShellGallery.com](https://PowerShellGallery.com) .</span><span class="sxs-lookup"><span data-stu-id="f8a0f-106">This resource requires the **PackageManagement** module, available from [https://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8a0f-107">**PackageManagement** -modulen måste vara minst version 1.1.7.0 för att följande egenskaps information ska vara korrekt.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8a0f-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8a0f-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f8a0f-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8a0f-109">Properties</span></span>

|<span data-ttu-id="f8a0f-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8a0f-110">Property</span></span> |<span data-ttu-id="f8a0f-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8a0f-111">Description</span></span> |
|---|---|
|<span data-ttu-id="f8a0f-112">Name</span><span class="sxs-lookup"><span data-stu-id="f8a0f-112">Name</span></span> |<span data-ttu-id="f8a0f-113">Anger namnet på det paket som ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="f8a0f-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="f8a0f-114">AdditionalParameters</span></span> |<span data-ttu-id="f8a0f-115">Leverantörsspecifik hash-information för parametrar som skulle skickas till `Get-Package -AdditionalArguments` .</span><span class="sxs-lookup"><span data-stu-id="f8a0f-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="f8a0f-116">För NuGet-Provider kan du till exempel skicka ytterligare parametrar som DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="f8a0f-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f8a0f-117">MaximumVersion</span></span> |<span data-ttu-id="f8a0f-118">Anger den högsta tillåtna versionen för det paket som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f8a0f-119">Om du inte lägger till den här parametern hittar resursen den högsta tillgängliga versionen av paketet.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="f8a0f-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f8a0f-120">MinimumVersion</span></span> |<span data-ttu-id="f8a0f-121">Anger den lägsta tillåtna versionen för det paket som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f8a0f-122">Om du inte lägger till den här parametern hittar resursen den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="f8a0f-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="f8a0f-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f8a0f-123">ProviderName</span></span> |<span data-ttu-id="f8a0f-124">Anger ett paket leverantörs namn som du vill använda för att begränsa pakets ökningen.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="f8a0f-125">Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="f8a0f-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f8a0f-126">RequiredVersion</span></span> |<span data-ttu-id="f8a0f-127">Anger den exakta versionen av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="f8a0f-128">Om du inte anger den här parametern installerar DSC-resursen den senaste tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="f8a0f-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="f8a0f-129">Källa</span><span class="sxs-lookup"><span data-stu-id="f8a0f-129">Source</span></span> |<span data-ttu-id="f8a0f-130">Anger namnet på paket källan där paketet kan hittas.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="f8a0f-131">Detta kan antingen vara en URI eller en källa som registrerats med `Register-PackageSource` eller PACKAGEMANAGEMENTSOURCE DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="f8a0f-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="f8a0f-132">SourceCredential</span></span> |<span data-ttu-id="f8a0f-133">Anger ett användar konto som har behörighet att installera ett paket för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="f8a0f-134">Ytterligare parametrar</span><span class="sxs-lookup"><span data-stu-id="f8a0f-134">Additional Parameters</span></span>

<span data-ttu-id="f8a0f-135">I följande tabell visas alternativ för egenskapen AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="f8a0f-136">Parameter</span><span class="sxs-lookup"><span data-stu-id="f8a0f-136">Parameter</span></span> |<span data-ttu-id="f8a0f-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8a0f-137">Description</span></span> |
|---|---|
|<span data-ttu-id="f8a0f-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f8a0f-138">DestinationPath</span></span> |<span data-ttu-id="f8a0f-139">Används av leverantörer, till exempel den inbyggda NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f8a0f-140">Anger en fil Sök väg dit du vill att paketet ska installeras.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="f8a0f-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="f8a0f-141">InstallationPolicy</span></span> |<span data-ttu-id="f8a0f-142">Används av leverantörer, till exempel den inbyggda NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f8a0f-143">Bestämmer om du litar på paketets källa.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="f8a0f-144">Ett av: **ej betrott** eller **betrott**.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f8a0f-145">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8a0f-145">Common properties</span></span>

|<span data-ttu-id="f8a0f-146">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8a0f-146">Property</span></span> |<span data-ttu-id="f8a0f-147">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8a0f-147">Description</span></span> |
|---|---|
|<span data-ttu-id="f8a0f-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8a0f-148">DependsOn</span></span> |<span data-ttu-id="f8a0f-149">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f8a0f-150">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="f8a0f-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f8a0f-151">Kontrol</span><span class="sxs-lookup"><span data-stu-id="f8a0f-151">Ensure</span></span> |<span data-ttu-id="f8a0f-152">Anger om paketet ska installeras eller avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="f8a0f-153">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="f8a0f-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="f8a0f-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f8a0f-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="f8a0f-155">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f8a0f-156">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f8a0f-157">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="f8a0f-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8a0f-158">Exempel</span><span class="sxs-lookup"><span data-stu-id="f8a0f-158">Example</span></span>

<span data-ttu-id="f8a0f-159">I det här exemplet installeras **jQuery** NuGet-paketet och **GistProvider** PowerShell-modulen med hjälp av **PackageManagement** DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="f8a0f-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="f8a0f-160">Det här exemplet säkerställer först att de nödvändiga paket källorna är tillgängliga och definierar sedan det förväntade läget för **jQuery** -och **GistProvider** -paketen (NuGet respektive PowerShell).</span><span class="sxs-lookup"><span data-stu-id="f8a0f-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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
