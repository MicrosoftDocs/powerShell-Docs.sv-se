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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355015"
---
# <a name="formatting-displayed-data"></a>Formatera data som visas

Du kan ange hur enskilda data punkter i listan, tabellen eller den breda vyn ska visas. Du kan använda `FormatString`-elementet när du definierar objekt i vyn, eller så kan du använda `ScriptBlock`-elementet för att anropa `FormatString`-metoden för data.

## <a name="using-the-formatstring-element"></a>Använda FormatString-elementet

I följande exempel formateras värdet för egenskapen `TotalProcessorTime` för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) med hjälp av FormatString-elementet. Egenskapen `TotalProcessorTime`

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



