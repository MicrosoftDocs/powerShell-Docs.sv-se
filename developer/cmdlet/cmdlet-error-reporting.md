---
title: Cmdlet-felrapportering | Microsoft Docs
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
ms.openlocfilehash: 7b54fc220a66a47c25b3e8cba644882d31713cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847994"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet-felrapportering

Cmdlet: ar bör rapportera fel på olika sätt beroende på om felen avslutande fel eller oändliga fel. Avslutande fel är fel som gör att avslutas omedelbart pipelinen eller fel som uppstår när det finns ingen anledning att fortsätta bearbetningen. Oändliga fel är dessa fel som rapporterar ett aktuella feltillstånd, men cmdlet: en kan fortsätta att bearbeta inkommande objekt. Normalt meddelas användaren om problemet med oändliga fel, men cmdleten fortsätter att bearbeta nästa inkommande objekt.

## <a name="terminating-and-nonterminating-errors"></a>Avslutande och oändliga fel

Följande riktlinjer kan användas för att avgöra om ett feltillstånd är ett avslutande fel eller ett oändliga fel.

- Felet hindrar din cmdlet bearbetar eventuella ytterligare indata objekt? I så, fall är detta ett avslutande fel.

- Beror felet på ett visst inkommande objekt eller en delmängd av inkommande objekt? I så, fall är detta ett oändliga fel.

- Cmdlet: en tar emot flera inkommande objekt, till exempel att bearbetningen kan fungera i en annan indataobjektet? I så, fall är detta ett oändliga fel.

- Cmdletar som kan acceptera flera inkommande objekt ska välja mellan vad avslutas och oändliga fel, även när en viss situation gäller bara en enda indataobjektet.

- Cmdlet: ar kan ta emot valfritt antal inkommande objekt och skicka valfritt antal objekt som slutfört eller fel innan du utlöser ett avslutande undantag. Det finns ingen relation mellan antal inkommande objekt som tagits emot och antalet lyckade och fel objekt skickas.

- Cmdletar som kan acceptera bara 0 – 1 indata objekt och generera bara 0 – 1 utdata objekt ska hantera fel som avslutande fel och generera avslutande undantag.

## <a name="reporting-nonterminating-errors"></a>Rapportering oändliga fel

Rapportering av ett oändliga fel ska endast göras inom cmdletens implementering av den [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metoden den [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden eller [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod. Dessa typer av fel rapporteras genom att anropa den [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod som i sin tur skickar en Felpost till felströmmen.

## <a name="reporting-terminating-errors"></a>Rapporterat avslutande fel

Avslutande fel som rapporteras genom att utlösa undantag eller genom att anropa den [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metod. Tänk på att cmdletarna kan även fånga upp och igen utlöser undantag, till exempel OutOfMemory, men de behöver inte igen detta görs som Windows PowerShell-runtime ska fånga upp dem också.

Du kan även definiera dina egna undantag för problem som är specifika för din situation eller lägga till ytterligare information till en befintlig undantag med dess Felpost.

## <a name="error-records"></a>Felposter

Windows PowerShell beskriver ett oändliga feltillstånd med [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt. Varje [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objektet innehåller information om fel, en valfri målobjektet och information om felet.

### <a name="error-identifiers"></a>Fel-ID

Fel-ID: t är en enkel sträng som identifierar feltillstånd i cmdleten. Windows PowerShell kombinerar den här identifieraren för en cmdlet-identifierare för att skapa ett fullständigt fel-ID som kan användas senare när du filtrerar felströmmar eller logga fel vid svar på specifika fel eller med andra användarspecifika aktiviteter.

Följande riktlinjer ska följas när du anger fel-ID.

- Tilldela olika kodsökvägar olika, specifika, fel-ID: n. Varje kodsökväg som anropar [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ska ha sin egen fel-identifierare.

- Fel-ID måste vara unikt för CLR-undantagstyper för både avslutande och oändliga fel.

- Ändra inte semantiken för en identifierare som fel mellan versioner av dina cmdlet eller Windows PowerShell-providern. När semantiken för ett fel-ID har upprättats, bör det förblir konstant under hela livscykeln för cmdlet:.

- Använd ett unikt fel-ID för en viss typ av CLR-undantag för avslutande fel. Om undantagstyp ändras, använder du en ny fel-identifierare.

- För oändliga fel, kan du använda ett specifikt fel-ID för ett specifikt objekt som indata.

- Välj text för identifierare som motsvarar tersely fel har rapporterats. Använd inte blanksteg eller skiljetecken.

- Generera inte fel-ID som inte är reproducerbar. Till exempel generera inte identifierare som innehåller ett process-ID. Fel-ID är användbara endast när de motsvarar identifierare som ses av andra användare som upplever samma problem.

### <a name="error-categories"></a>Felkategorier

Felkategorier använder för att gruppera fel för slutanvändaren. Windows PowerShell definierar dessa kategorier och cmdlets och providers för Windows PowerShell måste välja mellan dem när du genererar en Felpost.

En beskrivning av felet kategorier som är tillgängliga finns i den [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) uppräkning. I allmänhet bör du undvika att använda NoError och UndefinedError GenericError när det är möjligt.

Användare kan visa fel baserat på kategori när de har ”`$ErrorView`” till ”CategoryView”.

## <a name="see-also"></a>Se även

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Cmdlet-utdata](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
