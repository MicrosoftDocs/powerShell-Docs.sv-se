---
title: Formatering visas Data | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846104"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="135d8-102">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="135d8-102">Formatting Displayed Data</span></span>

<span data-ttu-id="135d8-103">Du kan ange hur enskilda datapunkter i din tabell, en lista eller en bred vy visas.</span><span class="sxs-lookup"><span data-stu-id="135d8-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="135d8-104">Du kan använda den `FormatString` element när du definierar objekten i vyn, eller om du kan använda den `ScriptBlock` element att anropa den `FormatString` metoden på data.</span><span class="sxs-lookup"><span data-stu-id="135d8-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="135d8-105">Med hjälp av FormatString-elementet</span><span class="sxs-lookup"><span data-stu-id="135d8-105">Using the FormatString Element</span></span>

<span data-ttu-id="135d8-106">I följande exempel värdet för den `TotalProcessorTime` egenskapen för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt är formaterad med FormatString-elementet.</span><span class="sxs-lookup"><span data-stu-id="135d8-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="135d8-107">den `TotalProcessorTime` egenskapen</span><span class="sxs-lookup"><span data-stu-id="135d8-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



