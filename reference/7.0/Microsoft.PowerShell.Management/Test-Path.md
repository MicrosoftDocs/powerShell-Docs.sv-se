---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: fcfb974a360c450f474ba97d65190b019860d8c4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262550"
---
# Test-Path

## SAMMANFATTNING
Anger om alla element i en sökväg finns.

## SYNTAX

### Sökväg (standard)

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### LiteralPath

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## BESKRIVNING

`Test-Path`Cmdleten avgör om alla element i sökvägen finns. Den returnerar `$True` om alla element finns och `$False` om några saknas. Det kan också avgöra om sökvägen är giltig och om sökvägen leder till en behållare eller ett terminal-eller löv element. Om `Path` är blank steg är en tom sträng `$False` tillbaka. Om matrisen `Path` är `$null` , matrisen för `$null` eller en tom matris returneras ett icke-avslutande fel.

## EXEMPEL

### Exempel 1: testa en bana

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

Det här kommandot kontrollerar om alla element i sökvägen finns, det vill säga katalogen C:, katalogen Documents and Settings och katalogen DavidC. Om några saknas returnerar cmdleten `$False` .
Annars returneras `$True` .

### Exempel 2: testa sökvägen till en profil

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

De här kommandona testar sökvägen till PowerShell-profilen.

Det första kommandot avgör om alla element i sökvägen finns. Det andra kommandot avgör om syntaxen för sökvägen är korrekt. I det här fallet är sökvägen `$False` , men syntaxen är korrekt `$True` . Dessa kommandon använder `$profile` sig av den automatiska variabeln som pekar på profilens plats, även om profilen inte finns.

Mer information om automatiska variabler finns i about_Automatic_Variables.

### Exempel 3: kontrol lera om det finns några filer förutom en angiven typ

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

Det här kommandot kontrollerar om det finns några filer i katalogen för kommersiella byggnader än. DWG-filer.

Kommandot använder parametern **Path** för att ange sökvägen. Eftersom sökvägen innehåller ett blank steg omges sökvägen av citat tecken. Asterisken i slutet av sökvägen visar innehållet i den kommersiella skapande katalogen. Med långa sökvägar, till exempel den här, skriver du de första bokstäverna i sökvägen och använder sedan TABB-tangenten för att slutföra sökvägen.

Kommandot anger parametern **exclude** för att ange filer som ska utelämnas från utvärderingen.

I det här fallet, eftersom katalogen bara innehåller. DWG-filer, blir resultatet `$False` .

### Exempel 4: Sök efter en fil

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

Det här kommandot kontrollerar om sökvägen som lagras i `$profile` variabeln leder till en fil. I det här fallet, eftersom PowerShell-profilen är en `.ps1` fil, returnerar cmdleten `$True` .

### Exempel 5: kontrol lera sökvägar i registret

Dessa kommandon används `Test-Path` med PowerShell-dataprovidern.

Det första kommandot testar om register Sök vägen för register nyckeln för **Microsoft. PowerShell** är korrekt i systemet. Om PowerShell är korrekt installerat returnerar cmdleten `$True` .

> [!IMPORTANT]
> `Test-Path` fungerar inte korrekt med alla PowerShell-leverantörer. Du kan till exempel använda `Test-Path` för att testa sökvägen till en register nyckel, men om du använder den för att testa sökvägen till en register post returneras den alltid `$False` , även om register posten finns.

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### Exempel 6: testa om en fil är nyare än ett angivet datum

Det här kommandot använder parametern **NewerThan** Dynamic för att avgöra om filen PowerShell.exe på datorn är nyare än den 13 juli 2009.

Parametern NewerThan fungerar bara i fil system enheter.

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### Exempel 7: testa en sökväg med null som värde

Felet som returnerades för `null` , matrisen `null` eller den tomma matrisen är ett icke-avslutande fel. Det kan vara undertryckt med `-ErrorAction SilentlyContinue` . I följande exempel visas alla fall där felet returneras `NullPathNotPermitted` .

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### Exempel 8: testa en sökväg med blank steg som värde

När ett blank steg eller en tom sträng anges för `-Path` parametern returneras **false**.
I följande exempel visas blank steg och en tom sträng.

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## PARAMETRAR

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell. Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

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

### -Undanta

Anger objekt som denna cmdlet utelämnar. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel "*. txt". Jokertecken är tillåtna.

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

### -Filter

Anger ett filter i formatet eller språket för providern. Värdet för den här parametern kvalificerar parametern **Path** . Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern. Filter är mer effektiva än andra parametrar, eftersom providern använder dem när den hämtar objekt i stället för att ha PowerShell filtrera objekten när de har hämtats.

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

### -Inkludera

Anger sökvägar som denna cmdlet testar. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel "*. txt". Jokertecken är tillåtna.

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

### -IsValid

Anger att den här cmdleten testar syntaxen för sökvägen, oavsett om elementen i sökvägen finns. Den här cmdleten returnerar `$True` om syntaxen för sökvägen är giltig och `$False` inte.

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

### -LiteralPath

Anger en sökväg som ska testas. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller tecken som kan tolkas av PowerShell som escape-sekvenser måste du omge sökvägen med enkla citat tecken så att de inte tolkas.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewerThan

Ange en tid som ett **datetime** -objekt.

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OlderThan

Ange en tid som ett **datetime** -objekt.

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger en sökväg som ska testas. Jokertecken är tillåtna. Om sökvägen innehåller blank steg, omger du den med citat tecken.

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

### -PathType

Anger typen för det sista elementet i sökvägen. Den här cmdleten returnerar `$True` om elementet är av den angivna typen och `$False` om det inte är det. De acceptabla värdena för den här parametern är:

- Fönster.
  Ett-element som innehåller andra element, till exempel en katalog eller register nyckel.
- Nod.
  Ett element som inte innehåller andra element, till exempel en fil.
- Helst.
  Antingen en behållare eller ett löv.

Anger om det sista elementet i sökvägen är av en viss typ.

> [!CAUTION]
>
> Upp till PowerShell-version 6.1.2 när **IsValid** -och **PathType** -växlarna anges tillsammans `Test-Path` ignorerar cmdleten **PathType** -växeln och validerar bara den syntaktiska sökvägen utan att verifiera Sök vägs typen.
>
> Enligt [problem #8607](https://github.com/PowerShell/PowerShell/issues/8607)kan det vara en avbrytande ändring i en framtida version, där **IsValid** -och **PathType** -växlarna tillhör separata parameter uppsättningar och därför inte kan användas tillsammans för att undvika denna förvirring.

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.

## UTDATA

### System. Boolean

Cmdleten returnerar ett **booleskt** värde.

## ANTECKNINGAR

Cmdlet: arna som innehåller **sökvägen** Substantiv ( **Sök vägs** -cmdletarna) fungerar med Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka. De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.
Använd dem på samma sätt som du använder **logsdirectory** , **Normpath** , **realpath** , **Join** eller andra Sök vägs manipulerare.

`Test-Path`Är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Konvertera-sökväg](Convert-Path.md)

[Anslut till sökväg](Join-Path.md)

[Lös-sökväg](Resolve-Path.md)

[Dela-sökväg](Split-Path.md)
