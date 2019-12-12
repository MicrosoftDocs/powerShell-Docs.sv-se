---
title: Format parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359318"
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
