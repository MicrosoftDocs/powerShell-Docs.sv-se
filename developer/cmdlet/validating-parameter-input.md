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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848806"
---
# <a name="validating-parameter-input"></a>Verifiera parameterindata

Windows PowerShell kan verifiera argumenten som skickades till cmdlet-parametrarna på flera olika sätt. Windows PowerShell kan verifiera längden och intervallet mönstret för tecken på argumentet. Det kan verifiera antalet argument tillgängliga (antal). Dessa valideringsregler definieras av verifiering attribut som deklareras med parametern-attributet på offentliga egenskaper för cmdlet-klassen.

För att verifiera ett argument för parametern, använder Windows PowerShell-runtime information som tillhandahålls av attributen verifiering för att bekräfta värdet för parametern innan cmdleten körs. Om parametern-indata inte är giltiga, får användaren ett felmeddelande. Varje parameter för verifiering definierar en valideringsregel som används av Windows PowerShell.

Windows PowerShell framtvingar valideringsregler baserat på följande attribut.

ValidateCount anger minsta och största antalet argument som en parameter kan godkänna. Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).

ValidateLength anger det minsta och högsta antalet tecken i Parameterargumentet. Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).

ValidatePattern anger ett reguljärt uttryck som validerar Parameterargumentet. Läs mer om vilken syntax som används för att deklarera det här attributet [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).

ValidateRange anger minsta och högsta värden för Parameterargumentet. Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).

ValidateSet anger giltiga värden för Parameterargumentet. Läs mer om vilken syntax som används för att deklarera det här attributet [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Hur du verifierar indata för parametern](./how-to-validate-parameter-input.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
