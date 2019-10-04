---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC PackageManagementSource-resurs
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942533"
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

## <a name="properties"></a>properties

|Egenskap |Description |
|---|---|
|Name |Anger namnet på den paket källa som ska registreras eller avregistreras i systemet. |
|ProviderName |Anger namnet på den OneGet-provider som du kan interopa med paket källan. |
|SourceLocation |Anger URI för paket källan. |
|InstallationPolicy |Används av leverantörer, till exempel den inbyggda NuGet-providern. Bestämmer om du litar på paketets källa. En av: **Ej betrodd** eller **betrodd**. |
|SourceCredential |Ger åtkomst till paketet på en fjärran sluten källa. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om paket källan ska registreras eller avregistreras. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I `https://nuget.org` det här exemplet registreras paket källan med hjälp av **PackageManagementSource** DSC-resursen.

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