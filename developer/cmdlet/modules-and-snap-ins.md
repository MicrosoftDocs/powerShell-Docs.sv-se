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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067628"
---
# <a name="modules-and-snap-ins"></a>Moduler och snapin-moduler

Cmdlet: ar kan läggas till en session med hjälp av snapin-modulen eller modulerna (som presenteras av Windows PowerShell 2.0). När cmdleten har lagts till i sessionen som den kan köras via programmering genom att ett program eller interaktivt på kommandoraden.

Vi rekommenderar att du använder moduler som leveransmetod för att lägga till cmdlet: ar till ett av följande skäl:

- Moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten har definierats. Det finns inget behov av att implementera en snapin-klass.

- Moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formatering filer och mer.

- Snapin-moduler kan användas endast för att lägga till cmdlets och providers i sessionen.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
