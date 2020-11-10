---
description: Filsystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem-Provider
ms.openlocfilehash: 204a90dc346e6d4ff483777b9adf7a70017ef093
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386938"
---
# <a name="filesystem-provider"></a><span data-ttu-id="a7204-104">FileSystem-Provider</span><span class="sxs-lookup"><span data-stu-id="a7204-104">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="a7204-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="a7204-105">Provider name</span></span>

<span data-ttu-id="a7204-106">Filsystem</span><span class="sxs-lookup"><span data-stu-id="a7204-106">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="a7204-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="a7204-107">Drives</span></span>

<span data-ttu-id="a7204-108">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="a7204-108">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="a7204-109">Funktioner</span><span class="sxs-lookup"><span data-stu-id="a7204-109">Capabilities</span></span>

<span data-ttu-id="a7204-110">**Filter** , **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="a7204-110">**Filter** , **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="a7204-111">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a7204-111">Short description</span></span>

<span data-ttu-id="a7204-112">Ger åtkomst till filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="a7204-112">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="a7204-113">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="a7204-113">Detailed description</span></span>

<span data-ttu-id="a7204-114">Med PowerShell- **dataprovidern** kan du hämta, lägga till, ändra, rensa och ta bort filer och kataloger i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7204-114">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="a7204-115">**Fil Systems** enheter är ett hierarkiskt namn område som innehåller de kataloger och filer som finns på din dator.</span><span class="sxs-lookup"><span data-stu-id="a7204-115">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="a7204-116">En **fil Systems** enhet kan vara en logisk eller phsyical enhet, katalog eller mappad nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="a7204-116">A **FileSystem** drive can be a logical or phsyical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="a7204-117">**Fil Systems** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="a7204-117">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="a7204-118">Get-location</span><span class="sxs-lookup"><span data-stu-id="a7204-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="a7204-119">Ange plats</span><span class="sxs-lookup"><span data-stu-id="a7204-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="a7204-120">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="a7204-121">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="a7204-122">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="a7204-123">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="a7204-124">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="a7204-125">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="a7204-126">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a7204-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="a7204-127">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a7204-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="a7204-128">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-128">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="a7204-129">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a7204-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="a7204-130">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-130">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="a7204-131">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a7204-131">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="a7204-132">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="a7204-132">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="a7204-133">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="a7204-133">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="a7204-134">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a7204-134">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="a7204-135">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a7204-135">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="a7204-136">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="a7204-136">Types exposed by this provider</span></span>

<span data-ttu-id="a7204-137">Filerna är instanser av klassen [system. io. fileinfo](/dotnet/api/system.io.fileinfo) .</span><span class="sxs-lookup"><span data-stu-id="a7204-137">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span>  <span data-ttu-id="a7204-138">Kataloger är instanser av klassen [system. io. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .</span><span class="sxs-lookup"><span data-stu-id="a7204-138">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="a7204-139">Navigera i fil Systems enheter</span><span class="sxs-lookup"><span data-stu-id="a7204-139">Navigating the FileSystem drives</span></span>

<span data-ttu-id="a7204-140">**Fil Systems** leverantören visar sina data lager genom att mappa alla logiska enheter på datorn som PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="a7204-140">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="a7204-141">Om du vill arbeta med en **fil Systems** enhet kan du ändra din plats till en enhet utfärdande enhets namnet följt av ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="a7204-141">To work with a **FileSystem** drive you can change your location to a drive uing the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="a7204-142">Du kan också arbeta med **fil Systems** leverantören från någon annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="a7204-142">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="a7204-143">Om du vill referera till en fil eller katalog från en annan plats använder du enhets namnet ( `C:` ,... `D:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a7204-143">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="a7204-144">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="a7204-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="a7204-145">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="a7204-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="a7204-146">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="a7204-146">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="a7204-147">Hämta filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="a7204-147">Getting files and directories</span></span>

<span data-ttu-id="a7204-148">`Get-ChildItem`Cmdleten returnerar alla filer och kataloger på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="a7204-148">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="a7204-149">Du kan ange en annan sökväg för att söka efter och använda inbyggda parametrar för att filtrera och styra rekursion-djupet.</span><span class="sxs-lookup"><span data-stu-id="a7204-149">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="a7204-150">Läs mer om cmdlet-användning i [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span><span class="sxs-lookup"><span data-stu-id="a7204-150">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="a7204-151">Kopiera filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="a7204-151">Copying files and directories</span></span>

<span data-ttu-id="a7204-152">`Copy-Item`Cmdleten kopierar filer och kataloger till en plats som du anger.</span><span class="sxs-lookup"><span data-stu-id="a7204-152">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="a7204-153">Parametrar är tillgängliga för att filtrera och rekursivt, ungefär som `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="a7204-153">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="a7204-154">Följande kommando kopierar alla filer och kataloger under sökvägen "C:\Temp" \" till mappen "C:\Windows\Temp".</span><span class="sxs-lookup"><span data-stu-id="a7204-154">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="a7204-155">`Copy-Item` skriver över filer i mål katalogen utan att uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="a7204-155">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="a7204-156">Det här kommandot kopierar `a.txt` filen från `C:\a` katalogen till `C:\a\bb` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a7204-156">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="a7204-157">Kopierar alla kataloger och filer i `C:\a` katalogen till `C:\c` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a7204-157">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="a7204-158">Om någon av de kataloger som ska kopieras redan finns i mål katalogen, kommer kommandot att Miss kopie ras om du inte anger en Force-parameter.</span><span class="sxs-lookup"><span data-stu-id="a7204-158">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="a7204-159">Mer information finns i [Kopiera objekt](xref:Microsoft.PowerShell.Management.Copy-Item).</span><span class="sxs-lookup"><span data-stu-id="a7204-159">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="a7204-160">Flytta filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="a7204-160">Moving files and directories</span></span>

<span data-ttu-id="a7204-161">Det här kommandot flyttar `c.txt` filen i `C:\a` katalogen till `C:\a\aa` katalogen:</span><span class="sxs-lookup"><span data-stu-id="a7204-161">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="a7204-162">Kommandot kommer inte att skriva över en befintlig fil som har samma namn automatiskt.</span><span class="sxs-lookup"><span data-stu-id="a7204-162">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="a7204-163">Om du vill tvinga cmdleten att skriva över en befintlig fil anger du parametern Force.</span><span class="sxs-lookup"><span data-stu-id="a7204-163">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="a7204-164">Du kan inte flytta en katalog när katalogen är den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="a7204-164">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="a7204-165">När du använder `Move-Item` för att flytta katalogen på den aktuella platsen visas det här felet.</span><span class="sxs-lookup"><span data-stu-id="a7204-165">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="a7204-166">Hantera fil innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-166">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="a7204-167">Hämta innehållet i en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-167">Get the content of a file</span></span>

<span data-ttu-id="a7204-168">Det här kommandot hämtar innehållet i filen "Test.txt" och visar dem i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="a7204-168">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="a7204-169">Du kan skicka vidare innehållet i filen till en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7204-169">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="a7204-170">Följande kommando läser till exempel innehållet i `Test.txt` filen och skickar dem som indata till [ConvertTo-HTML-](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdleten:</span><span class="sxs-lookup"><span data-stu-id="a7204-170">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="a7204-171">Du kan också hämta innehållet i en fil genom att förkorrigera dess Provider-sökväg med dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="a7204-171">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="a7204-172">Sökvägen måste stå inom klammerparenteser på grund av variabla namngivnings begränsningar.</span><span class="sxs-lookup"><span data-stu-id="a7204-172">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="a7204-173">Mer information finns i [about_Variables](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="a7204-173">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="a7204-174">Lägga till innehåll i en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-174">Add content to a file</span></span>

<span data-ttu-id="a7204-175">Detta kommando lägger till strängen "testa innehåll" till `Test.txt` filen:</span><span class="sxs-lookup"><span data-stu-id="a7204-175">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="a7204-176">Det befintliga innehållet i `Test.txt` filen tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="a7204-176">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="a7204-177">Ersätt innehållet i en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-177">Replace the content of a file</span></span>

<span data-ttu-id="a7204-178">Det här kommandot ersätter `Test.txt` filens innehåll med strängen "test content":</span><span class="sxs-lookup"><span data-stu-id="a7204-178">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="a7204-179">Innehållet i skrivs över `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="a7204-179">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="a7204-180">Du kan använda **Value** -parametern för cmdleten [New-item](xref:Microsoft.PowerShell.Management.New-Item) för att lägga till innehåll i en fil när du skapar den.</span><span class="sxs-lookup"><span data-stu-id="a7204-180">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="a7204-181">Loopa igenom innehållet i en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-181">Loop through the contents of a file</span></span>

<span data-ttu-id="a7204-182">Som standard `Get-Content` använder cmdleten rad slutet som avgränsare, så den hämtar en fil som en samling strängar, med varje rad som en sträng i filen.</span><span class="sxs-lookup"><span data-stu-id="a7204-182">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="a7204-183">Du kan använda `-Delimiter` parametern för att ange en alternativ avgränsare.</span><span class="sxs-lookup"><span data-stu-id="a7204-183">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="a7204-184">Om du ställer in det på tecknen som anger slutet på ett avsnitt eller början av nästa avsnitt, kan du dela upp filen i logiska delar.</span><span class="sxs-lookup"><span data-stu-id="a7204-184">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="a7204-185">Det första kommandot hämtar `Employees.txt` filen och delar den i avsnitt, som var och en slutar med orden "slutet av medarbetar posten" och sparar den i `$e` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a7204-185">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="a7204-186">Det andra kommandot använder mat ris notation för att hämta det första objektet i samlingen i `$e` .</span><span class="sxs-lookup"><span data-stu-id="a7204-186">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="a7204-187">Det använder ett index på 0, eftersom PowerShell-matriser är noll-baserade.</span><span class="sxs-lookup"><span data-stu-id="a7204-187">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="a7204-188">Mer information om `Get-Content` cmdlet finns i hjälp avsnittet för [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span><span class="sxs-lookup"><span data-stu-id="a7204-188">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="a7204-189">Mer information om matriser finns [about_Arrays](../About/about_Arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a7204-189">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="a7204-190">Hantera säkerhets beskrivningar</span><span class="sxs-lookup"><span data-stu-id="a7204-190">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="a7204-191">Visa ACL för en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-191">View the ACL for a file</span></span>

<span data-ttu-id="a7204-192">Det här kommandot returnerar ett [system. Security. AccessControl. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -objekt:</span><span class="sxs-lookup"><span data-stu-id="a7204-192">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="a7204-193">Om du vill ha mer information om det här objektet, rör du kommandot till cmdleten [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) .</span><span class="sxs-lookup"><span data-stu-id="a7204-193">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="a7204-194">Eller, se [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -klass.</span><span class="sxs-lookup"><span data-stu-id="a7204-194">Or, see [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="a7204-195">Ändra ACL för en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-195">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="a7204-196">Skapa och ange en ACL för en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-196">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="a7204-197">Skapa filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="a7204-197">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="a7204-198">Skapa en katalog</span><span class="sxs-lookup"><span data-stu-id="a7204-198">Create a directory</span></span>

<span data-ttu-id="a7204-199">Det här kommandot skapar `logfiles` katalogen på `C` enheten:</span><span class="sxs-lookup"><span data-stu-id="a7204-199">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="a7204-200">PowerShell innehåller också en `mkdir` funktion (alias `md` ) som använder cmdleten [New-item](xref:Microsoft.PowerShell.Management.New-Item) för att skapa en ny katalog.</span><span class="sxs-lookup"><span data-stu-id="a7204-200">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="a7204-201">Skapa en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-201">Create a file</span></span>

<span data-ttu-id="a7204-202">Det här kommandot skapar `log2.txt` filen i `C:\logfiles` katalogen och lägger sedan till strängen "testa logg" i filen:</span><span class="sxs-lookup"><span data-stu-id="a7204-202">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="a7204-203">Skapa en fil med innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-203">Create a file with content</span></span>

<span data-ttu-id="a7204-204">Skapar en fil som kallas `log2.txt` i `C:\logfiles` katalogen och lägger till strängen "test loggen" i filen.</span><span class="sxs-lookup"><span data-stu-id="a7204-204">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="a7204-205">Byta namn på filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="a7204-205">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="a7204-206">Byt namn på en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-206">Rename a file</span></span>

<span data-ttu-id="a7204-207">Det här kommandot byter namn på `a.txt` filen i `C:\a` katalogen till `b.txt` :</span><span class="sxs-lookup"><span data-stu-id="a7204-207">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="a7204-208">Byta namn på en katalog</span><span class="sxs-lookup"><span data-stu-id="a7204-208">Rename a directory</span></span>

<span data-ttu-id="a7204-209">Det här kommandot byter namn på `C:\a\cc` katalogen till `C:\a\dd` :</span><span class="sxs-lookup"><span data-stu-id="a7204-209">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="a7204-210">Ta bort filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="a7204-210">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="a7204-211">Ta bort en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-211">Delete a file</span></span>

<span data-ttu-id="a7204-212">Det här kommandot tar bort `Test.txt` filen i den aktuella katalogen:</span><span class="sxs-lookup"><span data-stu-id="a7204-212">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="a7204-213">Ta bort filer med jokertecken</span><span class="sxs-lookup"><span data-stu-id="a7204-213">Delete files using wildcards</span></span>

<span data-ttu-id="a7204-214">Det här kommandot tar bort alla filer i den aktuella katalogen som har `.xml` fil namns tillägget:</span><span class="sxs-lookup"><span data-stu-id="a7204-214">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="a7204-215">Starta ett program genom att anropa en associerad fil</span><span class="sxs-lookup"><span data-stu-id="a7204-215">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="a7204-216">Anropa en fil</span><span class="sxs-lookup"><span data-stu-id="a7204-216">Invoke a file</span></span>

<span data-ttu-id="a7204-217">Det första kommandot använder cmdleten [Get-service](xref:Microsoft.PowerShell.Management.Get-Service) för att hämta information om lokala tjänster.</span><span class="sxs-lookup"><span data-stu-id="a7204-217">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="a7204-218">Den rör informationen till [export-csv-](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdleten och lagrar sedan informationen i `Services.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="a7204-218">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="a7204-219">Det andra kommandot använder [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item) för att öppna `services.csv` filen i programmet som är associerat med `.csv` tillägget:</span><span class="sxs-lookup"><span data-stu-id="a7204-219">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="a7204-220">Hämta filer och mappar med angivna attribut</span><span class="sxs-lookup"><span data-stu-id="a7204-220">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="a7204-221">Hämta systemfiler</span><span class="sxs-lookup"><span data-stu-id="a7204-221">Get System files</span></span>

<span data-ttu-id="a7204-222">Detta kommando hämtar systemfiler i den aktuella katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="a7204-222">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="a7204-223">`-File`Parametern används för att bara hämta filer (inte kataloger) och `-System` parametern för att bara hämta objekt med attributet "system".</span><span class="sxs-lookup"><span data-stu-id="a7204-223">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="a7204-224">Den använder `-Recurse` parametern för att hämta objekten i den aktuella katalogen och alla under kataloger.</span><span class="sxs-lookup"><span data-stu-id="a7204-224">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="a7204-225">Hämta dolda filer</span><span class="sxs-lookup"><span data-stu-id="a7204-225">Get Hidden files</span></span>

<span data-ttu-id="a7204-226">Det här kommandot hämtar alla filer, inklusive dolda filer, i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="a7204-226">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="a7204-227">Den använder parametern **attributes** med två värden, `!Directory+Hidden` , som hämtar dolda filer och `!Directory` , som hämtar alla andra filer.</span><span class="sxs-lookup"><span data-stu-id="a7204-227">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="a7204-228">`dir -att !d,!d+h` är motsvarigheten till det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="a7204-228">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="a7204-229">Hämta komprimerade och krypterade filer</span><span class="sxs-lookup"><span data-stu-id="a7204-229">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="a7204-230">Det här kommandot hämtar filer i den aktuella katalogen som är antingen komprimerade eller krypterade.</span><span class="sxs-lookup"><span data-stu-id="a7204-230">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="a7204-231">`-Attributes`Parametern med två värden används `Compressed` och `Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="a7204-231">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="a7204-232">Värdena avgränsas med ett kommatecken `,` som representerar operatorn "eller".</span><span class="sxs-lookup"><span data-stu-id="a7204-232">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="a7204-233">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="a7204-233">Dynamic parameters</span></span>

<span data-ttu-id="a7204-234">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="a7204-234">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="a7204-235">Inställning \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="a7204-235">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="a7204-236">Anger fil kodningen.</span><span class="sxs-lookup"><span data-stu-id="a7204-236">Specifies the file encoding.</span></span> <span data-ttu-id="a7204-237">Standardvärdet är ASCII.</span><span class="sxs-lookup"><span data-stu-id="a7204-237">The default is ASCII.</span></span>

- <span data-ttu-id="a7204-238">**ASCII** : använder kodningen för ASCII-teckenuppsättningen (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="a7204-238">**ASCII** :  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="a7204-239">**BigEndianUnicode** : kodar i UTF-16-format med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="a7204-239">**BigEndianUnicode** :  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="a7204-240">**Sträng** : använder kodnings typen för en sträng.</span><span class="sxs-lookup"><span data-stu-id="a7204-240">**String** :  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="a7204-241">**Unicode** : kodar i UTF-16-format med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="a7204-241">**Unicode** :  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="a7204-242">**UTF7** : kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="a7204-242">**UTF7** :   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="a7204-243">**Utf8** : kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="a7204-243">**UTF8** :  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="a7204-244">**UTF8BOM** : kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="a7204-244">**UTF8BOM** : Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="a7204-245">**UF8NOBOM** : kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="a7204-245">**UF8NOBOM** : Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="a7204-246">**UTF32** : kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="a7204-246">**UTF32** :  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="a7204-247">**Standard** : kodas på den installerade standard tecken tabellen.</span><span class="sxs-lookup"><span data-stu-id="a7204-247">**Default** : Encodes in the default installed code page.</span></span>
- <span data-ttu-id="a7204-248">**OEM** : använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="a7204-248">**OEM** : Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="a7204-249">**Okänd** : kodnings typen är okänd eller ogiltig.</span><span class="sxs-lookup"><span data-stu-id="a7204-249">**Unknown** :  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="a7204-250">Data kan behandlas som binära.</span><span class="sxs-lookup"><span data-stu-id="a7204-250">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-251">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-251">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-252">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-252">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="a7204-253">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-253">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="a7204-254">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-254">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="a7204-255">Avgränsare \<System.String\></span><span class="sxs-lookup"><span data-stu-id="a7204-255">Delimiter \<System.String\></span></span>

<span data-ttu-id="a7204-256">Anger den avgränsare som [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) använder för att dela upp filen i objekt när den läses.</span><span class="sxs-lookup"><span data-stu-id="a7204-256">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="a7204-257">Standardvärdet är `\n` rad slutet.</span><span class="sxs-lookup"><span data-stu-id="a7204-257">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="a7204-258">När du läser en textfil returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) en samling av sträng objekt, som var och en slutar med avgränsnings tecken.</span><span class="sxs-lookup"><span data-stu-id="a7204-258">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="a7204-259">Om du anger en avgränsare som inte finns i filen returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) hela filen som ett enskilt avgränsat objekt.</span><span class="sxs-lookup"><span data-stu-id="a7204-259">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="a7204-260">Du kan använda den här parametern för att dela upp en stor fil i mindre filer genom att ange en fil avgränsare, till exempel "slutet av exemplet", som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="a7204-260">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="a7204-261">Avgränsaren bevaras (tas inte bort) och blir det sista objektet i varje fil avsnitt.</span><span class="sxs-lookup"><span data-stu-id="a7204-261">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="a7204-262">När värdet för `-Delimiter` parametern är en tom sträng returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) inte något.</span><span class="sxs-lookup"><span data-stu-id="a7204-262">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="a7204-263">Detta är ett känt problem.</span><span class="sxs-lookup"><span data-stu-id="a7204-263">This is a known issue.</span></span> <span data-ttu-id="a7204-264">Om du vill tvinga [Get-innehåll](xref:Microsoft.PowerShell.Management.Get-Content) att returnera hela filen som en enskild, icke-avgränsad sträng anger du ett värde som inte finns i filen.</span><span class="sxs-lookup"><span data-stu-id="a7204-264">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-265">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-265">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-266">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-266">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="a7204-267">Vänta \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-267">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="a7204-268">Väntar på att innehåll ska läggas till i filen.</span><span class="sxs-lookup"><span data-stu-id="a7204-268">Waits for content to be appended to the file.</span></span> <span data-ttu-id="a7204-269">Om innehållet läggs till, returneras det tillagda innehållet.</span><span class="sxs-lookup"><span data-stu-id="a7204-269">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="a7204-270">Om innehållet har ändrats returnerar det hela filen.</span><span class="sxs-lookup"><span data-stu-id="a7204-270">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="a7204-271">När du väntar så kontrollerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) att filen är en gång i sekunden tills du avbryter den, till exempel genom att trycka på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="a7204-271">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-272">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-272">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-273">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-273">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="a7204-274">Dokumentattribut \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="a7204-274">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="a7204-275">Hämtar filer och mappar med de angivna attributen.</span><span class="sxs-lookup"><span data-stu-id="a7204-275">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="a7204-276">Den här parametern stöder alla attribut och gör att du kan ange komplexa kombinationer av attribut.</span><span class="sxs-lookup"><span data-stu-id="a7204-276">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="a7204-277">`-Attributes`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7204-277">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7204-278">`-Attributes`Parametern stöder följande attribut:</span><span class="sxs-lookup"><span data-stu-id="a7204-278">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="a7204-279">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="a7204-279">**Archive**</span></span>
- <span data-ttu-id="a7204-280">**Komprimerade**</span><span class="sxs-lookup"><span data-stu-id="a7204-280">**Compressed**</span></span>
- <span data-ttu-id="a7204-281">**Enhet**</span><span class="sxs-lookup"><span data-stu-id="a7204-281">**Device**</span></span>
- <span data-ttu-id="a7204-282">**Katalog**</span><span class="sxs-lookup"><span data-stu-id="a7204-282">**Directory**</span></span>
- <span data-ttu-id="a7204-283">**Krypterad**</span><span class="sxs-lookup"><span data-stu-id="a7204-283">**Encrypted**</span></span>
- <span data-ttu-id="a7204-284">**Dold**</span><span class="sxs-lookup"><span data-stu-id="a7204-284">**Hidden**</span></span>
- <span data-ttu-id="a7204-285">**Normal**</span><span class="sxs-lookup"><span data-stu-id="a7204-285">**Normal**</span></span>
- <span data-ttu-id="a7204-286">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="a7204-286">**NotContentIndexed**</span></span>
- <span data-ttu-id="a7204-287">**Offline**</span><span class="sxs-lookup"><span data-stu-id="a7204-287">**Offline**</span></span>
- <span data-ttu-id="a7204-288">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="a7204-288">**ReadOnly**</span></span>
- <span data-ttu-id="a7204-289">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="a7204-289">**ReparsePoint**</span></span>
- <span data-ttu-id="a7204-290">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="a7204-290">**SparseFile**</span></span>
- <span data-ttu-id="a7204-291">**System**</span><span class="sxs-lookup"><span data-stu-id="a7204-291">**System**</span></span>
- <span data-ttu-id="a7204-292">**Tillfälliga**</span><span class="sxs-lookup"><span data-stu-id="a7204-292">**Temporary**</span></span>

<span data-ttu-id="a7204-293">En beskrivning av dessa attribut finns i [FileAttributes](/dotnet/api/system.io.fileattributes) -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="a7204-293">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="a7204-294">Använd följande operatorer för att kombinera attribut.</span><span class="sxs-lookup"><span data-stu-id="a7204-294">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="a7204-295">`!` – INTE</span><span class="sxs-lookup"><span data-stu-id="a7204-295">`!` - NOT</span></span>
- <span data-ttu-id="a7204-296">`+` -OCH</span><span class="sxs-lookup"><span data-stu-id="a7204-296">`+` - AND</span></span>
- <span data-ttu-id="a7204-297">`,` -ELLER</span><span class="sxs-lookup"><span data-stu-id="a7204-297">`,` - OR</span></span>

<span data-ttu-id="a7204-298">Inga blank steg är tillåtna mellan en operator och dess attribut.</span><span class="sxs-lookup"><span data-stu-id="a7204-298">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="a7204-299">Blank steg tillåts dock före kommatecken.</span><span class="sxs-lookup"><span data-stu-id="a7204-299">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-300">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-300">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-301">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-301">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="a7204-302">Katalogen \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-302">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="a7204-303">Hämtar kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="a7204-303">Gets directories (folders).</span></span>

<span data-ttu-id="a7204-304">`-Directory`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7204-304">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7204-305">Om du bara vill hämta kataloger använder du `-Directory` parametern och utelämnar `-File` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-305">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="a7204-306">Om du vill utesluta kataloger använder du `-File` parametern och utelämnar `-Directory` parametern, eller använder `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-306">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-307">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-307">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-308">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-308">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="a7204-309">Arkiv \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-309">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="a7204-310">Hämtar filer.</span><span class="sxs-lookup"><span data-stu-id="a7204-310">Gets files.</span></span>

<span data-ttu-id="a7204-311">`-File`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7204-311">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7204-312">Om du bara vill hämta filer använder du `-File` parametern och utelämnar `-Directory` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-312">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="a7204-313">Om du vill undanta filer använder du `-Directory` parametern och utelämnar `-File` parametern, eller så använder du `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-313">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-314">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-314">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-315">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-315">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="a7204-316">Dölja \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-316">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="a7204-317">Hämtar endast dolda filer och kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="a7204-317">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="a7204-318">Som standard får [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) endast icke-dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="a7204-318">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="a7204-319">`-Hidden`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7204-319">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7204-320">Om du bara vill ha dolda objekt använder du `-Hidden` parametern, dess `h` eller `ah` alias eller det **dolda** värdet för `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-320">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="a7204-321">Om du vill utesluta dolda objekt utelämnar du `-Hidden` parametern eller använder `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-321">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-322">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-322">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-323">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-323">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="a7204-324">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-324">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="a7204-325">Hämtar endast skrivskyddade filer och kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="a7204-325">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="a7204-326">`-ReadOnly`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7204-326">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7204-327">Om du bara vill hämta skrivskyddade objekt använder du `-ReadOnly` parametern, dess `ar` alias eller det **skrivskyddade** värdet för `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-327">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="a7204-328">Använd parametern för att undanta skrivskyddade objekt `-Attributes` .</span><span class="sxs-lookup"><span data-stu-id="a7204-328">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-329">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-329">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-330">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-330">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="a7204-331">Säker \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-331">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="a7204-332">Hämtar endast systemfiler och kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="a7204-332">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="a7204-333">`-System`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7204-333">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7204-334">Om du bara vill hämta systemfiler och mappar använder du `-System` parametern, dess `as` alias eller **systemets** värde för `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-334">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="a7204-335">Om du vill undanta systemfiler och mappar använder du `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="a7204-335">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-336">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-336">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-337">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a7204-337">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="a7204-338">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="a7204-338">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="a7204-339">Returnerar `$True` när `LastWriteTime` värdet för en fil är större än det angivna datumet.</span><span class="sxs-lookup"><span data-stu-id="a7204-339">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="a7204-340">Annars returneras `$False` .</span><span class="sxs-lookup"><span data-stu-id="a7204-340">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="a7204-341">Ange ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel ett som cmdleten [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) returnerar, eller en sträng som kan konverteras till ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="a7204-341">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-342">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-342">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-343">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="a7204-343">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="a7204-344">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="a7204-344">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="a7204-345">Returnerar `$True` när `LastWriteTime` värdet för en fil är mindre än det angivna datumet.</span><span class="sxs-lookup"><span data-stu-id="a7204-345">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="a7204-346">Annars returneras `$False` .</span><span class="sxs-lookup"><span data-stu-id="a7204-346">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="a7204-347">Ange ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel ett som cmdleten [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) returnerar, eller en sträng som kan konverteras till ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="a7204-347">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-348">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-348">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-349">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="a7204-349">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="a7204-350">Skicka \<System.String\></span><span class="sxs-lookup"><span data-stu-id="a7204-350">Stream \<System.String\></span></span>

<span data-ttu-id="a7204-351">Hanterar alternativa data strömmar.</span><span class="sxs-lookup"><span data-stu-id="a7204-351">Manages alternate data streams.</span></span> <span data-ttu-id="a7204-352">Ange data ström namnet.</span><span class="sxs-lookup"><span data-stu-id="a7204-352">Enter the stream name.</span></span> <span data-ttu-id="a7204-353">Jokertecken tillåts endast i kommandona [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) för och [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item) i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="a7204-353">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-354">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-354">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-355">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-355">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="a7204-356">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-356">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="a7204-357">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-357">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="a7204-358">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-358">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="a7204-359">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-359">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="a7204-360">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-360">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="a7204-361">Outspädd \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="a7204-361">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="a7204-362">Ignorerar rad matnings tecken.</span><span class="sxs-lookup"><span data-stu-id="a7204-362">Ignores newline characters.</span></span> <span data-ttu-id="a7204-363">Returnerar innehåll som ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="a7204-363">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-364">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-364">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-365">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="a7204-365">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="a7204-366">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="a7204-366">ItemType \<String\></span></span>

<span data-ttu-id="a7204-367">Med den här parametern kan du ange Tye för det objekt som ska skapas med `New-Item`</span><span class="sxs-lookup"><span data-stu-id="a7204-367">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="a7204-368">De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.</span><span class="sxs-lookup"><span data-stu-id="a7204-368">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="a7204-369">I en `FileSystem` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="a7204-369">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="a7204-370">Fil</span><span class="sxs-lookup"><span data-stu-id="a7204-370">File</span></span>
- <span data-ttu-id="a7204-371">Katalog</span><span class="sxs-lookup"><span data-stu-id="a7204-371">Directory</span></span>
- <span data-ttu-id="a7204-372">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="a7204-372">SymbolicLink</span></span>
- <span data-ttu-id="a7204-373">Knutpunkt</span><span class="sxs-lookup"><span data-stu-id="a7204-373">Junction</span></span>
- <span data-ttu-id="a7204-374">HardLink</span><span class="sxs-lookup"><span data-stu-id="a7204-374">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="a7204-375">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="a7204-375">Cmdlets supported</span></span>

- [<span data-ttu-id="a7204-376">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="a7204-376">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="a7204-377">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="a7204-377">Using the pipeline</span></span>

<span data-ttu-id="a7204-378">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="a7204-378">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="a7204-379">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7204-379">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="a7204-380">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="a7204-380">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="a7204-381">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="a7204-381">Getting help</span></span>

<span data-ttu-id="a7204-382">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="a7204-382">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="a7204-383">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="a7204-383">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="a7204-384">Se även</span><span class="sxs-lookup"><span data-stu-id="a7204-384">See also</span></span>

[<span data-ttu-id="a7204-385">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a7204-385">about_Providers</span></span>](../About/about_Providers.md)
