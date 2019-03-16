---
title: Avslutande fel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059243"
---
# <a name="terminating-errors"></a>Fel som avbryter körningen

Det här avsnittet beskrivs den metod som används för att rapportera avslutande fel. Den behandlar också hur du anropar metoden från cmdlet: en och den beskriver de undantag som kan returneras av Windows PowerShell-körningen när metoden anropas.

När ett avslutande fel inträffar, cmdleten ska rapportera felet genom att anropa den [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metod. Den här metoden kan cmdleten för att skicka en Felpost som beskriver den situation som orsakade det avslutande felet. Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).

När den [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metoden anropas, Windows PowerShell-runtime permanent stoppar körningen av pipelinen och genererar en [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) undantag. Alla efterföljande försök att anropa [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), eller flera andra API: er gör dessa anrop till utlöser en [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) undantag.

Den [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) undantag kan också inträffa om en annan cmdlet i pipelinen rapporterar ett avslutande fel om användaren har bett att stoppa pipelinen, eller om pipelinen har stoppats innan du slutförande av någon anledning. Cmdlet: en inte behöver se den [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) undantag såvida inte den rensning öppna resurser eller det interna tillståndet.

Cmdlet: ar kan skriva valfritt antal utdata objekt eller icke-avslutande fel innan den rapporterar ett avslutande fel. Men det avslutande felet slutar permanent pipelinen och inga ytterligare utdata, avslutande fel, eller icke-avslutande fel rapporteras.

Cmdlet: ar kan anropa [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) endast från den tråd som kallas den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), eller [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) indatametod för bearbetning. Försök inte att anropa [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) eller [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från en annan tråd. Fel måste i stället lämnas tillbaka till huvudtråden.

Det är möjligt för en cmdlet utlöser ett undantag genomför den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), eller [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod. Alla undantag som genereras från dessa metoder (förutom några allvarligt feltillstånd som stoppar Windows PowerShell-värd) tolkas som ett avslutande fel som stoppar pipeline, men inte Windows PowerShell som helhet. (Detta gäller endast för den huvudsakliga cmdlet-tråden. Undantagsfel i trådar som skapade av cmdlet: en, stoppa i allmänhet Windows PowerShell-värd.) Vi rekommenderar att du använder [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) i stället för undantagsfel eftersom en Felpost tillhandahåller ytterligare information om felet, vilket är användbart att slutanvändaren. Cmdlet: ar bör respektera riktlinjen förvaltad kod mot identifiering och hantering av alla undantag (`catch (Exception e)`). Konvertera endast undantag av kända och förväntade typer till felposter.

## <a name="see-also"></a>Se även

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
