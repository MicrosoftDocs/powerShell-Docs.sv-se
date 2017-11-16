---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAny resurs
ms.openlocfilehash: ba1873cc0ecfc4596cbad5b61b4a52b61ea4778a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny resurs

> Gäller för: Windows PowerShell 5.1 och senare

Den **WaitForSome** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.

Den här resursen lyckas om om resursen som anges av den **ResourceName** egenskapen finns i tillståndet på alla målnoder som definierats i den **nodnamn** egenskapen.


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
| resourceName| Resursnamnet beroende.| 
| Nodnamn| Målnoder av resursen ska beroende.| 
| RetryIntervalSec| Antalet sekunder innan du försöker igen. Minsta är 1.| 
| retryCount| Maximalt antal nya försök.| 
| ThrottleLimit| Antal datorer ansluta samtidigt. Standardvärdet är standard för nya cimsession.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)

