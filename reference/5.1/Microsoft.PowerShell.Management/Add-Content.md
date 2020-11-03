---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266270"
---
# <span data-ttu-id="4c472-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="4c472-103">Add-Content</span></span>

## <span data-ttu-id="4c472-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4c472-104">SYNOPSIS</span></span>
<span data-ttu-id="4c472-105">Lägger till innehåll till de angivna objekten, till exempel att lägga till ord i en fil.</span><span class="sxs-lookup"><span data-stu-id="4c472-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="4c472-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4c472-106">SYNTAX</span></span>

### <span data-ttu-id="4c472-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="4c472-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="4c472-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4c472-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="4c472-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4c472-109">DESCRIPTION</span></span>

<span data-ttu-id="4c472-110">`Add-Content`Cmdleten lägger till innehåll i ett angivet objekt eller en angiven fil.</span><span class="sxs-lookup"><span data-stu-id="4c472-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="4c472-111">Du kan ange innehållet genom att skriva innehållet i kommandot eller genom att ange ett objekt som innehåller innehållet.</span><span class="sxs-lookup"><span data-stu-id="4c472-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="4c472-112">Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="4c472-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="4c472-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4c472-113">EXAMPLES</span></span>

### <span data-ttu-id="4c472-114">Exempel 1: Lägg till en sträng till alla textfiler med ett undantag</span><span class="sxs-lookup"><span data-stu-id="4c472-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="4c472-115">I det här exemplet läggs ett värde till i textfiler i den aktuella katalogen, men filer som är baserade på fil namnet exkluderas.</span><span class="sxs-lookup"><span data-stu-id="4c472-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="4c472-116">`Add-Content`Cmdleten använder parametern **Path** för att ange alla. txt-filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="4c472-116">The `Add-Content` cmdlet uses the **Path** parameter to specify all .txt files in the current directory.</span></span> <span data-ttu-id="4c472-117">Parametern **exclude** ignorerar fil namn som matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="4c472-117">The **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="4c472-118">Parametern **Value** anger text strängen som skrivs till filerna.</span><span class="sxs-lookup"><span data-stu-id="4c472-118">The **Value** parameter specifies the text string that is written to the files.</span></span>

<span data-ttu-id="4c472-119">Använd [Get-Content](Get-Content.md) för att visa innehållet i de här filerna.</span><span class="sxs-lookup"><span data-stu-id="4c472-119">Use [Get-Content](Get-Content.md) to display the contents of these files.</span></span>

### <span data-ttu-id="4c472-120">Exempel 2: Lägg till ett datum i slutet av de angivna filerna</span><span class="sxs-lookup"><span data-stu-id="4c472-120">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="4c472-121">I det här exemplet läggs datumet till i den aktuella katalogen och datumet visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4c472-121">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

<span data-ttu-id="4c472-122">`Add-Content`Cmdleten använder parametrarna **Path** och **Value** för att skapa två nya filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="4c472-122">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create two new files in the current directory.</span></span> <span data-ttu-id="4c472-123">Parametern **Value** anger den `Get-Date` cmdlet som ska hämta datumet och skickar datumet till `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="4c472-123">The **Value** parameter specifies the `Get-Date` cmdlet to get the date and passes the date to `Add-Content`.</span></span> <span data-ttu-id="4c472-124">`Add-Content`Cmdleten skriver datumet till varje fil.</span><span class="sxs-lookup"><span data-stu-id="4c472-124">The `Add-Content` cmdlet writes the date to each file.</span></span> <span data-ttu-id="4c472-125">Parametern **Passthru** skickar ett objekt som representerar date-objektet.</span><span class="sxs-lookup"><span data-stu-id="4c472-125">The **PassThru** parameter passes an object that represents the date object.</span></span> <span data-ttu-id="4c472-126">Eftersom det inte finns någon annan cmdlet för att ta emot det skickade objektet visas det i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4c472-126">Because there is no other cmdlet to receive the passed object, it is displayed in the PowerShell console.</span></span> <span data-ttu-id="4c472-127">`Get-Content`Cmdleten visar den uppdaterade filen DateTimeFile1. log.</span><span class="sxs-lookup"><span data-stu-id="4c472-127">The `Get-Content` cmdlet displays the updated file, DateTimeFile1.log.</span></span>

### <span data-ttu-id="4c472-128">Exempel 3: lägga till innehållet i en angiven fil till en annan fil</span><span class="sxs-lookup"><span data-stu-id="4c472-128">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="4c472-129">Det här exemplet hämtar innehållet från en fil och lägger till innehållet i en annan fil.</span><span class="sxs-lookup"><span data-stu-id="4c472-129">This example gets the content from a file and appends that content into another file.</span></span>

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="4c472-130">`Add-Content`Cmdleten använder parametern **Path** för att ange den nya filen i den aktuella katalogen CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="4c472-130">The `Add-Content` cmdlet uses the **Path** parameter to specify the new file in the current directory, CopyToFile.txt.</span></span> <span data-ttu-id="4c472-131">Parametern **Value** använder `Get-Content` cmdleten för att hämta innehållet i filen CopyFromFile.txt.</span><span class="sxs-lookup"><span data-stu-id="4c472-131">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of the file, CopyFromFile.txt.</span></span> <span data-ttu-id="4c472-132">Parenteserna runt `Get-Content` cmdleten ser till att kommandot slutförs innan `Add-Content` kommandot börjar.</span><span class="sxs-lookup"><span data-stu-id="4c472-132">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="4c472-133">Parametern **Value** skickas till `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="4c472-133">The **Value** parameter is passed to `Add-Content`.</span></span> <span data-ttu-id="4c472-134">`Add-Content`Cmdleten lägger till data i CopyToFile.txts filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-134">The `Add-Content` cmdlet appends the data to the CopyToFile.txt file.</span></span> <span data-ttu-id="4c472-135">`Get-Content`Cmdleten visar den uppdaterade filen CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="4c472-135">The `Get-Content` cmdlet displays the updated file, CopyToFile.txt.</span></span>

### <span data-ttu-id="4c472-136">Exempel 4: Använd en variabel för att lägga till innehållet i en angiven fil till en annan fil</span><span class="sxs-lookup"><span data-stu-id="4c472-136">Example 4: Use a variable to add the contents of a specified file to another file</span></span>

<span data-ttu-id="4c472-137">Det här exemplet hämtar innehållet från en fil och lagrar innehållet i en variabel.</span><span class="sxs-lookup"><span data-stu-id="4c472-137">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="4c472-138">Variabeln används för att lägga till innehållet i en annan fil.</span><span class="sxs-lookup"><span data-stu-id="4c472-138">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="4c472-139">`Get-Content`Cmdlet: en hämtar innehållet i CopyFromFile.txt och lagrar innehållet i `$From` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4c472-139">The `Get-Content` cmdlet gets the contents of CopyFromFile.txt and stores the contents in the `$From` variable.</span></span> <span data-ttu-id="4c472-140">`Add-Content`Cmdleten använder parametern **Path** för att ange CopyToFile.txt filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="4c472-140">The `Add-Content` cmdlet uses the **Path** parameter to specify the CopyToFile.txt file in the current directory.</span></span> <span data-ttu-id="4c472-141">**Värde** parametern använder `$From` variabeln och skickar innehållet till `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="4c472-141">The **Value** parameter uses the `$From` variable and passes the content to `Add-Content`.</span></span> <span data-ttu-id="4c472-142">`Add-Content`Cmdleten uppdaterar CopyToFile.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-142">The `Add-Content` cmdlet updates the CopyToFile.txt file.</span></span> <span data-ttu-id="4c472-143">`Get-Content`Cmdleten visar CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="4c472-143">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="4c472-144">Exempel 5: skapa en ny fil och kopiera innehåll</span><span class="sxs-lookup"><span data-stu-id="4c472-144">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="4c472-145">Det här exemplet skapar en ny fil och kopierar en befintlig fils innehåll till den nya filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-145">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

<span data-ttu-id="4c472-146">`Add-Content`Cmdleten använder **sökvägen** och **värde** parametrarna för att skapa en ny fil i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="4c472-146">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span> <span data-ttu-id="4c472-147">Parametern **Value** använder `Get-Content` cmdleten för att hämta innehållet i en befintlig fil CopyFromFile.txt.</span><span class="sxs-lookup"><span data-stu-id="4c472-147">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of an existing file, CopyFromFile.txt.</span></span> <span data-ttu-id="4c472-148">Parenteserna runt `Get-Content` cmdleten ser till att kommandot slutförs innan `Add-Content` kommandot börjar.</span><span class="sxs-lookup"><span data-stu-id="4c472-148">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="4c472-149">**Värdet** parameter överför det innehåll som `Add-Content` NewFile.txt-filen uppdateras till.</span><span class="sxs-lookup"><span data-stu-id="4c472-149">The **Value** parameter passes the content to `Add-Content` which updates the NewFile.txt file.</span></span> <span data-ttu-id="4c472-150">`Get-Content`Cmdleten visar innehållet i den nya filen NewFile.txt.</span><span class="sxs-lookup"><span data-stu-id="4c472-150">The `Get-Content` cmdlet displays the contents of the new file, NewFile.txt.</span></span>

### <span data-ttu-id="4c472-151">Exempel 6: Lägg till innehåll i en skrivskyddad fil</span><span class="sxs-lookup"><span data-stu-id="4c472-151">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="4c472-152">Det här kommandot lägger till värdet i filen även om Filattributet **IsReadOnly** har angetts till true.</span><span class="sxs-lookup"><span data-stu-id="4c472-152">This command adds the value to the file even if the **IsReadOnly** file attribute is set to True.</span></span>
<span data-ttu-id="4c472-153">Stegen för att skapa en skrivskyddad fil ingår i exemplet.</span><span class="sxs-lookup"><span data-stu-id="4c472-153">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

<span data-ttu-id="4c472-154">`New-Item`Cmdleten använder parametrarna **Path** och **itemType** för att skapa filen IsReadOnlyTextFile.txt i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="4c472-154">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file IsReadOnlyTextFile.txt in the current directory.</span></span> <span data-ttu-id="4c472-155">`Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true.</span><span class="sxs-lookup"><span data-stu-id="4c472-155">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span> <span data-ttu-id="4c472-156">`Get-ChildItem`Cmdleten visar att filen är tom (0) och har attributet skrivskyddad ( `r` ).</span><span class="sxs-lookup"><span data-stu-id="4c472-156">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span> <span data-ttu-id="4c472-157">`Add-Content`Cmdleten använder parametern **Path** för att ange filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-157">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="4c472-158">Parametern **Value** innehåller text strängen som ska läggas till i filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-158">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="4c472-159">Parametern **Force** skriver texten till den skrivskyddade filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-159">The **Force** parameter writes the text to the read-only file.</span></span> <span data-ttu-id="4c472-160">`Get-Content`Cmdleten använder parametern **Path** för att visa filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="4c472-160">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="4c472-161">Om du vill ta bort det skrivskyddade attributet använder du `Set-ItemProperty` kommandot med **värdet** parameter inställt på `False` .</span><span class="sxs-lookup"><span data-stu-id="4c472-161">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

## <span data-ttu-id="4c472-162">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4c472-162">PARAMETERS</span></span>

### <span data-ttu-id="4c472-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c472-163">-Confirm</span></span>

<span data-ttu-id="4c472-164">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c472-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4c472-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="4c472-165">-Credential</span></span>

<span data-ttu-id="4c472-166">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4c472-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="4c472-167">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4c472-167">The default is the current user.</span></span>

<span data-ttu-id="4c472-168">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c472-168">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4c472-169">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="4c472-169">If you type a user name, you will be prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="4c472-170">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c472-170">This parameter is not supported by any providers installed with PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c472-171">-Encoding</span><span class="sxs-lookup"><span data-stu-id="4c472-171">-Encoding</span></span>

<span data-ttu-id="4c472-172">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="4c472-172">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="4c472-173">Standardvärdet är `Default`.</span><span class="sxs-lookup"><span data-stu-id="4c472-173">The default value is `Default`.</span></span>

<span data-ttu-id="4c472-174">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="4c472-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4c472-175">`Ascii` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="4c472-175">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="4c472-176">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="4c472-176">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="4c472-177">`BigEndianUTF32` Använder UTF-32 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="4c472-177">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="4c472-178">`Byte` Kodar en uppsättning tecken i en sekvens med byte.</span><span class="sxs-lookup"><span data-stu-id="4c472-178">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="4c472-179">`Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="4c472-179">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="4c472-180">`Oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="4c472-180">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="4c472-181">`String` Samma som **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="4c472-181">`String` Same as **Unicode**.</span></span>
- <span data-ttu-id="4c472-182">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="4c472-182">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="4c472-183">`Unknown` Samma som **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="4c472-183">`Unknown` Same as **Unicode**.</span></span>
- <span data-ttu-id="4c472-184">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="4c472-184">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="4c472-185">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4c472-185">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="4c472-186">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="4c472-186">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="4c472-187">Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c472-187">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="4c472-188">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="4c472-188">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c472-189">-Undanta</span><span class="sxs-lookup"><span data-stu-id="4c472-189">-Exclude</span></span>

<span data-ttu-id="4c472-190">Utesluter de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="4c472-190">Omits the specified items.</span></span> <span data-ttu-id="4c472-191">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="4c472-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4c472-192">Ange ett Sök vägs element eller ett mönster, till exempel **\* . txt**.</span><span class="sxs-lookup"><span data-stu-id="4c472-192">Enter a path element or pattern, such as **\*.txt**.</span></span> <span data-ttu-id="4c472-193">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4c472-193">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="4c472-194">-Filter</span><span class="sxs-lookup"><span data-stu-id="4c472-194">-Filter</span></span>

<span data-ttu-id="4c472-195">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="4c472-195">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="4c472-196">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="4c472-196">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4c472-197">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="4c472-197">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="4c472-198">**Filter** är mer effektiva än andra parametrar eftersom providern använder filter när objekt hämtas.</span><span class="sxs-lookup"><span data-stu-id="4c472-198">**Filters** are more efficient than other parameters because the provider applies filters when objects are retrieved.</span></span> <span data-ttu-id="4c472-199">Annars filtrerar PowerShell-processen efter att objekten har hämtats.</span><span class="sxs-lookup"><span data-stu-id="4c472-199">Otherwise, PowerShell processes filters after the objects are retrieved.</span></span>

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

### <span data-ttu-id="4c472-200">-Force</span><span class="sxs-lookup"><span data-stu-id="4c472-200">-Force</span></span>

<span data-ttu-id="4c472-201">Åsidosätter det skrivskyddade attributet så att du kan lägga till innehåll i en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="4c472-201">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="4c472-202">**Tvinga** åsidosätter till exempel det skrivskyddade attributet eller skapa kataloger för att slutföra en fil Sök väg, men kommer inte att försöka ändra fil behörigheter.</span><span class="sxs-lookup"><span data-stu-id="4c472-202">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="4c472-203">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="4c472-203">-Include</span></span>

<span data-ttu-id="4c472-204">Lägger bara till de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="4c472-204">Adds only the specified items.</span></span> <span data-ttu-id="4c472-205">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="4c472-205">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4c472-206">Ange ett Sök vägs element eller ett mönster, till exempel **\* . txt**.</span><span class="sxs-lookup"><span data-stu-id="4c472-206">Enter a path element or pattern, such as **\*.txt**.</span></span> <span data-ttu-id="4c472-207">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4c472-207">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="4c472-208">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4c472-208">-LiteralPath</span></span>

<span data-ttu-id="4c472-209">Anger sökvägen till de objekt som tar emot det ytterligare innehållet.</span><span class="sxs-lookup"><span data-stu-id="4c472-209">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="4c472-210">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="4c472-210">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="4c472-211">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="4c472-211">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4c472-212">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="4c472-212">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4c472-213">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="4c472-213">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c472-214">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="4c472-214">-NoNewline</span></span>

<span data-ttu-id="4c472-215">Anger att denna cmdlet inte lägger till en ny rad eller vagn retur i innehållet.</span><span class="sxs-lookup"><span data-stu-id="4c472-215">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="4c472-216">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="4c472-216">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="4c472-217">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="4c472-217">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="4c472-218">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="4c472-218">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="4c472-219">– PassThru</span><span class="sxs-lookup"><span data-stu-id="4c472-219">-PassThru</span></span>

<span data-ttu-id="4c472-220">Returnerar ett objekt som representerar det tillagda innehållet.</span><span class="sxs-lookup"><span data-stu-id="4c472-220">Returns an object representing the added content.</span></span> <span data-ttu-id="4c472-221">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4c472-221">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4c472-222">-Path</span><span class="sxs-lookup"><span data-stu-id="4c472-222">-Path</span></span>

<span data-ttu-id="4c472-223">Anger sökvägen till de objekt som tar emot det ytterligare innehållet.</span><span class="sxs-lookup"><span data-stu-id="4c472-223">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="4c472-224">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4c472-224">Wildcards are permitted.</span></span> <span data-ttu-id="4c472-225">Om du anger flera sökvägar använder du kommatecken för att avgränsa Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="4c472-225">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4c472-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="4c472-226">-Stream</span></span>

<span data-ttu-id="4c472-227">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="4c472-227">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="4c472-228">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="4c472-228">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="4c472-229">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="4c472-229">Wildcard characters are not supported.</span></span>

<span data-ttu-id="4c472-230">**Stream** är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="4c472-230">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="4c472-231">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="4c472-231">This parameter works only in file system drives.</span></span>

<span data-ttu-id="4c472-232">Du kan använda `Add-Content` cmdleten för att ändra innehållet i **zonen. unik identifierare** för den alternativa data strömmen.</span><span class="sxs-lookup"><span data-stu-id="4c472-232">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="4c472-233">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="4c472-233">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="4c472-234">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c472-234">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="4c472-235">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c472-235">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c472-236">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="4c472-236">-UseTransaction</span></span>

<span data-ttu-id="4c472-237">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c472-237">Includes the command in the active transaction.</span></span> <span data-ttu-id="4c472-238">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="4c472-238">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="4c472-239">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="4c472-239">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="4c472-240">-Värde</span><span class="sxs-lookup"><span data-stu-id="4c472-240">-Value</span></span>

<span data-ttu-id="4c472-241">Anger det innehåll som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="4c472-241">Specifies the content to be added.</span></span> <span data-ttu-id="4c472-242">Skriv en Citerad sträng, till exempel **den här informationen endast för intern användning** eller ange ett objekt som innehåller innehåll, till exempel det **datetime** -objekt som `Get-Date` genereras.</span><span class="sxs-lookup"><span data-stu-id="4c472-242">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="4c472-243">Du kan inte ange innehållet i en fil genom att ange dess sökväg, eftersom sökvägen bara är en sträng.</span><span class="sxs-lookup"><span data-stu-id="4c472-243">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="4c472-244">Du kan använda ett `Get-Content` kommando för att hämta innehållet och skicka det till **värde** parametern.</span><span class="sxs-lookup"><span data-stu-id="4c472-244">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4c472-245">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c472-245">-WhatIf</span></span>

<span data-ttu-id="4c472-246">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4c472-246">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4c472-247">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4c472-247">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4c472-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c472-248">CommonParameters</span></span>

<span data-ttu-id="4c472-249">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="4c472-249">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4c472-250">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4c472-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c472-251">INDATA</span><span class="sxs-lookup"><span data-stu-id="4c472-251">INPUTS</span></span>

### <span data-ttu-id="4c472-252">System. Object, system. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="4c472-252">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="4c472-253">Du kan skicka pipe-värden, sökvägar eller autentiseringsuppgifter till `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="4c472-253">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="4c472-254">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4c472-254">OUTPUTS</span></span>

### <span data-ttu-id="4c472-255">Ingen eller system. String</span><span class="sxs-lookup"><span data-stu-id="4c472-255">None or System.String</span></span>

<span data-ttu-id="4c472-256">När du använder parametern **Passthru** `Add-Content` genererar ett **system. String** -objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="4c472-256">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="4c472-257">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4c472-257">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4c472-258">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4c472-258">NOTES</span></span>

<span data-ttu-id="4c472-259">När du rör ett objekt till `Add-Content` konverteras objektet till en sträng innan det läggs till i objektet.</span><span class="sxs-lookup"><span data-stu-id="4c472-259">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="4c472-260">Objekt typen bestämmer sträng formatet, men formatet kan vara ett annat än standard visningen av objektet.</span><span class="sxs-lookup"><span data-stu-id="4c472-260">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="4c472-261">Om du vill kontrol lera sträng formatet använder du formateringsegenskaperna för sändnings-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c472-261">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>

<span data-ttu-id="4c472-262">Du kan också referera till `Add-Content` med dess inbyggda alias `ac` .</span><span class="sxs-lookup"><span data-stu-id="4c472-262">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="4c472-263">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="4c472-263">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="4c472-264">`Add-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="4c472-264">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4c472-265">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="4c472-265">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="4c472-266">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4c472-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="4c472-267">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4c472-267">RELATED LINKS</span></span>

[<span data-ttu-id="4c472-268">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="4c472-268">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="4c472-269">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4c472-269">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="4c472-270">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="4c472-270">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="4c472-271">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="4c472-271">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="4c472-272">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="4c472-272">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="4c472-273">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="4c472-273">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="4c472-274">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="4c472-274">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="4c472-275">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="4c472-275">Set-Content</span></span>](Set-Content.md)
