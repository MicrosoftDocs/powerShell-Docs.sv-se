---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265178"
---
# Convert-String

## SAMMANFATTNING
Formaterar en sträng för att matcha exempel.

## SYNTAX

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Convert-String** formaterar en sträng för att matcha formatet på exempel.

## EXEMPEL

### Exempel 1: konvertera format för en sträng

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

Det första kommandot skapar en matris som innehåller för-och efter namn.

Det andra kommandot formaterar namnen enligt exemplet.
Förnamnet placeras först i utdata, följt av en initial.

### Exempel 2: förenkla format för en sträng

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

Det första kommandot skapar en matris som innehåller First-, mitten-och efter namn.
Observera att den sista posten inte har något mellan namn.

Det andra kommandot formaterar namnen enligt exemplet.
Det placerar efter namnet först i utdata, följt av det första namnet.
Alla mellan namn har tagits bort. posten utan mellan namn hanteras korrekt.

### Exempel 3: hantering av utdata när strängar inte matchar exemplet

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

Det första kommandot skapar en matris som innehåller First-, mitten-och efter namn.
Observera att den sista posten inte har något mellan namn.

Det andra kommandot formaterar namnen enligt exemplet.
Det placerar det **mittersta namnet** först i utdata, följt av det första namnet.
Den sista posten i **$Composers** hoppas över eftersom den inte matchar exempel mönstret: det saknar mellan namn.

### Exempel 4: försiktighet med skönhets utrymmen

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

Det första kommandot skapar en matris med för-och efter namn.
Observera att andra och fjärde objekt har ett extra avslutande blank steg efter efter namn.

Det andra kommandot konverterar alla strängar som matchar exempel mönstret: _ord, blank steg, ord och avslutande avslutande blank steg_ , allt detta före likhets tecknet.
Observera också det inledande utrymmet i utdata.

### Exempel 5: formatera process information med flera mönster

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

**$ExamplePatterns** definierar olika förväntade mönster i data med hjälp av exempel.

Det första mönstret, `@{before='"Hello","World"'; after='World: Hello'}` , läst på följande sätt: _förväntar sig att strängar där ett ord omges av dubbla citat tecken, ett kommatecken_ 
 _och sedan det andra och sista ordet inom citat tecken._ 
 _utan blank steg i strängen. På utdata: Placera andra ordet först,_ 
 _utan citat tecken, ett enda blank steg och sedan det första ordet, utan citat tecken._

Det andra mönstret, `@{before='"Hello","1"'; after='1: Hello'}` , läses på följande sätt: _förväntar sig strängar där ett ord omges av dubbla citat tecken, ett kommatecken_ 
 _och sedan ett tal inom citat tecken._ 
 _utan blank steg i strängen. På utdata: placera talet först,_ 
 _utan citat tecken, ett enda blank steg och sedan ordet utan citat tecken._

Det tredje mönstret, `@{before='"Hello-World","22"'; after='22: Hello-World'}` , läser följande: _förväntar sig strängar där två ord med ett bindestreck mellan omges av_ 
 _dubbla citat tecken, ett kommatecken och sedan ett tal inom citat tecken._ 
 _utan blank steg mellan kommatecken och det tredje dubbla citat tecknet._ 
 _På utdata: placera talet först, utan citat tecken, sedan ett enda blank steg,_ 
 _och sedan avstavade ord, utan citat tecken._

Det fjärde och slutgiltiga mönstret, läser följande `@{before='"hello world","333"'; after='333: hello world'}` : _förväntar sig att strängar där två ord med ett blank steg omges av_ 
 _dubbla citat tecken, ett kommatecken och sedan ett tal inom citat tecken._ 
 _utan blank steg mellan kommatecken och det tredje dubbla citat tecknet._ 
 _På utdata: placera talet först, utan citat tecken, sedan ett enda blank steg,_ 
 _och sedan orden med blank steg mellan, utan citat tecken._

Det första kommandot hämtar alla processer med hjälp av Get-Process-cmdleten.
Kommandot skickar dem till Select-Object-cmdlet, som väljer processens namn och process-ID. I slutet av pipelinen konverterar kommandot utdata till kommaavgränsade värden, utan typ information med hjälp av ConvertTo-Csv cmdlet.
Kommandot lagrar resultaten i variabeln **$Processes** .
**$Processes** innehåller nu process namn och PID.

Det andra kommandot anger en exempel variabel som ändrar ordningen på inobjekten.
Kommandot behandlar varje sträng i **$Processes**.

>**Obs!** Det fjärde mönstret säger implicit att två eller flera ord avgränsade med blank steg matchas.
>
>Utan det fjärde mönstret matchas bara det första ordet i strängen som omges av dubbla citat tecken.

## PARAMETRAR

### – Exempel

Anger en lista med exempel på mål formatet.
Ange par avgränsade med likhets tecknet (=) med käll mönstret till vänster och mål mönstret till höger, som i följande exempel:

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

>**Obs!** I det andra exemplet används en lista över mönster

Alternativt kan du ange en lista över hash-tabeller som innehåller **före** och **efter** egenskaper.

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

>**Varning** Undvik att använda blank steg runt likhets tecknet eftersom de behandlas som en del av mönstret.

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger en sträng som ska formateras.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Sträng

Du kan skicka vidare strängar till denna cmdlet.

## UTDATA

### Sträng

Den här cmdleten returnerar en sträng.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[ConvertFrom-sträng](ConvertFrom-String.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Hämta process](../Microsoft.PowerShell.Management/Get-Process.md)

[Out-sträng](Out-String.md)

[Select-Object](Select-Object.md)
