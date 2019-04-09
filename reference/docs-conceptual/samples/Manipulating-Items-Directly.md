---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Manipulera objekt direkt
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293273"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="2b543-103">Manipulera objekt direkt</span><span class="sxs-lookup"><span data-stu-id="2b543-103">Manipulating Items Directly</span></span>

<span data-ttu-id="2b543-104">De element som du ser i Windows PowerShell-enheter, till exempel filer och mappar i filen systemenheter och registernycklar i Windows PowerShell registret enheter, kallas *objekt* i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b543-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="2b543-105">Cmdletar för att arbeta med dem objekt har substantivet **objekt** i sina namn.</span><span class="sxs-lookup"><span data-stu-id="2b543-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="2b543-106">Utdata från den **Get-Command - substantiv objekt** kommandot visar att det finns nio artikel-cmdletar för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b543-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

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

## <a name="creating-new-items-new-item"></a><span data-ttu-id="2b543-107">Skapa nya objekt (nya objekt)</span><span class="sxs-lookup"><span data-stu-id="2b543-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="2b543-108">Om du vill skapa ett nytt objekt i filsystemet, Använd den **New-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b543-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="2b543-109">Inkludera den **sökväg** parameter med sökvägen till objektet och **ItemType** parametern med värdet ”fil” eller ”directory”.</span><span class="sxs-lookup"><span data-stu-id="2b543-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="2b543-110">Till exempel vill skapa en ny katalog med namnet ”New.Directory"in enhet C:\\Temp-katalog, skriver du in:</span><span class="sxs-lookup"><span data-stu-id="2b543-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="2b543-111">Skapa en fil genom att ändra värdet för den **ItemType** parameter ”fil”.</span><span class="sxs-lookup"><span data-stu-id="2b543-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="2b543-112">Till exempel för att skapa en fil med namnet ”file1.txt” i katalogen New.Directory, skriver du:</span><span class="sxs-lookup"><span data-stu-id="2b543-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="2b543-113">Du kan använda samma metod för att skapa en ny registernyckel.</span><span class="sxs-lookup"><span data-stu-id="2b543-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="2b543-114">I själva verket är det enklare att skapa eftersom endast objekttypen i Windows-registret är en nyckel med en registernyckel.</span><span class="sxs-lookup"><span data-stu-id="2b543-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="2b543-115">(Registerposter är objektet *egenskaper*.) Till exempel för att skapa en nyckel med namnet ”_testa” i undernyckeln CurrentVersion, skriver du:</span><span class="sxs-lookup"><span data-stu-id="2b543-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="2b543-116">När du skriver en registersökväg, måste du använda kolumnen (**:**) i Windows PowerShell enhet namn, HKLM: och HKCU:.</span><span class="sxs-lookup"><span data-stu-id="2b543-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="2b543-117">Utan kolumnen identifieras Windows PowerShell inte enhetsbeteckning i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="2b543-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="2b543-118">Varför registervärden finns inga objekt</span><span class="sxs-lookup"><span data-stu-id="2b543-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="2b543-119">När du använder den **Get-ChildItem** cmdlet för att hitta objekt i en registernyckel visas aldrig faktiska registerposterna eller deras värden.</span><span class="sxs-lookup"><span data-stu-id="2b543-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="2b543-120">Till exempel registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion\\kör** innehåller vanligtvis flera registerposter som representerar program som körs när datorn startas.</span><span class="sxs-lookup"><span data-stu-id="2b543-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="2b543-121">Men när du använder **Get-ChildItem** för att leta efter underordnade objekt i nyckeln, visas bara den **OptionalComponents** undernycklar för nyckeln:</span><span class="sxs-lookup"><span data-stu-id="2b543-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="2b543-122">Även om det skulle vara praktiskt att behandla registerposter som objekt, kan du inte ange en sökväg till en registerpost på ett sätt som säkerställer att det blir unikt.</span><span class="sxs-lookup"><span data-stu-id="2b543-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="2b543-123">Sökvägen notation skiljer inte mellan registerundernyckeln med namnet **kör** och **(standard)** registerposten i den **kör** undernyckel.</span><span class="sxs-lookup"><span data-stu-id="2b543-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="2b543-124">Dessutom eftersom registernamn posten kan innehålla ett omvänt snedstreck (**\\**), om registerposter objekt, så du inte kan använda beteckningen sökväg att skilja mellan en registerpost med namnet  **Windows\\CurrentVersion\\kör** från undernyckeln som finns i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="2b543-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="2b543-125">Byta namn på befintliga objekt (Byt namn på objekt)</span><span class="sxs-lookup"><span data-stu-id="2b543-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="2b543-126">Du kan ändra namnet på en fil eller mapp med det **Rename-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b543-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="2b543-127">Följande kommando byter namn på den **file1.txt** filen till **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="2b543-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="2b543-128">Den **Rename-Item** cmdlet kan ändra namnet på en fil eller mapp, men det går inte att flytta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="2b543-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="2b543-129">Följande kommando misslyckas eftersom den försöker flytta filen från katalogen New.Directory till Temp-katalog.</span><span class="sxs-lookup"><span data-stu-id="2b543-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="2b543-130">Flytta objekt (flytta objekt)</span><span class="sxs-lookup"><span data-stu-id="2b543-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="2b543-131">Om du vill flytta en fil eller mapp, använda den **flytta objekt** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b543-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="2b543-132">Till exempel följande kommando flyttas katalogen New.Directory från enhet C:\\temp-katalogen i roten på enhet C:.</span><span class="sxs-lookup"><span data-stu-id="2b543-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="2b543-133">Om du vill kontrollera att objektet har flyttats, innehåller den **PassThru** -parametern för den **flytta objekt** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b543-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="2b543-134">Utan **Passthru**, **flytta objekt** cmdlet visar inte några resultat.</span><span class="sxs-lookup"><span data-stu-id="2b543-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="2b543-135">Kopiera objekt (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="2b543-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="2b543-136">Om du är bekant med kopieringsåtgärder i andra gränssnitt, kanske du upptäcker beteendet för den **Copy-Item** cmdlet i Windows PowerShell är ovanliga.</span><span class="sxs-lookup"><span data-stu-id="2b543-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="2b543-137">När du kopierar ett objekt från en plats till en annan, kopierar inte Copy-Item innehållet som standard.</span><span class="sxs-lookup"><span data-stu-id="2b543-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="2b543-138">Exempel: Om du kopierar den **New.Directory** katalogen från C:-enheten till enhet C:\\temp-katalog, kommandot lyckas men kopieras inte filerna i katalogen New.Directory.</span><span class="sxs-lookup"><span data-stu-id="2b543-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="2b543-139">Om du visar innehållet i **C:\\temp\\New.Directory**, hittar du att den innehåller inga filer:</span><span class="sxs-lookup"><span data-stu-id="2b543-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="2b543-140">Varför inte den **Copy-Item** cmdlet kopiera innehållet till den nya platsen?</span><span class="sxs-lookup"><span data-stu-id="2b543-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="2b543-141">Den **Copy-Item** cmdlet har utformats för att vara Allmänt, och inte bara för att kopiera filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="2b543-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="2b543-142">Även om kopiering av filer och mappar, kanske du vill kopiera endast för behållaren och inte objekt i den.</span><span class="sxs-lookup"><span data-stu-id="2b543-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="2b543-143">Kopiera hela innehållet i en mapp genom att inkludera den **Recurse** -parametern för den **Copy-Item** cmdlet i kommandot.</span><span class="sxs-lookup"><span data-stu-id="2b543-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="2b543-144">Om du redan har kopierat katalogen utan dess innehåll kan du lägga till den **kraft** parametern, som du kan skriva över den tomma mappen.</span><span class="sxs-lookup"><span data-stu-id="2b543-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

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

## <a name="deleting-items-remove-item"></a><span data-ttu-id="2b543-145">Ta bort objekt (ta bort objekt)</span><span class="sxs-lookup"><span data-stu-id="2b543-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="2b543-146">Ta bort filer och mappar genom att använda den **Remove-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b543-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="2b543-147">Windows PowerShell-cmdletar, till exempel **Remove-Item**, som kan göra betydande, går inte att ångra ändringar ofta efterfrågar bekräftelse när du anger kommandona.</span><span class="sxs-lookup"><span data-stu-id="2b543-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="2b543-148">Exempel: Om du försöker ta bort den **New.Directory** mappen du uppmanas att bekräfta kommandot, eftersom mappen innehåller filer:</span><span class="sxs-lookup"><span data-stu-id="2b543-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="2b543-149">Eftersom **Ja** är Standardsvar att ta bort mappen och dess filer, tryck på den **RETUR** nyckel.</span><span class="sxs-lookup"><span data-stu-id="2b543-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="2b543-150">Ta bort mappen utan att bekräfta att använda den **-Recurse** parametern.</span><span class="sxs-lookup"><span data-stu-id="2b543-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="2b543-151">Körning av objekt (anropa-objekt)</span><span class="sxs-lookup"><span data-stu-id="2b543-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="2b543-152">Windows PowerShell använder den **Invoke-Item** cmdlet för att utföra en standardåtgärd för en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="2b543-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="2b543-153">Den här standardåtgärd bestäms av Programhanteraren standard i registret. effekten är samma som om du dubbelklickar på objektet i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="2b543-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="2b543-154">Anta exempelvis att du kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="2b543-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="2b543-155">Ett Explorer-fönster som finns i C:\\Windows visas, precis som om du hade dubbelklickade på enhet C:\\Windows-mappen.</span><span class="sxs-lookup"><span data-stu-id="2b543-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="2b543-156">Om du anropar den **Boot.ini** filen i ett system innan Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="2b543-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="2b543-157">Om typen ini-filen är associerad med anteckningar, öppnas boot.ini-filen i anteckningar.</span><span class="sxs-lookup"><span data-stu-id="2b543-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
