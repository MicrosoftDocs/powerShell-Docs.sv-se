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
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **PackageManagement** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera paketet Management-paketen på målnoden. Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.

## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger namnet på paketet som ska installeras eller avinstalleras.| 
| Källa| Anger namnet på paketkällan där paketet kan hittas. Detta kan antingen vara en URI eller en källa som har registrerats med registrera PackageSource eller PackageManagementSource DSC-resurs. DSC-resursen MSFT_PackageManagementSource kan också registrera en paketkällan.| 
| Se till att| Anger om paketet ska installeras eller avinstalleras.| 
| RequiredVersion| Anger den exakta versionen av paketet som du vill installera. Om du inte anger den här parametern installerar den senaste tillgängliga versionen av paketet som också uppfyller alla högsta version som anges av parametern MaximumVersion i den här DSC-resursen.| 
| MinimumVersion| Anger det minsta tillåtna version av paketet som du vill installera. Om du inte lägga till den här parametern anges den här DSC resurs intalls högsta tillgängliga versionen av paketet som också uppfyller eventuella maximalt angivna versionen av parametern MaximumVersion.| 
| MaximumVersion| Anger högsta tillåtna version av paketet som du vill installera. Om du inte anger den här parametern installerar den här DSC-resursen högsta numret tillgänglig version av paketet.| 
| SourceCredential | Anger ett användarkonto som har behörighet att installera ett paket för ett angivet paket provider eller källa.| 
| ProviderName| Anger ett provider-namn för paketet som du vill begränsa sökningen paketet. Du kan hämta paketet providernamn genom att köra cmdlet Get-PackageProvider.| 
| AdditionalParameters| Providern specifika parametrar som skickas som en hash-tabell. Du kan till exempel överföra ytterligare parametrar som DestinationPath för NuGet-providern.| 

## <a name="additional-parameters"></a>Ytterligare parametrar
I följande tabell visas alternativ för egenskapen AdditionalParameters.
|  Parameter  | Beskrivning   | 
|---|---|
| Målsökväg| Används av providrar, till exempel den inbyggda Nuget-providern. Anger en plats där du vill att paket som ska installeras.|
| InstallationPolicy| Används av providrar, till exempel den inbyggda Nuget-providern. Anger om du litar på den paketkällan. En av: ”betrodd”, ”betrodd”.|

## <a name="example"></a>Exempel

Det här exemplet installerar den **JQuery** NuGet-paketet och **GistProvider** PowerShell-modulen använder den **PackageManagement** DSC-resurs. Det här exemplet ser först källorna nödvändigt paket är tillgängliga och sedan definierar förväntade tillståndet för den **JQuery** och **GistProvider** paket (NuGet och PowerShell, respektive).

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

