---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Välja objekt för objekt Välj objekt
description: Du kan använda `Select-Object` cmdleten för att skapa nya, anpassade PowerShell-objekt som innehåller egenskaper som valts från objekten i pipelinen.
ms.openlocfilehash: 92635ac54ea1469739bcb228c5e9a0a8dbfc648b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501039"
---
# <a name="selecting-parts-of-objects-select-object"></a>Välj delar av objekt (Select-Object)

Du kan använda `Select-Object` cmdleten för att skapa nya, anpassade PowerShell-objekt som innehåller egenskaper som valts från de objekt som du använder för att skapa dem. Skriv följande kommando för att skapa ett nytt objekt som bara innehåller egenskaperna för **namn** och **ledigt utrymme** i **Win32_LogicalDisk** WMI-klassen:

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

Med `Select-Object` kan du skapa beräknade egenskaper. Så du kan visa **ledigt utrymme** i GB i stället för byte.

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
