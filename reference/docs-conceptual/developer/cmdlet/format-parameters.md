---
ms.date: 09/13/2016
ms.topic: reference
title: Formatparametrar
description: Formatparametrar
ms.openlocfilehash: 5f970683fedc71b208ff6becad761d94611a91a6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652819"
---
# <a name="format-parameters"></a>Formatparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller generera data.

|Parameter|Funktioner|
|---|---|
|**Som**<br>Datatyp: nyckelord|Implementera den här parametern för att ange formatet för cmdlet-utdata. Möjliga värden kan till exempel vara text eller skript.|
|**Binär**<br>Datatyp: SwitchParameter|Implementera den här parametern för att ange att cmdleten hanterar binära värden.|
|**Kodning**<br>Datatyp: nyckelord|Implementera den här parametern för att ange vilken typ av kodning som stöds. Möjliga värden kan till exempel vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte och String.|
|**Ny rad**<br>Datatyp: SwitchParameter|Implementera den här parametern så att rad matnings tecken stöds när parametern anges.|
|**Kortnamn**<br>Datatyp: SwitchParameter|Implementera den här parametern så att korta namn stöds när parametern anges.|
|**LED**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange bredden på utmatnings enheten.|
|**Flytta**<br>Datatyp: SwitchParameter|Implementera den här parametern så att figur sättningen stöds när parametern anges.|
## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
