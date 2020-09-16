---
title: ValidatePattern-Attribute-deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.openlocfilehash: 713fa7a46a8eeefdbfd679a5e8436285fac085f8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787809"
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
