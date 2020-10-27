---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-logg resurs
description: DSC-logg resurs
ms.openlocfilehash: c5d965924ac8cc9bb68cf7b4e17c4e521a20548f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650436"
---
# <a name="dsc-log-resource"></a>DSC-logg resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Logg** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att skriva meddelanden till Microsoft-Windows-önskad tillstånds konfiguration/analytisk händelse logg.

## <a name="syntax"></a>Syntax

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> Som standard är bara drift loggar för DSC aktiverade. Innan den analytiska loggen blir tillgänglig eller synlig måste den vara aktive rad. Mer information finns i [var är DSC-händelseloggar?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Egenskaper

| Egenskap |                                                   Beskrivning                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| Meddelande  | Anger det meddelande som du vill skriva till Microsoft-Windows-önskad tillstånds konfiguration/analytisk händelse logg. |

## <a name="common-properties"></a>Gemensamma egenskaper

|       Egenskap       |                                                                                                                                                          Beskrivning                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DependsOn            | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
| PsDscRunAsCredential | Anger autentiseringsuppgifter för att köra hela resursen som.                                                                                                                                                                                                                                                                        |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du inkluderar ett meddelande i Microsoft-Windows-Desired State Configuration/analytisk händelse logg.

> [!NOTE]
> Om du kör [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) med den här resursen konfigurerad kommer den alltid att returnera **$false** .

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
