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
ms.openlocfilehash: 9f3a3176ae16ac7c014cadce6b4e856f9bd3b5da
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560397"
---
# <a name="formatting-displayed-data"></a>Formatera data som visas

Du kan ange hur enskilda data punkter i listan, tabellen eller den breda vyn ska visas. Du kan använda `FormatString` elementet när du definierar objekt i vyn, eller så kan du använda `ScriptBlock` elementet för att anropa `FormatString` metoden för data.

## <a name="using-the-formatstring-element"></a>Använda FormatString-elementet

I följande exempel `TotalProcessorTime` formateras värdet för egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet med hjälp av FormatString-elementet. `TotalProcessorTime`egenskapen

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
