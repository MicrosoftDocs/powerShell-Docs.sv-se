---
title: ValidateRange-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359134"
---
# <a name="validaterange-attribute-declaration"></a>Deklaration av attributet ValidateRange

Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter. Det här attributet kan också användas av Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametrar

`MinRange` ([system. Object](/dotnet/api/system.object)) krävs. Anger det lägsta tillåtna värdet.

`MaxRange` ([system. Object](/dotnet/api/system.object)) krävs. Anger det högsta tillåtna värdet.

## <a name="remarks"></a>Anmärkningar

- Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för parametern `MinRange` är större än värdet för parametern `MaxRange`.

- Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:

    - När värdet för argumentet är mindre än `MinRange`-gränsen eller större än `MaxRange`-gränsen.

    - Om argumentet inte är av samma typ som parametrarna `MinRange` och `MaxRange`.

- Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
