---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 4c247513ab06f1bcba648a62969fb7d458e0d35d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709487"
---
# <span data-ttu-id="788f9-102">New-Item</span><span class="sxs-lookup"><span data-stu-id="788f9-102">New-Item</span></span>

## <span data-ttu-id="788f9-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="788f9-103">SYNOPSIS</span></span>
<span data-ttu-id="788f9-104">Skapar ett nytt objekt.</span><span class="sxs-lookup"><span data-stu-id="788f9-104">Creates a new item.</span></span>

## <span data-ttu-id="788f9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="788f9-105">SYNTAX</span></span>

### <span data-ttu-id="788f9-106">pathSet (standard)</span><span class="sxs-lookup"><span data-stu-id="788f9-106">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="788f9-107">nameSet</span><span class="sxs-lookup"><span data-stu-id="788f9-107">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="788f9-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="788f9-108">DESCRIPTION</span></span>

<span data-ttu-id="788f9-109">`New-Item`Cmdleten skapar ett nytt objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="788f9-109">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="788f9-110">Vilka typer av objekt som kan skapas beror på objektets plats.</span><span class="sxs-lookup"><span data-stu-id="788f9-110">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="788f9-111">I fil systemet skapas till exempel `New-Item` filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="788f9-111">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="788f9-112">I registret `New-Item` skapas register nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="788f9-112">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="788f9-113">`New-Item` kan också ange värdet för de objekt som skapas.</span><span class="sxs-lookup"><span data-stu-id="788f9-113">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="788f9-114">Till exempel, när den skapar en ny fil, `New-Item` kan lägga till det ursprungliga innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="788f9-114">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="788f9-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="788f9-115">EXAMPLES</span></span>

### <span data-ttu-id="788f9-116">Exempel 1: skapa en fil i den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="788f9-116">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="788f9-117">Det här kommandot skapar en textfil med namnet "testfile1.txt" i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="788f9-117">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="788f9-118">Punkten (".") i värdet för parametern **Path** anger den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="788f9-118">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="788f9-119">Den citerade text som följer **värde** parametern läggs till i filen som innehåll.</span><span class="sxs-lookup"><span data-stu-id="788f9-119">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="788f9-120">Exempel 2: skapa en katalog</span><span class="sxs-lookup"><span data-stu-id="788f9-120">Example 2: Create a directory</span></span>

<span data-ttu-id="788f9-121">Det här kommandot skapar en katalog med namnet "LogFiles" på `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="788f9-121">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="788f9-122">Parametern **itemType** anger att det nya objektet är en katalog, inte en fil eller något annat fil Systems objekt.</span><span class="sxs-lookup"><span data-stu-id="788f9-122">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="788f9-123">Exempel 3: skapa en profil</span><span class="sxs-lookup"><span data-stu-id="788f9-123">Example 3: Create a profile</span></span>

<span data-ttu-id="788f9-124">Det här kommandot skapar en PowerShell-profil i den sökväg som anges av `$profile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="788f9-124">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="788f9-125">Du kan använda profiler för att anpassa PowerShell.</span><span class="sxs-lookup"><span data-stu-id="788f9-125">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="788f9-126">`$profile` är en automatisk (inbyggd) variabel som lagrar sökvägen och fil namnet för profilen "CurrentUser/CurrentHost".</span><span class="sxs-lookup"><span data-stu-id="788f9-126">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="788f9-127">Profilen finns inte som standard, även om PowerShell lagrar en sökväg och ett fil namn för den.</span><span class="sxs-lookup"><span data-stu-id="788f9-127">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="788f9-128">I det här kommandot `$profile` representerar variabeln sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="788f9-128">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="788f9-129">Parametern **itemType** anger att kommandot skapar en fil.</span><span class="sxs-lookup"><span data-stu-id="788f9-129">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="788f9-130">Med parametern **Force** kan du skapa en fil i profil Sök vägen, även om katalogerna i sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="788f9-130">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="788f9-131">När du har skapat en profil kan du ange alias, funktioner och skript i profilen för att anpassa ditt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="788f9-131">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="788f9-132">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) och [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-132">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### <span data-ttu-id="788f9-133">Exempel 4: skapa en katalog i en annan katalog</span><span class="sxs-lookup"><span data-stu-id="788f9-133">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="788f9-134">I det här exemplet skapas en ny skript katalog i katalogen "C:\PS-Test".</span><span class="sxs-lookup"><span data-stu-id="788f9-134">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="788f9-135">Namnet på det nya katalog objektet, "skript", ingår i värdet för parametern **Path** i stället för att anges i värdet för **namnet**.</span><span class="sxs-lookup"><span data-stu-id="788f9-135">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name**.</span></span> <span data-ttu-id="788f9-136">Som anges av syntaxen är kommando formuläret giltiga.</span><span class="sxs-lookup"><span data-stu-id="788f9-136">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="788f9-137">Exempel 5: skapa flera filer</span><span class="sxs-lookup"><span data-stu-id="788f9-137">Example 5: Create multiple files</span></span>

<span data-ttu-id="788f9-138">I det här exemplet skapas filer i två olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="788f9-138">This example creates files in two different directories.</span></span> <span data-ttu-id="788f9-139">Eftersom **sökvägen** tar flera strängar kan du använda den för att skapa flera objekt.</span><span class="sxs-lookup"><span data-stu-id="788f9-139">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="788f9-140">Exempel 6: Använd jokertecken för att skapa filer i flera kataloger</span><span class="sxs-lookup"><span data-stu-id="788f9-140">Example 6: Use wildcards to create files in multiple directories</span></span>

<span data-ttu-id="788f9-141">`New-Item`Cmdleten stöder jokertecken i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="788f9-141">The `New-Item` cmdlet supports wildcards in the **Path** parameter.</span></span> <span data-ttu-id="788f9-142">Följande kommando skapar en `temp.txt` fil i alla kataloger som anges av jokertecknen i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="788f9-142">The following command creates a `temp.txt` file in all of the directories specified by the wildcards in the **Path** parameter.</span></span>

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

<span data-ttu-id="788f9-143">`Get-ChildItem`Cmdleten visar tre kataloger under `C:\Temp` katalogen.</span><span class="sxs-lookup"><span data-stu-id="788f9-143">The `Get-ChildItem` cmdlet shows three directories under the `C:\Temp` directory.</span></span> <span data-ttu-id="788f9-144">Med jokertecken `New-Item` skapar cmdleten en `temp.txt` fil i alla kataloger under den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="788f9-144">Using wildcards the `New-Item` cmdlet creates a `temp.txt` file in all of the directories under the current directory.</span></span> <span data-ttu-id="788f9-145">`New-Item`Cmdleten matar ut de objekt som du har skapat, vilket är skickas för `Select-Object` att verifiera Sök vägarna för de filer som skapats nyligen.</span><span class="sxs-lookup"><span data-stu-id="788f9-145">The `New-Item` cmdlet outputs the items you created, which is piped to `Select-Object` to verify the paths of the newly created files.</span></span>

### <span data-ttu-id="788f9-146">Exempel 7: skapa en symbolisk länk till en fil eller mapp</span><span class="sxs-lookup"><span data-stu-id="788f9-146">Example 7: Create a symbolic link to a file or folder</span></span>

<span data-ttu-id="788f9-147">I det här exemplet skapas en symbolisk länk till Notice.txt-filen i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="788f9-147">This example creates a symbolic link to the Notice.txt file in the current folder.</span></span>

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

<span data-ttu-id="788f9-148">I det här exemplet är **målet** ett alias för **värde** parametern.</span><span class="sxs-lookup"><span data-stu-id="788f9-148">In this example, **Target** is an alias for the **Value** parameter.</span></span> <span data-ttu-id="788f9-149">Målet för den symboliska länken kan vara en relativ sökväg.</span><span class="sxs-lookup"><span data-stu-id="788f9-149">The target of the symbolic link can be a relative path.</span></span> <span data-ttu-id="788f9-150">Innan PowerShell v 6.2 måste målet vara en fullständigt kvalificerad sökväg.</span><span class="sxs-lookup"><span data-stu-id="788f9-150">Prior to PowerShell v6.2, the target must be a fully-qualified path.</span></span>

<span data-ttu-id="788f9-151">Från och med PowerShell 7,1 kan du nu skapa en **SymbolicLink** till en mapp i Windows med hjälp av en relativ sökväg.</span><span class="sxs-lookup"><span data-stu-id="788f9-151">Beginning in PowerShell 7.1, you can now create to a **SymbolicLink** to a folder on Windows using a relative path.</span></span>

### <span data-ttu-id="788f9-152">Exempel 8: Använd parametern-Force för att försöka återskapa mappar</span><span class="sxs-lookup"><span data-stu-id="788f9-152">Example 8: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="788f9-153">I det här exemplet skapas en mapp med en fil i.</span><span class="sxs-lookup"><span data-stu-id="788f9-153">This example creates a folder with a file inside.</span></span> <span data-ttu-id="788f9-154">Försöker sedan skapa samma mapp med `-Force` .</span><span class="sxs-lookup"><span data-stu-id="788f9-154">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="788f9-155">Mappen skrivs inte över, men returnerar bara det befintliga objektet med filen som skapats intakt.</span><span class="sxs-lookup"><span data-stu-id="788f9-155">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### <span data-ttu-id="788f9-156">Exempel 9: Använd parametern-Force för att skriva över befintliga filer</span><span class="sxs-lookup"><span data-stu-id="788f9-156">Example 9: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="788f9-157">Det här exemplet skapar en fil med ett värde och återskapar sedan filen med hjälp av `-Force` .</span><span class="sxs-lookup"><span data-stu-id="788f9-157">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="788f9-158">Den befintliga filen skrivs över och den kommer att förlora innehållet som du kan se i egenskapen length</span><span class="sxs-lookup"><span data-stu-id="788f9-158">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> <span data-ttu-id="788f9-159">När `New-Item` du använder med `-Force` växeln för att skapa register nycklar, fungerar kommandot likadant som när du skriver över en fil.</span><span class="sxs-lookup"><span data-stu-id="788f9-159">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="788f9-160">Om register nyckeln redan finns kommer nyckeln och alla egenskaper och värden att skrivas över med en tom register nyckel.</span><span class="sxs-lookup"><span data-stu-id="788f9-160">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="788f9-161">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="788f9-161">PARAMETERS</span></span>

### <span data-ttu-id="788f9-162">-Credential</span><span class="sxs-lookup"><span data-stu-id="788f9-162">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="788f9-163">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="788f9-163">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="788f9-164">Använd för att personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="788f9-164">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-165">-Force</span><span class="sxs-lookup"><span data-stu-id="788f9-165">-Force</span></span>

<span data-ttu-id="788f9-166">Tvingar denna cmdlet att skapa ett objekt som skriver över ett befintligt skrivskyddat objekt.</span><span class="sxs-lookup"><span data-stu-id="788f9-166">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="788f9-167">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="788f9-167">Implementation varies from provider to provider.</span></span> <span data-ttu-id="788f9-168">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="788f9-168">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="788f9-169">-ItemType</span><span class="sxs-lookup"><span data-stu-id="788f9-169">-ItemType</span></span>

<span data-ttu-id="788f9-170">Anger providerns angivna typ för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="788f9-170">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="788f9-171">De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.</span><span class="sxs-lookup"><span data-stu-id="788f9-171">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="788f9-172">Om platsen finns i en `FileSystem` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="788f9-172">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="788f9-173">Fil</span><span class="sxs-lookup"><span data-stu-id="788f9-173">File</span></span>
- <span data-ttu-id="788f9-174">Katalog</span><span class="sxs-lookup"><span data-stu-id="788f9-174">Directory</span></span>
- <span data-ttu-id="788f9-175">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="788f9-175">SymbolicLink</span></span>
- <span data-ttu-id="788f9-176">Knutpunkt</span><span class="sxs-lookup"><span data-stu-id="788f9-176">Junction</span></span>
- <span data-ttu-id="788f9-177">HardLink</span><span class="sxs-lookup"><span data-stu-id="788f9-177">HardLink</span></span>

> [!NOTE]
> <span data-ttu-id="788f9-178">Att skapa en `SymbolicLink` typ i Windows kräver utökade privilegier som administratör.</span><span class="sxs-lookup"><span data-stu-id="788f9-178">Creating a `SymbolicLink` type on Windows requires elevation as administrator.</span></span> <span data-ttu-id="788f9-179">Windows 10 (version 14972 eller senare) med utvecklarläge aktiverat kräver dock inte längre utökade privilegier för att skapa symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="788f9-179">However, Windows 10 (build 14972 or newer) with Developer Mode enabled no longer requires elevation creating symbolic links.</span></span>

<span data-ttu-id="788f9-180">I en `Certificate` enhet är dessa värden som du kan ange:</span><span class="sxs-lookup"><span data-stu-id="788f9-180">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="788f9-181">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="788f9-181">Certificate Provider</span></span>
- <span data-ttu-id="788f9-182">Certifikat</span><span class="sxs-lookup"><span data-stu-id="788f9-182">Certificate</span></span>
- <span data-ttu-id="788f9-183">Lagringsplats</span><span class="sxs-lookup"><span data-stu-id="788f9-183">Store</span></span>
- <span data-ttu-id="788f9-184">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="788f9-184">StoreLocation</span></span>

<span data-ttu-id="788f9-185">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-185">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-186">-Name</span><span class="sxs-lookup"><span data-stu-id="788f9-186">-Name</span></span>

<span data-ttu-id="788f9-187">Anger namnet på det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="788f9-187">Specifies the name of the new item.</span></span> <span data-ttu-id="788f9-188">Du kan ange namnet på det nya objektet i parametervärdet för **namn** eller **sökväg** och du kan ange sökvägen till det nya objektet i värdet **namn** eller **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="788f9-188">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="788f9-189">Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="788f9-189">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-190">-Path</span><span class="sxs-lookup"><span data-stu-id="788f9-190">-Path</span></span>

<span data-ttu-id="788f9-191">Anger sökvägen till platsen för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="788f9-191">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="788f9-192">Standardvärdet är den aktuella platsen när **sökvägen** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="788f9-192">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="788f9-193">Du kan ange namnet på det nya objektet i **namn** eller ta med det i **sökvägen**.</span><span class="sxs-lookup"><span data-stu-id="788f9-193">You can specify the name of the new item in **Name**, or include it in **Path**.</span></span> <span data-ttu-id="788f9-194">Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="788f9-194">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="788f9-195">För den här cmdleten fungerar **Sök vägs** parametern som parametern **LiteralPath** för andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="788f9-195">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="788f9-196">Jokertecken tolkas inte.</span><span class="sxs-lookup"><span data-stu-id="788f9-196">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="788f9-197">Alla tecken skickas till platsens Provider.</span><span class="sxs-lookup"><span data-stu-id="788f9-197">All characters are passed to the location's provider.</span></span> <span data-ttu-id="788f9-198">Providern kanske inte har stöd för alla tecken.</span><span class="sxs-lookup"><span data-stu-id="788f9-198">The provider may not support all characters.</span></span> <span data-ttu-id="788f9-199">Du kan till exempel inte skapa ett fil namn som innehåller en asterisk ( `*` )-bokstav.</span><span class="sxs-lookup"><span data-stu-id="788f9-199">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-200">-Värde</span><span class="sxs-lookup"><span data-stu-id="788f9-200">-Value</span></span>

<span data-ttu-id="788f9-201">Anger värdet för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="788f9-201">Specifies the value of the new item.</span></span> <span data-ttu-id="788f9-202">Du kan också skicka ett värde till `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="788f9-202">You can also pipe a value to `New-Item`.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-203">-Confirm</span><span class="sxs-lookup"><span data-stu-id="788f9-203">-Confirm</span></span>

<span data-ttu-id="788f9-204">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="788f9-204">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-205">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="788f9-205">-WhatIf</span></span>

<span data-ttu-id="788f9-206">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="788f9-206">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="788f9-207">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="788f9-207">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="788f9-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="788f9-208">CommonParameters</span></span>

<span data-ttu-id="788f9-209">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="788f9-209">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="788f9-210">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-210">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="788f9-211">INDATA</span><span class="sxs-lookup"><span data-stu-id="788f9-211">INPUTS</span></span>

### <span data-ttu-id="788f9-212">System. Object</span><span class="sxs-lookup"><span data-stu-id="788f9-212">System.Object</span></span>

<span data-ttu-id="788f9-213">Du kan skicka ett värde för det nya objektet till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="788f9-213">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="788f9-214">UTDATA</span><span class="sxs-lookup"><span data-stu-id="788f9-214">OUTPUTS</span></span>

### <span data-ttu-id="788f9-215">System. Object</span><span class="sxs-lookup"><span data-stu-id="788f9-215">System.Object</span></span>

<span data-ttu-id="788f9-216">Den här cmdleten returnerar det objekt som skapas.</span><span class="sxs-lookup"><span data-stu-id="788f9-216">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="788f9-217">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="788f9-217">NOTES</span></span>

<span data-ttu-id="788f9-218">`New-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="788f9-218">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="788f9-219">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="788f9-219">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="788f9-220">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-220">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="788f9-221">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="788f9-221">RELATED LINKS</span></span>

[<span data-ttu-id="788f9-222">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-222">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="788f9-223">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-223">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="788f9-224">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-224">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="788f9-225">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-225">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="788f9-226">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-226">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="788f9-227">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-227">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="788f9-228">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-228">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="788f9-229">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="788f9-229">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="788f9-230">about_Providers</span><span class="sxs-lookup"><span data-stu-id="788f9-230">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

