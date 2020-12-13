---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera parameterindata
description: Verifiera parameterindata
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660396"
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
