---
title: Verifierar parameter Indatatyp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354882"
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

[Verifiera parameter ingångar](./how-to-validate-parameter-input.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
