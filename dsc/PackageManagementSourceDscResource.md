---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagementSource resurs
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="16e9e-103">DSC PackageManagementSource resurs</span><span class="sxs-lookup"><span data-stu-id="16e9e-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="16e9e-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16e9e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="16e9e-105">Den **PackageManagementSource** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att registrera eller avregistrera paketet Management datakällor på målnoden.</span><span class="sxs-lookup"><span data-stu-id="16e9e-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="16e9e-106">**Paketet Management datakällor som har registrerats på så sätt registreras under systemkontext, kan användas av System-kontot eller av DSC-motorn.**</span><span class="sxs-lookup"><span data-stu-id="16e9e-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="16e9e-107">Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="16e9e-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="16e9e-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="16e9e-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="16e9e-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="16e9e-109">Properties</span></span>
|  <span data-ttu-id="16e9e-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="16e9e-110">Property</span></span>  |  <span data-ttu-id="16e9e-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="16e9e-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="16e9e-112">Namn</span><span class="sxs-lookup"><span data-stu-id="16e9e-112">Name</span></span>| <span data-ttu-id="16e9e-113">Anger namnet på paketkällan registreras eller avregistreras på datorn.</span><span class="sxs-lookup"><span data-stu-id="16e9e-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="16e9e-114">Se till att</span><span class="sxs-lookup"><span data-stu-id="16e9e-114">Ensure</span></span>| <span data-ttu-id="16e9e-115">Anger om paketkällan ska registreras eller avregistreras.</span><span class="sxs-lookup"><span data-stu-id="16e9e-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="16e9e-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="16e9e-116">InstallationPolicy</span></span>| <span data-ttu-id="16e9e-117">Anger om du litar på paketkällan.</span><span class="sxs-lookup"><span data-stu-id="16e9e-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="16e9e-118">En av: ”betrodd”, ”betrodd”.</span><span class="sxs-lookup"><span data-stu-id="16e9e-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="16e9e-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="16e9e-119">ProviderName</span></span>| <span data-ttu-id="16e9e-120">Anger namnet på providern OneGet genom vilka du kan interop paketkällan.</span><span class="sxs-lookup"><span data-stu-id="16e9e-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="16e9e-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="16e9e-121">SourceUri</span></span>| <span data-ttu-id="16e9e-122">Anger URI för paketkällan.</span><span class="sxs-lookup"><span data-stu-id="16e9e-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="16e9e-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="16e9e-123">SourceCredential</span></span>| <span data-ttu-id="16e9e-124">Tillhandahåller åtkomst till paketet på en fjärrkälla.</span><span class="sxs-lookup"><span data-stu-id="16e9e-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="16e9e-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="16e9e-125">Example</span></span>

<span data-ttu-id="16e9e-126">Det här exemplet registrerar http://nuget.org paketet källan med den **PackageManagementSource** DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="16e9e-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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

