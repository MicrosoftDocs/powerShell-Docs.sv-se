---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet Alias
description: Deklaration av attributet Alias
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668311"
---
# <a name="alias-attribute-declaration"></a>Deklaration av attributet Alias

Attributet alias gör att användaren kan ange olika namn för en cmdlet-parameter. Alias kan användas för att ange genvägar för ett parameter namn, eller så kan de ange olika namn som passar för olika scenarier.

## <a name="syntax"></a>Syntax

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametrar

`aliasName` (Sträng []) Kunna. Anger en uppsättning kommaavgränsade aliasnamn för cmdlet-parametern.

## <a name="remarks"></a>Kommentarer

- Attributet alias används med attributet parameter när du anger en cmdlet-parameter. Mer information om hur du deklarerar dessa attribut finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).

- Varje aliasnamn måste vara unikt inom en-cmdlet. Windows PowerShell söker inte efter dubbla aliasnamn.

- Attributet alias används en gång för varje parameter i en cmdlet.

- Attributet alias definieras av klassen [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Se även

[Parameteralias](./parameter-aliases.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
