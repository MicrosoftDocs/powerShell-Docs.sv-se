---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188065"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="e7c52-102">Urklipps-cmdletar</span><span class="sxs-lookup"><span data-stu-id="e7c52-102">Clipboard cmdlets</span></span>
<span data-ttu-id="e7c52-103">**Get-Urklipp** och **Set Urklipp** gör det enklare att överföra innehåll till och från en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e7c52-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="e7c52-104">Till exempel om du använder Utforskaren för att kopiera tre filer till Urklipp (genom att markera dem och trycka på `ctrl-c`, till exempel), du kan sedan enkelt komma åt innehållet i Urklipp som en lista över filer:</span><span class="sxs-lookup"><span data-stu-id="e7c52-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="e7c52-105">Cmdlet: ar för Urklipp stöder bilder, ljudfiler, fillistor och text.</span><span class="sxs-lookup"><span data-stu-id="e7c52-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
