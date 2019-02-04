---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Välj delar av objekt Välj objekt
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684516"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="61f53-103">Välj delar av objekt (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="61f53-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="61f53-104">Du kan använda den **Select-Object** cmdlet för att skapa nya, anpassade Windows PowerShell-objekt som innehåller egenskaper som har valt från de objekt som du använder för att skapa dem.</span><span class="sxs-lookup"><span data-stu-id="61f53-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="61f53-105">Skriv följande kommando för att skapa ett nytt objekt som innehåller endast namn och FreeSpace Win32_LogicalDisk WMI-klass:</span><span class="sxs-lookup"><span data-stu-id="61f53-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="61f53-106">Du kan inte se vilken typ av data efter kommandot, men om du skicka resultatet till Get-Member när Select-Object Berätta att du har en ny typ av objekt, en PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="61f53-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="61f53-107">Select-Object har många användningsområden.</span><span class="sxs-lookup"><span data-stu-id="61f53-107">Select-Object has many uses.</span></span> <span data-ttu-id="61f53-108">En av dem replikering av data som du sedan kan ändra.</span><span class="sxs-lookup"><span data-stu-id="61f53-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="61f53-109">Vi kan nu hantera problemet som vi körde i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="61f53-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="61f53-110">Vi kan uppdatera värdet för FreeSpace i vår nyligen skapade objekt och utdata innehåller den beskrivande etiketten:</span><span class="sxs-lookup"><span data-stu-id="61f53-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```