---
title: Attribut i cmdlet-kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359464"
---
# <a name="attributes-in-cmdlet-code"></a>Attribut i cmdlet-kod

För att kunna använda de vanliga funktionerna i Windows PowerShell, dekoreras de klasser och offentliga egenskaper som definierats i cmdlet-koden med attribut. Följande klass definition använder exempelvis cmdlet-attributet för att identifiera den Microsoft .NET Ramverks klass där **Get-proc-** cmdleten implementeras. (Denna cmdlet används som ett exempel i det här dokumentet och liknar den `Get-Process`-cmdleten som tillhandahålls av Windows PowerShell.)

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
