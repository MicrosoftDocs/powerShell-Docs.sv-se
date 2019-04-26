---
title: Tolka ErrorRecord objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067645"
---
# <a name="interpreting-errorrecord-objects"></a>Tolka ErrorRecord-objekt

I de flesta fall en [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objektet representerar en icke-avslutande fel som genereras av ett kommando eller skript. Avslutande fel kan också ange ytterligare information i en ErrorRecord via den [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) gränssnitt.

Om du vill skriva ett Felhanteraren i ditt skript eller en värden för att hantera fel som har inträffat vid körning av kommandot eller skriptet, måste du tolka den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objektet för att avgöra om den representerar klassen för fel som du vill hantera.

När en cmdlet påträffar avslutande eller icke-avslutande fel, bör den skapa en Felpost som beskriver felet. Värdprogrammet måste undersöka dessa felposter och utföra åtgärder värduppdateringarna åtgärdar felet. Värdprogrammet måste också undersöka felposter för oändliga fel som kunde inte bearbeta en post, men kunde fortsätta och den måste undersöka felposter avslutande fel som orsakade att stoppa pipelinen.

> [!NOTE]
> Avslutande fel cmdleten anropar den [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metod. För icke-avslutande fel cmdleten anropar den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod.

## <a name="error-record-design"></a>Fel poster Design

Felposter är utformad att ge ytterligare felinformation som inte är tillgänglig i undantag samtidigt som man säkerställer att kombinerade informationen i varje Felpost är unikt. Den här unikhet kan värdprogrammet granska de olika delarna i en Felpost så att den kan identifiera felet och måste vidta åtgärden värden.

## <a name="interpreting-error-records"></a>Tolka felposter

Du kan granska flera olika delar av felposten som ska identifiera felet. Dessa delar är följande:

- Felkategori

- Felundantag

- Det fullständigt kvalificerade fel ID: t (FQID)

- Annan information

### <a name="the-error-category"></a>Felkategori

Kategorin fel på en Felpost är en av de fördefinierade konstanterna som tillhandahålls av den [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) uppräkning. Den här informationen är tillgänglig via den [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) egenskapen för den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt.

Cmdlet: en kan ange CloseError, OpenError, InvalidType, ReadError och WriteError kategorier och andra felkategorier. Värdprogrammet kan använda kategorin fel för att samla in grupper med fel.

### <a name="the-exception"></a>Undantaget

Undantag som ingår i en Felpost tillhandahålls av cmdlet: en och kan nås via den [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) egenskapen för den [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt.

Vara värd för program kan använda den `is` nyckelordet identifiera att undantaget är i en viss klass eller i en härledd klass. Det är bättre att branch på undantagstyp, som visas i följande exempel.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

På så sätt kan du fånga härledda klasser. Det finns dock problem om undantaget avserialiseras.

### <a name="the-fqid"></a>FQID

FQID är den mest specifik information som du kan använda för att identifiera felet. Det är en sträng som innehåller en cmdlet-definierade identifierare, namnet på klassen cmdlet och källan som rapporterade fel. I allmänhet är en Felpost detsamma som en händelsepost för en Windows-händelseloggen. FQID är detsamma som följande tuppel, som identifierar klassen till händelseposten: (*loggnamn*, *källa*, *händelse-ID*).

FQID har utformats för att granskas som en sträng. Dock finnas fall där det fel-ID: t är utformat för att tolkas av värdprogrammet. I följande exempel är en korrekt strukturerad fullständiga fel-identifierare.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

I exemplet ovan är den första token fel-ID, som följs av namnet på klassen cmdlet. Fel-ID kan vara en enskild token eller det kan vara en punkt-avgränsade identifierare som tillåter förgreningar enligt om kontroll av identifierare. Använd inte blanksteg eller skiljetecken i fel-identifierare. Det är särskilt viktigt att inte använda ett kommatecken; ett kommatecken används av Windows PowerShell för att avgränsa identifierare och klassnamn cmdlet.

### <a name="other-information"></a>Annan Information

Den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt också innehålla information som beskriver den miljö där felet inträffade. Den här informationen innehåller sådant som felinformation och anrop information målobjektet som behandlades när felet inträffade. Även om den här informationen kan vara praktiskt att värdprogrammet, är det inte vanligt att identifiera felet. Den här informationen är tillgänglig via följande egenskaper:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Se även

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Att lägga till icke-avslutande fel som rapporterar till cmdlet:](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Felrapportering för Windows PowerShell](./error-reporting-concepts.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
