---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "93269384"
---
# ConvertFrom-String

## SAMMANFATTNING
Extraherar och tolkar strukturerade egenskaper från sträng innehåll.

## SYNTAX

### ByDelimiter (standard)

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### TemplateParsing

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## BESKRIVNING

**ConvertFrom-String-** cmdleten extraherar och tolkar strukturerade egenskaper från sträng innehåll.
Denna cmdlet genererar ett objekt genom att parsa text från en vanlig text ström.
För varje sträng i pipelinen delar cmdleten indatamängden med antingen en avgränsare eller ett pars uttryck, och tilldelar sedan egenskaps namnen till var och en av de resulterande delade elementen.
Du kan ange dessa egenskaps namn. Om du inte gör det genereras de automatiskt åt dig.

Cmdletens standard parameter uppsättning, **ByDelimiter** , delar upp exakt den reguljära uttrycks avgränsaren.
Den utför inte offert matchning eller avgränsare undantags tecken som `Import-Csv` cmdleten gör.

Cmdletens alternativa parameter uppsättning, **TemplateParsing** , genererar element från grupper som har samlats in med ett reguljärt uttryck. Mer information om reguljära uttryck finns [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).

Denna cmdlet har stöd för två lägen: grundläggande avgränsad parsning och automatiskt genererad, exempel beroende parsning.

Delimited parsing, som standard, delar in indatamängden med blank steg och tilldelar de resulterande grupperna egenskaps namn.

Du kan anpassa avgränsaren genom att skicka `ConvertFrom-String` resultatet till en av `Format-*` cmdletarna, eller så kan du använda **avgränsnings** parametern.

Cmdleten stöder också automatiskt genererad, exempel-driven parsning baserat på [FlashExtract, forskning som fungerar av Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).

## EXEMPEL

### Exempel 1: generera ett objekt med standard egenskaps namn

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

Det här kommandot genererar ett objekt med standard egenskaps namn, **P1** och **P2**.

### Exempel 1A: bekanta dig med det genererade objektet

Det här kommandot genererar ett objekt med egenskaperna **P1** , **P2** ; båda egenskaperna är av **sträng** typ, som standard.

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### Exempel 2: generera ett objekt med standard egenskaps namn med hjälp av en avgränsare

Det här kommandot genererar ett objekt med en domän och ett användar namn som använder omvänt snedstreck ( `\` ) som avgränsare. Det omvända snedstrecket måste föregås av ett annat omvänt snedstreck när du använder reguljära uttryck.

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### Exempel 3: generera ett objekt som innehåller två namngivna egenskaper

I följande exempel skapas objekt från fil poster i Windows-värdar.

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

`Get-Content`Cmdlet: en lagrar innehållet i en Windows Hosts-fil i `$content` . Det andra kommandot tar bort alla kommentarer i början av värd filen med ett reguljärt uttryck som matchar alla rader som inte börjar med ( `#` ). Det sista kommandot konverterar den återstående texten till objekt med **Server** **-och IP-** egenskaper.

### Exempel 4: Använd ett uttryck som värde för parametern TemplateContent och spara resultatet i en variabel.

Det här kommandot använder ett uttryck som värde för parametern **TemplateContent** .
Uttrycket sparas i en variabel för enkelhetens skull.
Windows PowerShell förstår nu att strängen som används i pipelinen `ConvertFrom-String` har tre egenskaper:

- **Namn**
- **nummer**
- **tids**

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

Varje rad i indatatypen utvärderas av exempel matchningarna. Om raden matchar exemplen som anges i mönstret extraheras värdena och skickas till den utgående variabeln.

Exempel data, har `$template` två olika telefon format:

- `425-123-6789`
- `(206) 987-4321`

Exempel data innehåller också två olika ålders format:

- `6`
- `12`

Detta innebär att telefoner som `(206) 987 4321` inte kommer att identifieras, eftersom det inte finns några exempel data som matchar mönstret eftersom det inte finns några bindestreck.

### Exempel 5: ange data typer för de genererade egenskaperna

Detta är samma exempel som exempel 4 ovan.
Skillnaden är att mönster strängen innehåller en datatyp för varje önskad egenskap.

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

`Get-Member`Cmdleten används för att visa att **ålders** egenskapen är ett heltal.

## PARAMETRAR

### -Avgränsare

Anger ett reguljärt uttryck som identifierar avgränsningen mellan element.
Element som skapas av Split blir egenskaper i det resulterande objektet.
Avgränsaren används slutligen i ett anrop till metoden **Split** för typen `[System.Text.RegularExpressions.RegularExpression]` .

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeExtent

Anger att denna cmdlet innehåller en text egenskap för omfattning som tas bort som standard.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger strängar som tagits emot från pipelinen eller en variabel som innehåller ett String-objekt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -PropertyNames

Anger en matris med egenskaps namn som ska tilldelas ett delat värde i det resulterande objektet.
Alla text rader som du delar eller tolkar genererar element som representerar egenskaps värden.
Om elementet är resultatet av en infångnings grupp och den infångnings gruppen har namnet (till exempel `(?<name>)` eller `(?'name')` ), tilldelas namnet på den infångnings gruppen till egenskapen.

Om du anger något element i matrisen **PropertyName** , tilldelas dessa namn egenskaper som ännu inte har namngetts.

Om du anger fler egenskaps namn än det finns fält, ignorerar PowerShell de extra egenskaps namnen. Om du inte anger tillräckligt många egenskaps namn för att namnge alla fält tilldelar PowerShell automatiskt numeriska egenskaps namn till alla egenskaper som inte heter: **P1** , **P2** osv.

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateContent

Anger ett uttryck eller ett uttryck som har sparats som en variabel som beskriver de egenskaper som denna cmdlet tilldelar strängar till. Syntaxen för en mall fält specifikation är följande: `{[optional-typecast]<name>:<example-value>}` .

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateFile

Anger en fil, som en matris, som innehåller en mall för den önskade parsningen av strängen.
I mallfilen anges egenskaper och deras värden inom hakparenteser, som du ser nedan.
Om en egenskap, till exempel egenskapen **namn** och tillhör ande andra egenskaper, visas flera gånger kan du lägga till en asterisk ( `*` ) för att indikera att detta resulterar i flera poster. Detta förhindrar att flera egenskaper extraheras till en enda post.

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UpdateTemplate

Anger att denna cmdlet sparar resultatet av en Learning-algoritm i en kommentar i mallfilen.
Detta gör att algoritm inlärnings processen går snabbare.
Om du vill använda den här parametern måste du även ange en mallfil med parametern **TemplateFile** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

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

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[ConvertFrom-sträng: exempel-baserad text tolkning](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[ConvertFrom-StringData](ConvertFrom-StringData.md)

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[ConvertTo-Xml](ConvertTo-Xml.md)
