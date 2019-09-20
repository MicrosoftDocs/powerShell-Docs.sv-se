---
ms.date: 09/13/2019
title: Skapar Get-WinEvent-frågor med FilterHashtable
ms.openlocfilehash: 1bf321c09c20736de36eb896fabced31cfdfbd75
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143660"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Skapar Get-WinEvent-frågor med FilterHashtable

Om du vill läsa det ursprungliga blogg inlägget 3 juni 2014 **Scripting Guy** , se [använda FilterHashTable för att filtrera händelse loggen med PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

Den här artikeln är ett utdrag från det ursprungliga blogg inlägget och förklarar hur du använder `Get-WinEvent` cmdletens **FilterHashtable** -parameter för att filtrera händelse loggar. PowerShell- `Get-WinEvent` cmdleten är en kraftfull metod för att filtrera Windows-händelser och diagnostikloggar. Prestanda förbättras när en `Get-WinEvent` fråga använder parametern **FilterHashtable** .

När du arbetar med stora händelse loggar är det inte effektivt att skicka objekt nedåt i pipelinen till ett `Where-Object` kommando. Innan PowerShell 6 `Get-EventLog` var cmdleten ett annat alternativ för att hämta loggdata. Följande kommandon är till exempel ineffektiva för att filtrera **Microsoft-Windows-defrag-** loggar:

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

Följande kommando använder en hash-tabell som förbättrar prestandan:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Blogg inlägg om uppräkning

Den här artikeln visar information om hur du använder uppräknade värden i en hash-tabell. Om du vill ha mer information om uppräkning läser du dessa blogg inlägg i **skript Guy** . Information om hur du skapar en funktion som returnerar de uppräknade värdena finns i [uppräkningar och värden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Mer information finns i [Scripting Guy-serien av blogg inlägg om uppräkning](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Nyckel/värde-par för hash-tabell

Om du vill bygga effektiva frågor använder `Get-WinEvent` du cmdleten med parametern **FilterHashtable** .
**FilterHashtable** accepterar en hash-tabell som ett filter för att hämta detaljerad information från händelse loggar i Windows. En hash-tabell använder **nyckel/värde-** par. Mer information om hash-tabeller finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Om **nyckel-/värdeparen** finns på samma rad måste de avgränsas med ett semikolon. Om varje **nyckel/värde-** par finns på en separat rad behövs inte semikolonet. I den här artikeln placeras till exempel **nyckel-** värdepar på separata rader och använder inte semikolon.

I det här exemplet används flera av **FilterHashtable** -parameterns **nyckel/värde-** par. Den slutförda frågan innehåller **LogName**, **ProviderName**, **keywords**, **ID**och **Level**.

De godtagna **nyckel/värdeparen** visas i följande tabell och ingår i dokumentationen för parametern [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** .

I följande tabell visas nyckel namnen, data typerna och om jokertecken accepteras för ett data värde.

|    Nyckelnamn    | Värde data typ | Accepterar jokertecken? |
| -------------- | --------------- | ---------------------------- |
| LogName        | `<String[]>`    | Ja                          |
| ProviderName   | `<String[]>`    | Ja                          |
| Sökväg           | `<String[]>`    | Nej                           |
| Nyckelord       | `<Long[]>`      | Nej                           |
| ID             | `<Int32[]>`     | Nej                           |
| Nivå          | `<Int32[]>`     | Nej                           |
| /St      | `<DateTime>`    | Nej                           |
| Slut        | `<DateTime>`    | Nej                           |
| Användar-ID         | `<SID>`         | Nej                           |
| Data           | `<String[]>`    | Nej                           |
| \<namngivna data\> | `<String[]>`    | Nej                           |

Den \<namngivna data\> nyckeln representerar ett namngivet händelse data fält. Till exempel kan Perflib Event 1008 innehålla följande händelse data:

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

Du kan fråga efter dessa händelser med hjälp av följande kommando:

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

## <a name="building-a-query-with-a-hash-table"></a>Skapa en fråga med en hash-tabell

Om du vill kontrol lera resultaten och felsöka problem kan du skapa hash-tabellen med ett **nyckel/värde-** par i taget. Frågan hämtar data från **program** loggen. Hash-tabellen motsvarar `Get-WinEvent –LogName Application`.

Börja genom att skapa `Get-WinEvent` frågan. Använd **FilterHashtable** -parameterns **nyckel/värde** -par med nyckeln, **LogName**och värdet, **programmet**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Fortsätt att skapa hash-tabellen med **ProviderName** -nyckeln. **ProviderName** är det namn som visas i fältet **källa** i **Windows Loggboken**. Till exempel **.NET Runtime** på följande skärm bild:

![Bild av Windows Loggboken-källor.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Uppdatera hash-tabellen och inkludera **nyckel/värde** -paret med nyckeln, * * ProviderName och värdet **.NET Runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Använd **Sök vägs** nyckeln om din fråga behöver hämta data från arkiverade händelse loggar. Värdet **Path** anger den fullständiga sökvägen till logg filen. Mer information finns i blogg inlägget **Scripting Guy** , [använda PowerShell för att analysera sparade händelse loggar för fel](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Använda uppräknade värden i en hash-tabell

**Nyckelord** är nästa nyckel i hash-tabellen. Data typen **keywords** är en matris av `[long]` värde typen som innehåller ett stort tal. Använd följande kommando för att hitta det högsta värdet `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

För **nyckelords** nyckeln använder PowerShell ett nummer, inte en sträng som **säkerhet**. **Windows Loggboken** visar **nyckelorden** som strängar, men de är uppräknade värden. Om du använder **nyckelords** nyckeln med ett sträng värde i hash-tabellen visas ett fel meddelande.

Öppna **Windows Loggboken** och klicka på **Filtrera aktuell logg**i fönstret **åtgärder** .
På den nedrullningsbara menyn **nyckelord** visas tillgängliga nyckelord, som du ser på följande skärm bild:

![Bild av Windows Loggboken nyckelord.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Använd följande kommando för att visa `StandardEventKeywords` egenskaps namnen.

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

De uppräknade värdena dokumenteras i **.NET Framework**. Mer information finns i [StandardEventKeywords-uppräkning](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

**Nyckelords** namnen och de uppräknade värdena är följande:

| Namn             |  Värde            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| SQM              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| SLA svarstid     | 281474976710656   |
| Inga             | 0                 |

Uppdatera hash-tabellen och inkludera **nyckel/värde** -paret med nyckeln, **nyckelorden**och **EventLogClassic** -uppräkning svärdet **36028797018963968**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Nyckelord statiskt egenskaps värde (valfritt)

**Nyckelords** nyckeln räknas upp, men du kan använda ett statiskt egenskaps namn i hash-tabellens fråga.
I stället för att använda den returnerade strängen måste egenskaps namnet konverteras till ett värde med egenskapen **Value _ _** .

Följande skript använder till exempel egenskapen **Value _ _** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtrera efter händelse-ID

För att få mer information, filtreras frågans resultat efter **händelse-ID**. **Händelse-ID: t** refereras i hash-tabellen som nyckel **-ID** och värdet är ett särskilt **händelse-ID**. **Windows-Loggboken** visar **händelse-ID: t**. I det här exemplet används **händelse-Id 1023**.

Uppdatera hash-tabellen och inkludera **nyckel/värde** -paret med nyckeln, **ID: t** och värdet **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtrera efter nivå

Om du vill förfina resultaten ytterligare och bara inkludera händelser som är fel använder du **nivå** nyckeln.
**Windows Loggboken** visar **nivån** som sträng värden, men de är uppräknade värden. Om du använder **nivå** nyckeln med ett sträng värde i hash-tabellen visas ett fel meddelande.

**Nivån** har värden som **fel**, **Varning**eller **information**. Använd följande kommando för att visa `StandardEventLevel` egenskaps namnen.

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

De uppräknade värdena dokumenteras i **.NET Framework**. Mer information finns i [StandardEventLevel-uppräkning](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

**Nivå** nyckelns namn och uppräknade värden är följande:

| Namn           | Värde |
| -------------- | ----- |
| Verbose        |   5   |
| Informativt  |   4   |
| Varning        |   3   |
| Fel          |   2   |
| Kritiskt       |   1   |
| LogAlways      |   0   |

Hash-tabellen för den slutförda frågan innehåller nyckeln, **nivån**och värdet, **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Nivå statisk egenskap i uppräkning (valfritt)

**Nivå** nyckeln räknas upp, men du kan använda ett statiskt egenskaps namn i hash-tabellens fråga.
I stället för att använda den returnerade strängen måste egenskaps namnet konverteras till ett värde med egenskapen **Value _ _** .

Följande skript använder till exempel egenskapen **Value _ _** .

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