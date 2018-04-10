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
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Upprepa en aktivitet för flera objekt (ForEach-Object)

Den **ForEach-Object** cmdlet använder skriptblocken och $_ beskrivningen för det aktuella pipeline-objektet så att du kan köra ett kommando för varje objekt i pipelinen. Detta kan användas för att utföra vissa komplicerade uppgifter.

En situation där detta kan vara användbart manipulera data så att de blir mer användbara. Win32_LogicalDisk klassen från WMI kan till exempel användas för att returnera information om ledigt diskutrymme för varje lokal disk. Data returneras i byte, vilket gör det svårt att läsa:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Vi kan konvertera FreeSpace värdet till megabyte genom att dividera varje värde med 1024 två gånger. efter den första divisionen data är i kilobyte efter det andra division är megabyte Du kan göra det i ett ForEach-Object-skriptblock genom att skriva:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Tyvärr är utdata nu data med ingen tillhörande etikett. Eftersom WMI-egenskaper som det är skrivskyddad, kan du konvertera FreeSpace direkt. Om du anger detta:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Du får ett felmeddelande:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Du kan ordna data genom att använda vissa avancerade, men en enklare metod är att skapa ett nytt objekt genom att använda **Select-Object**.