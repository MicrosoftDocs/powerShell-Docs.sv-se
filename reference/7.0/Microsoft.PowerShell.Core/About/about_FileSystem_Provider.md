---
description: Filsystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem-Provider
ms.openlocfilehash: 085d714fce8475dd3eeee656d1cd17db02e772a6
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661400"
---
# <a name="filesystem-provider"></a><span data-ttu-id="5ca86-104">FileSystem-Provider</span><span class="sxs-lookup"><span data-stu-id="5ca86-104">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="5ca86-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="5ca86-105">Provider name</span></span>

<span data-ttu-id="5ca86-106">Filsystem</span><span class="sxs-lookup"><span data-stu-id="5ca86-106">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="5ca86-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="5ca86-107">Drives</span></span>

<span data-ttu-id="5ca86-108">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="5ca86-108">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="5ca86-109">Funktioner</span><span class="sxs-lookup"><span data-stu-id="5ca86-109">Capabilities</span></span>

<span data-ttu-id="5ca86-110">**Filter**, **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="5ca86-110">**Filter**, **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="5ca86-111">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ca86-111">Short description</span></span>

<span data-ttu-id="5ca86-112">Ger åtkomst till filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="5ca86-112">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="5ca86-113">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ca86-113">Detailed description</span></span>

<span data-ttu-id="5ca86-114">Med PowerShell- **dataprovidern** kan du hämta, lägga till, ändra, rensa och ta bort filer och kataloger i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ca86-114">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="5ca86-115">**Fil Systems** enheter är ett hierarkiskt namn område som innehåller de kataloger och filer som finns på din dator.</span><span class="sxs-lookup"><span data-stu-id="5ca86-115">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="5ca86-116">En **fil Systems** enhet kan vara en logisk eller fysisk enhet, katalog eller mappad nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="5ca86-116">A **FileSystem** drive can be a logical or physical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="5ca86-117">En enhet `TEMP:` som heter kommer att mappas till användarens tillfälliga katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="5ca86-117">A drive called `TEMP:` will be mapped to the user's temporary directory path.</span></span>

>[!NOTE]
> <span data-ttu-id="5ca86-118">Innehåll i TEMP: enheten tas inte bort automatiskt av PowerShell och är upp till den användare eller det operativ system som ska hanteras.</span><span class="sxs-lookup"><span data-stu-id="5ca86-118">Contents in the TEMP: drive are not automatically removed by PowerShell and is up to the user or operating system to manage.</span></span> <span data-ttu-id="5ca86-119">Den här funktionen har flyttats från experimentella funktioner i PowerShell version 7,0</span><span class="sxs-lookup"><span data-stu-id="5ca86-119">This Feature was moved out of experimental features in PowerShell Version 7.0</span></span>

<span data-ttu-id="5ca86-120">**Fil Systems** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="5ca86-120">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="5ca86-121">Get-location</span><span class="sxs-lookup"><span data-stu-id="5ca86-121">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="5ca86-122">Ange plats</span><span class="sxs-lookup"><span data-stu-id="5ca86-122">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="5ca86-123">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-123">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="5ca86-124">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-124">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="5ca86-125">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-125">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="5ca86-126">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-126">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="5ca86-127">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-127">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="5ca86-128">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-128">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="5ca86-129">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5ca86-129">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="5ca86-130">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5ca86-130">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="5ca86-131">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-131">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="5ca86-132">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5ca86-132">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="5ca86-133">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-133">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="5ca86-134">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5ca86-134">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="5ca86-135">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="5ca86-135">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="5ca86-136">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="5ca86-136">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="5ca86-137">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5ca86-137">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="5ca86-138">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5ca86-138">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="5ca86-139">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="5ca86-139">Types exposed by this provider</span></span>

<span data-ttu-id="5ca86-140">Filerna är instanser av klassen [system. io. fileinfo](/dotnet/api/system.io.fileinfo) .</span><span class="sxs-lookup"><span data-stu-id="5ca86-140">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span> <span data-ttu-id="5ca86-141">Kataloger är instanser av klassen [system. io. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .</span><span class="sxs-lookup"><span data-stu-id="5ca86-141">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="5ca86-142">Navigera i fil Systems enheter</span><span class="sxs-lookup"><span data-stu-id="5ca86-142">Navigating the FileSystem drives</span></span>

<span data-ttu-id="5ca86-143">**Fil Systems** leverantören visar sina data lager genom att mappa alla logiska enheter på datorn som PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="5ca86-143">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="5ca86-144">Om du vill arbeta med en **fil Systems** enhet kan du ändra din plats till en enhet med hjälp av enhets namnet följt av ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="5ca86-144">To work with a **FileSystem** drive you can change your location to a drive using the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="5ca86-145">Du kan också arbeta med **fil Systems** leverantören från någon annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-145">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="5ca86-146">Om du vill referera till en fil eller katalog från en annan plats använder du enhets namnet ( `C:` ,... `D:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-146">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="5ca86-147">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="5ca86-147">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="5ca86-148">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="5ca86-148">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="5ca86-149">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="5ca86-149">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="5ca86-150">Hämta filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="5ca86-150">Getting files and directories</span></span>

<span data-ttu-id="5ca86-151">`Get-ChildItem`Cmdleten returnerar alla filer och kataloger på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-151">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="5ca86-152">Du kan ange en annan sökväg för att söka efter och använda inbyggda parametrar för att filtrera och styra rekursion-djupet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-152">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="5ca86-153">Läs mer om cmdlet-användning i [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span><span class="sxs-lookup"><span data-stu-id="5ca86-153">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="5ca86-154">Kopiera filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="5ca86-154">Copying files and directories</span></span>

<span data-ttu-id="5ca86-155">`Copy-Item`Cmdleten kopierar filer och kataloger till en plats som du anger.</span><span class="sxs-lookup"><span data-stu-id="5ca86-155">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="5ca86-156">Parametrar är tillgängliga för att filtrera och rekursivt, ungefär som `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-156">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="5ca86-157">Följande kommando kopierar alla filer och kataloger under sökvägen "C:\Temp" \" till mappen "C:\Windows\Temp".</span><span class="sxs-lookup"><span data-stu-id="5ca86-157">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="5ca86-158">`Copy-Item` skriver över filer i mål katalogen utan att uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="5ca86-158">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="5ca86-159">Det här kommandot kopierar `a.txt` filen från `C:\a` katalogen till `C:\a\bb` katalogen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-159">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="5ca86-160">Kopierar alla kataloger och filer i `C:\a` katalogen till `C:\c` katalogen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-160">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="5ca86-161">Om någon av de kataloger som ska kopieras redan finns i mål katalogen, kommer kommandot att Miss kopie ras om du inte anger en Force-parameter.</span><span class="sxs-lookup"><span data-stu-id="5ca86-161">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="5ca86-162">Mer information finns i [Kopiera objekt](xref:Microsoft.PowerShell.Management.Copy-Item).</span><span class="sxs-lookup"><span data-stu-id="5ca86-162">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="5ca86-163">Flytta filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="5ca86-163">Moving files and directories</span></span>

<span data-ttu-id="5ca86-164">Det här kommandot flyttar `c.txt` filen i `C:\a` katalogen till `C:\a\aa` katalogen:</span><span class="sxs-lookup"><span data-stu-id="5ca86-164">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="5ca86-165">Kommandot kommer inte att skriva över en befintlig fil som har samma namn automatiskt.</span><span class="sxs-lookup"><span data-stu-id="5ca86-165">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="5ca86-166">Om du vill tvinga cmdleten att skriva över en befintlig fil anger du parametern Force.</span><span class="sxs-lookup"><span data-stu-id="5ca86-166">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="5ca86-167">Du kan inte flytta en katalog när katalogen är den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-167">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="5ca86-168">När du använder `Move-Item` för att flytta katalogen på den aktuella platsen visas det här felet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-168">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="5ca86-169">Hantera fil innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-169">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="5ca86-170">Hämta innehållet i en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-170">Get the content of a file</span></span>

<span data-ttu-id="5ca86-171">Det här kommandot hämtar innehållet i filen "Test.txt" och visar dem i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-171">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="5ca86-172">Du kan skicka vidare innehållet i filen till en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-172">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="5ca86-173">Följande kommando läser till exempel innehållet i `Test.txt` filen och skickar dem som indata till [ConvertTo-HTML-](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdleten:</span><span class="sxs-lookup"><span data-stu-id="5ca86-173">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="5ca86-174">Du kan också hämta innehållet i en fil genom att förkorrigera dess Provider-sökväg med dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="5ca86-174">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="5ca86-175">Sökvägen måste stå inom klammerparenteser på grund av variabla namngivnings begränsningar.</span><span class="sxs-lookup"><span data-stu-id="5ca86-175">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="5ca86-176">Mer information finns i [about_Variables](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="5ca86-176">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="5ca86-177">Lägga till innehåll i en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-177">Add content to a file</span></span>

<span data-ttu-id="5ca86-178">Detta kommando lägger till strängen "testa innehåll" till `Test.txt` filen:</span><span class="sxs-lookup"><span data-stu-id="5ca86-178">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="5ca86-179">Det befintliga innehållet i `Test.txt` filen tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="5ca86-179">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="5ca86-180">Ersätt innehållet i en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-180">Replace the content of a file</span></span>

<span data-ttu-id="5ca86-181">Det här kommandot ersätter `Test.txt` filens innehåll med strängen "test content":</span><span class="sxs-lookup"><span data-stu-id="5ca86-181">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="5ca86-182">Innehållet i skrivs över `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-182">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="5ca86-183">Du kan använda **Value** -parametern för cmdleten [New-item](xref:Microsoft.PowerShell.Management.New-Item) för att lägga till innehåll i en fil när du skapar den.</span><span class="sxs-lookup"><span data-stu-id="5ca86-183">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="5ca86-184">Loopa igenom innehållet i en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-184">Loop through the contents of a file</span></span>

<span data-ttu-id="5ca86-185">Som standard `Get-Content` använder cmdleten rad slutet som avgränsare, så den hämtar en fil som en samling strängar, med varje rad som en sträng i filen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-185">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="5ca86-186">Du kan använda `-Delimiter` parametern för att ange en alternativ avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5ca86-186">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="5ca86-187">Om du ställer in det på tecknen som anger slutet på ett avsnitt eller början av nästa avsnitt, kan du dela upp filen i logiska delar.</span><span class="sxs-lookup"><span data-stu-id="5ca86-187">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="5ca86-188">Det första kommandot hämtar `Employees.txt` filen och delar den i avsnitt, som var och en slutar med orden "slutet av medarbetar posten" och sparar den i `$e` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5ca86-188">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="5ca86-189">Det andra kommandot använder mat ris notation för att hämta det första objektet i samlingen i `$e` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-189">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="5ca86-190">Det använder ett index på 0, eftersom PowerShell-matriser är noll-baserade.</span><span class="sxs-lookup"><span data-stu-id="5ca86-190">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="5ca86-191">Mer information om `Get-Content` cmdlet finns i hjälp avsnittet för [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span><span class="sxs-lookup"><span data-stu-id="5ca86-191">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="5ca86-192">Mer information om matriser finns [about_Arrays](../About/about_Arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5ca86-192">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="5ca86-193">Hantera säkerhets beskrivningar</span><span class="sxs-lookup"><span data-stu-id="5ca86-193">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="5ca86-194">Visa ACL för en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-194">View the ACL for a file</span></span>

<span data-ttu-id="5ca86-195">Det här kommandot returnerar ett [system. Security. AccessControl. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -objekt:</span><span class="sxs-lookup"><span data-stu-id="5ca86-195">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="5ca86-196">Om du vill ha mer information om det här objektet, rör du kommandot till cmdleten [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) .</span><span class="sxs-lookup"><span data-stu-id="5ca86-196">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="5ca86-197">Eller, se [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -klass.</span><span class="sxs-lookup"><span data-stu-id="5ca86-197">Or, see [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="5ca86-198">Ändra ACL för en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-198">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="5ca86-199">Skapa och ange en ACL för en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-199">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="5ca86-200">Skapa filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="5ca86-200">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="5ca86-201">Skapa en katalog</span><span class="sxs-lookup"><span data-stu-id="5ca86-201">Create a directory</span></span>

<span data-ttu-id="5ca86-202">Det här kommandot skapar `logfiles` katalogen på `C` enheten:</span><span class="sxs-lookup"><span data-stu-id="5ca86-202">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="5ca86-203">PowerShell innehåller också en `mkdir` funktion (alias `md` ) som använder cmdleten [New-item](xref:Microsoft.PowerShell.Management.New-Item) för att skapa en ny katalog.</span><span class="sxs-lookup"><span data-stu-id="5ca86-203">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="5ca86-204">Skapa en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-204">Create a file</span></span>

<span data-ttu-id="5ca86-205">Det här kommandot skapar `log2.txt` filen i `C:\logfiles` katalogen och lägger sedan till strängen "testa logg" i filen:</span><span class="sxs-lookup"><span data-stu-id="5ca86-205">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="5ca86-206">Skapa en fil med innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-206">Create a file with content</span></span>

<span data-ttu-id="5ca86-207">Skapar en fil som kallas `log2.txt` i `C:\logfiles` katalogen och lägger till strängen "test loggen" i filen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-207">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="5ca86-208">Byta namn på filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="5ca86-208">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="5ca86-209">Byt namn på en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-209">Rename a file</span></span>

<span data-ttu-id="5ca86-210">Det här kommandot byter namn på `a.txt` filen i `C:\a` katalogen till `b.txt` :</span><span class="sxs-lookup"><span data-stu-id="5ca86-210">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="5ca86-211">Byta namn på en katalog</span><span class="sxs-lookup"><span data-stu-id="5ca86-211">Rename a directory</span></span>

<span data-ttu-id="5ca86-212">Det här kommandot byter namn på `C:\a\cc` katalogen till `C:\a\dd` :</span><span class="sxs-lookup"><span data-stu-id="5ca86-212">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="5ca86-213">Ta bort filer och kataloger</span><span class="sxs-lookup"><span data-stu-id="5ca86-213">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="5ca86-214">Ta bort en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-214">Delete a file</span></span>

<span data-ttu-id="5ca86-215">Det här kommandot tar bort `Test.txt` filen i den aktuella katalogen:</span><span class="sxs-lookup"><span data-stu-id="5ca86-215">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="5ca86-216">Ta bort filer med jokertecken</span><span class="sxs-lookup"><span data-stu-id="5ca86-216">Delete files using wildcards</span></span>

<span data-ttu-id="5ca86-217">Det här kommandot tar bort alla filer i den aktuella katalogen som har `.xml` fil namns tillägget:</span><span class="sxs-lookup"><span data-stu-id="5ca86-217">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="5ca86-218">Starta ett program genom att anropa en associerad fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-218">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="5ca86-219">Anropa en fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-219">Invoke a file</span></span>

<span data-ttu-id="5ca86-220">Det första kommandot använder cmdleten [Get-service](xref:Microsoft.PowerShell.Management.Get-Service) för att hämta information om lokala tjänster.</span><span class="sxs-lookup"><span data-stu-id="5ca86-220">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="5ca86-221">Den rör informationen till [export-csv-](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdleten och lagrar sedan informationen i `Services.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-221">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="5ca86-222">Det andra kommandot använder [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item) för att öppna `services.csv` filen i programmet som är associerat med `.csv` tillägget:</span><span class="sxs-lookup"><span data-stu-id="5ca86-222">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="5ca86-223">Hämta filer och mappar med angivna attribut</span><span class="sxs-lookup"><span data-stu-id="5ca86-223">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="5ca86-224">Hämta systemfiler</span><span class="sxs-lookup"><span data-stu-id="5ca86-224">Get System files</span></span>

<span data-ttu-id="5ca86-225">Detta kommando hämtar systemfiler i den aktuella katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="5ca86-225">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="5ca86-226">`-File`Parametern används för att bara hämta filer (inte kataloger) och `-System` parametern för att bara hämta objekt med attributet "system".</span><span class="sxs-lookup"><span data-stu-id="5ca86-226">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="5ca86-227">Den använder `-Recurse` parametern för att hämta objekten i den aktuella katalogen och alla under kataloger.</span><span class="sxs-lookup"><span data-stu-id="5ca86-227">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="5ca86-228">Hämta dolda filer</span><span class="sxs-lookup"><span data-stu-id="5ca86-228">Get Hidden files</span></span>

<span data-ttu-id="5ca86-229">Det här kommandot hämtar alla filer, inklusive dolda filer, i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-229">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="5ca86-230">Den använder parametern **attributes** med två värden, `!Directory+Hidden` , som hämtar dolda filer och `!Directory` , som hämtar alla andra filer.</span><span class="sxs-lookup"><span data-stu-id="5ca86-230">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="5ca86-231">`dir -att !d,!d+h` är motsvarigheten till det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="5ca86-231">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="5ca86-232">Hämta komprimerade och krypterade filer</span><span class="sxs-lookup"><span data-stu-id="5ca86-232">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="5ca86-233">Det här kommandot hämtar filer i den aktuella katalogen som är antingen komprimerade eller krypterade.</span><span class="sxs-lookup"><span data-stu-id="5ca86-233">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="5ca86-234">`-Attributes`Parametern med två värden används `Compressed` och `Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-234">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="5ca86-235">Värdena avgränsas med ett kommatecken `,` som representerar operatorn "eller".</span><span class="sxs-lookup"><span data-stu-id="5ca86-235">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="5ca86-236">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5ca86-236">Dynamic parameters</span></span>

<span data-ttu-id="5ca86-237">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="5ca86-237">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="5ca86-238">Inställning \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="5ca86-238">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="5ca86-239">Anger fil kodningen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-239">Specifies the file encoding.</span></span> <span data-ttu-id="5ca86-240">Standardvärdet är ASCII.</span><span class="sxs-lookup"><span data-stu-id="5ca86-240">The default is ASCII.</span></span>

- <span data-ttu-id="5ca86-241">**ASCII**: använder kodningen för ASCII-teckenuppsättningen (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="5ca86-241">**ASCII**:  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="5ca86-242">**BigEndianUnicode**: kodar i UTF-16-format med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-242">**BigEndianUnicode**:  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="5ca86-243">**Sträng**: använder kodnings typen för en sträng.</span><span class="sxs-lookup"><span data-stu-id="5ca86-243">**String**:  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="5ca86-244">**Unicode**: kodar i UTF-16-format med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="5ca86-244">**Unicode**:  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="5ca86-245">**UTF7**: kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="5ca86-245">**UTF7**:   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="5ca86-246">**Utf8**: kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="5ca86-246">**UTF8**:  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="5ca86-247">**UTF8BOM**: kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="5ca86-247">**UTF8BOM**: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="5ca86-248">**UF8NOBOM**: kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="5ca86-248">**UF8NOBOM**: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="5ca86-249">**UTF32**: kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="5ca86-249">**UTF32**:  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="5ca86-250">**Standard**: kodas på den installerade standard tecken tabellen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-250">**Default**: Encodes in the default installed code page.</span></span>
- <span data-ttu-id="5ca86-251">**OEM**: använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="5ca86-251">**OEM**: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="5ca86-252">**Okänd**: kodnings typen är okänd eller ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5ca86-252">**Unknown**:  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="5ca86-253">Data kan behandlas som binära.</span><span class="sxs-lookup"><span data-stu-id="5ca86-253">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-254">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-254">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-255">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-255">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="5ca86-256">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-256">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="5ca86-257">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-257">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="5ca86-258">Avgränsare \<System.String\></span><span class="sxs-lookup"><span data-stu-id="5ca86-258">Delimiter \<System.String\></span></span>

<span data-ttu-id="5ca86-259">Anger den avgränsare som [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) använder för att dela upp filen i objekt när den läses.</span><span class="sxs-lookup"><span data-stu-id="5ca86-259">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="5ca86-260">Standardvärdet är `\n` rad slutet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-260">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="5ca86-261">När du läser en textfil returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) en samling av sträng objekt, som var och en slutar med avgränsnings tecken.</span><span class="sxs-lookup"><span data-stu-id="5ca86-261">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="5ca86-262">Om du anger en avgränsare som inte finns i filen returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) hela filen som ett enskilt avgränsat objekt.</span><span class="sxs-lookup"><span data-stu-id="5ca86-262">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="5ca86-263">Du kan använda den här parametern för att dela upp en stor fil i mindre filer genom att ange en fil avgränsare, till exempel "slutet av exemplet", som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5ca86-263">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="5ca86-264">Avgränsaren bevaras (tas inte bort) och blir det sista objektet i varje fil avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5ca86-264">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="5ca86-265">När värdet för `-Delimiter` parametern är en tom sträng returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) inte något.</span><span class="sxs-lookup"><span data-stu-id="5ca86-265">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="5ca86-266">Detta är ett känt problem.</span><span class="sxs-lookup"><span data-stu-id="5ca86-266">This is a known issue.</span></span> <span data-ttu-id="5ca86-267">Om du vill tvinga [Get-innehåll](xref:Microsoft.PowerShell.Management.Get-Content) att returnera hela filen som en enskild, icke-avgränsad sträng anger du ett värde som inte finns i filen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-267">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-268">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-268">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-269">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-269">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5ca86-270">Vänta \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-270">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="5ca86-271">Väntar på att innehåll ska läggas till i filen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-271">Waits for content to be appended to the file.</span></span> <span data-ttu-id="5ca86-272">Om innehållet läggs till, returneras det tillagda innehållet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-272">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="5ca86-273">Om innehållet har ändrats returnerar det hela filen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-273">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="5ca86-274">När du väntar så kontrollerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) att filen är en gång i sekunden tills du avbryter den, till exempel genom att trycka på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="5ca86-274">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-275">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-275">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-276">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-276">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="5ca86-277">Dokumentattribut \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="5ca86-277">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="5ca86-278">Hämtar filer och mappar med de angivna attributen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-278">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="5ca86-279">Den här parametern stöder alla attribut och gör att du kan ange komplexa kombinationer av attribut.</span><span class="sxs-lookup"><span data-stu-id="5ca86-279">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="5ca86-280">`-Attributes`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ca86-280">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5ca86-281">`-Attributes`Parametern stöder följande attribut:</span><span class="sxs-lookup"><span data-stu-id="5ca86-281">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="5ca86-282">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="5ca86-282">**Archive**</span></span>
- <span data-ttu-id="5ca86-283">**Komprimerade**</span><span class="sxs-lookup"><span data-stu-id="5ca86-283">**Compressed**</span></span>
- <span data-ttu-id="5ca86-284">**Enhet**</span><span class="sxs-lookup"><span data-stu-id="5ca86-284">**Device**</span></span>
- <span data-ttu-id="5ca86-285">**Katalog**</span><span class="sxs-lookup"><span data-stu-id="5ca86-285">**Directory**</span></span>
- <span data-ttu-id="5ca86-286">**Krypterad**</span><span class="sxs-lookup"><span data-stu-id="5ca86-286">**Encrypted**</span></span>
- <span data-ttu-id="5ca86-287">**Dold**</span><span class="sxs-lookup"><span data-stu-id="5ca86-287">**Hidden**</span></span>
- <span data-ttu-id="5ca86-288">**Normal**</span><span class="sxs-lookup"><span data-stu-id="5ca86-288">**Normal**</span></span>
- <span data-ttu-id="5ca86-289">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="5ca86-289">**NotContentIndexed**</span></span>
- <span data-ttu-id="5ca86-290">**Offline**</span><span class="sxs-lookup"><span data-stu-id="5ca86-290">**Offline**</span></span>
- <span data-ttu-id="5ca86-291">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="5ca86-291">**ReadOnly**</span></span>
- <span data-ttu-id="5ca86-292">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="5ca86-292">**ReparsePoint**</span></span>
- <span data-ttu-id="5ca86-293">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="5ca86-293">**SparseFile**</span></span>
- <span data-ttu-id="5ca86-294">**System**</span><span class="sxs-lookup"><span data-stu-id="5ca86-294">**System**</span></span>
- <span data-ttu-id="5ca86-295">**Tillfälliga**</span><span class="sxs-lookup"><span data-stu-id="5ca86-295">**Temporary**</span></span>

<span data-ttu-id="5ca86-296">En beskrivning av dessa attribut finns i [FileAttributes](/dotnet/api/system.io.fileattributes) -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="5ca86-296">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="5ca86-297">Använd följande operatorer för att kombinera attribut.</span><span class="sxs-lookup"><span data-stu-id="5ca86-297">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="5ca86-298">`!` – INTE</span><span class="sxs-lookup"><span data-stu-id="5ca86-298">`!` - NOT</span></span>
- <span data-ttu-id="5ca86-299">`+` -OCH</span><span class="sxs-lookup"><span data-stu-id="5ca86-299">`+` - AND</span></span>
- <span data-ttu-id="5ca86-300">`,` -ELLER</span><span class="sxs-lookup"><span data-stu-id="5ca86-300">`,` - OR</span></span>

<span data-ttu-id="5ca86-301">Inga blank steg är tillåtna mellan en operator och dess attribut.</span><span class="sxs-lookup"><span data-stu-id="5ca86-301">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="5ca86-302">Blank steg tillåts dock före kommatecken.</span><span class="sxs-lookup"><span data-stu-id="5ca86-302">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-303">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-303">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-304">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-304">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5ca86-305">Katalogen \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-305">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="5ca86-306">Hämtar kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="5ca86-306">Gets directories (folders).</span></span>

<span data-ttu-id="5ca86-307">`-Directory`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ca86-307">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5ca86-308">Om du bara vill hämta kataloger använder du `-Directory` parametern och utelämnar `-File` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-308">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="5ca86-309">Om du vill utesluta kataloger använder du `-File` parametern och utelämnar `-Directory` parametern, eller använder `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-309">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-310">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-310">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-311">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-311">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5ca86-312">Arkiv \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-312">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="5ca86-313">Hämtar filer.</span><span class="sxs-lookup"><span data-stu-id="5ca86-313">Gets files.</span></span>

<span data-ttu-id="5ca86-314">`-File`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ca86-314">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5ca86-315">Om du bara vill hämta filer använder du `-File` parametern och utelämnar `-Directory` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-315">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="5ca86-316">Om du vill undanta filer använder du `-Directory` parametern och utelämnar `-File` parametern, eller så använder du `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-316">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-317">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-317">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-318">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-318">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5ca86-319">Dölja \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-319">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="5ca86-320">Hämtar endast dolda filer och kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="5ca86-320">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="5ca86-321">Som standard får [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) endast icke-dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="5ca86-321">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="5ca86-322">`-Hidden`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ca86-322">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5ca86-323">Om du bara vill ha dolda objekt använder du `-Hidden` parametern, dess `h` eller `ah` alias eller det **dolda** värdet för `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-323">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="5ca86-324">Om du vill utesluta dolda objekt utelämnar du `-Hidden` parametern eller använder `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-324">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-325">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-325">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-326">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-326">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5ca86-327">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-327">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="5ca86-328">Hämtar endast skrivskyddade filer och kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="5ca86-328">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="5ca86-329">`-ReadOnly`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ca86-329">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5ca86-330">Om du bara vill hämta skrivskyddade objekt använder du `-ReadOnly` parametern, dess `ar` alias eller det **skrivskyddade** värdet för `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-330">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="5ca86-331">Använd parametern för att undanta skrivskyddade objekt `-Attributes` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-331">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-332">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-332">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-333">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-333">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5ca86-334">Säker \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-334">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="5ca86-335">Hämtar endast systemfiler och kataloger (mappar).</span><span class="sxs-lookup"><span data-stu-id="5ca86-335">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="5ca86-336">`-System`Parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ca86-336">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5ca86-337">Om du bara vill hämta systemfiler och mappar använder du `-System` parametern, dess `as` alias eller **systemets** värde för `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-337">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="5ca86-338">Om du vill undanta systemfiler och mappar använder du `-Attributes` parametern.</span><span class="sxs-lookup"><span data-stu-id="5ca86-338">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-339">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-339">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-340">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5ca86-340">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="5ca86-341">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="5ca86-341">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="5ca86-342">Returnerar `$True` när `LastWriteTime` värdet för en fil är större än det angivna datumet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-342">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="5ca86-343">Annars returneras `$False` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-343">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="5ca86-344">Ange ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel ett som cmdleten [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) returnerar, eller en sträng som kan konverteras till ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-344">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-345">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-345">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-346">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="5ca86-346">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="5ca86-347">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="5ca86-347">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="5ca86-348">Returnerar `$True` när `LastWriteTime` värdet för en fil är mindre än det angivna datumet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-348">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="5ca86-349">Annars returneras `$False` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-349">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="5ca86-350">Ange ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel ett som cmdleten [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) returnerar, eller en sträng som kan konverteras till ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="5ca86-350">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-351">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-351">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-352">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="5ca86-352">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="5ca86-353">Skicka \<System.String\></span><span class="sxs-lookup"><span data-stu-id="5ca86-353">Stream \<System.String\></span></span>

<span data-ttu-id="5ca86-354">Hanterar alternativa data strömmar.</span><span class="sxs-lookup"><span data-stu-id="5ca86-354">Manages alternate data streams.</span></span> <span data-ttu-id="5ca86-355">Ange data ström namnet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-355">Enter the stream name.</span></span> <span data-ttu-id="5ca86-356">Jokertecken tillåts endast i kommandona [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) för och [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item) i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="5ca86-356">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-357">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-357">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-358">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-358">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="5ca86-359">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-359">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="5ca86-360">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-360">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="5ca86-361">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-361">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="5ca86-362">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-362">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="5ca86-363">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-363">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="5ca86-364">Outspädd \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="5ca86-364">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="5ca86-365">Ignorerar rad matnings tecken.</span><span class="sxs-lookup"><span data-stu-id="5ca86-365">Ignores newline characters.</span></span> <span data-ttu-id="5ca86-366">Returnerar innehåll som ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="5ca86-366">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-367">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-367">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-368">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="5ca86-368">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="5ca86-369">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="5ca86-369">ItemType \<String\></span></span>

<span data-ttu-id="5ca86-370">Med den här parametern kan du ange Tye för det objekt som ska skapas med `New-Item`</span><span class="sxs-lookup"><span data-stu-id="5ca86-370">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="5ca86-371">De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.</span><span class="sxs-lookup"><span data-stu-id="5ca86-371">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="5ca86-372">I en `FileSystem` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="5ca86-372">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="5ca86-373">Fil</span><span class="sxs-lookup"><span data-stu-id="5ca86-373">File</span></span>
- <span data-ttu-id="5ca86-374">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca86-374">Directory</span></span>
- <span data-ttu-id="5ca86-375">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="5ca86-375">SymbolicLink</span></span>
- <span data-ttu-id="5ca86-376">Knutpunkt</span><span class="sxs-lookup"><span data-stu-id="5ca86-376">Junction</span></span>
- <span data-ttu-id="5ca86-377">HardLink</span><span class="sxs-lookup"><span data-stu-id="5ca86-377">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="5ca86-378">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="5ca86-378">Cmdlets supported</span></span>

- [<span data-ttu-id="5ca86-379">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="5ca86-379">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="5ca86-380">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="5ca86-380">Using the pipeline</span></span>

<span data-ttu-id="5ca86-381">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="5ca86-381">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="5ca86-382">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ca86-382">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="5ca86-383">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="5ca86-383">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="5ca86-384">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="5ca86-384">Getting help</span></span>

<span data-ttu-id="5ca86-385">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="5ca86-385">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="5ca86-386">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="5ca86-386">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="5ca86-387">Se även</span><span class="sxs-lookup"><span data-stu-id="5ca86-387">See also</span></span>

[<span data-ttu-id="5ca86-388">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5ca86-388">about_Providers</span></span>](../About/about_Providers.md)
