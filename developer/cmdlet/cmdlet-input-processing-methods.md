---
title: Cmdlet-indata metoderna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670312"
---
# <a name="cmdlet-input-processing-methods"></a>Bearbetningsmetoder för cmdlet-indata

Cmdlet: ar måste åsidosätta en eller flera av indata metoderna som beskrivs i det här avsnittet för att utföra sitt arbete.
Dessa metoder kan cmdleten för att utföra åtgärder för förbearbetning, inkommande bearbetning och efterbearbeta.
Dessa metoder kan du stoppa cmdlet-bearbetning.
Ett mer detaljerat exempel på hur du använder dessa metoder, se [SelectStr självstudien](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Före bearbetnings åtgärder

Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod för att lägga till alla förbearbetning åtgärder som gäller för alla poster som bearbetas senare av cmdlet: en.
När PowerShell bearbetar en kommando-pipeline, anropar PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen.
Mer information om hur PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](/previous-versions/ms714429(v=vs.85)).

Följande kod visar en implementering av metoden BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Bearbetning av indata

Cmdlet: ar kan åsidosätta den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att bearbeta indata som ska skickas till cmdleten.
När PowerShell bearbetar en kommando-pipeline, anropar den här metoden för varje inkommande post som bearbetas av cmdlet: en med hjälp av PowerShell.
Mer information om hur PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](/previous-versions/ms714429(v=vs.85)).

Följande kod visar en implementering av metoden ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Efterbearbetning åtgärder

Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod för att lägga till alla efterbearbetning åtgärder som gäller för alla poster som bearbetats av cmdlet: en.
Till exempel cmdlet: kan behöva Rensa objektvariabler när den har slutförts bearbetning.

När PowerShell bearbetar en kommando-pipeline, anropar PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen.
Det är dock viktigt att komma ihåg att PowerShell-runtime inte anropa metoden EndProcessing om cmdleten avbryts mitt via dess inkommande bearbetning eller om ett avslutande fel som inträffar i någon del av cmdlet: en.
Därför bör en cmdlet som kräver objektet Rensa implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) mönstret, inklusive en finaliserare så att körningen kan anropa både EndProcessing och [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) metoder i slutet av bearbetning.
Mer information om hur PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](/previous-versions/ms714429(v=vs.85)).

Följande kod visar en implementering av metoden EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Se även

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr självstudien](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
