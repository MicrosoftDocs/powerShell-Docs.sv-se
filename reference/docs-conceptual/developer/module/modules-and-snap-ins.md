---
title: Moduler och snapin-moduler | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787316"
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
