---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC ServiceSet-resurs
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324119"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet-resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**ServiceSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på målnoden. Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [tjänst resursen](serviceResource.md) för varje tjänst som anges i egenskapen **Name** .

Använd den här resursen när du vill konfigurera ett antal tjänster till samma tillstånd.

## <a name="syntax"></a>Syntax

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Egenskap |Description |
|---|---|
|Name |Anger tjänst namn. Observera att ibland skiljer det sig från visnings namnen. Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service` cmdleten. |
|Startuptype tjänst |Anger start typen för tjänsterna. De värden som tillåts för den här egenskapen är: **Automatiskt**, **inaktiverat**och **manuellt**. |
|BuiltInAccount |Anger det inloggnings konto som ska användas för tjänsterna. De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**och **NetworkService**. |
|State |Anger det tillstånd som du vill säkerställa för tjänsterna: **Stoppas** eller **körs**inte. |
|Certifiering |Anger autentiseringsuppgifter för det konto som tjänst resursen kommer att köras under. Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om tjänsterna finns i systemet. Ange den här egenskapen som **saknas** för att säkerställa att tjänsterna inte finns. Att ställa in det för att **Visa** garanterar att mål tjänsterna finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Följande konfiguration startar tjänsterna Windows Audio och Fjärrskrivbordstjänster.

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```