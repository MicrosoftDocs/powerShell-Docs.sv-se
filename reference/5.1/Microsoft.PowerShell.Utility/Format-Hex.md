---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265088"
---
# <span data-ttu-id="2c587-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="2c587-103">Format-Hex</span></span>

## <span data-ttu-id="2c587-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2c587-104">SYNOPSIS</span></span>

<span data-ttu-id="2c587-105">Visar en fil eller andra indata som hexadecimala.</span><span class="sxs-lookup"><span data-stu-id="2c587-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="2c587-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2c587-106">SYNTAX</span></span>

### <span data-ttu-id="2c587-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="2c587-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### <span data-ttu-id="2c587-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2c587-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### <span data-ttu-id="2c587-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="2c587-109">ByInputObject</span></span>

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="2c587-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2c587-110">DESCRIPTION</span></span>

<span data-ttu-id="2c587-111">`Format-Hex`Cmdleten visar en fil eller andra indata som hexadecimala värden.</span><span class="sxs-lookup"><span data-stu-id="2c587-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="2c587-112">Om du vill fastställa förskjutningen för ett Character från utdata lägger du till numret längst till vänster i raden till talet överst i kolumnen för det aktuella specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="2c587-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="2c587-113">`Format-Hex`Cmdleten kan hjälpa dig att avgöra filtypen för en skadad fil eller en fil som kanske inte har fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="2c587-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="2c587-114">Du kan köra denna cmdlet och läsa de hexadecimala utdata för att hämta fil information.</span><span class="sxs-lookup"><span data-stu-id="2c587-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="2c587-115">När `Format-Hex` du använder på en fil, ignorerar cmdleten rad matnings tecken och returnerar hela innehållet i en fil i en sträng med rad matnings tecken bevarade.</span><span class="sxs-lookup"><span data-stu-id="2c587-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="2c587-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2c587-116">EXAMPLES</span></span>

### <span data-ttu-id="2c587-117">Exempel 1: hämta den hexadecimala representationen av en sträng</span><span class="sxs-lookup"><span data-stu-id="2c587-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="2c587-118">Det här kommandot returnerar de hexadecimala värdena för en sträng.</span><span class="sxs-lookup"><span data-stu-id="2c587-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="2c587-119">Strängen **Hello World** skickas ned pipelinen till `Format-Hex` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c587-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="2c587-120">De hexadecimala utdata från `Format-Hex` visar värdena för varje tecken i strängen.</span><span class="sxs-lookup"><span data-stu-id="2c587-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="2c587-121">Exempel 2: hitta en filtyp från hexadecimala utdata</span><span class="sxs-lookup"><span data-stu-id="2c587-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="2c587-122">I det här exemplet används de hexadecimala utdata för att fastställa filtypen.</span><span class="sxs-lookup"><span data-stu-id="2c587-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="2c587-123">Cmdleten visar filens fullständiga sökväg och de hexadecimala värdena.</span><span class="sxs-lookup"><span data-stu-id="2c587-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="2c587-124">Du testar följande kommando genom att göra en kopia av en befintlig PDF-fil på den lokala datorn och byta namn på den kopierade filen till **filen. t7f**.</span><span class="sxs-lookup"><span data-stu-id="2c587-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to **File.t7f**.</span></span>

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

<span data-ttu-id="2c587-125">`Format-Hex`Cmdleten använder parametern **Path** för att ange ett fil namn i den aktuella katalogen `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="2c587-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="2c587-126">Fil namns tillägget `.t7f` är ovanligt, men det hexadecimala resultatet `%PDF` visar att det är en PDF-fil.</span><span class="sxs-lookup"><span data-stu-id="2c587-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span>

### <span data-ttu-id="2c587-127">Exempel 3: Visa rå hexadecimala utdata</span><span class="sxs-lookup"><span data-stu-id="2c587-127">Example 3: Display raw hexadecimal output</span></span>

<span data-ttu-id="2c587-128">Som standard `Format-Hex` väljer du komprimera utdata av numeriska data typer: enkla byte eller dubbla byte-sekvenser används om värdet är tillräckligt litet.</span><span class="sxs-lookup"><span data-stu-id="2c587-128">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="2c587-129">Den **råa** parametern inaktiverar det här beteendet.</span><span class="sxs-lookup"><span data-stu-id="2c587-129">The **Raw** parameter deactivates this behavior.</span></span>

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

<span data-ttu-id="2c587-130">Observera skillnaden i utdata.</span><span class="sxs-lookup"><span data-stu-id="2c587-130">Notice the difference in output.</span></span> <span data-ttu-id="2c587-131">Parametern **RAW** visar talen som 4 byte-värden, true till deras **Int32** -typer.</span><span class="sxs-lookup"><span data-stu-id="2c587-131">The **Raw** parameter displays the numbers as 4-byte values, true to their **Int32** types.</span></span>

## <span data-ttu-id="2c587-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2c587-132">PARAMETERS</span></span>

### <span data-ttu-id="2c587-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="2c587-133">-Encoding</span></span>

<span data-ttu-id="2c587-134">Anger kodningen för utdata.</span><span class="sxs-lookup"><span data-stu-id="2c587-134">Specifies the encoding of the output.</span></span> <span data-ttu-id="2c587-135">Detta gäller endast för `[string]` inmatade.</span><span class="sxs-lookup"><span data-stu-id="2c587-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="2c587-136">Parametern har ingen påverkan på numeriska typer.</span><span class="sxs-lookup"><span data-stu-id="2c587-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="2c587-137">Standardvärdet är `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="2c587-137">The default value is `ASCII`.</span></span>

<span data-ttu-id="2c587-138">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="2c587-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2c587-139">`Ascii` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="2c587-139">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="2c587-140">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="2c587-140">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="2c587-141">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="2c587-141">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="2c587-142">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="2c587-142">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="2c587-143">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2c587-143">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="2c587-144">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="2c587-144">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="2c587-145">Icke-ASCII-tecken i indata är utdata som litterala `?` tecken som resulterar i förlust av information.</span><span class="sxs-lookup"><span data-stu-id="2c587-145">Non-ASCII characters in the input are output as literal `?` characters resulting in a loss of information.</span></span>

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c587-146">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2c587-146">-InputObject</span></span>

<span data-ttu-id="2c587-147">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="2c587-147">Used for pipeline input.</span></span> <span data-ttu-id="2c587-148">Pipeline-inmatare stöder endast vissa skalära typer och `[system.io.fileinfo]` instanser för rör dragning `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="2c587-148">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="2c587-149">De skalära typer som stöds är:</span><span class="sxs-lookup"><span data-stu-id="2c587-149">The supported scalar types are:</span></span>

- `[string]`
- `[byte]`
- <span data-ttu-id="2c587-150">`[int]`, `[int32]`</span><span class="sxs-lookup"><span data-stu-id="2c587-150">`[int]`, `[int32]`</span></span>
- <span data-ttu-id="2c587-151">`[long]`, `[int64]`</span><span class="sxs-lookup"><span data-stu-id="2c587-151">`[long]`, `[int64]`</span></span>

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2c587-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2c587-152">-LiteralPath</span></span>

<span data-ttu-id="2c587-153">Anger den fullständiga sökvägen till en fil.</span><span class="sxs-lookup"><span data-stu-id="2c587-153">Specifies the complete path to a file.</span></span> <span data-ttu-id="2c587-154">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="2c587-154">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="2c587-155">Den här parametern accepterar inte jokertecken.</span><span class="sxs-lookup"><span data-stu-id="2c587-155">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="2c587-156">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="2c587-156">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="2c587-157">Om parametern **LiteralPath** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2c587-157">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="2c587-158">PowerShell tolkar inga tecken i en enskild citat sträng som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="2c587-158">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="2c587-159">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="2c587-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c587-160">-Path</span><span class="sxs-lookup"><span data-stu-id="2c587-160">-Path</span></span>

<span data-ttu-id="2c587-161">Anger sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="2c587-161">Specifies the path to files.</span></span> <span data-ttu-id="2c587-162">`.`Ange den aktuella platsen genom att använda en punkt ().</span><span class="sxs-lookup"><span data-stu-id="2c587-162">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="2c587-163">Jokertecknet ( `*` ) accepteras och kan användas för att ange alla objekt på en plats.</span><span class="sxs-lookup"><span data-stu-id="2c587-163">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="2c587-164">Om parametern **Path** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2c587-164">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="2c587-165">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="2c587-165">To specify multiple paths to files, separate the paths with a comma.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2c587-166">– RAW</span><span class="sxs-lookup"><span data-stu-id="2c587-166">-Raw</span></span>

<span data-ttu-id="2c587-167">Som standard `Format-Hex` väljer du komprimera utdata av numeriska data typer: enkla byte eller dubbla byte-sekvenser används om värdet är tillräckligt litet.</span><span class="sxs-lookup"><span data-stu-id="2c587-167">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="2c587-168">Den **råa** parametern inaktiverar det här beteendet.</span><span class="sxs-lookup"><span data-stu-id="2c587-168">The **Raw** parameter deactivates this behavior.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c587-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2c587-169">CommonParameters</span></span>

<span data-ttu-id="2c587-170">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2c587-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2c587-171">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2c587-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2c587-172">INDATA</span><span class="sxs-lookup"><span data-stu-id="2c587-172">INPUTS</span></span>

### <span data-ttu-id="2c587-173">System. String</span><span class="sxs-lookup"><span data-stu-id="2c587-173">System.String</span></span>

<span data-ttu-id="2c587-174">Du kan skicka vidare en sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c587-174">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="2c587-175">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2c587-175">OUTPUTS</span></span>

### <span data-ttu-id="2c587-176">Microsoft. PowerShell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="2c587-176">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="2c587-177">Den här cmdleten returnerar en **ByteCollection**.</span><span class="sxs-lookup"><span data-stu-id="2c587-177">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="2c587-178">Det här objektet representerar en samling byte.</span><span class="sxs-lookup"><span data-stu-id="2c587-178">This object represents a collection of bytes.</span></span> <span data-ttu-id="2c587-179">Den innehåller metoder som konverterar mängden med byte till en sträng formaterad som varje rad utdata som returneras av `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="2c587-179">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="2c587-180">Om du anger **sökvägen** eller parametern **LiteralPath** innehåller objektet också sökvägen till filen som innehåller varje byte.</span><span class="sxs-lookup"><span data-stu-id="2c587-180">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="2c587-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2c587-181">NOTES</span></span>

<span data-ttu-id="2c587-182">Den högra kolumnen med utdata försöker återge byte som tecken:</span><span class="sxs-lookup"><span data-stu-id="2c587-182">The right-most column of output tries to render the bytes as characters:</span></span>

<span data-ttu-id="2c587-183">I allmänhet tolkas varje byte som en Unicode-kodtyp, vilket innebär att:</span><span class="sxs-lookup"><span data-stu-id="2c587-183">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="2c587-184">Skrivbara ASCII-tecken återges alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="2c587-184">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="2c587-185">UTF-8-tecken i flera byte återges aldrig korrekt</span><span class="sxs-lookup"><span data-stu-id="2c587-185">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="2c587-186">UTF-16-tecken återges på rätt sätt endast om deras höga byte-byte inträffar `NUL` .</span><span class="sxs-lookup"><span data-stu-id="2c587-186">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="2c587-187">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2c587-187">RELATED LINKS</span></span>

[<span data-ttu-id="2c587-188">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="2c587-188">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="2c587-189">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="2c587-189">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="2c587-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="2c587-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="2c587-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="2c587-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="2c587-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="2c587-192">Format-Wide</span></span>](Format-Wide.md)
