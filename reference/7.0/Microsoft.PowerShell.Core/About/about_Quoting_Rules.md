---
description: Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 8e30640c74976ac79634f5f7f648aafc16977f31
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271826"
---
# <a name="about-quoting-rules"></a>Om citat regler

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Citat tecken används för att ange en tecken sträng. Du kan omge en sträng med enkla citat tecken ( `'` ) eller dubbla citat tecken ( `"` ).

Citat tecken används också för att skapa en här-sträng. En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen. En här-sträng kan sträcka sig över flera rader. Alla rader i en här-sträng tolkas som strängar, även om de inte omges av citat tecken.

I kommandon till fjärrdatorer definierar citat tecken de delar av kommandot som körs på fjärrdatorn. I en fjärran sluten session avgör citat tecken också om variablerna i ett kommando tolkas först på den lokala datorn eller på fjärrdatorn.

### <a name="single-and-double-quoted-strings"></a>STRÄNGAR MED ENKLA OCH DUBBLA CITAT TECKEN

När du omger en sträng med dubbla citat tecken (en dubbels omgiven sträng) ersätts variabel namn som föregås av ett dollar tecken ( `$` ) med variabelns värde innan strängen skickas till kommandot för bearbetning.

Ett exempel:

```powershell
$i = 5
"The value of $i is $i."
```

Utdata från det här kommandot är:

```Output
The value of 5 is 5.
```

Dessutom utvärderas uttryck i en dubbelt Citerad sträng och resultatet infogas i strängen. Ett exempel:

```powershell
"The value of $(2+3) is 5."
```

Utdata från det här kommandot är:

```Output
The value of 5 is 5.
```

När du omger en sträng med enkla citat tecken (en sträng med en citat tecken) skickas strängen till kommandot exakt när du skriver den. Ingen ersättning utförs. Ett exempel:

```powershell
$i = 5
'The value of $i is $i.'
```

Utdata från det här kommandot är:

```Output
The value $i is $i.
```

På samma sätt utvärderas inte uttryck i ensiffriga strängar. De tolkas som litteraler. Ett exempel:

```powershell
'The value of $(2+3) is 5.'
```

Utdata från det här kommandot är:

```Output
The value of $(2+3) is 5.
```

För att förhindra att ett variabel värde byts ut i en dubbel-Citerad sträng, använder du bakticket ( `` ` `` ) (ASCII 96), som är PowerShell-escape-tecken.

I följande exempel förhindrar det Baknings kort som föregår den första $i variabeln att PowerShell ersätter variabelns namn med värdet.
Ett exempel:

```powershell
$i = 5
"The value of `$i is $i."
```

Utdata från det här kommandot är:

```Output
The value $i is 5.
```

Om du vill att dubbla citat tecken ska visas i en sträng omger du hela strängen med enkla citat tecken. Ett exempel:

```powershell
'As they say, "live and learn."'
```

Utdata från det här kommandot är:

```Output
As they say, "live and learn."
```

Du kan också ange en ensiffrig sträng i en sträng med dubbla citat tecken. Ett exempel:

```powershell
"As they say, 'live and learn.'"
```

Utdata från det här kommandot är:

```Output
As they say, 'live and learn.'
```

Eller, dubbla citat tecknen runt en fras med dubbla citat tecken. Ett exempel:

```powershell
"As they say, ""live and learn."""
```

Utdata från det här kommandot är:

```Output
As they say, "live and learn."
```

Om du vill inkludera ett enkelt citat tecken i en enciterad sträng använder du ett andra sammanhängande citat tecken. Ett exempel:

```powershell
'don''t'
```

Utdata från det här kommandot är:

```Output
don't
```

Om du vill tvinga PowerShell att tolka dubbla citat tecken bokstavligen använder du ett Baknings tecken. Detta förhindrar att PowerShell tolkar citat tecknet som en sträng avgränsare. Ett exempel:

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

Eftersom innehållet i ensiffriga strängar tolkas bokstavligen, behandlas det som ett bokstavligt tecken och visas i utdata.

### <a name="here-strings"></a>HÄR – STRÄNGAR

Offert reglerna för här – strängarna är något annorlunda.

En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen. En här-sträng kan sträcka sig över flera rader. Alla rader i en här-sträng tolkas som strängar även om de inte omges av citat tecken.

Precis som med vanliga strängar ersätts variablerna med deras värden i dubbla citat tecken. I ensiffriga här – strängar ersätts inte variablerna med deras värden.

Du kan använda här – strängar för valfri text, men de är särskilt användbara för följande typer av text:

- Text som innehåller litterala citat tecken
- Flera rader med text, till exempel texten i en HTML-eller XML-fil
- Hjälp texten för ett skript eller funktions dokument

En här-sträng kan ha något av följande format, där `<Enter>` representerar rad matnings tecken eller sid matnings tecken som läggs till när du trycker på <kbd>RETUR</kbd> -tangenten.

Dubbla citat tecken:

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

Enkla citat tecken:

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

I båda formaten måste det avslutande citat tecknet vara det första tecknet på raden.

En här-sträng innehåller all text mellan de två dolda tecknen. I den här strängen tolkas alla citat tecken bokstavligen. Ett exempel:

```powershell
@"
For help, type "get-help"
"@
```

Utdata från det här kommandot är:

```Output
For help, type "get-help"
```

Om du använder en här-sträng kan du förenkla användningen av en sträng i ett kommando. Ett exempel:

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

Utdata från det här kommandot är:

```Output
Use a quotation mark (') to begin a string.
```

I ensiffriga här – strängar tolkas variablerna i bokstavligen och reproduceras exakt. Ett exempel:

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

Utdata från det här kommandot är:

```Output
The $profile variable contains the path
of your PowerShell profile.
```

I Double-citerade här – strängar ersätts variablerna med deras värden. Ett exempel:

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

Utdata från det här kommandot är:

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

Här – strängarna används vanligt vis för att tilldela flera rader till en variabel. Följande – sträng tilldelar till exempel en sida med XML till variabeln $page.

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

Här – strängarna är också ett bekvämt format för inmatade `ConvertFrom-StringData` cmdlet, som konverterar hit-strängar till hash-tabeller.
Mer information finns i `ConvertFrom-StringData`.

## <a name="see-also"></a>SE ÄVEN

[about_Special_Characters](about_Special_Characters.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
