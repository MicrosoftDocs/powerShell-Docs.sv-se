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
ms.openlocfilehash: f58e8ecb67238939e90d4c5650bddd03da3c9409
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851753"
---
# <a name="resource-parameters"></a>Resursparametrar

I följande tabell visas de rekommenderade namn och de funktioner för Resursparametrar. Resurserna som kan vara sammansättningen som innehåller klassen cmdlet eller värdprogrammet som kör cmdlet: en för dessa parametrar.

Programdata skriver du: Sträng

Implementera den här parametern så att användaren kan ange ett program.

Sammansättningen datatyp: Sträng

Implementera den här parametern så att användaren kan ange en sammansättning.

Attributets datatyp: Sträng

Implementera den här parametern så att användaren kan ange ett attribut.

Klass-datatyp: Sträng

Implementera den här parametern så att användaren kan ange en Microsoft .NET Framework-klass.

Kluster-datatyp: Sträng

Implementera den här parametern så att användaren kan ange ett kluster.

Kulturen datatyp: Sträng

Implementera den här parametern så att användaren kan ange kulturen där du vill köra cmdleten.

Domän-datatyp: Sträng

Implementera den här parametern så att användaren kan ange domännamnet.

Enhetstyp för Data: Sträng

Implementera den här parametern så att användaren kan ange ett enhetsnamn.

Händelsedata skriver du: Sträng

Implementera den här parametern så att användaren kan ange ett händelsenamn.

Gränssnittstyp Data: Sträng

Implementera den här parametern så att användaren kan ange ett nätverksnamn för gränssnittet.

IP-adress datatyp: Sträng

Implementera den här parametern så att användaren kan ange en IP-adress.

Jobbdata skriver du: Sträng

Implementera den här parametern så att användaren kan ange ett jobb.

LiteralPath datatyp: Sträng

Implementera den här parametern så att användaren kan ange sökvägen till en resurs när jokertecken inte stöds. (Använd den `Path` parameter när jokertecken stöds.)

Mac-datatyp: Sträng

Implementera den här parametern så att användaren kan ange en adress för media access controller (MAC).

Datatyp ParentId: Sträng

Implementera den här parametern så att användaren kan ange det överordnade ID: t.

Typ av sökväg: String, String[]

Implementera den här parametern så att användaren kan ange sökvägar till en resurs när jokertecken stöds. (Använd den `LiteralPath` parameter när jokertecken inte stöds.)

Vi rekommenderar att du utvecklar den här parametern så att den stöder fullständig ”provider: sökväg”-syntax som används av providrar. Vi rekommenderar också att du utvecklar det så att den fungerar med så många leverantörer som möjligt.

Port datatyp: Integer, String

Implementera den här parametern så att användaren kan ange ett heltalsvärde för nätverk eller ett strängvärde, till exempel ”biztalk” för andra typer av port.

Skrivardata skriver du: Integer, String

Implementera den här parametern så att användaren kan ange skrivaren för cmdleten för att använda.

Ändra storlek på datatyp: Int32

Implementera den här parametern så att användaren kan ange en storlek.

TID datatyp: Sträng

Implementera den här parametern så att användaren kan ange en transaktion identifierare (TID) för cmdlet: en.

Skriv datatyp: Sträng

Implementera den här parametern så att användaren kan ange den typ av resurs som ska användas.

URL: en datatyp: Sträng

Implementera den här parametern så att användaren kan ange en URL (Uniform Resource Locator).

Användardatatypen: Sträng

Implementera den här parametern så att användaren kan ange användarens namn eller namnet på en annan användare.

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
