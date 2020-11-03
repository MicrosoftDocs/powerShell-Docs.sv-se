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
# Format-Hex

## SAMMANFATTNING

Visar en fil eller andra indata som hexadecimala.

## SYNTAX

### Sökväg (standard)

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### InputObject

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## BESKRIVNING

`Format-Hex`Cmdleten visar en fil eller andra indata som hexadecimala värden. Om du vill fastställa förskjutningen för ett Character från utdata lägger du till numret längst till vänster i raden till talet överst i kolumnen för det aktuella specialtecknet.

`Format-Hex`Cmdleten kan hjälpa dig att avgöra filtypen för en skadad fil eller en fil som kanske inte har fil namns tillägget. Du kan köra denna cmdlet och läsa de hexadecimala utdata för att hämta fil information.

När `Format-Hex` du använder på en fil, ignorerar cmdleten rad matnings tecken och returnerar hela innehållet i en fil i en sträng med rad matnings tecken bevarade.

## EXEMPEL

### Exempel 1: hämta den hexadecimala representationen av en sträng

Det här kommandot returnerar de hexadecimala värdena för en sträng.

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

Strängen **Hello World** skickas ned pipelinen till `Format-Hex` cmdleten. De hexadecimala utdata från `Format-Hex` visar värdena för varje tecken i strängen.

### Exempel 2: hitta en filtyp från hexadecimala utdata

I det här exemplet används de hexadecimala utdata för att fastställa filtypen. Cmdleten visar filens fullständiga sökväg och de hexadecimala värdena.

Testa följande kommando genom att göra en kopia av en befintlig PDF-fil på den lokala datorn och byta namn på den kopierade filen till `File.t7f` .

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

`Format-Hex`Cmdleten använder parametern **Path** för att ange ett fil namn i den aktuella katalogen, **File. t7f**. Fil namns tillägget **. t7f** är ovanligt, men den hexadecimala utdata **% PDF** visar att det är en PDF-fil.

## PARAMETRAR

### -Encoding

Anger kodningen för utdata. Detta gäller endast för `[string]` inmatade. Parametern har ingen påverkan på numeriska typer. Standardvärdet är `utf8NoBOM`.

De acceptabla värdena för den här parametern är följande:

- `ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).
- `bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.
- `oem`: Använder standard kodning för MS-DOS-och-konsol program.
- `unicode`: Kodar i UTF-16-format med lite-endian-dataordning.
- `utf7`: Kodar i UTF-7-format.
- `utf8`: Kodar i UTF-8-format.
- `utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)
- `utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)
- `utf32`: Kodar i UTF-32-format.

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

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

### – InputObject

Används för pipeline-ininformation. Pipeline-inmatare stöder endast vissa skalära typer och `[system.io.fileinfo]` instanser för rör dragning `Get-ChildItem` .

De skalära typer som stöds är:

- `[string]`, `[char]`
- `[byte]`, `[sbyte]`
- `[int16]`, `[uint16]`, `[short]`, `[ushort]`
- `[int]`, `[uint]`, `[int32]`, `[uint32]`,
- `[long]`, `[ulong]`, `[int64]`, `[uint64]`
- `[single]`, `[float]`, `[double]`

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

### -LiteralPath

Anger den fullständiga sökvägen till en fil. Värdet för **LiteralPath** används exakt som det har angetts.
Den här parametern accepterar inte jokertecken. Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer. Om parametern **LiteralPath** innehåller escape-tecken, omger du sökvägen med enkla citat tecken. PowerShell tolkar inga tecken i en enskild citat sträng som escape-sekvenser. Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

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

### -Path

Anger sökvägen till filerna. `.`Ange den aktuella platsen genom att använda en punkt (). Jokertecknet ( `*` ) accepteras och kan användas för att ange alla objekt på en plats. Om parametern **Path** innehåller escape-tecken, omger du sökvägen med enkla citat tecken. Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer.

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

### – RAW

Den här parametern gör ingenting längre. Den behålls för skript kompatibilitet.

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

### -Förskjutning

Detta representerar antalet byte som ska hoppas över från att ingå i hex-utdata.

Den här parametern introducerades i PowerShell 6,2.

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

### -Antal

Detta representerar antalet byte som ska inkluderas i hex-utdata.

Den här parametern introducerades i PowerShell 6,2.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. ByteCollection

Den här cmdleten returnerar en **ByteCollection**. Det här objektet representerar en samling byte. Den innehåller metoder som konverterar mängden med byte till en sträng formaterad som varje rad utdata som returneras av `Format-Hex` . Om du anger **sökvägen** eller parametern **LiteralPath** innehåller objektet också sökvägen till filen som innehåller varje byte.

## ANTECKNINGAR

Den högra kolumnen med utdata försöker återge byte som ASCII-tecken:

I allmänhet tolkas varje byte som en Unicode-kodtyp, vilket innebär att:

- Skrivbara ASCII-tecken återges alltid korrekt
- UTF-8-tecken i flera byte återges aldrig korrekt
- UTF-16-tecken återges på rätt sätt endast om deras höga byte-byte inträffar `NUL` .

## RELATERADE LÄNKAR

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Format-Custom](Format-Custom.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)