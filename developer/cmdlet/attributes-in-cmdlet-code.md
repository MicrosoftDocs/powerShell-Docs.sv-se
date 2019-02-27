---
title: I Cmdlet-koden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845264"
---
# <a name="attributes-in-cmdlet-code"></a>Attribut i cmdlet-kod

Om du vill använda de vanliga funktioner som Windows PowerShell dekorerad-klasser och offentliga egenskaperna som definierats i cmdlet-kod med attribut. Till exempel följande klassdefinition använder Cmdlet-attribut för att identifiera Microsoft .NET Framework-klassen där den **Get-Proc** cmdlet har implementerats. (Den här cmdleten används som exempel i det här dokumentet och liknar den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Dessa attribut kallas metadata eftersom deras implementering skiljer sig från implementeringen av cmdlet-kod. När Windows PowerShell-körningen körs cmdleten identifierar attribut och utför sedan lämplig åtgärd för varje attribut.

Även om du implementerar en egen version av funktionerna i dessa attribut, använder en bra cmdlet-design dessa vanliga funktioner.

Mer information om de olika attribut kan deklareras i dina cmdlets finns i [attributtyper](./attribute-types.md).

## <a name="see-also"></a>Se även

[Attributtyper](./attribute-types.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
