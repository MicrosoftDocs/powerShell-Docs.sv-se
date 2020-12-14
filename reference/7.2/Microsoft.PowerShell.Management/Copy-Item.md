---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: ee2d8b8a3b736a59b5af4a81710a0d29dd2238d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709535"
---
# <span data-ttu-id="f0b92-102">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="f0b92-102">Copy-Item</span></span>

## <span data-ttu-id="f0b92-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f0b92-103">SYNOPSIS</span></span>
<span data-ttu-id="f0b92-104">Kopierar ett objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="f0b92-104">Copies an item from one location to another.</span></span>

## <span data-ttu-id="f0b92-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0b92-105">SYNTAX</span></span>

### <span data-ttu-id="f0b92-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="f0b92-106">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="f0b92-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0b92-107">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## <span data-ttu-id="f0b92-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f0b92-108">DESCRIPTION</span></span>

<span data-ttu-id="f0b92-109">`Copy-Item`Cmdleten kopierar ett objekt från en plats till en annan plats i samma namnrymd.</span><span class="sxs-lookup"><span data-stu-id="f0b92-109">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="f0b92-110">Den kan till exempel kopiera en fil till en mapp, men den kan inte kopiera en fil till en certifikat enhet.</span><span class="sxs-lookup"><span data-stu-id="f0b92-110">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="f0b92-111">Den här cmdleten klipps inte ut eller raderas inte objekten som kopieras.</span><span class="sxs-lookup"><span data-stu-id="f0b92-111">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="f0b92-112">De specifika objekt som cmdleten kan kopiera beror på vilken PowerShell-provider som exponerar objektet.</span><span class="sxs-lookup"><span data-stu-id="f0b92-112">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="f0b92-113">Till exempel kan den kopiera filer och kataloger i en fil systemen het och register nycklar och poster i register enheten.</span><span class="sxs-lookup"><span data-stu-id="f0b92-113">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="f0b92-114">Denna cmdlet kan kopiera och byta namn på objekt i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="f0b92-114">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="f0b92-115">Om du vill byta namn på ett objekt anger du det nya namnet i värdet för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="f0b92-115">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="f0b92-116">Använd cmdleten om du vill byta namn på ett objekt och inte kopiera det `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-116">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="f0b92-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f0b92-117">EXAMPLES</span></span>

### <span data-ttu-id="f0b92-118">Exempel 1: kopiera en fil till den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="f0b92-118">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="f0b92-119">I det här exemplet kopieras `mar1604.log.txt` filen till `C:\Presentation` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-119">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="f0b92-120">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="f0b92-120">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="f0b92-121">Exempel 2: kopiera katalog innehåll till en befintlig katalog</span><span class="sxs-lookup"><span data-stu-id="f0b92-121">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="f0b92-122">I det här exemplet kopieras innehållet i `C:\Logfiles` katalogen till den befintliga `C:\Drawings` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-122">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="f0b92-123">`Logfiles`Katalogen har inte kopierats.</span><span class="sxs-lookup"><span data-stu-id="f0b92-123">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="f0b92-124">Om `Logfiles` katalogen innehåller filer i under kataloger, kopieras dessa under kataloger med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="f0b92-124">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="f0b92-125">Som standard anges **container** parametern till **True**, vilket bevarar katalog strukturen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-125">By default, the **Container** parameter is set to **True**, which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="f0b92-126">Om du behöver inkludera `Logfiles` katalogen i kopian tar du bort den `\*` från **sökvägen**.</span><span class="sxs-lookup"><span data-stu-id="f0b92-126">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path**.</span></span>
> <span data-ttu-id="f0b92-127">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f0b92-127">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="f0b92-128">Exempel 3: Kopiera katalogen och innehållet till en ny katalog</span><span class="sxs-lookup"><span data-stu-id="f0b92-128">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="f0b92-129">I det här exemplet kopieras innehållet i `C:\Logfiles` käll katalogen och en ny mål katalog skapas.</span><span class="sxs-lookup"><span data-stu-id="f0b92-129">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="f0b92-130">Den nya mål katalogen `\Logs` skapas i `C:\Drawings` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-130">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="f0b92-131">Om du vill inkludera käll katalogens namn kopierar du till en befintlig mål katalog som visas i **exempel 2**.</span><span class="sxs-lookup"><span data-stu-id="f0b92-131">To include the source directory's name, copy to an existing destination directory as shown in **Example 2**.</span></span> <span data-ttu-id="f0b92-132">Du kan också ge den nya mål katalogen samma namn som käll katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-132">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="f0b92-133">Om **sökvägen** inkluderar `\*` kopieras alla katalogens fil innehåll, inklusive under katalog träd, till den nya mål katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-133">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="f0b92-134">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f0b92-134">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="f0b92-135">Exempel 4: kopiera en fil till den angivna katalogen och Byt namn på filen</span><span class="sxs-lookup"><span data-stu-id="f0b92-135">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="f0b92-136">I det här exemplet används `Copy-Item` cmdleten för att kopiera `Get-Widget.ps1` skriptet från `\\Server01\Share` katalogen till `\\Server12\ScriptArchive` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-136">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="f0b92-137">Som en del av kopierings åtgärden ändrar kommandot objekt namnet från `Get-Widget.ps1` till `Get-Widget.ps1.txt` , så att det kan bifogas e-postmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="f0b92-137">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="f0b92-138">Exempel 5: kopiera en fil till en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="f0b92-138">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="f0b92-139">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-139">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-140">`Copy-Item`Cmdleten kopierar `test.log` från `D:\Folder001` mappen till `C:\Folder001_Copy` mappen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-140">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-141">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="f0b92-141">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="f0b92-142">Exempel 6: kopiera en mapp till en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="f0b92-142">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="f0b92-143">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-143">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-144">`Copy-Item`Cmdleten kopierar `D:\Folder002` mappen till `C:\Folder002_Copy` katalogen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-144">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-145">Eventuella undermappar eller filer kopieras inte utan att använda **rekursivt** -växeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-145">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="f0b92-146">Åtgärden skapar `Folder002_Copy` mappen om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="f0b92-146">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="f0b92-147">Exempel 7: kopiera hela innehållet i en mapp till en fjärrdator rekursivt</span><span class="sxs-lookup"><span data-stu-id="f0b92-147">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="f0b92-148">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-148">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-149">`Copy-Item`Cmdleten kopierar hela innehållet från `D:\Folder003` mappen till `C:\Folder003_Copy` katalogen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-149">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-150">Undermapparna kopieras med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="f0b92-150">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="f0b92-151">Åtgärden skapar `Folder003_Copy` mappen om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="f0b92-151">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="f0b92-152">Exempel 8: kopiera en fil till en fjärrdator och byt sedan namn på filen</span><span class="sxs-lookup"><span data-stu-id="f0b92-152">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="f0b92-153">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-153">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-154">`Copy-Item`Cmdleten kopierar `scriptingexample.ps1` från `D:\Folder004` mappen till `C:\Folder004_Copy` mappen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-154">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-155">Som en del av kopierings åtgärden ändrar kommandot objekt namnet från `scriptingexample.ps1` till `scriptingexample_copy.ps1` , så att det kan bifogas e-postmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="f0b92-155">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="f0b92-156">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="f0b92-156">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="f0b92-157">Exempel 9: kopiera en fjärrfil till den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="f0b92-157">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="f0b92-158">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-158">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-159">`Copy-Item`Cmdleten kopierar `test.log` från fjärrplatsen `C:\MyRemoteData\` till den lokala `D:\MyLocalData` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-159">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-160">Den ursprungliga filen har inte tagits bort.</span><span class="sxs-lookup"><span data-stu-id="f0b92-160">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="f0b92-161">Exempel 10: kopiera hela innehållet i en fjärran sluten mapp till den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="f0b92-161">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="f0b92-162">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-162">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-163">`Copy-Item`Cmdleten kopierar hela innehållet från `C:\MyRemoteData\scripts` fjärrmappen till den lokala `D:\MyLocalData` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-163">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-164">Om mappen Scripts innehåller filer i undermappar, kopieras dessa undermappar med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="f0b92-164">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="f0b92-165">Exempel 11: kopiera hela innehållet i en fjärrmapp till den lokala datorn rekursivt</span><span class="sxs-lookup"><span data-stu-id="f0b92-165">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="f0b92-166">En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-166">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="f0b92-167">`Copy-Item`Cmdleten kopierar hela innehållet från `C:\MyRemoteData\scripts` fjärrmappen till den lokala `D:\MyLocalData\scripts` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0b92-167">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="f0b92-168">Eftersom parametern **rekursivt** används skapar åtgärden scripts-mappen om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="f0b92-168">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="f0b92-169">Om mappen Scripts innehåller filer i undermappar, kopieras dessa undermappar med sina fil träd intakta.</span><span class="sxs-lookup"><span data-stu-id="f0b92-169">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="f0b92-170">Exempel 12: kopiera filer rekursivt från ett mappträd till den aktuella mappen</span><span class="sxs-lookup"><span data-stu-id="f0b92-170">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="f0b92-171">Det här exemplet visar hur du kopierar filer från en mappstruktur på flera nivåer till en enda platt mapp.</span><span class="sxs-lookup"><span data-stu-id="f0b92-171">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="f0b92-172">De tre första kommandona visar den befintliga mappstrukturen och innehållet i två filer, båda namnen `file3.txt` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-172">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

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

<span data-ttu-id="f0b92-173">`Copy-Item`Parametern **container** har angetts till `$false` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-173">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="f0b92-174">Detta gör att innehållet i källmappen kopieras, men inte att mappstrukturen bevaras.</span><span class="sxs-lookup"><span data-stu-id="f0b92-174">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="f0b92-175">Observera att filer med samma namn skrivs över i målmappen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-175">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="f0b92-176">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f0b92-176">PARAMETERS</span></span>

### <span data-ttu-id="f0b92-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f0b92-177">-Confirm</span></span>

<span data-ttu-id="f0b92-178">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f0b92-178">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f0b92-179">-Container</span><span class="sxs-lookup"><span data-stu-id="f0b92-179">-Container</span></span>

<span data-ttu-id="f0b92-180">Anger att den här cmdleten bevarar behållar objekt under kopierings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f0b92-180">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="f0b92-181">Som standard anges **container** parametern till **True**.</span><span class="sxs-lookup"><span data-stu-id="f0b92-181">By default, the **Container** parameter is set to **True**.</span></span>

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

### <span data-ttu-id="f0b92-182">-Credential</span><span class="sxs-lookup"><span data-stu-id="f0b92-182">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f0b92-183">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0b92-183">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f0b92-184">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="f0b92-184">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f0b92-185">-Mål</span><span class="sxs-lookup"><span data-stu-id="f0b92-185">-Destination</span></span>

<span data-ttu-id="f0b92-186">Anger sökvägen till den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-186">Specifies the path to the new location.</span></span> <span data-ttu-id="f0b92-187">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-187">The default is the current directory.</span></span>

<span data-ttu-id="f0b92-188">Om du vill byta namn på objektet som kopieras anger du ett nytt namn i värdet för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="f0b92-188">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

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

### <span data-ttu-id="f0b92-189">-Undanta</span><span class="sxs-lookup"><span data-stu-id="f0b92-189">-Exclude</span></span>

<span data-ttu-id="f0b92-190">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f0b92-190">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="f0b92-191">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="f0b92-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f0b92-192">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-192">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f0b92-193">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f0b92-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="f0b92-194">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-194">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f0b92-195">-Filter</span><span class="sxs-lookup"><span data-stu-id="f0b92-195">-Filter</span></span>

<span data-ttu-id="f0b92-196">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="f0b92-196">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="f0b92-197">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="f0b92-197">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="f0b92-198">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="f0b92-198">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="f0b92-199">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten efter att de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="f0b92-199">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

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

### <span data-ttu-id="f0b92-200">-Force</span><span class="sxs-lookup"><span data-stu-id="f0b92-200">-Force</span></span>

<span data-ttu-id="f0b92-201">Anger att den här cmdleten kopierar objekt som inte kan ändras på annat sätt, t. ex. kopiera över en skrivskyddad fil eller ett alias.</span><span class="sxs-lookup"><span data-stu-id="f0b92-201">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

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

### <span data-ttu-id="f0b92-202">-FromSession</span><span class="sxs-lookup"><span data-stu-id="f0b92-202">-FromSession</span></span>

<span data-ttu-id="f0b92-203">Anger det **PSSession** -objekt som en fjärrfil kopieras från.</span><span class="sxs-lookup"><span data-stu-id="f0b92-203">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="f0b92-204">När du använder den här parametern, refererar **sökvägen** och **LiteralPath** -parametrarna till den lokala sökvägen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f0b92-204">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

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

### <span data-ttu-id="f0b92-205">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="f0b92-205">-Include</span></span>

<span data-ttu-id="f0b92-206">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f0b92-206">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="f0b92-207">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="f0b92-207">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f0b92-208">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-208">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="f0b92-209">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f0b92-209">Wildcard characters are permitted.</span></span> <span data-ttu-id="f0b92-210">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f0b92-210">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f0b92-211">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0b92-211">-LiteralPath</span></span>

<span data-ttu-id="f0b92-212">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="f0b92-212">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f0b92-213">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="f0b92-213">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="f0b92-214">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="f0b92-214">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f0b92-215">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f0b92-215">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f0b92-216">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f0b92-216">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f0b92-217">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="f0b92-217">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="f0b92-218">– PassThru</span><span class="sxs-lookup"><span data-stu-id="f0b92-218">-PassThru</span></span>

<span data-ttu-id="f0b92-219">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="f0b92-219">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="f0b92-220">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f0b92-220">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="f0b92-221">-Path</span><span class="sxs-lookup"><span data-stu-id="f0b92-221">-Path</span></span>

<span data-ttu-id="f0b92-222">Anger, som en sträng mat ris, sökvägen till de objekt som ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="f0b92-222">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="f0b92-223">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f0b92-223">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f0b92-224">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="f0b92-224">-Recurse</span></span>

<span data-ttu-id="f0b92-225">Anger att denna cmdlet gör en rekursiv kopia.</span><span class="sxs-lookup"><span data-stu-id="f0b92-225">Indicates that this cmdlet does a recursive copy.</span></span>

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

### <span data-ttu-id="f0b92-226">-ToSession</span><span class="sxs-lookup"><span data-stu-id="f0b92-226">-ToSession</span></span>

<span data-ttu-id="f0b92-227">Anger det **PSSession** -objekt som en fjärrfil kopieras till.</span><span class="sxs-lookup"><span data-stu-id="f0b92-227">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="f0b92-228">När du använder den här parametern refererar **mål** parametern till den lokala sökvägen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f0b92-228">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

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

### <span data-ttu-id="f0b92-229">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f0b92-229">-WhatIf</span></span>

<span data-ttu-id="f0b92-230">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f0b92-230">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f0b92-231">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f0b92-231">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="f0b92-232">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0b92-232">CommonParameters</span></span>

<span data-ttu-id="f0b92-233">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-233">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f0b92-234">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0b92-234">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0b92-235">INDATA</span><span class="sxs-lookup"><span data-stu-id="f0b92-235">INPUTS</span></span>

### <span data-ttu-id="f0b92-236">System. String</span><span class="sxs-lookup"><span data-stu-id="f0b92-236">System.String</span></span>

<span data-ttu-id="f0b92-237">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0b92-237">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="f0b92-238">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f0b92-238">OUTPUTS</span></span>

### <span data-ttu-id="f0b92-239">Ingen eller ett objekt som representerar det kopierade objektet</span><span class="sxs-lookup"><span data-stu-id="f0b92-239">None or an object representing the copied item</span></span>

<span data-ttu-id="f0b92-240">När du använder parametern **Passthru** , returnerar denna cmdlet ett objekt som representerar det kopierade objektet.</span><span class="sxs-lookup"><span data-stu-id="f0b92-240">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="f0b92-241">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f0b92-241">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="f0b92-242">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f0b92-242">NOTES</span></span>

<span data-ttu-id="f0b92-243">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="f0b92-243">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f0b92-244">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="f0b92-244">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f0b92-245">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="f0b92-245">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f0b92-246">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f0b92-246">RELATED LINKS</span></span>

[<span data-ttu-id="f0b92-247">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f0b92-247">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="f0b92-248">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-248">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="f0b92-249">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-249">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="f0b92-250">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="f0b92-250">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="f0b92-251">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-251">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="f0b92-252">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-252">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="f0b92-253">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-253">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="f0b92-254">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-254">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="f0b92-255">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-255">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="f0b92-256">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="f0b92-256">Set-Item</span></span>](Set-Item.md)

