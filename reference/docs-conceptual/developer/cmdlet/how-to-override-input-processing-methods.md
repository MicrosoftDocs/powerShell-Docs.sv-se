---
title: Så här åsidosätter du metoder för indata-bearbetning | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355554"
---
# <a name="how-to-override-input-processing-methods"></a>Åsidosätta bearbetningsmetoder för indata

I de här exemplen visas hur du skriver över metoderna för bearbetning av indata i en-cmdlet. Dessa metoder används för att utföra följande åtgärder:

- Metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) används för att utföra start åtgärder vid en tidpunkt som är giltiga för alla objekt som bearbetas av cmdleten. Windows PowerShell-körningen anropar den här metoden bara en gång.

- Metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) används för att bearbeta de objekt som skickas till cmdleten. Windows PowerShell-körningen anropar den här metoden för varje objekt som skickas till cmdleten.

- Metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) används för att utföra bearbetnings åtgärder vid enstaka tidpunkter. Windows PowerShell-körningen anropar den här metoden bara en gång.

## <a name="to-override-the-beginprocessing-method"></a>För att åsidosätta metoden BeginProcessing

- Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

Följande klass skriver ut ett exempel meddelande. Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodsignatur.

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
