---
title: ValidateRange-Attribute-deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.openlocfilehash: 9aeaa6f03c170389ff61a058b505dbcf74df6958
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787792"
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
