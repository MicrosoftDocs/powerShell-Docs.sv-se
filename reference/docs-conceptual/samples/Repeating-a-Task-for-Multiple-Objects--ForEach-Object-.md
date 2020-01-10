---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Upprepa en uppgift för ett förgrunds objekt för flera objekt
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736887"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="036a7-103">Upprepa en uppgift för flera objekt (förgrunds objekt)</span><span class="sxs-lookup"><span data-stu-id="036a7-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="036a7-104">`ForEach-Object` cmdlet använder skript block och `$_` beskrivningen för det aktuella pipelinen för att köra ett kommando på varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="036a7-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="036a7-105">Detta kan användas för att utföra komplicerade uppgifter.</span><span class="sxs-lookup"><span data-stu-id="036a7-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="036a7-106">En situation där detta kan vara användbart är att ändra data så att de blir mer användbara.</span><span class="sxs-lookup"><span data-stu-id="036a7-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="036a7-107">**Win32_LogicalDisk** -klassen från WMI kan till exempel användas för att returnera information om ledigt utrymme för varje lokal disk.</span><span class="sxs-lookup"><span data-stu-id="036a7-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="036a7-108">Data returneras i antal byte, vilket gör det svårt att läsa:</span><span class="sxs-lookup"><span data-stu-id="036a7-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="036a7-109">Vi kan konvertera värdet för det **lediga utrymmet** till megabyte genom att dividera varje värde med 1 MB.</span><span class="sxs-lookup"><span data-stu-id="036a7-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="036a7-110">Du kan göra det i ett `ForEach-Object`-skript block genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="036a7-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="036a7-111">Tyvärr är utdata nu data utan tillhör ande etikett.</span><span class="sxs-lookup"><span data-stu-id="036a7-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="036a7-112">Eftersom WMI-egenskaper som detta är skrivskyddade kan du inte konvertera ett **ledigt utrymme**direkt.</span><span class="sxs-lookup"><span data-stu-id="036a7-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="036a7-113">Om du skriver följande:</span><span class="sxs-lookup"><span data-stu-id="036a7-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="036a7-114">Du får ett fel meddelande:</span><span class="sxs-lookup"><span data-stu-id="036a7-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="036a7-115">Du kan organisera om data med hjälp av vissa avancerade tekniker, men en enklare metod är att skapa ett nytt objekt genom att använda `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="036a7-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
