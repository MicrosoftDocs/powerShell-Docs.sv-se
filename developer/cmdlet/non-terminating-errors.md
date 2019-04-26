---
title: Icke-avslutande fel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067662"
---
# <a name="non-terminating-errors"></a>Fel som inte avbryter körningen

Det här avsnittet beskrivs den metod som används för att rapportera icke-avslutande fel. Den behandlar också hur du anropar metoden från cmdlet: en.

När ett icke-avslutande fel inträffar, cmdleten ska rapportera det här felet genom att anropa den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod. När cmdleten visar ett icke-avslutande fel, cmdleten fortsätter att fungera på den här indataobjektet och ytterligare inkommande pipeline-objekt. Om cmdleten anropar den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoden cmdlet: en kan skriva en Felpost som beskriver den situation som orsakade icke avslutande fel. Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).

Cmdlet: ar kan anropa [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) vid behov från inom sin syn metoderna. Dock cmdlets kan anropa [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) endast från den tråd som kallas den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), eller [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) indatametod för bearbetning. Anropa inte [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från en annan tråd. I stället kommunicera fel tillbaka till huvudtråden.

## <a name="see-also"></a>Se även

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
