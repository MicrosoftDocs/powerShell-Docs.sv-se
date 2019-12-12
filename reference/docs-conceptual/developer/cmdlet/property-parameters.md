---
title: Egenskaps parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359371"
---
# <a name="property-parameters"></a>Egenskapsparametrar

I följande tabell visas de rekommenderade namnen och egenskaperna för egenskaps parametrar.

|Parameter|Funktioner|
|---|---|
|**Reparationer**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange antalet objekt som ska bearbetas.|
|**Beskrivning**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en beskrivning för en resurs.|
|**From**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange det referens objekt som informationen ska hämtas från.|
|**Id**<br>Datatyp: resurs beroende|Implementera den här parametern så att användaren kan ange identifieraren för en resurs.|
|**Indata**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange specifikationen för indatafilen.|
|**Position**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange resursens plats.|
|**LogName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på logg filen som ska bearbetas eller användas.|
|**Namn**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på resursen.|
|**Resultat**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange utdatafilen.|
|**Ägare**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på resursens ägare.|
|**Egenskap**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namn eller namn på de egenskaper som ska användas.|
|**Orsak**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange varför denna cmdlet anropas.|
|**Verifiering**<br>Datatyp: SwitchParameter|Implementera den här parametern så att reguljära uttryck används när parametern anges. När den här parametern anges matchas inte jokertecken.|
|**Hastighet**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange överföringshastigheten. Användaren anger den här parametern till resursens hastighet.|
|**Tillstånd**<br>Datatyp: nyckelords mat ris|Implementera den här parametern så att användaren kan ange namn på tillstånd, t. ex. NEDPIL.|
|**Värde**<br>Datatyp: objekt|Implementera den här parametern så att användaren kan ange ett värde som ska användas för cmdleten.|
|**Version**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange version för egenskapen.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
