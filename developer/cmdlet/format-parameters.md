---
title: Formatera parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251191"
---
# <a name="format-parameters"></a>Formatparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller för att generera data.

|Parameter|Funktioner|
|---|---|
|**Som**<br>Datatyp: Nyckelord|Implementera den här parametern om du vill ange formatet för cmdlet-utdata. Möjliga värden kan exempelvis vara Text eller skript.|
|**Binary**<br>Datatyp: SwitchParameter|Implementera den här parametern om du vill ange att cmdleten hanterar binära värden.|
|**Kodning**<br>Datatyp: Nyckelord|Implementera den här parametern om du vill ange vilken typ av kodning som stöds. Möjliga värden kan exempelvis vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte och sträng.|
|**NewLine**<br>Datatyp: SwitchParameter|Implementera den här parametern så att radmatningstecken stöds när parametern anges.|
|**Kortnamn**<br>Datatyp: SwitchParameter|Implementera den här parametern så att kortnamn stöds när parametern anges.|
|**Bredd**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange bredden på enheten.|
|**Omsluta**<br>Datatyp: SwitchParameter|Implementera den här parametern så att radbrytning stöds när parametern anges.|
## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
