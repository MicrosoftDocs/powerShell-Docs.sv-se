---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateCount
description: Deklaration av attributet ValidateCount
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646274"
---
# <a name="validatecount-attribute-declaration"></a>Deklaration av attributet ValidateCount

Attributet ValidateCount anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([System. Int32][]) krävs. Anger det minsta antalet argument.

`MaxLength`([System. Int32][]) krävs. Anger det maximala antalet argument.

## <a name="remarks"></a>Kommentarer

- Mer information om hur du deklarerar det här attributet finns i [så här verifierar du ett argument antal][].

- När det här attributet inte anropas kan motsvarande cmdlet-parameter ha valfritt antal argument.

- Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:

  - `MinLength`Parametrarna och `MaxLength` är inte av typen [system. Int32][].

  - Värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.

- Attributet ValidateCount definieras av klassen [system. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Se även

[System. Management. Automation. ValidateCountAttribute][]

[Verifiera argumentantal][]

[Skriva en Windows PowerShell-cmdlet][]

[Verifiera argumentantal]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
