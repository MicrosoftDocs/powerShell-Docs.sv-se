---
title: Kommentera-baserade hjälp nyckelord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353377"
---
# <a name="comment-based-help-keywords"></a>Nyckelord för kommentarsbaserad hjälp

Det här avsnittet innehåller information om nyckelorden i kommenterad hjälp.

## <a name="keywords-in-comment-based-help"></a>Nyckelord i kommenterings-baserad hjälp

Följande är giltiga kommentarer baserade hjälp nyckelord. De visas i den ordning som de normalt visas i ett hjälp avsnitt, tillsammans med deras avsedda användning. Dessa nyckelord kan visas i vilken ordning som helst i den kommenterade hjälpen, och de är inte Skift läges känsliga.

Observera att nyckelordet `.ExternalHelp` har företräde framför alla andra kommenterings-baserade hjälp nyckelord. När `.ExternalHelp` finns visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.

`.Synopsis` en kort beskrivning av funktionen eller skriptet. Det här nyckelordet kan bara användas en gång i varje ämne.

`.Description` en detaljerad beskrivning av funktionen eller skriptet. Det här nyckelordet kan bara användas en gång i varje ämne.

`.Parameter` *\<parameter-Name >* beskrivningen av en parameter. Du kan inkludera ett `.Parameter` nyckelord för varje parameter i funktionen eller skriptet.

`.Parameter` nyckelord kan visas i vilken ordning som helst i kommentars blocket, men i vilken ordning parametrarna visas i instruktionen `Param` eller funktions deklaration bestämmer ordningen i vilken parametrarna visas i hjälp avsnittet. Om du vill ändra ordningen på parametrarna i hjälp avsnittet ändrar du ordningen på parametrarna i `Param`-instruktionen eller funktions deklarationen.

Du kan också ange en parameter beskrivning genom att placera en kommentar i `Param` instruktionen omedelbart före parameter variabel namnet. Om du använder både en kommentar från `Param`-satsen och ett `.Parameter` nyckelord, används beskrivningen som är associerad med nyckelordet `.Parameter` och kommentaren `Param`-satsen ignoreras.

`.Example` ett exempel kommando som använder funktionen eller skriptet, eventuellt följt av exempel på utdata och en beskrivning. Upprepa det här nyckelordet för varje exempel.

`.Inputs` de Microsoft .NET Ramverks typerna av objekt som kan skickas till funktionen eller skriptet. Du kan också inkludera en beskrivning av inobjekten.

`.Outputs` .NET Framework typ av objekt som cmdleten returnerar. Du kan också inkludera en beskrivning av de returnerade objekten.

`.Notes` ytterligare information om funktionen eller skriptet.

`.Link` namnet på ett relaterat ämne. Upprepa det här nyckelordet för varje relaterat ämne. Det här innehållet visas i avsnittet relaterade länkar i hjälp avsnittet.

Det `.Link` nyckelordet innehåll kan även innehålla en Uniform Resource Identifier (URI) till en online-version av samma hjälp avsnitt. Online-versionen öppnas när du använder `Online`-parametern för Get-Help. URI: n måste börja med http eller https.

`.Component` tekniken eller funktionen som används av funktionen eller skriptet eller som den är relaterad till. Det här innehållet visas när kommandot Get-Help innehåller `Component`-parametern för Get-Help.

`.Role` användar rollen för hjälp avsnittet. Det här innehållet visas när kommandot Get-Help innehåller `Role`-parametern för Get-Help.

`.Functionality` den avsedda användningen av funktionen. Det här innehållet visas när kommandot Get-Help innehåller `Functionality`-parametern för Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` omdirigeras till hjälp avsnittet för det angivna kommandot. Du kan omdirigera användare till valfritt hjälp avsnitt, inklusive hjälp avsnitt för en funktion, ett skript, en cmdlet eller en provider.

`.ForwardHelpCategory` `<Category>` anger hjälp kategorin för objektet i ForwardHelpTargetName. Giltiga värden är alias, cmdlet, hjälpfil, Function, Provider, General, FAQ, ordlista, ScriptCommand, ExternalScript, filter eller alla. Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.

`.RemoteHelpRunspace` `<PSSession-variable>` anger en session som innehåller hjälp avsnittet. Ange en variabel som innehåller en PSSession. Det här nyckelordet används av `Export-PSSession`-cmdleten för att hitta hjälp avsnitten för de exporterade kommandona.

`.ExternalHelp` `<XML Help File>` anger sökvägen och/eller namnet på en XML-baserad hjälpfil för skriptet eller funktionen.

Nyckelordet `.ExternalHelp` anger cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) för att få hjälp med skriptet eller funktionen i en XML-baserad fil. **.** Nyckelordet ExternalHelp krävs när du använder en XML-baserad hjälpfil för ett skript eller en funktion. Utan det kommer `Get-Help` inte att hitta någon hjälp fil för funktionen eller skriptet.

Nyckelordet `.ExternalHelp` har företräde framför alla andra kommenterings-baserade hjälp nyckelord. När `.ExternalHelp` finns visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.

När funktionen exporteras av en-skript-modul ska värdet för `.ExternalHelp` vara ett fil namn utan sökväg. `Get-Help` söker efter filen i en språkspecifik under katalog i modulens katalog. Det finns inga krav på fil namnet, men det är en bra idé att använda följande fil namns format: `<ScriptModule>.psm1-help.xml`.

Om funktionen inte är associerad med en modul inkluderar du en sökväg och ett fil namn i värdet för **. ExternalHelp** -nyckelord. Om den angivna sökvägen till XML-filen innehåller UI-kultur-specifika under kataloger, `Get-Help` genomsöks under katalogerna rekursivt för en XML-fil med namnet på skriptet eller funktionen i enlighet med de språk reserv standarder som är etablerade för Windows, precis som för alla XML-baserade hjälp ämnen.

Mer information om cmdlet Help XML-baserade hjälp fils format finns i [skriva Windows PowerShell-cmdlet-hjälpen](./writing-help-for-windows-powershell-cmdlets.md).