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
# <a name="formatting-displayed-data"></a>Formatera data som visas

Du kan ange hur enskilda datapunkter i din tabell, en lista eller en bred vy visas. Du kan använda den `FormatString` element när du definierar objekten i vyn, eller om du kan använda den `ScriptBlock` element att anropa den `FormatString` metoden på data.

## <a name="using-the-formatstring-element"></a>Med hjälp av FormatString-elementet

I följande exempel värdet för den `TotalProcessorTime` egenskapen för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt är formaterad med FormatString-elementet. den `TotalProcessorTime` egenskapen

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



