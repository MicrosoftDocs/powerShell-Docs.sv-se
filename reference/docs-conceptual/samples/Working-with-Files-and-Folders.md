---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeta med filer och mappar
description: Den här artikeln beskriver hur du hanterar vissa åtgärder för att manipulera filer och mappar med hjälp av PowerShell.
ms.openlocfilehash: c0c3abb082b05296daa480ac06bcbfa3a784e0c9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500036"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="ceb23-104">Arbeta med filer och mappar</span><span class="sxs-lookup"><span data-stu-id="ceb23-104">Working with Files and Folders</span></span>

<span data-ttu-id="ceb23-105">Att navigera genom Windows PowerShell-enheter och ändra objekten på dem liknar att manipulera filer och mappar på fysiska Windows-diskar.</span><span class="sxs-lookup"><span data-stu-id="ceb23-105">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="ceb23-106">Den här artikeln beskriver hur du hanterar vissa åtgärder för att manipulera filer och mappar med hjälp av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb23-106">This article discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="ceb23-107">Visar alla filer och mappar i en mapp</span><span class="sxs-lookup"><span data-stu-id="ceb23-107">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="ceb23-108">Du kan hämta alla objekt direkt i en mapp med hjälp av `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="ceb23-108">You can get all items directly within a folder by using `Get-ChildItem`.</span></span> <span data-ttu-id="ceb23-109">Lägg till den valfria **Force** -parametern om du vill visa dolda eller system objekt.</span><span class="sxs-lookup"><span data-stu-id="ceb23-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="ceb23-110">Detta kommando visar till exempel direkt innehållet i Windows PowerShell-enhet C (som är samma som den fysiska Windows-enheten C):</span><span class="sxs-lookup"><span data-stu-id="ceb23-110">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="ceb23-111">Kommandot visar bara de objekt som finns direkt, ungefär som att `Cmd.exe` använda `DIR` kommandot eller `ls` i ett UNIX-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="ceb23-111">The command lists only the directly contained items, much like using `Cmd.exe`'s `DIR` command or `ls` in a UNIX shell.</span></span> <span data-ttu-id="ceb23-112">För att kunna visa de objekt som finns måste du även ange `-Recurse` parametern.</span><span class="sxs-lookup"><span data-stu-id="ceb23-112">In order to show contained items, you need to specify the `-Recurse` parameter as well.</span></span> <span data-ttu-id="ceb23-113">(Det kan ta mycket lång tid att slutföra.) Så här visar du allt på C-enheten:</span><span class="sxs-lookup"><span data-stu-id="ceb23-113">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="ceb23-114">`Get-ChildItem` kan filtrera objekt med dess **sökväg**, **filtrera**, **Inkludera**och **exkludera** parametrar, men de är vanligt vis endast baserade på namn.</span><span class="sxs-lookup"><span data-stu-id="ceb23-114">`Get-ChildItem` can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="ceb23-115">Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="ceb23-115">You can perform complex filtering based on other properties of items by using `Where-Object`.</span></span>

<span data-ttu-id="ceb23-116">Följande kommando hittar alla körbara filer i mappen program som senast ändrades efter den 1 oktober 2005 och som inte är mindre än 1 MB eller större än 10 megabyte:</span><span class="sxs-lookup"><span data-stu-id="ceb23-116">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="ceb23-117">Kopiera filer och mappar</span><span class="sxs-lookup"><span data-stu-id="ceb23-117">Copying Files and Folders</span></span>

<span data-ttu-id="ceb23-118">Kopieringen görs med `Copy-Item` .</span><span class="sxs-lookup"><span data-stu-id="ceb23-118">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="ceb23-119">Följande kommando säkerhetskopierar C: \\boot.ini till c: \\ Boot. bak:</span><span class="sxs-lookup"><span data-stu-id="ceb23-119">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="ceb23-120">Om målfilen redan finns, Miss lyckas kopierings försöket.</span><span class="sxs-lookup"><span data-stu-id="ceb23-120">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="ceb23-121">Om du vill skriva över ett redan befintligt mål använder du parametern **Force** :</span><span class="sxs-lookup"><span data-stu-id="ceb23-121">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="ceb23-122">Kommandot fungerar även om målet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="ceb23-122">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="ceb23-123">Kopiering av mappar fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="ceb23-123">Folder copying works the same way.</span></span> <span data-ttu-id="ceb23-124">Det här kommandot kopierar mappen `C:\temp\test1` till den nya mappen `C:\temp\DeleteMe` rekursivt:</span><span class="sxs-lookup"><span data-stu-id="ceb23-124">This command copies the folder `C:\temp\test1` to the new folder `C:\temp\DeleteMe` recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="ceb23-125">Du kan också kopiera ett urval av objekt.</span><span class="sxs-lookup"><span data-stu-id="ceb23-125">You can also copy a selection of items.</span></span> <span data-ttu-id="ceb23-126">Följande kommando kopierar alla. txt-filer som finns var som helst i `C:\data` till `C:\temp\text` :</span><span class="sxs-lookup"><span data-stu-id="ceb23-126">The following command copies all .txt files contained anywhere in `C:\data` to `C:\temp\text`:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="ceb23-127">Du kan fortfarande använda andra verktyg för att utföra fil system kopior.</span><span class="sxs-lookup"><span data-stu-id="ceb23-127">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="ceb23-128">XCOPY-, ROBOCOPY-och COM-objekt, till exempel **Scripting. FileSystemObject,** allt arbete i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb23-128">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="ceb23-129">Du kan till exempel använda Windows Script Host **Scripting. filesystem COM-** klassen för att säkerhetskopiera `C:\boot.ini` till `C:\boot.bak` :</span><span class="sxs-lookup"><span data-stu-id="ceb23-129">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up `C:\boot.ini` to `C:\boot.bak`:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="ceb23-130">Skapa filer och mappar</span><span class="sxs-lookup"><span data-stu-id="ceb23-130">Creating Files and Folders</span></span>

<span data-ttu-id="ceb23-131">Att skapa nya objekt fungerar likadant på alla Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="ceb23-131">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="ceb23-132">Om en Windows PowerShell-provider har fler än en typ av objekt, till exempel Windows PowerShell-providern för fil systemet skiljer sig mellan kataloger och filer, måste du ange objekt typen.</span><span class="sxs-lookup"><span data-stu-id="ceb23-132">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="ceb23-133">Det här kommandot skapar en ny mapp `C:\temp\New Folder` :</span><span class="sxs-lookup"><span data-stu-id="ceb23-133">This command creates a new folder `C:\temp\New Folder`:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="ceb23-134">Det här kommandot skapar en ny tom fil `C:\temp\New Folder\file.txt`</span><span class="sxs-lookup"><span data-stu-id="ceb23-134">This command creates a new empty file `C:\temp\New Folder\file.txt`</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> <span data-ttu-id="ceb23-135">När du använder **Force** -växeln med `New-Item` kommandot för att skapa en mapp, och mappen redan finns, _kommer den inte_ att skriva över eller ersätta mappen.</span><span class="sxs-lookup"><span data-stu-id="ceb23-135">When using the **Force** switch with the `New-Item` command to create a folder, and the folder already exists, it _won't_ overwrite or replace the folder.</span></span> <span data-ttu-id="ceb23-136">Det kommer bara att returnera det befintliga objektet Folder.</span><span class="sxs-lookup"><span data-stu-id="ceb23-136">It will simply return the existing folder object.</span></span> <span data-ttu-id="ceb23-137">Men om du använder `New-Item -Force` på en fil som redan finns _kommer_ filen att skrivas över helt.</span><span class="sxs-lookup"><span data-stu-id="ceb23-137">However, if you use `New-Item -Force` on a file that already exists, the file _will_ be completely overwritten.</span></span>

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="ceb23-138">Ta bort alla filer och mappar i en mapp</span><span class="sxs-lookup"><span data-stu-id="ceb23-138">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="ceb23-139">Du kan ta bort de objekt som finns i `Remove-Item` , men du uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="ceb23-139">You can remove contained items using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ceb23-140">Om du till exempel försöker ta bort mappen `C:\temp\DeleteMe` som innehåller andra objekt, uppmanas du i Windows PowerShell att bekräfta innan du tar bort mappen:</span><span class="sxs-lookup"><span data-stu-id="ceb23-140">For example, if you attempt to delete the folder `C:\temp\DeleteMe` that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ceb23-141">Om du inte vill bli tillfrågad om varje objekt som ingår, anger du parametern **rekursivt** :</span><span class="sxs-lookup"><span data-stu-id="ceb23-141">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="ceb23-142">Mappa en lokal mapp som en enhet</span><span class="sxs-lookup"><span data-stu-id="ceb23-142">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="ceb23-143">Du kan också mappa en lokal mapp med hjälp av `New-PSDrive` kommandot.</span><span class="sxs-lookup"><span data-stu-id="ceb23-143">You can also map a local folder, using the `New-PSDrive` command.</span></span> <span data-ttu-id="ceb23-144">Följande kommando skapar en lokal enhet `P:` som är rotad i katalogen lokala program filer, som endast visas från PowerShell-sessionen:</span><span class="sxs-lookup"><span data-stu-id="ceb23-144">The following command creates a local drive `P:` rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="ceb23-145">Precis som med nätverks enheter är enheter som mappas i Windows PowerShell direkt synliga för Windows PowerShell-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ceb23-145">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span> <span data-ttu-id="ceb23-146">För att kunna skapa en mappad enhet som visas i Utforskaren, `-Persist` krävs parametern.</span><span class="sxs-lookup"><span data-stu-id="ceb23-146">In order to create a mapped drive visible from File Explorer, the parameter `-Persist` is needed.</span></span> <span data-ttu-id="ceb23-147">Dock kan endast fjärrsökvägar användas med persist.</span><span class="sxs-lookup"><span data-stu-id="ceb23-147">However, only remote paths can be used with Persist.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="ceb23-148">Läsa en textfil i en matris</span><span class="sxs-lookup"><span data-stu-id="ceb23-148">Reading a Text File into an Array</span></span>

<span data-ttu-id="ceb23-149">Ett av de vanligaste lagrings formaten för text data finns i en fil med separata rader som behandlas som distinkta data element.</span><span class="sxs-lookup"><span data-stu-id="ceb23-149">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="ceb23-150">`Get-Content`Cmdleten kan användas för att läsa en hel fil i ett enda steg, som du ser här:</span><span class="sxs-lookup"><span data-stu-id="ceb23-150">The `Get-Content` cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="ceb23-151">`Get-Content` behandlar redan data som läses från filen som en matris, med ett element per rad med fil innehåll.</span><span class="sxs-lookup"><span data-stu-id="ceb23-151">`Get-Content` already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="ceb23-152">Du kan bekräfta detta genom att kontrol lera **längden** på det returnerade innehållet:</span><span class="sxs-lookup"><span data-stu-id="ceb23-152">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="ceb23-153">Det här kommandot är mest användbart för att hämta listor med information till Windows PowerShell direkt.</span><span class="sxs-lookup"><span data-stu-id="ceb23-153">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="ceb23-154">Du kan till exempel lagra en lista med dator namn eller IP-adresser i en fil `C:\temp\domainMembers.txt` med ett namn på varje rad i filen.</span><span class="sxs-lookup"><span data-stu-id="ceb23-154">For example, you might store a list of computer names or IP addresses in a file `C:\temp\domainMembers.txt`, with one name on each line of the file.</span></span> <span data-ttu-id="ceb23-155">Du kan använda `Get-Content` för att hämta fil innehållet och infoga dem i variabeln `$Computers` :</span><span class="sxs-lookup"><span data-stu-id="ceb23-155">You can use `Get-Content` to retrieve the file contents and put them in the variable `$Computers`:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="ceb23-156">`$Computers` är nu en matris som innehåller ett dator namn i varje element.</span><span class="sxs-lookup"><span data-stu-id="ceb23-156">`$Computers` is now an array containing a computer name in each element.</span></span>
