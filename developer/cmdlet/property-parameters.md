---
title: Egenskapsparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251429"
---
# <a name="property-parameters"></a>Egenskapsparametrar

I följande tabell visas de rekommenderade namn och funktioner för Egenskapsparametrar.

|Parameter|Funktioner|
|---|---|
|**Antal**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange antalet objekt som ska bearbetas.|
|**Beskrivning**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en beskrivning för en resurs.|
|**Från**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange referensobjekt om du vill hämta information från.|
|**Id**<br>Datatyp: Resursen beroende|Implementera den här parametern så att användaren kan ange identifierare för en resurs.|
|**Indata**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange filen med indata-specifikationen.|
|**Position**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange platsen för resursen.|
|**Loggnamn**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett namn på loggfil för att bearbeta eller använda.|
|**Namn**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange namnet på resursen.|
|**Resultat**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange utdatafilen.|
|**Ägare**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange namnet på ägare till resursen.|
|**Egenskapen**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange namnet eller namnen på egenskaperna som ska användas.|
|**Orsak**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange varför denna cmdlet anropas.|
|**Regex**<br>Datatyp: SwitchParameter|Implementera den här parametern så att reguljära uttryck används när parametern anges. När den här parametern anges, löses inte jokertecken.|
|**Speed**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange överföringshastigheten. Användaren anger den här parametern för resursen.|
|**tillstånd**<br>Datatyp: Nyckelordet matris|Implementera den här parametern så att användaren kan ange namnen på delstater, till exempel Tangent ned.|
|**Värde**<br>Datatyp: Objekt|Implementera den här parametern så att användaren kan ange ett värde att förse cmdlet: en.|
|**Version**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange vilken version av egenskapen.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
