---
ms.date: 09/13/2016
ms.topic: reference
title: Moduler och snapin-moduler
description: Moduler och snapin-moduler
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658684"
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
