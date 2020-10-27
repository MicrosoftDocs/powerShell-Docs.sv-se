---
ms.date: 06/09/2020
ms.topic: reference
title: Nyckelord för kommentarsbaserad hjälp
description: Nyckelord för kommentarsbaserad hjälp
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645472"
---
# <a name="comment-based-help-keywords"></a>Nyckelord för kommentarsbaserad hjälp

Det här avsnittet innehåller information om nyckelorden i kommenterad hjälp.

## <a name="keywords-in-comment-based-help"></a>Nyckelord i Comment-Based hjälp

Följande är giltiga kommentarer baserade hjälp nyckelord. De visas i den ordning som de normalt visas i ett hjälp avsnitt, tillsammans med deras avsedda användning. Dessa nyckelord kan visas i vilken ordning som helst i den kommenterade hjälpen, och de är inte Skift läges känsliga.

Observera att `.EXTERNALHELP` nyckelordet har företräde framför alla andra kommenterings-baserade hjälp nyckelord.
När `.EXTERNALHELP` finns, visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.

## <a name="synopsis"></a>. Sammanfattning

En kort beskrivning av funktionen eller skriptet. Det här nyckelordet kan bara användas en gång i varje ämne.

## <a name="description"></a>. BETECKNING

En detaljerad beskrivning av funktionen eller skriptet. Det här nyckelordet kan bara användas en gång i varje ämne.

## <a name="parameter-parameter-name"></a>. PROFILESERVICEAPPLICATIONPROXY \<Parameter-Name>

Beskrivningen av en parameter. Du kan inkludera ett `.PARAMETER` nyckelord för varje parameter i funktionen eller skriptet.

`.PARAMETER`Nyckelorden kan visas i vilken ordning som helst i kommentars blocket, men i vilken ordning parametrarna visas i `Param` instruktions-eller funktions deklarationen fastställs i vilken ordning parametrarna visas i hjälp avsnittet. Ändra ordningen på parametrarna i `Param` instruktions-eller funktions deklarationen om du vill ändra ordningen på parametrarna i hjälp avsnittet.

Du kan också ange en parameter beskrivning genom att placera en kommentar i `Param` instruktionen omedelbart före parameterns variabel namn. Om du använder både en `Param` instruktions kommentar och ett `.PARAMETER` nyckelord, används beskrivningen som är associerad med `.PARAMETER` nyckelordet och `Param` instruktions kommentaren ignoreras.

## <a name="example"></a>. EXEMPEL

Ett exempel kommando som använder funktionen eller skriptet, eventuellt följt av exempel på utdata och en beskrivning. Upprepa det här nyckelordet för varje exempel.

## <a name="inputs"></a>. TILLFÖR

De Microsoft .NET Ramverks typerna av objekt som kan skickas till funktionen eller skriptet. Du kan också inkludera en beskrivning av inobjekten.

## <a name="outputs"></a>. UTDATA

Den .NET Framework typ av objekt som cmdleten returnerar. Du kan också inkludera en beskrivning av de returnerade objekten.

## <a name="notes"></a>. NOTER

Ytterligare information om funktionen eller skriptet.

## <a name="link"></a>. OPERATIONSFÖLJDSLÄNKKOD

Namnet på ett relaterat ämne. Upprepa det här nyckelordet för varje relaterat ämne. Det här innehållet visas i avsnittet relaterade länkar i hjälp avsnittet.

`.LINK`Nyckelords innehållet kan också innehålla en Uniform Resource Identifier (URI) till en online-version av samma hjälp avsnitt. Online-versionen öppnas när du använder- `Online` parametern för `Get-Help` . URI: n måste börja med http eller https.

## <a name="component"></a>. KOMPONENTFILERNA

Namnet på tekniken eller funktionen som funktionen eller skriptet använder, eller som den är relaterad till.
**Komponent** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .

## <a name="role"></a>. Rollinnehavaren

Namnet på användar rollen för hjälp avsnittet. **Roll** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .

## <a name="functionality"></a>. FUNKTIONS

Nyckelord som beskriver den avsedda användningen av funktionen. **Funktions** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .

## <a name="forwardhelptargetname-command-name"></a>. FORWARDHELPTARGETNAME \<Command-Name>

Omdirigerar till hjälp avsnittet för det angivna kommandot. Du kan omdirigera användare till valfritt hjälp avsnitt, inklusive hjälp avsnitt för en funktion, ett skript, en cmdlet eller en provider.

## <a name="forwardhelpcategory-category"></a>. FORWARDHELPCATEGORY \<Category>

Anger hjälp kategorin för objektet i `.FORWARDHELPTARGETNAME` . Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.

Giltiga värden är:

- Alias
- Cmdlet
- Hjälpfil
- Funktion
- Leverantör
- Allmänt
- Vanliga frågor
- Ordlista
- ScriptCommand
- ExternalScript
- Filtrera
- Alla

## <a name="remotehelprunspace-pssession-variable"></a>. REMOTEHELPRUNSPACE \<PSSession-variable>

Anger en session som innehåller hjälp avsnittet. Ange en variabel som innehåller en PSSession. Det här nyckelordet används av `Export-PSSession` cmdleten för att hitta hjälp avsnitten för de exporterade kommandona.

## <a name="externalhelp-xml-help-file"></a>. EXTERNALHELP \<XML Help File>

Anger sökvägen och/eller namnet på en XML-baserad hjälpfil för skriptet eller funktionen.

`.EXTERNALHELP`Nyckelordet instruerar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) för att få hjälp med skriptet eller funktionen i en XML-baserad fil. `.EXTERNALHELP`Nyckelordet krävs när du använder en XML-baserad hjälp fil för ett skript eller en funktion. Utan det `Get-Help` kommer inte att hitta någon hjälp fil för funktionen eller skriptet.

`.EXTERNALHELP`Nyckelordet har företräde framför alla andra kommenterings-baserade hjälp nyckelord. När `.EXTERNALHELP` finns, visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.

När funktionen exporteras av en-skript-modul `.EXTERNALHELP` ska värdet vara ett fil namn utan sökväg. `Get-Help` söker efter filen i en språkspecifik under katalog i modulens katalog. Det finns inga krav på fil namnet, men det är en bra idé att använda följande fil namns format: `<ScriptModule>.psm1-help.xml` .

Om funktionen inte är associerad med en modul inkluderar du en sökväg och ett fil namn i värdet för `.EXTERNALHELP` nyckelordet. Om den angivna sökvägen till XML-filen innehåller UI-kultur-specifika under kataloger, `Get-Help` söker igenom under katalogerna rekursivt efter en XML-fil med namnet på skriptet eller funktionen i enlighet med de språk reserv standarder som är etablerade för Windows, precis som för alla XML-baserade hjälp avsnitt.

Mer information om cmdlet Help XML-baserade hjälp fils format finns i [skriva Windows PowerShell-cmdlet-hjälpen](./writing-help-for-windows-powershell-cmdlets.md).
