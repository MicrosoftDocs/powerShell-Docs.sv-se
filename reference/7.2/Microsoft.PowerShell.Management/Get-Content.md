---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 8ad7df860533b9f394fd81199dd7213175cce213
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710837"
---
# Get-Content

## SAMMANFATTNING
Hämtar innehållet i objektet på den angivna platsen.

## SYNTAX

### Sökväg (standard)

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### LiteralPath

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## BESKRIVNING

`Get-Content`Cmdleten hämtar innehållet för objektet på den plats som anges av sökvägen, till exempel texten i en fil eller innehållet i en funktion. För filer läser innehållet en rad i taget och returnerar en samling objekt som representerar en rad med innehåll.

Från och med PowerShell 3,0 `Get-Content` kan även ett angivet antal rader hämtas från början eller slutet av ett objekt.

## EXEMPEL

### Exempel 1: hämta innehållet i en textfil

Det här exemplet hämtar innehållet i en fil i den aktuella katalogen. `LineNumbers.txt`Filen innehåller 100 rader i formatet, **Detta är rad X** och används i flera exempel.

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

Mat ris värdena 1-100 skickas ned pipelinen till `ForEach-Object` cmdleten. `ForEach-Object` använder ett-skript block med `Add-Content` cmdleten för att skapa `LineNumbers.txt` filen. Variabeln `$_` representerar mat ris värden som varje objekt skickas nedåt i pipelinen. `Get-Content`Cmdleten använder parametern **Path** för att ange `LineNumbers.txt` filen och visar innehållet i PowerShell-konsolen.

### Exempel 2: begränsa antalet rader Get-Content returnerar

Det här kommandot hämtar de fem första raderna i en fil. Parametern **totalCount** används för att hämta de första fem innehålls raderna. I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### Exempel 3: Hämta en bestämd innehålls rad från en textfil

Det här kommandot hämtar ett särskilt antal rader från en fil och visar sedan bara den sista raden i innehållet. Parametern **totalCount** hämtar de första 25 innehålls raderna. I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

`Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan du fortsätter till nästa steg. `Get-Content`Returnerar en matris med rader. Detta gör att du kan lägga till index notation efter parentesen för att hämta ett angivet rad nummer. I det här fallet `[-1]` anger indexet det sista indexet i den returnerade matrisen med 25 hämtade rader.

### Exempel 4: hämta den sista raden i en textfil

Det här kommandot hämtar den första raden och den sista raden i innehållet från en fil. I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

I det här exemplet används `Get-Item` cmdleten för att demonstrera att du kan skicka filer till- `Get-Content` parametern. Parametern **pilslut** hämtar den sista raden i filen. Den här metoden är snabbare än att hämta alla rader och använda `[-1]` index notation.

### Exempel 5: hämta innehållet i en alternativ data ström

Det här exemplet beskriver hur du använder **Stream** -parametern för att hämta innehållet i en alternativ data ström för filer som lagras på en Windows NTFS-volym. I det här exemplet `Set-Content` används cmdleten för att skapa exempel innehåll i en fil med namnet `Stream.txt` .

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

**Stream** -parametern är en dynamisk parameter för [fil Systems leverantören](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).
Som standard `Get-Content` hämtar endast data från den primära eller `$DATA` Stream. **Strömmar** kan användas för att lagra dolda data, till exempel attribut, säkerhets inställningar eller andra data.

### Exempel 6: Hämta RAW-innehåll

Kommandona i det här exemplet hämtar innehållet i en fil som en sträng, i stället för en sträng mat ris. Som standard, utan den **obearbetade** dynamiska parametern, returneras innehållet som en matris med rad matnings strängar. I det här exemplet används `LineNumbers.txt` filen som skapades i exemplet
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### Exempel 7: använda filter med Get-Content

Du kan ange ett filter för `Get-Content` cmdleten. När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.

Följande kommando hämtar innehållet för alla `*.log` filer i `C:\Temp` katalogen.

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### Exempel 8: Hämta fil innehåll som en byte mat ris

Det här exemplet visar hur du hämtar innehållet i en fil som ett `[byte[]]` enda objekt.

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

Det första kommandot använder parametern **AsByteStream** för att hämta data strömmen av byte från filen.
Parametern **RAW** ser till att byte returneras som en `[System.Byte[]]` . Om den **råa** parametern saknas är returvärdet en data ström med byte, som tolkas av PowerShell som `[System.Object[]]` .

## PARAMETRAR

### -Path

Anger sökvägen till ett objekt där `Get-Content` hämtar innehållet. Jokertecken är tillåtna. Sök vägarna måste vara sökvägar till objekt, inte behållare. Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.

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

### -ReadCount

Anger hur många rader med innehåll som skickas via pipelinen i taget. Standardvärdet är 1.
Värdet 0 (noll) skickar allt innehåll på en och samma tidpunkt.

Den här parametern ändrar inte det innehåll som visas, men det påverkar hur lång tid det tar att visa innehållet. När värdet för **ReadCount** ökar, kommer tiden det tar att returnera den första raden att öka, men den totala tiden för åtgärden minskar. Detta kan göra en märkbar skillnad i stora objekt.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – TotalCount

Anger antalet rader från början av en fil eller ett annat objekt. Standardvärdet är-1 (alla rader).

Du kan använda **totalCount** -parameterns namn eller dess alias, **först** eller **Head**.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Pilslut

Anger antalet rader från slutet av en fil eller ett annat objekt. Du kan använda **slutet** av parameter namnet eller dess alias, **sist**. Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

### -Undanta

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.
Värdet för den här parametern kvalificerar parametern **Path** .

Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .
Jokertecken är tillåtna.

Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

### -Force

**Force** åsidosätter ett skrivskyddat attribut eller skapar kataloger för att slutföra en fil Sök väg. **Force** -parametern försöker inte ändra fil behörigheter eller Åsidosätt säkerhets begränsningar.

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Avgränsare

Anger den avgränsare som `Get-Content` används för att dela upp filen i objekt när den läses. Standardvärdet är `\n` rad slutet. När du läser en textfil `Get-Content` returnerar en samling sträng objekt, som var och en slutar med ett rad sluts tecken. När du anger en avgränsare som inte finns i filen `Get-Content` returneras hela filen som ett enkelt, icke-avgränsat objekt.

Du kan använda den här parametern för att dela upp en stor fil i mindre filer genom att ange en fil avgränsare, som avgränsare. Avgränsaren bevaras (tas inte bort) och blir det sista objektet i varje fil avsnitt.

**Avgränsaren** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten. Den här parametern fungerar bara i fil system enheter.

> [!NOTE]
> När värdet för **avgränsare** -parametern är en tom sträng `Get-Content` returnerar inte något. Detta är ett känt problem. För att tvinga fram `Get-Content` att returnera hela filen som en enda, unavgränsad sträng. Ange ett värde som inte finns i filen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### – Vänta

Ser till att filen är öppen när alla befintliga rader har skrivits ut. Vid väntan, `Get-Content` kontrollerar filen en gång i sekunden och utvärderar nya rader om den är tillgänglig. Du kan avbryta **väntan** genom att trycka på **CTRL + C**. Väntan avslutas också om filen tas bort, i vilket fall ett icke-avslutande fel rapporteras.

**Wait** är en dynamisk parameter som fil system leverantören lägger till i `Get-Content` cmdleten. Den här parametern fungerar bara i fil system enheter. **Väntan** kan inte kombineras med **RAW**.

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

### – RAW

Ignorerar rad matnings tecken och returnerar hela innehållet i en fil i en sträng med newlines bevarad. Som standard används rad matnings tecken i en fil som avgränsare för att separera indata till en sträng mat ris. Den här parametern introducerades i PowerShell 3,0.

**RAW** är en dynamisk parameter som **fil** Systems leverantören lägger till i `Get-Content` cmdleten den här parametern fungerar endast i fil system enheter.

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

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är `utf8NoBOM`.

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

Encoding är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.
Den här parametern är endast tillgänglig i fil system enheter.

När du läser från och skriver till binära filer använder du parametern **AsByteStream** och värdet 0 för parametern **ReadCount** . Ett **ReadCount** -värde på 0 läser hela filen i en enda Läs åtgärd. Standardvärdet för **ReadCount** , 1, läser en byte i varje Läs åtgärd och konverterar varje byte till ett separat objekt, vilket orsakar fel när du använder `Set-Content` cmdleten för att skriva byte till en fil om du inte använder parametern **AsByteStream** .

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

### -Stream

Hämtar innehållet i den angivna alternativa NTFS-filströmen från filen. Ange data ström namnet.
Jokertecken stöds inte.

**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.
Den här parametern fungerar bara i fil system enheter på Windows-system. Den här parametern introducerades i Windows PowerShell 3,0.

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

### -AsByteStream

Anger att innehållet ska läsas som en data ström med byte. **AsByteStream** -parametern introducerades i Windows PowerShell 6,0.

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

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Int64, system. string [], system. Management. Automation. PSCredential

Du kan skicka vidare antalet läsningar, totalt antal, sökvägar eller autentiseringsuppgifter till `Get-Content` .

## UTDATA

### System. byte, system. String

`Get-Content` Returnerar strängar eller byte. Utdatatypen beror på vilken typ av innehåll som du anger som indata.

## ANTECKNINGAR

`Get-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Använd cmdleten för att hämta providers i sessionen `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Lägg till innehåll](Add-Content.md)

[Rensa innehåll](Clear-Content.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-PSProvider](Get-PSProvider.md)

[Ange innehåll](Set-Content.md)

