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
# <a name="formatting-displayed-data"></a><span data-ttu-id="2beaa-102">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="2beaa-102">Formatting Displayed Data</span></span>

<span data-ttu-id="2beaa-103">Du kan ange hur enskilda data punkter i listan, tabellen eller den breda vyn ska visas.</span><span class="sxs-lookup"><span data-stu-id="2beaa-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="2beaa-104">Du kan använda `FormatString` elementet när du definierar objekt i vyn, eller så kan du använda `ScriptBlock` elementet för att anropa `FormatString` metoden för data.</span><span class="sxs-lookup"><span data-stu-id="2beaa-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="2beaa-105">Använda FormatString-elementet</span><span class="sxs-lookup"><span data-stu-id="2beaa-105">Using the FormatString Element</span></span>

<span data-ttu-id="2beaa-106">I följande exempel `TotalProcessorTime` formateras värdet för egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet med hjälp av FormatString-elementet.</span><span class="sxs-lookup"><span data-stu-id="2beaa-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="2beaa-107">`TotalProcessorTime`egenskapen</span><span class="sxs-lookup"><span data-stu-id="2beaa-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
