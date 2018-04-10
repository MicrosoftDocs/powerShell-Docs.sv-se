---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Förstå viktiga Windows PowerShell-koncept
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 07ceaa2f3e6a192c6281cb4c99aed4c3f66afc7e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="understanding-important-windows-powershell-concepts"></a>Förstå viktiga Windows PowerShell-koncept
Windows PowerShell-designen integreras begrepp från många olika miljöer. Flera av dem är bekant för personer med erfarenhet av specifika tankar eller programmeringsmiljöer, men mycket få användarna vet om alla. Titta på några av dessa koncept ger en bra översikt över Windows-gränssnittet.

### <a name="commands-are-not-text-based"></a>Kommandon kan inte textbaserade
Till skillnad från traditionella kommandoradsgränssnittet kommandon, Windows PowerShell-cmdletarna har utformats för att behandla objekt - strukturerad information som är mer än bara en sträng med tecken som visas på skärmen. Kommandoutdata alltid innebär längs extra information som du kan använda om du behöver den. Diskuteras i det här avsnittet på djupet i det här dokumentet.

Om du har använt bearbetning av text-verktyg för att bearbeta kommandoradsverktyget data i förflutna, hittar du att de fungerar annorlunda om du försöker använda dem i Windows PowerShell. I de flesta fall behöver du inte bearbetning av text-verktyg för att extrahera specifik information. Du kan komma åt delar av data direkt med hjälp av standard manipulering kommandon i Windows PowerShell-objektet.

### <a name="the-command-family-is-extensible"></a>Kommandot-familjen är Extensible
Gränssnitt, till exempel Cmd.exe tillhandahåller ett sätt att utöka den inbyggda kommandouppsättningen direkt. Du kan skapa externa kommandoradsverktyg som körs i Cmd.exe, men dessa externa verktyg har inte tjänster, till exempel hjälp integration och Cmd.exe automatiskt vet inte att de är giltiga kommandon.

Intern binary-kommandon i Windows PowerShell, kallas även *cmdlets* (uttalas Commando-lets) kan förstärkas med cmdlets som du skapar och som du lägger till Windows PowerShell med hjälp av snapin-moduler. Windows PowerShell *snapin-moduler* kompileras precis som binära verktyg i andra gränssnitt. Du kan använda dem för att lägga till Windows PowerShell-providers shell, samt nya cmdlet: ar.

På grund av särskilda karaktär av interna Windows PowerShell-kommandon, kommer vi att referera till dem som *cmdlets*.

> [!NOTE]
> Windows PowerShell kan köra kommandon än cmdlets. Vi kommer inte att diskutera dem i detalj i den Användarhandbok för Windows PowerShell, men de kan vara användbart att veta om som kategorier av kommandot. Windows PowerShell stöder skript som kan jämföras med UNIX shell-skript och Cmd.exe batch-filer, men har filnamnstillägget .ps1. Windows PowerShell kan du skapa interna funktioner som kan användas direkt i gränssnittet eller i skript.

### <a name="windows-powershell-handles-console-input-and-display"></a>Windows PowerShell handtag konsolindata och visa
När du skriver ett kommando, bearbetar Windows PowerShell alltid kommandoradsverktyget indata direkt. Windows PowerShell, formateras även utdata som visas på skärmen. Detta är viktig eftersom det minskar det arbete som krävs för varje cmdlet och ser till att du kan alltid göra saker på samma sätt som du använder oavsett vilken cmdlet. Ett exempel på hur detta förenklar livslängd för verktyget utvecklare och användare är hjälp.

Traditionella kommandoradsverktyg har egna scheman för att begära och visa hjälp. Vissa kommandoradsverktyg använder **/?** utlöser den bidrar till att visa; andra använder **-?**, **/H**, eller till och med **//**. Vissa visas hjälp i ett GUI-fönster i stället för i konsolen visas. Vissa avancerade verktyg, till exempel programmet uppdaterings packa upp filer innan deras hjälp. Om du använder parametern fel, kan verktyget Ignorera vad du har angett och ska kunna utföra en uppgift automatiskt.

När du anger ett kommando i Windows PowerShell är allt du anger automatiskt parsa och före bearbetas av Windows PowerShell. Om du använder den **-?** parameter med en Windows PowerShell-cmdlet alltid betyder ”Visa hjälp för det här kommandot”. Cmdlet-utvecklare har inte att parsa kommandot. de behöver bara ange hjälptexten.

Det är viktigt att förstå att hjälp-funktioner i Windows PowerShell är tillgängliga även när du kör traditionella kommandoradsverktyg i Windows PowerShell. Windows PowerShell bearbetar parametrarna och skickar resultatet till externa verktyg.

> [!NOTE]
> Om du kör ett grafiskt program i Windows PowerShell, öppnas fönstret för programmet. Windows PowerShell intervenes endast när bearbetning kommandoraden indata du ange eller programmet utdatan till konsolfönstret; den påverkar inte hur programmet fungerar internt.

### <a name="windows-powershell-uses-some-c-syntax"></a>Windows PowerShell använder vissa C#-Syntax
Windows PowerShell har syntaxfunktioner och nyckelord som liknar de som används i programmeringsspråket, C# eftersom Windows PowerShell är baserad på .NET Framework. Lära sig Windows PowerShell gör det enklare att lära dig C#, om du är intresserad av språket.

Den här likhet är inte viktigt om du inte är en C#-programmerare. Men om du redan är bekant med C# kan likheterna göra lära sig Windows PowerShell mycket enklare.