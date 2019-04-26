---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Upprepa en uppgift för flera objekt ForEach-Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086178"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="d54d7-103">Upprepa en uppgift för flera objekt (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="d54d7-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="d54d7-104">Den **ForEach-Object** cmdlet använder skriptblocken och `$_` beskrivning av det aktuella pipeline-objektet så att du kan köra ett kommando för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="d54d7-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="d54d7-105">Detta kan användas för att utföra vissa komplicerade uppgifter.</span><span class="sxs-lookup"><span data-stu-id="d54d7-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="d54d7-106">En situation där det kan vara användbart manipulera data för att göra det mer användbart.</span><span class="sxs-lookup"><span data-stu-id="d54d7-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="d54d7-107">Win32_LogicalDisk klassen från WMI kan till exempel användas för att returnera information om ledigt utrymme för varje lokal disk.</span><span class="sxs-lookup"><span data-stu-id="d54d7-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="d54d7-108">Data returneras när det gäller byte, men, vilket gör det svårt att läsa:</span><span class="sxs-lookup"><span data-stu-id="d54d7-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="d54d7-109">Vi kan konvertera FreeSpace värdet till megabyte genom att dividera varje värde med 1024 två gånger. data är i kilobyte efter första divisionen och efter den andra delen av är det megabyte.</span><span class="sxs-lookup"><span data-stu-id="d54d7-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="d54d7-110">Du kan göra det i en ForEach-Object-skriptblocket genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="d54d7-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="d54d7-111">Utdata är tyvärr nu data med inga associerade etiketten.</span><span class="sxs-lookup"><span data-stu-id="d54d7-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="d54d7-112">Du kan inte direkt konvertera FreeSpace eftersom WMI-egenskaper som detta är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="d54d7-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="d54d7-113">Om du anger detta:</span><span class="sxs-lookup"><span data-stu-id="d54d7-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="d54d7-114">Du får ett felmeddelande visas:</span><span class="sxs-lookup"><span data-stu-id="d54d7-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="d54d7-115">Du kan ordna om data med hjälp av några avancerade tekniker, men en enklare metod är att skapa ett nytt objekt genom att använda **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="d54d7-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>