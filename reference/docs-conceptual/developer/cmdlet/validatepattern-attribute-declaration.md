---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidatePattern
description: Deklaration av attributet ValidatePattern
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646169"
---
# <a name="validatepattern-attribute-declaration"></a>Deklaration av attributet ValidatePattern

Attributet ValidatePattern anger ett mönster för reguljära uttryck som validerar argumentet för en cmdlet-parameter. Det här attributet kan också användas av Windows PowerShell-funktioner.

När ValidatePattern anropas i en cmdlet konverterar Windows PowerShell-körningsmiljön argumentet för cmdlet-parametern till en sträng och jämför sedan strängen med det mönster som anges av attributet ValidatePattern. Cmdleten körs bara om den konverterade sträng representationen för argumentet och den angivna mönster matchningen. Om de inte matchar uppstår ett fel i Windows PowerShell-körningsmiljön.

## <a name="syntax"></a>Syntax

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parametrar

`RegexString` ([System. String](/dotnet/api/System.String)) krävs. Anger ett reguljärt uttryck som validerar parameter argumentet.

Alternativ ([system. text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) valfri namngiven parameter. Anger en bitvis kombination av [system. text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -flaggor som anger alternativ för reguljära uttryck.

## <a name="remarks"></a>Kommentarer

- Det här attributet kan bara användas en gång per parameter.

- Du kan använda- `Option` parametern för attributet för att ytterligare definiera mönstret. Du kan till exempel göra mönster Skift läges känsliga.

- Om attributet används för en samling måste varje element i samlingen matcha mönstret.

- Attributet ValidatePattern definieras av klassen [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
