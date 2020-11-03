---
description: Förklarar hur du använder en växel för att hantera flera `If` instruktioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 2b39f8e0ad49c9e5f6cab06eea34e8f27b37186b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270368"
---
# <a name="about-switch"></a>Om-växel

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du använder en växel för att hantera flera `If` instruktioner.

## <a name="long-description"></a>Lång beskrivning

Om du vill kontrol lera ett villkor i ett skript eller en funktion använder du en `If` instruktion. `If`Instruktionen kan kontrol lera många typer av villkor, inklusive värdet för variabler och egenskaper för objekt.

Använd en instruktion för att kontrol lera flera villkor `Switch` . `Switch`Instruktionen motsvarar en serie `If` instruktioner, men det är enklare. `Switch`Instruktionen visar varje villkor och en valfri åtgärd. Om ett villkor hämtas utförs åtgärden.

`Switch`Instruktionen kan använda `$_` `$switch` Automatiska variabler och. Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).

En Basic- `Switch` instruktion har följande format:

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

Följande `Switch` uttryck jämför exempelvis testvärdet, 3, för var och en av villkoren. När testvärdet matchar villkoret utförs åtgärden.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

I det här enkla exemplet jämförs värdet med varje villkor i listan, även om det finns en matchning för värdet 3. Följande `Switch` instruktion har två villkor för värdet 3. Det visar att alla villkor testas som standard.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

Använd instruktionen om du vill leda `Switch` till att jämförelsen avbryts efter en matchning `Break` . Instruktionen `Break` avslutar `Switch` instruktionen.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

Om testvärdet är en samling, till exempel en matris, utvärderas varje objekt i samlingen i den ordning som den visas. I följande exempel utvärderas 4 och sedan 2.

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

Alla `Break` instruktioner gäller för samlingen, inte för varje värde, som du ser i följande exempel. `Switch`Instruktionen avslutas med `Break` instruktionen i villkoret för värdet 4.

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a>Syntax

Den fullständiga `Switch` syntaxen för uttrycket är följande:

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

eller

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

Om inga parametrar används, `Switch` fungerar samma sak som att använda den **exakta** parametern. En Skift läges okänslig matchning för värdet utförs. Om värdet är en samling utvärderas varje element i den ordning som det visas.

`Switch`Instruktionen måste innehålla minst en villkors instruktion.

`Default`Satsen utlöses när värdet inte matchar något av villkoren. Den motsvarar en `Else` sats i en `If` instruktion. Endast en `Default` sats tillåts i varje `Switch` instruktion.

`Switch` har följande parametrar:

- **Jokertecken** – anger att villkoret är en jokertecken. Om match-satsen inte är en sträng ignoreras parametern. Jämförelsen är inte Skift läges känslig.
- **Exakt** -visar att match-satsen, om det är en sträng, måste matcha exakt. Om match-satsen inte är en sträng ignoreras den här parametern. Jämförelsen är inte Skift läges känslig.
- **CaseSensitive** – utför en Skift läges känslig matchning. Om match-satsen inte är en sträng ignoreras den här parametern.
- **File** – tar emot indata från en fil i stället för en värde instruktion. Om flera **fil** parametrar ingår, används bara den sista. Varje rad i filen läses och utvärderas av `Switch` instruktionen. Jämförelsen är inte Skift läges känslig.
- **Regex** – utför matchning av reguljära uttryck för värdet på villkoret. Om match-satsen inte är en sträng ignoreras den här parametern.
  Jämförelsen är inte Skift läges känslig. Den `$matches` automatiska variabeln är tillgänglig för användning i det matchande instruktions blocket.

> [!NOTE]
> När du anger motstridiga värden, t. ex. **regex** och **jokertecken** , har den senast angivna parametern företräde och alla motstridiga parametrar ignoreras. Flera instanser av parametrar tillåts också. Men endast den sista parametern som används är giltig.

I det här exemplet skickas ett objekt som inte är en sträng eller numeriska data till `Switch` . Den `Switch` utför en sträng som tvingas på objektet och utvärderar resultatet.

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

I det här exemplet finns det inget matchande fall, så det finns inga utdata.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

Genom att lägga till `Default` -satsen kan du utföra en åtgärd när inga andra villkor lyckas.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

För ordet "fjorton" för att matcha ett ärende måste du använda `-Wildcard` parametern eller `-Regex` .

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

I följande exempel används `-Regex` parametern.

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

Ett villkor för Switch-satsen kan vara antingen:

- Ett uttryck vars värde jämförs med indatavärdet
- Ett skript block som ska returneras `$true` om ett villkor uppfylls.

Den `$_` automatiska variabeln innehåller det värde som skickas till Switch-instruktionen och är tillgänglig för utvärdering och användning inom villkors satsernas omfattning.

Åtgärden för varje villkor är oberoende av åtgärderna i andra villkor.

I följande exempel demonstreras användningen av skript block som `Switch` villkor för uttrycket.

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

Om värdet matchar flera villkor körs åtgärden för varje villkor. Om du vill ändra det här beteendet använder du `Break` `Continue` nyckelorden eller.

`Break`Nyckelordet stoppar bearbetningen och avslutar `Switch` instruktionen.

`Continue`Nyckelordet slutar bearbeta det aktuella värdet, men fortsätter att bearbeta eventuella efterföljande värden.

Följande exempel bearbetar en matris med tal och visar om de är udda eller jämna. Negativa tal hoppas över med `Continue` nyckelordet. Om ett icke-nummer påträffas avslutas körningen med `Break` nyckelordet.

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a>Se även

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)
