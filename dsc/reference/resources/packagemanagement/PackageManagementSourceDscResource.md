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
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource Resource

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

Den **PackageManagementSource** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att registrera eller avregistrera pakethantering källor på målnoden. **Paketet Management datakällor som registrerats på så sätt registreras under systemkontexten kan användas av System-kontot eller av DSC-motorn.** Den här resursen kräver den **PackageManagement** modulen, som är tillgängliga från http://PowerShellGallery.com.

> [!IMPORTANT]
> Den **PackageManagement** modul bör vara minst version 1.1.7.0 för egenskapen följande ska vara giltig.

## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Namn| Anger namnet på paketkällan för att registreras eller avregistreras på datorn.|
| ProviderName| Anger namnet på providern OneGet genom vilka du kan interop med paketkällan.|
| SourceLocation| Anger URI för paketkällan.|
| Se till att| Anger om paketkällan ska registreras eller avregistreras.|
| InstallationPolicy| Används av providrar, till exempel inbyggda Nuget-providern. Anger om du litar på den paketkällan. En av: "Untrusted", "Trusted".|
| SourceCredential| Ger åtkomst till paketet på en fjärransluten källa.|

## <a name="example"></a>Exempel

Det här exemplet registrerar den http://nuget.org paketet datakällan med den **PackageManagementSource** DSC-resurs.

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