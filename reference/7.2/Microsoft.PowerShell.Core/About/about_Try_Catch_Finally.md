---
description: Beskriver hur du använder `Try` , `Catch` och `Finally` blockerar för att hantera avslutande fel.
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709235"
---
# <a name="about-try-catch-finally"></a>Om try catch finally

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du använder `Try` , `Catch` och `Finally` blockerar för att hantera avslutande fel.

## <a name="long-description"></a>LÅNG BESKRIVNING

Använd `Try` , `Catch` och `Finally` blockerar för att svara på eller hantera avslutande fel i skript. `Trap`Instruktionen kan också användas för att hantera avslutande fel i skript. Mer information finns i [about_Trap](about_Trap.md).

Ett avslutande fel stoppar en instruktion som körs. Om PowerShell inte hanterar ett avbrotts fel på något sätt slutar PowerShell också att köra funktionen eller skriptet med den aktuella pipelinen. På andra språk, t. ex. C \# , kallas att avsluta fel som undantag.

Använd `Try` blocket för att definiera ett avsnitt i ett skript där du vill att PowerShell ska övervakas för fel. När ett fel uppstår i `Try` blocket sparas felet först i den `$Error` automatiska variabeln. PowerShell söker sedan efter ett `Catch` block för att hantera felet. Om `Try` instruktionen inte har något matchande `Catch` block fortsätter PowerShell att söka efter ett lämpligt `Catch` block eller `Trap` en instruktion i de överordnade omfången. När ett `Catch` block har slutförts eller om det inte finns något lämpligt `Catch` block eller en `Trap` instruktion, `Finally` körs blocket. Om felet inte kan hanteras skrivs felet till fel strömmen.

Ett `Catch` block kan innehålla kommandon för att spåra felet eller för att återskapa det förväntade flödet i skriptet. Ett `Catch` block kan ange vilka fel typer den fångar upp. En `Try` instruktion kan innehålla flera `Catch` block för olika typer av fel.

Ett `Finally` block kan användas för att frigöra de resurser som inte längre behövs i skriptet.

`Try`, `Catch` , och `Finally` liknar `Try` `Catch` nyckelorden, och `Finally` som används i programmeringsspråket C \# .

### <a name="syntax"></a>SYNTAX

En `Try` instruktion innehåller ett `Try` block, noll eller flera `Catch` block och inget eller ett `Finally` block. En `Try` instruktion måste innehålla minst ett `Catch` block eller ett `Finally` block.

Följande visar `Try` syntaxen för blockering:

```powershell
try {<statement list>}
```

`Try`Nyckelordet följs av en instruktions lista inom klammerparenteser. Om ett avslutande fel inträffar när instruktionerna i instruktions listan körs, skickar skriptet felobjektet från `Try` blocket till ett lämpligt `Catch` block.

Följande visar `Catch` syntaxen för blockering:

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

Fel typer visas inom hak paren tes. De yttersta hakparenteserna anger att elementet är valfritt.

`Catch`Nyckelordet följs av en valfri lista med fel typs specifikationer och en instruktions lista. Om ett avslutande fel inträffar i `Try` blocket söker PowerShell efter ett lämpligt `Catch` block. Om det finns en sådan sådan körs instruktionerna i `Catch` blocket.

`Catch`Blocket kan ange en eller flera fel typer. En typ av fel är ett Microsoft .NET Framework-undantag eller ett undantag som härleds från ett .NET Framework undantag. Ett `Catch` block hanterar fel i den angivna .NET Framework undantags klassen eller klasser som härleds från den angivna klassen.

Om ett `Catch` block anger en typ av fel, `Catch` hanterar blocket den typen av fel. Om ett `Catch` block inte anger någon typ av fel, `Catch` hanterar blocket ett fel som påträffas i `Try` blocket. En `Try` instruktion kan innehålla flera `Catch` block för de olika angivna fel typerna.

Följande visar `Finally` syntaxen för blockering:

```powershell
finally {<statement list>}
```

`Finally`Nyckelordet följs av en instruktions lista som körs varje gång skriptet körs, även om `Try` instruktionen kördes utan fel eller om ett fel har uppstått i en `Catch` instruktion.

Observera att genom att trycka på <kbd>CTRL</kbd> + <kbd>C</kbd> stoppas pipelinen. Objekt som skickas till pipelinen visas inte som utdata. Om du lägger till en instruktion som ska visas, t. ex. "finally block" har körts, visas det inte när du har tryckt på <kbd>CTRL</kbd> + <kbd>C</kbd>, även om `Finally` blocket kördes.

### <a name="catching-errors"></a>FÅNGA FEL

Följande exempel skript visar ett `Try` block med ett `Catch` block:

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

`Catch`Nyckelordet måste omedelbart följa `Try` blocket eller ett annat `Catch` block.

PowerShell känner inte igen "NonsenseString" som en cmdlet eller något annat objekt.
När skriptet körs returneras följande resultat:

```powershell
An error occurred.
```

När skriptet påträffar "NonsenseString" orsakar det ett avslutande fel meddelande. `Catch`Blocket hanterar felet genom att köra instruktions listan inuti blocket.

### <a name="using-multiple-catch-statements"></a>ANVÄNDA FLERA CATCH-INSTRUKTIONER

En `Try` instruktion kan ha valfritt antal `Catch` block. Följande skript har till exempel ett `Try` block som laddas ned `MyDoc.doc` och innehåller två `Catch` block:

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

Det första `Catch` blocket hanterar fel i typerna **system .net. WebException** och **system. io. IOException** . Det andra `Catch` blocket anger ingen feltyp. Det andra `Catch` blocket hanterar alla andra avslutande fel som inträffar.

PowerShell matchar fel typer genom arv. Ett `Catch` block hanterar fel i den angivna .NET Framework undantags klassen eller klasser som härleds från den angivna klassen. Följande exempel innehåller ett `Catch` block som fångar fel meddelandet "kommandot hittades inte":

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

Den angivna feltypen, **CommandNotFoundException**, ärver från **System.SystemException** -typen. Följande exempel fångar också upp ett kommando som inte hittas:

```powershell
catch [System.SystemException] {"Base Exception" }
```

Det här `Catch` blocket hanterar felet "kommandot hittades inte" och andra fel som ärver från **SystemException** -typen.

Om du anger en felklass och en av dess härledda klasser, placerar du `Catch` blocket för den härledda klassen före `Catch` blocket för den allmänna klassen.

### <a name="using-traps-in-a-try-catch"></a>Använda traps i en try-catch

När ett avbrotts fel inträffar i ett `Try` block med en `Trap` definierad i `Try` blocket, även om det finns ett matchande `Catch` block, `Trap` tar instruktionen kontroll.

Om det `Trap` finns ett högre block än `Try` , och det inte finns något matchande `Catch` block inom det aktuella omfånget, `Trap` kommer kontrollen att ta kontroll, även om ett överordnat omfång har ett matchande `Catch` block.

### <a name="accessing-exception-information"></a>ÅTKOMST TILL UNDANTAGS INFORMATION

I ett `Catch` block kan du komma åt det aktuella felet med `$_` , vilket även kallas `$PSItem` . Objektet är av typen **ErrorRecord**.

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

När skriptet körs returneras följande resultat:

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

Det finns ytterligare egenskaper som kan nås, till exempel **ScriptStackTrace**, **undantag** och **ErrorDetails**.  Om vi till exempel ändrar skriptet till följande:

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

Resultatet ser ut ungefär så här:

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a>FRIGÖRA RESURSER MED FINALLY

Om du vill frigöra resurser som används av ett skript lägger du till ett `Finally` block efter- `Try` och- `Catch` blocken. `Finally`Block satserna körs oavsett om `Try` blocket påträffar ett avslutande fel. PowerShell kör `Finally` blocket innan skriptet avslutas eller innan det aktuella blocket hamnar utanför omfånget.

Ett `Finally` block körs även om du använder <kbd>CTRL</kbd> + <kbd>C</kbd> för att stoppa skriptet. Ett `Finally` block körs också om ett avslutnings nyckelord stoppar skriptet inifrån ett `Catch` block.

### <a name="see-also"></a>SE ÄVEN

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

