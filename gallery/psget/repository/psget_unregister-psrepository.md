---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Avregistrera PSRepository
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="unregister-psrepository"></a><span data-ttu-id="5ad96-103">Avregistrera PSRepository</span><span class="sxs-lookup"><span data-stu-id="5ad96-103">Unregister-PSRepository</span></span>

<span data-ttu-id="5ad96-104">Avregistrerar en databas.</span><span class="sxs-lookup"><span data-stu-id="5ad96-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="5ad96-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ad96-105">Description</span></span>

<span data-ttu-id="5ad96-106">Avregistrera PSRepository cmdlet Avregistrerar en lagringsplats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5ad96-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="5ad96-107">Avregistrering av och omregistrering av PSGallery databasen tillåts för ett företag och frånkopplad scenarier.</span><span class="sxs-lookup"><span data-stu-id="5ad96-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="5ad96-108">Användare kan registrera PSGallery genom att bara köra`Register-PSRepository -Default`</span><span class="sxs-lookup"><span data-stu-id="5ad96-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="5ad96-109">Eftersom PSGallery är standard publicera databasen i Publicera modul och publicera skript-cmdlets, genereras ett fel om PSGallery inte är tillgänglig i databaslistan över registrerade.</span><span class="sxs-lookup"><span data-stu-id="5ad96-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="5ad96-110">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="5ad96-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="5ad96-111">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="5ad96-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="5ad96-112">Avregistrera PSRepository</span><span class="sxs-lookup"><span data-stu-id="5ad96-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="5ad96-113">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="5ad96-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="5ad96-114">Avregistrering av och omregistrering av PSGallery databasen tillåts för ett företag och frånkopplad scenarier.</span><span class="sxs-lookup"><span data-stu-id="5ad96-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

