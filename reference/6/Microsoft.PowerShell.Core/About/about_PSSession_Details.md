---
description: Innehåller detaljerad information om PowerShell-sessioner och den roll de spelar i fjärrkommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 6f469d0bf2268604e9a1bf09535c53afe89e184e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270609"
---
# <a name="about-pssession-details"></a>Om PSSession-information

## <a name="short-description"></a>Kort beskrivning
Innehåller detaljerad information om PowerShell-sessioner och den roll de spelar i fjärrkommandon.

## <a name="long-description"></a>Lång beskrivning

En session är en miljö där PowerShell körs. En session skapas åt dig när du startar PowerShell. Du kan skapa ytterligare sessioner som kallas "PowerShell-sessioner" eller "PSSessions" på datorn eller en annan dator.

Till skillnad från de sessioner som PowerShell skapar, styr du och hanterar de PSSessions som du skapar.

PSSessions spelar en viktig roll i fjärrdatorer. När du skapar en PSSession som är ansluten till en fjärrdator upprättar PowerShell en permanent anslutning till fjärrdatorn för att stödja PSSession. Du kan använda PSSession för att köra en serie kommandon, funktioner och skript som delar data.

Det här avsnittet innehåller detaljerad information om sessioner och PSSessions i PowerShell. Grundläggande information om de uppgifter som du kan utföra med sessioner finns [about_PSSessions](about_PSSessions.md).

## <a name="about-sessions"></a>Om sessioner

Tekniskt sett är en session en körnings miljö där PowerShell körs. Varje session innehåller en instans av system. Management. Automation-motorn och ett värd program där PowerShell körs. Värden kan vara den välbekanta PowerShell-konsolen eller ett annat program som kör kommandon, t. ex. Cmd.exe eller ett program som är byggt för att vara värd för PowerShell, till exempel Windows PowerShell ISE (Integrated Scripting Environment). I ett Windows-perspektiv är en session en Windows-process på mål datorn.

Varje session konfigureras separat. Den innehåller egna egenskaper, sin egen körnings princip och dess egna profiler. Den miljö som finns när sessionen skapas behålls för dess livstid även om du ändrar miljön på datorn. Alla sessioner skapas i ett globalt omfång, även sessioner som du skapar i ett skript.

Du kan bara köra ett kommando (eller en kommando pipeline) i en session i taget. Ett andra kommando körs synkront (ett i taget) och väntar upp till fyra minuter innan det första kommandot slutförs. Ett andra kommando körs asynkront (inte samtidigt).

## <a name="about-pssessions"></a>Om PSSessions

En session skapas varje gången du startar PowerShell. Dessutom skapar PowerShell tillfälliga sessioner för att köra enskilda kommandon.
Du kan dock också skapa sessioner (kallas "PowerShell-sessioner" eller "PSSessions") som du styr och hanterar.

PSSessions är viktiga för fjärrkommandon. Om du använder parametern **computername** i `Invoke-Command` `Enter-PSSession` cmdletarna eller upprättar PowerShell en tillfällig session för att köra kommandot och stänger sedan sessionen så snart kommandot eller den interaktiva sessionen är slutförd.

Men om du använder `New-PSSession` cmdleten för att skapa en PSSession, upprättar PowerShell en beständig session på den fjärrdator där du kan köra flera kommandon eller interaktiva sessioner. PSSessions som du skapar förblir öppen och tillgänglig för användning tills du tar bort dem eller tills du stänger sessionen där de skapades.

När du skapar en PSSession på en fjärrdator skapar systemet en PowerShell-process på fjärrdatorn och upprättar en anslutning från den lokala datorn till processen på fjärrdatorn. När du skapar en PSSession på den lokala datorn skapas både den nya processen och anslutningarna på den lokala datorn.

## <a name="when-do-i-need-a-pssession"></a>När behöver jag ett PSSession?

`Invoke-Command` `Enter-PSSession` Cmdletarna och har både **computername** -och **session** -parametrarna. Du kan använda antingen för att köra ett fjärrkommando.

Använd parametern **computername** för att köra ett enskilt kommando eller en serie orelaterade kommandon på en eller flera datorer.

Om du vill köra kommandon som delar data behöver du en permanent anslutning till fjärrdatorn. I så fall skapar du en PSSession och använder sedan parametern **session** för att köra kommandon i PSSession.

Många andra cmdletar som hämtar data från fjärrdatorer, till exempel,, `Get-Process` `Get-Service` och som `Get-EventLog` `Get-WmiObject` bara har en **computername** -parameter. De använder andra tekniker än PowerShell-fjärrkommunikation för att samla in data via en fjärr anslutning. Dessa cmdletar har ingen **sessionsnyckel** , men du kan använda `Invoke-Command` cmdleten för att köra dessa kommandon i en PSSession.

## <a name="how-do-i-create-a-pssession"></a>Hur skapar jag en PSSession?

Använd cmdleten för att skapa en PSSession `New-PSSession` . Du kan använda `New-PSSession` för att skapa en PSSession på en lokal eller fjärran sluten dator.

## <a name="can-i-create-a-pssession-on-any-computer"></a>Kan jag skapa en PSSession på vilken dator som helst?

Om du vill skapa en PSSession som är ansluten till en fjärrdator måste datorn konfigureras för fjärr kommunikation i PowerShell. Den aktuella användaren måste vara medlem i gruppen Administratörer på fjärrdatorn, annars måste den aktuella användaren kunna ange autentiseringsuppgifterna för en medlem i gruppen Administratörer. Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).

## <a name="can-i-see-my-pssessions-in-other-sessions"></a>Kan jag se min PSSessions i andra sessioner?

Från och med Windows PowerShell 3,0 hämtar parametern **computername** för cmdlet: en `Get-PSSession` PSSessions som du skapade på de angivna fjärrdatorerna.

Aktiva PSSessions underhålls på fjärrdatorn ("Server sidan" i en anslutning) och du kan hämta dem från valfri session på vilken dator som helst.

Om du till exempel skapar en PSSession från Server01-datorn till Server02-datorn och sedan växlar till Server03-datorn kan du använda ett kommando som följande för att hämta sessionen.

```powershell
Get-PSSession -ComputerName Server02
```

Även om du kopplar från sessionen behålls sessionen på fjärrdatorn tills du tar bort den eller tids gränsen.

I Windows PowerShell 2,0 kan du bara hämta de PSSessions som du har skapat i den aktuella sessionen. Det går inte att hämta PSSessions som du skapade i andra sessioner.

Mer information finns i [Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession).

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a>Kan jag se PSSessions som andra har skapat på datorn?

Du kan bara hämta och hantera de PSSessions som andra bara har skapat om du kan ange autentiseringsuppgifterna för den användare som skapade PSSession eller den session konfiguration som PSSession använder, inklusive RunAs-autentiseringsuppgifter. Annars kan du hämta, ansluta till, använda och hantera enbart de PSSessions som du har skapat.

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a>Kan jag ansluta till en PSSession från en annan dator?

Från och med Windows PowerShell 3,0 är PSSessions oberoende av de sessioner som de skapades i. Aktiva PSSessions bevaras på datorn på fjärran slutet eller på Server sidan av en anslutning.

Du kan använda `Disconnect-PSSession` cmdleten för att koppla från en PSSession. PSSession är frånkopplad från den lokala sessionen, men den underhålls på fjärrdatorn.
Kommandona fortsätter att köras i den frånkopplade PSSession. Du kan stänga PowerShell och stänga av den ursprungliga datorn utan att avbryta PSSession.

Sedan kan du, till och med timmar senare, använda `Get-PSSession` cmdleten för att hämta PSSession och `Connect-PSSession` cmdleten för att ansluta till PSSession från en ny session på en annan dator.

Mer information finns i [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a>Vad händer med min PSSession om min dator stannar?

Frånkopplade PSSessions är oberoende av de sessioner som de skapades i. Om du kopplar från en PSSession och stänger den ursprungliga datorn, bevaras PSSession på fjärrdatorn.

Dessutom försöker PowerShell återställa aktiva PSSessions som frånkopplas oavsiktligt, t. ex. genom en omstart av datorn, ett tillfälligt strömavbrott eller nätverks avbrott. PowerShell försöker underhålla eller återställa PSSession till ett öppet tillstånd, om den ursprungliga sessionen fortfarande är tillgänglig eller till frånkopplat tillstånd om det inte är det.

En "aktiv" PSSession är en som kör-kommandon. Om en PSSession är ansluten (inte frånkopplad) och kommandon körs i PSSession när den anslutna sessionen stängs försöker PowerShell att underhålla PSSession på fjärrdatorn. Men om inga kommandon körs i PSSession stänger PowerShell PSSession när den anslutna sessionen stängs.

Mer information finns i [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).

## <a name="can-i-run-a-background-job-in-a-pssession"></a>Kan jag köra ett bakgrunds jobb i en PSSession?

Ja. Ett bakgrunds jobb är ett kommando som körs asynkront i bakgrunden utan att interagera med den aktuella sessionen. När du skickar ett kommando för att starta ett jobb returnerar kommandot ett jobb objekt, men jobbet fortsätter att köras i bakgrunden tills det är klart.

Om du vill starta ett bakgrunds jobb på en lokal dator använder du `Start-Job` kommandot.
Du kan köra bakgrunds jobbet i en tillfällig anslutning (med parametern **computername** ) eller i en PSSession (med hjälp av parametern **session** ).

Om du vill starta ett bakgrunds jobb på en fjärrdator använder du `Invoke-Command` cmdleten med dess **AsJob** -parameter eller använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på en fjärrdator. När du använder parametern **AsJob** kan du använda **dator namn** eller **sessionsnycklar** .

När `Invoke-Command` du använder för att köra ett `Start-Job` kommando måste du köra kommandot i en PSSession. Om du använder parametern **computername** avslutar PowerShell anslutningen när jobbobjektet returnerar och jobbet avbryts.

Mer information finns i artikeln [om jobb](about_Jobs.md).

## <a name="can-i-run-an-interactive-session"></a>Kan jag köra en interaktiv session?

Ja. Använd cmdleten för att starta en interaktiv session med en fjärrdator `Enter-PSSession` . I en interaktiv session, de kommandon som du skriver körs på fjärrdatorn, precis som om du har angett dem direkt på fjärrdatorn.

Du kan köra en interaktiv session i en tillfällig session (med hjälp av parametern **computername** ) eller i en PSSession (med hjälp av parametern **session** ).
Om du använder en PSSession behåller PSSession data från föregående kommandon och PSSession behåller alla data som genereras under den interaktiva sessionen för användning i senare kommandon.

När du slutar den interaktiva sessionen förblir PSSession öppen och tillgänglig för användning.

Mer information finns i [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) och [exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession).

## <a name="must-i-delete-the-pssessions"></a>Måste jag ta bort PSSessions?

Ja. En PSSession är en process som är en fristående miljö som använder minne och andra resurser, även om du inte använder den. När du är färdig med en PSSession tar du bort den. Om du skapar flera PSSessions stänger du dem som du inte använder och bibehåller bara de som för närvarande används.

Använd cmdleten för att ta bort PSSessions `Remove-PSSession` . Den tar bort PSSessions och släpper alla resurser som de använde.

Du kan också använda **IdleTimeOut** -parametern för `New-PSSessionOption` för att stänga en inaktiv PSSession efter ett intervall som du anger. Mer information finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

Om du sparar ett PSSession-objekt i en variabel och sedan tar bort PSSession, eller låter det ta lång tid, innehåller variabeln fortfarande objektet PSSession, men PSSession är inte aktiv och kan inte användas eller repare ras.

## <a name="are-all-sessions-and-pssessions-alike"></a>Är alla sessioner och PSSessions likadana?

Nej. Utvecklare kan skapa anpassade sessioner som bara innehåller valda providers och cmdlets. Om ett kommando fungerar i en session men inte i en annan, kan det bero på att sessionen är begränsad.

## <a name="see-also"></a>Se även

[about_Jobs](about_Jobs.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Avsluta-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)
