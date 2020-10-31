---
ms.date: 09/20/2019
ms.topic: reference
title: DSC-tjänst resurs
description: DSC-tjänst resurs
ms.openlocfilehash: 24121688bc46dcef70e3751d243d140fb7fcc7c9
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142632"
---
# <a name="dsc-service-resource"></a>DSC-tjänst resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Tjänst** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på målnoden.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger tjänstens namn. Observera att ibland skiljer det sig från visnings namnet. Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service` cmdleten. |
|BuiltInAccount |Anger det inloggnings konto som ska användas för tjänsten. De värden som tillåts för den här egenskapen är: **LocalService** , **LocalSystem** och **NetworkService** . |
|Autentiseringsuppgift |Anger autentiseringsuppgifter för det konto som tjänsten ska köras under. Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans. |
|Startuptype tjänst |Anger tjänstens starttyp. De värden som tillåts för den här egenskapen är: **Automatisk** , **inaktive rad** och **manuell** . |
|Tillstånd |Anger det tillstånd som du vill säkerställa för tjänsten. Värdena är: **körs** eller **stoppas** . |
|Beroenden | En matris med namnen på de beroenden som tjänsten ska ha. |
|Beskrivning |Anger beskrivningen av mål tjänsten. |
|DisplayName |Anger visnings namnet för mål tjänsten. |
|Sökväg |Anger sökvägen till den binära filen för en ny tjänst. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
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
