---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: 0bcd46e49559ad625621a7ff81162af695f6f93c
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661332"
---
# <span data-ttu-id="15a3e-103">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="15a3e-103">Get-ChildItem</span></span>

## <span data-ttu-id="15a3e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="15a3e-104">SYNOPSIS</span></span>

<span data-ttu-id="15a3e-105">Hämtar objekten och underordnade objekt på en eller flera angivna platser.</span><span class="sxs-lookup"><span data-stu-id="15a3e-105">Gets the items and child items in one or more specified locations.</span></span>

## <span data-ttu-id="15a3e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15a3e-106">SYNTAX</span></span>

### <span data-ttu-id="15a3e-107">Objekt (standard)</span><span class="sxs-lookup"><span data-stu-id="15a3e-107">Items (Default)</span></span>

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="15a3e-108">LiteralItems</span><span class="sxs-lookup"><span data-stu-id="15a3e-108">LiteralItems</span></span>

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## <span data-ttu-id="15a3e-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="15a3e-109">DESCRIPTION</span></span>

<span data-ttu-id="15a3e-110">`Get-ChildItem`Cmdlet: en hämtar objekten på en eller flera angivna platser.</span><span class="sxs-lookup"><span data-stu-id="15a3e-110">The `Get-ChildItem` cmdlet gets the items in one or more specified locations.</span></span> <span data-ttu-id="15a3e-111">Om objektet är en behållare hämtas objekten inuti behållaren, så kallade underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="15a3e-111">If the item is a container, it gets the items inside the container, known as child items.</span></span> <span data-ttu-id="15a3e-112">Du kan använda parametern **rekursivt** för att hämta objekt i alla underordnade behållare och använda parametern **djup** för att begränsa antalet nivåer till rekursivt.</span><span class="sxs-lookup"><span data-stu-id="15a3e-112">You can use the **Recurse** parameter to get items in all child containers and use the **Depth** parameter to limit the number of levels to recurse.</span></span>

<span data-ttu-id="15a3e-113">`Get-ChildItem` visar inte tomma kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-113">`Get-ChildItem` doesn't display empty directories.</span></span> <span data-ttu-id="15a3e-114">När ett `Get-ChildItem` kommando innehåller **djup** -eller **rekursivt** -parametrarna tas tomma kataloger inte med i utdata.</span><span class="sxs-lookup"><span data-stu-id="15a3e-114">When a `Get-ChildItem` command includes the **Depth** or **Recurse** parameters, empty directories aren't included in the output.</span></span>

<span data-ttu-id="15a3e-115">Platser exponeras `Get-ChildItem` av PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="15a3e-115">Locations are exposed to `Get-ChildItem` by PowerShell providers.</span></span> <span data-ttu-id="15a3e-116">En plats kan vara en fil system katalog, en registrerings data fil eller ett certifikat arkiv.</span><span class="sxs-lookup"><span data-stu-id="15a3e-116">A location can be a file system directory, registry hive, or a certificate store.</span></span> <span data-ttu-id="15a3e-117">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-117">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="15a3e-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="15a3e-118">EXAMPLES</span></span>

### <span data-ttu-id="15a3e-119">Exempel 1: Hämta underordnade objekt från en fil system katalog</span><span class="sxs-lookup"><span data-stu-id="15a3e-119">Example 1: Get child items from a file system directory</span></span>

<span data-ttu-id="15a3e-120">Det här exemplet hämtar underordnade objekt från en fil system katalog.</span><span class="sxs-lookup"><span data-stu-id="15a3e-120">This example gets the child items from a file system directory.</span></span> <span data-ttu-id="15a3e-121">Fil namnen och under katalog namnen visas.</span><span class="sxs-lookup"><span data-stu-id="15a3e-121">The filenames and subdirectory names are displayed.</span></span> <span data-ttu-id="15a3e-122">För tomma platser returnerar kommandot inga utdata och återgår till PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="15a3e-122">For empty locations, the command doesn't return any output and returns to the PowerShell prompt.</span></span>

<span data-ttu-id="15a3e-123">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-123">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span>
<span data-ttu-id="15a3e-124">`Get-ChildItem` visar filer och kataloger i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-124">`Get-ChildItem` displays the files and directories in the PowerShell console.</span></span>

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="15a3e-125">Som standard `Get-ChildItem` visas läget (**attribut**), **LastWriteTime**, fil storlek (**längd**) och **namnet** på objektet.</span><span class="sxs-lookup"><span data-stu-id="15a3e-125">By default `Get-ChildItem` lists the mode (**Attributes**), **LastWriteTime**, file size (**Length**), and the **Name** of the item.</span></span> <span data-ttu-id="15a3e-126">Bokstäverna i egenskapen **mode** kan tolkas på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="15a3e-126">The letters in the **Mode** property can be interpreted as follows:</span></span>

- <span data-ttu-id="15a3e-127">`l` Operationsföljdslänkkod</span><span class="sxs-lookup"><span data-stu-id="15a3e-127">`l` (link)</span></span>
- <span data-ttu-id="15a3e-128">`d` katalogen</span><span class="sxs-lookup"><span data-stu-id="15a3e-128">`d` (directory)</span></span>
- <span data-ttu-id="15a3e-129">`a` arkivattributet</span><span class="sxs-lookup"><span data-stu-id="15a3e-129">`a` (archive)</span></span>
- <span data-ttu-id="15a3e-130">`r` (skrivskyddad)</span><span class="sxs-lookup"><span data-stu-id="15a3e-130">`r` (read-only)</span></span>
- <span data-ttu-id="15a3e-131">`h` dölja</span><span class="sxs-lookup"><span data-stu-id="15a3e-131">`h` (hidden)</span></span>
- <span data-ttu-id="15a3e-132">`s` (system).</span><span class="sxs-lookup"><span data-stu-id="15a3e-132">`s` (system).</span></span>

<span data-ttu-id="15a3e-133">Mer information om läges flaggor finns [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span><span class="sxs-lookup"><span data-stu-id="15a3e-133">For more information about the mode flags, see [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span></span>

### <span data-ttu-id="15a3e-134">Exempel 2: Hämta underordnade objekt namn i en katalog</span><span class="sxs-lookup"><span data-stu-id="15a3e-134">Example 2: Get child item names in a directory</span></span>

<span data-ttu-id="15a3e-135">I det här exemplet visas endast namn på objekt i en katalog.</span><span class="sxs-lookup"><span data-stu-id="15a3e-135">This example lists only the names of items in a directory.</span></span>

<span data-ttu-id="15a3e-136">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-136">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span> <span data-ttu-id="15a3e-137">Parametern **Name** returnerar bara fil-eller katalog namnen från den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-137">The **Name** parameter returns only the file or directory names from the specified path.</span></span>

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### <span data-ttu-id="15a3e-138">Exempel 3: Hämta underordnade objekt i den aktuella katalogen och under kataloger</span><span class="sxs-lookup"><span data-stu-id="15a3e-138">Example 3: Get child items in the current directory and subdirectories</span></span>

<span data-ttu-id="15a3e-139">I det här exemplet visas **. txt** -filer som finns i den aktuella katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-139">This example displays **.txt** files that are located in the current directory and its subdirectories.</span></span>

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="15a3e-140">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange `C:\Test\*.txt` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-140">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify `C:\Test\*.txt`.</span></span> <span data-ttu-id="15a3e-141">**Sökvägen** använder jokertecknet asterisk ( `*` ) för att ange alla filer med fil namns tillägget `.txt` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-141">**Path** uses the asterisk (`*`) wildcard to specify all files with the filename extension `.txt`.</span></span> <span data-ttu-id="15a3e-142">Parametern **rekursivt** söker igenom **Sök vägs** katalogen under kataloger, som du ser i **katalogen:** rubriker.</span><span class="sxs-lookup"><span data-stu-id="15a3e-142">The **Recurse** parameter searches the **Path** directory its subdirectories, as shown in the **Directory:** headings.</span></span> <span data-ttu-id="15a3e-143">Parametern **Force** visar dolda filer som `hiddenfile.txt` har ett läge på **h**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-143">The **Force** parameter displays hidden files such as `hiddenfile.txt` that have a mode of **h**.</span></span>

### <span data-ttu-id="15a3e-144">Exempel 4: Hämta underordnade objekt med parametern include</span><span class="sxs-lookup"><span data-stu-id="15a3e-144">Example 4: Get child items using the Include parameter</span></span>

<span data-ttu-id="15a3e-145">I det här exemplet `Get-ChildItem` används parametern **include** för att hitta specifika objekt från katalogen som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-145">In this example `Get-ChildItem` uses the **Include** parameter to find specific items from the directory specified by the **Path** parameter.</span></span>

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="15a3e-146">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen **C:\test**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-146">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test**.</span></span> <span data-ttu-id="15a3e-147">Parametern **Path** innehåller ett avslutande asterisk ( `*` )-jokertecken för att ange katalogens innehåll.</span><span class="sxs-lookup"><span data-stu-id="15a3e-147">The **Path** parameter includes a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span>
<span data-ttu-id="15a3e-148">Parametern **include** använder en asterisk ( `*` ) som jokertecken för att ange alla filer med fil namns tillägget **. txt**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-148">The **Include** parameter uses an asterisk (`*`) wildcard to specify all files with the file name extension **.txt**.</span></span>

<span data-ttu-id="15a3e-149">När parametern **include** används, behöver parametern **Path** en avslutande asterisk ( `*` ) som jokertecken för att ange katalogens innehåll.</span><span class="sxs-lookup"><span data-stu-id="15a3e-149">When the **Include** parameter is used, the **Path** parameter needs a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span> <span data-ttu-id="15a3e-150">Ett exempel är `-Path C:\Test\*`.</span><span class="sxs-lookup"><span data-stu-id="15a3e-150">For example, `-Path C:\Test\*`.</span></span>

- <span data-ttu-id="15a3e-151">Om parametern **rekursivt** läggs till i kommandot är den efterföljande asterisken ( `*` ) i parametern **Path** valfri.</span><span class="sxs-lookup"><span data-stu-id="15a3e-151">If the **Recurse** parameter is added to the command, the trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="15a3e-152">Parametern **rekursivt** hämtar objekt från **Sök vägs** katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-152">The **Recurse** parameter gets items from the **Path** directory and its subdirectories.</span></span> <span data-ttu-id="15a3e-153">Till exempel `-Path C:\Test\ -Recurse -Include *.txt`</span><span class="sxs-lookup"><span data-stu-id="15a3e-153">For example, `-Path C:\Test\ -Recurse -Include *.txt`</span></span>
- <span data-ttu-id="15a3e-154">Om en avslutande asterisk ( `*` ) inte ingår i parametern **Path** returnerar kommandot inga utdata och återgår till PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="15a3e-154">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the command doesn't return any output and returns to the PowerShell prompt.</span></span> <span data-ttu-id="15a3e-155">Ett exempel är `-Path C:\Test\`.</span><span class="sxs-lookup"><span data-stu-id="15a3e-155">For example, `-Path C:\Test\`.</span></span>

### <span data-ttu-id="15a3e-156">Exempel 5: Hämta underordnade objekt med parametern exclude</span><span class="sxs-lookup"><span data-stu-id="15a3e-156">Example 5: Get child items using the Exclude parameter</span></span>

<span data-ttu-id="15a3e-157">I exemplet visas innehållet i katalogen **C:\Test\Logs**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-157">The example's output shows the contents of the directory **C:\Test\Logs**.</span></span> <span data-ttu-id="15a3e-158">Utdata är en referens för de andra kommandona som använder parametrarna **exclude** och **rekursivt** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-158">The output is a reference for the other commands that use the **Exclude** and **Recurse** parameters.</span></span>

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

<span data-ttu-id="15a3e-159">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-159">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test\Logs`.</span></span>
<span data-ttu-id="15a3e-160">Parametern **exclude** använder jokertecknet asterisk ( `*` ) för att ange vilka filer eller kataloger som börjar med  eller som  ska uteslutas från utdata.</span><span class="sxs-lookup"><span data-stu-id="15a3e-160">The **Exclude** parameter uses the asterisk (`*`) wildcard to specify any files or directories that begin with **A** or **a** are excluded from the output.</span></span>

<span data-ttu-id="15a3e-161">När **exkluderings** parametern används är en efterföljande asterisk ( `*` ) i parametern **Path** valfri.</span><span class="sxs-lookup"><span data-stu-id="15a3e-161">When the **Exclude** parameter is used, a trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="15a3e-162">Exempel: `-Path C:\Test\Logs` eller `-Path C:\Test\Logs\*`.</span><span class="sxs-lookup"><span data-stu-id="15a3e-162">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span>

- <span data-ttu-id="15a3e-163">Om en avslutande asterisk ( `*` ) inte ingår i parametern **Path** , visas innehållet i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-163">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="15a3e-164">Undantag är fil namn eller under Katalog namn som matchar värdet för **exkluderings** parametern.</span><span class="sxs-lookup"><span data-stu-id="15a3e-164">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="15a3e-165">Om en avslutande asterisk ( `*` ) ingår i parametern **Path** , recurses kommandot till **Sök vägs** parameterns under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-165">If a trailing asterisk (`*`) is included in the **Path** parameter, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="15a3e-166">Undantag är fil namn eller under Katalog namn som matchar värdet för **exkluderings** parametern.</span><span class="sxs-lookup"><span data-stu-id="15a3e-166">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="15a3e-167">Om parametern **rekursivt** läggs till i kommandot är rekursion-utdata detsamma, oavsett om **Sök vägs** parametern innehåller en efterföljande asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="15a3e-167">If the **Recurse** parameter is added to the command, the recursion output is the same whether or not the **Path** parameter includes a trailing asterisk (`*`).</span></span>

### <span data-ttu-id="15a3e-168">Exempel 6: Hämta register nycklar från en registrerings data fil</span><span class="sxs-lookup"><span data-stu-id="15a3e-168">Example 6: Get the registry keys from a registry hive</span></span>

<span data-ttu-id="15a3e-169">Det här exemplet hämtar alla register nycklar från `HKEY_LOCAL_MACHINE\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-169">This example gets all the registry keys from `HKEY_LOCAL_MACHINE\HARDWARE`.</span></span>

<span data-ttu-id="15a3e-170">`Get-ChildItem` använder parametern **Path** för att ange register nyckeln `HKLM:\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-170">`Get-ChildItem` uses the **Path** parameter to specify the registry key `HKLM:\HARDWARE`.</span></span> <span data-ttu-id="15a3e-171">Hive-sökvägen och den översta nivån i register nycklar visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-171">The hive's path and top level of registry keys are displayed in the PowerShell console.</span></span>

<span data-ttu-id="15a3e-172">Mer information finns i [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-172">For more information, see [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span></span>

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

<span data-ttu-id="15a3e-173">Det första kommandot visar innehållet i `HKLM:\HARDWARE` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="15a3e-173">The first command shows the contents of the `HKLM:\HARDWARE` registry key.</span></span> <span data-ttu-id="15a3e-174">Parametern **exclud** instruerar `Get-ChildItem` att inte returnera några under nycklar som börjar med `D*` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-174">The **Exclude** parameter tells `Get-ChildItem` not to return any subkeys that start with `D*`.</span></span> <span data-ttu-id="15a3e-175">För närvarande fungerar inte parametern **exclude** på under nycklar, inte objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="15a3e-175">Currently, the **Exclude** parameter only works on subkeys, not item properties.</span></span>

### <span data-ttu-id="15a3e-176">Exempel 7: Hämta alla certifikat med kod signerings utfärdare</span><span class="sxs-lookup"><span data-stu-id="15a3e-176">Example 7: Get all certificates with code-signing authority</span></span>

<span data-ttu-id="15a3e-177">Det här exemplet hämtar varje certifikat i PowerShell- **certifikatet:** enhet som har kod signerings auktoritet.</span><span class="sxs-lookup"><span data-stu-id="15a3e-177">This example gets each certificate in the PowerShell **Cert:** drive that has code-signing authority.</span></span>

<span data-ttu-id="15a3e-178">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange **certifikatet:** Provider.</span><span class="sxs-lookup"><span data-stu-id="15a3e-178">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the **Cert:** provider.</span></span> <span data-ttu-id="15a3e-179">Parametern **rekursivt** söker igenom katalogen som anges av **sökväg** och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-179">The **Recurse** parameter searches the directory specified by **Path** and its subdirectories.</span></span> <span data-ttu-id="15a3e-180">Parametern **CodeSigningCert** hämtar endast certifikat som har kod signerings auktoritet.</span><span class="sxs-lookup"><span data-stu-id="15a3e-180">The **CodeSigningCert** parameter gets only certificates that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

<span data-ttu-id="15a3e-181">Mer information om certifikat leverantören och certifikatet: enhet finns i [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-181">For more information about the Certificate provider and the Cert: drive, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="15a3e-182">Exempel 8: Hämta objekt med hjälp av parametern djup</span><span class="sxs-lookup"><span data-stu-id="15a3e-182">Example 8: Get items using the Depth parameter</span></span>

<span data-ttu-id="15a3e-183">I det här exemplet visas objekten i en katalog och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-183">This example displays the items in a directory and its subdirectories.</span></span> <span data-ttu-id="15a3e-184">Parametern **djup** anger antalet under katalog nivåer som ska tas med i rekursion.</span><span class="sxs-lookup"><span data-stu-id="15a3e-184">The **Depth** parameter determines the number of subdirectory levels to include in the recursion.</span></span> <span data-ttu-id="15a3e-185">Tomma kataloger undantas från utdata.</span><span class="sxs-lookup"><span data-stu-id="15a3e-185">Empty directories are excluded from the output.</span></span>

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

<span data-ttu-id="15a3e-186">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange **C:\Parent**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-186">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify **C:\Parent**.</span></span> <span data-ttu-id="15a3e-187">Parametern **djup** anger två nivåer av rekursion.</span><span class="sxs-lookup"><span data-stu-id="15a3e-187">The **Depth** parameter specifies two levels of recursion.</span></span> <span data-ttu-id="15a3e-188">`Get-ChildItem` visar innehållet i katalogen som anges av parametern **Path** och de två nivåerna av under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-188">`Get-ChildItem` displays the contents of the directory specified by the **Path** parameter and the two levels of subdirectories.</span></span>

### <span data-ttu-id="15a3e-189">Exempel 9: Hämta information om hårda länkar</span><span class="sxs-lookup"><span data-stu-id="15a3e-189">Example 9: Getting hard link information</span></span>

<span data-ttu-id="15a3e-190">I PowerShell 6,2 lades en alternativ vy till för att hämta information om hårda länkar.</span><span class="sxs-lookup"><span data-stu-id="15a3e-190">In PowerShell 6.2, an alternate view was added to get hard link information.</span></span>

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### <span data-ttu-id="15a3e-191">Exempel 9: utdata för operativ system som inte är Windows-operativsystem</span><span class="sxs-lookup"><span data-stu-id="15a3e-191">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="15a3e-192">I PowerShell 7,1 på UNIX `Get-ChildItem` -system tillhandahåller UNIX-liknande utdata:</span><span class="sxs-lookup"><span data-stu-id="15a3e-192">In PowerShell 7.1 on Unix systems, the `Get-ChildItem` provides Unix-like output:</span></span>

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

<span data-ttu-id="15a3e-193">De nya egenskaperna som nu är en del av utdata är:</span><span class="sxs-lookup"><span data-stu-id="15a3e-193">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="15a3e-194">**UnixMode** är de fil behörigheter som representeras i ett UNIX-system</span><span class="sxs-lookup"><span data-stu-id="15a3e-194">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="15a3e-195">**Användaren** är filens ägare</span><span class="sxs-lookup"><span data-stu-id="15a3e-195">**User** is the file owner</span></span>
- <span data-ttu-id="15a3e-196">**Grupp** är grupp ägare</span><span class="sxs-lookup"><span data-stu-id="15a3e-196">**Group** is the group owner</span></span>
- <span data-ttu-id="15a3e-197">**Storlek** är storleken på filen eller katalogen som representeras på ett UNIX-system</span><span class="sxs-lookup"><span data-stu-id="15a3e-197">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="15a3e-198">Den här funktionen har flyttats från experimentell till vanlig i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="15a3e-198">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="15a3e-199">Parameters (Parametrar)</span><span class="sxs-lookup"><span data-stu-id="15a3e-199">Parameters</span></span>

### <span data-ttu-id="15a3e-200">-Attribut</span><span class="sxs-lookup"><span data-stu-id="15a3e-200">-Attributes</span></span>

<span data-ttu-id="15a3e-201">Hämtar filer och mappar med de angivna attributen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-201">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="15a3e-202">Den här parametern stöder alla attribut och gör att du kan ange komplexa kombinationer av attribut.</span><span class="sxs-lookup"><span data-stu-id="15a3e-202">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="15a3e-203">Om du till exempel vill hämta icke-systemfiler (inte kataloger) som är krypterade eller komprimerade skriver du:</span><span class="sxs-lookup"><span data-stu-id="15a3e-203">For example, to get non-system files (not directories) that are encrypted or compressed, type:</span></span>

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

<span data-ttu-id="15a3e-204">Om du vill söka efter filer och mappar med attribut som används ofta använder du parametern **attribut** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-204">To find files and folders with commonly used attributes, use the **Attributes** parameter.</span></span> <span data-ttu-id="15a3e-205">Eller Parameters- **katalogen**, **fil**, **dold**, **ReadOnly** och **system**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-205">Or, the parameters **Directory**, **File**, **Hidden**, **ReadOnly**, and **System**.</span></span>

<span data-ttu-id="15a3e-206">Parametern **attributs** stöder följande egenskaper:</span><span class="sxs-lookup"><span data-stu-id="15a3e-206">The **Attributes** parameter supports the following properties:</span></span>

- <span data-ttu-id="15a3e-207">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="15a3e-207">**Archive**</span></span>
- <span data-ttu-id="15a3e-208">**Komprimerade**</span><span class="sxs-lookup"><span data-stu-id="15a3e-208">**Compressed**</span></span>
- <span data-ttu-id="15a3e-209">**Enhet**</span><span class="sxs-lookup"><span data-stu-id="15a3e-209">**Device**</span></span>
- <span data-ttu-id="15a3e-210">**Katalog**</span><span class="sxs-lookup"><span data-stu-id="15a3e-210">**Directory**</span></span>
- <span data-ttu-id="15a3e-211">**Krypterad**</span><span class="sxs-lookup"><span data-stu-id="15a3e-211">**Encrypted**</span></span>
- <span data-ttu-id="15a3e-212">**Dold**</span><span class="sxs-lookup"><span data-stu-id="15a3e-212">**Hidden**</span></span>
- <span data-ttu-id="15a3e-213">**IntegrityStream**</span><span class="sxs-lookup"><span data-stu-id="15a3e-213">**IntegrityStream**</span></span>
- <span data-ttu-id="15a3e-214">**Normal**</span><span class="sxs-lookup"><span data-stu-id="15a3e-214">**Normal**</span></span>
- <span data-ttu-id="15a3e-215">**NoScrubData**</span><span class="sxs-lookup"><span data-stu-id="15a3e-215">**NoScrubData**</span></span>
- <span data-ttu-id="15a3e-216">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="15a3e-216">**NotContentIndexed**</span></span>
- <span data-ttu-id="15a3e-217">**Offline**</span><span class="sxs-lookup"><span data-stu-id="15a3e-217">**Offline**</span></span>
- <span data-ttu-id="15a3e-218">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="15a3e-218">**ReadOnly**</span></span>
- <span data-ttu-id="15a3e-219">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="15a3e-219">**ReparsePoint**</span></span>
- <span data-ttu-id="15a3e-220">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="15a3e-220">**SparseFile**</span></span>
- <span data-ttu-id="15a3e-221">**System**</span><span class="sxs-lookup"><span data-stu-id="15a3e-221">**System**</span></span>
- <span data-ttu-id="15a3e-222">**Tillfälliga**</span><span class="sxs-lookup"><span data-stu-id="15a3e-222">**Temporary**</span></span>

<span data-ttu-id="15a3e-223">En beskrivning av dessa attribut finns i FileAttributes- [uppräkningen](/dotnet/api/system.io.fileattributes).</span><span class="sxs-lookup"><span data-stu-id="15a3e-223">For a description of these attributes, see the [FileAttributes Enumeration](/dotnet/api/system.io.fileattributes).</span></span>

<span data-ttu-id="15a3e-224">Använd följande operatorer för att kombinera attribut:</span><span class="sxs-lookup"><span data-stu-id="15a3e-224">To combine attributes, use the following operators:</span></span>

- <span data-ttu-id="15a3e-225">`!` Ogiltigt</span><span class="sxs-lookup"><span data-stu-id="15a3e-225">`!` (NOT)</span></span>
- <span data-ttu-id="15a3e-226">`+` SÄRSKILT</span><span class="sxs-lookup"><span data-stu-id="15a3e-226">`+` (AND)</span></span>
- <span data-ttu-id="15a3e-227">`,` ELLER</span><span class="sxs-lookup"><span data-stu-id="15a3e-227">`,` (OR)</span></span>

<span data-ttu-id="15a3e-228">Använd inte blank steg mellan en operator och dess attribut.</span><span class="sxs-lookup"><span data-stu-id="15a3e-228">Don't use spaces between an operator and its attribute.</span></span> <span data-ttu-id="15a3e-229">Blank steg accepteras efter kommatecken.</span><span class="sxs-lookup"><span data-stu-id="15a3e-229">Spaces are accepted after commas.</span></span>

<span data-ttu-id="15a3e-230">Använd följande förkortningar för gemensamma attribut:</span><span class="sxs-lookup"><span data-stu-id="15a3e-230">For common attributes, use the following abbreviations:</span></span>

- <span data-ttu-id="15a3e-231">`D` Katalogen</span><span class="sxs-lookup"><span data-stu-id="15a3e-231">`D` (Directory)</span></span>
- <span data-ttu-id="15a3e-232">`H` Dölja</span><span class="sxs-lookup"><span data-stu-id="15a3e-232">`H` (Hidden)</span></span>
- <span data-ttu-id="15a3e-233">`R` (Skrivskyddad)</span><span class="sxs-lookup"><span data-stu-id="15a3e-233">`R` (Read-only)</span></span>
- <span data-ttu-id="15a3e-234">`S` Säker</span><span class="sxs-lookup"><span data-stu-id="15a3e-234">`S` (System)</span></span>

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-235">-Djup</span><span class="sxs-lookup"><span data-stu-id="15a3e-235">-Depth</span></span>

<span data-ttu-id="15a3e-236">Den här parametern lades till i PowerShell 5,0 och du kan kontrol lera djupet i rekursion.</span><span class="sxs-lookup"><span data-stu-id="15a3e-236">This parameter was added in PowerShell 5.0 and enables you to control the depth of recursion.</span></span> <span data-ttu-id="15a3e-237">Som standard `Get-ChildItem` visas innehållet i den överordnade katalogen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-237">By default, `Get-ChildItem` displays the contents of the parent directory.</span></span> <span data-ttu-id="15a3e-238">Parametern **djup** avgör antalet under katalog nivåer som ingår i rekursion och visar innehållet.</span><span class="sxs-lookup"><span data-stu-id="15a3e-238">The **Depth** parameter determines the number of subdirectory levels that are included in the recursion and displays the contents.</span></span>

<span data-ttu-id="15a3e-239">Innehåller till exempel `Depth 2` **Sök vägs** parameterns katalog, första nivån av under kataloger och den andra nivån av under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-239">For example, `Depth 2` includes the **Path** parameter's directory, first level of subdirectories, and second level of subdirectories.</span></span> <span data-ttu-id="15a3e-240">Som standard inkluderas katalog namn och fil namn i utdata.</span><span class="sxs-lookup"><span data-stu-id="15a3e-240">By default directory names and filenames are included in the output.</span></span>

> [!NOTE]
> <span data-ttu-id="15a3e-241">På en Windows-dator från PowerShell eller **cmd.exe** kan du Visa en grafisk vy över en katalog struktur med kommandot **Tree.com** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-241">On a Windows computer from PowerShell or **cmd.exe**, you can display a graphical view of a directory structure with the **tree.com** command.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-242">-Directory</span><span class="sxs-lookup"><span data-stu-id="15a3e-242">-Directory</span></span>

<span data-ttu-id="15a3e-243">Om du vill hämta en lista över kataloger använder du **katalog** parametern eller parametern **attribut** med **katalog** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-243">To get a list of directories, use the **Directory** parameter or the **Attributes** parameter with the **Directory** property.</span></span> <span data-ttu-id="15a3e-244">Du kan använda parametern **rekursivt** med **Directory**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-244">You can use the **Recurse** parameter with **Directory**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-245">-Undanta</span><span class="sxs-lookup"><span data-stu-id="15a3e-245">-Exclude</span></span>

<span data-ttu-id="15a3e-246">Anger, som en sträng mat ris, en egenskap eller egenskap som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="15a3e-246">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="15a3e-247">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-247">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="15a3e-248">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` eller `A*` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-248">Enter a path element or pattern, such as `*.txt` or `A*`.</span></span> <span data-ttu-id="15a3e-249">Jokertecken accepteras.</span><span class="sxs-lookup"><span data-stu-id="15a3e-249">Wildcard characters are accepted.</span></span>

<span data-ttu-id="15a3e-250">En efterföljande asterisk ( `*` ) i parametern **Path** är valfri.</span><span class="sxs-lookup"><span data-stu-id="15a3e-250">A trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="15a3e-251">Exempel: `-Path C:\Test\Logs` eller `-Path C:\Test\Logs\*`.</span><span class="sxs-lookup"><span data-stu-id="15a3e-251">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span> <span data-ttu-id="15a3e-252">Om en avslutande asterisk ( `*` ) tas med, recurses kommandot till **Sök vägs** parameterns under kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-252">If a trailing asterisk (`*`) is included, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="15a3e-253">Utan asterisk ( `*` ) visas innehållet i **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="15a3e-253">Without the asterisk (`*`), the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="15a3e-254">Mer information finns i exempel 5 och avsnittet om anteckningar.</span><span class="sxs-lookup"><span data-stu-id="15a3e-254">More details are included in Example 5 and the Notes section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="15a3e-255">– Fil</span><span class="sxs-lookup"><span data-stu-id="15a3e-255">-File</span></span>

<span data-ttu-id="15a3e-256">Använd **fil** parametern om du vill hämta en lista över filer.</span><span class="sxs-lookup"><span data-stu-id="15a3e-256">To get a list of files, use the **File** parameter.</span></span> <span data-ttu-id="15a3e-257">Du kan använda parametern **rekursivt** med **filen**.</span><span class="sxs-lookup"><span data-stu-id="15a3e-257">You can use the **Recurse** parameter with **File**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-258">-Filter</span><span class="sxs-lookup"><span data-stu-id="15a3e-258">-Filter</span></span>

<span data-ttu-id="15a3e-259">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="15a3e-259">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="15a3e-260">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder filter.</span><span class="sxs-lookup"><span data-stu-id="15a3e-260">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="15a3e-261">Filter är mer effektiva än andra parametrar.</span><span class="sxs-lookup"><span data-stu-id="15a3e-261">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="15a3e-262">Providern använder filter när-cmdlet: en hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="15a3e-262">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="15a3e-263">Filter strängen skickas till .NET-API: et för att räkna upp filer.</span><span class="sxs-lookup"><span data-stu-id="15a3e-263">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="15a3e-264">API: t stöder bara `*` och `?` jokertecken.</span><span class="sxs-lookup"><span data-stu-id="15a3e-264">The API only supports `*` and `?` wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="15a3e-265">-FollowSymlink</span><span class="sxs-lookup"><span data-stu-id="15a3e-265">-FollowSymlink</span></span>

<span data-ttu-id="15a3e-266">Som standard `Get-ChildItem` visar cmdlet symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte till dem.</span><span class="sxs-lookup"><span data-stu-id="15a3e-266">By default, the `Get-ChildItem` cmdlet displays symbolic links to directories found during recursion, but doesn't recurse into them.</span></span> <span data-ttu-id="15a3e-267">Använd parametern **FollowSymlink** för att söka i de kataloger som är riktade mot de symboliska länkarna.</span><span class="sxs-lookup"><span data-stu-id="15a3e-267">Use the **FollowSymlink** parameter to search the directories that target those symbolic links.</span></span> <span data-ttu-id="15a3e-268">**FollowSymlink** är en dynamisk parameter och stöds bara i **fil** tjänst leverantören.</span><span class="sxs-lookup"><span data-stu-id="15a3e-268">The **FollowSymlink** is a dynamic parameter and is supported only in the **FileSystem** provider.</span></span>

<span data-ttu-id="15a3e-269">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="15a3e-269">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-270">-Force</span><span class="sxs-lookup"><span data-stu-id="15a3e-270">-Force</span></span>

<span data-ttu-id="15a3e-271">Tillåter att cmdleten hämtar objekt som annars inte kan nås av användaren, till exempel dolda filer eller systemfiler.</span><span class="sxs-lookup"><span data-stu-id="15a3e-271">Allows the cmdlet to get items that otherwise can't be accessed by the user, such as hidden or system files.</span></span> <span data-ttu-id="15a3e-272">Parametern **Force** åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="15a3e-272">The **Force** parameter doesn't override security restrictions.</span></span> <span data-ttu-id="15a3e-273">Implementeringen varierar mellan olika leverantörer.</span><span class="sxs-lookup"><span data-stu-id="15a3e-273">Implementation varies among providers.</span></span> <span data-ttu-id="15a3e-274">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-274">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-275">– Dold</span><span class="sxs-lookup"><span data-stu-id="15a3e-275">-Hidden</span></span>

<span data-ttu-id="15a3e-276">Om du bara vill ha dolda objekt använder du parametern **Hidden** eller parametern **attribut** med egenskapen **Hidden** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-276">To get only hidden items, use the **Hidden** parameter or the **Attributes** parameter with the **Hidden** property.</span></span> <span data-ttu-id="15a3e-277">Som standard `Get-ChildItem` visar inte dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="15a3e-277">By default, `Get-ChildItem` doesn't display hidden items.</span></span> <span data-ttu-id="15a3e-278">Använd parametern **Force** för att hämta dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="15a3e-278">Use the **Force** parameter to get hidden items.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-279">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="15a3e-279">-Include</span></span>

<span data-ttu-id="15a3e-280">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="15a3e-280">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="15a3e-281">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-281">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="15a3e-282">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-282">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="15a3e-283">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="15a3e-283">Wildcard characters are permitted.</span></span> <span data-ttu-id="15a3e-284">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-284">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="15a3e-285">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="15a3e-285">-LiteralPath</span></span>

<span data-ttu-id="15a3e-286">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="15a3e-286">Specifies a path to one or more locations.</span></span> <span data-ttu-id="15a3e-287">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="15a3e-287">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="15a3e-288">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="15a3e-288">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="15a3e-289">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="15a3e-289">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="15a3e-290">Enkla citat tecken anger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="15a3e-290">Single quotation marks tell PowerShell to not interpret any characters as escape sequences.</span></span>

<span data-ttu-id="15a3e-291">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-291">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-292">-Name</span><span class="sxs-lookup"><span data-stu-id="15a3e-292">-Name</span></span>

<span data-ttu-id="15a3e-293">Hämtar endast namnen på objekten på platsen.</span><span class="sxs-lookup"><span data-stu-id="15a3e-293">Gets only the names of the items in the location.</span></span> <span data-ttu-id="15a3e-294">Utdata är ett sträng objekt som kan skickas ned pipelinen till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="15a3e-294">The output is a string object that can be sent down the pipeline to other commands.</span></span> <span data-ttu-id="15a3e-295">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="15a3e-295">Wildcards are permitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="15a3e-296">-Path</span><span class="sxs-lookup"><span data-stu-id="15a3e-296">-Path</span></span>

<span data-ttu-id="15a3e-297">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="15a3e-297">Specifies a path to one or more locations.</span></span> <span data-ttu-id="15a3e-298">Jokertecken accepteras.</span><span class="sxs-lookup"><span data-stu-id="15a3e-298">Wildcards are accepted.</span></span> <span data-ttu-id="15a3e-299">Standard platsen är den aktuella katalogen ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="15a3e-299">The default location is the current directory (`.`).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="15a3e-300">– ReadOnly</span><span class="sxs-lookup"><span data-stu-id="15a3e-300">-ReadOnly</span></span>

<span data-ttu-id="15a3e-301">Om du bara vill hämta skrivskyddade objekt kan du använda **ReadOnly** -parametern eller egenskapen **attributs** **ReadOnly** .</span><span class="sxs-lookup"><span data-stu-id="15a3e-301">To get only read-only items, use the **ReadOnly** parameter or the **Attributes** parameter **ReadOnly** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-302">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="15a3e-302">-Recurse</span></span>

<span data-ttu-id="15a3e-303">Hämtar objekten på de angivna platserna och i alla underordnade objekt på platserna.</span><span class="sxs-lookup"><span data-stu-id="15a3e-303">Gets the items in the specified locations and in all child items of the locations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-304">– System</span><span class="sxs-lookup"><span data-stu-id="15a3e-304">-System</span></span>

<span data-ttu-id="15a3e-305">Hämtar endast systemfiler och kataloger.</span><span class="sxs-lookup"><span data-stu-id="15a3e-305">Gets only system files and directories.</span></span> <span data-ttu-id="15a3e-306">Om du bara vill hämta systemfiler och mappar använder du **system** parametern eller **attributets** parameter **system** egenskap.</span><span class="sxs-lookup"><span data-stu-id="15a3e-306">To get only system files and folders, use the **System** parameter or **Attributes** parameter **System** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15a3e-307">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15a3e-307">CommonParameters</span></span>

<span data-ttu-id="15a3e-308">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15a3e-308">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15a3e-309">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="15a3e-309">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15a3e-310">INDATA</span><span class="sxs-lookup"><span data-stu-id="15a3e-310">INPUTS</span></span>

### <span data-ttu-id="15a3e-311">System. String</span><span class="sxs-lookup"><span data-stu-id="15a3e-311">System.String</span></span>

<span data-ttu-id="15a3e-312">Du kan skicka vidare en sträng som innehåller en sökväg till `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-312">You can pipe a string that contains a path to `Get-ChildItem`.</span></span>

## <span data-ttu-id="15a3e-313">UTDATA</span><span class="sxs-lookup"><span data-stu-id="15a3e-313">OUTPUTS</span></span>

### <span data-ttu-id="15a3e-314">System. Object</span><span class="sxs-lookup"><span data-stu-id="15a3e-314">System.Object</span></span>

<span data-ttu-id="15a3e-315">Vilken typ av objekt som `Get-ChildItem` returneras bestäms av objekten i providerns enhets Sök väg.</span><span class="sxs-lookup"><span data-stu-id="15a3e-315">The type of object that `Get-ChildItem` returns is determined by the objects in the provider drive path.</span></span>

### <span data-ttu-id="15a3e-316">System. String</span><span class="sxs-lookup"><span data-stu-id="15a3e-316">System.String</span></span>

<span data-ttu-id="15a3e-317">Om du använder parametern **Name** `Get-ChildItem` returneras objekt namnen som strängar.</span><span class="sxs-lookup"><span data-stu-id="15a3e-317">If you use the **Name** parameter, `Get-ChildItem` returns the object names as strings.</span></span>

## <span data-ttu-id="15a3e-318">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="15a3e-318">NOTES</span></span>

- <span data-ttu-id="15a3e-319">`Get-ChildItem` kan köras med något av de inbyggda aliasen,, `ls` `dir` och `gci` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-319">`Get-ChildItem` can be run using any of the built-in aliases, `ls`, `dir`, and `gci`.</span></span> <span data-ttu-id="15a3e-320">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-320">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="15a3e-321">`Get-ChildItem` som standard visas inte dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="15a3e-321">`Get-ChildItem` doesn't get hidden items by default.</span></span> <span data-ttu-id="15a3e-322">Använd parametern **Force** för att hämta dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="15a3e-322">To get hidden items, use the **Force** parameter.</span></span>
- <span data-ttu-id="15a3e-323">`Get-ChildItem`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="15a3e-323">The `Get-ChildItem` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="15a3e-324">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="15a3e-324">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="15a3e-325">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="15a3e-325">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="15a3e-326">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="15a3e-326">RELATED LINKS</span></span>

[<span data-ttu-id="15a3e-327">about_Certificate_Provider</span><span class="sxs-lookup"><span data-stu-id="15a3e-327">about_Certificate_Provider</span></span>](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[<span data-ttu-id="15a3e-328">about_Providers</span><span class="sxs-lookup"><span data-stu-id="15a3e-328">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="15a3e-329">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="15a3e-329">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="15a3e-330">about_Registry_Provider</span><span class="sxs-lookup"><span data-stu-id="15a3e-330">about_Registry_Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[<span data-ttu-id="15a3e-331">-Objekt</span><span class="sxs-lookup"><span data-stu-id="15a3e-331">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="15a3e-332">Get-alias</span><span class="sxs-lookup"><span data-stu-id="15a3e-332">Get-Alias</span></span>](../Microsoft.PowerShell.Utility/Get-Alias.md)

[<span data-ttu-id="15a3e-333">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="15a3e-333">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="15a3e-334">Get-location</span><span class="sxs-lookup"><span data-stu-id="15a3e-334">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="15a3e-335">Hämta process</span><span class="sxs-lookup"><span data-stu-id="15a3e-335">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="15a3e-336">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="15a3e-336">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="15a3e-337">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="15a3e-337">Split-Path</span></span>](Split-Path.md)

