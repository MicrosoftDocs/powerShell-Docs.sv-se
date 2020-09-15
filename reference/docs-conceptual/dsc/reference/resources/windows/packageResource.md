---
ms.date: 07/16/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Resurs för DSC-paket
ms.openlocfilehash: faeebc5bac7caad733600720f1c9f3d916d4c0a8
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464017"
---
# <a name="dsc-package-resource"></a>Resurs för DSC-paket

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Paket** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera paket, till exempel Windows Installer och setup.exe paket, på en målnod.

## <a name="syntax"></a>Syntax

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Name |Anger namnet på det paket som du vill säkerställa ett speciellt tillstånd för. |
|Sökväg |Anger sökvägen dit paketet finns. |
|ProductId |Anger det produkt-ID som unikt identifierar paketet. |
|Argument |Visar en sträng med argument som skickas till paketet exakt som de anges. |
|Autentiseringsuppgift |Ger åtkomst till paketet på en fjärran sluten källa. Den här egenskapen används inte för att installera paketet. Paketet är alltid installerat på det lokala systemet. |
|LogPath |Anger den fullständiga sökvägen dit du vill att providern ska spara en loggfil för att installera eller avinstallera paketet. |
|ReturnCode |Anger den förväntade retur koden. Om den faktiska retur koden inte matchar det förväntade värdet här, returnerar konfigurationen ett fel. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om paketet är installerat. Ange den här egenskapen som **saknas** för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat). Ange att det är **tillgängligt** för att se till att paketet är installerat. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Det här exemplet kör msi-installationsprogrammet som finns på den angivna sökvägen och har det angivna produkt-ID: t.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```
