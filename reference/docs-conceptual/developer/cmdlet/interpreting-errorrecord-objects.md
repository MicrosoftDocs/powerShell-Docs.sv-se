---
title: Tolka ErrorRecord-objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356219"
---
# <a name="interpreting-errorrecord-objects"></a>Tolka ErrorRecord-objekt

I de flesta fall representerar ett [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt ett icke-avslutande fel som genereras av ett kommando eller skript. Om du avslutar fel kan du också ange ytterligare information i en ErrorRecord via gränssnittet [system. Management. Automation. Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) .

Om du vill skriva en fel hanterare i skriptet eller en värd för att hantera vissa fel som inträffar under kommando-eller skript körningen måste du tolka objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) för att avgöra om det representerar klassen för fel som du vill hantera.

När en cmdlet påträffar ett avslutande eller icke-avslutande fel, ska den skapa en fel post som beskriver fel tillståndet. Värd programmet måste undersöka dessa fel poster och utföra de åtgärder som gör att felet minimeras. Värd programmet måste också undersöka fel poster för fel som inte kan bearbeta en post, men som kan fortsätta, och det måste undersöka fel poster för att avsluta fel som orsakade att pipelinen stoppades.

> [!NOTE]
> För att avbryta fel anropar cmdleten metoden [system. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . För icke-avslutande fel anropar cmdleten metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) .

## <a name="error-record-design"></a>Fel vid post design

Fel poster är utformade för att ge ytterligare fel information som inte är tillgänglig i undantags syfte och som säkerställer att den kombinerade informationen i varje fel post är unik. Den här unikheten gör att värd programmet kan kontrol lera de olika delarna av fel posten så att de kan identifiera fel tillståndet och den åtgärd som måste vidtas av värden.

## <a name="interpreting-error-records"></a>Tolka fel poster

Du kan granska flera delar av fel posten för att identifiera felet. Dessa delar innehåller följande:

- Fel kategorin

- Fel undantaget

- Den fullständigt kvalificerade fel identifieraren (FQID)

- Annan information

### <a name="the-error-category"></a>Fel kategorin

Fel kategorin för fel posten är en av de fördefinierade konstanterna som tillhandahålls av uppräkningen [system. Management. Automation. Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Den här informationen är tillgänglig via egenskapen [system. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) för objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Cmdleten kan ange CloseError-, OpenError-, InvalidType-, ReadError-och WriteError-kategorierna och andra fel kategorier. Värd programmet kan använda fel kategorin för att avbilda grupper av fel.

### <a name="the-exception"></a>Undantaget

Undantaget som ingår i fel posten tillhandahålls av cmdleten och kan nås via egenskapen [system. Management. Automation. ErrorRecord. Exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) för objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Värd program kan använda nyckelordet `is` för att identifiera att undantaget är en speciell klass eller en härledd klass. Det är bättre att förgrena över undantags typen, som visas i följande exempel.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

På så sätt fångar du de härledda klasserna. Det finns dock problem om undantaget avserialiseras.

### <a name="the-fqid"></a>FQID

FQID är den mest detaljerade information som du kan använda för att identifiera felet. Det är en sträng som innehåller en cmdlet-definierad identifierare, namnet på cmdlet-klassen och källan som rapporterade felet. I allmänhet är en fel post analog till en händelse post i en händelse logg i Windows. FQID är detsamma som i följande tupel, som identifierar klassen för händelse posten: (*logg namn*, *källa*, *händelse-ID*).

FQID är utformad för att kontrol leras som en enskild sträng. Det finns dock fall där fel identifieraren är utformad för att kunna parsas av värd programmet. Följande exempel är ett välformulerat fullständigt fel-ID.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

I föregående exempel är den första token fel identifieraren, som följs av namnet på cmdlet-klassen. Fel identifieraren kan vara en enskild token, eller så kan den vara en punktavgränsad identifierare som gör det möjligt att kontrol lera identifieringen av identifieraren. Använd inte blank steg eller interpunktion i fel identifieraren. Det är särskilt viktigt att inte använda ett kommatecken. ett kommatecken används av Windows PowerShell för att avgränsa identifieraren och cmdlet-klassens namn.

### <a name="other-information"></a>Annan information

Objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) kan också innehålla information som beskriver miljön där felet uppstod. Den här informationen omfattar objekt som fel information, information om anrop och det mål objekt som bearbetades när felet uppstod. Även om den här informationen kan vara användbar för värd programmet, används vanligt vis inte för att identifiera felet. Den här informationen är tillgänglig via följande egenskaper:

[System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System. Management. Automation. ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System. Management. Automation. ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Se även

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Lägga till icke-avslutande fel rapportering till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell fel rapportering](./error-reporting-concepts.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
