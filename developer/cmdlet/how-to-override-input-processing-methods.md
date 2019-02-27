---
title: Åsidosätta indata metoderna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846755"
---
# <a name="how-to-override-input-processing-methods"></a>Åsidosätta bearbetningsmetoder för indata

De här exemplen visar hur du skriva över den inkommande metoderna i en cmdlet. Dessa metoder används för att utföra följande åtgärder:

- Den [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod för att utföra en start-åtgärder som gäller för alla objekt som bearbetas av cmdlet: en. Windows PowerShell-runtime anropar den här metoden bara en gång.

- Den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att bearbeta objekt som överförs till cmdleten. Windows PowerShell-runtime anropar den här metoden för varje objekt som skickas till cmdleten.

- Den [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod för att utföra åtgärder för bearbetning av enstaka inlägget. Windows PowerShell-runtime anropar den här metoden bara en gång.

## <a name="to-override-the-beginprocessing-method"></a>Åsidosätta metoden BeginProcessing

- Deklarera en skyddad åsidosättning av den [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod.

Följande klass skriver ett exempelmeddelande. Om du vill använda den här klassen ändra verb och substantiv i Cmdlet-attribut, ändra namnet på klassen för att återspegla den nya verb och substantiv och Lägg sedan till vilka funktioner du behöver du åsidosättandet av den [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod.

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

## <a name="to-override-the-processrecord-method"></a>Åsidosätta metoden ProcessRecord

- Deklarera en skyddad åsidosättning av den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.

Följande klass skriver ett exempelmeddelande. Om du vill använda den här klassen ändra verb och substantiv i Cmdlet-attribut, ändra namnet på klassen för att återspegla den nya verb och substantiv och Lägg sedan till vilka funktioner du behöver du åsidosättandet av den [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.

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

## <a name="to-override-the-endprocessing-method"></a>Åsidosätta metoden EndProcessing

- Deklarera en skyddad åsidosättning av den [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.

Följande klass skriver ett exempel. Om du vill använda den här klassen ändra verb och substantiv i Cmdlet-attribut, ändra namnet på klassen för att återspegla den nya verb och substantiv och Lägg sedan till vilka funktioner du behöver du åsidosättandet av den [System.Management.Automation.Cmdlet.Endprocessing* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.

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

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
