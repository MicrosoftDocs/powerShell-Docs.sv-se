---
title: Skrivhjälp för PowerShell-skript och -funktioner | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847847"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Skrivhjälp för PowerShell-skript och funktioner

PowerShell-skript och funktioner bör dokumenteras fullständigt när de delas med andra.
Den `Get-Help` cmdlet visar hjälpavsnitt skript och funktion i samma format som den visar hjälpen för cmdlet: ar, och alla de `Get-Help` parametrar som fungerar på skriptet och funktionen hjälpavsnitt.

PowerShell-skript kan innehålla ett hjälpavsnitt om skriptet och hjälpavsnitt innehåller information om varje funktioner i skriptet.
Funktioner som är delade oberoende av skript kan innehålla egna hjälpavsnitt.

Det här dokumentet beskriver format och korrekt placering av hjälpavsnitten och förslag riktlinjer för innehållet.

## <a name="types-of-script-and-function-help"></a>Typer av skript och funktionen hjälp

### <a name="comment-based-help"></a>Kommentarbaserad hjälp
Hjälpavsnitt som beskriver ett skript eller funktion kan implementeras som en uppsättning kommentarer i skript eller funktioner.
När du skriver kommentarbaserad hjälp för ett skript och funktioner i ett skript kan du vara noggrann uppmärksam reglerna för att placera kommentarbaserad hjälp.
Placeringen avgör om den `Get-Help` cmdlet kopplar hjälpavsnittet till skriptet eller en funktion.
Läs mer om hur du skriver hjälpavsnitt kommentarbaserad [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>XML-baserade kommandohjälp
Hjälpavsnitt som beskriver ett skript eller funktion kan implementeras i en XML-fil som använder kommandot hjälp schemat.
Du associerar skript eller funktion med XML-filen genom att använda den `ExternalHelp` kommentera följt av sökvägen och namnet på XML-filen.

När den `ExternalHelp` kommentar nyckelordet finns, åsidosätter kommentarbaserad hjälp, även om `Get-Help` kan inte hitta en hjälpfil som överensstämmer med värdet för den `ExternalHelp` nyckelord.

### <a name="online-help"></a>Onlinehjälp
Du kan publicera dina hjälpavsnitt på Internet och sedan dirigera `Get-Help` att öppna i avsnitt.
Läs mer om hur du skriver hjälpavsnitt kommentarbaserad [stödja onlinehjälp](../module/supporting-online-help.md).

Det finns ingen etablerade metod för att skriva konceptuella (”information”) ämnen för skript och funktioner.
Du kan dock skicka konceptuella ämnen på listan över Internet i avsnitt och deras URL: er i avsnittet med länkar i ett hjälpavsnitt för kommandot.

## <a name="content-considerations-for-script-and-function-help"></a>Innehåll överväganden för skript och funktionen hjälper

- Om du skriver ett mycket kort hjälpavsnitt med bara några av de kommando som är tillgängliga hjälpavsnitten, måste du inkludera Rensa beskrivningar av parametrar för skript eller funktioner. Även innehålla en eller två exempelkommandon i avsnittet exempel även om du vill utelämna exempel beskrivningar.

- Alla beskrivningar, referera till kommandot som skript eller funktioner. Den här informationen hjälper användarna att förstå och hantera kommandot.

  Följande detaljerad beskrivning om till exempel att kommandot New-avsnittet är ett skript. Detta påminner användarna som de behöver för att ange sökvägen och det fullständiga namnet när de kör den.

  > ”New-avsnittet skriptet skapar en tom konceptuellt avsnitt för varje ämnesnamnet i indatafilen...”

  Följande detaljerade beskrivningen anger att `Disable-PSRemoting` är en funktion. Den här informationen är särskilt användbart för användare när sessionen innehåller flera kommandon med samma namn, vilket kan vara dolt av ett kommando med högre prioritet.

  > Den `Disable-PSRemoting` funktionen inaktiverar alla sessionskonfigurationer på den lokala datorn...

- Beskriver hur du använder skriptet som helhet i ett hjälpavsnitt för skriptet. Om du också skriver hjälpavsnitt för funktioner i skriptet, nämner funktionerna i ditt skript hjälpavsnitt och innehålla referenser till funktionen hjälpavsnitten i avsnittet med länkar i hjälpavsnittet för skriptet. Däremot när en funktion är en del av ett skript, beskrivs i hjälpavsnittet funktionen den roll som funktionen spelar i skriptet och hur den kan användas oberoende av varandra. Sedan en lista över hjälpavsnitt skriptet i avsnittet med länkar i hjälpavsnittet för funktionen.

- När du skriver exempel för ett skript hjälpavsnitt, måste du ta med sökväg till skriptfilen i detta kommando. Detta påminner användarna att de måste ange sökvägen explicit, även när skriptet är i den aktuella katalogen.

- I ett hjälpavsnitt för funktionen påminna användarna om att funktionen finns bara i den aktuella sessionen och för att använda den i andra sessioner, de behöver för att lägga till den eller lägga till den i en PowerShell-profil.

- `Get-Help` Visar hjälpavsnittet för ett skript eller funktion endast när skriptfilen och hjälpavsnittsfiler sparas i rätt platser. Det är därför inte användbart att inkludera anvisningar för att installera PowerShell, eller spara eller installation av skript eller funktion i ett skript eller funktion hjälpavsnitt. Inkludera i stället några installationsanvisningar i dokumentet som används för att distribuera skript eller funktioner.

## <a name="see-also"></a>Se även

 [Skriva XML-baserade hjälpavsnitt för skript och funktioner](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Skriva XML-baserade hjälpavsnitt för kommandon](./writing-xml-based-help-topics-for-commands.md)

 [Skriva Kommentarbaserad hjälpavsnitt](./writing-comment-based-help-topics.md)
