---
title: Formatera data som visas | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355015"
---
# <a name="formatting-displayed-data"></a>Formatera data som visas

Du kan ange hur enskilda data punkter i listan, tabellen eller den breda vyn ska visas. Du kan använda elementet `FormatString` när du definierar objekt i vyn, eller så kan du använda elementet `ScriptBlock` för att anropa metoden @no__t 2 på data.

## <a name="using-the-formatstring-element"></a>Använda FormatString-elementet

I följande exempel formateras värdet för egenskapen `TotalProcessorTime` för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) med hjälp av FormatString-elementet. Egenskapen `TotalProcessorTime`

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```


