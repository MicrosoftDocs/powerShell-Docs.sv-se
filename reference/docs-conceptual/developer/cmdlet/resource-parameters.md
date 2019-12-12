---
title: Resurs parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359233"
---
# <a name="resource-parameters"></a>Resursparametrar

I följande tabell visas de rekommenderade namnen och funktionerna för resurs parametrar. För dessa parametrar kan resurserna vara den sammansättning som innehåller cmdlet-klassen eller värd programmet som kör cmdleten.

|Parameter|Funktioner|
|---|---|
|**Programmet**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett program.|
|**Sammansättning**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en sammansättning.|
|**Basattributet**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett attribut.|
|**Lektion**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en Microsoft .NET Ramverks klass.|
|**Flernodskluster**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett kluster.|
|**Substrat**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange kulturen som cmdleten ska köras i.|
|**Domän**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange domän namnet.|
|**Kombinationsenhet**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett enhets namn.|
|**Händelse**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett händelse namn.|
|**Gränssnitt**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett nätverks gränssnitts namn.|
|**Adresser**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en IP-adress.|
|**Jobb**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett jobb.|
|**LiteralPath**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange sökvägen till en resurs när jokertecken inte stöds. (Använd parametern **Path** när jokertecken stöds.)|
|**Mac**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en MAC-adress (Media Access Controller).|
|**ParentId**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange den överordnade identifieraren.|
|**Sökväg**<br>Datatyp: sträng, sträng []|Implementera den här parametern så att användaren kan ange sökvägar till en resurs när jokertecken stöds. (Använd parametern **LiteralPath** när jokertecken inte stöds.) Vi rekommenderar att du utvecklar den här parametern så att den stöder fullständig `provider:path`-syntax som används av providers. Vi rekommenderar också att du utvecklar det så att det fungerar med så många leverantörer som möjligt.|
|**Port**<br>Datatyp: heltal, sträng|Implementera den här parametern så att användaren kan ange ett heltals värde för nätverk eller ett sträng värde som "BizTalk" för andra typer av portar.|
|**Skrivarkö**<br>Datatyp: heltal, sträng|Implementera den här parametern så att användaren kan ange skrivare för den cmdlet som ska användas.|
|**Storlek**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange en storlek.|
|**BEKRÄFTA**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett transaktions-ID (TID) för cmdlet: en.|
|**Typ**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange vilken typ av resurs som ska användas.|
|**URL**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en Uniform Resource Locator (URL).|
|**Användare**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange sitt namn eller namnet på en annan användare.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
