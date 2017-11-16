---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="d49c0-102">Urklipps-cmdletar</span><span class="sxs-lookup"><span data-stu-id="d49c0-102">Clipboard cmdlets</span></span>
<span data-ttu-id="d49c0-103">**Get-Urklipp** och **Set Urklipp** gör det enklare att överföra innehåll till och från en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d49c0-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="d49c0-104">Till exempel om du använder Utforskaren för att kopiera tre filer till Urklipp (genom att markera dem och trycka på `ctrl-c`, till exempel), du kan sedan enkelt komma åt innehållet i Urklipp som en lista över filer:</span><span class="sxs-lookup"><span data-stu-id="d49c0-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="d49c0-105">Cmdlet: ar för Urklipp stöder bilder, ljudfiler, fillistor och text.</span><span class="sxs-lookup"><span data-stu-id="d49c0-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

