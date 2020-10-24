---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Upprepa en uppgift för ett förgrunds objekt för flera objekt
description: Med ForEach-Object kan du upprepa en uppsättning kommandon för varje objekt som skickas via pipelinen.
ms.openlocfilehash: 7353be833dc8bf77dd18b7fc45bdd97e092ff6ef
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499966"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="f76d2-104">Upprepa en uppgift för flera objekt (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="f76d2-104">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="f76d2-105">`ForEach-Object`Cmdleten använder skript block och `$_` beskrivningen för det aktuella pipeline-objektet så att du kan köra ett kommando på varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="f76d2-105">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="f76d2-106">Detta kan användas för att utföra komplicerade uppgifter.</span><span class="sxs-lookup"><span data-stu-id="f76d2-106">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="f76d2-107">En situation där detta kan vara användbart är att ändra data så att de blir mer användbara.</span><span class="sxs-lookup"><span data-stu-id="f76d2-107">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="f76d2-108">**Win32_LogicalDisk** -klassen från WMI kan till exempel användas för att returnera information om ledigt utrymme för varje lokal disk.</span><span class="sxs-lookup"><span data-stu-id="f76d2-108">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="f76d2-109">Data returneras i antal byte, vilket gör det svårt att läsa:</span><span class="sxs-lookup"><span data-stu-id="f76d2-109">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="f76d2-110">Vi kan konvertera värdet för det **lediga utrymmet** till megabyte genom att dividera varje värde med 1 MB.</span><span class="sxs-lookup"><span data-stu-id="f76d2-110">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="f76d2-111">Du kan göra det i ett- `ForEach-Object` skript block genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="f76d2-111">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="f76d2-112">Tyvärr är utdata nu data utan tillhör ande etikett.</span><span class="sxs-lookup"><span data-stu-id="f76d2-112">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="f76d2-113">Eftersom WMI-egenskaper som detta är skrivskyddade kan du inte konvertera ett **ledigt utrymme**direkt.</span><span class="sxs-lookup"><span data-stu-id="f76d2-113">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="f76d2-114">Om du skriver följande:</span><span class="sxs-lookup"><span data-stu-id="f76d2-114">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="f76d2-115">Du får ett fel meddelande:</span><span class="sxs-lookup"><span data-stu-id="f76d2-115">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="f76d2-116">Du kan organisera om data med hjälp av vissa avancerade tekniker, men en enklare metod är att skapa ett nytt objekt genom att använda `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f76d2-116">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
