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
# <a name="formatting-displayed-data"></a><span data-ttu-id="6da6d-102">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="6da6d-102">Formatting Displayed Data</span></span>

<span data-ttu-id="6da6d-103">Du kan ange hur enskilda data punkter i listan, tabellen eller den breda vyn ska visas.</span><span class="sxs-lookup"><span data-stu-id="6da6d-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="6da6d-104">Du kan använda `FormatString`-elementet när du definierar objekt i vyn, eller så kan du använda `ScriptBlock`-elementet för att anropa `FormatString`-metoden för data.</span><span class="sxs-lookup"><span data-stu-id="6da6d-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="6da6d-105">Använda FormatString-elementet</span><span class="sxs-lookup"><span data-stu-id="6da6d-105">Using the FormatString Element</span></span>

<span data-ttu-id="6da6d-106">I följande exempel formateras värdet för egenskapen `TotalProcessorTime` för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) med hjälp av FormatString-elementet.</span><span class="sxs-lookup"><span data-stu-id="6da6d-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="6da6d-107">Egenskapen `TotalProcessorTime`</span><span class="sxs-lookup"><span data-stu-id="6da6d-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



