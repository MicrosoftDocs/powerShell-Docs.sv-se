---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 890f8e92172f2d492b6b817b558d4f25c70e8949
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269936"
---
# <a name="psreadline"></a>PSReadLine

## <a name="about_psreadline"></a>about_PSReadLine

## <a name="short-description"></a>KORT BESKRIVNING

PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.

## <a name="long-description"></a>LÅNG BESKRIVNING

PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen. Den tillhandahåller:

- Syntax för kommando rads färg
- En visuell indikation på syntaxfel
- En bättre multi-line-upplevelse (både redigering och historik)
- Anpassningsbara nyckel bindningar
- Cmd-och emacs-lägen
- Många konfigurations alternativ
- Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)
- Emacs YANK/Kill-ring
- PowerShell-token-baserad "Word"-förflyttning och stopp

Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.

> [!NOTE]
> Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats. PSReadLine fungerar för närvarande inte bra med skärm läsare. Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt. Du kan läsa in modulen manuellt om det behövs.

## <a name="basic-editing-functions"></a>Grundläggande redigerings funktioner

### <a name="abort"></a>Avbryta

Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.

- Emacs: `<Ctrl+g>`

### <a name="acceptandgetnext"></a>AcceptAndGetNext

Försök att köra den aktuella indatamängden. Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.

- Emacs: `<Ctrl+o>`

### <a name="acceptline"></a>AcceptLine

Försök att köra den aktuella indatamängden. Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.

- Kommandot `<Enter>`
- Emacs: `<Enter>`
- Vi infognings läge: `<Enter>`

### <a name="addline"></a>AddLine

Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden. Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.

- Kommandot `<Shift+Enter>`
- Emacs: `<Shift+Enter>`
- Vi infognings läge: `<Shift+Enter>`
- Kommando läge för vi: `<Shift+Enter>`

### <a name="backwarddeletechar"></a>BackwardDeleteChar

Ta bort det före markören.

- CMD: `<Backspace>` , `<Ctrl+h>`
- Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`
- Vi infognings läge: `<Backspace>`
- Kommando läge för vi: `<X>` , `<d,h>`

### <a name="backwarddeleteline"></a>BackwardDeleteLine

Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.

- Kommandot `<Ctrl+Home>`
- Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`
- Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`

### <a name="backwarddeleteword"></a>BackwardDeleteWord

Tar bort föregående ord.

- Kommando läge för vi: `<Ctrl+w>` , `<d,b>`

### <a name="backwardkillline"></a>BackwardKillLine

Ta bort indatamängden från början av inmatarna till markören. Den avmarkerade texten placeras i stopp ringen.

- Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`

### <a name="backwardkillword"></a>BackwardKillWord

Ta bort indatamängden från början av det aktuella ordet till markören. Om markören är mellan ord raderas indatatypen från början av föregående ord till markören. Den avmarkerade texten placeras i stopp ringen.

- Kommandot `<Ctrl+Backspace>`
- Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`
- Vi infognings läge: `<Ctrl+Backspace>`
- Kommando läge för vi: `<Ctrl+Backspace>`

### <a name="cancelline"></a>CancelLine

Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.

- Vi infognings läge: `<Ctrl+c>`
- Kommando läge för vi: `<Ctrl+c>`

### <a name="copy"></a>Kopiera

Kopiera vald region till Urklipp i systemet. Om ingen region har valts kopierar du hela raden.

- Kommandot `<Ctrl+C>`

### <a name="copyorcancelline"></a>CopyOrCancelLine

Om text är markerad kopierar du till Urklipp, annars avbryter du raden.

- Kommandot `<Ctrl+c>`
- Emacs: `<Ctrl+c>`

### <a name="cut"></a>Klipp ut

Ta bort markerad region som placerar borttagen text i Urklipp i systemet.

- Kommandot `<Ctrl+x>`

### <a name="deletechar"></a>DeleteChar

Ta bort specialtecknet under markören.

- Kommandot `<Delete>`
- Emacs: `<Delete>`
- Vi infognings läge: `<Delete>`
- Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`

### <a name="deletecharorexit"></a>DeleteCharOrExit

Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.

- Emacs: `<Ctrl+d>`

### <a name="deleteendofword"></a>DeleteEndOfWord

Ta bort till slutet av ordet.

- Kommando läge för vi: `<d,e>`

### <a name="deleteline"></a>DeleteLine

Tar bort den aktuella raden och aktiverar ångra.

- Kommando läge för vi: `<d,d>`

### <a name="deletelinetofirstchar"></a>DeleteLineToFirstChar

Tar bort text från markören till det första icke-tomma tecken på raden.

- Kommando läge för vi: `<d,^>`

### <a name="deletetoend"></a>DeleteToEnd

Ta bort till slutet av raden.

- Kommando läge för vi: `<D>` , `<d,$>`

### <a name="deleteword"></a>DeleteWord

Ta bort nästa ord.

- Kommando läge för vi: `<d,w>`

### <a name="forwarddeleteline"></a>ForwardDeleteLine

Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.

- Kommandot `<Ctrl+End>`
- Vi infognings läge: `<Ctrl+End>`
- Kommando läge för vi: `<Ctrl+End>`

### <a name="insertlineabove"></a>InsertLineAbove

En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden. Markören flyttas till början av den nya raden.

- Kommandot `<Ctrl+Enter>`

### <a name="insertlinebelow"></a>InsertLineBelow

En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden. Markören flyttas till början av den nya raden.

- Kommandot `<Shift+Ctrl+Enter>`

### <a name="invertcase"></a>InvertCase

Invertera Skift läget för det aktuella specialtecknet och gå till nästa.

- Kommando läge för vi: `<~>`

### <a name="killline"></a>KillLine

Ta bort indatamängden från markören till slutet av indatamängden. Den avmarkerade texten placeras i stopp ringen.

- Emacs: `<Ctrl+k>`

### <a name="killregion"></a>KillRegion

Stoppa texten mellan markören och markeringen.

- Funktionen är obunden.

### <a name="killword"></a>KillWord

Ta bort indatamängden från markören till slutet av det aktuella ordet. Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord. Den avmarkerade texten placeras i stopp ringen.

- Kommandot `<Ctrl+Delete>`
- Emacs: `<Alt+d>` , `<Escape,d>`
- Vi infognings läge: `<Ctrl+Delete>`
- Kommando läge för vi: `<Ctrl+Delete>`

### <a name="paste"></a>Klistra in

Klistra in text från Urklipp i systemet.

- CMD: `<Ctrl+v>` , `<Shift+Insert>`
- Vi infognings läge: `<Ctrl+v>`
- Kommando läge för vi: `<Ctrl+v>`

> [!IMPORTANT]
> När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine. Indatabufferten skickas sedan till PowerShell-parsern. Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget. Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras. Därför parsas inmatarna en rad i taget. Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.

### <a name="pasteafter"></a>PasteAfter

Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.

- Kommando läge för vi: `<p>`

### <a name="pastebefore"></a>PasteBefore

Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.

- Kommando läge för vi: `<P>`

### <a name="prependandaccept"></a>PrependAndAccept

Lägga a # och acceptera raden.

- Kommando läge för vi: `<#>`

### <a name="redo"></a>Gör om

Ångra en ångra-åtgärd.

- Kommandot `<Ctrl+y>`
- Vi infognings läge: `<Ctrl+y>`
- Kommando läge för vi: `<Ctrl+y>`

### <a name="repeatlastcommand"></a>RepeatLastCommand

Upprepa den senaste text ändringen.

- Kommando läge för vi: `<.>`

### <a name="revertline"></a>RevertLine

Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.

- Kommandot `<Escape>`
- Emacs: `<Alt+r>` , `<Escape,r>`

### <a name="shellbackwardkillword"></a>ShellBackwardKillWord

Ta bort indatamängden från början av det aktuella ordet till markören. Om markören är mellan ord raderas indatatypen från början av föregående ord till markören. Den avmarkerade texten placeras i stopp ringen.

Funktionen är obunden.

### <a name="shellkillword"></a>ShellKillWord

Ta bort indatamängden från markören till slutet av det aktuella ordet. Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord. Den avmarkerade texten placeras i stopp ringen.

Funktionen är obunden.

### <a name="swapcharacters"></a>SwapCharacters

Byt det aktuella tecknen och det som är före det.

- Emacs: `<Ctrl+t>`
- Vi infognings läge: `<Ctrl+t>`
- Kommando läge för vi: `<Ctrl+t>`

### <a name="undo"></a>Ångra

Ångra en tidigare redigering.

- Kommandot `<Ctrl+z>`
- Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`
- Vi infognings läge: `<Ctrl+z>`
- Kommando läge för vi: `<Ctrl+z>` , `<u>`

### <a name="undoall"></a>UndoAll

Ångra alla tidigare redigeringar för raden.

- Kommando läge för vi: `<U>`

### <a name="unixwordrubout"></a>UnixWordRubout

Ta bort indatamängden från början av det aktuella ordet till markören. Om markören är mellan ord raderas indatatypen från början av föregående ord till markören. Den avmarkerade texten placeras i stopp ringen.

- Emacs: `<Ctrl+w>`

### <a name="validateandacceptline"></a>ValidateAndAcceptLine

Försök att köra den aktuella indatamängden. Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.

- Emacs: `<Ctrl+m>`

### <a name="viacceptline"></a>ViAcceptLine

Godkänn linjen och växla till infognings läge.

- Kommando läge för vi: `<Enter>`

### <a name="viacceptlineorexit"></a>ViAcceptLineOrExit

Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.

- Vi infognings läge: `<Ctrl+d>`
- Kommando läge för vi: `<Ctrl+d>`

### <a name="viappendline"></a>ViAppendLine

En ny rad infogas under den aktuella raden.

- Kommando läge för vi: `<o>`

### <a name="vibackwarddeleteglob"></a>ViBackwardDeleteGlob

Tar bort föregående ord, med bara blank steg som ord avgränsare.

- Kommando läge för vi: `<d,B>`

### <a name="vibackwardglob"></a>ViBackwardGlob

Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.

- Kommando läge för vi: `<B>`

### <a name="videletebrace"></a>ViDeleteBrace

Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.

- Kommando läge för vi: `<d,%>`

### <a name="videleteendofglob"></a>ViDeleteEndOfGlob

Ta bort till slutet av ordet.

- Kommando läge för vi: `<d,E>`

### <a name="videleteglob"></a>ViDeleteGlob

Ta bort nästa BLOB (tomt blank steg).

- Kommando läge för vi: `<d,W>`

### <a name="videletetobeforechar"></a>ViDeleteToBeforeChar

Raderas tills det tilldelas ett blank steg.

- Kommando läge för vi: `<d,t>`

### <a name="videletetobeforecharbackward"></a>ViDeleteToBeforeCharBackward

Raderas tills det tilldelas ett blank steg.

- Kommando läge för vi: `<d,T>`

### <a name="videletetochar"></a>ViDeleteToChar

Raderas tills det tilldelas ett blank steg.

- Kommando läge för vi: `<d,f>`

### <a name="videletetocharbackward"></a>ViDeleteToCharBackward

Tar bort baklänges tills angivet format.

- Kommando läge för vi: `<d,F>`

### <a name="viinsertatbegining"></a>ViInsertAtBegining

Växla till infognings läge och placera markören i början av raden.

- Kommando läge för vi: `<I>`

### <a name="viinsertatend"></a>ViInsertAtEnd

Växla till infognings läge och placera markören i slutet av raden.

- Kommando läge för vi: `<A>`

### <a name="viinsertline"></a>ViInsertLine

En ny rad infogas ovanför den aktuella raden.

- Kommando läge för vi: `<O>`

### <a name="viinsertwithappend"></a>ViInsertWithAppend

Lägg till från den aktuella rad positionen.

- Kommando läge för vi: `<a>`

### <a name="viinsertwithdelete"></a>ViInsertWithDelete

Ta bort det aktuella specialtecknet och växla till infognings läge.

- Kommando läge för vi: `<s>`

### <a name="vijoinlines"></a>ViJoinLines

Kopplar ihop den aktuella raden och nästa rad.

- Kommando läge för vi: `<J>`

### <a name="vireplaceline"></a>ViReplaceLine

Ta bort hela kommando raden.

- Kommando läge för vi: `<S>` , `<c,c>`

### <a name="vireplacetobeforechar"></a>ViReplaceToBeforeChar

Ersätter det tilldelade specialtecknet.

- Kommando läge för vi: `<c,t>`

### <a name="vireplacetobeforecharbackward"></a>ViReplaceToBeforeCharBackward

Ersätter det tilldelade specialtecknet.

- Kommando läge för vi: `<c,T>`

### <a name="vireplacetochar"></a>ViReplaceToChar

Raderas tills det tilldelas ett blank steg.

- Kommando läge för vi: `<c,f>`

### <a name="vireplacetocharbackward"></a>ViReplaceToCharBackward

Ersätter det tilldelade specialtecknet.

- Kommando läge för vi: `<c,F>`

### <a name="viyankbeginningofline"></a>ViYankBeginningOfLine

YANK från buffertens början till markören.

- Kommando läge för vi: `<y,0>`

### <a name="viyankendofglob"></a>ViYankEndOfGlob

YANK från markören till slutet av ordet/orden.

- Kommando läge för vi: `<y,E>`

### <a name="viyankendofword"></a>ViYankEndOfWord

YANK från markören till slutet av ordet/orden.

- Kommando läge för vi: `<y,e>`

### <a name="viyankleft"></a>ViYankLeft

YANK-tecknen till vänster om markören.

- Kommando läge för vi: `<y,h>`

### <a name="viyankline"></a>ViYankLine

YANK hela bufferten.

- Kommando läge för vi: `<y,y>`

### <a name="viyanknextglob"></a>ViYankNextGlob

YANK från markören till början av nästa ord.

- Kommando läge för vi: `<y,W>`

### <a name="viyanknextword"></a>ViYankNextWord

YANK ordet (s) efter markören.

- Kommando läge för vi: `<y,w>`

### <a name="viyankpercent"></a>ViYankPercent

YANK till/från matchande klammerparentes.

- Kommando läge för vi: `<y,%>`

### <a name="viyankpreviousglob"></a>ViYankPreviousGlob

YANK från början av ordet/orden till markören.

- Kommando läge för vi: `<y,B>`

### <a name="viyankpreviousword"></a>ViYankPreviousWord

YANK ordet (s) före markören.

- Kommando läge för vi: `<y,b>`

### <a name="viyankright"></a>ViYankRight

YANK-tecknen under och till höger om markören.

- Kommando läge för vi: `<y,l>` , `<y,Space>`

### <a name="viyanktoendofline"></a>ViYankToEndOfLine

YANK från markören till slutet av bufferten.

- Kommando läge för vi: `<y,$>`

### <a name="viyanktofirstchar"></a>ViYankToFirstChar

YANK från det första icke-tomt-tecken till markören.

- Kommando läge för vi: `<y,^>`

### <a name="yank"></a>Yank

Lägg till den senast nedlagda texten i indatamängden.

- Emacs: `<Ctrl+y>`

### <a name="yanklastarg"></a>YankLastArg

YANK det sista argumentet från föregående historik rad. Med ett argument fungerar den första gången som den anropas, precis som YankNthArg. Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).

- Kommandot `<Alt+.>`
- Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`

### <a name="yankntharg"></a>YankNthArg

YANK det första argumentet (efter kommandot) från föregående historik rad.
Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.

- Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`

### <a name="yankpop"></a>YankPop

Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.

- Emacs: `<Alt+y>` , `<Escape,y>`

## <a name="cursor-movement-functions"></a>Markör rörelse funktioner

### <a name="backwardchar"></a>BackwardChar

Flytta markören ett till vänster. Detta kan flytta markören till föregående rad med flera rader.

- Kommandot `<LeftArrow>`
- Emacs: `<LeftArrow>` , `<Ctrl+b>`
- Vi infognings läge: `<LeftArrow>`
- Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`

### <a name="backwardword"></a>BackwardWord

Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord. Ord gränser definieras med en konfigurerbar uppsättning tecken.

- Kommandot `<Ctrl+LeftArrow>`
- Emacs: `<Alt+b>` , `<Escape,b>`
- Vi infognings läge: `<Ctrl+LeftArrow>`
- Kommando läge för vi: `<Ctrl+LeftArrow>`

### <a name="beginningofline"></a>BeginningOfLine

Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden. Om indatamängden har en enda rad flyttar du till början av inmatade värden.

- Kommandot `<Home>`
- Emacs: `<Home>` , `<Ctrl+a>`
- Vi infognings läge: `<Home>`
- Kommando läge för vi: `<Home>`

### <a name="endofline"></a>EndOfLine

Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden. Om indatamängden har en enda rad, går du till slutet av indatamängden.

- Kommandot `<End>`
- Emacs: `<End>` , `<Ctrl+e>`
- Vi infognings läge: `<End>`

### <a name="forwardchar"></a>ForwardChar

Flytta markören ett till höger. Detta kan flytta markören till nästa rad med flera rader.

- Kommandot `<RightArrow>`
- Emacs: `<RightArrow>` , `<Ctrl+f>`
- Vi infognings läge: `<RightArrow>`
- Vi kommando läge: `<RightArrow>` , `<Space>` , `<l>`

### <a name="forwardword"></a>ForwardWord

Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord. Ord gränser definieras med en konfigurerbar uppsättning tecken.

- Emacs: `<Alt+f>` , `<Escape,f>`

### <a name="gotobrace"></a>GotoBrace

Gå till den matchande klammerparentesen, parentesen eller hakparentesen.

- Kommandot `<Ctrl+]>`
- Vi infognings läge: `<Ctrl+]>`
- Kommando läge för vi: `<Ctrl+]>`

### <a name="gotocolumn"></a>GotoColumn

Flytta till kolumnen som anges av arg.

- Kommando läge för vi: `<|>`

### <a name="gotofirstnonblankofline"></a>GotoFirstNonBlankOfLine

Flytta markören till det första icke-tomma tecken på raden.

- Kommando läge för vi: `<^>`

### <a name="movetoendofline"></a>MoveToEndOfLine

Flytta markören till slutet av indatamängden.

- Kommando läge för vi: `<End>` , `<$>`

### <a name="nextline"></a>NextLine

Flytta markören till nästa rad.

- Funktionen är obunden.

### <a name="nextword"></a>NextWord

Flytta markören framåt till början av nästa ord. Ord gränser definieras med en konfigurerbar uppsättning tecken.

- Kommandot `<Ctrl+RightArrow>`
- Vi infognings läge: `<Ctrl+RightArrow>`
- Kommando läge för vi: `<Ctrl+RightArrow>`

### <a name="nextwordend"></a>NextWordEnd

Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord. Ord gränser definieras med en konfigurerbar uppsättning tecken.

- Kommando läge för vi: `<e>`

### <a name="previousline"></a>PreviousLine

Flytta markören till föregående rad.

- Funktionen är obunden.

### <a name="shellbackwardword"></a>ShellBackwardWord

Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord. Ord gränser definieras av PowerShell-token.

- Funktionen är obunden.

### <a name="shellforwardword"></a>ShellForwardWord

Flytta markören framåt till början av nästa ord. Ord gränser definieras av PowerShell-token.

- Funktionen är obunden.

### <a name="shellnextword"></a>ShellNextWord

Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord. Ord gränser definieras av PowerShell-token.

- Funktionen är obunden.

### <a name="vibackwardword"></a>ViBackwardWord

Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord. Ord gränser definieras med en konfigurerbar uppsättning tecken.

- Kommando läge för vi: `<b>`

### <a name="viendofglob"></a>ViEndOfGlob

Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.

- Kommando läge för vi: `<E>`

### <a name="viendofpreviousglob"></a>ViEndOfPreviousGlob

Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.

- Funktionen är obunden.

### <a name="vigotobrace"></a>ViGotoBrace

Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.

- Kommando läge för vi: `<%>`

### <a name="vinextglob"></a>ViNextGlob

Flyttar till nästa ord, med bara blank steg som ord avgränsare.

- Kommando läge för vi: `<W>`

### <a name="vinextword"></a>ViNextWord

Flytta markören framåt till början av nästa ord. Ord gränser definieras med en konfigurerbar uppsättning tecken.

- Kommando läge för vi: `<w>`

## <a name="history-functions"></a>Historik funktioner

### <a name="beginningofhistory"></a>BeginningOfHistory

Flytta till det första objektet i historiken.

- Emacs: `<Alt+`<>`

### <a name="clearhistory"></a>ClearHistory

Rensar historiken i PSReadLine. Detta påverkar inte PowerShell-historiken.

- Kommandot `<Alt+F7>`

### <a name="endofhistory"></a>EndOfHistory

Flytta till det sista objektet (den aktuella indatamängden) i historiken.

- Emacs: `<Alt+>>`

### <a name="forwardsearchhistory"></a>ForwardSearchHistory

Utför en stegvis sökning i historiken.

- Kommandot `<Ctrl+s>`
- Emacs: `<Ctrl+s>`

### <a name="historysearchbackward"></a>HistorySearchBackward

Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.

- Kommandot `<F8>`

### <a name="historysearchforward"></a>HistorySearchForward

Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.

- Kommandot `<Shift+F8>`

### <a name="nexthistory"></a>NextHistory

Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.

- Kommandot `<DownArrow>`
- Emacs: `<DownArrow>` , `<Ctrl+n>`
- Vi infognings läge: `<DownArrow>`
- Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`

### <a name="previoushistory"></a>PreviousHistory

Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.

- Kommandot `<UpArrow>`
- Emacs: `<UpArrow>` , `<Ctrl+p>`
- Vi infognings läge: `<UpArrow>`
- Vi kommando läge: `<UpArrow>` , `<k>` , `<->`

### <a name="reversesearchhistory"></a>ReverseSearchHistory

Utför en stegvis sökning i historiken.

- Kommandot `<Ctrl+r>`
- Emacs: `<Ctrl+r>`

### <a name="visearchhistorybackward"></a>ViSearchHistoryBackward

Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.

- Vi infognings läge: `<Ctrl+r>`
- Kommando läge för vi: `</>` , `<Ctrl+r>`

## <a name="completion-functions"></a>Funktioner för slut för ande

### <a name="complete"></a>Klart

Försök att utföra slut för Ande på texten runt markören. Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande. Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.

- Emacs: `<Tab>`

### <a name="menucomplete"></a>MenuComplete

Försök att utföra slut för Ande på texten runt markören. Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande. Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.

- Kommandot `<Ctrl+Space>`
- Emacs: `<Ctrl+Space>`

### <a name="possiblecompletions"></a>PossibleCompletions

Visa listan över möjliga slut för ande.

- Emacs: `<Alt+=>`
- Vi infognings läge: `<Ctrl+Space>`
- Kommando läge för vi: `<Ctrl+Space>`

### <a name="tabcompletenext"></a>TabCompleteNext

Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.

- Kommandot `<Tab>`
- Kommando läge för vi: `<Tab>`

### <a name="tabcompleteprevious"></a>TabCompletePrevious

Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.

- Kommandot `<Shift+Tab>`
- Kommando läge för vi: `<Shift+Tab>`

### <a name="vitabcompletenext"></a>ViTabCompleteNext

Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.

- Vi infognings läge: `<Tab>`

### <a name="vitabcompleteprevious"></a>ViTabCompletePrevious

Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.

- Vi infognings läge: `<Shift+Tab>`

## <a name="miscellaneous-functions"></a>Diverse-funktioner

### <a name="capturescreen"></a>CaptureScreen

Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.

- Funktionen är obunden.

### <a name="clearscreen"></a>ClearScreen

Ta bort skärmen och rita den aktuella raden överst på skärmen.

- Kommandot `<Ctrl+l>`
- Emacs: `<Ctrl+l>`
- Vi infognings läge: `<Ctrl+l>`
- Kommando läge för vi: `<Ctrl+l>`

### <a name="digitargument"></a>DigitArgument

Starta ett nytt siffer argument för att skicka till andra funktioner.

- CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`
- Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`
- Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`

### <a name="invokeprompt"></a>InvokePrompt

Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen. Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.

- Funktionen är obunden.

### <a name="scrolldisplaydown"></a>ScrollDisplayDown

Rulla ned skärmen en skärm.

- Kommandot `<PageDown>`
- Emacs: `<PageDown>`

### <a name="scrolldisplaydownline"></a>ScrollDisplayDownLine

Bläddra nedåt en rad.

- Kommandot `<Ctrl+PageDown>`
- Emacs: `<Ctrl+PageDown>`

### <a name="scrolldisplaytocursor"></a>ScrollDisplayToCursor

Rulla skärmen till markören.

- Emacs: `<Ctrl+End>`

### <a name="scrolldisplaytop"></a>ScrollDisplayTop

Rulla visningen längst upp.

- Emacs: `<Ctrl+Home>`

### <a name="scrolldisplayup"></a>ScrollDisplayUp

Rulla ned skärmen som visas på en skärm.

- Kommandot `<PageUp>`
- Emacs: `<PageUp>`

### <a name="scrolldisplayupline"></a>ScrollDisplayUpLine

Rulla upp en rad som visas.

- Kommandot `<Ctrl+PageUp>`
- Emacs: `<Ctrl+PageUp>`

### <a name="selfinsert"></a>SelfInsert

Infoga nyckeln.

- Funktionen är obunden.

### <a name="showkeybindings"></a>ShowKeyBindings

Visa alla bindnings nycklar.

- Kommandot `<Ctrl+Alt+?>`
- Emacs: `<Ctrl+Alt+?>`
- Vi infognings läge: `<Ctrl+Alt+?>`

### <a name="vicommandmode"></a>ViCommandMode

Växla det aktuella operativ läget från Vi-Insert till vi-Command.

- Vi infognings läge: `<Escape>`

### <a name="vidigitargumentinchord"></a>ViDigitArgumentInChord

Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.

- Funktionen är obunden.

### <a name="vieditvisually"></a>ViEditVisually

Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.

- Emacs: `<Ctrl+x,Ctrl+e>`
- Kommando läge för vi: `<v>`

### <a name="viexit"></a>ViExit

Avslutar gränssnittet.

- Funktionen är obunden.

### <a name="viinsertmode"></a>ViInsertMode

Växla till infognings läge.

- Kommando läge för vi: `<i>`

### <a name="whatiskey"></a>WhatIsKey

Läs en nyckel och berätta vad nyckeln är kopplad till.

- Kommandot `<Alt+?>`
- Emacs: `<Alt+?>`

## <a name="selection-functions"></a>Markerings funktioner

### <a name="exchangepointandmark"></a>ExchangePointAndMark

Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.

- Emacs: `<Ctrl+x,Ctrl+x>`

### <a name="selectall"></a>SelectAll

Markera hela raden.

- Kommandot `<Ctrl+a>`

### <a name="selectbackwardchar"></a>SelectBackwardChar

Justera det aktuella urvalet så att det innehåller föregående-tecknen.

- Kommandot `<Shift+LeftArrow>`
- Emacs: `<Shift+LeftArrow>`

### <a name="selectbackwardsline"></a>SelectBackwardsLine

Justera det aktuella urvalet så att det tas från markören till början av raden.

- Kommandot `<Shift+Home>`
- Emacs: `<Shift+Home>`

### <a name="selectbackwardword"></a>SelectBackwardWord

Justera det aktuella urvalet så att det innehåller föregående ord.

- Kommandot `<Shift+Ctrl+LeftArrow>`
- Emacs: `<Alt+B>`

### <a name="selectforwardchar"></a>SelectForwardChar

Justera det aktuella urvalet så att det inkluderar nästa-tecknen.

- Kommandot `<Shift+RightArrow>`
- Emacs: `<Shift+RightArrow>`

### <a name="selectforwardword"></a>SelectForwardWord

Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.

- Emacs: `<Alt+F>`

### <a name="selectline"></a>SelectLine

Justera det aktuella urvalet så att det tas från markören till slutet av raden.

- Kommandot `<Shift+End>`
- Emacs: `<Shift+End>`

### <a name="selectnextword"></a>SelectNextWord

Justera det aktuella urvalet så att det inkluderar nästa ord.

- Kommandot `<Shift+Ctrl+RightArrow>`

### <a name="selectshellbackwardword"></a>SelectShellBackwardWord

Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.

- Funktionen är obunden.

### <a name="selectshellforwardword"></a>SelectShellForwardWord

Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.

- Funktionen är obunden.

### <a name="selectshellnextword"></a>SelectShellNextWord

Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.

- Funktionen är obunden.

### <a name="setmark"></a>SetMark

Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.

- Emacs: `<Ctrl+`>`

## <a name="search-functions"></a>Sök funktioner

### <a name="charactersearch"></a>CharacterSearch

Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.
Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.

- Kommandot `<F3>`
- Emacs: `<Ctrl+]>`
- Vi infognings läge: `<F3>`
- Kommando läge för vi: `<F3>`

### <a name="charactersearchbackward"></a>CharacterSearchBackward

Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet. Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.

- Kommandot `<Shift+F3>`
- Emacs: `<Ctrl+Alt+]>`
- Vi infognings läge: `<Shift+F3>`
- Kommando läge för vi: `<Shift+F3>`

### <a name="repeatlastcharsearch"></a>RepeatLastCharSearch

Upprepa den senast inspelade sökningen.

- Kommando läge för vi: `<;>`

### <a name="repeatlastcharsearchbackwards"></a>RepeatLastCharSearchBackwards

Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.

- Kommando läge för vi: `<,>`

### <a name="repeatsearch"></a>RepeatSearch

Upprepa den senaste sökningen i samma riktning som tidigare.

- Kommando läge för vi: `<n>`

### <a name="repeatsearchbackward"></a>RepeatSearchBackward

Upprepa den senaste sökningen i samma riktning som tidigare.

- Kommando läge för vi: `<N>`

### <a name="searchchar"></a>SearchChar

Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken. Detta är endast för funktioner.

- Kommando läge för vi: `<f>`

### <a name="searchcharbackward"></a>SearchCharBackward

Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen. Detta är endast för funktioner.

- Kommando läge för vi: `<F>`

### <a name="searchcharbackwardwithbackoff"></a>SearchCharBackwardWithBackoff

Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen. Detta är endast för funktioner.

- Kommando läge för vi: `<T>`

### <a name="searchcharwithbackoff"></a>SearchCharWithBackoff

Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken. Detta är endast för funktioner.

- Kommando läge för vi: `<t>`

### <a name="searchforward"></a>SearchForward

Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.

- Vi infognings läge: `<Ctrl+s>`
- Kommando läge för vi: `<?>` , `<Ctrl+s>`

## <a name="custom-key-bindings"></a>Anpassade nyckel bindningar

PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` . De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

Du kan binda en script block till en nyckel. Script block kan göra det mycket du vill. Några användbara exempel är

- redigera kommando raden
- öppna ett nytt fönster (t. ex. hjälp)
- ändra kataloger utan att ändra kommando raden

Script block tar emot två argument:

- `$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen. Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key. Många anpassade bindningar ignorerar det här argumentet.

- `$arg` – Ett godtyckligt argument. Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument. Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.

Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den. Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.

De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.
Dessa API: er dokumenteras i nästa avsnitt.

## <a name="custom-key-binding-support-apis"></a>API: er för anpassad nyckel bindning support

Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel. De flesta är användbara i anpassade nyckel bindningar.

```csharp
void AddToHistory(string command)
```

Lägg till en kommando rad i historiken utan att köra den.

```csharp
void ClearKillRing()
```

Rensa Kill-ringen.  Detta används främst för testning.

```csharp
void Delete(int start, int length)
```

Ta bort tecken längd från början.  Den här åtgärden stöder ångra/gör om.

```csharp
void Ding()
```

Utför instruktionen dings baserat på användarnas preferenser.

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.  Den första används ofta i enkla fall.  Den andra används om bindningen gör något mer avancerat med AST.

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

Den här funktionen används av Get-PSReadLineKeyHandler och är förmodligen inte användbar i en anpassad nyckel bindning.

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

Om det inte finns något val på kommando raden returneras-1 både i Start-och längd. Om det finns ett val på kommando raden returneras start och längden på markeringen.

```csharp
void Insert(char c)
void Insert(string s)
```

Infoga ett tecken eller en sträng vid markören.  Den här åtgärden stöder ångra/gör om.

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

Detta är den huvudsakliga start punkten för PSReadLine. Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.

```csharp
void RemoveKeyHandler(string[] key)
```

Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.

```csharp
void Replace(int start, int length, string replacement)
```

Ersätt några av inmatarna. Den här åtgärden stöder ångra/gör om. Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.

```csharp
void SetCursorPosition(int cursor)
```

Flytta markören till den aktuella förskjutningen. Markör förflyttning spåras inte för ångra.

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

Den här hjälp metoden används för anpassade bindningar som följer DigitArgument. Ett typiskt anrop ser ut så här

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a>NOTE

### <a name="powershell-compatibility"></a>POWERSHELL-KOMPATIBILITET

PSReadLine kräver PowerShell 3,0 eller senare och konsol värden. Den fungerar inte i PowerShell ISE. Den fungerar i-konsolen i Visual Studio Code.

### <a name="command-history"></a>KOMMANDO HISTORIK

PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden. Detta kan innehålla känsliga data, inklusive lösen ord. Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text. Historikfilerna är en fil med namnet `$($host.Name)_history.txt` . I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` . På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .

### <a name="feedback--contributing-to-psreadline"></a>FEEDBACK & som bidrar till PSReadLine

[PSReadLine på GitHub](https://github.com/PowerShell/PSReadLine)

Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.

## <a name="see-also"></a>SE ÄVEN

PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.
