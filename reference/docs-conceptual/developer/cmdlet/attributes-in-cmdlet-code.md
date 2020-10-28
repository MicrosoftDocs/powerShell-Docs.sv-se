---
ms.date: 09/13/2016
ms.topic: reference
title: Attribut i cmdlet-kod
description: Attribut i cmdlet-kod
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653646"
---
# <a name="attributes-in-cmdlet-code"></a>Attribut i cmdlet-kod

För att kunna använda de vanliga funktionerna i Windows PowerShell, dekoreras de klasser och offentliga egenskaper som definierats i cmdlet-koden med attribut. Följande klass definition använder exempelvis cmdlet-attributet för att identifiera den Microsoft .NET Ramverks klass där **Get-proc-** cmdleten implementeras. (Denna cmdlet används som ett exempel i det här dokumentet och liknar den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Attributen betraktas som metadata eftersom deras implementering är separat från implementeringen av cmdlet-koden. När Windows PowerShell-körningsmiljön kör cmdleten känner den igen attributen och utför sedan lämplig åtgärd för varje attribut.

Även om du kanske vill implementera din egen version av funktionerna som tillhandahålls av dessa attribut, använder en bra cmdlet-design dessa vanliga funktioner.

Mer information om de olika attribut som kan deklareras i dina cmdlets finns i [attributtyper](./attribute-types.md).

## <a name="see-also"></a>Se även

[Attributtyper](./attribute-types.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
