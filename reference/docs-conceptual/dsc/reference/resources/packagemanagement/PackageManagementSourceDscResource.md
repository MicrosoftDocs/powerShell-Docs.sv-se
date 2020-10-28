---
ms.date: 07/15/2020
ms.topic: reference
title: DSC PackageManagementSource-resurs
description: DSC PackageManagementSource-resurs
ms.openlocfilehash: 4842a13dbf06073080c0dd02be986b0d7ba051d0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667359"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource-resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**PackageManagementSource** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att registrera eller avregistrera paket hanterings källor på en målnod.
**Paket hanterings källor som registreras på det här sättet registreras under system kontexten, vilket kan användas av system kontot eller av DSC-motorn.** Den här resursen kräver modulen **PackageManagement** , som är tillgänglig från [PowerShell-galleriet](https://PowerShellGallery.com).

> [!IMPORTANT]
> **PackageManagement** -modulen måste vara minst version 1.1.7.0 för att följande egenskaps information ska vara korrekt.

## <a name="syntax"></a>Syntax

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på den paket källa som ska registreras eller avregistreras i systemet. |
|ProviderName |Anger namnet på den OneGet-provider som du kan interopa med paket källan. |
|SourceLocation |Anger URI för paket källan. |
|InstallationPolicy |Används av leverantörer, till exempel den inbyggda NuGet-providern. Bestämmer om du litar på paketets källa. Ett av: **ej betrott** eller **betrott** . |
|SourceCredential |Ger åtkomst till paketet på en fjärran sluten källa. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om paket källan ska registreras eller avregistreras. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I det här exemplet registreras `https://nuget.org` paket källan med hjälp av **PackageManagementSource** DSC-resursen.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
