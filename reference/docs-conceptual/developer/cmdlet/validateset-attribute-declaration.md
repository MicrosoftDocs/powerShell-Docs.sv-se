---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidateSet
description: Deklaration av attributet ValidateSet
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660465"
---
# <a name="validateset-attribute-declaration"></a>Deklaration av attributet ValidateSet

Attributet ValidateSetAttribute anger en uppsättning möjliga värden för ett cmdlet parameter argument. Det här attributet kan också användas av Windows PowerShell-funktioner.

När det här attributet anges avgör Windows PowerShell-körningsmiljön om det angivna argumentet för cmdlet-parametern matchar ett element i den angivna element uppsättningen. Cmdleten körs bara om parameter argumentet matchar ett element i mängden. Om ingen matchning hittas uppstår ett fel i Windows PowerShell-körningsmiljön.

## <a name="syntax"></a>Syntax

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parametrar

`ValidValues` ([System. String](/dotnet/api/System.String)) krävs. Anger giltiga parameter element värden. I följande exempel visas hur du anger ett eller flera element.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. Standardvärdet för `true` anger att Case ignoreras. Värdet `false` gör cmdlet Skift läges känsligt.

## <a name="remarks"></a>Kommentarer

- Det här attributet kan bara användas en gång per parameter.

- Om parametervärdet är en matris måste varje element i matrisen matcha ett element i attribut uppsättningen.

- Attributet ValidateSetAttribute definieras av klassen [system. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
