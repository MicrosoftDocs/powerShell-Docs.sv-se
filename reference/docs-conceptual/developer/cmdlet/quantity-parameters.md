---
title: Antal parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7ff6562380bb6336b08879b31d8d9fed47bfb6a7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781825"
---
# <a name="quantity-parameters"></a>Kvantitetsparametrar

I följande tabell visas rekommenderade namn och funktioner för mängd parametrar.

|Parameter|Funktioner|
|---|---|
|**Alla**<br>Datatyp: boolesk|Implementera den här parametern så att `true` alla resurser ska agera i stället för en standard del av resurserna. Implementera den här parametern så att `false` anger en delmängd av resurserna.|
|**Allokering**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange antalet objekt som ska allokeras.|
|**BlockCount**<br>Datatyp: Int64|Implementera den här parametern så att användaren kan ange block antalet.|
|**Reparationer**<br>Datatyp: Int64|Implementera den här parametern så att användaren kan ange antalet.|
|**Omfång**<br>Datatyp: nyckelord|Implementera den här parametern så att användaren kan ange det omfång som ska användas.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
