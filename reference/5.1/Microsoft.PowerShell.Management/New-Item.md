---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: b1657d369d44d575ee7bed8b76d36224ea2748f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265527"
---
# <span data-ttu-id="49dbe-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="49dbe-103">New-Item</span></span>

## <span data-ttu-id="49dbe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="49dbe-104">SYNOPSIS</span></span>
<span data-ttu-id="49dbe-105">Skapar ett nytt objekt.</span><span class="sxs-lookup"><span data-stu-id="49dbe-105">Creates a new item.</span></span>

## <span data-ttu-id="49dbe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49dbe-106">SYNTAX</span></span>

### <span data-ttu-id="49dbe-107">pathSet (standard)</span><span class="sxs-lookup"><span data-stu-id="49dbe-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="49dbe-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="49dbe-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="49dbe-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="49dbe-109">DESCRIPTION</span></span>

<span data-ttu-id="49dbe-110">`New-Item`Cmdleten skapar ett nytt objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="49dbe-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="49dbe-111">Vilka typer av objekt som kan skapas beror på objektets plats.</span><span class="sxs-lookup"><span data-stu-id="49dbe-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="49dbe-112">I fil systemet skapas till exempel `New-Item` filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="49dbe-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="49dbe-113">I registret `New-Item` skapas register nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="49dbe-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="49dbe-114">`New-Item` kan också ange värdet för de objekt som skapas.</span><span class="sxs-lookup"><span data-stu-id="49dbe-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="49dbe-115">Till exempel, när den skapar en ny fil, `New-Item` kan lägga till det ursprungliga innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="49dbe-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="49dbe-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="49dbe-116">EXAMPLES</span></span>

### <span data-ttu-id="49dbe-117">Exempel 1: skapa en fil i den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="49dbe-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="49dbe-118">Det här kommandot skapar en textfil med namnet "testfile1.txt" i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="49dbe-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="49dbe-119">Punkten (".") i värdet för parametern **Path** anger den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="49dbe-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="49dbe-120">Den citerade text som följer **värde** parametern läggs till i filen som innehåll.</span><span class="sxs-lookup"><span data-stu-id="49dbe-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="49dbe-121">Exempel 2: skapa en katalog</span><span class="sxs-lookup"><span data-stu-id="49dbe-121">Example 2: Create a directory</span></span>

<span data-ttu-id="49dbe-122">Det här kommandot skapar en katalog med namnet "LogFiles" på `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="49dbe-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="49dbe-123">Parametern **itemType** anger att det nya objektet är en katalog, inte en fil eller något annat fil Systems objekt.</span><span class="sxs-lookup"><span data-stu-id="49dbe-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="49dbe-124">Exempel 3: skapa en profil</span><span class="sxs-lookup"><span data-stu-id="49dbe-124">Example 3: Create a profile</span></span>

<span data-ttu-id="49dbe-125">Det här kommandot skapar en PowerShell-profil i den sökväg som anges av `$profile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="49dbe-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="49dbe-126">Du kan använda profiler för att anpassa PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49dbe-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="49dbe-127">`$profile` är en automatisk (inbyggd) variabel som lagrar sökvägen och fil namnet för profilen "CurrentUser/CurrentHost".</span><span class="sxs-lookup"><span data-stu-id="49dbe-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="49dbe-128">Profilen finns inte som standard, även om PowerShell lagrar en sökväg och ett fil namn för den.</span><span class="sxs-lookup"><span data-stu-id="49dbe-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="49dbe-129">I det här kommandot `$profile` representerar variabeln sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="49dbe-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="49dbe-130">Parametern **itemType** anger att kommandot skapar en fil.</span><span class="sxs-lookup"><span data-stu-id="49dbe-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="49dbe-131">Med parametern **Force** kan du skapa en fil i profil Sök vägen, även om katalogerna i sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="49dbe-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="49dbe-132">När du har skapat en profil kan du ange alias, funktioner och skript i profilen för att anpassa ditt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="49dbe-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="49dbe-133">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) och [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="49dbe-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

> [!NOTE]
> <span data-ttu-id="49dbe-134">När du skapar en fil med den här metoden kodas den resulterande filen som UTF-8 utan en byte-order-markering (BOM).</span><span class="sxs-lookup"><span data-stu-id="49dbe-134">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

### <span data-ttu-id="49dbe-135">Exempel 4: skapa en katalog i en annan katalog</span><span class="sxs-lookup"><span data-stu-id="49dbe-135">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="49dbe-136">I det här exemplet skapas en ny skript katalog i katalogen "C:\PS-Test".</span><span class="sxs-lookup"><span data-stu-id="49dbe-136">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="49dbe-137">Namnet på det nya katalog objektet, "skript", ingår i värdet för parametern **Path** i stället för att anges i värdet för **namnet**.</span><span class="sxs-lookup"><span data-stu-id="49dbe-137">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name**.</span></span> <span data-ttu-id="49dbe-138">Som anges av syntaxen är kommando formuläret giltiga.</span><span class="sxs-lookup"><span data-stu-id="49dbe-138">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="49dbe-139">Exempel 5: skapa flera filer</span><span class="sxs-lookup"><span data-stu-id="49dbe-139">Example 5: Create multiple files</span></span>

<span data-ttu-id="49dbe-140">I det här exemplet skapas filer i två olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="49dbe-140">This example creates files in two different directories.</span></span> <span data-ttu-id="49dbe-141">Eftersom **sökvägen** tar flera strängar kan du använda den för att skapa flera objekt.</span><span class="sxs-lookup"><span data-stu-id="49dbe-141">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="49dbe-142">Exempel 6: Använd parametern-Force för att försöka återskapa mappar</span><span class="sxs-lookup"><span data-stu-id="49dbe-142">Example 6: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="49dbe-143">I det här exemplet skapas en mapp med en fil i.</span><span class="sxs-lookup"><span data-stu-id="49dbe-143">This example creates a folder with a file inside.</span></span> <span data-ttu-id="49dbe-144">Försöker sedan skapa samma mapp med `-Force` .</span><span class="sxs-lookup"><span data-stu-id="49dbe-144">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="49dbe-145">Mappen skrivs inte över, men returnerar bara det befintliga objektet med filen som skapats intakt.</span><span class="sxs-lookup"><span data-stu-id="49dbe-145">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

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

### <span data-ttu-id="49dbe-146">Exempel 7: Använd parametern-Force för att skriva över befintliga filer</span><span class="sxs-lookup"><span data-stu-id="49dbe-146">Example 7: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="49dbe-147">Det här exemplet skapar en fil med ett värde och återskapar sedan filen med hjälp av `-Force` .</span><span class="sxs-lookup"><span data-stu-id="49dbe-147">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="49dbe-148">Den befintliga filen skrivs över och den kommer att förlora innehållet som du kan se i egenskapen length</span><span class="sxs-lookup"><span data-stu-id="49dbe-148">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

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
> <span data-ttu-id="49dbe-149">När `New-Item` du använder med `-Force` växeln för att skapa register nycklar, fungerar kommandot likadant som när du skriver över en fil.</span><span class="sxs-lookup"><span data-stu-id="49dbe-149">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="49dbe-150">Om register nyckeln redan finns kommer nyckeln och alla egenskaper och värden att skrivas över med en tom register nyckel.</span><span class="sxs-lookup"><span data-stu-id="49dbe-150">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="49dbe-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="49dbe-151">PARAMETERS</span></span>

### <span data-ttu-id="49dbe-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="49dbe-152">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="49dbe-153">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49dbe-153">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="49dbe-154">Använd för att personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="49dbe-154">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="49dbe-155">-Force</span><span class="sxs-lookup"><span data-stu-id="49dbe-155">-Force</span></span>

<span data-ttu-id="49dbe-156">Tvingar denna cmdlet att skapa ett objekt som skriver över ett befintligt skrivskyddat objekt.</span><span class="sxs-lookup"><span data-stu-id="49dbe-156">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="49dbe-157">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="49dbe-157">Implementation varies from provider to provider.</span></span> <span data-ttu-id="49dbe-158">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="49dbe-158">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="49dbe-159">-ItemType</span><span class="sxs-lookup"><span data-stu-id="49dbe-159">-ItemType</span></span>

<span data-ttu-id="49dbe-160">Anger providerns angivna typ för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="49dbe-160">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="49dbe-161">De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.</span><span class="sxs-lookup"><span data-stu-id="49dbe-161">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="49dbe-162">Om platsen finns i en `FileSystem` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="49dbe-162">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="49dbe-163">Fil</span><span class="sxs-lookup"><span data-stu-id="49dbe-163">File</span></span>
- <span data-ttu-id="49dbe-164">Katalog</span><span class="sxs-lookup"><span data-stu-id="49dbe-164">Directory</span></span>
- <span data-ttu-id="49dbe-165">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="49dbe-165">SymbolicLink</span></span>
- <span data-ttu-id="49dbe-166">Knutpunkt</span><span class="sxs-lookup"><span data-stu-id="49dbe-166">Junction</span></span>
- <span data-ttu-id="49dbe-167">HardLink</span><span class="sxs-lookup"><span data-stu-id="49dbe-167">HardLink</span></span>

<span data-ttu-id="49dbe-168">När du skapar en fil med den här metoden kodas den resulterande filen som UTF-8 utan en byte-order-markering (BOM).</span><span class="sxs-lookup"><span data-stu-id="49dbe-168">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

<span data-ttu-id="49dbe-169">I en `Certificate` enhet är dessa värden som du kan ange:</span><span class="sxs-lookup"><span data-stu-id="49dbe-169">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="49dbe-170">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="49dbe-170">Certificate Provider</span></span>
- <span data-ttu-id="49dbe-171">Certifikat</span><span class="sxs-lookup"><span data-stu-id="49dbe-171">Certificate</span></span>
- <span data-ttu-id="49dbe-172">Lagringsplats</span><span class="sxs-lookup"><span data-stu-id="49dbe-172">Store</span></span>
- <span data-ttu-id="49dbe-173">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="49dbe-173">StoreLocation</span></span>

<span data-ttu-id="49dbe-174">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="49dbe-174">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="49dbe-175">-Name</span><span class="sxs-lookup"><span data-stu-id="49dbe-175">-Name</span></span>

<span data-ttu-id="49dbe-176">Anger namnet på det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="49dbe-176">Specifies the name of the new item.</span></span> <span data-ttu-id="49dbe-177">Du kan ange namnet på det nya objektet i parametervärdet för **namn** eller **sökväg** och du kan ange sökvägen till det nya objektet i värdet **namn** eller **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="49dbe-177">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="49dbe-178">Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="49dbe-178">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="49dbe-179">-Path</span><span class="sxs-lookup"><span data-stu-id="49dbe-179">-Path</span></span>

<span data-ttu-id="49dbe-180">Anger sökvägen till platsen för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="49dbe-180">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="49dbe-181">Standardvärdet är den aktuella platsen när **sökvägen** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="49dbe-181">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="49dbe-182">Du kan ange namnet på det nya objektet i **namn** eller ta med det i **sökvägen**.</span><span class="sxs-lookup"><span data-stu-id="49dbe-182">You can specify the name of the new item in **Name** , or include it in **Path**.</span></span> <span data-ttu-id="49dbe-183">Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="49dbe-183">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="49dbe-184">För den här cmdleten fungerar **Sök vägs** parametern som parametern **LiteralPath** för andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="49dbe-184">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="49dbe-185">Jokertecken tolkas inte.</span><span class="sxs-lookup"><span data-stu-id="49dbe-185">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="49dbe-186">Alla tecken skickas till platsens Provider.</span><span class="sxs-lookup"><span data-stu-id="49dbe-186">All characters are passed to the location's provider.</span></span> <span data-ttu-id="49dbe-187">Providern kanske inte har stöd för alla tecken.</span><span class="sxs-lookup"><span data-stu-id="49dbe-187">The provider may not support all characters.</span></span> <span data-ttu-id="49dbe-188">Du kan till exempel inte skapa ett fil namn som innehåller en asterisk ( `*` )-bokstav.</span><span class="sxs-lookup"><span data-stu-id="49dbe-188">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet, nameSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49dbe-189">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="49dbe-189">-UseTransaction</span></span>

<span data-ttu-id="49dbe-190">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="49dbe-190">Includes the command in the active transaction.</span></span> <span data-ttu-id="49dbe-191">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="49dbe-191">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="49dbe-192">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="49dbe-192">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49dbe-193">-Värde</span><span class="sxs-lookup"><span data-stu-id="49dbe-193">-Value</span></span>

<span data-ttu-id="49dbe-194">Anger värdet för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="49dbe-194">Specifies the value of the new item.</span></span> <span data-ttu-id="49dbe-195">Du kan också skicka ett värde till `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="49dbe-195">You can also pipe a value to `New-Item`.</span></span>

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

### <span data-ttu-id="49dbe-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="49dbe-196">-Confirm</span></span>

<span data-ttu-id="49dbe-197">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="49dbe-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="49dbe-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="49dbe-198">-WhatIf</span></span>

<span data-ttu-id="49dbe-199">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="49dbe-199">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="49dbe-200">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="49dbe-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="49dbe-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49dbe-201">CommonParameters</span></span>

<span data-ttu-id="49dbe-202">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="49dbe-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="49dbe-203">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="49dbe-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="49dbe-204">INDATA</span><span class="sxs-lookup"><span data-stu-id="49dbe-204">INPUTS</span></span>

### <span data-ttu-id="49dbe-205">System. Object</span><span class="sxs-lookup"><span data-stu-id="49dbe-205">System.Object</span></span>

<span data-ttu-id="49dbe-206">Du kan skicka ett värde för det nya objektet till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49dbe-206">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="49dbe-207">UTDATA</span><span class="sxs-lookup"><span data-stu-id="49dbe-207">OUTPUTS</span></span>

### <span data-ttu-id="49dbe-208">System. Object</span><span class="sxs-lookup"><span data-stu-id="49dbe-208">System.Object</span></span>

<span data-ttu-id="49dbe-209">Den här cmdleten returnerar det objekt som skapas.</span><span class="sxs-lookup"><span data-stu-id="49dbe-209">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="49dbe-210">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="49dbe-210">NOTES</span></span>

<span data-ttu-id="49dbe-211">`New-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="49dbe-211">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="49dbe-212">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="49dbe-212">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="49dbe-213">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="49dbe-213">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="49dbe-214">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="49dbe-214">RELATED LINKS</span></span>

[<span data-ttu-id="49dbe-215">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-215">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="49dbe-216">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-216">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="49dbe-217">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-217">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="49dbe-218">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="49dbe-219">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="49dbe-220">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-220">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="49dbe-221">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-221">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="49dbe-222">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="49dbe-222">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="49dbe-223">about_Providers</span><span class="sxs-lookup"><span data-stu-id="49dbe-223">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
