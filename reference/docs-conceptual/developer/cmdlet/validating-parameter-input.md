---
title: Verifierar parameter Indatatyp | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784001"
---
# <a name="validating-parameter-input"></a>Verifiera parameterindata

PowerShell kan verifiera argumenten som skickas till cmdlet-parametrar på flera sätt.
PowerShell kan verifiera längden, intervallet och mönstret för tecknen i argumentet.
Det kan verifiera antalet tillgängliga argument (count).
Dessa validerings regler definieras av verifierings-attribut som deklareras med attributet parameter i offentliga egenskaper för cmdlet-klassen.

För att validera ett parameter argument använder PowerShell-körningen den information som anges av verifierings-attributen för att bekräfta värdet för parametern innan cmdleten körs.
Om parameter indata inte är giltiga får användaren ett fel meddelande.
Varje validerings parameter definierar en validerings regel som tillämpas av PowerShell.

PowerShell framtvingar verifierings reglerna baserat på följande attribut.

### <a name="validatecount"></a>ValidateCount

Anger det lägsta och högsta antalet argument som en parameter kan acceptera.
Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Anger det lägsta och högsta antalet tecken i parameter argumentet.
Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Anger ett reguljärt uttryck som validerar parameter argumentet.
Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Anger det lägsta och högsta värdet för parameter argumentet.
Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Anger giltiga värden för parameter argumentet.
Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Verifiera parameterindata](./how-to-validate-parameter-input.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
