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
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Upprepa en uppgift för flera objekt (ForEach-Object)

`ForEach-Object`Cmdleten använder skript block och `$_` beskrivningen för det aktuella pipeline-objektet så att du kan köra ett kommando på varje objekt i pipelinen. Detta kan användas för att utföra komplicerade uppgifter.

En situation där detta kan vara användbart är att ändra data så att de blir mer användbara. **Win32_LogicalDisk** -klassen från WMI kan till exempel användas för att returnera information om ledigt utrymme för varje lokal disk. Data returneras i antal byte, vilket gör det svårt att läsa:

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

Vi kan konvertera värdet för det **lediga utrymmet** till megabyte genom att dividera varje värde med 1 MB. Du kan göra det i ett- `ForEach-Object` skript block genom att skriva:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

Tyvärr är utdata nu data utan tillhör ande etikett. Eftersom WMI-egenskaper som detta är skrivskyddade kan du inte konvertera ett **ledigt utrymme**direkt. Om du skriver följande:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

Du får ett fel meddelande:

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

Du kan organisera om data med hjälp av vissa avancerade tekniker, men en enklare metod är att skapa ett nytt objekt genom att använda `Select-Object` .
