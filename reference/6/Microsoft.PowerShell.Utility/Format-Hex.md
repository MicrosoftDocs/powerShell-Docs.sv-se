---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267087"
---
# <span data-ttu-id="66e6b-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="66e6b-103">Format-Hex</span></span>

## <span data-ttu-id="66e6b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="66e6b-104">SYNOPSIS</span></span>

<span data-ttu-id="66e6b-105">Visar en fil eller andra indata som hexadecimala.</span><span class="sxs-lookup"><span data-stu-id="66e6b-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="66e6b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="66e6b-106">SYNTAX</span></span>

### <span data-ttu-id="66e6b-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="66e6b-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="66e6b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="66e6b-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="66e6b-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="66e6b-109">InputObject</span></span>

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="66e6b-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="66e6b-110">DESCRIPTION</span></span>

<span data-ttu-id="66e6b-111">`Format-Hex`Cmdleten visar en fil eller andra indata som hexadecimala värden.</span><span class="sxs-lookup"><span data-stu-id="66e6b-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="66e6b-112">Om du vill fastställa förskjutningen för ett Character från utdata lägger du till numret längst till vänster i raden till talet överst i kolumnen för det aktuella specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="66e6b-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="66e6b-113">`Format-Hex`Cmdleten kan hjälpa dig att avgöra filtypen för en skadad fil eller en fil som kanske inte har fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="66e6b-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="66e6b-114">Du kan köra denna cmdlet och läsa de hexadecimala utdata för att hämta fil information.</span><span class="sxs-lookup"><span data-stu-id="66e6b-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="66e6b-115">När `Format-Hex` du använder på en fil, ignorerar cmdleten rad matnings tecken och returnerar hela innehållet i en fil i en sträng med rad matnings tecken bevarade.</span><span class="sxs-lookup"><span data-stu-id="66e6b-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="66e6b-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="66e6b-116">EXAMPLES</span></span>

### <span data-ttu-id="66e6b-117">Exempel 1: hämta den hexadecimala representationen av en sträng</span><span class="sxs-lookup"><span data-stu-id="66e6b-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="66e6b-118">Det här kommandot returnerar de hexadecimala värdena för en sträng.</span><span class="sxs-lookup"><span data-stu-id="66e6b-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="66e6b-119">Strängen **Hello World** skickas ned pipelinen till `Format-Hex` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="66e6b-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="66e6b-120">De hexadecimala utdata från `Format-Hex` visar värdena för varje tecken i strängen.</span><span class="sxs-lookup"><span data-stu-id="66e6b-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="66e6b-121">Exempel 2: hitta en filtyp från hexadecimala utdata</span><span class="sxs-lookup"><span data-stu-id="66e6b-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="66e6b-122">I det här exemplet används de hexadecimala utdata för att fastställa filtypen.</span><span class="sxs-lookup"><span data-stu-id="66e6b-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="66e6b-123">Cmdleten visar filens fullständiga sökväg och de hexadecimala värdena.</span><span class="sxs-lookup"><span data-stu-id="66e6b-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="66e6b-124">Testa följande kommando genom att göra en kopia av en befintlig PDF-fil på den lokala datorn och byta namn på den kopierade filen till `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="66e6b-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

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

<span data-ttu-id="66e6b-125">`Format-Hex`Cmdleten använder parametern **Path** för att ange ett fil namn i den aktuella katalogen, **File. t7f**.</span><span class="sxs-lookup"><span data-stu-id="66e6b-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, **File.t7f**.</span></span> <span data-ttu-id="66e6b-126">Fil namns tillägget **. t7f** är ovanligt, men den hexadecimala utdata **% PDF** visar att det är en PDF-fil.</span><span class="sxs-lookup"><span data-stu-id="66e6b-126">The file extension **.t7f** is uncommon, but the hexadecimal output **%PDF** shows that it is a PDF file.</span></span>

## <span data-ttu-id="66e6b-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="66e6b-127">PARAMETERS</span></span>

### <span data-ttu-id="66e6b-128">-Encoding</span><span class="sxs-lookup"><span data-stu-id="66e6b-128">-Encoding</span></span>

<span data-ttu-id="66e6b-129">Anger kodningen för utdata.</span><span class="sxs-lookup"><span data-stu-id="66e6b-129">Specifies the encoding of the output.</span></span> <span data-ttu-id="66e6b-130">Detta gäller endast för `[string]` inmatade.</span><span class="sxs-lookup"><span data-stu-id="66e6b-130">This only applies to `[string]` input.</span></span> <span data-ttu-id="66e6b-131">Parametern har ingen påverkan på numeriska typer.</span><span class="sxs-lookup"><span data-stu-id="66e6b-131">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="66e6b-132">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="66e6b-132">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="66e6b-133">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="66e6b-133">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="66e6b-134">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="66e6b-134">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="66e6b-135">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="66e6b-135">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="66e6b-136">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="66e6b-136">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="66e6b-137">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="66e6b-137">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="66e6b-138">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="66e6b-138">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="66e6b-139">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="66e6b-139">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="66e6b-140">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="66e6b-140">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="66e6b-141">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="66e6b-141">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="66e6b-142">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="66e6b-142">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="66e6b-143">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="66e6b-143">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="66e6b-144">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="66e6b-144">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="66e6b-145">– InputObject</span><span class="sxs-lookup"><span data-stu-id="66e6b-145">-InputObject</span></span>

<span data-ttu-id="66e6b-146">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="66e6b-146">Used for pipeline input.</span></span> <span data-ttu-id="66e6b-147">Pipeline-inmatare stöder endast vissa skalära typer och `[system.io.fileinfo]` instanser för rör dragning `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="66e6b-147">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="66e6b-148">De skalära typer som stöds är:</span><span class="sxs-lookup"><span data-stu-id="66e6b-148">The supported scalar types are:</span></span>

- <span data-ttu-id="66e6b-149">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="66e6b-149">`[string]`, `[char]`</span></span>
- <span data-ttu-id="66e6b-150">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="66e6b-150">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="66e6b-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="66e6b-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="66e6b-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="66e6b-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="66e6b-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="66e6b-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="66e6b-154">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="66e6b-154">`[single]`, `[float]`, `[double]`</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="66e6b-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="66e6b-155">-LiteralPath</span></span>

<span data-ttu-id="66e6b-156">Anger den fullständiga sökvägen till en fil.</span><span class="sxs-lookup"><span data-stu-id="66e6b-156">Specifies the complete path to a file.</span></span> <span data-ttu-id="66e6b-157">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="66e6b-157">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="66e6b-158">Den här parametern accepterar inte jokertecken.</span><span class="sxs-lookup"><span data-stu-id="66e6b-158">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="66e6b-159">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="66e6b-159">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="66e6b-160">Om parametern **LiteralPath** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="66e6b-160">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="66e6b-161">PowerShell tolkar inga tecken i en enskild citat sträng som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="66e6b-161">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="66e6b-162">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="66e6b-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="66e6b-163">-Path</span><span class="sxs-lookup"><span data-stu-id="66e6b-163">-Path</span></span>

<span data-ttu-id="66e6b-164">Anger sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="66e6b-164">Specifies the path to files.</span></span> <span data-ttu-id="66e6b-165">`.`Ange den aktuella platsen genom att använda en punkt ().</span><span class="sxs-lookup"><span data-stu-id="66e6b-165">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="66e6b-166">Jokertecknet ( `*` ) accepteras och kan användas för att ange alla objekt på en plats.</span><span class="sxs-lookup"><span data-stu-id="66e6b-166">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="66e6b-167">Om parametern **Path** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="66e6b-167">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="66e6b-168">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="66e6b-168">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="66e6b-169">– RAW</span><span class="sxs-lookup"><span data-stu-id="66e6b-169">-Raw</span></span>

<span data-ttu-id="66e6b-170">Den här parametern gör ingenting längre.</span><span class="sxs-lookup"><span data-stu-id="66e6b-170">This parameter no longer does anything.</span></span> <span data-ttu-id="66e6b-171">Den behålls för skript kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="66e6b-171">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="66e6b-172">-Förskjutning</span><span class="sxs-lookup"><span data-stu-id="66e6b-172">-Offset</span></span>

<span data-ttu-id="66e6b-173">Detta representerar antalet byte som ska hoppas över från att ingå i hex-utdata.</span><span class="sxs-lookup"><span data-stu-id="66e6b-173">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="66e6b-174">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="66e6b-174">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="66e6b-175">-Antal</span><span class="sxs-lookup"><span data-stu-id="66e6b-175">-Count</span></span>

<span data-ttu-id="66e6b-176">Detta representerar antalet byte som ska inkluderas i hex-utdata.</span><span class="sxs-lookup"><span data-stu-id="66e6b-176">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="66e6b-177">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="66e6b-177">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="66e6b-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="66e6b-178">CommonParameters</span></span>

<span data-ttu-id="66e6b-179">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="66e6b-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="66e6b-180">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="66e6b-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="66e6b-181">INDATA</span><span class="sxs-lookup"><span data-stu-id="66e6b-181">INPUTS</span></span>

### <span data-ttu-id="66e6b-182">System. String</span><span class="sxs-lookup"><span data-stu-id="66e6b-182">System.String</span></span>

<span data-ttu-id="66e6b-183">Du kan skicka vidare en sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="66e6b-183">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="66e6b-184">UTDATA</span><span class="sxs-lookup"><span data-stu-id="66e6b-184">OUTPUTS</span></span>

### <span data-ttu-id="66e6b-185">Microsoft. PowerShell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="66e6b-185">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="66e6b-186">Den här cmdleten returnerar en **ByteCollection**.</span><span class="sxs-lookup"><span data-stu-id="66e6b-186">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="66e6b-187">Det här objektet representerar en samling byte.</span><span class="sxs-lookup"><span data-stu-id="66e6b-187">This object represents a collection of bytes.</span></span> <span data-ttu-id="66e6b-188">Den innehåller metoder som konverterar mängden med byte till en sträng formaterad som varje rad utdata som returneras av `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="66e6b-188">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="66e6b-189">Om du anger **sökvägen** eller parametern **LiteralPath** innehåller objektet också sökvägen till filen som innehåller varje byte.</span><span class="sxs-lookup"><span data-stu-id="66e6b-189">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="66e6b-190">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="66e6b-190">NOTES</span></span>

<span data-ttu-id="66e6b-191">Den högra kolumnen med utdata försöker återge byte som ASCII-tecken:</span><span class="sxs-lookup"><span data-stu-id="66e6b-191">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="66e6b-192">I allmänhet tolkas varje byte som en Unicode-kodtyp, vilket innebär att:</span><span class="sxs-lookup"><span data-stu-id="66e6b-192">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="66e6b-193">Skrivbara ASCII-tecken återges alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="66e6b-193">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="66e6b-194">UTF-8-tecken i flera byte återges aldrig korrekt</span><span class="sxs-lookup"><span data-stu-id="66e6b-194">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="66e6b-195">UTF-16-tecken återges på rätt sätt endast om deras höga byte-byte inträffar `NUL` .</span><span class="sxs-lookup"><span data-stu-id="66e6b-195">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="66e6b-196">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="66e6b-196">RELATED LINKS</span></span>

[<span data-ttu-id="66e6b-197">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="66e6b-197">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="66e6b-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="66e6b-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="66e6b-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="66e6b-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="66e6b-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="66e6b-200">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="66e6b-201">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="66e6b-201">Format-Wide</span></span>](Format-Wide.md)
