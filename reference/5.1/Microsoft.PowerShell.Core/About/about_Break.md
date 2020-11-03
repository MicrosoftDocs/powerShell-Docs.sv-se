---
description: Beskriver ett uttryck som du kan använda för att omedelbart avsluta,,,, `foreach` `for` `while` `do` `switch` eller- `trap` instruktioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: a50b98c1ec816658d353173eee9743c49e25c2a4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271634"
---
# <a name="about-break"></a>Om avbrott

## <a name="short-description"></a>Kort beskrivning

Beskriver ett uttryck som du kan använda för att omedelbart avsluta,,,, `foreach` `for` `while` `do` `switch` eller- `trap` instruktioner.

## <a name="long-description"></a>Lång beskrivning

`break`Instruktionen gör det möjligt att avsluta det aktuella kontroll blocket.
Körningen fortsätter vid nästa instruktion efter kontroll blocket. Instruktionen stöder etiketter. En etikett är ett namn som du tilldelar till en instruktion i ett skript.

## <a name="using-break-in-loops"></a>Använda avbrott i slingor

När en `break` instruktion visas i en slinga, till exempel en `foreach` , `for` , `do` eller `while` loop, avslutar PowerShell omedelbart loopen.

En `break` instruktion kan innehålla en etikett som låter dig avsluta inbäddade slingor. En etikett kan ange valfritt loop-nyckelord, till exempel, `foreach` `for` eller `while` , i ett skript.

Följande exempel visar hur du använder en `break` instruktion för att avsluta en `for` instruktion:

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

I det här exemplet `break` avslutar instruktionen `for` loopen när `$i` variabeln är lika med 1. Även om `for` instruktionen utvärderas till **True** tills `$i` är större än 10, kommer PowerShell att nå break-instruktionen första `for` gången slingan körs.

Det är vanligare att använda `break` instruktionen i en slinga där ett inre villkor måste uppfyllas. Tänk på följande `foreach` exempel:

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

I det här exemplet `foreach` upprepar instruktionen `$varB` matrisen. `if`Instruktionen utvärderar till falskt de första två gånger som loopen körs och variabeln `$i` ökas med 1. Den tredje gången slingan körs, `$i` är lika med 2 och `$val` variabeln är lika med 30. Nu `break` körs instruktionen och `foreach` loopen avslutas.

### <a name="using-a-labeled-break-in-a-loop"></a>Använda en etikettad rast i en slinga

En `break` instruktion kan innehålla en etikett. Om du använder `break` nyckelordet med en etikett, avslutar PowerShell den märkta loopen i stället för att avsluta den aktuella slingan.
Etiketten är ett kolon följt av ett namn som du tilldelar. Etiketten måste vara den första token i en instruktion, och den måste följas av nyckelordet loop, till exempel `while` .

`break` flyttar körningen från den märkta slingan. I inbäddade slingor har detta ett annat resultat än `break` nyckelordet när det används av sig självt. Det här exemplet har en `while` instruktion med en `for` instruktion:

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

Om villkoret 2 utvärderas till **Sant** , hoppar körningen av skriptet ned till instruktionen efter den märkta loopen. I exemplet börjar körningen igen med instruktionen `$a = $c` .

Du kan kapsla många etiketterade slingor, som du ser i följande exempel.

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

Om `$b` variabeln utvärderas till True återupptas körningen av skriptet efter loopen med etiketten "Red". Om `$c` variabeln utvärderas till True återupptas körningen av skript kontrollen efter loopen med etiketten "gul".

Om `$a` variabeln utvärderas till True återupptas körningen efter den innersta slingan. Ingen etikett krävs.

PowerShell begränsar inte hur långt etiketter kan återuppta körningen. Etiketten kan till och med överföra kontroll över skript-och funktions anrops gränser.

## <a name="using-break-in-a-switch-statement"></a>Använda Break i en switch-instruktion

I en `switch` konstruktion kommer `break` PowerShell att avsluta `switch` kod blocket.

`break`Nyckelordet används för att lämna `switch` konstruktionen. Till exempel använder följande uttryck `switch` `break` för att testa för det mest aktuella villkoret:

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

I det här exemplet `$var` skapas variabeln och initieras till ett sträng värde för `word2` . `switch`Instruktionen använder **regex** -klassen för att matcha variabelns värde först med termen `word2` . Eftersom variabelvärdet och det första testet i `switch` instruktionen matchar, körs det första kod blocket i `switch` instruktionen.

När PowerShell når den första `break` instruktionen `switch` avslutas instruktionen. Om de fyra `break` satserna tas bort från exemplet är alla fyra villkor uppfyllda. I det här exemplet används `break` instruktionen för att visa resultaten när det mest aktuella villkoret är uppfyllt.

## <a name="using-break-in-a-trap-statement"></a>Använda Break i en trap-instruktion

Om den slutliga instruktionen som körs i bröd texten i en `trap` instruktion är `break` , ignoreras felobjektet och undantags felet återskapas.

I följande exempel skapas ett **DivideByZeroException** -undantag som fångas med `trap` instruktionen.

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

Observera att körningen stoppas vid undantag. `After loop`Nås aldrig.
Undantaget återskapas efter `trap` körningen.

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
Attempted to divide by zero.
At line:10 char:6
+      "1 / $i = " + (1 / $i--)
+      ~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RuntimeException
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a>Använd inte Break utanför en slinga, switch eller trap

När `break` används utanför en konstruktion som stöder den direkt (loopar, `switch` , `trap` ), letar PowerShell _upp anrops stacken_ för en omsluten konstruktion. Om det inte går att hitta en omsluten konstruktion avslutas den aktuella körnings utrymme tyst.

Det innebär att funktioner och skript som oavsiktligt använder en `break` utanför en omsluten konstruktion som stöder det kan oavsiktligt avsluta sina _anropare_.

Om du använder `break` inuti en pipeline `break` , t. ex. ett `ForEach-Object` skript block, avslutar inte bara pipelinen, utan kan avsluta hela körnings utrymme.

## <a name="see-also"></a>Se även

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Continue](about_Continue.md)

[about_For](about_For.md)

[about_Foreach](about_Foreach.md)

[about_Switch](about_Switch.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

[about_While](about_While.md)
