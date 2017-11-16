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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="5c31d-103">Markera delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="5c31d-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="5c31d-104">Du kan använda den **Select-Object** för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper för valt de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="5c31d-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="5c31d-105">Skriv följande kommando för att skapa ett nytt objekt som innehåller endast namn och FreeSpace Win32_LogicalDisk WMI-klassen:</span><span class="sxs-lookup"><span data-stu-id="5c31d-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="5c31d-106">Du kan inte se vilken typ av data efter kommandot, men om du skicka resultatet till Get-medlem efter Select-Object Berätta att du har en ny typ av objekt, en PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="5c31d-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="5c31d-107">Select-Object har många användningsområden.</span><span class="sxs-lookup"><span data-stu-id="5c31d-107">Select-Object has many uses.</span></span> <span data-ttu-id="5c31d-108">En av dem replikerar data som du sedan kan ändra.</span><span class="sxs-lookup"><span data-stu-id="5c31d-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="5c31d-109">Vi kan nu hantera problemet vi råkade i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5c31d-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="5c31d-110">Vi kan uppdatera värdet för FreeSpace i vår nya objekt och utdata innehåller beskrivande etikett:</span><span class="sxs-lookup"><span data-stu-id="5c31d-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

