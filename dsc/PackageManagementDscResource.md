---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagement resurs
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268100"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement resurs

Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

Den **PackageManagement** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att installera eller avinstallera pakethantering paket på målnoden. Den här resursen kräver den **PackageManagement** modulen, som är tillgängliga från [ http://PowerShellGallery.com ](http://PowerShellGallery.com).

> [!IMPORTANT]
> Den **PackageManagement** modul bör vara minst version 1.1.7.0 för egenskapen följande ska vara giltig.

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

| Egenskap | Beskrivning |
| --- | --- |
| Namn| Anger namnet på paketet installeras eller avinstalleras.|
| AdditionalParameters| Providern specifika hashtabell med parametrar som skulle skickas till `Get-Package -AdditionalArguments`. Du kan exempelvis skicka ytterligare parametrar som målsökväg för NuGet-providern.|
| Se till att| Anger om paketet ska installeras eller avinstalleras.|
| MaximumVersion|Anger det högsta tillåtna version av det paket som du vill söka efter. Om du inte lägga till den här parametern hittar den senaste tillgängliga versionen av paketet i resursen.|
| MinimumVersion|Anger den lägsta tillåtna versionen på det paket som du vill söka efter. Om du inte lägga till den här parametern resursen hittar den högsta tillgängliga versionen av paketet som också uppfyller alla högsta angivna version som anges av den _MaximumVersion_ parametern.|
| ProviderName| Anger ett namn på providern som du vill begränsa sökningen paketet. Du kan hämta paketet providernamn genom att köra den `Get-PackageProvider` cmdlet.|
| RequiredVersion| Anger den exakta versionen av det paket som du vill installera. Om du inte anger den här parametern, den här DSC-resursen installerar den senaste tillgängliga versionen av paketet som också uppfyller alla högsta version som anges av den _MaximumVersion_ parametern.|
| Källa| Anger namnet på paketkällan där paketet kan hittas. Detta kan vara en URI eller en källa som har registrerats med `Register-PackageSource` eller PackageManagementSource DSC-resurs.|
| SourceCredential | Anger ett användarkonto som har behörighet att installera ett paket för en angiven paket-providern eller källa.|

## <a name="additional-parameters"></a>Ytterligare parametrar

I följande tabell visas alternativ för egenskapen AdditionalParameters.

| Parameter | Beskrivning |
| --- | --- |
| Målsökväg| Används av providrar, till exempel inbyggda Nuget-providern. Anger en plats där du vill att paketet installeras.|
| InstallationPolicy| Används av providrar, till exempel inbyggda Nuget-providern. Anger om du litar på den paketkällan. En av: `Untrusted`, `Trusted`.|

## <a name="example"></a>Exempel

Det här exemplet installerar den **JQuery** NuGet-paketet och **GistProvider** PowerShell-modulen med den **PackageManagement** DSC-resurs. Det här exemplet ser först till källor för paket som krävs är tillgängliga och sedan definierar det förväntade tillståndet för den **JQuery** och **GistProvider** paket (NuGet och PowerShell, respektive).

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