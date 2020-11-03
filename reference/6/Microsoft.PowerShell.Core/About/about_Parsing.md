---
description: Beskriver hur PowerShell tolkar kommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: 200a3aa7aac6477a2b2d3660167621132514c333
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270567"
---
# <a name="about-parsing"></a>Om parsning

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver hur PowerShell tolkar kommandon.

## <a name="long-description"></a>LÅNG BESKRIVNING

När du anger ett kommando i kommando tolken, avbryter PowerShell kommando texten till en serie segment som kallas _tokens_ och avgör sedan hur varje token ska tolkas.

Om du till exempel skriver:

```powershell
Write-Host book
```

PowerShell delar upp kommandot i två tokens `Write-Host` och `book` tolkar varje token oberoende av varandra med ett av två huvud tolknings lägen: uttrycks läge och argument läge.

> [!NOTE]
> Som PowerShell parsar kommando inmatat det försöker matcha kommando namn med cmdletar eller interna körbara filer. Om ett kommando namn inte har en exakt matchning, är PowerShell-prepends `Get-` till kommandot som standardverb. Till exempel tolkar PowerShell `Process` som `Get-Process` . Vi rekommenderar inte att du använder den här funktionen av följande orsaker:
>
> - Det är ineffektivt. Detta gör att PowerShell söker flera gånger.
> - Externa program med samma namn löses först, så du kan inte köra avsedd cmdlet.
> - `Get-Help` och `Get-Command` känner inte igen verb-mindre namn.

### <a name="expression-mode"></a>Uttrycks läge

Uttrycks läget är avsett för att kombinera uttryck som krävs för värde manipulation i ett skript språk. Uttryck är representationer av värden i PowerShell-syntax och kan vara enkla eller sammansatta, till exempel:

Literala uttryck är direkt representationer av deras värden: 

```powershell
'hello', 32
```

Variabel uttryck bär värdet för variabeln som de refererar till: 

```powershell
$x, $script:path
```
Operatorer kombinerar andra uttryck för utvärdering: 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- _Tecken Strängs litteraler_ måste finnas inom citat tecken.
- _Siffror_ behandlas som numeriska värden i stället för en serie med tecken (om inte escapeas).
- _Operatorer_ , inklusive unära operatorer som `-` och `-not` binära operatorer som `+` och `-gt` , tolkas som operatorer och tillämpar deras respektive åtgärder på argumenten (operander).
- _Attribut och konverterings uttryck_ tolkas som uttryck och tillämpas på underordnade uttryck, t. ex. `[int] '7'` .
- _Variabel referenser_ utvärderas till sina värden, men _ihopbuntning_ (d.v.s. inklistring av förifyllda parameter uppsättningar) är förbjuden och orsakar ett parsningsfel.
- Allt annat kommer att behandlas som ett kommando som ska anropas.

### <a name="argument-mode"></a>Argument läge

Vid parsningen ser PowerShell först till att tolka inmatade som ett uttryck. Men när ett kommando anrop påträffas fortsätter parsningen i argument läge.

Argument läget är utformat för att parsa argument och parametrar för kommandon i en gränssnitts miljö. Alla inmatade värden behandlas som en expanderbar sträng om den inte använder någon av följande syntaxer:

- Dollar tecken ( `$` ) startar en variabel referens (endast om det följs av ett giltigt variabel namn, annars tolkas det som en del av den expanderbara strängen).
- Citat tecken ( `'` och `"` ) inleder sträng värden
- Parenteser ( `(` och `)` ) avgränsning av nya uttryck.
- Operatorn för under uttryck ( `$(` ... `)` ) avgränsnings av inbäddade uttryck.
- Klammerparenteser ( `{` och `}` ) avgränsning av nya skript block.
- Initialt vid inloggning ( `@` ) börjar uttrycks syntaxer som ihopbuntning ( `@args` ), matriser ( `@(1,2,3)` ) och hash-tabeller ( `@{a=1;b=2}` ).
- Kommatecken ( `,` ) introducera listor som skickats som matriser, förutom när kommandot som ska anropas är ett internt program, i vilket fall de tolkas som en del av den expanderbara strängen. Inledande, efterföljande eller efterföljande kommatecken stöds inte.

Värdena för inbäddade uttryck konverteras till strängar.

Följande tabell innehåller flera exempel på värden som bearbetas i uttrycks läge och argument läge och utvärderingen av dessa värden. Vi antar att värdet för variabeln `a` är `4` .

|       Exempel        |    Läge    |      Resultat       |
| -------------------- | ---------- | ----------------- |
| `2`                  | Uttryck | 2 (heltal)       |
| `` `2``              | Uttryck | "2" (kommando)     |
| `echo 2`             | Uttryck | 2 (heltal)       |
| `2+2`                | Uttryck | 4 (heltal)       |
| `echo 2+2`           | Argument   | "2 + 2" (sträng)    |
| `echo(2+2)`          | Uttryck | 4 (heltal)       |
| `$a`                 | Uttryck | 4 (heltal)       |
| `echo $a`            | Uttryck | 4 (heltal)       |
| `$a+2`               | Uttryck | 6 (heltal)       |
| `echo $a+2`          | Argument   | 4 + 2 (sträng)      |
| `$-`                 | Argument   | "$-" (kommando)    |
| `echo $-`            | Argument   | "$-" (sträng)     |
| `a$a`                | Uttryck | "a $ a" (kommando)   |
| `echo a$a`           | Argument   | "A4" (sträng)     |
| `a'$a'`              | Uttryck | "a $ a" (kommando)   |
| `echo a'$a'`         | Argument   | "a $ a" (sträng)    |
| `a"$a"`              | Uttryck | "a $ a" (kommando)   |
| `echo a"$a"`         | Argument   | "A4" (sträng)     |
| `a$(2)`              | Uttryck | "a $ (2)" (kommando) |
| `echo a$(2)`         | Argument   | "a2" (sträng)     |

Varje token kan tolkas som en typ av objekt typ, till exempel Boolean eller String. PowerShell försöker fastställa objekt typen från uttrycket.
Objekt typen beror på vilken typ av parameter ett kommando förväntar sig och på om PowerShell vet hur argumentet ska konverteras till rätt typ. I följande tabell visas flera exempel på de typer som tilldelats värden som returneras av uttrycken.

|       Exempel          |    Läge    |     Resultat      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | -argument   | "! 1" (sträng)   |
| `Write-Output (!1)`    | uttryck | Falskt (boolesk) |
| `Write-Output (2)`     | uttryck | 2 (heltal)     |
| `Set-Variable AB A,B`  | -argument   | "A", "B" (matris) |
| `CMD /CECHO A,B`       | -argument   | "A, B" (sträng)  |
| `CMD /CECHO $AB`       | uttryck | "A", "B" (matris) |
| `CMD /CECHO :$AB`      | -argument   | ': A B ' (sträng) |

Med stop parser-symbolen ( `--%` ) som introducerades i powershell 3,0, använder PowerShell för att undvika att tolka ininformation som PowerShell-kommandon eller uttryck.

När du anropar ett körbart program i PowerShell ska du placera stop-parser-symbolen före program argumenten. Den här metoden är mycket enklare än att använda escape-tecken för att förhindra feltolkning.

När den påträffar en stopp tolknings symbol behandlar PowerShell de återstående tecknen på raden som en litteral. Den enda tolkning som det utför är att ersätta värden för miljövariabler som använder standard Windows-notation, t `%USERPROFILE%` . ex..

Den avparsande symbolen börjar bara gälla fram till nästa rad matning eller pipeline-tecken. Du kan inte använda ett fortsättnings tecken ( `` ` `` ) för att utöka dess inverkan eller använda en kommando avgränsare ( `;` ) för att avsluta dess funktion.

Till exempel anropar följande kommando **icacls** -programmet.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

Om du vill köra det här kommandot i PowerShell 2,0 måste du använda escape-tecken för att förhindra att PowerShell tolkar en parentes.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

Från och med PowerShell 3,0 kan du använda Stop-parser-symbolen.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell skickar följande kommando sträng till **icacls** -programmet:

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> Avtolknings symbolen är endast avsedd för användning på Windows-plattformar.

## <a name="see-also"></a>SE ÄVEN

[about_Command_Syntax](about_Command_Syntax.md)
