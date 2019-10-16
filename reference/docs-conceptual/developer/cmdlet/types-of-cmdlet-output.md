---
title: Typer av cmdlet-utdata | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359184"
---
# <a name="types-of-cmdlet-output"></a>Typer av cmdlet-utdata

PowerShell tillhandahåller flera metoder som kan anropas av cmdlets för att generera utdata. Dessa metoder använder en speciell åtgärd för att skriva utdata till en speciell data ström, till exempel data strömmen eller fel data strömmen. I den här artikeln beskrivs de olika typerna av utdata och de metoder som används för att generera dem.

## <a name="types-of-output"></a>Typer av utdata

### <a name="success-output"></a>Lyckade utdata

-Cmdletar kan rapportera framgång genom att returnera ett objekt som kan bearbetas av nästa kommando i pipelinen. När cmdleten har slutfört åtgärden anropar cmdleten metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Vi rekommenderar att du anropar den här metoden i stället för metoderna [system. Console. WriteLine](/dotnet/api/System.Console.WriteLine) eller [system. Management. Automation. Host. PSHostUserInterface. WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) .

Du kan ange en **Passthru** växel parameter för cmdletar som vanligt vis inte returnerar objekt.
När växel parametern **Passthru** anges på kommando raden uppmanas cmdleten att returnera ett objekt. Ett exempel på en-cmdlet som har en **Passthru** -parameter finns i [Lägg till-historik](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Fel utdata

Cmdlets kan rapportera fel. När ett avbrotts fel inträffar genererar cmdleten ett undantag. När ett icke-avslutande fel inträffar anropar cmdleten metoden [system. Management. Automation. Provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) för att skicka en fel post till fel data strömmen. Mer information om fel rapportering finns i [fel rapporterings koncept](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Utförlig utdata

Cmdletar kan ge värdefull information till dig medan cmdleten bearbetar poster korrekt genom att anropa metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) . Metoden genererar utförliga meddelanden som visar hur åtgärden fortsätter.

Som standard visas inte utförliga meddelanden. Du kan ange **verbose** -parametern när cmdleten körs för att visa dessa meddelanden. **Verbose** är en gemensam parameter som är tillgänglig för alla cmdletar.

### <a name="progress-output"></a>Förlopps utdata

-Cmdletar kan tillhandahålla information om förloppet när cmdleten utför aktiviteter som tar lång tid att slutföra, till exempel kopiering av en katalog rekursivt. För att Visa förlopps information anropar cmdleten metoden [system. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

### <a name="debug-output"></a>Fel söknings utdata

Cmdlets kan ge fel söknings meddelanden som är användbara vid fel sökning av cmdlet-koden. För att Visa felsöknings information anropar cmdleten metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) .

Som standard visas inte fel söknings meddelanden. Du kan ange parametern **Felsök** när cmdleten körs för att visa dessa meddelanden. **Debug** är en gemensam parameter som är tillgänglig för alla cmdletar.

### <a name="warning-output"></a>Varnings resultat

Cmdletar kan visa varnings meddelanden genom att anropa metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

Varnings meddelanden visas som standard. Du kan dock konfigurera varnings meddelanden med hjälp av variabeln `$WarningPreference` eller med hjälp av parametrarna **verbose** och **Debug** när cmdleten anropas.

## <a name="displaying-output"></a>Visar utdata

För alla Skriv metods anrop bestäms innehålls visningen av vissa körnings variabler. Undantaget är metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Genom att använda dessa variabler kan du göra ett lämpligt Skriv anrop på rätt plats i koden och inte bekymra dig om när eller om utdata ska visas.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Åtkomst till utmatnings funktionen för ett värd program

Du kan också utforma en cmdlet för att direkt komma åt utmatnings funktionen för ett värd program via PowerShell-körningen. Med hjälp av de värd-API: er som tillhandahålls av PowerShell i stället för [system. Console](/dotnet/api/System.Console) eller [system. Windows. Forms](/dotnet/api/System.Windows.Forms) säkerställer du att cmdleten fungerar med en mängd olika värdar. Till exempel: **PowerShell. exe** -konsolens värd, den grafiska **powershell_ise. exe** -värden, PowerShell-fjärrkörnings värden och värdar från tredje part.

## <a name="see-also"></a>Se även

[Fel rapporterings begrepp](./error-reporting-concepts.md)

[Cmdlet-översikt](./cmdlet-overview.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)