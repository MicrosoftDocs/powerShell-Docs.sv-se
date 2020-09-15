---
ms.date: 07/16/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsPackageCab-resurs
ms.openlocfilehash: 7205a454d100bb369fd6cf0c5ac419585c8bbe86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464153"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab-resurs

> Gäller för: Windows PowerShell 5,1

**WindowsPackageCab** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera Windows kabinett paket (. cab) på en målnod.

Målnod måste ha DISM PowerShell-modulen installerad. Mer information finns i [använda DISM i Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).

## <a name="syntax"></a>Syntax

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Name |Anger namnet på det paket som du vill säkerställa ett speciellt tillstånd för. |
|Sök |Anger sökvägen dit paketet finns. |
|LogPath |Anger den fullständiga sökvägen dit du vill att providern ska spara en loggfil för att installera eller avinstallera paketet. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om paketet är installerat. Ange den här egenskapen som **saknas** för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat). Ange att det är **tillgängligt** för att se till att paketet är installerat. **Se till att** det finns en obligatorisk egenskap för **WindowsPackageCab** -resursen. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

## <a name="example"></a>Exempel

Följande exempel konfiguration använder indataparametrar och säkerställer att CAB-filen som anges av `$Name` parametern är installerad.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
