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
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059379"
---
# <a name="cmdlet-input-processing-methods"></a>Bearbetningsmetoder för cmdlet-indata

Cmdlet: ar måste åsidosätta en eller flera av indata metoderna som beskrivs i det här avsnittet för att utföra sitt arbete. Dessa metoder kan cmdleten förväg bearbetnings åtgärder, inkommande bearbetningsåtgärder och efter bearbetningsåtgärder. Dessa metoder kan du stoppa cmdlet-bearbetning.

## <a name="pre-processing-tasks"></a>Före bearbetnings uppgifter

Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod för att lägga till alla förbearbetning åtgärder som gäller för alla poster som bearbetas senare av cmdlet: en. När Windows PowerShell bearbetar en kommando-pipeline, anropar Windows PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen. Mer information om hur Windows PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Följande kod visar en implementering av den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Ett mer detaljerat exempel på hur du använder den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod, se [SelectStr självstudien](./selectstr-tutorial.md). I de här självstudierna i **väljer Str** cmdlet använder den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod för att generera det reguljära uttrycket som används för att söka efter de indata som bearbetar poster.

## <a name="input-processing-tasks"></a>Ange uppgifter

Cmdlet: ar kan åsidosätta den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod för att bearbeta indata som ska skickas till cmdleten. När Windows PowerShell bearbetar en kommando-pipeline, anropar den här metoden för varje inkommande post som bearbetas av cmdlet: en i Windows PowerShell. Mer information om hur Windows PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Följande kod visar en implementering av den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Ett mer detaljerat exempel på hur du använder den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod, se [SelectStr självstudien](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Efterbearbetning

Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metod för att lägga till alla efterbearbetning åtgärder som gäller för alla poster som bearbetats av cmdlet: en. Till exempel cmdlet: kan behöva Rensa objektvariabler när den har slutförts bearbetning.

När Windows PowerShell bearbetar en kommando-pipeline, anropar Windows PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen. Det är dock viktigt att komma ihåg att Windows PowerShell-runtime inte anropar den [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metoden om cmdlet: en har avbrutits mitt via dess inkommande bearbetning eller om avslutande fel uppstår i någon del av cmdlet: en. Därför bör en cmdlet som kräver objektet Rensa implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) mönstret, inklusive en finaliserare så att körningen kan anropa både den [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) och [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) metoder i slutet av bearbetning. Mer information om hur Windows PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Följande kod visar en implementering av den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Ett mer detaljerat exempel på hur du använder den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod, se [SelectStr självstudien](./selectstr-tutorial.md).

## <a name="see-also"></a>Se även

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
