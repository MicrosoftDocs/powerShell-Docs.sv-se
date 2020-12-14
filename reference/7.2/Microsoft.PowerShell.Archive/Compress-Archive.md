---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 58807ba0745a6b09e7956547425c489b427d4f4b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708534"
---
# Compress-Archive

## SAMMANFATTNING
Skapar ett komprimerat arkiv eller en komprimerad fil från angivna filer och kataloger.

## SYNTAX

### Sökväg (standard)

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithUpdate

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithForce

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithUpdate

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithForce

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Compress-Archive`Cmdleten skapar en komprimerad eller zippad Arkiv fil från en eller flera angivna filer eller kataloger. Ett arkiv paketerar flera filer, med valfri komprimering, i en enda zippad fil för enklare distribution och lagring. En arkivfil kan komprimeras med hjälp av den Compression-algoritm som anges av parametern **CompressionLevel** .

`Compress-Archive`Cmdlet: en använder Microsoft .NET API [System.IO.Compression.Zip-arkivet](/dotnet/api/system.io.compression.ziparchive) för att komprimera filer.
Den maximala fil storleken är 2 GB eftersom det finns en begränsning i det underliggande API: et.

Några exempel använder ihopbuntning för att minska rad längden för kod exemplen. Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

## EXEMPEL

### Exempel 1: komprimera filer för att skapa en arkivfil

Det här exemplet komprimerar filer från olika kataloger och skapar en Arkiv fil. Ett jokertecken används för att hämta alla filer med ett visst fil namns tillägg. Det finns ingen katalog struktur i Arkiv filen eftersom **sökvägen** bara anger fil namn.

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

Parametern **Path** accepterar vissa fil namn och fil namn med jokertecken `*.vsd` . **Sökvägen** använder en kommaavgränsad lista för att hämta filer från olika kataloger. Komprimerings nivån är **snabbast** för att minska bearbetnings tiden. Parametern **DestinationPath** anger platsen för `Draft.zip` filen. `Draft.zip`Filen innehåller `Draftdoc.docx` och alla filer med `.vsd` fil namns tillägget.

### Exempel 2: komprimera filer med en LiteralPath

I det här exemplet komprimeras vissa namngivna filer och en ny arkivfil skapas. Det finns ingen katalog struktur i Arkiv filen eftersom **sökvägen** bara anger fil namn.

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

Absoluta sökvägar och fil namn används eftersom **LiteralPath** -parametern inte accepterar jokertecken. **Sökvägen** använder en kommaavgränsad lista för att hämta filer från olika kataloger. Komprimerings nivån är **snabbast** för att minska bearbetnings tiden. Parametern **DestinationPath** anger platsen för `Draft.zip` filen. `Draft.zip`Filen innehåller `Draftdoc.docx` och `diagram2.vsd` .

### Exempel 3: komprimera en katalog som innehåller rot katalogen

Det här exemplet komprimerar en katalog och skapar en arkivfil som **innehåller** rot katalogen och alla dess filer och under kataloger. Arkiv filen har en katalog struktur eftersom **sökvägen** anger en rot Katalog.

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` använder parametern **Path** för att ange rot katalogen `C:\Reference` . Parametern **DestinationPath** anger platsen för Arkiv filen. `Draft.zip`Arkivet innehåller `Reference` rot katalogen och alla dess filer och under kataloger.

### Exempel 4: komprimera en katalog som undantar rot katalogen

Det här exemplet komprimerar en katalog och skapar en arkivfil som **undantar** rot katalogen eftersom **sökvägen** använder en asterisk () som `*` jokertecken. Arkivet innehåller en katalog struktur som innehåller rot katalogens filer och under kataloger.

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` använder parametern **Path** för att ange rot katalogen, `C:\Reference` med jokertecknet asterisk ( `*` ). Parametern **DestinationPath** anger platsen för Arkiv filen. `Draft.zip`Arkivet innehåller rot katalogens filer och under kataloger. `Reference`Rot katalogen är exkluderad från arkivet.

### Exempel 5: komprimera bara filerna i en rot Katalog

I det här exemplet komprimeras bara filerna i en rot Katalog och en Arkiv fil skapas. Det finns ingen katalog struktur i arkivet eftersom endast filer komprimeras.

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` använder parametern **Path** för att ange rot katalogen, `C:\Reference` med ett jokertecken ( **Star-dot-Star** `*.*` ). Parametern **DestinationPath** anger platsen för Arkiv filen. `Draft.zip`Arkivet innehåller bara `Reference` rot katalogen filer och rot katalogen är exkluderad.

### Exempel 6: Använd pipelinen för att arkivera filer

Det här exemplet skickar filer ned pipelinen för att skapa ett arkiv. Det finns ingen katalog struktur i Arkiv filen eftersom **sökvägen** bara anger fil namn.

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

`Get-ChildItem` använder parametern **Path** för att ange två filer från olika kataloger. Varje fil representeras av ett **fileinfo** -objekt och skickas till pipelinen `Compress-Archive` .
De två angivna filerna arkiveras i `PipelineFiles.zip` .

### Exempel 7: Använd pipelinen för att arkivera en katalog

I det här exemplet skickas en katalog ned i pipeline för att skapa ett arkiv. Filer skickas som **fileinfo** -objekt och kataloger som **DirectoryInfo** -objekt. Arkivets katalog struktur innehåller inte rot katalogen, men dess filer och under kataloger ingår i arkivet.

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

`Get-ChildItem` använder parametern **Path** för att ange `C:\LogFiles` rot katalogen. Varje **fileinfo** -och **DirectoryInfo** -objekt skickas ned pipelinen.

`Compress-Archive` lägger till varje objekt i `PipelineDir.zip` arkivet. Parametern **Path** har inte angetts eftersom pipeline-objekten tas emot i parameter position 0.

### Exempel 8: hur rekursion kan påverka Arkiv

Det här exemplet visar hur rekursion kan duplicera filer i arkivet. Om du till exempel använder `Get-ChildItem` med parametern **rekursivt** . Som rekursion-processer skickas varje **fileinfo** -och **DirectoryInfo** -objekt nedåt i pipelinen och läggs till i arkivet.

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

`C:\TestLog`Katalogen innehåller inte några filer. Den innehåller en under katalog med namnet `testsub` som innehåller `testlog.txt` filen.

`Get-ChildItem` använder parametern **Path** för att ange rot katalogen `C:\TestLog` . **Rekursivt** -parametern bearbetar filer och kataloger. Ett **DirectoryInfo** -objekt skapas för `testsub` och ett **fileinfo** -objekt `testlog.txt` .

Varje objekt skickas ned pipelinen till `Compress-Archive` . **DestinationPath** anger platsen för Arkiv filen. Parametern **Path** har inte angetts eftersom pipeline-objekten tas emot i parameter position 0.

Följande sammanfattning beskriver det `PipelineRecurse.zip` arkiverade innehållet som innehåller en duplicerad fil:

- **DirectoryInfo** -objektet skapar `testsub` katalogen och innehåller `testlog.txt` filen som visar den ursprungliga katalog strukturen.
- **Fileinfo** -objektet skapar en dubblett `testlog.txt` i arkivets rot. Den duplicerade filen skapas eftersom rekursion skickade ett fil objekt till `Compress-Archive` . Det här beteendet är förväntat eftersom varje objekt som skickas i pipelinen läggs till i arkivet.

### Exempel 9: uppdatera en befintlig arkivfil

Det här exemplet uppdaterar en befintlig arkivfil, `Draft.Zip` i `C:\Archives` katalogen. I det här exemplet innehåller den befintliga Arkiv filen rot katalogen och dess filer och under kataloger.

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

Kommandot uppdateras `Draft.Zip` med nyare versioner av befintliga filer i `C:\Reference` katalogen och dess under kataloger. Och nya filer som har lagts till i `C:\Reference` eller dess under kataloger ingår i det uppdaterade `Draft.Zip` arkivet.

## PARAMETRAR

### -CompressionLevel

Anger hur mycket komprimering som ska gälla när du skapar arkiv filen. Snabbare komprimering kräver kortare tid för att skapa filen, men kan resultera i större fil storlekar.

Om den här parametern inte anges använder kommandot standardvärdet, **optimal**.

Följande är de acceptabla värdena för den här parametern:

- **Snabbast**. Använd den snabbaste komprimerings metoden som är tillgänglig för att minska bearbetnings tiden. Snabbare komprimering kan resultera i större fil storlekar.
- **Nocompression**. Komprimerar inte källfilerna.
- **Optimalt**. Bearbetnings tiden beror på fil storleken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
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

### – DestinationPath

Den här parametern är obligatorisk och anger sökvägen till den arkiverade utdatafilen. **DestinationPath** ska innehålla namnet på den zippade filen och antingen den absoluta eller relativa sökvägen till den zippade filen.

Om fil namnet i **DestinationPath** inte har något `.zip` fil namns tillägg lägger cmdleten till `.zip` fil namns tillägget.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen eller Sök vägarna till de filer som du vill lägga till i den arkiverade zip-filen. Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken, omger du varje escape-tecken inom enkla citat tecken för att instruera PowerShell att inte tolka några tecken som escape-sekvenser.
Om du vill ange flera sökvägar och inkludera filer på flera platser i den zippade filen använder du kommatecken för att avgränsa Sök vägarna.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Gör att cmdleten genererar ett fil objekt som representerar den skapade arkivfil.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen eller Sök vägarna till de filer som du vill lägga till i den arkiverade zip-filen. Om du vill ange flera sökvägar och inkludera filer på flera platser använder du kommatecken för att avgränsa Sök vägarna.

Den här parametern accepterar jokertecken. Med jokertecken kan du lägga till alla filer i en katalog till Arkiv filen.

Att använda jokertecken med en rot Katalog påverkar arkivets innehåll:

- Om du vill skapa ett arkiv som **innehåller** rot katalogen och alla dess filer och under kataloger, anger du rot katalogen i **sökvägen** utan jokertecken. Exempel: `-Path C:\Reference`
- Om du vill skapa ett arkiv som **undantar** rot katalogen, men zips alla filer och under kataloger, använder du jokertecknet asterisk ( `*` ). Exempel: `-Path C:\Reference\*`
- Om du vill skapa ett arkiv som endast zips filerna i rot katalogen använder du jokertecknet **Star-dot-Star** ( `*.*` ). Under kataloger i roten ingår inte i arkivet. Exempel: `-Path C:\Reference\*.*`

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Uppdatera

Uppdaterar det angivna arkivet genom att ersätta äldre fil versioner i arkivet med nyare fil versioner som har samma namn. Du kan också lägga till den här parametern för att lägga till filer i ett befintligt arkiv.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
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

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till en eller flera filer.

## UTDATA

### System. IO. FileInfo

Cmdleten returnerar bara ett **fileinfo** -objekt när du använder parametern **Passthru** .

## ANTECKNINGAR

Med rekursion och skicka objekt nedåt kan pipelinen duplicera filer i arkivet. Om du till exempel använder `Get-ChildItem` med parametern **rekursivt** , läggs varje **fileinfo** -och **DirectoryInfo** -objekt som skickas ned pipelinen till arkivet.

[Zip-filspecifikationen](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) anger inte ett standardiserat sätt för kodnings fil namn som innehåller icke-ASCII-tecken. Cmdlet: en `Compress-Archive` använder UTF-8-kodning. Andra ZIP-arkiv verktyg kan använda ett annat kodnings schema. När filer extraheras med fil namn som inte lagras med UTF-8-kodning, `Expand-Archive` används det råa värde som finns i arkivet. Detta kan resultera i ett fil namn som skiljer sig från käll fil namnet som lagras i arkivet.

## RELATERADE LÄNKAR

[Expandera – arkivera](Expand-Archive.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

