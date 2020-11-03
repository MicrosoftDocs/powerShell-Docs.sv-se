---
description: Förklarar hur du använder Split-operatorn för att dela upp en eller flera strängar i del strängar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: ed57cec30577fbd02f7aa317460bf1a73b006685
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269930"
---
# <a name="about-split"></a>Om delning

## <a name="short-description"></a>KORT BESKRIVNING
Förklarar hur du använder Split-operatorn för att dela upp en eller flera strängar i del strängar.

## <a name="long-description"></a>LÅNG BESKRIVNING

Operatorn Split delar en eller flera strängar i del strängar. Du kan ändra följande delar av delnings åtgärden:

- Avgränsare. Standardvärdet är blank steg, men du kan ange tecken, strängar, mönster eller skript block som anger avgränsaren. Operatorn Split i PowerShell använder ett reguljärt uttryck i avgränsaren i stället för ett enkelt tecken.
- Maximalt antal del strängar. Standardvärdet är att returnera alla del strängar. Om du anger ett tal som är mindre än antalet under strängar sammanfogas de återstående del strängarna i den sista del strängen.
- Alternativ som anger de villkor under vilka avgränsaren matchas, till exempel SimpleMatch och Multiline.

## <a name="syntax"></a>SYNTAX

Följande diagram visar syntaxen för operatorn-Split.

Parameter namnen visas inte i kommandot. Inkludera endast parameter värden. Värdena måste visas i den ordning som anges i syntax-diagrammet.

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

Du kan ersätta `-iSplit` eller `-cSplit` för `-split` i en binär delnings instruktion (en delad instruktion som innehåller en avgränsare eller ett skript block). `-iSplit` `-split` Operatorerna och är inte Skift läges känsliga. `-cSplit`Operatorn är Skift läges känslig, vilket innebär att ärendet beaktas när reglerna för avgränsare används.

## <a name="parameters"></a>PARAMETRAR

### <a name="string-or-string"></a>\<String\> eller \<String[]\>

Anger en eller flera strängar som ska delas upp. Om du skickar flera strängar delas alla strängar med samma regler för avgränsare.

Exempel:

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

De tecken som identifierar slutet av en under sträng. Standard avgränsaren är blank steg, inklusive blank steg och tecken som inte kan skrivas ut, till exempel ny rad matning ( \` n) och TABB ( \` t). När strängarna delas, utelämnas avgränsaren från alla del strängar. Exempel:

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

Som standard utelämnas avgränsaren från resultaten. Om du vill bevara hela eller delar av avgränsaren omger du den del som du vill behålla.
Om \<Max-substrings\> parametern läggs till, prioriteras det när kommandot delar upp samlingen. Om du väljer att ta med en avgränsare som en del av utdata returnerar kommandot avgränsaren som en del av utdata. men att dela strängen för att returnera avgränsaren som en del av utdata räknas inte som en delning.

Exempel:

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

I följande exempel \<Max-substrings\> är värdet 3. Detta resulterar i tre delar av sträng värden, men totalt fem strängar i resultatet. avgränsaren ingår efter delningarna tills det maximala antalet under strängar har nåtts. Ytterligare avgränsare i den sista del strängen blir del av under strängen.

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

Anger det maximala antalet gånger som en sträng är delad. Standardvärdet är alla del strängar som delas av avgränsaren. Om det finns fler del strängar sammanfogas de till den slutliga del strängen. Om det finns färre del strängar returneras alla del strängar. Värdet 0 returnerar alla del strängar. Negativa värden returnerar mängden del strängar som begärs från slutet av Indatasträngen.

> [!NOTE]
> Stöd för negativa värden har lagts till i PowerShell 7.

**Max-delsträngar** anger inte det maximala antalet objekt som returneras. Värdet är lika med det maximala antalet gånger som en sträng är delad.
Om du skickar mer än en sträng (en sträng mat ris) till `-split` operatorn, används **Max-substring-** gränsen på varje sträng separat.

Exempel:

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

Ett uttryck som anger regler för att tillämpa avgränsaren. Uttrycket måste utvärderas till $true eller $false. Omge skript blocket med klammerparenteser.

Exempel:

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

Omge alternativets namn inom citat tecken. Alternativen är endast giltiga när \<Max-substrings\> parametern används i instruktionen.

Syntaxen för parametern options är:

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

Alternativen för SimpleMatch är:

- **SimpleMatch** : Använd enkel sträng jämförelse när du utvärderar avgränsaren. Kan inte användas med RegexMatch.
- **IgnoreCase** : tvingar Skift läges okänslig matchning, även om operatorn-cSplit har angetts.

Alternativen för RegexMatch är:

- **RegexMatch** : Använd reguljär uttrycks matchning för att utvärdera avgränsaren. Det här är standardbeteendet. Kan inte användas med SimpleMatch.
- **IgnoreCase** : tvingar Skift läges okänslig matchning, även om operatorn-cSplit har angetts.
- **CultureInvariant** : ignorerar kultur skillnader i språk när evaluting avgränsaren. Endast giltig med RegexMatch.
- **IgnorePatternWhitespace** : ignorerar ej Escaped blank steg och kommentarer som marker ATS med nummer tecknet (#). Endast giltig med RegexMatch.
- Flera **rader** : Multiline-läge tvingar fram `^` och `$` matchar början av varje rad i stället för början och slutet av Indatasträngen.
- **Singleline** : Singleline mode behandlar Indatasträngen som en *Singleline*.
  Det tvingar `.` tecknet att matcha varje Character (inklusive newlines), i stället för att matcha alla bokstäver förutom rad matningen `\n` .
- **ExplicitCapture** : ignorerar matchnings grupper som inte är namngivna så att endast explicita infångnings grupper returneras i resultat listan. Endast giltig med RegexMatch.

## <a name="unary-and-binary-split-operators"></a>UNÄRA och binära delade OPERATORer

Den unära delnings operatorn ( `-split <string>` ) har högre prioritet än ett kommatecken. Det innebär att om du skickar en kommaavgränsad lista med strängar till den unära delnings operatorn, är det bara den första strängen (före det första kommatecknet) som delas.

Använd något av följande mönster för att dela fler än en sträng:

- Använd den binära delnings operatorn ( \<string[]\> -Split \<delimiter\> )
- Omslut alla strängar inom parentes
- Lagra strängarna i en variabel och skicka sedan variabeln till operatorn Split

Se följande exempel:

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a>EXEMPEL

Följande instruktion delar upp strängen vid blank steg.

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

Följande instruktion delar upp strängen vid valfritt kommatecken.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

Följande instruktion delar upp strängen i mönstret "er".

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

Följande instruktion utför en Skift läges känslig delning vid bokstaven "N".

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

Följande instruktion delar upp strängen i "e" och "t".

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

Följande instruktion delar upp strängen i "e" och "r", men begränsar de resulterande del strängarna till sex del strängar.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

Följande instruktion delar upp en sträng i tre del strängar.

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

Följande instruktion delar upp en sträng i tre del strängar som börjar från slutet av strängen.

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

Följande instruktion delar upp två strängar i tre del strängar.
(Gränsen tillämpas på varje sträng oberoende av varandra.)

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

Följande instruktion delar upp varje rad i den här-strängen vid den första siffran. Alternativet för flera rader används för att identifiera början av varje rad och sträng.

0 representerar värdet "returnera alla" för parametern för max-under strängar. Du kan använda alternativ, till exempel flera rader, endast när värdet för max-under strängar har angetts.

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

I följande instruktion används omvänt snedstreck för att undvika punkt (.)-avgränsaren.

Med standardvärdet, RegexMatch, kommer punkten inom citat tecken (".") att tolkas för att matcha alla tecken utom ett rad matnings tecken. Därför returnerar delnings instruktionen en tom rad för varje tecken förutom ny rad.

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

I följande instruktion används alternativet SimpleMatch för att dirigera operatorn-Split för att tolka punkt (.)-avgränsaren.

0 representerar värdet "returnera alla" för parametern för max-under strängar. Du kan använda alternativ, till exempel SimpleMatch, endast när värdet för max-under strängar har angetts.

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

Följande instruktion delar upp strängen på en av två avgränsare, beroende på värdet för en variabel.

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a>SE ÄVEN

[Dela-sökväg](xref:Microsoft.PowerShell.Management.Split-Path)

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Join](about_Join.md)
