---
ms.date: 09/13/2016
ms.topic: reference
title: Deklarera egenskaper som parametrar
description: Deklarera egenskaper som parametrar
ms.openlocfilehash: ade7928e2ca277da8bbd1a5e04997bd1d05f1e5d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653153"
---
# <a name="declaring-properties-as-parameters"></a>Deklarera egenskaper som parametrar

Det här avsnittet innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.

Om du vill deklarera parametrarna för en cmdlet i cmdlet-klassen definierar du de offentliga egenskaper som representerar varje parameter och lägger sedan till ett eller flera parametriserade till varje egenskap. Windows PowerShell-körningsmiljön använder parameter-attribut för att identifiera egenskapen som en cmdlet-parameter. Den grundläggande syntaxen för att deklarera parameter-attributet är `[Parameter()]` .

Här är ett exempel på en egenskap som definierats som en obligatorisk parameter.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Här är några saker att komma ihåg om parametrar.

- En parameter måste markeras som offentlig. Parametrar som inte har marker ATS som offentliga som offentliga som standard till interna och som inte hittas av Windows PowerShell-körningsmiljön.

- Parametrar ska definieras som Microsoft .NET Framework-typer för att ge bättre parameter verifiering. Till exempel ska parametrar som är begränsade till ett värde av en uppsättning värden definieras som en uppräknings typ. Parametrar som tar ett Uniform Resource Identifier (URI)-värde måste vara av typen [system. URI](/dotnet/api/System.Uri).

- Undvik grundläggande sträng parametrar för alla fält med fri Forms egenskaper.

- Du kan lägga till en parameter till valfritt antal parameter uppsättningar. Mer information om parameter uppsättningar finns i [cmdlet parameter Sets](./cmdlet-parameter-sets.md).

Windows PowerShell tillhandahåller också en uppsättning vanliga parametrar som automatiskt är tillgängliga för varje cmdlet. Mer information om dessa parametrar och deras alias finns i parametrar för [cmdlets common](./common-parameter-names.md).

## <a name="see-also"></a>Se även

[Vanliga parametrar för cmdlet](./common-parameter-names.md)

[Typer av cmdlet-parameter](./types-of-cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
