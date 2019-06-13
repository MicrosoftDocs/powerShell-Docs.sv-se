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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="6ca0c-103">Välj delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="6ca0c-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="6ca0c-104">Du kan använda den **Select-Object** cmdlet för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper som har valt från de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="6ca0c-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="6ca0c-105">Skriv följande kommando för att skapa ett nytt objekt som innehåller endast namn och FreeSpace Win32_LogicalDisk WMI-klass:</span><span class="sxs-lookup"><span data-stu-id="6ca0c-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="6ca0c-106">Du kan inte se vilken typ av data efter kommandot, men om du skicka resultatet till Get-Member när Select-Object Berätta att du har en ny typ av objekt, en PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="6ca0c-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="6ca0c-107">Select-Object har många användningsområden.</span><span class="sxs-lookup"><span data-stu-id="6ca0c-107">Select-Object has many uses.</span></span> <span data-ttu-id="6ca0c-108">En av dem replikering av data som du sedan kan ändra.</span><span class="sxs-lookup"><span data-stu-id="6ca0c-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="6ca0c-109">Vi kan nu hantera problemet som vi körde i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="6ca0c-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="6ca0c-110">Vi kan uppdatera värdet för FreeSpace i vår nyligen skapade objekt och utdata innehåller den beskrivande etiketten:</span><span class="sxs-lookup"><span data-stu-id="6ca0c-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
