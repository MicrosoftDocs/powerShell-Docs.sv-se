---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: d231396e0ff167d6af644af008c7a22e9d6f99bb
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "93269270"
---
# Select-String

## SAMMANFATTNING
Söker efter text i strängar och filer.

## SYNTAX

### Fil (standard)

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### ObjectRaw

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### Objekt

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### FileRaw

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFileRaw

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFile

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## BESKRIVNING

`Select-String`Cmdleten söker efter text-och text mönster i inmatade strängar och filer. Du kan använda `Select-String` liknande **grep** i UNIX eller **findstr.exe** i Windows.

`Select-String` baseras på text rader. Som standard `Select-String` söker den första matchningen i varje rad, och för varje matchning visas fil namnet, rad numret och all text på raden som innehåller matchningen. Du kan direkt `Select-String` hitta flera matchningar per rad, Visa text före och efter matchningen eller visa ett booleskt värde (sant eller falskt) som anger om en matchning hittas.

`Select-String` använder reguljär uttrycks matchning, men den kan också utföra en matchning som söker i indatamängden för den text som du anger.

`Select-String` kan visa alla text matchningar eller stoppa efter den första matchningen i varje indatafil.
`Select-String` kan användas för att visa all text som inte matchar det angivna mönstret.

Du kan också ange om `Select-String` du vill att en viss tecken kodning ska förväntas, till exempel när du söker filer med Unicode-text. `Select-String` använder byte-order-markering (BOM) för att identifiera filens kodnings format. Om filen saknar struktur antas kodningen vara UTF8.

## EXEMPEL

### Exempel 1: hitta en Skift läges känslig matchning

I det här exemplet är Skift läges känslig matchning av texten som skickades pipelinen till `Select-String` cmdleten.

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

Text strängarna **Hello** och **Hej** skickas ned pipelinen till `Select-String` cmdleten.
`Select-String` använder **Pattern** -parametern för att ange **Hej**. Parametern **caseSensitive** anger att Skift läget endast måste matcha versaler och gemener. **SimpleMatch** är en valfri parameter och anger att strängen i mönstret inte tolkas som ett reguljärt uttryck.
`Select-String` visar **Hello** i PowerShell-konsolen.

### Exempel 2: Sök efter matchningar i textfiler

Det här kommandot söker igenom alla filer med `.txt` fil namns tillägget i den aktuella katalogen. I utdata visas raderna i de filer som innehåller den angivna strängen.

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

I det här exemplet `Get-Alias` och `Get-Command` används med `Out-File` cmdleten för att skapa två textfiler i den aktuella katalogen **Alias.txt** och **Command.txt**.

`Select-String` använder parametern **Path** med jokertecknet asterisk ( `*` ) för att söka igenom alla filer i den aktuella katalogen med fil namns tillägget `.txt` . Parametern **Pattern** anger texten som ska matcha **Get-**. `Select-String` visar utdata i PowerShell-konsolen. Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.

### Exempel 3: hitta en mönster matchning

I det här exemplet genomsöks flera filer för att hitta matchningar för det angivna mönstret. Mönstret använder en kvantifierare för reguljära uttryck. Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

`Select-String`Cmdleten använder två parametrar, **sökväg** och **mönster**. Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen. Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen. **Pattern** -parametern anger att matchar ett frågetecken ( `?` ) i varje fil. Ett omvänt snedstreck ( `\` ) används som ett escape-tecken och är nödvändigt eftersom frågetecknet ( `?` ) är en kvantifierare för reguljära uttryck. `Select-String` visar utdata i PowerShell-konsolen. Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.

### Exempel 4: Använd Select-String i en funktion

I det här exemplet skapas en funktion för att söka efter ett mönster i PowerShell-hjälpfilerna. I det här exemplet finns bara funktionen i PowerShell-sessionen. När PowerShell-sessionen stängs tas funktionen bort. Mer information finns i [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

Funktionen skapas på PowerShell-kommandoraden. `Function`Kommandot använder namns **ökning-hjälpen**. Tryck på **RETUR** för att börja lägga till instruktioner till funktionen. I `>>` prompten lägger du till varje instruktion och trycker på **RETUR** som visas i exemplet. När du har lagt till en avslutande hak paren tes returneras en PowerShell-prompt.

Funktionen innehåller två kommandon. `$PSHelp`Variabeln lagrar sökvägen till PowerShell-hjälpfilerna. `$PSHOME` är PowerShell-installationsmappen med under katalogen **en-US** som anger varje `*.txt` fil i katalogen.

`Select-String`Kommandot i funktionen använder parametrarna **Path** och **pattern** . Parametern **Path** använder `$PSHelp` variabeln för att hämta sökvägen. Parametern **Pattern** använder sträng **About_** som Sök villkor.

Om du vill köra funktionen skriver du `Search-Help` . Funktionens `Select-String` kommando visar utdata i PowerShell-konsolen.

### Exempel 5: Sök efter en sträng i en händelse logg i Windows

Det här exemplet söker efter en sträng i en händelse logg i Windows. Variabeln `$_` representerar det aktuella objektet i pipelinen. Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

`Get-WinEvent`Cmdleten använder parametern **LogName** för att ange program loggen. Parametern **MaxEvents** hämtar de senaste 50 händelserna från loggen. Logg innehållet lagras i variabeln med namnet `$Events` .

`$Events`Variabeln skickas ned pipelinen till `Select-String` cmdleten. `Select-String` använder parametern **InputObject** . `$_`Variabeln representerar det aktuella objektet och `message` är en egenskap för händelsen. **Pattern** -parametern anger att strängen **misslyckades** och söker efter matchningar i `$_.message` . `Select-String` visar utdata i PowerShell-konsolen.

### Exempel 6: hitta en sträng i under kataloger

I det här exemplet genomsöks en katalog och alla dess under kataloger för en speciell text sträng.

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

`Get-ChildItem` använder parametern **Path** för att ange **C:\Windows\System32 \* . txt**. Parametern **rekursivt** innehåller under kataloger. Objekten skickas ned pipelinen till `Select-String` .

`Select-String` använder **mönster** parametern och anger strängen **Microsoft**. Parametern **caseSensitive** används för att matcha det exakta Skift läget för strängen. `Select-String` visar utdata i PowerShell-konsolen.

> [!NOTE]
> Beroende på dina behörigheter kan du se **åtkomst nekade** meddelanden i utdata.

### Exempel 7: hitta strängar som inte matchar ett mönster

Det här exemplet visar hur du kan utesluta rader med data som inte matchar ett mönster.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen. `Select-String` använder parametern **Path** för att ange **Command.txt** -filen. Parametern **Pattern** anger **Get** och **set** som Sök mönster. **NotMatch** -parametern utesluter **Get** och **set** från resultaten.
`Select-String` visar utdata i PowerShell-konsolen som inte innehåller **Get** eller **set**.

### Exempel 8: Hitta rader före och efter en matchning

Det här exemplet visar hur du hämtar raderna före och efter det matchade mönstret.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen. `Select-String` använder parametern **Path** för att ange **Command.txt** -filen. Parametern **Pattern** anger **Get-Computer** som Sök mönster. **Kontext** parametern använder två värden, före och efter, och markerar mönster matchningar i utdata med en vinkel paren tes ( `>` ). **Kontext** parametern matar ut de två raderna före den första mönster matchningen och tre rader efter den sista mönster matchningen.

### Exempel 9: Sök efter alla mönster matchningar

I det här exemplet visas hur **AllMatches** -parametern hittar varje mönster matchning i en rad med text. Som standard `Select-String` söker bara den första förekomsten av ett mönster i en textrad. I det här exemplet används objekt egenskaper som hittas med `Get-Member` cmdleten.

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

`Get-ChildItem`Cmdleten använder parametern **Path** . Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen. Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen. `Get-ChildItem`Objekten lagras i `$A` variabeln. `$A`Variabeln skickas ned pipelinen till `Select-String` cmdleten. `Select-String` använder **Pattern** -parametern för att söka igenom varje fil för sträng **PowerShell**.

På kommando raden för PowerShell `$A` visas variabel innehållet. Det finns en rad som innehåller två förekomster av sträng **PowerShell**.

`$A.Matches`Egenskapen visar den första förekomsten av Pattern **PowerShell** på varje rad.

`$A.Matches.Length`Egenskapen räknar den första förekomsten av mönstret **PowerShell** på varje rad.

`$B`Variabeln använder samma `Get-ChildItem` `Select-String` cmdletar, men lägger till parametern **AllMatches** . **AllMatches** hittar varje förekomst av Pattern **PowerShell** på varje rad. De objekt som lagras i `$A` `$B` variablerna och är identiska.

`$B.Matches.Length`Egenskapen ökar eftersom alla förekomster av mönstret **PowerShell** räknas för varje rad.

## PARAMETRAR

### -AllMatches

Anger att cmdleten söker efter fler än en matchning i varje textrad. Utan den här parametern `Select-String` hittar bara den första matchningen i varje textrad.

När `Select-String` söker efter fler än en matchning i en rad med text, genererar den fortfarande bara ett **MatchInfo** -objekt för raden, men egenskapen **matchar** för objektet innehåller alla matchningar.

> [!NOTE]
> Den här parametern ignoreras när den används i kombination med parametern **SimpleMatch** . Om du vill returnera alla matchningar och mönstret som du söker efter innehåller tecken för reguljära uttryck, måste du undanta dessa tecken i stället för att använda **SimpleMatch**. Mer information om hur du hoppar över reguljära uttryck finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) .

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

### -CaseSensitive

Anger att cmdleten matchar är Skift läges känsliga. Som standard är matchningar inte Skift läges känsliga.

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

### – Kontext

Fångar upp det angivna antalet rader före och efter den rad som matchar mönstret.

Om du anger ett tal som värde för den här parametern, bestämmer den siffran antalet rader som fångats före och efter matchningen. Om du anger två tal som värde bestämmer det första talet antalet rader före matchningen och det andra talet bestämmer antalet rader efter matchningen. Till exempel `-Context 2,3`.

I standard visningen visas rader med en matchning med en höger vinkel paren tes ( `>` ) (ASCII 62) i den första kolumnen i visningen. Omarkerade rader är kontexten.

**Kontext** parametern ändrar inte antalet objekt som genereras av `Select-String` .
`Select-String` genererar ett [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -objekt för varje matchning. Kontexten lagras som en sträng mat ris i objektets **kontext** egenskap.

När utdata från ett `Select-String` kommando skickas ned pipelinen till ett annat `Select-String` kommando, söker kommandot ta emot bara texten på den matchade raden. Den matchade raden är värdet för egenskapen **line** för **MatchInfo** -objektet, inte texten i Sammanhangs linjerna. Därför är **kontext** parametern inte giltig i mottagnings `Select-String` kommandot.

När kontexten innehåller en matchning inkluderar **MatchInfo** -objektet för varje matchning alla kontext linjer, men de överlappande linjerna visas bara en gång i visningen.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Kultur

Anger ett kultur namn som matchar det angivna mönstret. **Kultur** parametern måste användas med parametern **SimpleMatch** . Standard beteendet använder kulturen för den aktuella PowerShell-körnings utrymme (session).

Om du vill hämta en lista över alla kulturer som stöds använder du `Get-Culture -ListAvailable` kommandot.

Dessutom accepterar den här parametern följande argument:

- CurrentCulture, som är standard.
- Ordnings tal, som är icke-språklig binär jämförelse;
- Invariant, som är kultur oberoende jämförelse.

Med `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` kommandot får du snabbast binär jämförelse.

**Kultur** parametern använder tabbtangenten för att bläddra igenom listan med argument som anger tillgängliga kulturer. Om du vill visa alla tillgängliga argument använder du följande kommando:

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

Mer information om .NET CultureInfo.Name-egenskapen finns i [CultureInfo.name](/dotnet/api//system.globalization.cultureinfo.name).

**Kultur** parametern introducerades i PowerShell 7.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
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

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

> [!NOTE]
> **UTF-7** * rekommenderas inte längre att använda. I PowerShell 7,1 skrivs en varning om du anger `utf7` för **kodnings** parametern.

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

Uteslut de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna.

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

### -Inkludera

Innehåller de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna.

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

### – InputObject

Anger den text som ska genomsökas. Ange en variabel som innehåller texten eller Skriv ett kommando eller uttryck som hämtar texten.

Att använda parametern **InputObject** är inte detsamma som att skicka strängar nedåt i pipeline till `Select-String` .

När du rör fler än en sträng till `Select-String` cmdleten söker den efter den angivna texten i varje sträng och returnerar varje sträng som innehåller Sök texten.

När du använder parametern **InputObject** för att skicka en samling med strängar, `Select-String` behandlar samlingen som en enda kombinerad sträng. `Select-String` Returnerar strängarna som en enhet om Sök texten hittas i en sträng.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object, ObjectRaw
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Lista

Endast den första instansen av matchande text returneras från varje indatafil. Detta är det mest effektiva sättet att hämta en lista över filer som har innehåll som matchar det reguljära uttrycket.

Som standard `Select-String` returnerar ett **MatchInfo** -objekt för varje matchning som hittas.

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

### -LiteralPath

Anger sökvägen till de filer som ska genomsökas. Värdet för parametern **LiteralPath** används exakt som det skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser. Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nobetoning

Som standard `Select-String` markeras den sträng som matchar det mönster du sökte efter med **Pattern** -parametern. Parametern **nobetoning** inaktiverar markeringen.

Betoningen använder negativa färger baserat på PowerShell-bakgrunden och text färgerna. Om dina PowerShell-färger till exempel är svarta bakgrunder med vit text. Betoningen är en vit bakgrund med svart text.

Den här parametern introducerades i PowerShell 7.

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

### -NotMatch

Parametern **NotMatch** söker efter text som inte matchar det angivna mönstret.

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

Anger sökvägen till filerna som ska genomsökas. Jokertecken är tillåtna. Standard platsen är den lokala katalogen.

Ange filer i katalogen, till exempel `log1.txt` , `*.doc` eller `*.*` . Om du bara anger en katalog Miss lyckas kommandot.

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Mönster

Anger vilken text som ska finnas på varje rad. Pattern-värdet behandlas som ett reguljärt uttryck.

Mer information om reguljära uttryck finns [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tyst

Anger att cmdleten returnerar ett booleskt värde (sant eller falskt) i stället för ett **MatchInfo** -objekt. Värdet är true om mönstret hittas. annars är värdet FALSKT.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – RAW

Gör att cmdleten bara matar ut de matchande strängarna, i stället för **MatchInfo** -objekt. Detta är resultatet som är mest likt Unix **grep** -eller Windows **findstr.exe** -kommandon.

Den här parametern introducerades i PowerShell 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SimpleMatch

Anger att cmdleten använder en enkel matchning i stället för en reguljär uttrycks matchning. I en enkel matchning `Select-String` söker efter texten i **mönster** -parametern i indatamängden. Den tolkar inte värdet för **Pattern** -parametern som en reguljär uttrycks instruktion.

Även om **SimpleMatch** används är egenskapen **matchar** för det **MatchInfo** -objekt som returnerades tomt.

> [!NOTE]
> När den här parametern används med parametern **AllMatches** ignoreras **AllMatches** .

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt som har en **toString** -Metod till `Select-String` .

## UTDATA

### Microsoft. PowerShell. commands. MatchInfo, system. Boolean, system. String

Som standard är utdata en uppsättning **MatchInfo** -objekt med en för varje matchning som hittas. Om du använder parametern **quiet** är utdata ett **booleskt** värde som anger om mönstret hittades.
Om du använder en **RAW** -parameter är utdata en uppsättning **sträng** objekt som matchar mönstret.

## ANTECKNINGAR

`Select-String` liknar **grep** i UNIX eller **findstr.exe** i Windows.

**SLS** -aliaset för `Select-String` cmdleten introducerades i PowerShell 3,0.

> [!NOTE]
> Enligt [godkända verb för PowerShell-kommandon](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)är det officiella aliaset för `Select-*` cmdlets `sc` , inte `sl` . Därför bör rätt alias för `Select-String` vara `scs` , inte `sls` . Detta är ett undantag till den här regeln.

Om du vill använda `Select-String` anger du den text som du vill hitta som värde för **mönster** parametern. Om du vill ange vilken text som ska genomsökas använder du följande kriterier:

- Skriv texten i en Citerad sträng och koppla den sedan till `Select-String` .
- Lagra en text sträng i en variabel och ange sedan variabeln som värdet för parametern **InputObject** .
- Om texten lagras i filer använder du parametern **Path** för att ange sökvägen till filerna.

Som standard `Select-String` tolkar värdet för **Pattern** -parametern som ett reguljärt uttryck. Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md). Du kan använda parametern **SimpleMatch** för att åsidosätta den reguljära uttrycks matchningen. Parametern **SimpleMatch** hittar förekomster av värdet för **Pattern** -parametern i indatamängden.

Standardutdata för `Select-String` är ett **MatchInfo** -objekt, som innehåller detaljerad information om matchningarna. Informationen i objektet är användbar när du söker efter text i filer, eftersom **MatchInfo** -objekt har egenskaper som **fil namn** och **rad**. När indata inte är från filen är värdet för dessa parametrar **InputStream**.

Om du inte behöver informationen i **MatchInfo** -objektet använder du parametern **quiet** . Parametern **quiet** returnerar ett booleskt värde (sant eller falskt) för att indikera om en matchning hittades i stället för ett **MatchInfo** -objekt.

När du matchar fraser `Select-String` använder den aktuella kulturen som har angetts för systemet. Använd cmdleten för att hitta den aktuella kulturen `Get-Culture` .

Om du vill hitta egenskaperna för ett **MatchInfo** -objekt skriver du följande kommando:

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## RELATERADE LÄNKAR

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[Get-alias](Get-Alias.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-Command](../Microsoft.PowerShell.Core/Get-Command.md)

[Hämta medlem](Get-Member.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Ut-fil](Out-File.md)

