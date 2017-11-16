---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Direkt manipulering av objekt
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: d9aa95dcb0da2e8203cbe32d64b95bf33d914166
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="749b1-103">Direkt manipulering av objekt</span><span class="sxs-lookup"><span data-stu-id="749b1-103">Manipulating Items Directly</span></span>
<span data-ttu-id="749b1-104">Element som du ser i Windows PowerShell-enheter, till exempel filer och mappar i systemenheter filer och registernycklar i Windows PowerShell registret enheter, kallas *objekt* i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="749b1-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="749b1-105">Cmdlets för att arbeta med dessa objekt har substantivet **objektet** i sina namn.</span><span class="sxs-lookup"><span data-stu-id="749b1-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="749b1-106">Utdata från den **Get-Command - objektet substantiv** kommando visar att det finns nio Windows PowerShell-cmdletar för objektet.</span><span class="sxs-lookup"><span data-stu-id="749b1-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a><span data-ttu-id="749b1-107">Skapa nya objekt (nytt objekt)</span><span class="sxs-lookup"><span data-stu-id="749b1-107">Creating New Items (New-Item)</span></span>
<span data-ttu-id="749b1-108">Använd för att skapa ett nytt objekt i filsystemet i **nytt objekt** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="749b1-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="749b1-109">Inkludera den **sökväg** parameter med sökvägen till objektet och **ItemType** parametern med värdet ”fil” eller ”directory”.</span><span class="sxs-lookup"><span data-stu-id="749b1-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="749b1-110">Till exempel vill skapa en ny katalog med namnet ”New.Directory"in enhet C:\\Temp-katalog, typ:</span><span class="sxs-lookup"><span data-stu-id="749b1-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="749b1-111">Om du vill skapa en fil, ändrar du värdet för den **ItemType** parameter för ”fil”.</span><span class="sxs-lookup"><span data-stu-id="749b1-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="749b1-112">Till exempel för att skapa en fil med namnet ”file1.txt” i katalogen New.Directory, skriver du:</span><span class="sxs-lookup"><span data-stu-id="749b1-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="749b1-113">Du kan använda samma metod för att skapa en ny registernyckel.</span><span class="sxs-lookup"><span data-stu-id="749b1-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="749b1-114">Faktum är är en registernyckel enklare att skapa eftersom endast objekttypen i Windows-registret är en nyckel.</span><span class="sxs-lookup"><span data-stu-id="749b1-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="749b1-115">(Registerposterna är objektet *egenskaper*.) Till exempel för att skapa en nyckel med namnet ”_Test” i undernyckeln CurrentVersion, skriver du:</span><span class="sxs-lookup"><span data-stu-id="749b1-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="749b1-116">När du skriver en registersökväg Glöm kolon (**:**) i Windows PowerShell enhet namn, HKLM: och HKCU:.</span><span class="sxs-lookup"><span data-stu-id="749b1-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="749b1-117">Utan kolon, kan Windows PowerShell inte identifiera enhetsnamnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="749b1-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

### <a name="why-registry-values-are-not-items"></a><span data-ttu-id="749b1-118">Varför registervärden inte är element</span><span class="sxs-lookup"><span data-stu-id="749b1-118">Why Registry Values are not Items</span></span>
<span data-ttu-id="749b1-119">När du använder den **Get-ChildItem** för att hitta objekt i en registernyckel visas aldrig faktiska registerposter eller deras värden.</span><span class="sxs-lookup"><span data-stu-id="749b1-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="749b1-120">Till exempel registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion\\kör** innehåller vanligtvis flera registerposter som representerar program som körs när systemet startar.</span><span class="sxs-lookup"><span data-stu-id="749b1-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="749b1-121">Men om du använder **Get-ChildItem** för att leta efter underordnade objekt i nyckeln visas bara de **OptionalComponents** undernycklar för nyckeln:</span><span class="sxs-lookup"><span data-stu-id="749b1-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="749b1-122">Även om det skulle vara praktiskt att behandla registerposter som objekt, kan du inte ange en sökväg till en registerpost på ett sätt som garanterar att den är unik.</span><span class="sxs-lookup"><span data-stu-id="749b1-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="749b1-123">Sökvägen notation skiljer inte mellan registerundernyckeln med namnet **kör** och **(standard)** registerpost i den **kör** undernyckel.</span><span class="sxs-lookup"><span data-stu-id="749b1-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="749b1-124">Dessutom eftersom registret postnamnen kan innehålla ett omvänt snedstreck (**\\**), om regsitry poster objekt som du kan inte använda sökväg notation för att särskilja en registerpost med namnet  **Windows\\CurrentVersion\\kör** från undernyckeln som finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="749b1-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if regsitry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

### <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="749b1-125">Byta namn på befintliga objekt (Byt namn på objekt)</span><span class="sxs-lookup"><span data-stu-id="749b1-125">Renaming Existing Items (Rename-Item)</span></span>
<span data-ttu-id="749b1-126">Du kan ändra namnet på en fil eller mapp med det **byta namnet på objektet** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="749b1-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="749b1-127">Följande kommando ändrar namnet på den **file1.txt** filen till **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="749b1-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="749b1-128">Den **byta namnet på objektet** cmdlet kan ändra namnet på en fil eller mapp, men det går inte att flytta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="749b1-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="749b1-129">Kommandot misslyckas eftersom den försöker flytta filen från katalogen New.Directory till Temp-katalogen.</span><span class="sxs-lookup"><span data-stu-id="749b1-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a><span data-ttu-id="749b1-130">Flytta objekt (flytta objekt)</span><span class="sxs-lookup"><span data-stu-id="749b1-130">Moving Items (Move-Item)</span></span>
<span data-ttu-id="749b1-131">Flytta en fil eller mapp med det **flytta objekt** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="749b1-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="749b1-132">Till exempel följande kommando flyttas katalogen New.Directory från enhet C:\\temp-katalogen i roten på enhet C:.</span><span class="sxs-lookup"><span data-stu-id="749b1-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="749b1-133">Om du vill kontrollera att objektet har flyttats, innehåller den **PassThru** parameter för den **flytta objekt** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="749b1-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="749b1-134">Utan **Passthru**, **flytta objekt** cmdleten visas inte några resultat.</span><span class="sxs-lookup"><span data-stu-id="749b1-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a><span data-ttu-id="749b1-135">Kopiera objekt (kopiera objekt)</span><span class="sxs-lookup"><span data-stu-id="749b1-135">Copying Items (Copy-Item)</span></span>
<span data-ttu-id="749b1-136">Om du är bekant med copy-åtgärder i andra, kanske beteendet för den **Copy-Item** cmdlet i Windows PowerShell för att vara annorlunda.</span><span class="sxs-lookup"><span data-stu-id="749b1-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="749b1-137">När du kopierar ett objekt från en plats till en annan, kopierar inte innehållet som standard i Kopiera objekt.</span><span class="sxs-lookup"><span data-stu-id="749b1-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="749b1-138">Till exempel om du kopierar den **New.Directory** katalog från enheten C: till C:\\temp-katalog, kommandot lyckas men kopieras inte filerna i katalogen New.Directory.</span><span class="sxs-lookup"><span data-stu-id="749b1-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="749b1-139">Om du visar innehållet i **C:\\temp\\New.Directory**, hittar du att den inte innehåller några filer:</span><span class="sxs-lookup"><span data-stu-id="749b1-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="749b1-140">Varför inte den **Copy-Item** cmdlet kopiera innehållet till den nya platsen?</span><span class="sxs-lookup"><span data-stu-id="749b1-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="749b1-141">Den **Copy-Item** cmdlet har utformats för att vara generisk och är inte bara för att kopiera filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="749b1-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="749b1-142">Trots att kopiera filer och mappar, kanske du vill kopiera endast för behållaren och inte objekt i den.</span><span class="sxs-lookup"><span data-stu-id="749b1-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="749b1-143">Kopiera hela innehållet i en mapp genom att inkludera den **Recurse** parameter för den **Copy-Item** cmdlet i kommandot.</span><span class="sxs-lookup"><span data-stu-id="749b1-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="749b1-144">Om du redan har kopierat katalogen utan innehållet kan lägga till den **kraft** parameter, där du kan skriva över den tomma mappen.</span><span class="sxs-lookup"><span data-stu-id="749b1-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a><span data-ttu-id="749b1-145">Ta bort objekt (ta bort objekt)</span><span class="sxs-lookup"><span data-stu-id="749b1-145">Deleting Items (Remove-Item)</span></span>
<span data-ttu-id="749b1-146">Ta bort filer och mappar genom att använda den **ta bort objektet** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="749b1-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="749b1-147">Windows PowerShell-cmdlets som **ta bort objektet**, som kan göra betydande, ångra ändringar ofta ombeds du att bekräfta när du anger dess kommandon.</span><span class="sxs-lookup"><span data-stu-id="749b1-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="749b1-148">Till exempel om du försöker ta bort den **New.Directory** mappen, du uppmanas att bekräfta kommandot, eftersom den innehåller filer:</span><span class="sxs-lookup"><span data-stu-id="749b1-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="749b1-149">Eftersom **Ja** är svaret som standard, ta bort mappen och dess filer, tryck på den **RETUR** nyckel.</span><span class="sxs-lookup"><span data-stu-id="749b1-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="749b1-150">Ta bort mappen utan att bekräfta den **-Recurse** parameter.</span><span class="sxs-lookup"><span data-stu-id="749b1-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a><span data-ttu-id="749b1-151">Köra objekt (anropa-objekt)</span><span class="sxs-lookup"><span data-stu-id="749b1-151">Executing Items (Invoke-Item)</span></span>
<span data-ttu-id="749b1-152">Windows PowerShell använder den **Invoke-objektet** för att utföra en standardåtgärd för en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="749b1-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="749b1-153">Den här standardåtgärd bestäms av standardprogram för programmet i registret. effekten är densamma som om du dubbelklickar på objektet i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="749b1-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="749b1-154">Anta att du kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="749b1-154">For example, suppose you run the following command:</span></span>

```
PS> Invoke-Item C:\WINDOWS
```

<span data-ttu-id="749b1-155">Ett Explorer-fönster som finns i C:\\Windows visas precis som om du hade dubbelklickar på enhet C:\\Windows-mappen.</span><span class="sxs-lookup"><span data-stu-id="749b1-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="749b1-156">Om du anropar den **Boot.ini** filen i ett system tidigare än Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="749b1-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```
PS> Invoke-Item C:\boot.ini
```

<span data-ttu-id="749b1-157">Om typen ini-filen är associerad med anteckningar öppnas boot.ini-filen i anteckningar.</span><span class="sxs-lookup"><span data-stu-id="749b1-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>

