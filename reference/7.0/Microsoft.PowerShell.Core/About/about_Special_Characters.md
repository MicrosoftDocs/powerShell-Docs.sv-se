---
description: Beskriver de teckenkombinationer som styr hur PowerShell tolkar nästa tecken i sekvensen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 5da2cf411519f2bd51296cd4311a607198a5ca6d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269960"
---
# <a name="about-special-characters"></a>Om specialtecken

## <a name="short-description"></a>Kort beskrivning

Beskriver de teckenkombinationer som styr hur PowerShell tolkar nästa tecken i sekvensen.

## <a name="long-description"></a>Lång beskrivning

PowerShell stöder en uppsättning specialtecken som används för att representera tecken som inte ingår i standard teckenuppsättningen. Sekvenserarna kallas ofta _escape-sekvenser_.

Escape-sekvenser börjar med snedstrecket, som kallas grav accent (ASCII 96) och är Skift läges känsliga. Det kan också kallas _escape-tecken_.

Escape-sekvenser tolkas bara när de finns i strängar med dubbla citat tecken ( `"` ).

PowerShell känner igen följande escape-sekvenser:

|  Sequence   |       Beskrivning       |
| ----------- | ----------------------- |
| `` `0 ``    | Null                    |
| `` `a ``    | Varning                   |
| `` `b ``    | Backsteg               |
| `` `e ``    | Escape                  |
| `` `f ``    | Formulär inmatning               |
| `` `n ``    | Ny rad                |
| `` `r ``    | Vagn retur         |
| `` `t ``    | Vågrät TABB          |
| `` `u{x} `` | Escape-sekvens för Unicode |
| `` `v ``    | Lodrät TABB            |

PowerShell har också en speciell token för att markera var du vill att parsningen ska stoppas. Alla tecken som följer denna token används som litterala värden som inte tolkas.

Särskild tolknings-token:

| Sequence |            Beskrivning             |
| -------- | ---------------------------------- |
| `--%`    | Sluta parsa något som följer |

## <a name="null-0"></a>Null (' 0)

Null- `` `0 `` tecken () visas som ett tomt utrymme i PowerShell-utdata.
Med den här funktionen kan du använda PowerShell för att läsa och bearbeta textfiler som använder null-tecken, t. ex. sträng avslutning eller post avslutnings indikatorer. Det särskilda null-värdet är inte detsamma som `$null` variabeln som lagrar ett **Null** -värde.

## <a name="alert-a"></a>Varning (' a)

Varning ( `` `a `` )-symbolen skickar en signal signal till datorns högtalare.
Du kan använda det här alternativet för att varna en användare om en förestående åtgärd. I följande exempel skickas två pip signaler till den lokala datorns högtalare.

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a>Backsteg (' b)

Tecknet Backsteg ( `` `b `` ) flyttar tillbaka markören ett tecken, men tar inte bort några tecken.

Exemplet skriver **säkerhets kopian** av ordet och flyttar sedan tillbaka markören två gånger.
Sedan skriver du ett blank steg följt av ordet **ut** på den nya platsen.

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a>Escape (' e)

Tecknet Escape ( `` `e `` ) används oftast för att ange en virtuell terminal-sekvens (ANSI escape-sekvens) som ändrar färgen på text och andra textattribut, till exempel fetstil och understrykning. Dessa sekvenser kan också användas för markör placering och rullning. PowerShell-värden måste ha stöd för virtuella Terminal-sekvenser. Du kan kontrol lera det booleska värdet för `$Host.UI.SupportsVirtualTerminal` för att avgöra om dessa ANSI-sekvenser stöds.

Mer information om ANSI escape-sekvenser finns [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).

I följande exempel matas texten med en grön förgrunds färg.

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a>Formulär flöde (' f)

Tecken formatet form ( `` `f `` ) är en utskrifts instruktion som matar ut den aktuella sidan och fortsätter att skriva ut på nästa sida. Formulärets matnings tecken påverkar endast utskrivna dokument. Det påverkar inte skärmens utdata.

## <a name="new-line-n"></a>Ny rad (' n)

Det nya Line ( `` `n `` )-symbolen infogar en rad brytning direkt efter specialtecknet.

Det här exemplet visar hur du använder det nya rad brytnings alternativet för att skapa rad brytningar i ett `Write-Host` kommando.

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a>Vagn retur (' r)

Tecken för vagn retur ( `` `r `` ) flyttar utmatnings markören till början av den aktuella raden och fortsätter skriva. Alla tecken på den aktuella raden skrivs över.

I det här exemplet skrivs texten före vagn returen över.

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

Observera att texten innan `` `r `` specialtecknet tas bort skrivs över.

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a>Vågrät TABB (ej)

Den vågräta tabben ( `` `t `` )-tecken går vidare till nästa tabbstopp och fortsätter att skriva vid den punkten. Som standard har PowerShell-konsolen ett tabbstopp med var åttonde plats.

I det här exemplet infogas två flikar mellan varje kolumn.

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a>Unicode-tecken (' u {x})

Med Unicode Escape Sequence ( `` `u{x} `` ) kan du ange valfritt Unicode-tecken genom den hexadecimala representationen av dess kod punkt. Detta inkluderar Unicode-tecken ovanför det grundläggande flerspråkiga planet (> `0xFFFF` ) som innehåller Emoji-tecken, till exempel tangenterna **tummen up** ( `` `u{1F44D} `` ). Unicode Escape-sekvensen kräver minst en hexadecimal siffra och har stöd för upp till sex hexadecimala siffror. Det maximala hexadecimala värdet för sekvensen är `10FFFF` .

I det här exemplet visas en **UPPIL** (&#x2195;) symbol.

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a>Lodrät TABB (' v)

Den vågräta tabben ( `` `v `` )-tecken går vidare till nästa lodräta TABB och skriver återstående utdata vid den punkten. Detta har ingen påverkan i standard konsolen för Windows.

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

I följande exempel visas de utdata som du skulle få på en skrivare eller en annan konsol värd.

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a>Stoppa-parsing-token (--%)

Token för Stop parsning ( `--%` ) förhindrar att PowerShell tolkar strängar som PowerShell-kommandon och uttryck. Detta gör att dessa strängar kan skickas till andra program för tolkning.

Placera token för att parsa efter program namn och före program argument som kan orsaka fel.

I det här exemplet `Icacls` använder kommandot Stop-parsing-token.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell skickar följande sträng till `Icacls` .

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

Här är ett annat exempel. Funktionen **showArgs** matar ut värdena som skickas till den. I det här exemplet skickar vi variabeln med namnet `$HOME` till funktionen två gånger.

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

Du kan se i utdata som för den första parametern `$HOME` tolkas variabeln av PowerShell så att värdet för variabeln skickas till funktionen. Den andra användningen av `$HOME` kommer efter att token för att tolkas, så strängen "$Home" skickas till funktionen utan tolkning.

```Output
$args = C:\Users\username|--%|$HOME
```

Mer information om stoppa-parsing-token finns [about_Parsing](about_Parsing.md).

## <a name="see-also"></a>Se även

[about_Quoting_Rules](about_Quoting_Rules.md)
