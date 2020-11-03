---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 897029cab790487f6834d021bfc447060fd39812
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265419"
---
# Set-Content

## SAMMANFATTNING
Skriver nytt innehåll eller ersätter befintligt innehåll i en fil.

## SYNTAX

### Sökväg (standard)

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### LiteralPath

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## BESKRIVNING

`Set-Content` är en sträng bearbetnings-cmdlet som skriver nytt innehåll eller ersätter innehållet i en fil. `Set-Content` ersätter det befintliga innehållet och skiljer sig från den `Add-Content` cmdlet som lägger till innehåll i en fil. Om du vill skicka innehåll till `Set-Content` kan du använda parametern **Value** på kommando raden eller skicka innehåll via pipelinen.

Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).

## EXEMPEL

### Exempel 1: Ersätt innehållet i flera filer i en katalog

I det här exemplet ersätts innehållet för flera filer i den aktuella katalogen.

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

`Get-ChildItem`Cmdleten använder **Sök vägs** parametern för att visa **. txt** -filer som börjar med `Test*` i den aktuella katalogen. `Set-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna. Parametern **Value** innehåller text strängen **Hello, World** som ersätter det befintliga innehållet i varje fil. `Get-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna och visar varje fils innehåll i PowerShell-konsolen.

### Exempel 2: skapa en ny fil och skriv innehåll

Det här exemplet skapar en ny fil och skriver aktuellt datum och tid till filen.

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

`Set-Content` använder parametrarna **sökväg** och **värde** för att skapa en ny fil med namnet **DateTime.txt** i den aktuella katalogen. **Värde** parametern använder `Get-Date` för att hämta aktuellt datum och aktuell tid.
`Set-Content` skriver **datetime** -objektet till filen som en sträng. `Get-Content`Cmdleten använder parametern **Path** för att visa innehållet i **DateTime.txt** i PowerShell-konsolen.

### Exempel 3: ersätt text i en fil

Det här kommandot ersätter alla instanser av Word i en befintlig fil.

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

`Get-Content`Cmdleten använder parametern **Path** för att ange **Notice.txt** filen i den aktuella katalogen. `Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan det skickas ned pipelinen.

Innehållet i **Notice.txt** -filen skickas ned pipelinen till `ForEach-Object` cmdleten.
`ForEach-Object` använder den automatiska variabeln `$_` och ersätter varje förekomst av **Varning** med **försiktighet**. Objekten skickas ned pipelinen till `Set-Content` cmdleten. `Set-Content` använder parametern **Path** för att ange **Notice.txt** -filen och skriver det uppdaterade innehållet till filen.

Den sista `Get-Content` cmdleten visar det uppdaterade fil innehållet i PowerShell-konsolen.

### Exempel 4: använda filter med Set-Content

Du kan ange ett filter för `Set-Content` cmdleten. När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.

Följande kommando anger innehållet `*.txt` för alla filer i `C:\Temp` katalogen till **värdet** Empty.

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## PARAMETRAR

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell.
> Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

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

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är `Default`.

Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Set-Content` . Den här parametern fungerar bara i fil system enheter.

De acceptabla värdena för den här parametern är följande:

- `Ascii` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `BigEndianUTF32` Använder UTF-32 med big-endian byte-ordningen.
- `Byte` Kodar en uppsättning tecken i en sekvens med byte.
- `Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).
- `Oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.
- `String` Samma som `Unicode` .
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `Unknown` Samma som `Unicode` .
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8.
- `UTF32` Använder UTF-32 med en liten-endian-order.

Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Set-Content` . Den här parametern fungerar bara i fil system enheter.

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Undanta

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna. Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter. Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.

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

### -Force

Tvingar cmdleten att ange innehållet i en fil, även om filen är skrivskyddad. Implementeringen varierar från providern till providern. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).
**Force** -parametern åsidosätter inte säkerhets begränsningar.

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

### -Inkludera

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` . Jokertecken är tillåtna. Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

### -LiteralPath

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – NoNewline

Sträng representationerna av indata-objekten sammanfogas för att bilda utdata. Inga blank steg eller newlines infogas mellan utgående strängar. Ingen ny rad läggs till efter den sista utgående strängen.

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

### – PassThru

Returnerar ett objekt som representerar innehållet. Som standard genererar denna cmdlet inga utdata.

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

### -Path

Anger sökvägen till det objekt som tar emot innehållet.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

Anger en alternativ data ström för innehåll. Om data strömmen inte finns skapar den här cmdleten den. Jokertecken stöds inte.

**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Set-Content` . Den här parametern fungerar bara i fil system enheter.

Du kan använda `Set-Content` cmdleten för att ändra innehållet i **zonen. unik identifierare** för den alternativa data strömmen. Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet. Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – UseTransaction

Inkluderar kommandot i den aktiva transaktionen. Den här parametern är bara giltig medan en transaktion pågår. Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Värde

Anger det nya innehållet för objektet.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

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

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .
Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Object

Du kan skicka en pipe till ett objekt som innehåller det nya värdet för objektet `Set-Content` .

## UTDATA

### Ingen eller system. String

När du använder parametern **Passthru** `Set-Content` genererar ett **system. String** -objekt som representerar innehållet. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- Du kan också referera till `Set-Content` med dess inbyggda alias `sc` .
  Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Set-Content` är utformad för sträng bearbetning. Om du rör icke-sträng objekt till `Set-Content` konverteras objektet till en sträng innan det skrivs. Använd om du vill skriva objekt till filer `Out-File` .
- `Set-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Automatic_Variables. MD](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[Lägg till innehåll](Add-Content.md)

[Rensa innehåll](Clear-Content.md)

[Get-ChildItem](Get-ChildItem.md)

[Hämta innehåll](Get-Content.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Nytt objekt](New-Item.md)
