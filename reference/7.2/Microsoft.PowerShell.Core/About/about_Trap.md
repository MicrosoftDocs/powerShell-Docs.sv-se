---
description: Beskriver ett nyckelord som hanterar ett avslutande fel.
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 30b03235cbc2338de3786e37416d1c1ce1d660e3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709240"
---
# <a name="about-trap"></a>Om trap

## <a name="short-description"></a>Kort beskrivning

Beskriver ett nyckelord som hanterar ett avslutande fel.

## <a name="long-description"></a>Lång beskrivning

Ett avslutande fel stoppar en instruktion som körs. Om PowerShell inte hanterar ett avbrotts fel på något sätt slutar PowerShell också att köra funktionen eller skriptet i den aktuella pipelinen. På andra språk, till exempel C#, kallas fel för undantag.

`trap`Nyckelordet anger en lista över instruktioner som ska köras när ett avslutande fel inträffar. `trap` -uttryck hanterar de avslutande felen på följande sätt:

- Visa felet efter bearbetning av `trap` instruktions blocket och fortsätta köra skriptet eller funktionen som innehåller `trap` . Det här är standardbeteendet.

- Visa fel och Avbryt körningen av skriptet eller funktionen som innehåller `trap` using `break` i- `trap` instruktionen.

- Dämpa felet, men fortsätt köra skriptet eller funktionen med `trap` hjälp av `continue` i `trap` instruktionen.

Instruktions listan i `trap` kan innehålla flera villkor eller funktions anrop. En `trap` kan skriva loggar, test villkor eller till och med köra ett annat program.

### <a name="syntax"></a>Syntax

`trap`Instruktionen har följande syntax:

```powershell
trap [[<error type>]] {<statement list>}
```

`trap`Instruktionen innehåller en lista över instruktioner som ska köras när ett avslutande fel inträffar. En `trap` instruktion består av `trap` nyckelordet, eventuellt följt av ett typ uttryck och instruktions blocket som innehåller listan över instruktioner som ska köras när ett fel har fångats. Typ uttrycket begränsar de typer av fel som `trap` fångas.

Ett skript eller kommando kan ha flera `trap` instruktioner. `trap` instruktioner kan visas var som helst i skriptet eller kommandot.

### <a name="trapping-all-terminating-errors"></a>Svällning av alla avslutande fel

När ett avslutande fel inträffar som inte hanteras på ett annat sätt i ett skript eller kommando, kontrollerar PowerShell om det finns en `trap` instruktion som hanterar felet. Om det finns en `trap` instruktion fortsätter PowerShell att köra skriptet eller kommandot i `trap` instruktionen.

Följande exempel är ett väldigt enkelt `trap` uttryck:

```powershell
trap {"Error found."}
```

Den här `trap` instruktionen påfäller eventuella avslutande fel.

I följande exempel innehåller funktionen en InSense-sträng som orsakar ett körnings fel.

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

När den här funktionen körs returneras följande:

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Följande exempel innehåller en `trap` instruktion som visar felet med hjälp av den `$_` automatiska variabeln:

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

Om du kör den här versionen av funktionen returneras följande:

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> `trap` -instruktioner kan definieras var som helst inom ett angivet omfång, men gäller alltid alla-instruktioner i det omfånget. Vid körning `trap` definieras instruktioner i ett block innan andra instruktioner körs. I Java Script kallas detta för att [lyfta](https://wikipedia.org/wiki/JavaScript_syntax#hoisting). Detta innebär att `trap` instruktioner gäller för alla instruktioner i det här blocket även om körningen inte har varit avancerad efter den tidpunkt då de har definierats. Om du till exempel definierar en i `trap` slutet av ett skript och utlöser ett fel i den första instruktionen utlöses fortfarande `trap` .

### <a name="trapping-specific-errors"></a>Trap-vissa fel

Ett skript eller kommando kan ha flera `trap` instruktioner. En `trap` kan definieras för att hantera vissa fel.

Följande exempel är en `trap` instruktion som fäller in det angivna felet **CommandNotFoundException**:

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

När en funktion eller ett skript påträffar en sträng som inte matchar ett känt kommando, visar den här `trap` instruktionen strängen "kommando fel som fångats".
När du `trap` har kört instruktions listan skriver PowerShell felobjektet till fel strömmen och fortsätter sedan med skriptet.

PowerShell använder .NET-undantags typer. I följande exempel anges fel typen **system. Exception** :

```powershell
trap [System.Exception] {"An error trapped"}
```

Fel typen **CommandNotFoundException** ärver från **system. Exception** -typen. Den här instruktionen påfäller ett fel som skapats av ett okänt kommando. Den sväller också andra fel typer.

Du kan ha mer än en `trap` instruktion i ett skript. Varje typ av fel kan bara fångas av en `trap` instruktion. När ett avbrotts fel inträffar söker PowerShell efter den `trap` mest exakta matchningen med början i det aktuella körnings omfånget.

Följande skript exempel innehåller ett fel. Skriptet innehåller en allmän `trap` instruktion som avbryter eventuella avslutande fel och en speciell `trap` instruktion som anger typen av **CommandNotFoundException** .

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

Att köra det här skriptet ger följande resultat:

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Eftersom PowerShell inte känner igen "nonsenseString" som en cmdlet eller något annat objekt, returnerar den ett **CommandNotFoundException** -fel. Detta avslutande fel har fångats upp av den speciella `trap` instruktionen.

Följande skript exempel innehåller samma `trap` uttryck med ett annat fel:

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

Att köra det här skriptet ger följande resultat:

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

Försöket att dividera med noll skapar inte ett **CommandNotFoundException** -fel. I stället svälls det här felet av den andra `trap` instruktionen, vilket sväller eventuella avslutande fel.

### <a name="trapping-errors-and-scope"></a>Trap-fel och omfattning

Om ett avslutande fel inträffar i samma omfång som `trap` instruktionen kör PowerShell listan över instruktioner som definierats av `trap` . Körningen fortsätter vid instruktionen efter felet. Om `trap` instruktionen är i ett annat omfång från felet fortsätter körningen vid nästa instruktion som är i samma omfång som `trap` instruktionen.

Om ett fel exempelvis inträffar i en funktion och `trap` instruktionen är i funktionen, fortsätter skriptet vid nästa instruktion. Följande skript innehåller ett fel och en `trap` instruktion:

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

Att köra det här skriptet ger följande resultat:

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

`trap`Instruktionen i funktionen traps-felet. När meddelandet har visats fortsätter PowerShell att köra funktionen. Obs! `Function1` har slutförts.

Jämför detta med följande exempel, som har samma fel och `trap` instruktion. I det här exemplet `trap` inträffar instruktionen utanför funktionen:

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

Att köra `Function2` funktionen ger följande resultat:

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

I det här exemplet kördes inte kommandot "function2 har slutförts". I båda exemplen inträffar det avslutande felet i funktionen. I det här exemplet `trap` finns dock instruktionen utanför funktionen. PowerShell går inte tillbaka till funktionen när `trap` instruktionen har körts.

> [!CAUTION]
> När flera traps har definierats för samma fel villkor används den första `trap` definierade (högst i definitions området).

I följande exempel `trap` körs bara med "Whoops 1".

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> En trap-instruktion är begränsad till den plats där den kompileras. Om du har en `trap` instruktion inuti ett skript med en funktion eller ett punkts källa, `trap` tas alla instruktioner i bort när skriptet avslutas.

### <a name="using-the-break-and-continue-keywords"></a>Använda nyckelorden Break och Continue

Du kan använda `break` `continue` nyckelorden och i en- `trap` instruktion för att avgöra om ett skript eller kommando fortsätter att köras efter ett avslutande fel.

Om du inkluderar en `break` instruktion i en `trap` instruktions lista, stoppar PowerShell funktionen eller skriptet. Följande exempel funktion använder `break` nyckelordet i en `trap` instruktion:

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

Eftersom `trap` instruktionen innehöll `break` nyckelordet, fortsätter inte funktionen att köras och raden "funktion slutförd" körs inte.

Om du inkluderar ett `continue` nyckelord i en `trap` instruktion, återupptar PowerShell efter instruktionen som orsakade felet, precis som det skulle utan `break` eller `continue` . Med `continue` nyckelordet, skriver PowerShell dock inte ett fel till fel strömmen.

Följande exempel funktion använder `continue` nyckelordet i en `trap` instruktion:

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

Funktionen återupptas när felet har fångats och instruktionen "Function Completed" körs. Inget fel har skrivits till fel strömmen.

## <a name="notes"></a>Kommentarer

`trap` -instruktioner ger ett enkelt sätt att se till att alla avslutande fel i ett omfång hanteras. För mer detaljerad fel hantering använder du `try` / `catch` block där traps har definierats med hjälp av `catch` instruktioner. `catch`Instruktionerna gäller endast koden i den associerade `try` instruktionen. Mer information finns i [about_Try_Catch_Finally](about_Try_Catch_Finally.md).

## <a name="see-also"></a>Se även

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
