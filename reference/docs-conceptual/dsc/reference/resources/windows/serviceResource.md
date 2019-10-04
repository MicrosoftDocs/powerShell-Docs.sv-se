---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-tjänst resurs
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941315"
---
# <a name="dsc-service-resource"></a>DSC-tjänst resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Tjänst** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på målnoden.

## <a name="syntax"></a>Syntax

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Egenskap |Description |
|---|---|
|Name |Anger tjänstens namn. Observera att ibland skiljer det sig från visnings namnet. Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service` cmdleten. |
|BuiltInAccount |Anger det inloggnings konto som ska användas för tjänsten. De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**och **NetworkService**. |
|Certifiering |Anger autentiseringsuppgifter för det konto som tjänsten ska köras under. Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans. |
|Startuptype tjänst |Anger tjänstens starttyp. De värden som tillåts för den här egenskapen är: **Automatiskt**, **inaktiverat**och **manuellt**. |
|State |Anger det tillstånd som du vill säkerställa för tjänsten. Värdena är: **Körs** eller **stoppas**. |
|Beskrivning |Anger beskrivningen av mål tjänsten. |
|DisplayName |Anger visnings namnet för mål tjänsten. |
|`Path` |Anger sökvägen till den binära filen för en ny tjänst. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om mål tjänsten finns i systemet. Ange den här egenskapen som **saknas** för att säkerställa att mål tjänsten inte finns. Att ställa in den så att den **visar** garanterar att mål tjänsten finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```