---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Välja objekt för objekt Välj objekt
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030121"
---
# <a name="selecting-parts-of-objects-select-object"></a>Välja delar av objekt (Select-Object)

Du kan använda cmdleten **Select-Object** för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper som valts från de objekt som du använder för att skapa dem. Skriv följande kommando för att skapa ett nytt objekt som bara innehåller egenskaperna för namn och ledigt utrymme i Win32_LogicalDisk WMI-klassen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Du kan inte se typen av data efter att kommandot har utfärdats, men om du skickar resultatet till att bli medlem efter Select-Object kan du se att du har en ny typ av objekt, en PSCustomObject:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Select-Object har många användnings områden. En av dem replikerar data som du sedan kan ändra. Vi kan nu hantera problemet som vi körde i föregående avsnitt. Vi kan uppdatera värdet för ledigt utrymme i våra nyligen skapade objekt och utdata kommer att innehålla den beskrivande etiketten:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
