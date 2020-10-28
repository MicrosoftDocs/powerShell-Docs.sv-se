---
ms.date: 09/12/2016
ms.topic: reference
title: Formatera data som visas
description: Formatera data som visas
ms.openlocfilehash: 40f6b3b4fa36062ee0bad3f197ad159f571445c8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667869"
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
