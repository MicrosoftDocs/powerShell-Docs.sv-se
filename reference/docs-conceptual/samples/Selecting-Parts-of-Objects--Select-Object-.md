---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Välj delar av objekt Välj objekt
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030121"
---
# <a name="selecting-parts-of-objects-select-object"></a>Välj delar av objekt (Select-Object)

Du kan använda den **Select-Object** cmdlet för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper som har valt från de objekt som du använder för att skapa dem. Skriv följande kommando för att skapa ett nytt objekt som innehåller endast namn och FreeSpace Win32_LogicalDisk WMI-klass:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Du kan inte se vilken typ av data efter kommandot, men om du skicka resultatet till Get-Member när Select-Object Berätta att du har en ny typ av objekt, en PSCustomObject:

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

Select-Object har många användningsområden. En av dem replikering av data som du sedan kan ändra. Vi kan nu hantera problemet som vi körde i föregående avsnitt. Vi kan uppdatera värdet för FreeSpace i vår nyligen skapade objekt och utdata innehåller den beskrivande etiketten:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
