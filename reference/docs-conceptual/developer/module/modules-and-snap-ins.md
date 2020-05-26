---
title: Moduler och snapin-moduler | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811165"
---
# <a name="modules-and-snap-ins"></a>Moduler och snapin-moduler

Cmdletar kan läggas till i en session med hjälp av moduler (som introduceras av Windows PowerShell 2,0) eller snapin-moduler. När cmdleten har lagts till i sessionen kan den köras program mässigt av ett värd program eller interaktivt på kommando raden.

Vi rekommenderar att du använder moduler som leverans metod för att lägga till cmdlets i en session av följande anledningar:

- Med moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten definieras. Det finns inget behov av att implementera en snapin-klass.

- Med moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formateringsattribut.

- Snapin-moduler kan bara användas för att lägga till cmdlets och providers i sessionen.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](writing-a-windows-powershell-module.md)

[Skriva en Windows PowerShell-cmdlet](../cmdlet/cmdlet-overview.md)
