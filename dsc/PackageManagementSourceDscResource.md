---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagementSource resurs
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753778"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 för Windows PowerShell

Den **PackageManagementSource** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att registrera eller avregistrera paketet Management datakällor på målnoden. **Paketet Management datakällor som har registrerats på så sätt registreras under systemkontext, kan användas av System-kontot eller av DSC-motorn.** Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.

> [!IMPORTANT]
> Den **PackageManagement** modulen bör vara minst version 1.1.7.0 med följande information för egenskapen ska vara giltig.

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
| Namn| Anger namnet på paketkällan registreras eller avregistreras på datorn.|
| ProviderName| Anger namnet på providern OneGet genom vilka du kan interop paketkällan.|
| SourceLocation| Anger URI för paketkällan.|
| Se till att| Anger om paketkällan ska registreras eller avregistreras.|
| InstallationPolicy| Används av providrar, till exempel den inbyggda Nuget-providern. Anger om du litar på den paketkällan. En av: ”betrodd”, ”betrodd”.|
| SourceCredential| Tillhandahåller åtkomst till paketet på en fjärrkälla.|

## <a name="example"></a>Exempel

Det här exemplet registrerar den http://nuget.org källa med den **PackageManagementSource** DSC-resurs.

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