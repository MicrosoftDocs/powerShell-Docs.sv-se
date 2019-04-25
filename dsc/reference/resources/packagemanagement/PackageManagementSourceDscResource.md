---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagementSource Resource
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077593"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="6cc8e-103">DSC PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="6cc8e-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="6cc8e-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="6cc8e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="6cc8e-105">Den **PackageManagementSource** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att registrera eller avregistrera pakethantering källor på målnoden.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="6cc8e-106">**Paketet Management datakällor som registrerats på så sätt registreras under systemkontexten kan användas av System-kontot eller av DSC-motorn.**</span><span class="sxs-lookup"><span data-stu-id="6cc8e-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="6cc8e-107">Den här resursen kräver den **PackageManagement** modulen, som är tillgängliga från http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc8e-108">Den **PackageManagement** modul bör vara minst version 1.1.7.0 för egenskapen följande ska vara giltig.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="6cc8e-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="6cc8e-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="6cc8e-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6cc8e-110">Properties</span></span>

|  <span data-ttu-id="6cc8e-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6cc8e-111">Property</span></span>  |  <span data-ttu-id="6cc8e-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6cc8e-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="6cc8e-113">Namn</span><span class="sxs-lookup"><span data-stu-id="6cc8e-113">Name</span></span>| <span data-ttu-id="6cc8e-114">Anger namnet på paketkällan för att registreras eller avregistreras på datorn.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="6cc8e-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="6cc8e-115">ProviderName</span></span>| <span data-ttu-id="6cc8e-116">Anger namnet på providern OneGet genom vilka du kan interop med paketkällan.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="6cc8e-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="6cc8e-117">SourceLocation</span></span>| <span data-ttu-id="6cc8e-118">Anger URI för paketkällan.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="6cc8e-119">Se till att</span><span class="sxs-lookup"><span data-stu-id="6cc8e-119">Ensure</span></span>| <span data-ttu-id="6cc8e-120">Anger om paketkällan ska registreras eller avregistreras.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="6cc8e-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="6cc8e-121">InstallationPolicy</span></span>| <span data-ttu-id="6cc8e-122">Används av providrar, till exempel inbyggda Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6cc8e-123">Anger om du litar på den paketkällan.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="6cc8e-124">En av: "Untrusted", "Trusted".</span><span class="sxs-lookup"><span data-stu-id="6cc8e-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="6cc8e-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="6cc8e-125">SourceCredential</span></span>| <span data-ttu-id="6cc8e-126">Ger åtkomst till paketet på en fjärransluten källa.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="6cc8e-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="6cc8e-127">Example</span></span>

<span data-ttu-id="6cc8e-128">Det här exemplet registrerar den http://nuget.org paketet datakällan med den **PackageManagementSource** DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6cc8e-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```