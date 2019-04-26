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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067543"
---
# <a name="quantity-parameters"></a>Kvantitetsparametrar

I följande tabell visas de rekommenderade namn och de funktioner för antal parametrar.

|Parameter|Funktioner|
|---|---|
|**Alla**<br>Datatyp: Boolesk|Implementera den här parametern så att `true` anger att alla resurser som bör åtgärdas i stället för en standard-delmängd av resurser. Implementera den här parametern så att `false` anger en delmängd av resurserna.|
|**Allokering**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange antalet objekt att allokera.|
|**BlockCount**<br>Datatyp: Int64|Implementera den här parametern så att användaren kan ange antal block.|
|**Antal**<br>Datatyp: Int64|Implementera den här parametern så att användaren kan ange antalet.|
|**Omfång**<br>Datatyp: Nyckelord|Implementera den här parametern så att användaren kan ange omfång ska användas.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
