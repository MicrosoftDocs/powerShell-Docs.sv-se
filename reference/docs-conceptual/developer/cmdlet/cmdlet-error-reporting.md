---
title: Fel rapportering för cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356569"
---
# <a name="cmdlet-error-reporting"></a>Fel rapportering för cmdlet

-Cmdletar bör rapportera fel på olika sätt beroende på om felen avslutar fel eller om fel inte avslutas. Att avsluta fel är fel som leder till att pipelinen avslutas omedelbart eller fel som inträffar när det inte finns någon anledning att fortsätta att bearbeta. Fel som inte avslutas är de fel som rapporterar ett aktuellt fel tillstånd, men cmdleten kan fortsätta att bearbeta inobjekten. Om det inte finns några fel, meddelas användaren vanligt vis om problemet, men cmdleten fortsätter att bearbeta nästa indata-objekt.

## <a name="terminating-and-nonterminating-errors"></a>Avsluta och avbryta fel

Följande rikt linjer kan användas för att avgöra om ett fel tillstånd är ett avslutande fel eller ett fel som inte kan avslutas.

- Hindrar fel villkoret att din cmdlet bearbetar ytterligare indata-objekt? I så fall är det ett avslutande fel.

- Är fel tillståndet relaterat till ett speciellt indatamängds objekt eller en delmängd av inobjekten? Om så är fallet, är det ett fel som inte avslutas.

- Accepterar cmdleten flera indata, så att bearbetningen kan lyckas på ett annat indata-objekt? Om så är fallet, är det ett fel som inte avslutas.

- -Cmdletar som kan acceptera flera inobjekt bör bestämma mellan vad som avslutas och inte avslutande fel, även om en viss situation endast gäller för ett enda inobjekt.

- Cmdletar kan ta emot valfritt antal inobjekt och skicka valfritt antal lyckade eller felaktiga objekt innan ett avslutande undantag utlöses. Det finns ingen relation mellan antalet mottagna inobjekt och antalet lyckade och felaktiga objekt som har skickats.

- Cmdletar som bara kan acceptera 0-1-indata-objekt och endast genererar 0-1-utdatafiler bör behandla fel som avslutas och generera undantags fel.

## <a name="reporting-nonterminating-errors"></a>Rapportera fel som inte avslutas

Rapportering av ett fel som inte avslutas bör alltid utföras inom cmdletens implementering av metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) eller metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Dessa typer av fel rapporteras genom att anropa metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , som i sin tur skickar en felpost till fel strömmen.

## <a name="reporting-terminating-errors"></a>Rapportera avslutande fel

Avslutande fel rapporteras genom att Utlös ande undantag eller genom att anropa metoden [system. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Tänk på att cmdlets också kan fånga upp och återanvända undantag, till exempel **OutOfMemory**, men de behöver inte rethrowa undantag eftersom PowerShell-körningen även kommer att fånga dem.

Du kan också definiera egna undantag för problem som är specifika för din situation eller lägga till ytterligare information i ett befintligt undantag med hjälp av fel posten.

## <a name="error-records"></a>Fel poster

PowerShell Beskriver ett fel tillstånd som inte avslutas med [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt. Varje-objekt innehåller information om fel kategori, ett valfritt mål objekt och information om fel tillståndet.

### <a name="error-identifiers"></a>Fel identifierare

Fel identifieraren är en enkel sträng som identifierar fel tillståndet i cmdleten.
PowerShell kombinerar den här identifieraren med en cmdlet-identifierare för att skapa en fullständigt kvalificerad fel identifierare som kan användas senare vid filtrering av fel strömmar eller loggnings fel, vid svar på särskilda fel eller med andra användarspecifika aktiviteter.

Följande rikt linjer bör följas när du anger fel identifierare:

- Tilldela olika kod Sök vägar olika, mycket detaljerade Varje kod Sök väg som anropar [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [system. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ska ha en egen fel identifierare.

- Fel identifierare ska vara unika för CLR-typer (Common Language Runtime) för både avslutande och inte avslutande fel.

- Ändra inte semantiken för en fel identifierare mellan versioner av cmdleten eller PowerShell-providern. När semantiken för en fel identifierare har upprättats bör den vara konstant under hela livs cykeln för din cmdlet.

- Om du vill avbryta fel använder du en unik fel identifierare för en viss CLR-undantags typ. Om undantags typen ändras använder du en ny fel-ID.

- Använd en unik fel identifierare för ett bestämt inobjekt för att avbryta fel.

- Välj text för den identifierare som tersely motsvarar det fel som rapporteras. Använd inte blank steg eller skiljetecken.

- Generera inte fel identifierare som inte är nyproducerade. Generera till exempel inte identifierare som innehåller en process identifierare. Fel identifierare är bara användbara när de motsvarar identifierare som visas av andra användare som har samma problem.

### <a name="error-categories"></a>Fel kategorier

Fel kategorier används för att gruppera fel för användaren. PowerShell definierar dessa kategorier och cmdlets och PowerShell-leverantörer måste välja mellan dem när fel posten skapas.

En beskrivning av de fel kategorier som är tillgängliga finns i uppräkningen [system. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . I allmänhet bör du undvika att använda **noerror**, **UndefinedError**och **GenericError** när det är möjligt.

Användare kan visa fel baserat på kategori när de anger `$ErrorView` till **CategoryView**.

## <a name="see-also"></a>Se även

[Cmdlet-översikt](./cmdlet-overview.md)

[Typer av cmdlet-utdata](./types-of-cmdlet-output.md)

[Windows PowerShell-referens](../windows-powershell-reference.md)
