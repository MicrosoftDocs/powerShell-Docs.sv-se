---
title: Antal parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359252"
---
# <a name="quantity-parameters"></a>Kvantitetsparametrar

I följande tabell visas rekommenderade namn och funktioner för mängd parametrar.

|Parameter|Funktioner|
|---|---|
|**Alla**<br>Datatyp: boolesk|Implementera den här parametern så att `true` anger att alla resurser ska åtgärdas på i stället för en standard del av resurserna. Implementera den här parametern så att `false` anger en delmängd av resurserna.|
|**Storlek**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange antalet objekt som ska allokeras.|
|**BlockCount**<br>Datatyp: Int64|Implementera den här parametern så att användaren kan ange block antalet.|
|**Reparationer**<br>Datatyp: Int64|Implementera den här parametern så att användaren kan ange antalet.|
|**Omfång**<br>Datatyp: nyckelord|Implementera den här parametern så att användaren kan ange det omfång som ska användas.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
