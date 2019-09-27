---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC PackageManagement-resurs
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324612"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement-resurs

Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0, Windows PowerShell 5,1

**PackageManagement** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera paket hanterings paket på en målnod. Den här resursen kräver **PackageManagement** -modulen som är [http://PowerShellGallery.com](https://PowerShellGallery.com)tillgänglig från.

> [!IMPORTANT]
> **PackageManagement** -modulen måste vara minst version 1.1.7.0 för att följande egenskaps information ska vara korrekt.

## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>properties

|Egenskap |Description |
|---|---|
|Name |Anger namnet på det paket som ska installeras eller avinstalleras. |
|AdditionalParameters |Leverantörsspecifik hash-information för parametrar som skulle skickas till `Get-Package -AdditionalArguments`. För NuGet-Provider kan du till exempel skicka ytterligare parametrar som DestinationPath. |
|MaximumVersion |Anger den högsta tillåtna versionen för det paket som du vill hitta. Om du inte lägger till den här parametern hittar resursen den högsta tillgängliga versionen av paketet. |
|MinimumVersion |Anger den lägsta tillåtna versionen för det paket som du vill hitta. Om du inte lägger till den här parametern hittar resursen den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern **MaximumVersion** . |
|ProviderName |Anger ett paket leverantörs namn som du vill använda för att begränsa pakets ökningen. Du kan hämta paket leverantörs namn genom att `Get-PackageProvider` köra cmdleten. |
|RequiredVersion |Anger den exakta versionen av paketet som du vill installera. Om du inte anger den här parametern installerar DSC-resursen den senaste tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern **MaximumVersion** . |
|Source |Anger namnet på paket källan där paketet kan hittas. Detta kan antingen vara en URI eller en källa som registrerats med `Register-PackageSource` eller PackageManagementSource DSC-resurs. |
|SourceCredential |Anger ett användar konto som har behörighet att installera ett paket för en angiven paket leverantör eller källa. |

## <a name="additional-parameters"></a>Ytterligare parametrar

I följande tabell visas alternativ för egenskapen AdditionalParameters.

|Parameter |Beskrivning |
|---|---|
|DestinationPath |Används av leverantörer, till exempel den inbyggda NuGet-providern. Anger en fil Sök väg dit du vill att paketet ska installeras. |
|InstallationPolicy |Används av leverantörer, till exempel den inbyggda NuGet-providern. Bestämmer om du litar på paketets källa. En av: **Ej betrodd** eller **betrodd**. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om paketet ska installeras eller avinstalleras. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I det här exemplet installeras **jQuery** NuGet-paketet och **GistProvider** PowerShell-modulen med hjälp av **PackageManagement** DSC-resursen. Det här exemplet säkerställer först att de nödvändiga paket källorna är tillgängliga och definierar sedan det förväntade läget för **jQuery** -och **GistProvider** -paketen (NuGet respektive PowerShell).

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