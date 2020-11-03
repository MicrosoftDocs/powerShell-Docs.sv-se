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
# Format-Hex

## SAMMANFATTNING

Visar en fil eller andra indata som hexadecimala.

## SYNTAX

### Sökväg (standard)

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### ByInputObject

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
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

Du testar följande kommando genom att göra en kopia av en befintlig PDF-fil på den lokala datorn och byta namn på den kopierade filen till **filen. t7f**.

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

`Format-Hex`Cmdleten använder parametern **Path** för att ange ett fil namn i den aktuella katalogen `File.t7f` . Fil namns tillägget `.t7f` är ovanligt, men det hexadecimala resultatet `%PDF` visar att det är en PDF-fil.

### Exempel 3: Visa rå hexadecimala utdata

Som standard `Format-Hex` väljer du komprimera utdata av numeriska data typer: enkla byte eller dubbla byte-sekvenser används om värdet är tillräckligt litet. Den **råa** parametern inaktiverar det här beteendet.

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

Observera skillnaden i utdata. Parametern **RAW** visar talen som 4 byte-värden, true till deras **Int32** -typer.

## PARAMETRAR

### -Encoding

Anger kodningen för utdata. Detta gäller endast för `[string]` inmatade. Parametern har ingen påverkan på numeriska typer. Standardvärdet är `ASCII`.

De acceptabla värdena för den här parametern är följande:

- `Ascii` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8.
- `UTF32` Använder UTF-32 med en liten-endian-order.

Icke-ASCII-tecken i indata är utdata som litterala `?` tecken som resulterar i förlust av information.

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

### – InputObject

Används för pipeline-ininformation. Pipeline-inmatare stöder endast vissa skalära typer och `[system.io.fileinfo]` instanser för rör dragning `Get-ChildItem` .

De skalära typer som stöds är:

- `[string]`
- `[byte]`
- `[int]`, `[int32]`
- `[long]`, `[int64]`

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

### -LiteralPath

Anger den fullständiga sökvägen till en fil. Värdet för **LiteralPath** används exakt som det har angetts.
Den här parametern accepterar inte jokertecken. Avgränsa Sök vägarna med kommatecken om du vill ange flera sökvägar till filer. Om parametern **LiteralPath** innehåller escape-tecken, omger du sökvägen med enkla citat tecken. PowerShell tolkar inga tecken i en enskild citat sträng som escape-sekvenser. Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

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

Som standard `Format-Hex` väljer du komprimera utdata av numeriska data typer: enkla byte eller dubbla byte-sekvenser används om värdet är tillräckligt litet. Den **råa** parametern inaktiverar det här beteendet.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. ByteCollection

Den här cmdleten returnerar en **ByteCollection**. Det här objektet representerar en samling byte. Den innehåller metoder som konverterar mängden med byte till en sträng formaterad som varje rad utdata som returneras av `Format-Hex` . Om du anger **sökvägen** eller parametern **LiteralPath** innehåller objektet också sökvägen till filen som innehåller varje byte.

## ANTECKNINGAR

Den högra kolumnen med utdata försöker återge byte som tecken:

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
