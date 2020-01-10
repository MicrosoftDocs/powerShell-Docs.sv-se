---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Välja objekt för objekt Välj objekt
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737176"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="0fe35-103">Välja delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="0fe35-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="0fe35-104">Du kan använda `Select-Object`-cmdlet för att skapa nya, anpassade PowerShell-objekt som innehåller egenskaper som valts från de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="0fe35-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="0fe35-105">Skriv följande kommando för att skapa ett nytt objekt som bara innehåller egenskaperna för **namn** och **ledigt utrymme** i **Win32_LogicalDisk** WMI-klassen:</span><span class="sxs-lookup"><span data-stu-id="0fe35-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="0fe35-106">Med `Select-Object` kan du skapa beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="0fe35-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="0fe35-107">Så du kan visa **ledigt utrymme** i GB i stället för byte.</span><span class="sxs-lookup"><span data-stu-id="0fe35-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
