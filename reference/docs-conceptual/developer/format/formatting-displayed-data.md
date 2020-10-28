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
# <a name="formatting-displayed-data"></a><span data-ttu-id="de6ec-103">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="de6ec-103">Formatting Displayed Data</span></span>

<span data-ttu-id="de6ec-104">Du kan ange hur enskilda data punkter i listan, tabellen eller den breda vyn ska visas.</span><span class="sxs-lookup"><span data-stu-id="de6ec-104">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="de6ec-105">Du kan använda `FormatString` elementet när du definierar objekt i vyn, eller så kan du använda `ScriptBlock` elementet för att anropa `FormatString` metoden för data.</span><span class="sxs-lookup"><span data-stu-id="de6ec-105">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="de6ec-106">Använda FormatString-elementet</span><span class="sxs-lookup"><span data-stu-id="de6ec-106">Using the FormatString Element</span></span>

<span data-ttu-id="de6ec-107">I följande exempel `TotalProcessorTime` formateras värdet för egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet med hjälp av FormatString-elementet.</span><span class="sxs-lookup"><span data-stu-id="de6ec-107">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="de6ec-108">`TotalProcessorTime`egenskapen</span><span class="sxs-lookup"><span data-stu-id="de6ec-108">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
