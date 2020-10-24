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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="90eb8-104">Välj delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="90eb8-104">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="90eb8-105">Du kan använda `Select-Object` cmdleten för att skapa nya, anpassade PowerShell-objekt som innehåller egenskaper som valts från de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="90eb8-105">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="90eb8-106">Skriv följande kommando för att skapa ett nytt objekt som bara innehåller egenskaperna för **namn** och **ledigt utrymme** i **Win32_LogicalDisk** WMI-klassen:</span><span class="sxs-lookup"><span data-stu-id="90eb8-106">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="90eb8-107">Med `Select-Object` kan du skapa beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="90eb8-107">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="90eb8-108">Så du kan visa **ledigt utrymme** i GB i stället för byte.</span><span class="sxs-lookup"><span data-stu-id="90eb8-108">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
