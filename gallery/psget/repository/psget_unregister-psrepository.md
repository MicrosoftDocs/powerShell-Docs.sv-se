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
# <a name="unregister-psrepository"></a>Avregistrera PSRepository

Avregistrerar en databas.

## <a name="description"></a>Beskrivning

Avregistrera PSRepository cmdlet Avregistrerar en lagringsplats för den aktuella användaren.
- Avregistrering av och omregistrering av PSGallery databasen tillåts för ett företag och frånkopplad scenarier.
- Användare kan registrera PSGallery genom att bara köra`Register-PSRepository -Default`
- Eftersom PSGallery är standard publicera databasen i Publicera modul och publicera skript-cmdlets, genereras ett fel om PSGallery inte är tillgänglig i databaslistan över registrerade.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Avregistrera PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Exempel på kommandon

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Avregistrering av och omregistrering av PSGallery databasen tillåts för ett företag och frånkopplad scenarier.
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

