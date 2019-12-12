---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Upprepa en uppgift för ett förgrunds objekt för flera objekt
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030813"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Upprepa en uppgift för flera objekt (förgrunds objekt)

I **förgrunds-Object-** cmdlet används skript block och `$_` beskrivningen för det aktuella pipelinen så att du kan köra ett kommando på varje objekt i pipelinen. Detta kan användas för att utföra komplicerade uppgifter.

En situation där detta kan vara användbart är att ändra data så att de blir mer användbara. Win32_LogicalDisk-klassen från WMI kan till exempel användas för att returnera information om ledigt utrymme för varje lokal disk. Data returneras i antal byte, vilket gör det svårt att läsa:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Vi kan konvertera värdet för ledigt utrymme till megabyte genom att dividera varje värde med 1024 två gånger. efter den första divisionen är data i kilobyte och efter den andra divisionen är det megabyte. Du kan göra det i en förgrunds-objekt skript block genom att skriva:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Tyvärr är utdata nu data utan tillhör ande etikett. Eftersom WMI-egenskaper som detta är skrivskyddade kan du inte konvertera ett ledigt utrymme direkt. Om du skriver följande:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Du får ett fel meddelande:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Du kan organisera om data med hjälp av vissa avancerade tekniker, men en enklare metod är att skapa ett nytt objekt genom att använda **Select-Object**.
