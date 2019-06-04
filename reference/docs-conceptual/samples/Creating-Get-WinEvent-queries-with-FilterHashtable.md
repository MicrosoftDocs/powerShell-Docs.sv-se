---
ms.date: 03/18/2019
title: Skapar Get-WinEvent-frågor med FilterHashtable
ms.openlocfilehash: 2f598fceb570f189bee776b6ed572b11a6938f64
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66471012"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Skapar Get-WinEvent-frågor med FilterHashtable

Att läsa den ursprungliga juni 3 2014 **Scripting Guy** blogg post-, se [Använd FilterHashTable att filtrera händelseloggen med PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

Den här artikeln är ett utdrag ur ursprungliga blogginlägget och förklarar hur du använder den `Get-WinEvent` cmdletens **FilterHashtable** parameter för att filtrera händelseloggar. PowerShell- `Get-WinEvent` cmdleten är en kraftfull metod för att filtrera Windows händelse- och diagnostikloggar. Prestanda förbättras när en `Get-WinEvent` fråga använder den **FilterHashtable** parametern.

När du arbetar med stora händelseloggar, är det inte effektivt att skicka objekt att pipelinen en `Where-Object` kommando. Innan du PowerShell 6, den `Get-EventLog` cmdlet har ett annat alternativ att hämta loggdata. Till exempel följande kommandon är ineffektiv till filter på **Microsoft-Windows-defragmenterar** loggar:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

Följande kommando använder en hash-tabell som förbättrar prestanda:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Blogginlägg om uppräkning

Den här artikeln innehåller information om hur du använder uppräknade värden i en hash-tabell. Mer information om uppräkning Läs dessa **Scripting Guy** blogginlägg. För att skapa en funktion som returnerar uppräknade värden, se [uppräkningar och värden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Mer information finns i den [Scripting Guy serie blogg inlägg om uppräkningen](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Hash-tabell nyckel/värde-par

För att skapa effektiva frågor, använda den `Get-WinEvent` cmdlet med den **FilterHashtable** parametern.
**FilterHashtable** accepterar en hash-tabell som ett filter för att få specifik information från Windows-händelseloggar. En hash-tabell använder **nyckel/värde** par. Mer information om hash-tabeller finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Om den **nyckel/värde** par är på samma rad, de måste avgränsas med semikolon. Om varje **nyckel/värde** par är på en separat rad, semikolon behövs inte. Exempelvis kan den här artikeln placerar **nyckel/värde** kombinationer av på separata rader och inte använda semikolon.

Det här exemplet används flera av de **FilterHashtable** parameterns **nyckel/värde** par. Slutförda frågan innehåller **loggnamn**, **ProviderName**, **nyckelord**, **ID**, och **nivå**.

Det godkända **nyckel/värde** par visas i följande tabell och ingår i dokumentationen för den [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.

I följande tabell visar namn, datatyper, och om jokertecken godkänns för värdet.

| Nyckelnamn     | Värdetyp för data    | Accepterar jokertecken? |
|------------- | ------------------ | ---------------------------- |
| Loggnamn      | `<String[]>`       | Ja |
| ProviderName | `<String[]>`       | Ja |
| Sökväg         | `<String[]>`       | Nej  |
| Nyckelord     | `<Long[]>`         | Nej  |
| ID           | `<Int32[]>`        | Nej  |
| Nivå        | `<Int32[]>`        | Nej  |
| startTime    | `<DateTime>`       | Nej  |
| endTime      | `<DateTime>`       | Nej  |
| Användar-ID       | `<SID>`            | Nej  |
| Data         | `<String[]>`       | Nej  |
| *            | `<String[]>`       | Nej  |

## <a name="building-a-query-with-a-hash-table"></a>Att skapa en fråga med en hash-tabell

För att kontrollera resultaten och felsöka problem, det hjälper dig för att skapa en hash-tabellen **nyckel/värde** paret åt gången. Frågan hämtar data från den **program** log. Hash-tabellen motsvarar `Get-WinEvent –LogName Application`.

Börja genom att skapa den `Get-WinEvent` fråga. Använd den **FilterHashtable** parameterns **nyckel/värde** paras ihop med nyckeln, **loggnamn**, och värdet, **program**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Fortsätt att skapa hash-tabellen med den **ProviderName** nyckel. Den **ProviderName** är det namn som visas i den **källa** i den **Windows Loggboken**. Till exempel **.NET Runtime** i följande skärmbild:

![Bild av Windows Loggboken källor.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Uppdatera hash-tabellen och inkludera den **nyckel/värde** paras ihop med nyckeln, ** ProviderName, och värdet, **.NET Runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Om din fråga måste hämta data från arkiverade händelseloggar, använder du den **sökväg** nyckel. Den **sökväg** värdet anger den fullständiga sökvägen till loggfilen. Mer information finns i den **Scripting Guy** blogginlägget [Använd PowerShell för att parsa sparade händelseloggarna för fel](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Använda uppräknade värden i en hash-tabell

**Nyckelord** är nästa nyckel i hash-tabellen. Den **nyckelord** datatyp är en matris med de `[long]` värdetyp som innehåller ett stort antal. Använd följande kommando för att hitta det maximala värdet `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

För den **nyckelord** nyckel, PowerShell använder ett tal, inte en sträng som **Security**. **Windows Loggboken** visar den **nyckelord** som strängar, men de är uppräknade värden. I hashtabellen, om du använder den **nyckelord** nyckeln med ett strängvärde, visas ett felmeddelande.

Öppna den **Windows Loggboken** och från den **åtgärder** klickar du på på **Filtrera aktuell logg**.
Den **nyckelord** nedrullningsbara menyn visar tillgängliga nyckelord, enligt följande skärmbild:

![Bild av Windows Loggboken nyckelord.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Använd följande kommando för att visa den `StandardEventKeywords` egenskapsnamn.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Uppräknade värden är dokumenterade i den **.NET Framework**. Mer information finns i [StandardEventKeywords uppräkning](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

Den **nyckelord** namn och uppräknade värden är följande:

| Namn             |  Värde            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Inga             | 0                 |

Uppdatera hash-tabellen och inkludera den **nyckel/värde** paras ihop med nyckeln, **nyckelord**, och **EventLogClassic** uppräkningsvärdet **36028797018963968** .

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Nyckelord statiska egenskapsvärdet (valfritt)

Den **nyckelord** nyckel räknas, men du kan använda en statisk egenskapsnamn i frågan för hash-tabell.
I stället för den returnerade strängen, egenskapsnamnet måste konverteras till ett värde med den **Value__** egenskapen.

Till exempel följande skript använder den **Value__** egenskapen.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtrering efter händelse-Id

Om du vill ha mer specifika data, resultatet av frågan filtreras efter **händelse-Id**. Den **händelse-Id** refereras till i hash-tabell som nyckel **ID** och värdet är en specifik **händelse-Id**. Den **Windows Loggboken** visar den **händelse-Id**. Det här exemplet används **händelse-Id 1023**.

Uppdatera hash-tabellen och inkludera den **nyckel/värde** paras ihop med nyckeln, **ID** och värdet, **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtrera efter nivå

För att ytterligare förfina resultaten och inkluderar endast de händelser som är fel, Använd den **nivå** nyckel.
**Windows Loggboken** visar den **nivå** som sträng värden, men de är uppräknade värden. I hashtabellen, om du använder den **nivå** nyckeln med ett strängvärde, visas ett felmeddelande.

**Nivå** har värden som **fel**, **varning**, eller **information**. Använd följande kommando för att visa den `StandardEventLevel` egenskapsnamn.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Uppräknade värden är dokumenterade i den **.NET Framework**. Mer information finns i [StandardEventLevel uppräkning](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

Den **nivå** nyckelns namn och uppräknade värden är följande:

| Namn           | Värde |
| -------------- | ----- |
| Verbose        |   5   |
| Informativt  |   4   |
| Varning        |   3   |
| Fel          |   2   |
| Kritiskt       |   1   |
| LogAlways      |   0   |

Hash-tabellen för slutförda frågan innehåller nyckeln, **nivå**, och värdet, **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Nivån statisk egenskap i uppräkningen (valfritt)

Den **nivå** nyckel räknas, men du kan använda en statisk egenskapsnamn i frågan för hash-tabell.
I stället för den returnerade strängen, egenskapsnamnet måste konverteras till ett värde med den **Value__** egenskapen.

Till exempel följande skript använder den **Value__** egenskapen.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```