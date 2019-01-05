---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForSome resurs
ms.openlocfilehash: 906375a8fcf9b87d4b7487e63e6fae3f05b86d0d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048637"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome resurs

> Gäller för: Windows PowerShell 5.0 och senare

Den **WaitForAny** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](../../../configurations/configurations.md) ange beroenden på konfigurationer på andra noder.

Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn**  egenskapen.


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
| NodeCount| Minsta antalet noder som måste vara i önskat läge för den här resursen ska lyckas.|
| Nodnamn| Målnoder resursens förlita sig på.|
| ResourceName| Resursnamnet förlita sig på. Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”|
| RetryIntervalSec| Antal sekunder innan du försöker igen. Minimum är 1.|
| retryCount| Det maximala antalet gånger att försöka igen.|
| ThrottleLimit| Antal datorer kan ansluta samtidigt. Standardvärdet är standard för nya-cimsession.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Se [med hjälp av DSC med autentiseringsuppgifterna för användaren](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)
