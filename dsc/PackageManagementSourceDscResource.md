---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC PackageManagementSource resurs
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **PackageManagementSource** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att registrera eller avregistrera paketet Management datakällor på målnoden. **Paketet Management datakällor som har registrerats på så sätt registreras under systemkontext, kan användas av System-kontot eller av DSC-motorn.** Den här resursen kräver den **PackageManagement** modulen från http://PowerShellGallery.com.

## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger namnet på paketkällan registreras eller avregistreras på datorn.| 
| Se till att| Anger om paketkällan ska registreras eller avregistreras.| 
| InstallationPolicy| Anger om du litar på paketkällan. En av: ”betrodd”, ”betrodd”.| 
| ProviderName| Anger namnet på providern OneGet genom vilka du kan interop paketkällan.| 
| SourceUri| Anger URI för paketkällan.| 
| SourceCredential| Tillhandahåller åtkomst till paketet på en fjärrkälla.| 

## <a name="example"></a>Exempel

Det här exemplet registrerar http://nuget.org paketet källan med den **PackageManagementSource** DSC-resurs.

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
