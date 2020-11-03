---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 0aeebac75c5a84fd78056954d7178de1dbac1460
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/26/2020
ms.locfileid: "93269349"
---
# <span data-ttu-id="2b13d-103">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="2b13d-103">Copy-Item</span></span>

## <span data-ttu-id="2b13d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2b13d-104">SYNOPSIS</span></span>
<span data-ttu-id="2b13d-105">Kopierar ett objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="2b13d-105">Copies an item from one location to another.</span></span>

## <span data-ttu-id="2b13d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2b13d-106">SYNTAX</span></span>

### <span data-ttu-id="2b13d-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="2b13d-107">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="2b13d-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2b13d-108">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## <span data-ttu-id="2b13d-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2b13d-109">DESCRIPTION</span></span>

<span data-ttu-id="2b13d-110">`Copy-Item`Cmdleten kopierar ett objekt från en plats till en annan plats i samma namnrymd.</span><span class="sxs-lookup"><span data-stu-id="2b13d-110">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="2b13d-111">Den kan till exempel kopiera en fil till en mapp, men den kan inte kopiera en fil till en certifikat enhet.</span><span class="sxs-lookup"><span data-stu-id="2b13d-111">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="2b13d-112">Den här cmdleten klipps inte ut eller raderas inte objekten som kopieras.</span><span class="sxs-lookup"><span data-stu-id="2b13d-112">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="2b13d-113">De specifika objekt som cmdleten kan kopiera beror på vilken PowerShell-provider som exponerar objektet.</span><span class="sxs-lookup"><span data-stu-id="2b13d-113">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="2b13d-114">Till exempel kan den kopiera filer och kataloger i en fil systemen het och register nycklar och poster i register enheten.</span><span class="sxs-lookup"><span data-stu-id="2b13d-114">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="2b13d-115">Denna cmdlet kan kopiera och byta namn på objekt i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="2b13d-115">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="2b13d-116">Om du vill byta namn på ett objekt anger du det nya namnet i värdet för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="2b13d-116">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="2b13d-117">Använd cmdleten om du vill byta namn på ett objekt och inte kopiera det `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-117">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="2b13d-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2b13d-118">EXAMPLES</span></span>

### <span data-ttu-id="2b13d-119">Exempel 1: kopiera en fil till den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="2b13d-119">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="2b13d-120">I det här exemplet kopieras `mar1604.log.txt` filen till `C:\Presentation` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-120">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="2b13d-121">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="2b13d-121">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="2b13d-122">Exempel 2: kopiera katalog innehåll till en befintlig katalog</span><span class="sxs-lookup"><span data-stu-id="2b13d-122">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="2b13d-123">I det här exemplet kopieras innehållet i `C:\Logfiles` katalogen till den befintliga `C:\Drawings` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-123">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="2b13d-124">`Logfiles`Katalogen har inte kopierats.</span><span class="sxs-lookup"><span data-stu-id="2b13d-124">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="2b13d-125">Om `Logfiles` katalogen innehåller filer i under kataloger, kopieras dessa under kataloger med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="2b13d-125">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="2b13d-126">Som standard anges **container** parametern till **True** , vilket bevarar katalog strukturen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-126">By default, the **Container** parameter is set to **True** , which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="2b13d-127">Om du behöver inkludera `Logfiles` katalogen i kopian tar du bort den `\*` från **sökvägen**.</span><span class="sxs-lookup"><span data-stu-id="2b13d-127">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path**.</span></span>
> <span data-ttu-id="2b13d-128">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="2b13d-128">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="2b13d-129">Exempel 3: Kopiera katalogen och innehållet till en ny katalog</span><span class="sxs-lookup"><span data-stu-id="2b13d-129">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="2b13d-130">I det här exemplet kopieras innehållet i `C:\Logfiles` käll katalogen och en ny mål katalog skapas.</span><span class="sxs-lookup"><span data-stu-id="2b13d-130">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="2b13d-131">Den nya mål katalogen `\Logs` skapas i `C:\Drawings` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-131">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="2b13d-132">Om du vill inkludera käll katalogens namn kopierar du till en befintlig mål katalog som visas i **exempel 2**.</span><span class="sxs-lookup"><span data-stu-id="2b13d-132">To include the source directory's name, copy to an existing destination directory as shown in **Example 2**.</span></span> <span data-ttu-id="2b13d-133">Du kan också ge den nya mål katalogen samma namn som käll katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-133">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="2b13d-134">Om **sökvägen** inkluderar `\*` kopieras alla katalogens fil innehåll, inklusive under katalog träd, till den nya mål katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-134">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="2b13d-135">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="2b13d-135">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="2b13d-136">Exempel 4: kopiera en fil till den angivna katalogen och Byt namn på filen</span><span class="sxs-lookup"><span data-stu-id="2b13d-136">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="2b13d-137">I det här exemplet används `Copy-Item` cmdleten för att kopiera `Get-Widget.ps1` skriptet från `\\Server01\Share` katalogen till `\\Server12\ScriptArchive` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-137">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="2b13d-138">Som en del av kopierings åtgärden ändrar kommandot objekt namnet från `Get-Widget.ps1` till `Get-Widget.ps1.txt` , så att det kan bifogas e-postmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="2b13d-138">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="2b13d-139">Exempel 5: kopiera en fil till en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="2b13d-139">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="2b13d-140">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-140">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-141">`Copy-Item`Cmdleten kopierar `test.log` från `D:\Folder001` mappen till `C:\Folder001_Copy` mappen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-141">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-142">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="2b13d-142">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="2b13d-143">Exempel 6: kopiera en mapp till en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="2b13d-143">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="2b13d-144">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-144">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-145">`Copy-Item`Cmdleten kopierar `D:\Folder002` mappen till `C:\Folder002_Copy` katalogen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-145">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-146">Eventuella undermappar eller filer kopieras inte utan att använda **rekursivt** -växeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-146">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="2b13d-147">Åtgärden skapar `Folder002_Copy` mappen om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="2b13d-147">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="2b13d-148">Exempel 7: kopiera hela innehållet i en mapp till en fjärrdator rekursivt</span><span class="sxs-lookup"><span data-stu-id="2b13d-148">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="2b13d-149">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-149">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-150">`Copy-Item`Cmdleten kopierar hela innehållet från `D:\Folder003` mappen till `C:\Folder003_Copy` katalogen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-150">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-151">Undermapparna kopieras med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="2b13d-151">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="2b13d-152">Åtgärden skapar `Folder003_Copy` mappen om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="2b13d-152">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="2b13d-153">Exempel 8: kopiera en fil till en fjärrdator och byt sedan namn på filen</span><span class="sxs-lookup"><span data-stu-id="2b13d-153">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="2b13d-154">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-154">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-155">`Copy-Item`Cmdleten kopierar `scriptingexample.ps1` från `D:\Folder004` mappen till `C:\Folder004_Copy` mappen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-155">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-156">Som en del av kopierings åtgärden ändrar kommandot objekt namnet från `scriptingexample.ps1` till `scriptingexample_copy.ps1` , så att det kan bifogas e-postmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="2b13d-156">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="2b13d-157">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="2b13d-157">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="2b13d-158">Exempel 9: kopiera en fjärrfil till den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="2b13d-158">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="2b13d-159">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-159">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-160">`Copy-Item`Cmdleten kopierar `test.log` från fjärrplatsen `C:\MyRemoteData\` till den lokala `D:\MyLocalData` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-160">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-161">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="2b13d-161">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="2b13d-162">Exempel 10: kopiera hela innehållet i en fjärran sluten mapp till den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="2b13d-162">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="2b13d-163">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-163">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-164">`Copy-Item`Cmdleten kopierar hela innehållet från `C:\MyRemoteData\scripts` fjärrmappen till den lokala `D:\MyLocalData` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-164">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-165">Om mappen Scripts innehåller filer i undermappar, kopieras dessa undermappar med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="2b13d-165">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="2b13d-166">Exempel 11: kopiera hela innehållet i en fjärrmapp till den lokala datorn rekursivt</span><span class="sxs-lookup"><span data-stu-id="2b13d-166">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="2b13d-167">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-167">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="2b13d-168">`Copy-Item`Cmdleten kopierar hela innehållet från `C:\MyRemoteData\scripts` fjärrmappen till den lokala `D:\MyLocalData\scripts` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b13d-168">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="2b13d-169">Eftersom parametern **rekursivt** används skapar åtgärden scripts-mappen om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="2b13d-169">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="2b13d-170">Om mappen Scripts innehåller filer i undermappar, kopieras dessa undermappar med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="2b13d-170">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="2b13d-171">Exempel 12: kopiera filer rekursivt från ett mappträd till den aktuella mappen</span><span class="sxs-lookup"><span data-stu-id="2b13d-171">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="2b13d-172">Det här exemplet visar hur du kopierar filer från en mappstruktur på flera nivåer till en enda platt mapp.</span><span class="sxs-lookup"><span data-stu-id="2b13d-172">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="2b13d-173">De tre första kommandona visar den befintliga mappstrukturen och innehållet i två filer, båda namnen `file3.txt` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-173">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

<span data-ttu-id="2b13d-174">`Copy-Item`Parametern **container** har angetts till `$false` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-174">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="2b13d-175">Detta gör att innehållet i källmappen kopieras, men inte att mappstrukturen bevaras.</span><span class="sxs-lookup"><span data-stu-id="2b13d-175">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="2b13d-176">Observera att filer med samma namn skrivs över i målmappen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-176">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="2b13d-177">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2b13d-177">PARAMETERS</span></span>

### <span data-ttu-id="2b13d-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2b13d-178">-Confirm</span></span>

<span data-ttu-id="2b13d-179">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2b13d-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2b13d-180">-Container</span><span class="sxs-lookup"><span data-stu-id="2b13d-180">-Container</span></span>

<span data-ttu-id="2b13d-181">Anger att den här cmdleten bevarar behållar objekt under kopierings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2b13d-181">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="2b13d-182">Som standard anges **container** parametern till **True**.</span><span class="sxs-lookup"><span data-stu-id="2b13d-182">By default, the **Container** parameter is set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b13d-183">-Credential</span><span class="sxs-lookup"><span data-stu-id="2b13d-183">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2b13d-184">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b13d-184">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2b13d-185">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="2b13d-185">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2b13d-186">-Mål</span><span class="sxs-lookup"><span data-stu-id="2b13d-186">-Destination</span></span>

<span data-ttu-id="2b13d-187">Anger sökvägen till den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-187">Specifies the path to the new location.</span></span> <span data-ttu-id="2b13d-188">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-188">The default is the current directory.</span></span>

<span data-ttu-id="2b13d-189">Om du vill byta namn på objektet som kopieras anger du ett nytt namn i värdet för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="2b13d-189">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2b13d-190">-Undanta</span><span class="sxs-lookup"><span data-stu-id="2b13d-190">-Exclude</span></span>

<span data-ttu-id="2b13d-191">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2b13d-191">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2b13d-192">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="2b13d-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2b13d-193">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-193">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2b13d-194">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2b13d-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="2b13d-195">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-195">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2b13d-196">-Filter</span><span class="sxs-lookup"><span data-stu-id="2b13d-196">-Filter</span></span>

<span data-ttu-id="2b13d-197">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="2b13d-197">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2b13d-198">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="2b13d-198">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2b13d-199">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="2b13d-199">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2b13d-200">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten efter att de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="2b13d-200">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2b13d-201">-Force</span><span class="sxs-lookup"><span data-stu-id="2b13d-201">-Force</span></span>

<span data-ttu-id="2b13d-202">Anger att den här cmdleten kopierar objekt som inte kan ändras på annat sätt, t. ex. kopiera över en skrivskyddad fil eller ett alias.</span><span class="sxs-lookup"><span data-stu-id="2b13d-202">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

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

### <span data-ttu-id="2b13d-203">-FromSession</span><span class="sxs-lookup"><span data-stu-id="2b13d-203">-FromSession</span></span>

<span data-ttu-id="2b13d-204">Anger det **PSSession** -objekt som en fjärrfil kopieras från.</span><span class="sxs-lookup"><span data-stu-id="2b13d-204">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="2b13d-205">När du använder den här parametern, refererar **sökvägen** och **LiteralPath** -parametrarna till den lokala sökvägen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="2b13d-205">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b13d-206">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="2b13d-206">-Include</span></span>

<span data-ttu-id="2b13d-207">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2b13d-207">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2b13d-208">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="2b13d-208">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2b13d-209">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-209">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2b13d-210">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2b13d-210">Wildcard characters are permitted.</span></span> <span data-ttu-id="2b13d-211">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b13d-211">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2b13d-212">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2b13d-212">-LiteralPath</span></span>

<span data-ttu-id="2b13d-213">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="2b13d-213">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2b13d-214">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="2b13d-214">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="2b13d-215">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="2b13d-215">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2b13d-216">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2b13d-216">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2b13d-217">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="2b13d-217">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2b13d-218">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="2b13d-218">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2b13d-219">– PassThru</span><span class="sxs-lookup"><span data-stu-id="2b13d-219">-PassThru</span></span>

<span data-ttu-id="2b13d-220">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="2b13d-220">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="2b13d-221">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2b13d-221">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="2b13d-222">-Path</span><span class="sxs-lookup"><span data-stu-id="2b13d-222">-Path</span></span>

<span data-ttu-id="2b13d-223">Anger, som en sträng mat ris, sökvägen till de objekt som ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="2b13d-223">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="2b13d-224">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2b13d-224">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2b13d-225">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="2b13d-225">-Recurse</span></span>

<span data-ttu-id="2b13d-226">Anger att denna cmdlet gör en rekursiv kopia.</span><span class="sxs-lookup"><span data-stu-id="2b13d-226">Indicates that this cmdlet does a recursive copy.</span></span>

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

### <span data-ttu-id="2b13d-227">-ToSession</span><span class="sxs-lookup"><span data-stu-id="2b13d-227">-ToSession</span></span>

<span data-ttu-id="2b13d-228">Anger det **PSSession** -objekt som en fjärrfil kopieras till.</span><span class="sxs-lookup"><span data-stu-id="2b13d-228">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="2b13d-229">När du använder den här parametern refererar **mål** parametern till den lokala sökvägen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="2b13d-229">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b13d-230">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2b13d-230">-WhatIf</span></span>

<span data-ttu-id="2b13d-231">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="2b13d-231">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2b13d-232">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="2b13d-232">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2b13d-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b13d-233">CommonParameters</span></span>

<span data-ttu-id="2b13d-234">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-234">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2b13d-235">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2b13d-235">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b13d-236">INDATA</span><span class="sxs-lookup"><span data-stu-id="2b13d-236">INPUTS</span></span>

### <span data-ttu-id="2b13d-237">System. String</span><span class="sxs-lookup"><span data-stu-id="2b13d-237">System.String</span></span>

<span data-ttu-id="2b13d-238">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b13d-238">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="2b13d-239">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2b13d-239">OUTPUTS</span></span>

### <span data-ttu-id="2b13d-240">Ingen eller ett objekt som representerar det kopierade objektet</span><span class="sxs-lookup"><span data-stu-id="2b13d-240">None or an object representing the copied item</span></span>

<span data-ttu-id="2b13d-241">När du använder parametern **Passthru** , returnerar denna cmdlet ett objekt som representerar det kopierade objektet.</span><span class="sxs-lookup"><span data-stu-id="2b13d-241">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="2b13d-242">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2b13d-242">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="2b13d-243">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2b13d-243">NOTES</span></span>

<span data-ttu-id="2b13d-244">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="2b13d-244">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2b13d-245">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="2b13d-245">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="2b13d-246">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2b13d-246">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2b13d-247">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2b13d-247">RELATED LINKS</span></span>

[<span data-ttu-id="2b13d-248">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2b13d-248">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="2b13d-249">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-249">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="2b13d-250">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-250">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="2b13d-251">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2b13d-251">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="2b13d-252">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-252">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="2b13d-253">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-253">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="2b13d-254">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-254">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="2b13d-255">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-255">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="2b13d-256">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-256">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="2b13d-257">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="2b13d-257">Set-Item</span></span>](Set-Item.md)
