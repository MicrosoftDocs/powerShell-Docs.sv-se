---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Arbeta med filer och mappar
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215530"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="475e8-103">Arbeta med filer och mappar</span><span class="sxs-lookup"><span data-stu-id="475e8-103">Working with Files and Folders</span></span>

<span data-ttu-id="475e8-104">Att navigera genom Windows PowerShell-enheter och ändra objekten på dem liknar att manipulera filer och mappar på fysiska Windows-diskar.</span><span class="sxs-lookup"><span data-stu-id="475e8-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="475e8-105">I det här avsnittet beskrivs hur du hanterar vissa åtgärder för att manipulera filer och mappar med hjälp av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="475e8-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="475e8-106">Visar alla filer och mappar i en mapp</span><span class="sxs-lookup"><span data-stu-id="475e8-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="475e8-107">Du kan hämta alla objekt direkt i en mapp med hjälp av **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="475e8-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="475e8-108">Lägg till den valfria **Force** -parametern om du vill visa dolda eller system objekt.</span><span class="sxs-lookup"><span data-stu-id="475e8-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="475e8-109">Detta kommando visar till exempel direkt innehållet i Windows PowerShell-enhet C (som är samma som den fysiska Windows-enheten C):</span><span class="sxs-lookup"><span data-stu-id="475e8-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="475e8-110">Kommandot visar bara de objekt som finns direkt, ungefär som att använda CMD. Exes **dir** -kommando eller **ls** i ett UNIX-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="475e8-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="475e8-111">Du måste ange parametern **-rekursivt** för att kunna visa befintliga objekt.</span><span class="sxs-lookup"><span data-stu-id="475e8-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="475e8-112">(Det kan ta mycket lång tid att slutföra.) Så här visar du allt på C-enheten:</span><span class="sxs-lookup"><span data-stu-id="475e8-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="475e8-113">**Get-ChildItem** kan filtrera objekt med dess **sökväg**, **filtrera**, **Inkludera**och **exkludera** parametrar, men de är vanligt vis endast baserade på namn.</span><span class="sxs-lookup"><span data-stu-id="475e8-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="475e8-114">Du kan utföra komplex filtrering baserat på andra egenskaper för objekt genom att använda **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="475e8-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="475e8-115">Följande kommando hittar alla körbara filer i mappen program som senast ändrades efter den 1 oktober 2005 och som inte är mindre än 1 MB eller större än 10 megabyte:</span><span class="sxs-lookup"><span data-stu-id="475e8-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="475e8-116">Kopiera filer och mappar</span><span class="sxs-lookup"><span data-stu-id="475e8-116">Copying Files and Folders</span></span>

<span data-ttu-id="475e8-117">Kopieringen görs med **Kopiera objekt**.</span><span class="sxs-lookup"><span data-stu-id="475e8-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="475e8-118">Följande kommando säkerhetskopierar c:\\Boot. ini till C:\\Boot. bak:</span><span class="sxs-lookup"><span data-stu-id="475e8-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="475e8-119">Om målfilen redan finns, Miss lyckas kopierings försöket.</span><span class="sxs-lookup"><span data-stu-id="475e8-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="475e8-120">Om du vill skriva över ett redan befintligt mål använder du parametern **Force** :</span><span class="sxs-lookup"><span data-stu-id="475e8-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="475e8-121">Kommandot fungerar även om målet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="475e8-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="475e8-122">Kopiering av mappar fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="475e8-122">Folder copying works the same way.</span></span> <span data-ttu-id="475e8-123">Det här kommandot kopierar mappen c:\\Temp\\TEST1 till den nya mappen c:\\Temp\\DeleteMe rekursivt:</span><span class="sxs-lookup"><span data-stu-id="475e8-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="475e8-124">Du kan också kopiera ett urval av objekt.</span><span class="sxs-lookup"><span data-stu-id="475e8-124">You can also copy a selection of items.</span></span> <span data-ttu-id="475e8-125">Följande kommando kopierar alla. txt-filer som finns var som helst\\i c: data\\till\\c: Temp-text:</span><span class="sxs-lookup"><span data-stu-id="475e8-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="475e8-126">Du kan fortfarande använda andra verktyg för att utföra fil system kopior.</span><span class="sxs-lookup"><span data-stu-id="475e8-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="475e8-127">XCOPY-, ROBOCOPY-och COM-objekt, till exempel **Scripting. FileSystemObject,** allt arbete i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="475e8-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="475e8-128">Du kan till exempel använda Windows Script Host **Scripting. filesystem com-** klassen för att säkerhetskopiera C:\\Boot. ini till C:\\Boot. bak:</span><span class="sxs-lookup"><span data-stu-id="475e8-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="475e8-129">Skapa filer och mappar</span><span class="sxs-lookup"><span data-stu-id="475e8-129">Creating Files and Folders</span></span>

<span data-ttu-id="475e8-130">Att skapa nya objekt fungerar likadant på alla Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="475e8-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="475e8-131">Om en Windows PowerShell-provider har fler än en typ av objekt, till exempel Windows PowerShell-providern för fil systemet skiljer sig mellan kataloger och filer, måste du ange objekt typen.</span><span class="sxs-lookup"><span data-stu-id="475e8-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="475e8-132">Det här kommandot skapar en ny mapp C\\:\\Temp ny mapp:</span><span class="sxs-lookup"><span data-stu-id="475e8-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="475e8-133">Det här kommandot skapar en ny tom fil C\\:\\Temp New\\Folder File. txt</span><span class="sxs-lookup"><span data-stu-id="475e8-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="475e8-134">Ta bort alla filer och mappar i en mapp</span><span class="sxs-lookup"><span data-stu-id="475e8-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="475e8-135">Du kan ta bort objekt som finns i **Remove-item**, men du uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="475e8-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="475e8-136">Om du till exempel försöker ta bort mappen C:\\Temp\\-DeleteMe som innehåller andra objekt, uppmanas du i Windows PowerShell att bekräfta innan du tar bort mappen:</span><span class="sxs-lookup"><span data-stu-id="475e8-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="475e8-137">Om du inte vill bli tillfrågad om varje objekt som ingår, anger du parametern **rekursivt** :</span><span class="sxs-lookup"><span data-stu-id="475e8-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="475e8-138">Mappa en lokal mapp som en enhet</span><span class="sxs-lookup"><span data-stu-id="475e8-138">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="475e8-139">Du kan också mappa en lokal mapp med kommandot **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="475e8-139">You can also map a local folder, using the **New-PSDrive** command.</span></span> <span data-ttu-id="475e8-140">Följande kommando skapar en lokal enhet P: rotad i katalogen lokala program filer, som endast visas från PowerShell-sessionen:</span><span class="sxs-lookup"><span data-stu-id="475e8-140">The following command creates a local drive P: rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="475e8-141">Precis som med nätverks enheter är enheter som mappas i Windows PowerShell direkt synliga för Windows PowerShell-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="475e8-141">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span>
<span data-ttu-id="475e8-142">För att du ska kunna skapa en mappad enhet som visas i Utforskaren, krävs parametern **-persist** .</span><span class="sxs-lookup"><span data-stu-id="475e8-142">In order to create a mapped drive visible from File Explorer, the parameter **-Persist** is needed.</span></span> <span data-ttu-id="475e8-143">Dock kan endast fjärrsökvägar användas med persist.</span><span class="sxs-lookup"><span data-stu-id="475e8-143">However, only remote paths can be used with Persist.</span></span>


## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="475e8-144">Läsa en textfil i en matris</span><span class="sxs-lookup"><span data-stu-id="475e8-144">Reading a Text File into an Array</span></span>

<span data-ttu-id="475e8-145">Ett av de vanligaste lagrings formaten för text data finns i en fil med separata rader som behandlas som distinkta data element.</span><span class="sxs-lookup"><span data-stu-id="475e8-145">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="475e8-146">Cmdleten **Get-Content** kan användas för att läsa en hel fil i ett enda steg, som du ser här:</span><span class="sxs-lookup"><span data-stu-id="475e8-146">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="475e8-147">**Get-Content** behandlar redan data som läses från filen som en matris, med ett element per rad med fil innehåll.</span><span class="sxs-lookup"><span data-stu-id="475e8-147">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="475e8-148">Du kan bekräfta detta genom att kontrol lera **längden** på det returnerade innehållet:</span><span class="sxs-lookup"><span data-stu-id="475e8-148">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="475e8-149">Det här kommandot är mest användbart för att hämta listor med information till Windows PowerShell direkt.</span><span class="sxs-lookup"><span data-stu-id="475e8-149">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="475e8-150">Du kan till exempel lagra en lista med dator namn eller IP-adresser i en fil C:\\Temp\\domainMembers. txt med ett namn på varje rad i filen.</span><span class="sxs-lookup"><span data-stu-id="475e8-150">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="475e8-151">Du kan använda **Get-Content** för att hämta fil innehållet och placera dem i variabeln **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="475e8-151">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="475e8-152">**$Computers** är nu en matris som innehåller ett dator namn i varje element.</span><span class="sxs-lookup"><span data-stu-id="475e8-152">**$Computers** is now an array containing a computer name in each element.</span></span>
