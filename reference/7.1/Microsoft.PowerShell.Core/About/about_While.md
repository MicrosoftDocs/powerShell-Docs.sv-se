---
description: Beskriver en språk instruktion som du kan använda för att köra ett kommando block baserat på resultatet av ett villkorligt test.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 60b944d3f09db786b54a1c7afb685543de808a92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272307"
---
# <a name="about-while"></a>Om medan

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver en språk instruktion som du kan använda för att köra ett kommando block baserat på resultatet av ett villkorligt test.

## <a name="long-description"></a>LÅNG BESKRIVNING

While-instruktionen (kallas även en while-loop) är en språk konstruktion för att skapa en loop som kör kommandon i ett kommando block så länge ett villkorligt test utvärderas till true. While-instruktionen är enklare att konstruera än en for-instruktion eftersom dess syntax är mindre komplicerad. Dessutom är det mer flexibelt än den förskotts instruktionen eftersom du anger ett villkorsstyrt test i while-instruktionen för att styra hur många gånger slingan körs.

Följande visar syntaxen för while-uttrycket:

```powershell
while (<condition>){<statement list>}
```

När du kör en while-instruktion utvärderar PowerShell `<condition>` avsnittet i instruktionen innan du anger `<statement list>` avsnittet. Villkors delen i instruktionen matchar antingen sant eller falskt. Så länge villkoret är sant, kör PowerShell avsnittet igen `<statement list>` .

`<statement list>`Avsnittet i instruktionen innehåller ett eller flera kommandon som körs varje gången loopen anges eller upprepas.

Till exempel visar följande while-uttryck talen 1 till 3 om variabeln $val inte har skapats eller om $val-variabeln har skapats och initierats till 0.

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

I det här exemplet är villkoret ($val inte lika med 3) sant när $val \= 0, 1, 2. Varje gången genom loopen ökas $val med 1 med hjälp av den \+ \+ unära öknings operatorn ($val \+ \+ ). Sista gången genom loopen $val \= 3. När $val är lika med 3, utvärderas villkors uttrycket till false och loopen avslutas.

Om du vill skriva detta kommando i PowerShell-kommandotolken kan du ange det på följande sätt:

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

Observera att semikolonet separerar det första kommandot som lägger till 1 $val från det andra kommandot som skriver värdet för $val till-konsolen.

## <a name="see-also"></a>SE ÄVEN

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Do](about_Do.md)

[about_Foreach](about_Foreach.md)

[about_For](about_For.md)

[about_Language_Keywords](about_Language_Keywords.md)

