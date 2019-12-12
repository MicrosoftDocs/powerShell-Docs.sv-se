---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsFeature-resurs
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942421"
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature-resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**WindowsFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att se till att roller och funktioner läggs till eller tas bort på en målnod.

## <a name="syntax"></a>Syntax

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på den roll eller funktion som du vill se till att den läggs till eller tas bort. Detta är samma som egenskapen **Name** från cmdleten [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) och inte visnings namnet för rollen eller funktionen. |
|Autentiseringsuppgift |Anger de autentiseringsuppgifter som ska användas för att lägga till eller ta bort rollen eller funktionen. |
|IncludeAllSubFeature |Ange den här egenskapen till `$true` för att se till att alla nödvändiga underfunktioner har statusen för den funktion som du anger med egenskapen **Name** . |
|LogPath |Anger sökvägen till en loggfil där du vill att resurs leverantören ska logga åtgärden. |
|Källa |Anger platsen för den käll fil som ska användas för installation, om det behövs. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`. |
|Kontrol |Anger om rollen eller funktionen har lagts till. Om du vill se till att rollen eller funktionen har lagts till ställer du in den här egenskapen som **tillgänglig**. För att säkerställa att rollen eller funktionen tas bort ställer du in egenskapen på **saknas**. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```