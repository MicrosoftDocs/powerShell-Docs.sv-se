---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: a45e7919b5a24189ca7f50661795ff035c38a037
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708671"
---
# <span data-ttu-id="21047-102">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="21047-102">Format-Hex</span></span>

## <span data-ttu-id="21047-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="21047-103">SYNOPSIS</span></span>

<span data-ttu-id="21047-104">Visar en fil eller andra indata som hexadecimala.</span><span class="sxs-lookup"><span data-stu-id="21047-104">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="21047-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21047-105">SYNTAX</span></span>

### <span data-ttu-id="21047-106">Sökväg</span><span class="sxs-lookup"><span data-stu-id="21047-106">Path</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="21047-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21047-107">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="21047-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="21047-108">ByInputObject</span></span>

```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="21047-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="21047-109">DESCRIPTION</span></span>

<span data-ttu-id="21047-110">`Format-Hex`Cmdleten visar en fil eller andra indata som hexadecimala värden.</span><span class="sxs-lookup"><span data-stu-id="21047-110">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="21047-111">Om du vill fastställa förskjutningen för ett Character från utdata lägger du till numret längst till vänster i raden till talet överst i kolumnen för det aktuella specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="21047-111">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="21047-112">`Format-Hex`Cmdleten kan hjälpa dig att avgöra filtypen för en skadad fil eller en fil som kanske inte har fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="21047-112">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="21047-113">Du kan köra denna cmdlet och läsa de hexadecimala utdata för att hämta fil information.</span><span class="sxs-lookup"><span data-stu-id="21047-113">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="21047-114">När `Format-Hex` du använder på en fil, ignorerar cmdleten rad matnings tecken och returnerar hela innehållet i en fil i en sträng med rad matnings tecken bevarade.</span><span class="sxs-lookup"><span data-stu-id="21047-114">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="21047-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="21047-115">EXAMPLES</span></span>

### <span data-ttu-id="21047-116">Exempel 1: hämta den hexadecimala representationen av en sträng</span><span class="sxs-lookup"><span data-stu-id="21047-116">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="21047-117">Det här kommandot returnerar de hexadecimala värdena för en sträng.</span><span class="sxs-lookup"><span data-stu-id="21047-117">This command returns the hexadecimal values of a string.</span></span>

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

<span data-ttu-id="21047-118">Strängen **Hello World** skickas ned pipelinen till `Format-Hex` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="21047-118">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="21047-119">De hexadecimala utdata från `Format-Hex` visar värdena för varje tecken i strängen.</span><span class="sxs-lookup"><span data-stu-id="21047-119">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="21047-120">Exempel 2: hitta en filtyp från hexadecimala utdata</span><span class="sxs-lookup"><span data-stu-id="21047-120">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="21047-121">I det här exemplet används de hexadecimala utdata för att fastställa filtypen.</span><span class="sxs-lookup"><span data-stu-id="21047-121">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="21047-122">Cmdleten visar filens fullständiga sökväg och de hexadecimala värdena.</span><span class="sxs-lookup"><span data-stu-id="21047-122">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="21047-123">Testa följande kommando genom att göra en kopia av en befintlig PDF-fil på den lokala datorn och byta namn på den kopierade filen till `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="21047-123">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

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

<span data-ttu-id="21047-124">`Format-Hex`Cmdleten använder parametern **Path** för att ange ett fil namn i den aktuella katalogen `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="21047-124">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="21047-125">Fil namns tillägget `.t7f` är ovanligt, men det hexadecimala resultatet `%PDF` visar att det är en PDF-fil.</span><span class="sxs-lookup"><span data-stu-id="21047-125">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="21047-126">I det här exemplet används **Count** -parametern för att begränsa utdata till den första 48 byten av filen.</span><span class="sxs-lookup"><span data-stu-id="21047-126">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="21047-127">Exempel 3: formatera en matris med olika data typer</span><span class="sxs-lookup"><span data-stu-id="21047-127">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="21047-128">I det här exemplet används en matris med olika data typer för att markera hur `Format-Hex` hanterar dem i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="21047-128">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="21047-129">Varje objekt skickas genom pipeline och processen individuellt.</span><span class="sxs-lookup"><span data-stu-id="21047-129">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="21047-130">Men om det är numeriskt data och det intilliggande objektet också är numeriskt, kommer det att gruppera dem i ett enda utdata-block.</span><span class="sxs-lookup"><span data-stu-id="21047-130">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

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
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾-Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="21047-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="21047-131">PARAMETERS</span></span>

### <span data-ttu-id="21047-132">-Encoding</span><span class="sxs-lookup"><span data-stu-id="21047-132">-Encoding</span></span>

<span data-ttu-id="21047-133">Anger kodningen för inmatade strängar.</span><span class="sxs-lookup"><span data-stu-id="21047-133">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="21047-134">Detta gäller endast för `[string]` inmatade.</span><span class="sxs-lookup"><span data-stu-id="21047-134">This only applies to `[string]` input.</span></span> <span data-ttu-id="21047-135">Parametern har ingen påverkan på numeriska typer.</span><span class="sxs-lookup"><span data-stu-id="21047-135">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="21047-136">Värdet för utdata är alltid `utf8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="21047-136">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="21047-137">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="21047-137">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="21047-138">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="21047-138">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="21047-139">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="21047-139">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="21047-140">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="21047-140">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="21047-141">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="21047-141">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="21047-142">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="21047-142">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="21047-143">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="21047-143">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="21047-144">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="21047-144">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="21047-145">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="21047-145">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="21047-146">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="21047-146">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="21047-147">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="21047-147">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="21047-148">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="21047-148">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="21047-149">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="21047-149">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="21047-150">**UTF-7** _ rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="21047-150">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="21047-151">I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ \*encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="21047-151">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21047-152">– InputObject</span><span class="sxs-lookup"><span data-stu-id="21047-152">-InputObject</span></span>

<span data-ttu-id="21047-153">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="21047-153">Used for pipeline input.</span></span> <span data-ttu-id="21047-154">Pipeline-inmatare stöder endast vissa skalära typer och `[system.io.fileinfo]` instanser för rör dragning `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="21047-154">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="21047-155">De skalära typer som stöds är:</span><span class="sxs-lookup"><span data-stu-id="21047-155">The supported scalar types are:</span></span>

- <span data-ttu-id="21047-156">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="21047-156">`[string]`, `[char]`</span></span>
- <span data-ttu-id="21047-157">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="21047-157">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="21047-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="21047-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="21047-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="21047-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="21047-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="21047-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="21047-161">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="21047-161">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="21047-162">Innan PowerShell 6,2 `Format-Hex` skulle hantera en pipeline-inmatare med flera indatatyper genom att gruppera alla som-objekt tillsammans.</span><span class="sxs-lookup"><span data-stu-id="21047-162">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="21047-163">Nu hanterar den varje enskilt objekt när det passerar genom pipelinen och kommer inte att gruppera objekt tillsammans om inte samma objekt är intilliggande.</span><span class="sxs-lookup"><span data-stu-id="21047-163">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

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

### <span data-ttu-id="21047-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21047-164">-LiteralPath</span></span>

<span data-ttu-id="21047-165">Anger den fullständiga sökvägen till en fil.</span><span class="sxs-lookup"><span data-stu-id="21047-165">Specifies the complete path to a file.</span></span> <span data-ttu-id="21047-166">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="21047-166">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="21047-167">Den här parametern accepterar inte jokertecken.</span><span class="sxs-lookup"><span data-stu-id="21047-167">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="21047-168">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="21047-168">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="21047-169">Om parametern **LiteralPath** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="21047-169">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="21047-170">PowerShell tolkar inga tecken i en enskild citat sträng som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="21047-170">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="21047-171">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="21047-171">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="21047-172">-Path</span><span class="sxs-lookup"><span data-stu-id="21047-172">-Path</span></span>

<span data-ttu-id="21047-173">Anger sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="21047-173">Specifies the path to files.</span></span> <span data-ttu-id="21047-174">`.`Ange den aktuella platsen genom att använda en punkt ().</span><span class="sxs-lookup"><span data-stu-id="21047-174">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="21047-175">Jokertecknet ( `*` ) accepteras och kan användas för att ange alla objekt på en plats.</span><span class="sxs-lookup"><span data-stu-id="21047-175">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="21047-176">Om parametern **Path** innehåller escape-tecken, omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="21047-176">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="21047-177">Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.</span><span class="sxs-lookup"><span data-stu-id="21047-177">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="21047-178">– RAW</span><span class="sxs-lookup"><span data-stu-id="21047-178">-Raw</span></span>

<span data-ttu-id="21047-179">Den här parametern gör ingenting längre.</span><span class="sxs-lookup"><span data-stu-id="21047-179">This parameter no longer does anything.</span></span> <span data-ttu-id="21047-180">Den behålls för skript kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="21047-180">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="21047-181">-Förskjutning</span><span class="sxs-lookup"><span data-stu-id="21047-181">-Offset</span></span>

<span data-ttu-id="21047-182">Detta representerar antalet byte som ska hoppas över från att ingå i hex-utdata.</span><span class="sxs-lookup"><span data-stu-id="21047-182">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="21047-183">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="21047-183">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="21047-184">-Antal</span><span class="sxs-lookup"><span data-stu-id="21047-184">-Count</span></span>

<span data-ttu-id="21047-185">Detta representerar antalet byte som ska inkluderas i hex-utdata.</span><span class="sxs-lookup"><span data-stu-id="21047-185">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="21047-186">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="21047-186">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="21047-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21047-187">CommonParameters</span></span>

<span data-ttu-id="21047-188">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21047-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21047-189">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="21047-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21047-190">INDATA</span><span class="sxs-lookup"><span data-stu-id="21047-190">INPUTS</span></span>

### <span data-ttu-id="21047-191">System. String</span><span class="sxs-lookup"><span data-stu-id="21047-191">System.String</span></span>

<span data-ttu-id="21047-192">Du kan skicka vidare en sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21047-192">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="21047-193">UTDATA</span><span class="sxs-lookup"><span data-stu-id="21047-193">OUTPUTS</span></span>

### <span data-ttu-id="21047-194">Microsoft. PowerShell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="21047-194">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="21047-195">Den här cmdleten returnerar en **ByteCollection**.</span><span class="sxs-lookup"><span data-stu-id="21047-195">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="21047-196">Det här objektet representerar en samling byte.</span><span class="sxs-lookup"><span data-stu-id="21047-196">This object represents a collection of bytes.</span></span> <span data-ttu-id="21047-197">Den innehåller metoder som konverterar mängden med byte till en sträng formaterad som varje rad utdata som returneras av `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="21047-197">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="21047-198">Utdata anger också de byte som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="21047-198">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="21047-199">Om du anger **sökvägen** eller **LiteralPath** -parametern innehåller objektet sökvägen till filen som innehåller varje byte.</span><span class="sxs-lookup"><span data-stu-id="21047-199">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="21047-200">Om du skickar en sträng, boolesk, heltal osv, så märks den på lämpligt sätt.</span><span class="sxs-lookup"><span data-stu-id="21047-200">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="21047-201">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="21047-201">NOTES</span></span>

<span data-ttu-id="21047-202">Den högra kolumnen med utdata försöker återge byte som ASCII-tecken:</span><span class="sxs-lookup"><span data-stu-id="21047-202">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="21047-203">I allmänhet tolkas varje byte som en Unicode-kodtyp, vilket innebär att:</span><span class="sxs-lookup"><span data-stu-id="21047-203">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="21047-204">Skrivbara ASCII-tecken återges alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="21047-204">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="21047-205">UTF-8-tecken i flera byte återges aldrig korrekt</span><span class="sxs-lookup"><span data-stu-id="21047-205">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="21047-206">UTF-16-tecken återges på rätt sätt endast om deras höga byte-byte inträffar `NUL` .</span><span class="sxs-lookup"><span data-stu-id="21047-206">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="21047-207">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="21047-207">RELATED LINKS</span></span>

[<span data-ttu-id="21047-208">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="21047-208">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="21047-209">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="21047-209">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="21047-210">Format-List</span><span class="sxs-lookup"><span data-stu-id="21047-210">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="21047-211">Format-Table</span><span class="sxs-lookup"><span data-stu-id="21047-211">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="21047-212">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="21047-212">Format-Wide</span></span>](Format-Wide.md)

