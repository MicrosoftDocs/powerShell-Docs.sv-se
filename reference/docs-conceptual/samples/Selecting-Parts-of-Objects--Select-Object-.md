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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="8372e-103">Välja delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="8372e-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="8372e-104">Du kan använda cmdleten **Select-Object** för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper som valts från de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="8372e-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="8372e-105">Skriv följande kommando för att skapa ett nytt objekt som bara innehåller egenskaperna för namn och ledigt utrymme i Win32_LogicalDisk WMI-klassen:</span><span class="sxs-lookup"><span data-stu-id="8372e-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="8372e-106">Du kan inte se typen av data efter att kommandot har utfärdats, men om du skickar resultatet till att bli medlem efter Select-Object kan du se att du har en ny typ av objekt, en PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="8372e-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="8372e-107">Select-Object har många användnings områden.</span><span class="sxs-lookup"><span data-stu-id="8372e-107">Select-Object has many uses.</span></span> <span data-ttu-id="8372e-108">En av dem replikerar data som du sedan kan ändra.</span><span class="sxs-lookup"><span data-stu-id="8372e-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="8372e-109">Vi kan nu hantera problemet som vi körde i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="8372e-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="8372e-110">Vi kan uppdatera värdet för ledigt utrymme i våra nyligen skapade objekt och utdata kommer att innehålla den beskrivande etiketten:</span><span class="sxs-lookup"><span data-stu-id="8372e-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
