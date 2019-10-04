---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsFeatureSet-resurs
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941252"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet-resurs

> Gäller för: Windows PowerShell 5. x

**WindowsFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att se till att roller och funktioner läggs till eller tas bort på en målnod. Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsFeature-resursen](windowsfeatureResource.md) för varje funktion som anges i egenskapen **Name** .

Använd den här resursen när du vill konfigurera ett antal Windows-funktioner till samma tillstånd.

## <a name="syntax"></a>Syntax

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|  Egenskap  |  Description   |
|---|---|
|Name |Namnen på de roller eller funktioner som du vill se läggs till eller tas bort. Detta är samma som egenskapen **Name** för cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) och inte visnings namnet för rollerna eller funktionerna. |
|Source |Anger platsen för den käll fil som ska användas för installation, om det behövs. |
|IncludeAllSubFeature |Ange den här egenskapen `$true` till att inkludera alla nödvändiga underfunktioner med de funktioner som du anger med egenskapen **Name** . |
|Certifiering |De autentiseringsuppgifter som ska användas för att lägga till eller ta bort roller och funktioner. |
|LogPath |Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om roller eller funktioner läggs till. Om du vill kontrol lera att rollerna eller funktionerna har lagts till ställer du in den här egenskapen som **tillgänglig**. För att säkerställa att rollerna eller funktionerna tas bort ställer du in egenskapen på **saknas**. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Följande konfiguration säkerställer att funktionerna för **webb server** (IIS) och **SMTP-servern** och alla underfunktioner i respektive är installerade.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```