---
title: Verifierar indata för parametern | Microsoft Docs
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
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429847"
---
# <a name="validating-parameter-input"></a>Verifiera parameterindata

PowerShell kan verifiera argumenten som skickades till cmdlet-parametrarna på flera olika sätt.
PowerShell kan verifiera längden och intervallet mönstret för tecken på argumentet.
Det kan verifiera antalet argument tillgängliga (antal).
Dessa valideringsregler definieras av verifiering attribut som deklareras med parametern-attributet på offentliga egenskaper för cmdlet-klassen.

För att verifiera en Parameterargumentet använder PowerShell-runtime information som tillhandahålls av attributen verifiering för att bekräfta värdet för parametern innan cmdleten körs.
Om parametern-indata inte är giltiga, får användaren ett felmeddelande.
Varje parameter för verifiering definierar en verifieringsregel som påtvingas av PowerShell.

PowerShell framtvingar valideringsregler baserat på följande attribut.

### <a name="validatecount"></a>ValidateCount

Anger minsta och största antalet argument som en parameter kan godkänna.
Mer information finns i [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Anger det minsta och högsta antalet tecken i Parameterargumentet.
Mer information finns i [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Anger ett reguljärt uttryck som validerar Parameterargumentet.
Mer information finns i [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Anger de lägsta och högsta värden för Parameterargumentet.
Mer information finns i [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Anger de giltiga värdena för Parameterargumentet.
Mer information finns i [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Hur du verifierar indata för parametern](./how-to-validate-parameter-input.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
