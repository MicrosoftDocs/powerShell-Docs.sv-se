---
ms.date: 07/15/2020
ms.topic: reference
title: DSC PackageManagementSource-resurs
description: DSC PackageManagementSource-resurs
ms.openlocfilehash: 4842a13dbf06073080c0dd02be986b0d7ba051d0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667359"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="cf306-103">DSC PackageManagementSource-resurs</span><span class="sxs-lookup"><span data-stu-id="cf306-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="cf306-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="cf306-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="cf306-105">**PackageManagementSource** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att registrera eller avregistrera paket hanterings källor på en målnod.</span><span class="sxs-lookup"><span data-stu-id="cf306-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="cf306-106">**Paket hanterings källor som registreras på det här sättet registreras under system kontexten, vilket kan användas av system kontot eller av DSC-motorn.**</span><span class="sxs-lookup"><span data-stu-id="cf306-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="cf306-107">Den här resursen kräver modulen **PackageManagement** , som är tillgänglig från [PowerShell-galleriet](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="cf306-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf306-108">**PackageManagement** -modulen måste vara minst version 1.1.7.0 för att följande egenskaps information ska vara korrekt.</span><span class="sxs-lookup"><span data-stu-id="cf306-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf306-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="cf306-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="cf306-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="cf306-110">Properties</span></span>

|<span data-ttu-id="cf306-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="cf306-111">Property</span></span> |<span data-ttu-id="cf306-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cf306-112">Description</span></span> |
|---|---|
|<span data-ttu-id="cf306-113">Namn</span><span class="sxs-lookup"><span data-stu-id="cf306-113">Name</span></span> |<span data-ttu-id="cf306-114">Anger namnet på den paket källa som ska registreras eller avregistreras i systemet.</span><span class="sxs-lookup"><span data-stu-id="cf306-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="cf306-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="cf306-115">ProviderName</span></span> |<span data-ttu-id="cf306-116">Anger namnet på den OneGet-provider som du kan interopa med paket källan.</span><span class="sxs-lookup"><span data-stu-id="cf306-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="cf306-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="cf306-117">SourceLocation</span></span> |<span data-ttu-id="cf306-118">Anger URI för paket källan.</span><span class="sxs-lookup"><span data-stu-id="cf306-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="cf306-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="cf306-119">InstallationPolicy</span></span> |<span data-ttu-id="cf306-120">Används av leverantörer, till exempel den inbyggda NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="cf306-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="cf306-121">Bestämmer om du litar på paketets källa.</span><span class="sxs-lookup"><span data-stu-id="cf306-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="cf306-122">Ett av: **ej betrott** eller **betrott** .</span><span class="sxs-lookup"><span data-stu-id="cf306-122">One of: **Untrusted** or **Trusted** .</span></span> |
|<span data-ttu-id="cf306-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="cf306-123">SourceCredential</span></span> |<span data-ttu-id="cf306-124">Ger åtkomst till paketet på en fjärran sluten källa.</span><span class="sxs-lookup"><span data-stu-id="cf306-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="cf306-125">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="cf306-125">Common properties</span></span>

|<span data-ttu-id="cf306-126">Egenskap</span><span class="sxs-lookup"><span data-stu-id="cf306-126">Property</span></span> |<span data-ttu-id="cf306-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cf306-127">Description</span></span> |
|---|---|
|<span data-ttu-id="cf306-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cf306-128">DependsOn</span></span> |<span data-ttu-id="cf306-129">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="cf306-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cf306-130">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="cf306-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="cf306-131">Kontrol</span><span class="sxs-lookup"><span data-stu-id="cf306-131">Ensure</span></span> |<span data-ttu-id="cf306-132">Anger om paket källan ska registreras eller avregistreras.</span><span class="sxs-lookup"><span data-stu-id="cf306-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="cf306-133">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="cf306-133">The default value is **Present** .</span></span> |
|<span data-ttu-id="cf306-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="cf306-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="cf306-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="cf306-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="cf306-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="cf306-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="cf306-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="cf306-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf306-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="cf306-138">Example</span></span>

<span data-ttu-id="cf306-139">I det här exemplet registreras `https://nuget.org` paket källan med hjälp av **PackageManagementSource** DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="cf306-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
