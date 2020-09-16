---
title: Format parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8e031f62aa8bcb0e9d5b900b2eace7187b1f3dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784290"
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
