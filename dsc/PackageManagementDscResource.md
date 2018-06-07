---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagement resurs
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753795"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 för Windows PowerShell

Den **PackageManagement** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera paketet Management-paketen på målnoden. Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.

> [!IMPORTANT]
> Den **PackageManagement** modulen bör vara minst version 1.1.7.0 med följande information för egenskapen ska vara giltig.

## <a name="syntax"></a>Syntax

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Namn| Anger namnet på paketet som ska installeras eller avinstalleras.|
| AdditionalParameters| Providern specifika hash av parametrar som skickas till `Get-Package -AdditionalArguments`. Du kan till exempel överföra ytterligare parametrar som DestinationPath för NuGet-providern.|
| Se till att| Anger om paketet ska installeras eller avinstalleras.|
| MaximumVersion|Anger högsta tillåtna version av paketet som du vill söka efter. Om du inte lägga till den här parametern hittar den högsta tillgängliga versionen av paketet i resursen.|
| MinimumVersion|Anger det minsta tillåtna version av paketet som du vill söka efter. Om du inte lägga till den här parametern resursen hittar den högsta tillgängliga versionen av paketet som också uppfyller alla angivna högsta version som anges av den _MaximumVersion_ parameter.|
| ProviderName| Anger ett provider-namn för paketet som du vill begränsa sökningen paketet. Du kan hämta paketet providernamn genom att köra den `Get-PackageProvider` cmdlet.|
| RequiredVersion| Anger den exakta versionen av paketet som du vill installera. Om du inte anger den här parametern DSC resursen installerar den senaste tillgängliga versionen av paketet som också uppfyller alla högsta version som anges av den _MaximumVersion_ parameter.|
| Källa| Anger namnet på paketkällan där paketet kan hittas. Detta kan antingen vara en URI eller en källa som har registrerats med `Register-PackageSource` eller PackageManagementSource DSC-resurs.|
| SourceCredential | Anger ett användarkonto som har behörighet att installera ett paket för ett angivet paket provider eller källa.|

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
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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