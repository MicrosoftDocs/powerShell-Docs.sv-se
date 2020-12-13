---
ms.date: 09/13/2016
ms.topic: reference
title: Resursparametrar
description: Resursparametrar
ms.openlocfilehash: 7533f91b6d5858bcefca289eabc7854d6d5d1f2b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668158"
---
# <a name="resource-parameters"></a>Resursparametrar

I följande tabell visas de rekommenderade namnen och funktionerna för resurs parametrar. För dessa parametrar kan resurserna vara den sammansättning som innehåller cmdlet-klassen eller värd programmet som kör cmdleten.

|Parameter|Funktioner|
|---|---|
|**Program**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett program.|
|**Sammansättning**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en sammansättning.|
|**Attribut**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett attribut.|
|**Klass**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en Microsoft .NET Ramverks klass.|
|**Kluster**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett kluster.|
|**Kultur**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange kulturen som cmdleten ska köras i.|
|**Domän**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange domän namnet.|
|**Enhet**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett enhets namn.|
|**Händelse**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett händelse namn.|
|**Gränssnitt**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett nätverks gränssnitts namn.|
|**Adresser**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en IP-adress.|
|**Jobb**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett jobb.|
|**LiteralPath**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange sökvägen till en resurs när jokertecken inte stöds. (Använd parametern **Path** när jokertecken stöds.)|
|**Mac**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en MAC-adress (Media Access Controller).|
|**ParentId**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange den överordnade identifieraren.|
|**Sökväg**<br>Datatyp: sträng, sträng []|Implementera den här parametern så att användaren kan ange sökvägar till en resurs när jokertecken stöds. (Använd parametern **LiteralPath** när jokertecken inte stöds.) Vi rekommenderar att du utvecklar den här parametern så att den stöder fullständig `provider:path` syntax som används av leverantörer. Vi rekommenderar också att du utvecklar det så att det fungerar med så många leverantörer som möjligt.|
|**Port**<br>Datatyp: heltal, sträng|Implementera den här parametern så att användaren kan ange ett heltals värde för nätverk eller ett sträng värde som "BizTalk" för andra typer av portar.|
|**Skrivare**<br>Datatyp: heltal, sträng|Implementera den här parametern så att användaren kan ange skrivare för den cmdlet som ska användas.|
|**Storlek**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange en storlek.|
|**BEKRÄFTA**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange ett transaktions-ID (TID) för cmdlet: en.|
|**Typ**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange vilken typ av resurs som ska användas.|
|**URL**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en Uniform Resource Locator (URL).|
|**Användare**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange sitt namn eller namnet på en annan användare.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
