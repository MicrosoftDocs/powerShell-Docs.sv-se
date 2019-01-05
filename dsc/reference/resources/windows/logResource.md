---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Loggresurs
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048682"
---
# <a name="dsc-log-resource"></a>DSC-Loggresurs

> _Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_

Den __Log__ resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att skriva meddelanden till Microsoft-Windows-Desired State Configuration / analytiska händelseloggen.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Endast de operativa loggarna för DSC är aktiverade som standard. Innan den analytiska loggen kommer att vara tillgängliga eller synliga, måste vara aktiverat. Mer information finns i [där är DSC-händelseloggar?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Egenskaper

| Egenskap | Beskrivning |
| --- | --- |
| Meddelande| Anger vilket meddelande som du vill skriva till händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analytiska.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här loggmeddelande skrivs. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Exempel

I följande exempel visar hur du inkludera ett meddelande i händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analytiska.

> [!NOTE]
> Om du kör [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) med den här resursen har konfigurerats, returnerar den alltid **$false**.

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
