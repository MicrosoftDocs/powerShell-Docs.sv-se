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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065673"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="c39ec-102">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="c39ec-102">Formatting Displayed Data</span></span>

<span data-ttu-id="c39ec-103">Du kan ange hur enskilda datapunkter i din tabell, en lista eller en bred vy visas.</span><span class="sxs-lookup"><span data-stu-id="c39ec-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="c39ec-104">Du kan använda den `FormatString` element när du definierar objekten i vyn, eller om du kan använda den `ScriptBlock` element att anropa den `FormatString` metoden på data.</span><span class="sxs-lookup"><span data-stu-id="c39ec-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="c39ec-105">Med hjälp av FormatString-elementet</span><span class="sxs-lookup"><span data-stu-id="c39ec-105">Using the FormatString Element</span></span>

<span data-ttu-id="c39ec-106">I följande exempel värdet för den `TotalProcessorTime` egenskapen för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt är formaterad med FormatString-elementet.</span><span class="sxs-lookup"><span data-stu-id="c39ec-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="c39ec-107">den `TotalProcessorTime` egenskapen</span><span class="sxs-lookup"><span data-stu-id="c39ec-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



