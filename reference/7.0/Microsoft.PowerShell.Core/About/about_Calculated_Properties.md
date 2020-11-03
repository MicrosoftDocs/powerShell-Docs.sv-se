---
description: PowerShell ger möjlighet att dynamiskt lägga till nya egenskaper och ändra formateringen av objekts utdata till pipelinen.
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 7937d4e59f2e73c8b52e9957dd143b6d48eeae57
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270092"
---
# <a name="about-calculated-properties"></a>Om beräknade egenskaper

## <a name="short-description"></a>Kort beskrivning

PowerShell ger möjlighet att dynamiskt lägga till nya egenskaper och ändra formateringen av objekts utdata till pipelinen.

## <a name="long-description"></a>Lång beskrivning

Ett antal PowerShell-cmdletar transformerar, aggregerar eller bearbetar indata till utgående objekt med parametrar som tillåter tillägg av nya egenskaper till dessa utdata-objekt. Dessa parametrar kan användas för att generera nya, beräknade egenskaper för utgående objekt baserat på värdena för indata-objekt.
Den beräknade egenskapen definieras av en [hash](about_hash_tables.md) som innehåller nyckel/värde-par som anger namnet på den nya egenskapen, ett uttryck för att beräkna värdet och eventuell formateringsinformation.

## <a name="supported-cmdlets"></a>Cmdlets som stöds

Följande cmdletar stöder beräknade egenskaps värden för **egenskaps** parametern. `Format-*`Cmdletarna stöder också beräknade värden för **groupby** -parametern.

I följande lista specificeras de cmdletar som stöder beräknade egenskaper och nyckel/värde-par som stöds av varje cmdlet.

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - `name`/`label` – valfritt (lades till i PowerShell 6. x)
  - `expression`
  - `width` – valfritt
  - `alignment` – valfritt

- `Format-Custom`
  - `expression`
  - `depth` – valfritt

- `Format-List`
  - `name`/`label` – valfritt
  - `expression`
  - `formatstring` – valfritt

  Samma uppsättning nyckel/värde-par gäller också beräknade egenskaps värden som skickas till **groupby** -parametern för alla `Format-*` cmdletar.

- `Format-Table`
  - `name`/`label` – valfritt
  - `expression`
  - `formatstring` – valfritt
  - `width` – valfritt
  - `alignment` – valfritt

- `Format-Wide`
  - `expression`
  - `formatstring` – valfritt

- `Group-Object`
  - `expression`

- `Measure-Object`
  - Stöder endast ett skript block för uttrycket, inte en hash-tabellen.
  - Stöds inte i PowerShell 5,1 och äldre.

- `Select-Object`
  - `name`/`label` – valfritt
  - `expression`

- `Sort-Object`
  - `expression`
  - `ascending`/`descending` – valfritt

> [!NOTE]
> Värdet för `expression` kan vara ett skript block i stället för en hash-tabellen. Mer information finns i avsnittet om [anteckningar](#notes) .

## <a name="hashtable-key-definitions"></a>Nyckel definitioner för hash

- `name`/`label` -Anger namnet på den egenskap som skapas. Du kan använda `name` eller dess alias, `label` och de är utbytbara.
- `expression` – Ett skript block som används för att beräkna värdet för den nya egenskapen.
- `alignment` – Används av cmdletar som producerar tabell data för att definiera hur värdena visas i en kolumn. Värdet måste vara `'left'` , `'center'` eller `'right'` .
- `formatstring` -Anger en format sträng som definierar hur värdet formateras för utdata. Mer information om format strängar finns i [format typer i .net](/dotnet/standard/base-types/formatting-types).
- `width` -Anger kolumnen maximal bredd i en tabell när värdet visas. Värdet måste vara större än `0` .
- `depth` – Parametern **djup** för `Format-Custom` anger djupet för expansionen för alla egenskaper. Med `depth` nyckeln kan du ange djupet för expansion per egenskap.
- `ascending` / `descending` – Gör att du kan ange sorterings ordningen för en eller flera egenskaper. Dessa är booleska värden.

Hash-nycklarna behöver inte stavas ut så länge det angivna namnet är oklart. Kan till exempel `n` användas i stället för `Name` och `e` kan användas i stället för `Expression` .

## <a name="examples"></a>Exempel

### <a name="compare-object"></a>Compare-Object

Med beräknade egenskaper kan du styra hur egenskaperna för inobjekten ska jämföras. I det här exemplet i stället för att jämföra värdena direkt, jämförs värdena med resultatet av den aritmetiska åtgärden (modul 2).

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a>ConvertTo-Html

`ConvertTo-Html` kan konvertera en samling objekt till en HTML-tabell.
Med beräknade egenskaper kan du styra hur tabellen presenteras.

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

I det här exemplet skapas en HTML-tabell som innehåller en lista med PowerShell-alias och antalet parametrar för varje aliased-kommando. Värdena för **ParameterCount** -kolumnen centreras.

### <a name="format-custom"></a>Format-Custom

`Format-Custom` innehåller en anpassad vy av ett objekt i ett format som liknar en klass definition. Mer komplexa objekt kan innehålla medlemmar som är djupt kapslade med komplexa typer. Parametern **djup** i `Format-Custom` anger djupet för expansionen för alla egenskaper. Med `depth` nyckeln kan du ange djupet för expansion per egenskap.

I det här exemplet `depth` fören klar nyckeln den anpassade utdata för `Get-Date` cmdleten. `Get-Date` Returnerar ett **datetime** -objekt. **Datum** egenskapen för det här objektet är också ett **datetime** -objekt, så objektet är kapslat.

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a>Format-List

I det här exemplet använder vi beräknade egenskaper för att ändra namn och format på utdata från `Get-ChildItem` .

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a>Format-Table

I det här exemplet lägger den beräknade egenskapen till en **typ** -egenskap som används för att klassificera filerna efter innehålls typ.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a>Format-Wide

Med `Format-Wide` cmdleten kan du Visa värdet för en egenskap för objekt i en samling som en lista med flera kolumner.

I det här exemplet vill vi se fil namnet och storleken (i kilobyte) som en bred lista. Eftersom `Format-Wide` visar inte mer än en egenskap, använder vi en beräknad egenskap för att kombinera värdet för två egenskaper till ett enda värde.

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a>Group-Object

`Group-Object`Cmdleten visar objekt i grupper baserat på värdet för en angiven egenskap. I det här exemplet räknar den beräknade egenskapen antalet filer av varje innehålls typ.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a>Measure-Object

`Measure-Object`Cmdleten beräknar numeriska egenskaper för objekt. I det här exemplet använder vi en beräknad egenskap för att hämta antalet ( **summan** ) av talen, mellan 1 och 10, som är jämnt delbar med 3.

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> Till skillnad från andra cmdletar `Measure-Object` accepterar inte en hash-tabellen för beräknade egenskaper. Du måste använda ett skript block.

### <a name="select-object"></a>Select-Object

Du kan använda beräknade egenskaper för att lägga till ytterligare medlemmar i objektets utdata med `Select-Object` cmdleten. I det här exemplet visar vi PowerShell-alias som börjar med bokstaven `C` . Med hjälp av skickar `Select-Object` vi aliaset, den cmdlet som det mappas till och antalet parametrar som definierats för cmdleten. Med en beräknad egenskap kan vi skapa egenskapen **ParameterCount** .

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a>Sort-Object

Med hjälp av beräknade egenskaper kan du sortera data i olika ordrar per egenskap. I det här exemplet sorteras data från en CSV-fil i stigande ordning efter **datum**. Men inom varje datum sorteras raderna i fallande ordning efter **UnitsSold**.

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a>Kommentarer

- Du kan ange uttryckets skript block _direkt_ , som ett argument, i stället för att ange det som `Expression` post i en hash-fil. Ett exempel:

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  Det här exemplet är praktiskt för cmdletar som inte kräver (eller stöder) namngivning av en egenskap via `Name` nyckeln, till exempel `Sort-Object` , `Group-Object` och `Measure-Object` .

  För cmdletar som stöder namngivning av egenskapen, konverteras skript blocket till en sträng och används som namn på egenskapen i utdata.

- `Expression` skript block körs i _underordnade_ omfång, vilket innebär att anroparens variabler inte kan ändras direkt.

- Pipeline-logiken används för utdata från `Expression` skript block. Det innebär att en matris med ett enda element gör att matrisen blir unwrap.

- I de flesta cmdlets ignoreras fel i uttryck skript block.
  För- `Sort-Object` ,-avsluta-och skript-avsluta-fel är _utdata_ , men de avslutar inte instruktionen.

## <a name="see-also"></a>Se även

[about_Hash_Tables](about_hash_tables.md)

[Jämför objekt](xref:Microsoft.PowerShell.Utility.Compare-Object)

[ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[Format-Custom](xref:Microsoft.PowerShell.Utility.Format-Custom)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Format-Wide](xref:Microsoft.PowerShell.Utility.Format-Wide)

[Gruppera objekt](xref:Microsoft.PowerShell.Utility.Group-Object)

[Mått – objekt](xref:Microsoft.PowerShell.Utility.Measure-Object)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Sortera objekt](xref:Microsoft.PowerShell.Utility.Sort-Object)

[Format typer i .NET](/dotnet/standard/base-types/formatting-types)
