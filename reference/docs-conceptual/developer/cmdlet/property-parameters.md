---
ms.date: 09/13/2016
ms.topic: reference
title: Egenskapsparametrar
description: Egenskapsparametrar
ms.openlocfilehash: eff51fcd395e5f9570193ea91684f9e70030bc7d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652600"
---
# <a name="property-parameters"></a>Egenskapsparametrar

I följande tabell visas de rekommenderade namnen och egenskaperna för egenskaps parametrar.

|Parameter|Funktioner|
|---|---|
|**Reparationer**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange antalet objekt som ska bearbetas.|
|**Beskrivning**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en beskrivning för en resurs.|
|**Som**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange det referens objekt som informationen ska hämtas från.|
|**Identitet**<br>Datatyp: resurs beroende|Implementera den här parametern så att användaren kan ange identifieraren för en resurs.|
|**Indata**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange specifikationen för indatafilen.|
|**Plats**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange resursens plats.|
|**LogName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på logg filen som ska bearbetas eller användas.|
|**Namn**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på resursen.|
|**Resultat**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange utdatafilen.|
|**Ägare**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på resursens ägare.|
|**Egenskap**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namn eller namn på de egenskaper som ska användas.|
|**Orsak**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange varför denna cmdlet anropas.|
|**Verifiering**<br>Datatyp: SwitchParameter|Implementera den här parametern så att reguljära uttryck används när parametern anges. När den här parametern anges matchas inte jokertecken.|
|**Hastighet**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange överföringshastigheten. Användaren anger den här parametern till resursens hastighet.|
|**Stat**<br>Datatyp: nyckelords mat ris|Implementera den här parametern så att användaren kan ange namn på tillstånd, t. ex. NEDPIL.|
|**Värde**<br>Datatyp: objekt|Implementera den här parametern så att användaren kan ange ett värde som ska användas för cmdleten.|
|**Version**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange version för egenskapen.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
