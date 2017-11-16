---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForSome resurs
ms.openlocfilehash: 3ea9dc51cbb00cf6158abf114fdb31fd91307df9
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2017
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome resurs

> Gäller för: Windows PowerShell 5.0 och senare

Den **WaitForAny** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.

Den här resursen lyckas om resursen som anges av den **ResourceName** egenskapen finns i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn**  egenskapen. 


## <a name="syntax"></a>Syntax

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   | 
|---|---| 
| NodeCount| Minsta antal noder som måste finnas i tillståndet för den här resursen ska lyckas.|
| Nodnamn| Målnoder av resursen ska beroende.| 
| resourceName| Resursnamnet beroende.| 
| RetryIntervalSec| Antalet sekunder innan du försöker igen. Minsta är 1.| 
| retryCount| Maximalt antal nya försök.| 
| ThrottleLimit| Antal datorer ansluta samtidigt. Standardvärdet är standard för nya cimsession.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Se [använder DSC med autentiseringsuppgifterna för användaren](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)

