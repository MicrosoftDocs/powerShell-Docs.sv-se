---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Upprepa en aktivitet för flera objekt ForEach-Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 8b8002af3ade0905421760ce29cdc84b084236e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954287"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="033a2-103">Upprepa en aktivitet för flera objekt (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="033a2-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="033a2-104">Den **ForEach-Object** cmdlet använder skriptblocken och $_ beskrivningen för det aktuella pipeline-objektet så att du kan köra ett kommando för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="033a2-104">The **ForEach-Object** cmdlet uses script blocks and the $_ descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="033a2-105">Detta kan användas för att utföra vissa komplicerade uppgifter.</span><span class="sxs-lookup"><span data-stu-id="033a2-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="033a2-106">En situation där detta kan vara användbart manipulera data så att de blir mer användbara.</span><span class="sxs-lookup"><span data-stu-id="033a2-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="033a2-107">Win32_LogicalDisk klassen från WMI kan till exempel användas för att returnera information om ledigt diskutrymme för varje lokal disk.</span><span class="sxs-lookup"><span data-stu-id="033a2-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="033a2-108">Data returneras i byte, vilket gör det svårt att läsa:</span><span class="sxs-lookup"><span data-stu-id="033a2-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="033a2-109">Vi kan konvertera FreeSpace värdet till megabyte genom att dividera varje värde med 1024 två gånger. efter den första divisionen data är i kilobyte efter det andra division är megabyte</span><span class="sxs-lookup"><span data-stu-id="033a2-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="033a2-110">Du kan göra det i ett ForEach-Object-skriptblock genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="033a2-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="033a2-111">Tyvärr är utdata nu data med ingen tillhörande etikett.</span><span class="sxs-lookup"><span data-stu-id="033a2-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="033a2-112">Eftersom WMI-egenskaper som det är skrivskyddad, kan du konvertera FreeSpace direkt.</span><span class="sxs-lookup"><span data-stu-id="033a2-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="033a2-113">Om du anger detta:</span><span class="sxs-lookup"><span data-stu-id="033a2-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="033a2-114">Du får ett felmeddelande:</span><span class="sxs-lookup"><span data-stu-id="033a2-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="033a2-115">Du kan ordna data genom att använda vissa avancerade, men en enklare metod är att skapa ett nytt objekt genom att använda **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="033a2-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>