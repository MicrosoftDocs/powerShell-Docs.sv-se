---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WaitForSome-resurs
description: DSC WaitForSome-resurs
ms.openlocfilehash: bc9c3df2b476e7046ccfe6257acc1d1641e7594b
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143100"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome-resurs

> Gäller för: Windows PowerShell 5. x

Du kan använda den **WAITFORSOME** DSC-resursen (Desired State Configuration) i ett Node-block i en [DSC-konfiguration](../../../configurations/configurations.md) för att ange beroenden för konfigurationer på andra noder.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

Den här resursen slutförs om resursen som anges av egenskapen **resourceName** har önskat tillstånd på ett minsta antal noder (anges av **NodeCount** ) som definieras av egenskapen **nodnamn** .

> [!NOTE]
> **WaitForSome** -resursen använder Windows Remote Management för att kontrol lera status för andra noder. Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity).

## <a name="syntax"></a>Syntax

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|NodeCount |Det minsta antalet noder som måste ha önskat tillstånd för att resursen ska lyckas. |
|NodeName |Målvärdena för resursen som är beroende av. |
|ResourceName |Resurs namnet som är beroende av. Om den här resursen tillhör en annan konfiguration formaterar du namnet som `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]` . |
|RetryIntervalSec |Antalet sekunder innan nytt försök. Minimivärdet är 1. |
|RetryCount |Det maximala antalet försök att försöka igen. |
|ThrottleLimit |Antal datorer som ska anslutas samtidigt. Standardvärdet är `New-CimSession` standard. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns i [ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)
