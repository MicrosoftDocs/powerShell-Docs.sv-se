---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAll resurs
ms.openlocfilehash: 7cb2fc134f4391de0e5df2cd719902097bf2ebf5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforall-resource"></a>DSC WaitForAll resurs

> Gäller för: Windows PowerShell 5.0 och senare

Den **WaitForAll** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.

Den här resursen lyckas om om resursen som anges av den **ResourceName** egenskapen finns i tillståndet på alla målnoder som definierats i den **nodnamn** egenskapen.


## <a name="syntax"></a>Syntax

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| resourceName| Resursnamnet beroende. Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”|
| NodeName| Målnoder av resursen ska beroende.|
| RetryIntervalSec| Antalet sekunder innan du försöker igen. Minsta är 1.|
| retryCount| Maximalt antal nya försök.|
| ThrottleLimit| Antal datorer ansluta samtidigt. Standardvärdet är standard för nya cimsession.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)