---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 6cb02f1c6f2583ce4146356fac3553e99a54c7c2
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262887"
---
# <span data-ttu-id="c75e9-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="c75e9-103">Format-Hex</span></span>

## <span data-ttu-id="c75e9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c75e9-104">SYNOPSIS</span></span>

<span data-ttu-id="c75e9-105">Visar en fil eller andra indata som hexadecimala.</span><span class="sxs-lookup"><span data-stu-id="c75e9-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="c75e9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c75e9-106">SYNTAX</span></span>

### <span data-ttu-id="c75e9-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="c75e9-107">Path (Default)</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="c75e9-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c75e9-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="c75e9-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="c75e9-109">ByInputObject</span></span>
```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="c75e9-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c75e9-110">DESCRIPTION</span></span>

<span data-ttu-id="c75e9-111">`Format-Hex`Cmdleten visar en fil eller andra indata som hexadecimala värden.</span><span class="sxs-lookup"><span data-stu-id="c75e9-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="c75e9-112">Om du vill fastställa förskjutningen för ett Character från utdata lägger du till numret längst till vänster i raden till talet överst i kolumnen för det aktuella specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="c75e9-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="c75e9-113">`Format-Hex`Cmdleten kan hjälpa dig att avgöra filtypen för en skadad fil eller en fil som kanske inte har fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="c75e9-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="c75e9-114">Du kan köra denna cmdlet och läsa de hexadecimala utdata för att hämta fil information.</span><span class="sxs-lookup"><span data-stu-id="c75e9-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="c75e9-115">När `Format-Hex` du använder på en fil, ignorerar cmdleten rad matnings tecken och returnerar hela innehållet i en fil i en sträng med rad matnings tecken bevarade.</span><span class="sxs-lookup"><span data-stu-id="c75e9-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="c75e9-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c75e9-116">EXAMPLES</span></span>

### <span data-ttu-id="c75e9-117">Exempel 1: hämta den hexadecimala representationen av en sträng</span><span class="sxs-lookup"><span data-stu-id="c75e9-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="c75e9-118">Det här kommandot returnerar de hexadecimala värdena för en sträng.</span><span class="sxs-lookup"><span data-stu-id="c75e9-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

<span data-ttu-id="c75e9-119">Strängen **Hello World** skickas ned pipelinen till `Format-Hex` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c75e9-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="c75e9-120">De hexadecimala utdata från `Format-Hex` visar värdena för varje tecken i strängen.</span><span class="sxs-lookup"><span data-stu-id="c75e9-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="c75e9-121">Exempel 2: hitta en filtyp från hexadecimala utdata</span><span class="sxs-lookup"><span data-stu-id="c75e9-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="c75e9-122">I det här exemplet används de hexadecimala utdata för att fastställa filtypen.</span><span class="sxs-lookup"><span data-stu-id="c75e9-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="c75e9-123">Cmdleten visar filens fullständiga sökväg och de hexadecimala värdena.</span><span class="sxs-lookup"><span data-stu-id="c75e9-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="c75e9-124">Testa följande kommando genom att göra en kopia av en befintlig PDF-fil på den lokala datorn och byta namn på den kopierade filen till `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="c75e9-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

<span data-ttu-id="c75e9-125">`Format-Hex`Cmdleten använder parametern **Path** för att ange ett fil namn i den aktuella katalogen `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="c75e9-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="c75e9-126">Fil namns tillägget `.t7f` är ovanligt, men det hexadecimala resultatet `%PDF` visar att det är en PDF-fil.</span><span class="sxs-lookup"><span data-stu-id="c75e9-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="c75e9-127">I det här exemplet används **Count** -parametern för att begränsa utdata till den första 48 byten av filen.</span><span class="sxs-lookup"><span data-stu-id="c75e9-127">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="c75e9-128">Exempel 3: formatera en matris med olika data typer</span><span class="sxs-lookup"><span data-stu-id="c75e9-128">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="c75e9-129">I det här exemplet används en matris med olika data typer för att markera hur `Format-Hex` hanterar dem i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c75e9-129">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="c75e9-130">Varje objekt skickas genom pipeline och processen individuellt.</span><span class="sxs-lookup"><span data-stu-id="c75e9-130">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="c75e9-131">Men om det är numeriskt data och det intilliggande objektet också är numeriskt, kommer det att gruppera dem i ett enda utdata-block.</span><span class="sxs-lookup"><span data-stu-id="c75e9-131">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾­Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="c75e9-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c75e9-132">PARAMETERS</span></span>

### <span data-ttu-id="c75e9-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c75e9-133">-Encoding</span></span>

<span data-ttu-id="c75e9-134">Anger kodningen för inmatade strängar.</span><span class="sxs-lookup"><span data-stu-id="c75e9-134">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="c75e9-135">Detta gäller endast för `[string]` inmatade.</span><span class="sxs-lookup"><span data-stu-id="c75e9-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="c75e9-136">Parametern har ingen påverkan på numeriska typer.</span><span class="sxs-lookup"><span data-stu-id="c75e9-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="c75e9-137">Värdet för utdata är alltid `utf8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="c75e9-137">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="c75e9-138">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="c75e9-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c75e9-139">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="c75e9-139">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c75e9-140">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="c75e9-140">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c75e9-141">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="c75e9-141">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c75e9-142">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="c75e9-142">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c75e9-143">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="c75e9-143">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c75e9-144">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="c75e9-144">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="c75e9-145">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="c75e9-145">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c75e9-146">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="c75e9-146">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c75e9-147">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="c75e9-147">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c75e9-148">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="c75e9-148">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c75e9-149">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="c75e9-149">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75e9-150">– InputObject</span><span class="sxs-lookup"><span data-stu-id="c75e9-150">-InputObject</span></span>

<span data-ttu-id="c75e9-151">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="c75e9-151">Used for pipeline input.</span></span> <span data-ttu-id="c75e9-152">Pipeline-inmatare stöder endast vissa skalära typer och `[system.io.fileinfo]` instanser för rör dragning `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="c75e9-152">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="c75e9-153">De skalära typer som stöds är:</span><span class="sxs-lookup"><span data-stu-id="c75e9-153">The supported scalar types are:</span></span>

- <span data-ttu-id="c75e9-154">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="c75e9-154">`[string]`, `[char]`</span></span>
- <span data-ttu-id="c75e9-155">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="c75e9-155">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="c75e9-156">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="c75e9-156">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="c75e9-157">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="c75e9-157">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="c75e9-158">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="c75e9-158">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="c75e9-159">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="c75e9-159">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="c75e9-160">Innan PowerShell 6,2 `Format-Hex` skulle hantera en pipeline-inmatare med flera indatatyper genom att gruppera alla som-objekt tillsammans.</span><span class="sxs-lookup"><span data-stu-id="c75e9-160">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="c75e9-161">Nu hanterar den varje enskilt objekt när det passerar genom pipelinen och kommer inte att gruppera objekt tillsammans om inte samma objekt är intilliggande.</span><span class="sxs-lookup"><span data-stu-id="c75e9-161">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

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

### <span data-ttu-id="c75e9-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c75e9-162">-LiteralPath</span></span>

<span data-ttu-id="c75e9-163">Anger den fullständiga sökvägen till en fil.</span><span class="sxs-lookup"><span data-stu-id="c75e9-163">Specifies the complete path to a file.</span></span> <span data-ttu-id="c75e9-164">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c75e9-164">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="c75e9-165">Den här parametern accepterar inte jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c75e9-165">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="c75e9-166">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="c75e9-166">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="c75e9-167">Om parametern **LiteralPath** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c75e9-167">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="c75e9-168">PowerShell tolkar inga tecken i en enskild citat sträng som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="c75e9-168">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="c75e9-169">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="c75e9-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c75e9-170">-Path</span><span class="sxs-lookup"><span data-stu-id="c75e9-170">-Path</span></span>

<span data-ttu-id="c75e9-171">Anger sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="c75e9-171">Specifies the path to files.</span></span> <span data-ttu-id="c75e9-172">`.`Ange den aktuella platsen genom att använda en punkt ().</span><span class="sxs-lookup"><span data-stu-id="c75e9-172">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="c75e9-173">Jokertecknet ( `*` ) accepteras och kan användas för att ange alla objekt på en plats.</span><span class="sxs-lookup"><span data-stu-id="c75e9-173">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="c75e9-174">Om parametern **Path** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c75e9-174">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="c75e9-175">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="c75e9-175">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="c75e9-176">– RAW</span><span class="sxs-lookup"><span data-stu-id="c75e9-176">-Raw</span></span>

<span data-ttu-id="c75e9-177">Den här parametern gör ingenting längre.</span><span class="sxs-lookup"><span data-stu-id="c75e9-177">This parameter no longer does anything.</span></span> <span data-ttu-id="c75e9-178">Den behålls för skript kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="c75e9-178">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="c75e9-179">-Förskjutning</span><span class="sxs-lookup"><span data-stu-id="c75e9-179">-Offset</span></span>

<span data-ttu-id="c75e9-180">Detta representerar antalet byte som ska hoppas över från att ingå i hex-utdata.</span><span class="sxs-lookup"><span data-stu-id="c75e9-180">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="c75e9-181">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="c75e9-181">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="c75e9-182">-Antal</span><span class="sxs-lookup"><span data-stu-id="c75e9-182">-Count</span></span>

<span data-ttu-id="c75e9-183">Detta representerar antalet byte som ska inkluderas i hex-utdata.</span><span class="sxs-lookup"><span data-stu-id="c75e9-183">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="c75e9-184">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="c75e9-184">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="c75e9-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c75e9-185">CommonParameters</span></span>

<span data-ttu-id="c75e9-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c75e9-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c75e9-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c75e9-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c75e9-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="c75e9-188">INPUTS</span></span>

### <span data-ttu-id="c75e9-189">System. String</span><span class="sxs-lookup"><span data-stu-id="c75e9-189">System.String</span></span>

<span data-ttu-id="c75e9-190">Du kan skicka vidare en sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c75e9-190">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="c75e9-191">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c75e9-191">OUTPUTS</span></span>

### <span data-ttu-id="c75e9-192">Microsoft. PowerShell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="c75e9-192">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="c75e9-193">Den här cmdleten returnerar en **ByteCollection**.</span><span class="sxs-lookup"><span data-stu-id="c75e9-193">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="c75e9-194">Det här objektet representerar en samling byte.</span><span class="sxs-lookup"><span data-stu-id="c75e9-194">This object represents a collection of bytes.</span></span> <span data-ttu-id="c75e9-195">Den innehåller metoder som konverterar mängden med byte till en sträng formaterad som varje rad utdata som returneras av `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="c75e9-195">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="c75e9-196">Utdata anger också de byte som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="c75e9-196">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="c75e9-197">Om du anger **sökvägen** eller **LiteralPath** -parametern innehåller objektet sökvägen till filen som innehåller varje byte.</span><span class="sxs-lookup"><span data-stu-id="c75e9-197">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="c75e9-198">Om du skickar en sträng, boolesk, heltal osv, så märks den på lämpligt sätt.</span><span class="sxs-lookup"><span data-stu-id="c75e9-198">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="c75e9-199">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c75e9-199">NOTES</span></span>

<span data-ttu-id="c75e9-200">Den högra kolumnen med utdata försöker återge byte som ASCII-tecken:</span><span class="sxs-lookup"><span data-stu-id="c75e9-200">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="c75e9-201">I allmänhet tolkas varje byte som en Unicode-kodtyp, vilket innebär att:</span><span class="sxs-lookup"><span data-stu-id="c75e9-201">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="c75e9-202">Skrivbara ASCII-tecken återges alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="c75e9-202">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="c75e9-203">UTF-8-tecken i flera byte återges aldrig korrekt</span><span class="sxs-lookup"><span data-stu-id="c75e9-203">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="c75e9-204">UTF-16-tecken återges på rätt sätt endast om deras höga byte-byte inträffar `NUL` .</span><span class="sxs-lookup"><span data-stu-id="c75e9-204">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="c75e9-205">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c75e9-205">RELATED LINKS</span></span>

[<span data-ttu-id="c75e9-206">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c75e9-206">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="c75e9-207">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="c75e9-207">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="c75e9-208">Format-List</span><span class="sxs-lookup"><span data-stu-id="c75e9-208">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="c75e9-209">Format-Table</span><span class="sxs-lookup"><span data-stu-id="c75e9-209">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="c75e9-210">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="c75e9-210">Format-Wide</span></span>](Format-Wide.md)
