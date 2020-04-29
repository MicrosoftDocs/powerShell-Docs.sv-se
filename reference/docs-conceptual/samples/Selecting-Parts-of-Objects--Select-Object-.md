---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Välja objekt för objekt Välj objekt
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737176"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="c6b9d-103">Välj delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="c6b9d-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="c6b9d-104">Du kan använda `Select-Object` cmdleten för att skapa nya, anpassade PowerShell-objekt som innehåller egenskaper som valts från de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="c6b9d-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="c6b9d-105">Skriv följande kommando för att skapa ett nytt objekt som bara innehåller egenskaperna för **namn** och **ledigt utrymme** i **Win32_LogicalDisk** WMI-klassen:</span><span class="sxs-lookup"><span data-stu-id="c6b9d-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="c6b9d-106">Med `Select-Object` kan du skapa beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c6b9d-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="c6b9d-107">Så du kan visa **ledigt utrymme** i GB i stället för byte.</span><span class="sxs-lookup"><span data-stu-id="c6b9d-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
