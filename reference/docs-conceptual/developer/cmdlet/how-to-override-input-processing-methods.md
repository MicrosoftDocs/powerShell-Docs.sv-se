---
ms.date: 09/13/2016
ms.topic: reference
title: Åsidosätta bearbetningsmetoder för indata
description: Åsidosätta bearbetningsmetoder för indata
ms.openlocfilehash: 4e8d71a34a1480ce63435ac6cc5dce60d4219c03
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667019"
---
# <a name="how-to-override-input-processing-methods"></a>Åsidosätta bearbetningsmetoder för indata

I de här exemplen visas hur du skriver över metoderna för bearbetning av indata i en-cmdlet. Dessa metoder används för att utföra följande åtgärder:

- Metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) används för att utföra start åtgärder vid en tidpunkt som är giltiga för alla objekt som bearbetas av cmdleten. Windows PowerShell-körningen anropar den här metoden bara en gång.

- Metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) används för att bearbeta de objekt som skickas till cmdleten. Windows PowerShell-körningen anropar den här metoden för varje objekt som skickas till cmdleten.

- Metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) används för att utföra bearbetnings åtgärder vid enstaka tidpunkter. Windows PowerShell-körningen anropar den här metoden bara en gång.

## <a name="to-override-the-beginprocessing-method"></a>För att åsidosätta metoden BeginProcessing

- Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

Följande klass skriver ut ett exempel meddelande. Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>För att åsidosätta metoden ProcessRecord

- Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Följande klass skriver ut ett exempel meddelande. Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Åsidosätta EndProcessing-metoden

- Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

Följande klass skriver ut ett exempel. Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Se även

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
