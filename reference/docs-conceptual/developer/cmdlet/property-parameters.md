---
title: Egenskaps parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0ded22dcda2b4eb957834ec092466767a4121f0e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781842"
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
