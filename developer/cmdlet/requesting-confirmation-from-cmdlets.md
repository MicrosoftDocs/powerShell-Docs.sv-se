---
title: Begär bekräftelse från cmdletar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: ec441831f5e3231a44c9875d1b6d2bf6280a6965
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844991"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Begära bekräftelse från cmdlets

Cmdlet: ar bör begära bekräftelse när de är på väg att göra en ändring i systemet som ligger utanför Windows PowerShell-miljö. Till exempel om en cmdlet är håller på att lägga till ett användarkonto eller stoppa en process, kräver cmdleten bekräftelse från användaren innan den fortsätter. Däremot om en cmdlet är att ändra en Windows PowerShell-variabel, behöver cmdleten inte bekräftelse.

För att göra en begäran om händelsebekräftelse cmdlet: en anger att den stöder begäranden om händelsebekräftelse och den måste anropa den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (valfritt) metoder för att visa ett meddelande om bekräftelse på begäran.

## <a name="supporting-confirmation-requests"></a>Stöd för begäranden om Händelsebekräftelse

Cmdlet: en kan anges för begäranden om händelsebekräftelse måste den `SupportsShouldProcess` parametern för Cmdlet-attributet till `true`. På så sätt kan den `Confirm` och `WhatIf` cmdlet-parametrarna som tillhandahålls av Windows PowerShell. Den `Confirm` parameter gör det möjligt för användaren att styra om begäran om händelsebekräftelse ska visas. Den `WhatIf` parameter gör det möjligt för användaren för att avgöra om cmdlet: en ska visa ett meddelande eller utföra åtgärden. Lägg inte till manuellt i `Confirm` och `WhatIf` parametrar för att en cmdlet.

I följande exempel visas en deklaration av Cmdlet attribut som har stöd för begäranden om händelsebekräftelse.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Anropa metodbegäranden bekräftelse

I cmdlet-koden anropar den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden innan åtgärden som ändrar systemet utförs. Utforma cmdlet: en så att om anropet returnerar ett värde av `false`, är det inte att utföra åtgärden och cmdlet bearbetar nästa åtgärd.

## <a name="calling-the-shouldcontinue-method"></a>Att anropa metoden ShouldContinue

De flesta cmdletar begär bekräftelse via endast den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod. Ibland kan dock kräva ytterligare bekräftelse. Dessa fall kan komplettera den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropa med ett anrop till den [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod. På så sätt kan cmdlet eller provider för att få en mer detaljerad styra omfattningen av den **Ja till alla** svar på bekräfta åtgärden.

Om en cmdlet anropar den [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden cmdlet: en måste också tillhandahålla en `Force` växla parametern. Om användaren anger `Force` när du anropar cmdleten, cmdleten fortfarande ska anropa [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), men ska kringgås anropet till [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) genereras ett undantagsfel när den anropas från en icke-interaktiv miljö där användaren uppmanas inte. Att lägga till en `Force` parametern säkerställer att kommandot fortfarande kan utföras när den anropas i en icke-interaktiv miljö.

I följande exempel visas hur du anropar [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Beteendet för en [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrop kan variera beroende på miljön där cmdleten har anropats. Med hjälp av föregående riktlinjer hjälper att säkerställa att cmdleten fungerar konsekvent med andra cmdletar, oavsett värdmiljön.

Ett exempel på anropar den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod, se [hur du begär bekräftelser](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Ange effektnivå

När du skapar cmdleten, ange effektnivå (allvarlighetsgrad) av ändringen. Gör detta genom att ange värdet för den `ConfirmImpact` parametern för Cmdlet-attributet till hög, medel eller låg. Du kan ange ett värde för `ConfirmImpact` bara när du även ange den `SupportsShouldProcess` parametern för cmdleten.

För de flesta cmdletarna behöver du inte uttryckligen ange `ConfirmImpact`.  Använd istället standardinställningen för parametern, som är Medium. Om du ställer in `ConfirmImpact` till hög, kommer åtgärden att bekräftas som standard. Reservera den här inställningen för mycket störande åtgärder, till exempel formatera en volym på hårddisken.

## <a name="calling-non-confirmation-methods"></a>Anropa metoder för icke-bekräftelse

Om cmdlet eller providern måste skicka ett meddelande men inte begär bekräftelse, kan det anropa följande tre metoder. Undvik att använda den [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod för att skicka meddelanden av typerna eftersom [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) utdata är en med normala utdata från cmdleten eller din leverantör, vilket gör skriptet skriva svårt.

- Varning användaren och fortsätt med åtgärden genom cmdlet eller providern kan anropa den [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod.

- Ange ytterligare information som du kan hämta genom att använda den `Verbose` parametern, cmdlet eller providern kan anropa den [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod.

- För att ge felsökning detaljnivåer för andra utvecklare eller för produktsupport, cmdlet eller providern kan anropa den [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod. Användaren kan hämta den här informationen med hjälp av den `Debug` parametern.

Cmdlets och providers först anropa följande metoder för att begära bekräftelse innan de försöker utföra en åtgärd som ändrar ett system utanför Windows PowerShell:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

De gör det genom att anropa den [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod, som uppmanar användaren att bekräfta åtgärden baserat på hur användaren anropas kommandot.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
