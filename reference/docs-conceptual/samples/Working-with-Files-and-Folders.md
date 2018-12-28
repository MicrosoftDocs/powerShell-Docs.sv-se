---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med filer och mappar
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: a8d57a1c269d95e692db6c3f1ae10df49e305e4e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404798"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="2c0aa-103">Arbeta med filer och mappar</span><span class="sxs-lookup"><span data-stu-id="2c0aa-103">Working with Files and Folders</span></span>

<span data-ttu-id="2c0aa-104">Navigera i Windows PowerShell-enheter och manipulera objekt på dem liknar manipulera filer och mappar på Windows fysiska hårddiskar.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="2c0aa-105">Det här avsnittet beskrivs hur du arbetar med specifika fil- och manipulering av uppgifter-med hjälp av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="2c0aa-106">Visa en lista över alla filer och mappar i en mapp</span><span class="sxs-lookup"><span data-stu-id="2c0aa-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="2c0aa-107">Du kan hämta alla objekt direkt i en mapp med hjälp av **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="2c0aa-108">Lägg till det valfria **kraft** parameter för att visa dolda eller poster.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="2c0aa-109">Det här kommandot visar till exempel direkt innehållet i Windows PowerShell-enhet C (som är samma som den fysiska Windows-enheten C):</span><span class="sxs-lookup"><span data-stu-id="2c0aa-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="2c0aa-110">Kommandot visas endast direkt inneslutna objekten, ungefär som med Cmd.exe's **DIR** kommando eller **ls** i ett UNIX-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="2c0aa-111">Du vill visa objekten, måste du ange den **-Recurse** parametern samt.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="2c0aa-112">(Det kan ta en mycket lång tid att slutföra.) Visa en lista över allt på enhet C:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="2c0aa-113">**Get-ChildItem** kan filtrera objekt med dess **sökväg**, **Filter**, **inkludera**, och **undanta** parametrar, men de är Vanligtvis baseras endast på namnet.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="2c0aa-114">Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="2c0aa-115">Kommandot söker efter alla körbara filer i mappen program som senast ändrades efter den 1 oktober 2005 och som varken är mindre än 1 MB eller större än 10 MB:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="2c0aa-116">Kopiera filer och mappar</span><span class="sxs-lookup"><span data-stu-id="2c0aa-116">Copying Files and Folders</span></span>

<span data-ttu-id="2c0aa-117">Kopieringen är klar med **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="2c0aa-118">Följande kommando säkerhetskopierar C:\\boot.ini till C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="2c0aa-119">Kopiera försöket misslyckas om filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="2c0aa-120">Om du vill skriva över en befintlig mål, använda den **kraft** parameter:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="2c0aa-121">Det här kommandot fungerar även när målet är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="2c0aa-122">Kopiera mappen fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-122">Folder copying works the same way.</span></span> <span data-ttu-id="2c0aa-123">Det här kommandot kopierar mappen C:\\temp\\test1 till den nya mappen C:\\temp\\DeleteMe rekursivt:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="2c0aa-124">Du kan också kopiera ett urval av objekt.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-124">You can also copy a selection of items.</span></span> <span data-ttu-id="2c0aa-125">I följande kopieras alla txt-filer som finns var som helst i c:\\data till c:\\temp\\text:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="2c0aa-126">Du kan fortfarande använda andra verktyg för att kopiera system.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="2c0aa-127">XCOPY ROBOCOPY och COM-objekt, till exempel den **Scripting.FileSystemObject,** användas i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="2c0aa-128">Du kan till exempel använda Windows Script Host **Scripting.FileSystem COM** klassen för att säkerhetskopiera C:\\boot.ini till C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="2c0aa-129">Skapa filer och mappar</span><span class="sxs-lookup"><span data-stu-id="2c0aa-129">Creating Files and Folders</span></span>

<span data-ttu-id="2c0aa-130">Skapa nya objekt fungerar på samma på alla Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="2c0aa-131">Om en Windows PowerShell-providern har mer än en typ av objekt, till exempel filsystem Windows PowerShell-providern skiljer mellan kataloger och filer, måste du ange vilken typ av objekt.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="2c0aa-132">Det här kommandot skapar en ny mapp C:\\temp\\ny mapp:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="2c0aa-133">Det här kommandot skapar en ny tom fil C:\\temp\\ny mapp\\fil.txt</span><span class="sxs-lookup"><span data-stu-id="2c0aa-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="2c0aa-134">Ta bort alla filer och mappar i en mapp</span><span class="sxs-lookup"><span data-stu-id="2c0aa-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="2c0aa-135">Du kan ta bort ingående objekt med hjälp av **Remove-Item**, men du kommer att uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="2c0aa-136">Exempel: Om du försöker ta bort mappen C:\\temp\\DeleteMe som innehåller andra objekt, Windows PowerShell uppmanas du att bekräfta innan du tar bort mappen:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="2c0aa-137">Om du inte vill uppmanas att varje ingående objekt anger du den **Recurse** parameter:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="2c0aa-138">Mappa en lokal mapp som en tillgänglig Windows-enhet</span><span class="sxs-lookup"><span data-stu-id="2c0aa-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="2c0aa-139">Du kan också mappa en lokal mapp med hjälp av den **subst** kommando.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="2c0aa-140">Följande kommando skapar en lokal enhet P: rotad i den lokala katalogen för programfiler:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="2c0aa-141">Precis som med nätverksenheter, mappade enheter i Windows PowerShell med hjälp av **subst** visas direkt för Windows PowerShell-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="2c0aa-142">Läser en textfil i en matris</span><span class="sxs-lookup"><span data-stu-id="2c0aa-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="2c0aa-143">En av de vanliga storage format för textdata är i en fil med separata rader behandlas som distinkta dataelement.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="2c0aa-144">Den **Get-innehåll** cmdlet kan användas för att läsa en hel fil i ett steg som visas här:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="2c0aa-145">**Get-innehåll** redan behandlar data läses från filen som en matris med ett element per rad i filinnehållet.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="2c0aa-146">Du kan kontrollera detta genom att markera den **längd** av returnerat innehåll:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="2c0aa-147">Det här kommandot är mest användbara för att hämta en lista över information i Windows PowerShell direkt.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="2c0aa-148">Du kan till exempel lagra en lista med datornamn eller IP-adresser i en fil C:\\temp\\domainMembers.txt med ett namn på varje rad i filen.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="2c0aa-149">Du kan använda **Get-innehåll** hämtar filinnehållet och placerar dem i variabeln **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="2c0aa-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="2c0aa-150">**$Computers** är nu en matris som innehåller namnet på en dator i varje element.</span><span class="sxs-lookup"><span data-stu-id="2c0aa-150">**$Computers** is now an array containing a computer name in each element.</span></span>
