---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 8c0a1b7a14f5dfa071a85808f5d7dfba4d06048e
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514974"
---
# Get-Date

## SAMMANFATTNING
Hämtar aktuellt datum och aktuell tid.

## SYNTAX

### Datum (standard)

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### DateUFormat

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### UnixTimeSeconds

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### UnixTimeSecondsUFormat

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## BESKRIVNING

`Get-Date`Cmdleten hämtar ett **datetime** -objekt som representerar det aktuella datumet eller ett datum som du anger. `Get-Date` kan formatera datum och tid i flera .NET-och UNIX-format. Du kan använda `Get-Date` för att generera en datum-eller tids tecken sträng och sedan skicka strängen till andra cmdletar eller program.

`Get-Date` använder datorns kultur inställningar för att avgöra hur utdata formateras. Använd om du vill visa datorns inställningar `(Get-Culture).DateTimeFormat` .

## EXEMPEL

### Exempel 1: Hämta aktuellt datum och tid

I det här exemplet `Get-Date` visas aktuellt system datum och aktuell tid. Utdata är i formatet för långt datum och långt klock slag.

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### Exempel 2: Hämta element i aktuellt datum och tid

Det här exemplet visar hur du kan använda `Get-Date` för att hämta antingen datum-eller tids element. Parametern använder argumenten **date**, **Time** eller **datetime**.

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

`Get-Date` använder parametern **DisplayHint** med **datum** argumentet för att bara hämta datumet.

### Exempel 3: Hämta datum och tid med en .NET-format specifikation

I det här exemplet används en .NET-format specifikation för att anpassa utdatatypens format. Utdata är ett **String** -objekt.

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

`Get-Date` använder **format** parametern för att ange flera format specificerare.

De .NET-format specificerare som används i det här exemplet definieras enligt följande:

| Specificerare |                      Definition                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | Veckodag-fullständigt namn                           |
| `MM`      | Månadsnummer                                          |
| `dd`      | Dag i månaden – 2 siffror                           |
| `yyyy`    | År i 4-siffrigt format                                |
| `HH:mm`   | Tid i 24-timmarsformat – inga sekunder                    |
| `K`       | Tids zons förskjutning från Universal Time Coordinator (UTC) |

Mer information om .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).

### Exempel 4: Hämta datum och tid med en UFormat-specificerare

I det här exemplet används flera **UFormat** format-specificerare för att anpassa utdatatypen.
Utdata är ett **String** -objekt.

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

`Get-Date` använder parametern **UFormat** för att ange flera format specificerare.

Det **UFormat** format som används i det här exemplet definieras enligt följande:

| Specificerare |                      Definition                       |
| --------- | ----------------------------------------------------- |
| `%A`      | Veckodag-fullständigt namn                           |
| `%m`      | Månadsnummer                                          |
| `%d`      | Dag i månaden – 2 siffror                           |
| `%Y`      | År i 4-siffrigt format                                |
| `%R`      | Tid i 24-timmarsformat – inga sekunder                    |
| `%Z`      | Tids zons förskjutning från Universal Time Coordinator (UTC) |

En lista över giltiga **UFormat** format-specificerare finns i avsnittet [Obs](#notes) !

### Exempel 5: Hämta datumets dag på året

I det här exemplet används en egenskap för att hämta årets numeriska dag.

Den gregorianska kalendern har 365 dagar, med undantag för skottår som har 366 dagar. Till exempel 31 december 2020 är dag 366.

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

`Get-Date` använder tre parametrar för att ange datum: **år**, **månad** och **dag**. Kommandot omges av parenteser så att resultatet utvärderas av egenskapen **DayofYear** .

### Exempel 6: kontrol lera om ett datum har justerats för sommar tid

I det här exemplet används en boolesk metod för att kontrol lera om ett datum justeras efter sommar tid.

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

En variabel, `$DST` lagrar resultatet av `Get-Date` . `$DST` använder metoden **IsDaylightSavingTime** för att testa om datumet justeras för sommar tid.

### Exempel 7: konvertera aktuell tid till UTC-tid

I det här exemplet konverteras den aktuella tiden till UTC-tid. UTC-förskjutningen för systemets nationella inställningar används för att konvertera tiden. I en tabell i avsnittet [anteckningar](#notes) visas giltiga **UFormat** format-specifikationer.

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

`Get-Date` använder parametern **UFormat** med format specificerare för att visa aktuellt system datum och tid. Format specifikationen **% Z** representerar UTC-förskjutningen **-07**.

`$Time`Variabeln lagrar systemets aktuella datum och tid. `$Time` använder metoden **ToUniversalTime ()** för att konvertera tiden baserat på datorns UTC-förskjutning.

### Exempel 8: skapa en tidsstämpel

I det här exemplet skapar en format specificerare ett **String** -objekt för tidsstämpel för ett katalog namn. Tidsstämpeln innehåller datum, tid och UTC-förskjutning.

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

`$timestamp`Variabeln lagrar resultatet av ett `Get-Date` kommando. `Get-Date` använder **format** parametern med format specifikationen för gemener `o` för att skapa ett **String** -objekt med tidsstämpel. Objektet skickas ned pipelinen till `ForEach-Object` . En **script block** innehåller `$_` variabeln som representerar det aktuella pipeline-objektet. Tids stämplings strängen avgränsas med kolon som ersätts med punkter.

`New-Item` använder parametern **Path** för att ange platsen för en ny katalog. Sökvägen innehåller `$timestamp` variabeln som katalog namn. Parametern **Type** anger att en katalog har skapats.

### Exempel 9: konvertera en Unix-tidsstämpel

I det här exemplet konverteras en UNIX-tid (som representeras av antalet sekunder sedan 1970-01-01 0:00:00) till DateTime.

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### Exempel 10: returnera ett datum värde som tolkas som UTC

Det här exemplet illustrerar hur du tolkar ett datum värde som dess UTC-motsvarighet. I exemplet är den här datorn inställd på **Pacific, normal tid**. Som standard `Get-Date` returnerar värden för den tids zonen. Använd parametern **AsUTC** för att konvertera värdet till UTC-ekvivalent tid.

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## PARAMETRAR

### -AsUTC

Konverterar datumvärdet till motsvarande tid i UTC.

Den här parametern introducerades i PowerShell 7,1.

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

### -Datum

Anger ett datum och en tid. Tiden är valfri och om det inte anges returneras 00:00:00.

Ange datum och tid i ett format som är standard för system språket.

Till exempel på engelska (USA):

`Get-Date -Date "6/25/2019 12:30:22"` Returnerar tisdag, 25 juni 2019 12:30:22

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – Dag

Anger den dag i månaden som visas. Ange ett värde från 1 till 31.

Om det angivna värdet är större än antalet dagar i månaden lägger PowerShell till antalet dagar i månaden. Visar till exempel `Get-Date -Month 2 -Day 31` **3 mars**, inte **31 februari**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayHint

Anger vilka element i datum och tid som visas.

De godkända värdena är följande:

- **Datum**: visar endast datumet
- **Tid**: visar endast tiden
- **Datetime**: visar datum och tid

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Format

Visar datum och tid i det Microsoft .NET Framework-format som anges av format specifikationen.
**Format** parametern matar ut ett **String** -objekt.

En lista över tillgängliga .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).

När **format** parametern används `Get-Date` får endast **datetime** -objektets egenskaper som krävs för att visa datumet. Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.

Från och med PowerShell 5,0 kan du använda följande ytterligare format som värden för parametern **format** .

- **Filedate**. En fil eller Sök vägs vänlig representation av aktuellt datum i lokal tid. Formatet är `yyyyMMdd` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad och en dag med två siffror). Exempel:
  20190627.

- **FileDateUniversal**. En fil eller Sök vägs vänlig representation av aktuellt datum i Universal Time (UTC). Formatet är `yyyyMMddZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, en dag med en bokstav `Z` som UTC-indikator). Till exempel: 20190627Z.

- **FileDateTime**. En fil eller Sök vägs vänlig representation av aktuellt datum och tid i 24-timmarsformat. Formatet är `yyyyMMddTHHmmssffff` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund och 4-siffriga millisekunder). Till exempel: 20190627T0840107271.

- **FileDateTimeUniversal**. En fil eller Sök vägs vänlig representation av aktuellt datum och tid i Universal Time (UTC) i 24-timmarsformat. Formatet är `yyyyMMddTHHmmssffffZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund, 4-siffriga millisekunder och bokstaven `Z` som UTC-indikator). Till exempel: 20190627T1540500718Z.

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Timme

Anger den timme som visas. Ange ett värde mellan 0 och 23.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Millisekunde

Anger millisekunderna i datumet. Ange ett värde mellan 0 och 999.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minut

Anger minuten som visas. Ange ett värde mellan 0 och 59.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Månad

Anger den månad som visas. Ange ett värde mellan 1 och 12.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Sekund

Anger det andra som visas. Ange ett värde mellan 0 och 59.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UFormat

Visar datum och tid i UNIX-format. **UFormat** -parametern matar ut ett String-objekt.

**UFormat** -specificerarna föregås av ett procent tecken ( `%` ), till exempel, `%m` , `%d` och `%Y` . Avsnittet [anteckningar](#notes) innehåller en tabell med giltiga **UFormat-specificerare**.

När parametern **UFormat** används `Get-Date` får bara **datetime** -objektets egenskaper som krävs för att visa datumet. Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnixTimeSeconds

Datum och tid som representeras i sekunder sedan 1 januari 1970, 0:00:00.

Den här parametern introducerades i PowerShell 7,1.

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -År

Anger året som visas. Ange ett värde mellan 1 och 9999.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Pipeline-inmatade

`Get-Date` accepterar pipeline-ininformation. Ett exempel är `Get-ChildItem | Get-Date`.

## UTDATA

### System. DateTime eller system. String

`Get-Date` Returnerar ett **datetime** -objekt utom när **format** -och **UFormat** -parametrarna används. **Format** -eller **UFormat** -parametrarna returnerar **sträng** objekt.

När ett **datetime** -objekt skickas ned pipelinen till en-cmdlet, till exempel `Add-Content` som förväntar sig sträng Indatatyp, konverterar PowerShell objektet till ett **String** -objekt.

Metoden `(Get-Date).ToString()` konverterar ett **datetime** -objekt till **ett String** -objekt.

Om du vill visa ett objekts egenskaper och metoder skickar du objektet nedåt i pipeline till `Get-Member` .
Ett exempel är `Get-Date | Get-Member`.

## ANTECKNINGAR

**Datetime** -objekt är i långa och långa format för system språket.

Giltiga **UFormat-specificerare** visas i följande tabell:

| Format specificerare |                                 Betydelse                     |         Exempel          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | Veckodag-fullständigt namn                                             | Måndag                   |
| `%a` | Veckodag-förkortat namn                                      | Mån                      |
| `%B` | Månads namn – fullständig                                                       | Januari                  |
| `%b` | Månads namn – förkortat                                                | Jan                      |
| `%C` | 1900                                                                 | 20 för 2019              |
| `%c` | Datum och tid – förkortat                                             | Tor Jun 27 08:44:18 2019 |
| `%D` | Datum i formatet åååå-mm-dd                                                 | 06/27/19                 |
| `%d` | Dag i månaden – 2 siffror                                             | 05                       |
| `%e` | Dag i månaden – föregås av ett blank steg om bara en siffra           | \<space\>5               |
| `%F` | Datum i åååå-mm-dd-format, motsvarar% Y-% m-% d (ISO 8601-datum format) | 2019-06-27               |
| `%G` | Samma som "Y"                                                             |                          |
| `%g` | Samma som "y"                                                             |                          |
| `%H` | Timme i 24-timmarsformat                                                  | 17                       |
| `%h` | Samma som "b"                                                             |                          |
| `%I` | Timme i 12-timmarsformat                                                  | 05                       |
| `%j` | Dag på året                                                         | 1-366                    |
| `%k` | Samma som "H"                                                             |                          |
| `%l` | Samma som "I" (versal I)                                              | 05                       |
| `%M` | Minuter                                                                 | 35                       |
| `%m` | Månadsnummer                                                            | 06                       |
| `%n` | rad matnings tecknet                                                       |                          |
| `%p` | FM eller EM                                                                |                          |
| `%R` | Tid i 24-timmarsformat – inga sekunder                                      | 17:45                    |
| `%r` | Tid i 12-timmarsformat                                                  | 09:15:36 AM              |
| `%S` | Sekunder                                                                 | 05                       |
| `%s` | Förflutna sekunder sedan den 1 januari 1970 00:00:00                          | 1150451174               |
| `%t` | Vågrätt tabbtecken                                                |                          |
| `%T` | Tid i 24-timmarsformat                                                  | 17:45:52                 |
| `%U` | Samma som "W"                                                             |                          |
| `%u` | Veckodag-nummer                                                | Söndag = 0               |
| `%V` | Vecka på året                                                        | 01-53                    |
| `%w` | Samma som u                                                             |                          |
| `%W` | Vecka på året                                                        | 00-52                    |
| `%X` | Samma som t '                                                             |                          |
| `%x` | Datum i standardformat för språkvariant                                      | 06/27/19 för engelska – USA  |
| `%Y` | År i 4-siffrigt format                                                  | 2019                     |
| `%y` | År i 2-siffrigt format                                                  | 19                       |
| `%Z` | Tids zons förskjutning från Universal Time Coordinator (UTC)                   | -07                      |

## RELATERADE LÄNKAR

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Culture](Get-Culture.md)

[Hämta medlem](Get-Member.md)

[Nytt objekt](../Microsoft.PowerShell.Management/New-Item.md)

[New-TimeSpan](New-TimeSpan.md)

[Ange datum](Set-Date.md)
