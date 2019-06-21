---
title: Kommentarbaserad hjälp nyckelord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301535"
---
# <a name="comment-based-help-keywords"></a>Nyckelord för kommentarsbaserad hjälp

Det här avsnittet listar och beskriver nyckelord i kommentarbaserad hjälp.

## <a name="keywords-in-comment-based-help"></a>Nyckelord i Kommentarbaserad hjälp

Följande är giltiga kommentarbaserad hjälp nyckelorden. De listas i den ordning som de normalt visas i ett hjälpavsnitt tillsammans med deras avsedda användning. Dessa nyckelord kan visas i vilken ordning som helst i kommentarbaserad hjälp och de är inte skiftlägeskänsliga.

Observera att den `.ExternalHelp` nyckelordet har företräde framför alla andra kommentarbaserad hjälp-nyckelord. När `.ExternalHelp` finns, den [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdleten visas inte kommentarbaserad hjälp, även om det går inte att hitta en hjälpfil som överensstämmer med värdet för nyckelordet.

`.Synopsis` En kort beskrivning av funktionen eller skript. Det här nyckelordet användas endast en gång i varje avsnitt.

`.Description` En detaljerad beskrivning av funktionen eller skript. Det här nyckelordet användas endast en gång i varje avsnitt.

`.Parameter` *\<Parametern-Name >* beskrivning av en parameter. Du kan inkludera en `.Parameter` nyckelord för varje parameter i funktionen eller skript.

Den `.Parameter` nyckelord kan visas i vilken ordning som helst i kommentarblocket, men den ordning som parametrarna som visas i den `Param` instruktionen eller funktionen deklarationen bestämmer den ordning som parametrarna som visas i hjälpavsnittet. Om du vill ändra ordningen på parametrar i hjälpavsnittet, ändra ordning på parametrarna i den `Param` instruktionen eller funktionen deklaration.

Du kan också ange en beskrivning av parameter genom att placera en kommentar i den `Param` instruktionen omedelbart före parametern variabelnamnet. Om du använder både en `Param` instruktionen kommentaren och en `.Parameter` nyckelord, den beskrivning som är associerade med den `.Parameter` nyckelord används, och `Param` instruktionen kommentar ignoreras.

`.Example` Ett exempel på kommando som använder funktionen eller skript, eventuellt följt av exempel på utdata och en beskrivning. Upprepa det här nyckelordet för varje exempel.

`.Inputs` Microsoft .NET Framework-typer av objekt som kan skickas till funktionen eller skript. Du kan också innehålla en beskrivning av objekt som indata.

`.Outputs` .NET Framework-typ av objekt som cmdleten returnerar. Du kan också innehålla en beskrivning av objekt som returneras.

`.Notes` Ytterligare information om funktionen eller skript.

`.Link` Namnet på ett närliggande avsnitt. Upprepa det här nyckelordet för varje relaterat ämne. Det här innehållet visas i avsnittet med länkar i hjälpavsnittet.

Den `.Link` nyckelordet innehåll kan även innehålla en identifierare URI (Uniform Resource) till en onlineversion av samma hjälpavsnittet. Online-versionen öppnas när du använder den `Online` -parametern för Get-Help. URI: N måste börja med ”http” eller ”https”.

`.Component` Teknik eller funktion som använder den funktion eller ett skript eller som den tillhör. Det här innehållet visas när kommandot Get-Help innehåller den `Component` -parametern för Get-Help.

`.Role` Användarrollen hjälpavsnittet. Det här innehållet visas när kommandot Get-Help innehåller den `Role` -parametern för Get-Help.

`.Functionality` Avsedd att användas för funktionen. Det här innehållet visas när kommandot Get-Help innehåller den `Functionality` -parametern för Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Omdirigerar till hjälpavsnitt för det angivna kommandot. Du kan omdirigera användare till alla hjälpavsnitt, inklusive hjälpavsnitt för en funktion, skript, cmdlet eller providern.

`.ForwardHelpCategory` `<Category>` Anger kategorin hjälp för objektet i ForwardHelpTargetName. Giltiga värden är Alias, Cmdlet, hjälpfil, funktion, leverantör, allmänna, vanliga frågor och svar, ordlista, ScriptCommand, ExternalScript, Filter eller alla. Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.

`.RemoteHelpRunspace` `<PSSession-variable>` Anger en session som innehåller hjälpavsnittet. Ange en variabel som innehåller en PSSession. Det här nyckelordet används av den `Export-PSSession` cmdlet för att hitta hjälpavsnitten för exporterade kommandon.

`.ExternalHelp` `<XML Help File>` Anger sökvägen och/eller namnet på en XML-baserade hjälpfilen för skript eller funktioner.

Den `.ExternalHelp` nyckelordet meddelar den [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet för att få hjälp med skript eller funktioner i en XML-baserade-fil. Den **. ExternalHelp** nyckelordet krävs när du använder en XML-baserade hjälpfilen för skript eller funktioner. Utan detta kommer `Get-Help` kommer inte att hitta en hjälpfilen för den funktion eller ett skript.

Den `.ExternalHelp` nyckelordet har företräde framför alla andra kommentarbaserad hjälp-nyckelord. När `.ExternalHelp` finns, den [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdleten visas inte kommentarbaserad hjälp, även om det går inte att hitta en hjälpfil som överensstämmer med värdet för nyckelordet.

När funktionen exporteras av en skriptmodul, värdet för `.ExternalHelp` ska vara ett filnamn utan sökväg. `Get-Help` söker efter filen i en underkatalog för språkspecifika till modulkatalogen. Det finns inga krav för filnamnet, men ett bra tips är att använda följande filformat för avbildningsnamn: `<ScriptModule>.psm1-help.xml`.

När funktionen inte är associerad med en modul, inkluderar du sökvägen och filnamnet i värdet för den **. ExternalHelp** nyckelord. Om den angivna sökvägen till XML-filen innehåller UI-kultur-specifika underkataloger `Get-Help` söker underkataloger rekursivt för en XML-fil med namnet på skriptet eller funktion i enlighet med det språk som reserv standarder som upprättats för Windows, precis som den gör för alla XML-baserade hjälpavsnitt.

Mer information om format för att XML-baserade Help cmdleten finns i [skriva Windows PowerShell-Cmdlet-hjälp](./writing-help-for-windows-powershell-cmdlets.md).