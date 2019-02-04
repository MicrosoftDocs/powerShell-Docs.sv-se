---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAny resurs
ms.openlocfilehash: 39e90f0df3459b8891ed46e02ae82c45a285e7f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686091"
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny resurs

> Gäller för: Windows PowerShell 5.1 och senare

Den **WaitForSome** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](../../../configurations/configurations.md) ange beroenden på konfigurationer på andra noder.

Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är med önskat tillstånd på alla målnoder som definierats i den **nodnamn** egenskapen.


## <a name="syntax"></a>Syntax

```
WaitForAny [string] #ResourceName
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
| ResourceName| Resursnamnet förlita sig på. Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”|
| Nodnamn| Målnoder resursens förlita sig på.|
| RetryIntervalSec| Antal sekunder innan du försöker igen. Minimum är 1.|
| retryCount| Det maximala antalet gånger att försöka igen.|
| ThrottleLimit| Antal datorer kan ansluta samtidigt. Standardvärdet är standard för nya-cimsession.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)
