---
description: Beskriver ett språk kommando som du kan använda för att köra instruktioner som baseras på ett villkorligt test.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 07037b73a5507bb0ef420ad39271be8832f7500b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270213"
---
# <a name="about-for"></a>Om för

## <a name="short-description"></a>Kort beskrivning
Beskriver ett språk kommando som du kan använda för att köra instruktioner som baseras på ett villkorligt test.

## <a name="long-description"></a>Lång beskrivning

`For`Instruktionen (kallas även en `For` loop) är en språk konstruktion som du kan använda för att skapa en loop som kör kommandon i ett kommando block medan ett angivet villkor utvärderas till `$true` .

En typisk användning av `For` slingan är att iterera en matris med värden och att använda en delmängd av dessa värden. I de flesta fall bör du överväga att använda en instruktion om du vill iterera alla värden i en matris `Foreach` .

### <a name="syntax"></a>Syntax

Följande visar `For` syntaxen för uttrycket.

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

Plats hållaren **init** representerar ett eller flera kommandon som körs innan loopen börjar. Du använder vanligt vis **init** -delen av instruktionen för att skapa och initiera en variabel med ett start värde.

Den här variabeln kommer sedan att ligga till grund för villkoret som ska testas i nästa del av `For` instruktionen.

Plats hållaren för **villkor** representerar den del av `For` instruktionen som matchar ett `$true` eller `$false` **booleskt** värde. PowerShell utvärderar villkoret varje gången `For` slingen körs. Om instruktionen är körs `$true` kommandona i kommando blocket och instruktionen utvärderas igen. Om villkoret fortfarande är `$true` fallet körs kommandona i **instruktions listan** igen. Loopen upprepas tills villkoret blir `$false` .

Plats hållaren för **upprepning** representerar ett eller flera kommandon, avgränsade med kommatecken, som körs varje gången upprepningen upprepas. Detta används vanligt vis för att ändra en variabel som testas inuti **villkors** delen i instruktionen.

Plats hållaren för **instruktions listan** representerar en uppsättning av ett eller flera kommandon som körs varje gången loopen anges eller upprepas. Innehållet i **instruktions listan** omges av klammerparenteser.

### <a name="support-for-multiple-operations"></a>Stöd för flera åtgärder

Följande syntax stöds för flera tilldelnings åtgärder i **init** -instruktionen:

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

Följande syntax stöds för flera tilldelnings åtgärder i instruktionen **REPEAT** :

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> Andra åtgärder än före eller efter-steg kanske inte fungerar med alla syntaxer.

För flera **villkor** använder logiska operatorer som de visas i följande exempel.

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

Mer information finns i [about_Logical_Operators](about_Logical_Operators.md).

### <a name="examples"></a>Exempel

En instruktion kräver minst en `For` parentes som omger kommandot **init** , **condition** och **REPEAT** i instruktionen och ett kommando omgiven av klamrar i **instruktions List** delen av instruktionen.

Observera att de kommande exemplen avsiktligt visar kod utanför `For` instruktionen. I senare exempel integreras kod i `For` instruktionen.

Till exempel `For` visar följande instruktion hela tiden värdet för `$i` variabeln tills du avbryter kommandot manuellt genom att trycka på CTRL + C.

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

Du kan lägga till ytterligare kommandon i instruktions listan så att värdet i `$i` ökas med 1 varje gången loopen körs, som i följande exempel.

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

Tills du har slut på kommandot genom att trycka på CTRL + C visar den här instruktionen hela tiden värdet för `$i` variabeln som ökas med 1 varje gång slingan körs.

I stället för att ändra värdet för variabeln i instruktions List delen av `For` instruktionen kan du använda den **upprepande** delen av `For` instruktionen i stället, enligt följande.

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

Den här instruktionen upprepas fortfarande oändligt tills du delar ut kommandot genom att trycka på CTRL + C.

Du kan avsluta `For` loopen med ett *villkor*. Du kan placera ett villkor med hjälp av **villkors** delen i `For` instruktionen. `For`Loopen avslutas när villkoret utvärderas till `$false` .

I följande exempel `For` körs loopen medan värdet `$i` är mindre än eller lika med 10.

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

I stället för att skapa och initiera variabeln utanför `For` instruktionen kan du utföra den här uppgiften i `For` loopen med hjälp av instruktionens **init** -del `For` .

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

Du kan använda vagn returer i stället för semikolon för att avgränsa delarna **init** , **condition** och **REPEAT** i `For` instruktionen. I följande exempel visas en `For` som använder den här alternativa syntaxen.

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

Den här alternativa formen av `For` instruktionen fungerar i PowerShell-skriptfiler och i PowerShell-Kommandotolken. Men det är enklare att använda kommandot `For` Statement med semikolon när du anger interaktiva kommandon i kommando tolken.

`For`Loopen är mer flexibel än `Foreach` loopen eftersom du kan öka värdena i en matris eller samling med hjälp av mönster. I följande exempel `$i` ökas variabeln med 2 i **upprepnings** delen av `For` instruktionen.

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

`For`Slingan kan också skrivas på en rad som i följande exempel.

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a>SE ÄVEN

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Foreach](about_Foreach.md)

