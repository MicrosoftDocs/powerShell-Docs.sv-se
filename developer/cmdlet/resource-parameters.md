---
title: Resursparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251208"
---
# <a name="resource-parameters"></a>Resursparametrar

I följande tabell visas de rekommenderade namn och de funktioner för Resursparametrar. Resurserna som kan vara sammansättningen som innehåller klassen cmdlet eller värdprogrammet som kör cmdlet: en för dessa parametrar.

|Parameter|Funktioner|
|---|---|
|**Programmet**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett program.|
|**Sammansättningen**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en sammansättning.|
|**Attributet**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett attribut.|
|**Klass**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en Microsoft .NET Framework-klass.|
|**Kluster**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett kluster.|
|**kultur**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange kulturen där du vill köra cmdleten.|
|**Domän**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange domännamnet.|
|**Drive**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett enhetsnamn.|
|**Händelse**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett händelsenamn.|
|**Gränssnittet**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett nätverksnamn för gränssnittet.|
|**IpAddress**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en IP-adress.|
|**Jobbet**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett jobb.|
|**LiteralPath**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange sökvägen till en resurs när jokertecken inte stöds. (Använd den **sökväg** parameter när jokertecken stöds.)|
|**Mac**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en adress för media access controller (MAC).|
|**ParentId**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange det överordnade ID: t.|
|**Sökväg**<br>Datatyp: String, String[]|Implementera den här parametern så att användaren kan ange sökvägar till en resurs när jokertecken stöds. (Använd den **LiteralPath** parameter när jokertecken inte stöds.) Vi rekommenderar att du utvecklar den här parametern så att den stöder fullständiga `provider:path` syntax som används av providers. Vi rekommenderar också att du utvecklar det så att den fungerar med så många leverantörer som möjligt.|
|**Port**<br>Datatyp: Integer, String|Implementera den här parametern så att användaren kan ange ett heltalsvärde för nätverk eller ett strängvärde, till exempel ”biztalk” för andra typer av port.|
|**Skrivare**<br>Datatyp: Integer, String|Implementera den här parametern så att användaren kan ange skrivaren för cmdleten för att använda.|
|**Size**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange en storlek.|
|**TID**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en transaktion identifierare (TID) för cmdlet: en.|
|**Typ**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange den typ av resurs som ska användas.|
|**URL**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en URL (Uniform Resource Locator).|
|**Användaren**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange användarens namn eller namnet på en annan användare.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
