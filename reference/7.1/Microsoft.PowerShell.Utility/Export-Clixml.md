---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8e1557bca62ade784bd5b4ed5cb170bbf079b423
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "93269294"
---
# <span data-ttu-id="6d951-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="6d951-103">Export-Clixml</span></span>

## <span data-ttu-id="6d951-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6d951-104">SYNOPSIS</span></span>
<span data-ttu-id="6d951-105">Skapar en XML-baserad representation av ett objekt eller objekt och lagrar det i en fil.</span><span class="sxs-lookup"><span data-stu-id="6d951-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="6d951-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6d951-106">SYNTAX</span></span>

### <span data-ttu-id="6d951-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="6d951-107">ByPath (Default)</span></span>

```
Export-Clixml [-Depth <Int32>] [-Path] <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6d951-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="6d951-108">ByLiteralPath</span></span>

```
Export-Clixml [-Depth <Int32>] -LiteralPath <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6d951-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6d951-109">DESCRIPTION</span></span>

<span data-ttu-id="6d951-110">`Export-Clixml`Cmdlet: en skapar en XML-baserad representation av ett objekt eller objekt och lagrar den i en fil.</span><span class="sxs-lookup"><span data-stu-id="6d951-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="6d951-111">Du kan sedan använda `Import-Clixml` cmdleten för att återskapa det sparade objektet baserat på innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="6d951-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="6d951-112">Mer information om CLI finns i [språk oberoende](/dotnet/standard/language-independence).</span><span class="sxs-lookup"><span data-stu-id="6d951-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="6d951-113">Denna cmdlet liknar `ConvertTo-Xml` , förutom att den kommer att `Export-Clixml` lagra XML i en fil.</span><span class="sxs-lookup"><span data-stu-id="6d951-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="6d951-114">`ConvertTo-XML` Returnerar XML, så du kan fortsätta att bearbeta den i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d951-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="6d951-115">En värdefull användning av `Export-Clixml` Windows-datorer är att exportera autentiseringsuppgifter och säkra strängar på ett säkert sätt till XML.</span><span class="sxs-lookup"><span data-stu-id="6d951-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="6d951-116">Ett exempel finns i exempel 3.</span><span class="sxs-lookup"><span data-stu-id="6d951-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="6d951-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6d951-117">EXAMPLES</span></span>

### <span data-ttu-id="6d951-118">Exempel 1: exportera en sträng till en XML-fil</span><span class="sxs-lookup"><span data-stu-id="6d951-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="6d951-119">I det här exemplet skapas en XML-fil som lagras i den aktuella katalogen, en representation av strängen som **Detta är ett test**.</span><span class="sxs-lookup"><span data-stu-id="6d951-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test**.</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="6d951-120">Strängen `This is a test` skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6d951-120">The string `This is a test` is sent down the pipeline.</span></span> <span data-ttu-id="6d951-121">`Export-Clixml` använder parametern **Path** för att skapa en XML-fil med namnet `sample.xml` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="6d951-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="6d951-122">Exempel 2: exportera ett objekt till en XML-fil</span><span class="sxs-lookup"><span data-stu-id="6d951-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="6d951-123">Det här exemplet visar hur du exporterar ett objekt till en XML-fil och sedan skapar ett objekt genom att importera XML-filen från filen.</span><span class="sxs-lookup"><span data-stu-id="6d951-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="6d951-124">`Get-Acl`Cmdlet: en hämtar filens säkerhets Beskrivning `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="6d951-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="6d951-125">Det skickar objektet nedåt i pipelinen för att skicka säkerhets beskrivningen till `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="6d951-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="6d951-126">XML-baserad representation av objektet lagras i en fil med namnet `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="6d951-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="6d951-127">`Import-Clixml`Cmdleten skapar ett objekt från XML-filen i `FileACL.xml` filen.</span><span class="sxs-lookup"><span data-stu-id="6d951-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="6d951-128">Sedan sparas objektet i `$fileacl` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6d951-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="6d951-129">Exempel 3: kryptera ett exporterat Credential-objekt i Windows</span><span class="sxs-lookup"><span data-stu-id="6d951-129">Example 3: Encrypt an exported credential object on Windows</span></span>

<span data-ttu-id="6d951-130">I det här exemplet har du fått en autentiseringsuppgift som du har lagrat i `$Credential` variabeln genom `Get-Credential` att köra cmdleten, så du kan köra `Export-Clixml` cmdleten för att spara autentiseringsuppgifterna på disken.</span><span class="sxs-lookup"><span data-stu-id="6d951-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d951-131">`Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows.</span><span class="sxs-lookup"><span data-stu-id="6d951-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="6d951-132">På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som en oformaterad text som lagras som en Unicode-tecken mat ris.</span><span class="sxs-lookup"><span data-stu-id="6d951-132">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="6d951-133">Detta ger vissa döljande men ger inte kryptering.</span><span class="sxs-lookup"><span data-stu-id="6d951-133">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="6d951-134">`Export-Clixml`Cmdleten krypterar Credential-objekt med hjälp av Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="6d951-134">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span> <span data-ttu-id="6d951-135">Krypteringen säkerställer att endast ditt användar konto på den datorn kan dekryptera innehållet i Credential-objektet.</span><span class="sxs-lookup"><span data-stu-id="6d951-135">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span>
<span data-ttu-id="6d951-136">Den exporterade `CLIXML` filen kan inte användas på en annan dator eller av en annan användare.</span><span class="sxs-lookup"><span data-stu-id="6d951-136">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="6d951-137">I exemplet representeras filen där autentiseringsuppgiften lagras av `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="6d951-137">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="6d951-138">Ersätt **TestScript** med namnet på skriptet som du läser in autentiseringsuppgiften med.</span><span class="sxs-lookup"><span data-stu-id="6d951-138">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="6d951-139">Du skickar Credential-objektet ned till pipelinen till `Export-Clixml` och sparar det på den sökväg, `$Credxmlpath` som du angav i det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="6d951-139">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="6d951-140">Kör de sista två kommandona om du vill importera autentiseringsuppgiften automatiskt till ditt skript.</span><span class="sxs-lookup"><span data-stu-id="6d951-140">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="6d951-141">Kör `Import-Clixml` för att importera det skyddade objektet Credential till skriptet.</span><span class="sxs-lookup"><span data-stu-id="6d951-141">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="6d951-142">Den här importen eliminerar risken att exponera lösen ord i klartext i skriptet.</span><span class="sxs-lookup"><span data-stu-id="6d951-142">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

### <span data-ttu-id="6d951-143">Exempel 4: exportera ett Credential-objekt på Linux eller macOS</span><span class="sxs-lookup"><span data-stu-id="6d951-143">Example 4: Exporting a credential object on Linux or macOS</span></span>

<span data-ttu-id="6d951-144">I det här exemplet skapar vi en **PSCredential** i `$Credential` variabeln med hjälp av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6d951-144">In this example, we create a **PSCredential** in the `$Credential` variable using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6d951-145">Sedan använder vi `Export-Clixml` för att spara autentiseringsuppgifterna på disken.</span><span class="sxs-lookup"><span data-stu-id="6d951-145">Then we use `Export-Clixml` to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d951-146">`Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows.</span><span class="sxs-lookup"><span data-stu-id="6d951-146">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="6d951-147">På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som en oformaterad text som lagras som en Unicode-tecken mat ris.</span><span class="sxs-lookup"><span data-stu-id="6d951-147">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="6d951-148">Detta ger vissa döljande men ger inte kryptering.</span><span class="sxs-lookup"><span data-stu-id="6d951-148">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

   Label: String (System.String) <52D60C91>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

<span data-ttu-id="6d951-149">Utdata från `Get-Content` i det här exemplet har trunkerats för att fokusera på autentiseringsinformation i XML-filen.</span><span class="sxs-lookup"><span data-stu-id="6d951-149">The output of `Get-Content` in this example has been truncate to focus on the credential information in the XML file.</span></span> <span data-ttu-id="6d951-150">Observera att lösen ordets oformaterade text lagras i XML-filen som en Unicode-tecken mat ris som anges av `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="6d951-150">Note that the plain text value of the password is stored in the XML file as a Unicode character array as proven by `Format-Hex`.</span></span> <span data-ttu-id="6d951-151">Värdet är kodat men inte krypterat.</span><span class="sxs-lookup"><span data-stu-id="6d951-151">So the value is encoded but not encrypted.</span></span>

## <span data-ttu-id="6d951-152">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6d951-152">PARAMETERS</span></span>

### <span data-ttu-id="6d951-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6d951-153">-Confirm</span></span>

<span data-ttu-id="6d951-154">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6d951-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6d951-155">-Djup</span><span class="sxs-lookup"><span data-stu-id="6d951-155">-Depth</span></span>

<span data-ttu-id="6d951-156">Anger hur många nivåer med objekt som ingår i XML-representationen.</span><span class="sxs-lookup"><span data-stu-id="6d951-156">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="6d951-157">Standardvärdet är `2`.</span><span class="sxs-lookup"><span data-stu-id="6d951-157">The default value is `2`.</span></span>

<span data-ttu-id="6d951-158">Standardvärdet kan åsidosättas av objekt typen i `Types.ps1xml` filerna.</span><span class="sxs-lookup"><span data-stu-id="6d951-158">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="6d951-159">Mer information finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="6d951-159">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

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

### <span data-ttu-id="6d951-160">-Encoding</span><span class="sxs-lookup"><span data-stu-id="6d951-160">-Encoding</span></span>

<span data-ttu-id="6d951-161">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="6d951-161">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="6d951-162">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="6d951-162">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="6d951-163">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="6d951-163">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="6d951-164">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="6d951-164">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="6d951-165">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="6d951-165">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="6d951-166">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="6d951-166">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="6d951-167">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="6d951-167">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="6d951-168">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="6d951-168">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="6d951-169">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="6d951-169">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="6d951-170">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="6d951-170">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="6d951-171">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="6d951-171">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="6d951-172">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="6d951-172">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="6d951-173">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="6d951-173">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="6d951-174">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="6d951-174">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="6d951-175">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="6d951-175">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="6d951-176">**UTF-7** \* rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="6d951-176">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="6d951-177">I PowerShell 7,1 skrivs en varning om du anger `utf7` för **kodnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="6d951-177">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d951-178">-Force</span><span class="sxs-lookup"><span data-stu-id="6d951-178">-Force</span></span>

<span data-ttu-id="6d951-179">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="6d951-179">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="6d951-180">Gör att cmdleten tar bort det skrivskyddade attributet för utdatafilen om det behövs.</span><span class="sxs-lookup"><span data-stu-id="6d951-180">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="6d951-181">Cmdleten försöker återställa det skrivskyddade attributet när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6d951-181">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

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

### <span data-ttu-id="6d951-182">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6d951-182">-InputObject</span></span>

<span data-ttu-id="6d951-183">Anger det objekt som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="6d951-183">Specifies the object to be converted.</span></span> <span data-ttu-id="6d951-184">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="6d951-184">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="6d951-185">Du kan också skicka pipe-objekt till `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="6d951-185">You can also pipe objects to `Export-Clixml`.</span></span>

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

### <span data-ttu-id="6d951-186">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6d951-186">-LiteralPath</span></span>

<span data-ttu-id="6d951-187">Anger sökvägen till filen där XML-representationen av objektet kommer att lagras.</span><span class="sxs-lookup"><span data-stu-id="6d951-187">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="6d951-188">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="6d951-188">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="6d951-189">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="6d951-189">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6d951-190">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="6d951-190">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6d951-191">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="6d951-191">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d951-192">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="6d951-192">-NoClobber</span></span>

<span data-ttu-id="6d951-193">Anger att cmdleten inte skriver över innehållet i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="6d951-193">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="6d951-194">Om en fil finns på den angivna sökvägen skrivs filen som standard `Export-Clixml` utan varning.</span><span class="sxs-lookup"><span data-stu-id="6d951-194">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="6d951-195">-Path</span><span class="sxs-lookup"><span data-stu-id="6d951-195">-Path</span></span>

<span data-ttu-id="6d951-196">Anger sökvägen till filen där XML-representationen av objektet kommer att lagras.</span><span class="sxs-lookup"><span data-stu-id="6d951-196">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

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

### <span data-ttu-id="6d951-197">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6d951-197">-WhatIf</span></span>

<span data-ttu-id="6d951-198">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="6d951-198">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6d951-199">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6d951-199">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="6d951-200">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d951-200">CommonParameters</span></span>

<span data-ttu-id="6d951-201">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6d951-201">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d951-202">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6d951-202">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d951-203">INDATA</span><span class="sxs-lookup"><span data-stu-id="6d951-203">INPUTS</span></span>

### <span data-ttu-id="6d951-204">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6d951-204">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6d951-205">Du kan pipelina ett objekt till `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="6d951-205">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="6d951-206">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6d951-206">OUTPUTS</span></span>

### <span data-ttu-id="6d951-207">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="6d951-207">System.IO.FileInfo</span></span>

<span data-ttu-id="6d951-208">`Export-Clixml` skapar en fil som innehåller XML.</span><span class="sxs-lookup"><span data-stu-id="6d951-208">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="6d951-209">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6d951-209">NOTES</span></span>

## <span data-ttu-id="6d951-210">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6d951-210">RELATED LINKS</span></span>

[<span data-ttu-id="6d951-211">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="6d951-211">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="6d951-212">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="6d951-212">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="6d951-213">Exportera-CSV</span><span class="sxs-lookup"><span data-stu-id="6d951-213">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="6d951-214">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="6d951-214">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="6d951-215">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="6d951-215">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="6d951-216">Lagra autentiseringsuppgifter på ett säkert sätt på disken</span><span class="sxs-lookup"><span data-stu-id="6d951-216">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="6d951-217">Använd PowerShell för att skicka autentiseringsuppgifter till äldre system</span><span class="sxs-lookup"><span data-stu-id="6d951-217">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="6d951-218">Windows. Security. Cryptography. DataProtection</span><span class="sxs-lookup"><span data-stu-id="6d951-218">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
