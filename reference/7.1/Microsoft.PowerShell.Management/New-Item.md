---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 50a7dba8c4e9cb1cfabd42f39e9fdfb43f22f9b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263306"
---
# <span data-ttu-id="9c69a-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="9c69a-103">New-Item</span></span>

## <span data-ttu-id="9c69a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9c69a-104">SYNOPSIS</span></span>
<span data-ttu-id="9c69a-105">Skapar ett nytt objekt.</span><span class="sxs-lookup"><span data-stu-id="9c69a-105">Creates a new item.</span></span>

## <span data-ttu-id="9c69a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c69a-106">SYNTAX</span></span>

### <span data-ttu-id="9c69a-107">pathSet (standard)</span><span class="sxs-lookup"><span data-stu-id="9c69a-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c69a-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="9c69a-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9c69a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9c69a-109">DESCRIPTION</span></span>

<span data-ttu-id="9c69a-110">`New-Item`Cmdleten skapar ett nytt objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="9c69a-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="9c69a-111">Vilka typer av objekt som kan skapas beror på objektets plats.</span><span class="sxs-lookup"><span data-stu-id="9c69a-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="9c69a-112">I fil systemet skapas till exempel `New-Item` filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="9c69a-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="9c69a-113">I registret `New-Item` skapas register nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="9c69a-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="9c69a-114">`New-Item` kan också ange värdet för de objekt som skapas.</span><span class="sxs-lookup"><span data-stu-id="9c69a-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="9c69a-115">Till exempel, när den skapar en ny fil, `New-Item` kan lägga till det ursprungliga innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="9c69a-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9c69a-116">EXAMPLES</span></span>

### <span data-ttu-id="9c69a-117">Exempel 1: skapa en fil i den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="9c69a-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="9c69a-118">Det här kommandot skapar en textfil med namnet "testfile1.txt" i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="9c69a-119">Punkten (".") i värdet för parametern **Path** anger den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="9c69a-120">Den citerade text som följer **värde** parametern läggs till i filen som innehåll.</span><span class="sxs-lookup"><span data-stu-id="9c69a-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="9c69a-121">Exempel 2: skapa en katalog</span><span class="sxs-lookup"><span data-stu-id="9c69a-121">Example 2: Create a directory</span></span>

<span data-ttu-id="9c69a-122">Det här kommandot skapar en katalog med namnet "LogFiles" på `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="9c69a-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="9c69a-123">Parametern **itemType** anger att det nya objektet är en katalog, inte en fil eller något annat fil Systems objekt.</span><span class="sxs-lookup"><span data-stu-id="9c69a-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="9c69a-124">Exempel 3: skapa en profil</span><span class="sxs-lookup"><span data-stu-id="9c69a-124">Example 3: Create a profile</span></span>

<span data-ttu-id="9c69a-125">Det här kommandot skapar en PowerShell-profil i den sökväg som anges av `$profile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9c69a-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="9c69a-126">Du kan använda profiler för att anpassa PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c69a-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="9c69a-127">`$profile` är en automatisk (inbyggd) variabel som lagrar sökvägen och fil namnet för profilen "CurrentUser/CurrentHost".</span><span class="sxs-lookup"><span data-stu-id="9c69a-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="9c69a-128">Profilen finns inte som standard, även om PowerShell lagrar en sökväg och ett fil namn för den.</span><span class="sxs-lookup"><span data-stu-id="9c69a-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="9c69a-129">I det här kommandot `$profile` representerar variabeln sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="9c69a-130">Parametern **itemType** anger att kommandot skapar en fil.</span><span class="sxs-lookup"><span data-stu-id="9c69a-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="9c69a-131">Med parametern **Force** kan du skapa en fil i profil Sök vägen, även om katalogerna i sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="9c69a-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="9c69a-132">När du har skapat en profil kan du ange alias, funktioner och skript i profilen för att anpassa ditt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="9c69a-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="9c69a-133">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) och [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9c69a-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### <span data-ttu-id="9c69a-134">Exempel 4: skapa en katalog i en annan katalog</span><span class="sxs-lookup"><span data-stu-id="9c69a-134">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="9c69a-135">I det här exemplet skapas en ny skript katalog i katalogen "C:\PS-Test".</span><span class="sxs-lookup"><span data-stu-id="9c69a-135">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="9c69a-136">Namnet på det nya katalog objektet, "skript", ingår i värdet för parametern **Path** i stället för att anges i värdet för **namnet**.</span><span class="sxs-lookup"><span data-stu-id="9c69a-136">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name**.</span></span> <span data-ttu-id="9c69a-137">Som anges av syntaxen är kommando formuläret giltiga.</span><span class="sxs-lookup"><span data-stu-id="9c69a-137">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="9c69a-138">Exempel 5: skapa flera filer</span><span class="sxs-lookup"><span data-stu-id="9c69a-138">Example 5: Create multiple files</span></span>

<span data-ttu-id="9c69a-139">I det här exemplet skapas filer i två olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="9c69a-139">This example creates files in two different directories.</span></span> <span data-ttu-id="9c69a-140">Eftersom **sökvägen** tar flera strängar kan du använda den för att skapa flera objekt.</span><span class="sxs-lookup"><span data-stu-id="9c69a-140">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="9c69a-141">Exempel 6: Använd jokertecken för att skapa filer i flera kataloger</span><span class="sxs-lookup"><span data-stu-id="9c69a-141">Example 6: Use wildcards to create files in multiple directories</span></span>

<span data-ttu-id="9c69a-142">`New-Item`Cmdleten stöder jokertecken i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c69a-142">The `New-Item` cmdlet supports wildcards in the **Path** parameter.</span></span> <span data-ttu-id="9c69a-143">Följande kommando skapar en `temp.txt` fil i alla kataloger som anges av jokertecknen i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c69a-143">The following command creates a `temp.txt` file in all of the directories specified by the wildcards in the **Path** parameter.</span></span>

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

<span data-ttu-id="9c69a-144">`Get-ChildItem`Cmdleten visar tre kataloger under `C:\Temp` katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-144">The `Get-ChildItem` cmdlet shows three directories under the `C:\Temp` directory.</span></span> <span data-ttu-id="9c69a-145">Med jokertecken `New-Item` skapar cmdleten en `temp.txt` fil i alla kataloger under den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-145">Using wildcards the `New-Item` cmdlet creates a `temp.txt` file in all of the directories under the current directory.</span></span> <span data-ttu-id="9c69a-146">`New-Item`Cmdleten matar ut de objekt som du har skapat, vilket är skickas för `Select-Object` att verifiera Sök vägarna för de filer som skapats nyligen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-146">The `New-Item` cmdlet outputs the items you created, which is piped to `Select-Object` to verify the paths of the newly created files.</span></span>

### <span data-ttu-id="9c69a-147">Exempel 7: skapa en symbolisk länk till en fil eller mapp</span><span class="sxs-lookup"><span data-stu-id="9c69a-147">Example 7: Create a symbolic link to a file or folder</span></span>

<span data-ttu-id="9c69a-148">I det här exemplet skapas en symbolisk länk till Notice.txt-filen i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="9c69a-148">This example creates a symbolic link to the Notice.txt file in the current folder.</span></span>

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

<span data-ttu-id="9c69a-149">I det här exemplet är **målet** ett alias för **värde** parametern.</span><span class="sxs-lookup"><span data-stu-id="9c69a-149">In this example, **Target** is an alias for the **Value** parameter.</span></span> <span data-ttu-id="9c69a-150">Målet för den symboliska länken kan vara en relativ sökväg.</span><span class="sxs-lookup"><span data-stu-id="9c69a-150">The target of the symbolic link can be a relative path.</span></span> <span data-ttu-id="9c69a-151">Innan PowerShell v 6.2 måste målet vara en fullständigt kvalificerad sökväg.</span><span class="sxs-lookup"><span data-stu-id="9c69a-151">Prior to PowerShell v6.2, the target must be a fully-qualified path.</span></span>

<span data-ttu-id="9c69a-152">Från och med PowerShell 7,1 kan du nu skapa en **SymbolicLink** till en mapp i Windows med hjälp av en relativ sökväg.</span><span class="sxs-lookup"><span data-stu-id="9c69a-152">Beginning in PowerShell 7.1, you can now create to a **SymbolicLink** to a folder on Windows using a relative path.</span></span>

### <span data-ttu-id="9c69a-153">Exempel 8: Använd parametern-Force för att försöka återskapa mappar</span><span class="sxs-lookup"><span data-stu-id="9c69a-153">Example 8: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="9c69a-154">I det här exemplet skapas en mapp med en fil i.</span><span class="sxs-lookup"><span data-stu-id="9c69a-154">This example creates a folder with a file inside.</span></span> <span data-ttu-id="9c69a-155">Försöker sedan skapa samma mapp med `-Force` .</span><span class="sxs-lookup"><span data-stu-id="9c69a-155">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="9c69a-156">Mappen skrivs inte över, men returnerar bara det befintliga objektet med filen som skapats intakt.</span><span class="sxs-lookup"><span data-stu-id="9c69a-156">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

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

### <span data-ttu-id="9c69a-157">Exempel 9: Använd parametern-Force för att skriva över befintliga filer</span><span class="sxs-lookup"><span data-stu-id="9c69a-157">Example 9: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="9c69a-158">Det här exemplet skapar en fil med ett värde och återskapar sedan filen med hjälp av `-Force` .</span><span class="sxs-lookup"><span data-stu-id="9c69a-158">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="9c69a-159">Den befintliga filen skrivs över och den kommer att förlora innehållet som du kan se i egenskapen length</span><span class="sxs-lookup"><span data-stu-id="9c69a-159">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

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
> <span data-ttu-id="9c69a-160">När `New-Item` du använder med `-Force` växeln för att skapa register nycklar, fungerar kommandot likadant som när du skriver över en fil.</span><span class="sxs-lookup"><span data-stu-id="9c69a-160">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="9c69a-161">Om register nyckeln redan finns kommer nyckeln och alla egenskaper och värden att skrivas över med en tom register nyckel.</span><span class="sxs-lookup"><span data-stu-id="9c69a-161">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="9c69a-162">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9c69a-162">PARAMETERS</span></span>

### <span data-ttu-id="9c69a-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="9c69a-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9c69a-164">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c69a-164">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="9c69a-165">Använd för att personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9c69a-165">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="9c69a-166">-Force</span><span class="sxs-lookup"><span data-stu-id="9c69a-166">-Force</span></span>

<span data-ttu-id="9c69a-167">Tvingar denna cmdlet att skapa ett objekt som skriver över ett befintligt skrivskyddat objekt.</span><span class="sxs-lookup"><span data-stu-id="9c69a-167">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="9c69a-168">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="9c69a-168">Implementation varies from provider to provider.</span></span> <span data-ttu-id="9c69a-169">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="9c69a-169">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="9c69a-170">-ItemType</span><span class="sxs-lookup"><span data-stu-id="9c69a-170">-ItemType</span></span>

<span data-ttu-id="9c69a-171">Anger providerns angivna typ för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="9c69a-171">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="9c69a-172">De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.</span><span class="sxs-lookup"><span data-stu-id="9c69a-172">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="9c69a-173">Om platsen finns i en `FileSystem` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="9c69a-173">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="9c69a-174">Fil</span><span class="sxs-lookup"><span data-stu-id="9c69a-174">File</span></span>
- <span data-ttu-id="9c69a-175">Katalog</span><span class="sxs-lookup"><span data-stu-id="9c69a-175">Directory</span></span>
- <span data-ttu-id="9c69a-176">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="9c69a-176">SymbolicLink</span></span>
- <span data-ttu-id="9c69a-177">Knutpunkt</span><span class="sxs-lookup"><span data-stu-id="9c69a-177">Junction</span></span>
- <span data-ttu-id="9c69a-178">HardLink</span><span class="sxs-lookup"><span data-stu-id="9c69a-178">HardLink</span></span>

> [!NOTE]
> <span data-ttu-id="9c69a-179">Att skapa en `SymbolicLink` typ i Windows kräver utökade privilegier som administratör.</span><span class="sxs-lookup"><span data-stu-id="9c69a-179">Creating a `SymbolicLink` type on Windows requires elevation as administrator.</span></span> <span data-ttu-id="9c69a-180">Windows 10 (version 14972 eller senare) med utvecklarläge aktiverat kräver dock inte längre utökade privilegier för att skapa symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="9c69a-180">However, Windows 10 (build 14972 or newer) with Developer Mode enabled no longer requires elevation creating symbolic links.</span></span>

<span data-ttu-id="9c69a-181">I en `Certificate` enhet är dessa värden som du kan ange:</span><span class="sxs-lookup"><span data-stu-id="9c69a-181">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="9c69a-182">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="9c69a-182">Certificate Provider</span></span>
- <span data-ttu-id="9c69a-183">Certifikat</span><span class="sxs-lookup"><span data-stu-id="9c69a-183">Certificate</span></span>
- <span data-ttu-id="9c69a-184">Lagringsplats</span><span class="sxs-lookup"><span data-stu-id="9c69a-184">Store</span></span>
- <span data-ttu-id="9c69a-185">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="9c69a-185">StoreLocation</span></span>

<span data-ttu-id="9c69a-186">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="9c69a-186">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="9c69a-187">-Name</span><span class="sxs-lookup"><span data-stu-id="9c69a-187">-Name</span></span>

<span data-ttu-id="9c69a-188">Anger namnet på det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="9c69a-188">Specifies the name of the new item.</span></span> <span data-ttu-id="9c69a-189">Du kan ange namnet på det nya objektet i parametervärdet för **namn** eller **sökväg** och du kan ange sökvägen till det nya objektet i värdet **namn** eller **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="9c69a-189">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="9c69a-190">Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c69a-190">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="9c69a-191">-Path</span><span class="sxs-lookup"><span data-stu-id="9c69a-191">-Path</span></span>

<span data-ttu-id="9c69a-192">Anger sökvägen till platsen för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="9c69a-192">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="9c69a-193">Standardvärdet är den aktuella platsen när **sökvägen** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="9c69a-193">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="9c69a-194">Du kan ange namnet på det nya objektet i **namn** eller ta med det i **sökvägen**.</span><span class="sxs-lookup"><span data-stu-id="9c69a-194">You can specify the name of the new item in **Name** , or include it in **Path**.</span></span> <span data-ttu-id="9c69a-195">Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c69a-195">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="9c69a-196">För den här cmdleten fungerar **Sök vägs** parametern som parametern **LiteralPath** för andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="9c69a-196">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="9c69a-197">Jokertecken tolkas inte.</span><span class="sxs-lookup"><span data-stu-id="9c69a-197">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="9c69a-198">Alla tecken skickas till platsens Provider.</span><span class="sxs-lookup"><span data-stu-id="9c69a-198">All characters are passed to the location's provider.</span></span> <span data-ttu-id="9c69a-199">Providern kanske inte har stöd för alla tecken.</span><span class="sxs-lookup"><span data-stu-id="9c69a-199">The provider may not support all characters.</span></span> <span data-ttu-id="9c69a-200">Du kan till exempel inte skapa ett fil namn som innehåller en asterisk ( `*` )-bokstav.</span><span class="sxs-lookup"><span data-stu-id="9c69a-200">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

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

### <span data-ttu-id="9c69a-201">-Värde</span><span class="sxs-lookup"><span data-stu-id="9c69a-201">-Value</span></span>

<span data-ttu-id="9c69a-202">Anger värdet för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="9c69a-202">Specifies the value of the new item.</span></span> <span data-ttu-id="9c69a-203">Du kan också skicka ett värde till `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="9c69a-203">You can also pipe a value to `New-Item`.</span></span>

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

### <span data-ttu-id="9c69a-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c69a-204">-Confirm</span></span>

<span data-ttu-id="9c69a-205">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9c69a-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c69a-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c69a-206">-WhatIf</span></span>

<span data-ttu-id="9c69a-207">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9c69a-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9c69a-208">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9c69a-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c69a-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c69a-209">CommonParameters</span></span>

<span data-ttu-id="9c69a-210">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="9c69a-210">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9c69a-211">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="9c69a-211">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9c69a-212">INDATA</span><span class="sxs-lookup"><span data-stu-id="9c69a-212">INPUTS</span></span>

### <span data-ttu-id="9c69a-213">System. Object</span><span class="sxs-lookup"><span data-stu-id="9c69a-213">System.Object</span></span>

<span data-ttu-id="9c69a-214">Du kan skicka ett värde för det nya objektet till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c69a-214">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="9c69a-215">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9c69a-215">OUTPUTS</span></span>

### <span data-ttu-id="9c69a-216">System. Object</span><span class="sxs-lookup"><span data-stu-id="9c69a-216">System.Object</span></span>

<span data-ttu-id="9c69a-217">Den här cmdleten returnerar det objekt som skapas.</span><span class="sxs-lookup"><span data-stu-id="9c69a-217">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="9c69a-218">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9c69a-218">NOTES</span></span>

<span data-ttu-id="9c69a-219">`New-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="9c69a-219">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9c69a-220">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="9c69a-220">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="9c69a-221">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="9c69a-221">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9c69a-222">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9c69a-222">RELATED LINKS</span></span>

[<span data-ttu-id="9c69a-223">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-223">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="9c69a-224">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-224">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="9c69a-225">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-225">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="9c69a-226">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-226">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="9c69a-227">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-227">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="9c69a-228">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-228">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="9c69a-229">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-229">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="9c69a-230">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="9c69a-230">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="9c69a-231">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9c69a-231">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

