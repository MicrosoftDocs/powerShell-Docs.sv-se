---
title: Avsluta fel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359206"
---
# <a name="terminating-errors"></a>Fel som avbryter körningen

I det här avsnittet beskrivs den metod som används för att rapportera avslutande fel. Den beskriver också hur du anropar-metoden från cmdleten och diskuterar undantagen som kan returneras av Windows PowerShell-körningsmiljön när metoden anropas.

När ett avbrotts fel inträffar ska cmdleten rapportera felet genom att anropa metoden [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Den här metoden gör att cmdleten kan skicka en felpost som beskriver det villkor som orsakade det avslutande felet. Mer information om fel poster finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).

När metoden [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) anropas, stoppas körningen av pipelinen permanent i Windows PowerShell-körningsmiljön och ett [system. Management. Automation. PipelineStoppedException](/dotnet/api/System.Management.Automation.PipelineStoppedException) -undantag genereras. Eventuella efterföljande försök att anropa [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)eller flera andra API: er medför att dessa anrop genererar ett [system. Management. Automation. PipelineStoppedException](/dotnet/api/System.Management.Automation.PipelineStoppedException) -undantag.

Undantags felet [system. Management. Automation. PipelineStoppedException](/dotnet/api/System.Management.Automation.PipelineStoppedException) kan också inträffa om en annan cmdlet i pipeline rapporterar ett avslutande fel, om användaren har bett att stoppa pipelinen eller om pipelinen har stoppats innan den slutförts av någon anledning. Cmdleten behöver inte fånga upp undantaget [system. Management. Automation. PipelineStoppedException](/dotnet/api/System.Management.Automation.PipelineStoppedException) , om det inte måste rensas öppna resurser eller det interna läget.

Cmdletar kan skriva valfritt antal utgående objekt eller icke-avslutande fel innan ett avslutande fel rapporteras. Det avslutande felet stoppar dock pipelinen permanent och inga ytterligare utdata, avslutande fel eller icke-avslutande fel kan rapporteras.

-Cmdletar kan anropa [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) endast från den tråd som anropade metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)eller [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) för bearbetnings metoden för indata. Försök inte anropa [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) eller [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från en annan tråd. I stället måste fel förmedlas tillbaka till huvud tråden.

Det är möjligt att en cmdlet genererar ett undantag i dess implementering av metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [system. Management. Automation.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)cmdlet. ProcessRecord eller [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Alla undantag som har utlösts av dessa metoder (förutom några allvarliga fel villkor som stoppar Windows PowerShell-värden) tolkas som ett avslutande fel som stoppar pipelinen, men inte Windows PowerShell som helhet. (Detta gäller endast för huvud-cmdlet-tråden. Ej fångade undantag i trådar som har skapats av cmdleten, i allmänhet, stoppar Windows PowerShell-värden.) Vi rekommenderar att du använder [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) i stället för att generera ett undantag eftersom fel posten innehåller ytterligare information om fel tillståndet, vilket är användbart för slutanvändaren. Cmdlets bör respektera den hanterade kod rikt linjen för att fånga och hantera alla undantag (`catch (Exception e)`). Konvertera endast undantag av kända och förväntade typer till fel poster.

## <a name="see-also"></a>Se även

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. PipelineStoppedException](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
