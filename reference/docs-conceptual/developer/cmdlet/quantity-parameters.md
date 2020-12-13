---
ms.date: 09/13/2016
ms.topic: reference
title: Kvantitetsparametrar
description: Kvantitetsparametrar
ms.openlocfilehash: 3f7c23eec34a709b1f2d59f611c93909b20f4124
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650304"
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
