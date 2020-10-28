---
ms.date: 09/20/2019
ms.topic: reference
title: DSC-tjänst resurs
description: DSC-tjänst resurs
ms.openlocfilehash: 68055983a8d2880b4d556fe990310f439afffe41
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664184"
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
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger tjänstens namn. Observera att ibland skiljer det sig från visnings namnet. Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service` cmdleten. |
|BuiltInAccount |Anger det inloggnings konto som ska användas för tjänsten. De värden som tillåts för den här egenskapen är: **LocalService** , **LocalSystem** och **NetworkService** . |
|Autentiseringsuppgift |Anger autentiseringsuppgifter för det konto som tjänsten ska köras under. Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans. |
|StartupTimeout | Vänte tiden innan tjänsten körs i millisekunder.|
|Startuptype tjänst |Anger tjänstens starttyp. De värden som tillåts för den här egenskapen är: **Automatisk** , **inaktive rad** och **manuell** . |
|Tillstånd |Anger det tillstånd som du vill säkerställa för tjänsten. Värdena är: **körs** eller **stoppas** . |
|TerminateTimeout |Vänte tiden innan tjänsten stoppas i millisekunder.|
|Beroenden | En matris med namnen på de beroenden som tjänsten ska ha. |
|Beskrivning |Anger beskrivningen av mål tjänsten. |
|DesktopInteract | Anger om tjänsten ska kunna kommunicera med ett fönster på Skriv bordet. Måste vara false för tjänster som inte körs som LocalSystem.|
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
