---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8485591165cce0425c85d52fbd31d40614af6249
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265113"
---
# <span data-ttu-id="aaf43-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="aaf43-103">Export-Clixml</span></span>

## <span data-ttu-id="aaf43-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aaf43-104">SYNOPSIS</span></span>
<span data-ttu-id="aaf43-105">Skapar en XML-baserad representation av ett objekt eller objekt och lagrar det i en fil.</span><span class="sxs-lookup"><span data-stu-id="aaf43-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="aaf43-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aaf43-106">SYNTAX</span></span>

### <span data-ttu-id="aaf43-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="aaf43-107">ByPath (Default)</span></span>

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aaf43-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="aaf43-108">ByLiteralPath</span></span>

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aaf43-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aaf43-109">DESCRIPTION</span></span>

<span data-ttu-id="aaf43-110">`Export-Clixml`Cmdlet: en skapar en XML-baserad representation av ett objekt eller objekt och lagrar den i en fil.</span><span class="sxs-lookup"><span data-stu-id="aaf43-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="aaf43-111">Du kan sedan använda `Import-Clixml` cmdleten för att återskapa det sparade objektet baserat på innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="aaf43-112">Mer information om CLI finns i [språk oberoende](/dotnet/standard/language-independence).</span><span class="sxs-lookup"><span data-stu-id="aaf43-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="aaf43-113">Denna cmdlet liknar `ConvertTo-Xml` , förutom att den kommer att `Export-Clixml` lagra XML i en fil.</span><span class="sxs-lookup"><span data-stu-id="aaf43-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="aaf43-114">`ConvertTo-XML` Returnerar XML, så du kan fortsätta att bearbeta den i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aaf43-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="aaf43-115">En värdefull användning av `Export-Clixml` Windows-datorer är att exportera autentiseringsuppgifter och säkra strängar på ett säkert sätt till XML.</span><span class="sxs-lookup"><span data-stu-id="aaf43-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="aaf43-116">Ett exempel finns i exempel 3.</span><span class="sxs-lookup"><span data-stu-id="aaf43-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="aaf43-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aaf43-117">EXAMPLES</span></span>

### <span data-ttu-id="aaf43-118">Exempel 1: exportera en sträng till en XML-fil</span><span class="sxs-lookup"><span data-stu-id="aaf43-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="aaf43-119">I det här exemplet skapas en XML-fil som lagras i den aktuella katalogen, en representation av strängen som **Detta är ett test**.</span><span class="sxs-lookup"><span data-stu-id="aaf43-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test**.</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="aaf43-120">Strängen som **Detta är ett test** skickas ned i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-120">The string **This is a test** is sent down the pipeline.</span></span> <span data-ttu-id="aaf43-121">`Export-Clixml` använder parametern **Path** för att skapa en XML-fil med namnet `sample.xml` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="aaf43-122">Exempel 2: exportera ett objekt till en XML-fil</span><span class="sxs-lookup"><span data-stu-id="aaf43-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="aaf43-123">Det här exemplet visar hur du exporterar ett objekt till en XML-fil och sedan skapar ett objekt genom att importera XML-filen från filen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="aaf43-124">`Get-Acl`Cmdlet: en hämtar filens säkerhets Beskrivning `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="aaf43-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="aaf43-125">Det skickar objektet nedåt i pipelinen för att skicka säkerhets beskrivningen till `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="aaf43-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="aaf43-126">XML-baserad representation av objektet lagras i en fil med namnet `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="aaf43-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="aaf43-127">`Import-Clixml`Cmdleten skapar ett objekt från XML-filen i `FileACL.xml` filen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="aaf43-128">Sedan sparas objektet i `$fileacl` variabeln.</span><span class="sxs-lookup"><span data-stu-id="aaf43-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="aaf43-129">Exempel 3: kryptera ett exporterat Credential-objekt</span><span class="sxs-lookup"><span data-stu-id="aaf43-129">Example 3: Encrypt an exported credential object</span></span>

<span data-ttu-id="aaf43-130">I det här exemplet har du fått en autentiseringsuppgift som du har lagrat i `$Credential` variabeln genom `Get-Credential` att köra cmdleten, så du kan köra `Export-Clixml` cmdleten för att spara autentiseringsuppgifterna på disken.</span><span class="sxs-lookup"><span data-stu-id="aaf43-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aaf43-131">`Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows.</span><span class="sxs-lookup"><span data-stu-id="aaf43-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="aaf43-132">På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="aaf43-132">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="aaf43-133">`Export-Clixml`Cmdleten krypterar Credential-objekt med hjälp av Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="aaf43-133">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="aaf43-134">Krypteringen säkerställer att endast ditt användar konto på den datorn kan dekryptera innehållet i Credential-objektet.</span><span class="sxs-lookup"><span data-stu-id="aaf43-134">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span> <span data-ttu-id="aaf43-135">Den exporterade `CLIXML` filen kan inte användas på en annan dator eller av en annan användare.</span><span class="sxs-lookup"><span data-stu-id="aaf43-135">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="aaf43-136">I exemplet representeras filen där autentiseringsuppgiften lagras av `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="aaf43-136">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="aaf43-137">Ersätt **TestScript** med namnet på skriptet som du läser in autentiseringsuppgiften med.</span><span class="sxs-lookup"><span data-stu-id="aaf43-137">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="aaf43-138">Du skickar Credential-objektet ned till pipelinen till `Export-Clixml` och sparar det på den sökväg, `$Credxmlpath` som du angav i det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="aaf43-138">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="aaf43-139">Kör de sista två kommandona om du vill importera autentiseringsuppgiften automatiskt till ditt skript.</span><span class="sxs-lookup"><span data-stu-id="aaf43-139">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="aaf43-140">Kör `Import-Clixml` för att importera det skyddade objektet Credential till skriptet.</span><span class="sxs-lookup"><span data-stu-id="aaf43-140">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="aaf43-141">Den här importen eliminerar risken att exponera lösen ord i klartext i skriptet.</span><span class="sxs-lookup"><span data-stu-id="aaf43-141">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="aaf43-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aaf43-142">PARAMETERS</span></span>

### <span data-ttu-id="aaf43-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aaf43-143">-Confirm</span></span>

<span data-ttu-id="aaf43-144">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aaf43-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aaf43-145">-Djup</span><span class="sxs-lookup"><span data-stu-id="aaf43-145">-Depth</span></span>

<span data-ttu-id="aaf43-146">Anger hur många nivåer med objekt som ingår i XML-representationen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-146">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="aaf43-147">Standardvärdet är `2`.</span><span class="sxs-lookup"><span data-stu-id="aaf43-147">The default value is `2`.</span></span>

<span data-ttu-id="aaf43-148">Standardvärdet kan åsidosättas av objekt typen i `Types.ps1xml` filerna.</span><span class="sxs-lookup"><span data-stu-id="aaf43-148">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="aaf43-149">Mer information finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="aaf43-149">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aaf43-150">-Encoding</span><span class="sxs-lookup"><span data-stu-id="aaf43-150">-Encoding</span></span>

<span data-ttu-id="aaf43-151">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-151">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="aaf43-152">Standardvärdet är **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="aaf43-152">The default value is **Unicode**.</span></span>

<span data-ttu-id="aaf43-153">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="aaf43-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="aaf43-154">`ASCII` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="aaf43-154">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="aaf43-155">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="aaf43-155">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="aaf43-156">`Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="aaf43-156">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="aaf43-157">`OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="aaf43-157">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="aaf43-158">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="aaf43-158">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="aaf43-159">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="aaf43-159">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="aaf43-160">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aaf43-160">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="aaf43-161">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="aaf43-161">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aaf43-162">-Force</span><span class="sxs-lookup"><span data-stu-id="aaf43-162">-Force</span></span>

<span data-ttu-id="aaf43-163">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="aaf43-163">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="aaf43-164">Gör att cmdleten tar bort det skrivskyddade attributet för utdatafilen om det behövs.</span><span class="sxs-lookup"><span data-stu-id="aaf43-164">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="aaf43-165">Cmdleten försöker återställa det skrivskyddade attributet när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="aaf43-165">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

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

### <span data-ttu-id="aaf43-166">– InputObject</span><span class="sxs-lookup"><span data-stu-id="aaf43-166">-InputObject</span></span>

<span data-ttu-id="aaf43-167">Anger det objekt som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="aaf43-167">Specifies the object to be converted.</span></span> <span data-ttu-id="aaf43-168">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="aaf43-168">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="aaf43-169">Du kan också skicka pipe-objekt till `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="aaf43-169">You can also pipe objects to `Export-Clixml`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aaf43-170">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aaf43-170">-LiteralPath</span></span>

<span data-ttu-id="aaf43-171">Anger sökvägen till filen där XML-representationen av objektet kommer att lagras.</span><span class="sxs-lookup"><span data-stu-id="aaf43-171">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="aaf43-172">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="aaf43-172">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="aaf43-173">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aaf43-173">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="aaf43-174">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="aaf43-174">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="aaf43-175">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="aaf43-175">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aaf43-176">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="aaf43-176">-NoClobber</span></span>

<span data-ttu-id="aaf43-177">Anger att cmdleten inte skriver över innehållet i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="aaf43-177">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="aaf43-178">Om en fil finns på den angivna sökvägen skrivs filen som standard `Export-Clixml` utan varning.</span><span class="sxs-lookup"><span data-stu-id="aaf43-178">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aaf43-179">-Path</span><span class="sxs-lookup"><span data-stu-id="aaf43-179">-Path</span></span>

<span data-ttu-id="aaf43-180">Anger sökvägen till filen där XML-representationen av objektet kommer att lagras.</span><span class="sxs-lookup"><span data-stu-id="aaf43-180">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aaf43-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aaf43-181">-WhatIf</span></span>

<span data-ttu-id="aaf43-182">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="aaf43-182">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="aaf43-183">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="aaf43-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="aaf43-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aaf43-184">CommonParameters</span></span>

<span data-ttu-id="aaf43-185">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aaf43-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aaf43-186">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aaf43-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aaf43-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="aaf43-187">INPUTS</span></span>

### <span data-ttu-id="aaf43-188">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="aaf43-188">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="aaf43-189">Du kan pipelina ett objekt till `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="aaf43-189">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="aaf43-190">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aaf43-190">OUTPUTS</span></span>

### <span data-ttu-id="aaf43-191">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="aaf43-191">System.IO.FileInfo</span></span>

<span data-ttu-id="aaf43-192">`Export-Clixml` skapar en fil som innehåller XML.</span><span class="sxs-lookup"><span data-stu-id="aaf43-192">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="aaf43-193">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aaf43-193">NOTES</span></span>

## <span data-ttu-id="aaf43-194">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aaf43-194">RELATED LINKS</span></span>

[<span data-ttu-id="aaf43-195">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="aaf43-195">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="aaf43-196">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="aaf43-196">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="aaf43-197">Exportera-CSV</span><span class="sxs-lookup"><span data-stu-id="aaf43-197">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="aaf43-198">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="aaf43-198">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="aaf43-199">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="aaf43-199">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="aaf43-200">Lagra autentiseringsuppgifter på ett säkert sätt på disken</span><span class="sxs-lookup"><span data-stu-id="aaf43-200">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="aaf43-201">Använd PowerShell för att skicka autentiseringsuppgifter till äldre system</span><span class="sxs-lookup"><span data-stu-id="aaf43-201">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="aaf43-202">Windows. Security. Cryptography. DataProtection</span><span class="sxs-lookup"><span data-stu-id="aaf43-202">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
