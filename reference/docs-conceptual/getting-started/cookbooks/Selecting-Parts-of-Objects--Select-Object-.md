---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Välj objekt för att välja delar av objekt"
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="selecting-parts-of-objects-select-object"></a>Markera delar av objekt (Select-Object)
Du kan använda den **Select-Object** för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper för valt de objekt som du använder för att skapa dem. Skriv följande kommando för att skapa ett nytt objekt som innehåller endast namn och FreeSpace Win32_LogicalDisk WMI-klassen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Du kan inte se vilken typ av data efter kommandot, men om du skicka resultatet till Get-medlem efter Select-Object Berätta att du har en ny typ av objekt, en PSCustomObject:

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

Select-Object har många användningsområden. En av dem replikerar data som du sedan kan ändra. Vi kan nu hantera problemet vi råkade i föregående avsnitt. Vi kan uppdatera värdet för FreeSpace i vår nya objekt och utdata innehåller beskrivande etikett:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
