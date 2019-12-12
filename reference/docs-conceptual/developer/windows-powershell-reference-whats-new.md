---
title: Windows PowerShell-referens – nyheter
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356688"
---
# <a name="whats-new"></a>Nyheter

Windows PowerShell 2,0 innehåller följande nya funktioner som du kan använda när du skriver cmdlets, providers och värd program.

## <a name="modules"></a>Moduler

Nu kan du paketera och distribuera Windows PowerShell-lösningar med hjälp av moduler. Med moduler kan du partitionera, organisera och abstrakta din Windows PowerShell-kod i fristående, åter användnings bara enheter. Mer information om moduler finns i skriva en Windows PowerShell-modul.

## <a name="the-powershell-class"></a>PowerShell-klassen

PowerShell-klassen ger en enklare lösning för att skapa program som kallas värd program, som program mässigt kör kommandon. Med den här klassen kan du skapa en pipeline med kommandon, ange den körnings utrymme som används för att köra kommandona och ange att kommandona ska anropas synkront eller asynkront.

## <a name="the-runspacepool-class"></a>RunspacePool-klassen

Med körnings utrymme pooler kan du skapa flera körnings utrymmen med hjälp av ett enda anrop. Metoden CreateRunspacePool tillhandahåller flera överlagringar som kan användas för att skapa körnings utrymmen som har samma funktioner, till exempel samma värd, inledande sessionstillstånd och anslutnings information.

## <a name="the-initialsessionstate-class"></a>InitialSessionState-klassen

Med klassen InitialSessionState kan du skapa en konfiguration för sessionstillstånd som används när en körnings utrymme öppnas. Du kan skapa en anpassad konfiguration, en standard konfiguration som innehåller de kommandon som tillhandahålls av mshshort och en konfiguration vars kommandon är begränsade baserat på funktionerna i sessionen.

## <a name="remote-runspaces"></a>Fjärran körnings utrymmen

Nu kan du skapa körnings utrymmen som kan öppnas på fjärrdatorer, så att du kan köra kommandon på fjärrdatorn och samla in resultaten lokalt. Om du vill skapa en fjärran sluten körnings utrymme måste du ange information om fjärr anslutningen när du skapar körnings utrymme. Se metoderna CreateRunspace och CreateRunspacePool för exempel. Anslutnings informationen definieras av RunspaceConnectionInfo-klassen.

## <a name="private-runspace-elements"></a>Privata körnings utrymme-element

Nu kan du skapa körnings utrymmen vars element är offentliga eller privata. På så sätt kan du skapa körnings utrymmen vars element är tillgängliga för körnings utrymme, men som inte är tillgängliga för användaren. Se ConstrainedSessionStateEntry-klassen för att ta reda på vilka element i körnings utrymme som kan göras privata.

## <a name="runspace-threading-modes-and-apartment-state"></a>Körnings utrymme tråd lägen och lägenhets status

Nu kan du ange hur trådar skapas och används när du kör kommandon i en körnings utrymme. Se egenskaperna system. Management. Automation. körnings utrymmen. körnings utrymme. ThreadOptions och system. Management. Automation. körnings utrymmen. RunspacePool. ThreadOptions.

Du kan nu hämta Apartment-statusen för de trådar som används för att köra kommandon i en körnings utrymme. Se egenskaperna system. Management. Automation. körnings utrymmen. körnings utrymme. ApartmentState och system. Management. Automation. körnings utrymmen. RunspacePool. ApartmentState.

## <a name="transaction-cmdlets"></a>Transaktions-cmdletar

Nu kan du skapa cmdletar som kan användas i en transaktion. När en cmdlet används i en transaktion, är dess åtgärder temporära och de kan godkännas eller avvisas av transaktions-cmdletarna som tillhandahålls av Windows PowerShell.

Mer information om transaktioner finns i så här stöder du transaktioner.

## <a name="transaction-provider"></a>Transaction Provider

Nu kan du skapa providrar som kan användas i en transaktion. I likhet med cmdletar, när en provider används i en transaktion, är dess åtgärder temporära och de kan godkännas eller avvisas av transaktions-cmdletarna som tillhandahålls av Windows PowerShell.

Mer information om hur du anger stöd för transaktioner inom en leverantörs klass finns i egenskapen system. Management. Automation. Provider. CmdletProviderAttribute. ProviderCapabilities.

## <a name="job-cmdlets"></a>Jobb-cmdletar

Nu kan du skriva cmdletar som kan utföra åtgärden som ett jobb. Dessa jobb körs i bakgrunden utan att interagera med den aktuella sessionen. Mer information om hur Windows PowerShell stöder jobb finns i bakgrunds jobb.

## <a name="cmdlet-output-types"></a>Cmdlet-utdataformat

Nu kan du ange de .NET Framework typer som returneras av dina cmdlets genom att deklarera attributet OutputType när du skriver cmdletarna. Detta gör att andra kan avgöra vilken typ av objekt som returneras av en cmdlet genom att titta på egenskapen OutputType för cmdleten.

## <a name="event-support"></a>Händelse support

Nu kan du skriva cmdletar som lägger till och använder händelser. Se klassen PSEvent.

## <a name="proxy-commands"></a>Proxy-kommandon

Du kan nu skriva proxy-kommandon som kan användas för att köra ett annat kommando. Med ett kommando för proxy kan du kontrol lera vilka funktioner i käll-cmdlet: en som är tillgängliga för användaren. Du kan till exempel skapa ett proxy-kommando som tar bort en parameter som anges av käll kommandot. Se klassen ProxyCommand.

## <a name="multiple-choice-prompts"></a>Flera alternativ-prompter

Nu kan du skriva program som kan ge prompter som gör det möjligt för användaren att välja flera alternativ. Se IHostUISupportsMultipleChoiceSelection-gränssnittet

## <a name="interactive-sessions"></a>Interaktiva sessioner

Nu kan du skriva program som kan starta och stoppa en interaktiv session på en fjärrdator.
Se IHostSupportsInteractiveSession-gränssnittet.

## <a name="custom-cmdlet-help-for-providers"></a>Anpassad cmdlet-hjälp för providers

Nu kan du skapa anpassade hjälp avsnitt för provider-cmdletarna. I hjälp avsnitten om anpassad cmdlet kan du förklara hur cmdleten fungerar i providerns sökväg och dokumentera särskilda funktioner, inklusive de dynamiska parametrar som providern lägger till i cmdleten.
