---
title: Referens för Windows PowerShell - Nyheter
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080534"
---
# <a name="whats-new"></a>Nyheter

Windows PowerShell 2.0 tillhandahåller följande nya funktioner för användning när du skriver cmdlets, leverantörer och vara värd för program.

## <a name="modules"></a>Moduler

Nu kan du paketera och distribuera Windows PowerShell-lösningar med hjälp av moduler. Moduler kan du till partition, organisera och abstrahera dina Windows PowerShell-kod i självständig, återanvändbara enheter. Mer information om finns i skriva en Windows PowerShell-modul.

## <a name="the-powershell-class"></a>PowerShell-klass

PowerShell-klassen innehåller en enklare lösning för att skapa program, kallat värdprogram som programmässigt kör kommandon. Den här klassen kan du skapa en pipeline med kommandon anger körningsutrymme som används för att köra kommandon, och anropar kommandona synkront eller asynkront.

## <a name="the-runspacepool-class"></a>RunspacePool-klass

Runspace pooler gör att du kan skapa flera körningsutrymmen med hjälp av ett enda anrop. Metoden CreateRunspacePool innehåller flera överlagringar som kan användas för att skapa körningsutrymmen som har samma funktioner som samma värd, inledande sessionstillstånd och anslutningsinformation.

## <a name="the-initialsessionstate-class"></a>InitialSessionState-klass

Klassen InitialSessionState kan du skapa en sessionskonfiguration tillstånd som ska användas när ett körningsutrymme öppnas. Du kan skapa en anpassad konfiguration, en standardkonfiguration som innehåller de kommandon som tillhandahålls av mshshort och en konfiguration som vars kommandon är begränsade baserat på funktionerna i sessionen.

## <a name="remote-runspaces"></a>Remote körningsutrymmen

Du kan nu skapa körningsutrymmen som kan öppnas på fjärrdatorer, så att du kan köra kommandon på fjärrdatorn och samla in resultatet lokalt. Om du vill skapa ett fjärrkörningsutrymme, måste du ange information om fjärranslutningen när du skapar körningsutrymmet. Se vilka CreateRunspace och CreateRunspacePool för exempel. Informationen som definieras av klassen RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Privat körningsutrymme element

Du kan nu skapa körningsutrymmen vars element är offentlig eller privat. På så sätt kan du skapa körningsutrymmen vars element är tillgängliga för körningsutrymmet, men är inte tillgängligt för användaren. Se ConstrainedSessionStateEntry klassen för att ta reda på vilka element i körningsutrymmet kan göras privata.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runspace threading lägen och inneslutningstillståndet

Du kan nu ange hur trådar skapas och används när du kör kommandon i ett körningsutrymme. Se egenskaperna System.Management.Automation.Runspaces.Runspace.ThreadOptions och System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Nu kan du få inneslutningstillståndet trådar som används för att köra kommandon i ett körningsutrymme. Se egenskaperna System.Management.Automation.Runspaces.Runspace.ApartmentState och System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Transaktions-cmdletar

Du kan nu skapa cmdletar som kan användas i en transaktion. När en cmdlet används i en transaktion, dess åtgärder är tillfälliga och de kan godkännas eller avvisas av transaktions-cmdletar som tillhandahålls av Windows PowerShell.

Läs mer om transaktioner, hur du stöd för transaktioner.

## <a name="transaction-provider"></a>Provider för transaktion

Du kan nu skapa leverantörer som kan användas i en transaktion. Liknar cmdlet: ar, när en leverantör används i en transaktion, dess åtgärder är tillfälliga och de kan godkännas eller avvisas av transaktions-cmdletar som tillhandahålls av Windows PowerShell.

Mer information om hur du anger stöd för transaktioner inom en providerklass finns i egenskapen System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Job-cmdlets

Du kan nu skriva cmdletar som kan utföra sina åtgärder som ett jobb. Dessa jobb körs i bakgrunden utan interaktion med den aktuella sessionen. Mer information om hur Windows PowerShell stöder se jobb, bakgrundsjobb.

## <a name="cmdlet-output-types"></a>Typer av cmdlet-utdata

Du kan nu ange vilka typer av .NET Framework som returneras av dina cmdlets genom att deklarera OutputType-attributet när du skriver dina cmdlets. Detta gör att andra ska kunna avgöra vilken typ av objekt som returneras av en cmdlet genom att titta på egenskapen OutputType för cmdlet: ar.

## <a name="event-support"></a>Händelsestöd för

Du kan nu skriva cmdletar som lägger till och använda händelser. Se PSEvent-klassen.

## <a name="proxy-commands"></a>Proxy-kommandon

Du kan nu skriva proxy-kommandon som kan användas för att köra ett annat kommando. En proxy-kommandot kan du kontrollera vilka funktioner för käll-cmdlet: en är tillgänglig för användaren. Du kan till exempel skapa en proxy-kommando som tar bort en parameter som tillhandahålls av kommandot källa. Se ProxyCommand-klassen.

## <a name="multiple-choice-prompts"></a>Anvisningarna för flera val

Du kan nu skriva program som kan ge anvisningarna som tillåter att användaren kan välja flera val. Se IHostUISupportsMultipleChoiceSelection-gränssnitt

## <a name="interactive-sessions"></a>Interaktiva sessioner

Du kan nu skriva program som kan starta och stoppa en interaktiv session på en fjärrdator.
Se IHostSupportsInteractiveSession-gränssnittet.

## <a name="custom-cmdlet-help-for-providers"></a>Anpassade Cmdlet-hjälpen för leverantörer

Nu kan du skapa anpassade hjälpavsnitten för provider-cmdletar. Anpassade hjälpämnen förklara hur cmdlet: en fungerar i de provider sökväg och dokumentet särskilda funktioner, inklusive de dynamiska parametrar som providern lägger till cmdleten.
