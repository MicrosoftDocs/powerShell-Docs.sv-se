---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagementSource resurs
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="93b76-103">DSC PackageManagementSource resurs</span><span class="sxs-lookup"><span data-stu-id="93b76-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="93b76-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="93b76-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="93b76-105">Den **PackageManagementSource** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att registrera eller avregistrera paketet Management datakällor på målnoden.</span><span class="sxs-lookup"><span data-stu-id="93b76-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="93b76-106">**Paketet Management datakällor som har registrerats på så sätt registreras under systemkontext, kan användas av System-kontot eller av DSC-motorn.**</span><span class="sxs-lookup"><span data-stu-id="93b76-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="93b76-107">Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="93b76-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="93b76-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="93b76-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="93b76-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="93b76-109">Properties</span></span>
|  <span data-ttu-id="93b76-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="93b76-110">Property</span></span>  |  <span data-ttu-id="93b76-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="93b76-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="93b76-112">Namn</span><span class="sxs-lookup"><span data-stu-id="93b76-112">Name</span></span>| <span data-ttu-id="93b76-113">Anger namnet på paketkällan registreras eller avregistreras på datorn.</span><span class="sxs-lookup"><span data-stu-id="93b76-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="93b76-114">Se till att</span><span class="sxs-lookup"><span data-stu-id="93b76-114">Ensure</span></span>| <span data-ttu-id="93b76-115">Anger om paketkällan ska registreras eller avregistreras.</span><span class="sxs-lookup"><span data-stu-id="93b76-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="93b76-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="93b76-116">InstallationPolicy</span></span>| <span data-ttu-id="93b76-117">Anger om du litar på paketkällan.</span><span class="sxs-lookup"><span data-stu-id="93b76-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="93b76-118">En av: ”betrodd”, ”betrodd”.</span><span class="sxs-lookup"><span data-stu-id="93b76-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="93b76-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="93b76-119">ProviderName</span></span>| <span data-ttu-id="93b76-120">Anger namnet på providern OneGet genom vilka du kan interop paketkällan.</span><span class="sxs-lookup"><span data-stu-id="93b76-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="93b76-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="93b76-121">SourceUri</span></span>| <span data-ttu-id="93b76-122">Anger URI för paketkällan.</span><span class="sxs-lookup"><span data-stu-id="93b76-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="93b76-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="93b76-123">SourceCredential</span></span>| <span data-ttu-id="93b76-124">Tillhandahåller åtkomst till paketet på en fjärrkälla.</span><span class="sxs-lookup"><span data-stu-id="93b76-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="93b76-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="93b76-125">Example</span></span>

<span data-ttu-id="93b76-126">Det här exemplet registrerar den http://nuget.org källa med den **PackageManagementSource** DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="93b76-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```