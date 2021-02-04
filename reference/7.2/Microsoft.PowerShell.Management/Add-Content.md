---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 70ef5033c3c5d37ed00a88abfb0d1353f5d10854
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693069"
---
# Add-Content

## SAMMANFATTNING
Lägger till innehåll till de angivna objekten, till exempel att lägga till ord i en fil.

## SYNTAX

### Sökväg (standard)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## BESKRIVNING

`Add-Content`Cmdleten lägger till innehåll i ett angivet objekt eller en angiven fil. Du kan ange innehållet genom att skriva innehållet i kommandot eller genom att ange ett objekt som innehåller innehållet.

Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).

## EXEMPEL

### Exempel 1: Lägg till en sträng till alla textfiler med ett undantag

I det här exemplet läggs ett värde till i textfiler i den aktuella katalogen, men filer som är baserade på fil namnet exkluderas.

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

Parametern **Path** anger alla `.txt` filer i den aktuella katalogen, men parametern **exclude** ignorerar fil namn som matchar det angivna mönstret. Parametern **Value** anger text strängen som skrivs till filerna.

### Exempel 2: Lägg till ett datum i slutet av de angivna filerna

I det här exemplet läggs datumet till i den aktuella katalogen och datumet visas i PowerShell-konsolen.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

`Add-Content`Cmdleten skapar två nya filer i den aktuella katalogen. Parametern **Value** innehåller utdata från `Get-Date` cmdleten. Parametern **Passthru** matar ut det tillagda innehållet i pipelinen.
Eftersom det inte finns någon annan cmdlet för att ta emot utdata visas den i PowerShell-konsolen.
`Get-Content`Cmdleten visar den uppdaterade filen `DateTimeFile1.log` .

### Exempel 3: lägga till innehållet i en angiven fil till en annan fil

Det här exemplet hämtar innehållet från en fil och lagrar innehållet i en variabel. Variabeln används för att lägga till innehållet i en annan fil.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- `Get-Content`Cmdleten hämtar innehållet `CopyFromFile.txt` i och lagrar innehållet i `$From` variabeln.
- `Add-Content`Cmdleten uppdaterar `CopyToFile.txt` filen med hjälp av innehållet i `$From` variabeln.
- `Get-Content`Cmdleten visar CopyToFile.txt.

### Exempel 4: Lägg till innehållet i en angiven fil till en annan fil med pipelinen

Det här exemplet hämtar innehållet från en fil och rör den till `Add-Content` cmdleten.

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Cmdlet: en hämtar innehållet i `CopyFromFile.txt` . Resultaten är skickas till `Add-Content` cmdleten, som uppdaterar `CopyToFile.txt` .
Den sista `Get-Content` cmdleten visas `CopyToFile.txt` .

### Exempel 5: skapa en ny fil och kopiera innehåll

Det här exemplet skapar en ny fil och kopierar en befintlig fils innehåll till den nya filen.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- `Add-Content`Cmdleten använder **sökvägen** och **värde** parametrarna för att skapa en ny fil i den aktuella katalogen.
- `Get-Content`Cmdlet: en hämtar innehållet i en befintlig fil `CopyFromFile.txt` och skickar den till **värde** parametern. Parenteserna runt `Get-Content` cmdleten ser till att kommandot slutförs innan `Add-Content` kommandot börjar.
- `Get-Content`Cmdleten visar innehållet i den nya filen `NewFile.txt` .

### Exempel 6: Lägg till innehåll i en skrivskyddad fil

Det här kommandot lägger till ett värde till filen även om Filattributet **IsReadOnly** har angetts till **True**.
Stegen för att skapa en skrivskyddad fil ingår i exemplet.

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- `New-Item`Cmdleten använder parametrarna **Path** och **itemType** för att skapa filen `IsReadOnlyTextFile.txt` i den aktuella katalogen.
- `Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true.
- `Get-ChildItem`Cmdleten visar att filen är tom (0) och har attributet skrivskyddad ( `r` ).
- `Add-Content`Cmdleten använder parametern **Path** för att ange filen. Parametern **Value** innehåller text strängen som ska läggas till i filen. Parametern **Force** skriver texten till den skrivskyddade filen.
- `Get-Content`Cmdleten använder parametern **Path** för att visa filens innehåll.

Om du vill ta bort det skrivskyddade attributet använder du `Set-ItemProperty` kommandot med **värdet** parameter inställt på `False` .

### Exempel 7: använda filter med Add-Content

Du kan ange ett filter för `Add-Content` cmdleten. När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.

Följande kommando lägger till ordet "utfört" på innehållet i alla `*.txt` filer i `C:\Temp` katalogen.

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## PARAMETRAR

### -AsByteStream

Anger att innehållet ska läsas som en data ström med byte. Den här parametern introducerades i PowerShell 6,0.

En varning inträffar när du använder parametern **AsByteStream** med parametern **encoding** . Parametern **AsByteStream** ignorerar all kodning och utdata returneras som en data ström med byte.

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

Anger typ av kodning för mål filen. Standardvärdet är `utf8NoBOM`.

Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` cmdleten. Den här parametern fungerar bara i fil system enheter.

De acceptabla värdena för den här parametern är följande:

- `ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).
- `bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.
- `bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.
- `oem`: Använder standard kodning för MS-DOS-och-konsol program.
- `unicode`: Kodar i UTF-16-format med lite-endian-dataordning.
- `utf7`: Kodar i UTF-7-format.
- `utf8`: Kodar i UTF-8-format.
- `utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)
- `utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)
- `utf32`: Kodar i UTF-32-format.

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

> [!NOTE]
> **UTF-7** _ rekommenderas inte längre att använda. I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ *encoding**.

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

Åsidosätter det skrivskyddade attributet så att du kan lägga till innehåll i en skrivskyddad fil. **Tvinga** åsidosätter till exempel det skrivskyddade attributet eller skapa kataloger för att slutföra en fil Sök väg, men kommer inte att försöka ändra fil behörigheter.

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
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – NoNewline

Anger att denna cmdlet inte lägger till en ny rad eller vagn retur i innehållet.

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

Returnerar ett objekt som representerar det tillagda innehållet. Som standard genererar denna cmdlet inga utdata.

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

Anger sökvägen till de objekt som tar emot det ytterligare innehållet.
Jokertecken är tillåtna.
Sök vägarna måste vara sökvägar till objekt, inte behållare.
Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.
Om du anger flera sökvägar använder du kommatecken för att avgränsa Sök vägarna.

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

> [!NOTE]
> Den här parametern är endast tillgänglig i Windows.

Anger en alternativ data ström för innehåll. Om data strömmen inte finns skapar den här cmdleten den. Jokertecken stöds inte.

**Stream** är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` . Den här parametern fungerar bara i fil system enheter.

Du kan använda `Add-Content` cmdleten för att ändra innehållet i valfri alternativ data ström, till exempel `Zone.Identifier` . Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet. Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.

Den här parametern introducerades i PowerShell 3,0.  Från och med PowerShell 7,2 `Add-Content` kan alternativa data strömmar vara riktade mot både filer och kataloger.


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

### -Värde

Anger det innehåll som ska läggas till. Skriv en Citerad sträng, till exempel **den här informationen endast för intern användning** eller ange ett objekt som innehåller innehåll, till exempel det **datetime** -objekt som `Get-Date` genereras.

Du kan inte ange innehållet i en fil genom att ange dess sökväg, eftersom sökvägen bara är en sträng.
Du kan använda ett `Get-Content` kommando för att hämta innehållet och skicka det till **värde** parametern.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Object, system. Management. Automation. PSCredential

Du kan skicka pipe-värden, sökvägar eller autentiseringsuppgifter till `Set-Content` .

## UTDATA

### Ingen eller system. String

När du använder parametern **Passthru** `Add-Content` genererar ett **system. String** -objekt som representerar innehållet. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- När du rör ett objekt till `Add-Content` konverteras objektet till en sträng innan det läggs till i objektet. Objekt typen bestämmer sträng formatet, men formatet kan vara ett annat än standard visningen av objektet. Om du vill kontrol lera sträng formatet använder du formateringsegenskaperna för sändnings-cmdleten.
- Du kan också referera till `Add-Content` med dess inbyggda alias `ac` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Add-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Rensa innehåll](Clear-Content.md)

[Hämta innehåll](Get-Content.md)

[Hämta objekt](Get-Item.md)

[Nytt objekt](New-Item.md)

[Ange innehåll](Set-Content.md)
