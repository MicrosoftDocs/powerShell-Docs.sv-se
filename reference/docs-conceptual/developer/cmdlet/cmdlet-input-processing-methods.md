---
ms.date: 09/13/2016
ms.topic: reference
title: Bearbetningsmetoder för cmdlet-indata
description: Bearbetningsmetoder för cmdlet-indata
ms.openlocfilehash: e1a7b58517d6285250edbf16d14810388c242218
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653388"
---
# <a name="cmdlet-input-processing-methods"></a>Bearbetningsmetoder för cmdlet-indata

Cmdletar måste åsidosätta en eller flera av de metoder för bearbetning av indata som beskrivs i det här avsnittet för att utföra sitt arbete.
Dessa metoder tillåter att cmdleten utför åtgärder för för bearbetning, bearbetning av indata och efter bearbetning.
Med dessa metoder kan du även stoppa cmdlet-bearbetning.
Ett mer detaljerat exempel på hur du använder dessa metoder finns i [självstudier om SelectStr](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>För bearbetnings åtgärder

-Cmdletar ska åsidosätta metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för att lägga till eventuella för bearbetnings åtgärder som är giltiga för alla poster som ska bearbetas senare av cmdleten.
När PowerShell bearbetar en kommando pipeline anropar PowerShell denna metod en gång för varje instans av cmdlet: en i pipelinen.
Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).

Följande kod visar en implementering av BeginProcessing-metoden.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Åtgärder för bearbetning av aktiviteter

-Cmdletar kan åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att bearbeta InInformationen som skickas till cmdleten.
När PowerShell bearbetar en kommando pipeline anropar PowerShell den här metoden för varje indatamängd som bearbetas av cmdleten.
Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).

Följande kod visar en implementering av ProcessRecord-metoden.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Efter bearbetnings åtgärder

Cmdletar ska åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) för att lägga till eventuella efter bearbetnings åtgärder som är giltiga för alla poster som bearbetats av cmdleten.
Din cmdlet kan till exempel behöva rensa objektvariabler när den har bearbetats.

När PowerShell bearbetar en kommando pipeline anropar PowerShell denna metod en gång för varje instans av cmdlet: en i pipelinen.
Det är dock viktigt att komma ihåg att PowerShell-körningen inte anropar EndProcessing-metoden om cmdleten avbryts halvvägs genom indata-bearbetningen eller om ett avslutande fel inträffar i någon del av cmdleten.
Därför bör en cmdlet som kräver rensning av objekt implementera hela [system. IDisposable](/dotnet/api/System.IDisposable) -mönstret, inklusive en slutförd, så att körningen kan anropa både EndProcessing-och [system. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) -metoderna i slutet av bearbetningen.
Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).

Följande kod visar en implementering av metoden EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Se även

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Självstudie om SelectStr](selectstr-tutorial.md)

[System. IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
