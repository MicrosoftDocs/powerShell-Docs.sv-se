---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-loggen resurs
ms.openlocfilehash: 72c9c5a9b8e2a4ed4ce43cfd792572ce95b502b3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-log-resource"></a>DSC-loggen resurs 

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den __loggen__ resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att skriva meddelanden till händelseloggen för Microsoft-Windows-önskade tillstånd Configuration/analys.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

Obs: Som standard de operativa loggarna för DSC är aktiverade.
Analytiska loggen ska vara tillgängliga eller synliga, måste vara aktiverat.
Se följande artikel.

[Var finns DSC-händelseloggar?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   | 
|---|---| 
| Meddelande| Anger meddelandet som du vill skriva till händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analys.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan det här loggmeddelandet hämtar skrivs. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Exempel

I följande exempel visas hur du lägger till ett meddelande i händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analys.

> **Obs**: Om du kör [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) med den här resursen har konfigurerats, returneras alltid **$false**.

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

