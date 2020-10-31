---
ms.date: 07/15/2020
ms.topic: reference
title: DSC PackageManagement-resurs
description: DSC PackageManagement-resurs
ms.openlocfilehash: 83839adbef8bd8d3265a06b44a3101108b2a4486
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142913"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement-resurs

Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0, Windows PowerShell 5,1

**PackageManagement** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera paket hanterings paket på en målnod. Den här resursen kräver **PackageManagement** -modulen som är tillgänglig från [https://PowerShellGallery.com](https://PowerShellGallery.com) .

> [!IMPORTANT]
> **PackageManagement** -modulen måste vara minst version 1.1.7.0 för att följande egenskaps information ska vara korrekt.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på det paket som ska installeras eller avinstalleras. |
|AdditionalParameters |Leverantörsspecifik hash-information för parametrar som skulle skickas till `Get-Package -AdditionalArguments` . För NuGet-Provider kan du till exempel skicka ytterligare parametrar som DestinationPath. |
|MaximumVersion |Anger den högsta tillåtna versionen för det paket som du vill hitta. Om du inte lägger till den här parametern hittar resursen den högsta tillgängliga versionen av paketet. |
|MinimumVersion |Anger den lägsta tillåtna versionen för det paket som du vill hitta. Om du inte lägger till den här parametern hittar resursen den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern **MaximumVersion** . |
|ProviderName |Anger ett paket leverantörs namn som du vill använda för att begränsa pakets ökningen. Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten. |
|RequiredVersion |Anger den exakta versionen av paketet som du vill installera. Om du inte anger den här parametern installerar DSC-resursen den senaste tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern **MaximumVersion** . |
|Källa |Anger namnet på paket källan där paketet kan hittas. Detta kan antingen vara en URI eller en källa som registrerats med `Register-PackageSource` eller PACKAGEMANAGEMENTSOURCE DSC-resurs. |
|SourceCredential |Anger ett användar konto som har behörighet att installera ett paket för en angiven paket leverantör eller källa. |

## <a name="additional-parameters"></a>Ytterligare parametrar

I följande tabell visas alternativ för egenskapen AdditionalParameters.

|Parameter |Beskrivning |
|---|---|
|DestinationPath |Används av leverantörer, till exempel den inbyggda NuGet-providern. Anger en fil Sök väg dit du vill att paketet ska installeras. |
|InstallationPolicy |Används av leverantörer, till exempel den inbyggda NuGet-providern. Bestämmer om du litar på paketets källa. Ett av: **ej betrott** eller **betrott** . |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
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
