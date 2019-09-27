---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WaitForAny-resurs
ms.openlocfilehash: 61fee456d2652e08ed9bdbe64457627ff5b2e145
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324046"
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny-resurs

> Gäller för: Windows PowerShell 5,1

Du kan använda den **WAITFORANY** DSC-resursen (Desired State Configuration) i ett Node-block i en [DSC-konfiguration](../../../configurations/configurations.md) för att ange beroenden för konfigurationer på andra noder.

Den här resursen slutförs om resursen som anges av egenskapen **resourceName** är i önskat tillstånd på alla målnod som definierats i egenskapen **nodnamn** .

> [!NOTE]
> **WaitForAny** -resursen använder Windows Remote Management för att kontrol lera status för andra noder. Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="syntax"></a>Syntax

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Egenskap |Beskrivning |
|---|---|
|ResourceName |Resurs namnet som är beroende av. Om den här resursen tillhör en annan konfiguration formaterar du namnet som `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`. |
|NodeName |Målvärdena för resursen som är beroende av. |
|RetryIntervalSec |Antalet sekunder innan nytt försök. Minimivärdet är 1. |
|retryCount |Det maximala antalet försök att försöka igen. |
|ThrottleLimit |Antal datorer som ska anslutas samtidigt. Standardvärdet är `New-CimSession` standard. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Ett exempel på hur du använder den här resursen finns i [ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)