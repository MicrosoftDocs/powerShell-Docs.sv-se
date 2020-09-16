---
title: Formatera data som visas | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: 97d23b3079b2779e518b6b6d2f2ac0c5e9d1f3a3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781519"
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
