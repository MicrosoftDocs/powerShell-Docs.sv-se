---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-logg resurs
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942449"
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

|Egenskap |Beskrivning |
|---|---|
|Meddelande |Anger det meddelande som du vill skriva till Microsoft-Windows-önskad tillstånds konfiguration/analytisk händelse logg. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du inkluderar ett meddelande i Microsoft-Windows-Desired State Configuration/analytisk händelse logg.

> [!NOTE]
> Om du kör [test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) med den här resursen konfigurerad kommer den alltid att returnera **$false**.

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