---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateLength
description: Deklaration av attributet ValidateLength
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646190"
---
# <a name="validatelength-attribute-declaration"></a>Deklaration av attributet ValidateLength

Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument. Det här attributet kan också användas av Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([System. Int32](/dotnet/api/System.Int32)) krävs. Anger det minsta antalet tecken som tillåts.

`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) krävs. Anger det maximala antalet tecken som tillåts.

## <a name="remarks"></a>Kommentarer

- Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).

- Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.

- Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:

  - När värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.

  - När `MaxLength` parametern Attribute anges till 0.

  - Om argumentet inte är en sträng.

- Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
