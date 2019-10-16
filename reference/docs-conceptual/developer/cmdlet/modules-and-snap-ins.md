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
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356184"
---
# <a name="modules-and-snap-ins"></a>Moduler och snapin-moduler

Cmdletar kan läggas till i en session med hjälp av moduler (som introduceras av Windows PowerShell 2,0) eller snapin-moduler. När cmdleten har lagts till i sessionen kan den köras program mässigt av ett värd program eller interaktivt på kommando raden.

Vi rekommenderar att du använder moduler som leverans metod för att lägga till cmdlets i en session av följande anledningar:

- Med moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten definieras. Det finns inget behov av att implementera en snapin-klass.

- Med moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formateringsattribut.

- Snapin-moduler kan bara användas för att lägga till cmdlets och providers i sessionen.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
