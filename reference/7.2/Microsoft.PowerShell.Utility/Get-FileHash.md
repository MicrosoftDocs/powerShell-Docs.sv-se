---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709432"
---
# Get-FileHash

## SAMMANFATTNING
Beräknar hash-värdet för en fil med hjälp av en angiven hash-algoritm.

## SYNTAX

### Sökväg (standard)

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### StreamParameterSet

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## BESKRIVNING

`Get-FileHash`Cmdleten beräknar hash-värdet för en fil med hjälp av en angiven hash-algoritm.
Ett hash-värde är ett unikt värde som motsvarar filens innehåll. I stället för att identifiera innehållet i en fil med hjälp av dess fil namn, tillägg eller annan beteckning tilldelar en hash ett unikt värde till innehållet i en fil. Fil namn och tillägg kan ändras utan att ändra innehållet i filen och utan att ändra hash-värdet. På samma sätt kan filens innehåll ändras utan att du ändrar namnet eller tillägget. Men om du ändrar till och med ett enda bokstav i innehållet i en fil ändras filens hash-värde.

Syftet med hash-värden är att tillhandahålla ett kryptografiskt, säkert sätt att verifiera att innehållet i en fil inte har ändrats. Vissa hash-algoritmer, inklusive MD5 och SHA1, anses inte längre vara säkra mot angrepp, målet för en säker hash-algoritm är att göra det omöjligt att ändra innehållet i en fil, antingen av misstag eller av skadlig eller obehörig försök--och underhålla samma hash-värde. Du kan också använda hash-värden för att avgöra om två olika filer har exakt samma innehåll. Om hash-värdena för två filer är identiska är innehållet i filerna också identiska.

Som standard `Get-FileHash` använder cmdleten SHA256-algoritmen, men alla hash-algoritmer som stöds av mål operativ systemet kan användas.

## EXEMPEL

### Exempel 1: beräkna hash-värdet för en fil

I det här exemplet används `Get-FileHash` cmdleten för att beräkna hash-värdet för `/etc/apt/sources.list` filen. Den hash-algoritm som används är standard **SHA256**. Utdata är skickas till `Format-List` cmdleten för att formatera utdata som en lista.

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### Exempel 2: beräkna hash-värdet för en ISO-fil

I det här exemplet används `Get-FileHash` cmdleten och **SHA384** -algoritmen för att beräkna hash-värdet för en ISO-fil som en administratör har hämtat från Internet. Utdata är skickas till `Format-List` cmdleten för att formatera utdata som en lista.

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### Exempel 3: beräkna hash-värdet för en ström

I det här exemplet kommer vi att använda **system .net. WebClient** för att ladda ned ett paket från [PowerShell-release-sidan](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4). På sidan version dokumenteras också SHA256-hashen för varje paket fil. Vi kan jämföra det publicerade hash-värdet med det som vi beräknar med `Get-FileHash` .

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### Exempel 4: beräkna hashen för en sträng

PowerShell tillhandahåller ingen cmdlet för att beräkna hashen för en sträng. Du kan dock skriva en sträng till en data ström och använda parametern **InputStream** för `Get-FileHash` för att hämta hash-värdet.

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## PARAMETRAR

### -Algoritm

Anger den kryptografiska hash-funktion som ska användas för att beräkna hash-värdet för innehållet i den angivna filen eller data strömmen. En kryptografisk hash-funktion har egenskapen det är omöjligt att hitta två olika filer med samma hash-värde. Hash-funktioner används ofta med digitala signaturer och för data integritet. De acceptabla värdena för den här parametern är:

- SHA1
- SHA256
- SHA384
- SHA512
- MD5

Om inget värde anges, eller om parametern utelämnas, är standardvärdet SHA256.

Av säkerhets skäl bör MD5 och SHA1, som inte längre anses vara säkra, endast användas för enkel ändrings validering och ska inte användas för att generera hash-värden för filer som kräver skydd mot angrepp eller manipulering.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputStream

Anger indataströmmen.

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till en fil. Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du sökvägen med enkla citat tecken. Enkla citat tecken instruerar PowerShell att inte tolka tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till en eller flera filer som en matris. Jokertecken är tillåtna.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng till den `Get-FileHash` cmdlet som innehåller en sökväg till en eller flera filer.

## UTDATA

### Microsoft. PowerShell. Utility. FileHash

`Get-FileHash` Returnerar ett objekt som representerar sökvägen till den angivna filen, värdet för den beräknade hashen och algoritmen som används för att beräkna hashen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Format-List](Format-List.md)

