---
ms.date: 09/13/2016
ms.topic: reference
title: Begära bekräftelse från cmdlets
description: Begära bekräftelse från cmdlets
ms.openlocfilehash: fd869d50b185cb4d38269640df58ec284a32da50
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646410"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Begära bekräftelse från cmdlets

Cmdlets bör begära bekräftelse när de ska göra en ändring i systemet som ligger utanför Windows PowerShell-miljön. Om en cmdlet till exempel ska lägga till ett användar konto eller stoppa en process, måste cmdleten kräva bekräftelse från användaren innan den kan fortsätta. Om en cmdlet är i färd med att ändra en Windows PowerShell-variabel behöver cmdleten däremot inte kräva bekräftelse.

För att kunna göra en bekräftelse förfrågan måste cmdleten ange att den stöder bekräftelse begär Anden och måste anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (valfritt) för att visa ett bekräftelse meddelande.

## <a name="supporting-confirmation-requests"></a>Support bekräftelse begär Anden

För att stödja bekräftelse begär Anden måste cmdleten ange `SupportsShouldProcess` parametern för cmdlet-attributet till `true` . Detta aktiverar `Confirm` parametrarna och för `WhatIf` cmdleten som tillhandahålls av Windows PowerShell. `Confirm`Parametern gör det möjligt för användaren att kontrol lera om bekräftelse förfrågningen visas. `WhatIf`Parametern låter användaren avgöra om cmdleten ska visa ett meddelande eller utföra åtgärden. Lägg inte till `Confirm` parametrarna och manuellt `WhatIf` i en cmdlet.

I följande exempel visas en deklaration för cmdlet-attribut som stöder bekräftelse begär Anden.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Anropar metoder för bekräftelse av begäran

I cmdlet-koden anropar du metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) innan åtgärden som ändrar systemet utförs. Utforma cmdleten så att om anropet returnerar värdet `false` , utförs inte åtgärden och cmdleten bearbetar nästa åtgärd.

## <a name="calling-the-shouldcontinue-method"></a>Anropar metoden ShouldContinue

De flesta cmdletar begär bekräftelse med hjälp av metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Vissa fall kan dock kräva ytterligare bekräftelse. I dessa fall ska du komplettera [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -anropet med ett anrop till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Detta gör att cmdleten eller providern kan styra omfånget för **Ja till alla** svar på bekräftelse meddelandet.

Om en cmdlet anropar metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , måste cmdleten också tillhandahålla en `Force` switch-parameter. Om användaren anger `Force` när användaren anropar cmdleten bör cmdleten fortfarande anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), men det bör kringgå anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) kommer att utlösa ett undantag när det anropas från en icke-interaktiv miljö där användaren inte kan uppmanas att göra det. Genom att lägga till en `Force` parameter ser du till att kommandot fortfarande kan utföras när det anropas i en icke-interaktiv miljö.

Följande exempel visar hur du anropar [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Beteendet för ett [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -anrop kan variera beroende på i vilken miljö cmdleten anropas. Genom att följa de tidigare rikt linjerna kan du se till att cmdleten fungerar konsekvent med andra cmdlets, oavsett värd miljö.

Ett exempel på hur du anropar metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) finns i [så här begär du bekräftelser](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Ange effekt nivå

När du skapar cmdleten anger du effekt nivån (allvarlighets grad) för ändringen. Det gör du genom att ange värdet för `ConfirmImpact` parametern för cmdlet-attributet till hög, medel eller låg. Du kan endast ange ett värde för `ConfirmImpact` när du också anger `SupportsShouldProcess` parametern för cmdleten.

För de flesta cmdletar behöver du inte uttryckligen ange `ConfirmImpact` .  Använd istället standard inställningen för parametern, som är medel. Om du ställer in `ConfirmImpact` till hög bekräftas åtgärden som standard. Reservera den här inställningen för mycket störande åtgärder, till exempel att omformatera en hård disk volym.

## <a name="calling-non-confirmation-methods"></a>Anropar icke-bekräftelse metoder

Om cmdleten eller providern måste skicka ett meddelande, men inte begära bekräftelse, kan det anropa följande tre metoder. Undvik att använda metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) för att skicka meddelanden av dessa typer eftersom utdata för [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) är blandas med den normala utmatningen av din cmdlet eller provider, vilket gör det svårt att skriva skript.

- För att varna användaren och fortsätta med åtgärden kan cmdleten eller providern anropa metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

- Om du vill ange ytterligare information som användaren kan hämta med hjälp av `Verbose` -parametern kan cmdleten eller providern anropa metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

- För att ge information om fel söknings nivå för andra utvecklare eller för produkt support kan cmdleten eller providern anropa metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . Användaren kan hämta den här informationen med hjälp av `Debug` parametern.

Cmdlets och providers anropar först följande metoder för att begära bekräftelse innan de försöker utföra en åtgärd som ändrar ett system utanför Windows PowerShell:

- [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

De gör detta genom att anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , som gör att användaren kan bekräfta åtgärden baserat på hur användaren anropade kommandot.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
