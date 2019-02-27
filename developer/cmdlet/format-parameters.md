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
ms.openlocfilehash: 4f24af9b32f785695d156bfb4784aa03c97e8987
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849422"
---
# <a name="format-parameters"></a>Formatparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller för att generera data.

Som datatyp: Nyckelord

Implementera den här parametern om du vill ange formatet för cmdlet-utdata. Möjliga värden kan exempelvis vara Text eller skript.

Datatypen Binary: SwitchParameter

Implementera den här parametern om du vill ange att cmdleten hanterar binära värden.

Kodning datatyp: Nyckelord

Implementera den här parametern om du vill ange vilken typ av kodning som stöds. Möjliga värden kan exempelvis vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte och sträng.

Ny rad datatyp: SwitchParameter

Implementera den här parametern så att radmatningstecken stöds när parametern anges.

Kortnamn datatyp: SwitchParameter

Implementera den här parametern så att kortnamn stöds när parametern anges.

Bredd datatyp: Int32

Implementera den här parametern så att användaren kan ange bredden på enheten.

Omsluta datatyp: SwitchParameter

Implementera den här parametern så att radbrytning stöds när parametern anges.

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
