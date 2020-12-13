---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateRange
description: Deklaration av attributet ValidateRange
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660597"
---
# <a name="validaterange-attribute-declaration"></a>Deklaration av attributet ValidateRange

Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter. Det här attributet kan också användas av Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametrar

`MinRange` ([System. Object](/dotnet/api/system.object)) krävs. Anger det lägsta tillåtna värdet.

`MaxRange` ([System. Object](/dotnet/api/system.object)) krävs. Anger det högsta tillåtna värdet.

## <a name="remarks"></a>Kommentarer

- Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för `MinRange` parametern är större än värdet för `MaxRange` parametern.

- Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:

  - När värdet för argumentet är mindre än `MinRange` gränsen eller större än `MaxRange` gränsen.

  - Om argumentet inte är av samma typ som `MinRange` `MaxRange` parametrarna och.

- Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
