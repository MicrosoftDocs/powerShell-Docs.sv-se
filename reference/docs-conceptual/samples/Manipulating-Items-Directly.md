---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Manipulera objekt direkt
description: PowerShell innehåller flera cmdlets som hjälper dig att hantera objekt på lokala och fjärranslutna datorer. Objekt är objekt som exponeras av PowerShell-leverantörer som fil system, register, certifikat och andra.
ms.openlocfilehash: 20132b63a8ff4ef24b1d8346066315dbb053e59c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500325"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="78ab2-105">Manipulera objekt direkt</span><span class="sxs-lookup"><span data-stu-id="78ab2-105">Manipulating Items Directly</span></span>

<span data-ttu-id="78ab2-106">De element som visas i Windows PowerShell-enheter, till exempel filerna och mapparna i fil system enheterna och register nycklarna i Windows PowerShell-registernycklarna, kallas *objekt* i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78ab2-106">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="78ab2-107">Cmdletarna för att arbeta med dem har **elementet Substantiv i** sina namn.</span><span class="sxs-lookup"><span data-stu-id="78ab2-107">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="78ab2-108">Utdata från kommandot **Get-Command-Substantiv objekt** visar att det finns nio objekt-cmdletar för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78ab2-108">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

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

## <a name="creating-new-items-new-item"></a><span data-ttu-id="78ab2-109">Skapa nya objekt (nytt objekt)</span><span class="sxs-lookup"><span data-stu-id="78ab2-109">Creating New Items (New-Item)</span></span>

<span data-ttu-id="78ab2-110">Om du vill skapa ett nytt objekt i fil systemet använder du cmdleten **New-item** .</span><span class="sxs-lookup"><span data-stu-id="78ab2-110">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="78ab2-111">Inkludera parametern **Path** med sökvägen till objektet och parametern **itemType** med värdet "File" eller "Directory".</span><span class="sxs-lookup"><span data-stu-id="78ab2-111">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="78ab2-112">Om du till exempel vill skapa en ny katalog med namnet "New. Directory" i katalogen C: \\ temp, skriver du:</span><span class="sxs-lookup"><span data-stu-id="78ab2-112">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="78ab2-113">Om du vill skapa en fil ändrar du värdet för parametern **itemType** till "File".</span><span class="sxs-lookup"><span data-stu-id="78ab2-113">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="78ab2-114">Om du till exempel vill skapa en fil med namnet "file1.txt" i katalogen New. Directory skriver du:</span><span class="sxs-lookup"><span data-stu-id="78ab2-114">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="78ab2-115">Du kan använda samma metod för att skapa en ny register nyckel.</span><span class="sxs-lookup"><span data-stu-id="78ab2-115">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="78ab2-116">I själva verket är det enklare att skapa en register nyckel eftersom den enda objekt typen i Windows-registret är en nyckel.</span><span class="sxs-lookup"><span data-stu-id="78ab2-116">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="78ab2-117">(Register poster är objekt *Egenskaper*.) Om du till exempel vill skapa en nyckel med namnet "_Test" i CurrentVersion-undernyckeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="78ab2-117">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="78ab2-118">När du skriver en register Sök väg ska du se till att inkludera kolon (**:**) i Windows PowerShell-enhetens namn, HKLM: och HKCU:.</span><span class="sxs-lookup"><span data-stu-id="78ab2-118">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="78ab2-119">Utan kolonet känner Windows PowerShell inte igen enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="78ab2-119">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="78ab2-120">Varför register värden inte är objekt</span><span class="sxs-lookup"><span data-stu-id="78ab2-120">Why Registry Values are not Items</span></span>

<span data-ttu-id="78ab2-121">När du använder cmdleten **Get-ChildItem** för att hitta objekten i en register nyckel, ser du aldrig faktiska register poster eller deras värden.</span><span class="sxs-lookup"><span data-stu-id="78ab2-121">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="78ab2-122">Till exempel innehåller register nyckeln **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ Windows CurrentVersion- \\ \\ körningen** vanligt vis flera register poster som representerar program som körs när systemet startar.</span><span class="sxs-lookup"><span data-stu-id="78ab2-122">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="78ab2-123">Men när du använder **Get-ChildItem** för att leta efter underordnade objekt i nyckeln ser du att det finns en **OptionalComponents** -under nyckel i nyckeln:</span><span class="sxs-lookup"><span data-stu-id="78ab2-123">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="78ab2-124">Även om det skulle vara praktiskt att behandla register poster som objekt kan du inte ange en sökväg till en register post på ett sätt som garanterar att det är unikt.</span><span class="sxs-lookup"><span data-stu-id="78ab2-124">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="78ab2-125">Sök vägs notationen skiljer sig inte mellan register under nyckeln med namnet **Run** och register posten **(default)** i **körnings** under nyckeln.</span><span class="sxs-lookup"><span data-stu-id="78ab2-125">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="78ab2-126">Dessutom, eftersom register post namn kan innehålla omvänt snedstreck ( **\\** ), om register poster var objekt, kunde du inte använda Sök vägs notation för att skilja en register post med namnet **Windows \\ CurrentVersion att \\ köras** från under nyckeln som finns i den sökvägen.</span><span class="sxs-lookup"><span data-stu-id="78ab2-126">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="78ab2-127">Byta namn på befintliga objekt (Byt namn på objekt)</span><span class="sxs-lookup"><span data-stu-id="78ab2-127">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="78ab2-128">Om du vill ändra namnet på en fil eller mapp använder du cmdleten **rename-item** .</span><span class="sxs-lookup"><span data-stu-id="78ab2-128">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="78ab2-129">Följande kommando ändrar namnet på den **file1.txt** -fil som ska **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="78ab2-129">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="78ab2-130">Cmdleten **rename-item** kan ändra namnet på en fil eller mapp, men det går inte att flytta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="78ab2-130">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="78ab2-131">Följande kommando Miss lyckas eftersom det försöker flytta filen från den nya katalog katalogen till Temp-katalogen.</span><span class="sxs-lookup"><span data-stu-id="78ab2-131">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="78ab2-132">Flytta objekt (flytta objekt)</span><span class="sxs-lookup"><span data-stu-id="78ab2-132">Moving Items (Move-Item)</span></span>

<span data-ttu-id="78ab2-133">Om du vill flytta en fil eller mapp använder du cmdleten **Move-item** .</span><span class="sxs-lookup"><span data-stu-id="78ab2-133">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="78ab2-134">Följande kommando flyttar till exempel den nya katalog katalogen från katalogen C: \\ Temp till roten på enheten c:.</span><span class="sxs-lookup"><span data-stu-id="78ab2-134">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="78ab2-135">För att verifiera att objektet har flyttats inkluderar du parametern **Passthru** i cmdleten **Move-item** .</span><span class="sxs-lookup"><span data-stu-id="78ab2-135">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="78ab2-136">Utan **Passthru**visar cmdleten **Move-item** inga resultat.</span><span class="sxs-lookup"><span data-stu-id="78ab2-136">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="78ab2-137">Kopiera objekt (kopiera objekt)</span><span class="sxs-lookup"><span data-stu-id="78ab2-137">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="78ab2-138">Om du är bekant med kopierings åtgärderna i andra gränssnitt kan du vara ovanlig om du märker att cmdleten **copy-item** i Windows PowerShell fungerar som den ska.</span><span class="sxs-lookup"><span data-stu-id="78ab2-138">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="78ab2-139">När du kopierar ett objekt från en plats till en annan kopierar Copy-Item inte innehållet som standard.</span><span class="sxs-lookup"><span data-stu-id="78ab2-139">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="78ab2-140">Om du till exempel kopierar den **nya katalog** katalogen från c:-enheten till katalogen c: \\ temp, lyckas kommandot, men filerna i katalogen New. Directory kopieras inte.</span><span class="sxs-lookup"><span data-stu-id="78ab2-140">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="78ab2-141">Om du visar innehållet i **C: \\ Temp \\ New. Directory**, kommer du att se att den inte innehåller några filer:</span><span class="sxs-lookup"><span data-stu-id="78ab2-141">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="78ab2-142">Varför kopierar inte cmdleten **copy-item** innehållet till den nya platsen?</span><span class="sxs-lookup"><span data-stu-id="78ab2-142">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="78ab2-143">Cmdleten **copy-item** har utformats för att vara generisk; Det är inte bara att kopiera filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="78ab2-143">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="78ab2-144">Även när du kopierar filer och mappar kanske du vill kopiera endast behållaren och inte objekten i den.</span><span class="sxs-lookup"><span data-stu-id="78ab2-144">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="78ab2-145">Om du vill kopiera hela innehållet i en mapp inkluderar du parametern **rekursivt** i cmdleten **copy-item** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="78ab2-145">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="78ab2-146">Om du redan har kopierat katalogen utan innehållet lägger du till parametern **Force** , så att du kan skriva över den tomma mappen.</span><span class="sxs-lookup"><span data-stu-id="78ab2-146">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

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

## <a name="deleting-items-remove-item"></a><span data-ttu-id="78ab2-147">Ta bort objekt (Remove-item)</span><span class="sxs-lookup"><span data-stu-id="78ab2-147">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="78ab2-148">Använd cmdleten **Remove-item** om du vill ta bort filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="78ab2-148">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="78ab2-149">Windows PowerShell-cmdletar, t. ex. **Remove-item**, som kan göra betydande, bestående ändringar kommer ofta att uppmanas att bekräfta när du anger dess kommandon.</span><span class="sxs-lookup"><span data-stu-id="78ab2-149">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="78ab2-150">Om du till exempel försöker ta bort den **nya.** mappen, uppmanas du att bekräfta kommandot, eftersom mappen innehåller filer:</span><span class="sxs-lookup"><span data-stu-id="78ab2-150">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="78ab2-151">Eftersom **Ja** är standard svaret tar du bort mappen och dess filer genom att trycka på **RETUR** .</span><span class="sxs-lookup"><span data-stu-id="78ab2-151">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="78ab2-152">Om du vill ta bort mappen utan att bekräfta, använder du parametern **-rekursivt** .</span><span class="sxs-lookup"><span data-stu-id="78ab2-152">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="78ab2-153">Köra objekt (Invoke-item)</span><span class="sxs-lookup"><span data-stu-id="78ab2-153">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="78ab2-154">Windows PowerShell använder cmdleten **Invoke-item** för att utföra en standard åtgärd för en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="78ab2-154">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="78ab2-155">Den här standard åtgärden bestäms av standard program hanteraren i registret. Resultatet är detsamma som om du dubbelklickar på objektet i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="78ab2-155">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="78ab2-156">Anta till exempel att du kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="78ab2-156">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="78ab2-157">Ett Explorer-fönster som finns i C: \\ Windows visas, precis som om du hade dubbelklickat på mappen C: \\ Windows.</span><span class="sxs-lookup"><span data-stu-id="78ab2-157">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="78ab2-158">Om du anropar **Boot.ini** -filen på ett system före Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="78ab2-158">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="78ab2-159">Om fil typen. ini är associerad med anteckningar öppnas boot.ini-filen i anteckningar.</span><span class="sxs-lookup"><span data-stu-id="78ab2-159">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
