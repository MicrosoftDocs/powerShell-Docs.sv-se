---
title: Deklarerar egenskaper som parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068274"
---
# <a name="declaring-properties-as-parameters"></a>Deklarera egenskaper som parametrar

Det här avsnittet innehåller grundläggande information som du måste förstå innan du deklarera parametrarna för en cmdlet.

Definiera de offentliga egenskaperna som representerar varje parameter för att deklarera parametrarna för en cmdlet i cmdlet-klass och sedan lägga till ett eller flera attribut för parametern i varje egenskap. Windows PowerShell-runtime använder parametern-attribut för att identifiera egenskapen som en cmdlet-parameter. Grundläggande syntaxen för att deklarera parametern-attributet är `[Parameter()]`.

Här är ett exempel på en egenskap som har definierats som en obligatorisk parameter.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Här följer några saker du bör tänka parametrar.

- En parameter måste uttryckligen markeras som offentliga. Parametrar som inte är markerad som offentlig standard till interna och kommer inte att hitta av Windows PowerShell-körningen.

- Parametrar ska definieras som Microsoft .NET Framework-typer för att ge bättre parameterverifieringen. Till exempel ska parametrar som är begränsade till ett värde från en uppsättning värden vara definierat som en uppräkningstyp. Parametrar som tar ett värde för ID: T URI (Uniform Resource) ska vara av typen [System.Uri](/dotnet/api/System.Uri).

- Undvik grundläggande strängparametrar för allt utom friformsarbetsyta textegenskaper.

- Du kan lägga till en parameter till valfritt antal parameteruppsättningar. Läs mer om parameteruppsättningar [cmdlet: en Parameter anger](./cmdlet-parameter-sets.md).

Windows PowerShell innehåller också en uppsättning gemensamma parametrar som är automatiskt tillgängliga för varje cmdlet. Läs mer om dessa parametrar och deras alias, [gemensamma parametrar för cmdleten](./common-parameter-names.md).

## <a name="see-also"></a>Se även

[Cmdlet gemensamma parametrar](./common-parameter-names.md)

[Typer av Cmdlet-Parameter](./types-of-cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
